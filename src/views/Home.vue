<template>
  <div class="home">
    <div id="J_prismPlayer" class="prism-player"></div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Home',
  mounted(){
    this.getToken()
  },
  methods: {
    async getToken(){
      const {
        accessKeyId,
        accessKeySecret,
        mtsHlsUriToken,
        region,
        securityToken
      } = await axios.post('https://app.newtiming.com/api/v1/sts/info')
      const player = new Aliplayer({
        id: 'J_prismPlayer',
        width: '100%',
        autoplay: true,
        // source : 'https://act.mcake.com/fangli/2018/pc/zhou-nian/video/zhounian-7.mp4',
        //播放方式四：使用STS方式播放
        vid : '00f1b67e4f974f9d9883af482613b7bc',
        accessKeyId: accessKeyId,
        securityToken: securityToken,
        accessKeySecret: accessKeySecret,
        region: region,
        setHlsUriToken: {

        }
        // getCurrentTime: _this.aaaa
      },function(player){
        console.log(111)
        // let vidsts = new VidSts();
        // let playerConfig = new VidPlayerConfigGen();
        // playerConfig.setMtsHlsUriToken(mtsHlsUriToken);
        // vidsts.setPlayConfig(playerConfig);
      });

      console.log(player)

    }
  }
}
</script>
