const headers = {
  "Content-Type": "application/json",
  Authorization:
{
	"Request Headers (718 B)": {
		"headers": [
			{
				"name": "Accept",
				"value": "application/json, text/plain, */*"
			},
			{
				"name": "Accept-Encoding",
				"value": "gzip, deflate, br, zstd"
			},
			{
				"name": "Accept-Language",
				"value": "en-US,en;q=0.5"
			},
			{
				"name": "Authorization",
				"value": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjIyMzU1NzkwLCJ0aW1lc3RhbXAiOjE3MjY1NjM5NjQzODgsInR5cGUiOjEsImlhdCI6MTcyNjU2Mzk2NCwiZXhwIjoxNzI3MTY4NzY0fQ.2wlUvEHlE6bIQZFML36kd5wnFpGbRGE5ozul9ZJu6sQ"
			},
			{
				"name": "Cache-Control",
				"value": "no-cache"
			},
			{
				"name": "Connection",
				"value": "keep-alive"
			},
			{
				"name": "Host",
				"value": "api.apiduck.xyz"
			},
			{
				"name": "Origin",
				"value": "https://app.duckcoop.xyz"
			},
			{
				"name": "Pragma",
				"value": "no-cache"
			},
			{
				"name": "Referer",
				"value": "https://app.duckcoop.xyz/"
			},
			{
				"name": "Sec-Fetch-Dest",
				"value": "empty"
			},
			{
				"name": "Sec-Fetch-Mode",
				"value": "cors"
			},
			{
				"name": "Sec-Fetch-Site",
				"value": "cross-site"
			},
			{
				"name": "TE",
				"value": "trailers"
			},
			{
				"name": "User-Agent",
				"value": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:130.0) Gecko/20100101 Firefox/130.0"
			}
		]
	}
}
}

async function delay(ms: number) {
  return new Promise((reslove) => setTimeout(() => reslove(true), ms))
}

async function makeMoney() {
  for (let i = 1; i <= 500; i++) {
    fetch("https://api.apiduck.xyz/user-partner-mission/claim", {
      method: "POST",
      headers,
      body: JSON.stringify({
        partner_mission_id: i,
      }),
    })
      .then(async (res) => {
        const data = await res.json()

        console.log(`${i}: ${res.status} ${data.error_code}`)
      })
      .catch((err) => {
        console.log(err)
      })

    await delay(250)
  }
}

makeMoney()
