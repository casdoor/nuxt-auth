// Copyright 2024 The Casdoor Authors. All Rights Reserved.
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//      http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

<template>
  <div>signing...</div>
</template>

<script>
import Cookies from 'js-cookie';
import Sdk from 'casdoor-js-sdk';
import sdkConfig from '@/conf';

export default {
  name: 'AuthCallback',

  mounted() {
    const CasdoorSDK = new Sdk(sdkConfig);
    const additionalParams = {
      client_secret: sdkConfig.clientSecret,
    };

    CasdoorSDK.exchangeForAccessToken(additionalParams)
      .then((res) => {
        if (res && res.access_token) {
          return CasdoorSDK.getUserInfo(res.access_token);
        }
      })
      .then((res) => {
        const casdoorUserInfo = res;
        console.log('casdoorUserInfo:', casdoorUserInfo);
        Cookies.set('casdoorUser', JSON.stringify(casdoorUserInfo));
        this.$router.push('/profile');
      })
      .catch((error) => {
        console.error('Failed to get access_token:', error);
        this.$router.push('/');
      });

    return <div>signing...</div>;
  },
};
</script>
