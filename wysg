const cookieName = '网易云音乐(刷歌)'
const chavy = init()

sign()

function sign() {
  let url = { url: `http://feihuastore.top/tingge/api.php?do=daka`, headers: { Cookie: `MUSIC_U=d826c73844f71144edebb09adb54ce53898bfe622261446fc81e799e4541cead33a649814e309366; __csrf=82e2041a725dcab6e7013e05e0d36d23; __csrf=e7400ed59181fe1c534998f66dcc67ed` } }
url.headers['Accept'] = 'application/json, text/javascript, */*; q=0.01'
url.headers['Accept-Encoding'] = 'gzip, deflate'
url.headers['Accept-Language']= 'zh-cn'
url.headers['Connection']='close'
url.headers['Content-Type']= 'application/x-www-form-urlencoded; charset=UTF-8'
url.headers['Host']= 'feihuastore.top'
url.headers['Origin']= 'http://feihuastore.top'
url.headers['Referer']= 'http://feihuastore.top/tingge/'
url.headers['User-Agent']= 'Mozilla/5.0 (iPhone; CPU iPhone OS 13_4_1 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.1 Mobile/15E148 Safari/604.1'
url.headers['X-Requested-With']= 'XMLHttpRequest'
  chavy.post(url, (error, response, data) => {
    let result = JSON.parse(data)
    const title = `${cookieName}`
    let subTitle = ``
    let detail = ``
    if (result.code == 0) {
      subTitle = `播放结果`
      detail = `成功听歌${result.count}首`
    } else if (result.code == 200) {
      subTitle = `播放结果`
 detail = `重复听歌${result.count}首`
      
    } else {
      subTitle = `刷歌结果: 失败`
      
    }
    chavy.msg(title, subTitle, detail)

console.log(`${cookieName}, data: ${data}`)

  })
  chavy.done()
}

function init() {
  isSurge = () => {
    return undefined === this.$httpClient ? false : true
  }
  isQuanX = () => {
    return undefined === this.$task ? false : true
  }
  getdata = (key) => {
    if (isSurge()) return $persistentStore.read(key)
    if (isQuanX()) return $prefs.valueForKey(key)
  }
  setdata = (key, val) => {
    if (isSurge()) return $persistentStore.write(key, val)
    if (isQuanX()) return $prefs.setValueForKey(key, val)
  }
  msg = (title, subtitle, body) => {
    if (isSurge()) $notification.post(title, subtitle, body)
    if (isQuanX()) $notify(title, subtitle, body)
  }
  log = (message) => console.log(message)
  get = (url, cb) => {
    if (isSurge()) {
      $httpClient.get(url, cb)
    }
    if (isQuanX()) {
      url.method = 'GET'
      $task.fetch(url).then((resp) => cb(null, {}, resp.body))
    }
  }
  post = (url, cb) => {
    if (isSurge()) {
      $httpClient.post(url, cb)
    }
    if (isQuanX()) {
      url.method = 'POST'
      $task.fetch(url).then((resp) => cb(null, {}, resp.body))
    }
  }
  done = (value = {}) => {
    $done(value)
  }
  return { isSurge, isQuanX, msg, log, getdata, setdata, get, post, done }
}
