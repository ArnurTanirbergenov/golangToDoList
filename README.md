# golangToDoList
Golang ToDo List for final
My list will have a authenfication by using JWT tokens.Users could create, delete and change tasks. This project is crucial for managment of your tasks.
I will be writing using Go language, postgresql, docker. If you have enough knowledge on docker it will be the only app that you needed to install this application.
All you need to start is
make build && make run

I am using files migration so if you start it first time you need to write this one too.
make migrate

Here is my endpoints:
```auth := router.Group("/auth")
	{
		auth.POST("/sign-up", h.signUp)
		auth.POST("/sign-in", h.signIn)
	}
	api := router.Group("/api")
	{
		lists := api.Group("/lists")
		{
			lists.POST("/", h.createList)
			lists.GET("/", h.getAllLists)
			lists.GET("/:id", h.getListById)
			lists.PUT("/:id", h.updateList)
			lists.DELETE("/:id", h.deleteList)
			items := lists.Group(":id/items")
			{
				items.POST("/", h.createItem)
				items.GET("/", h.getAllItems)
			}
		}
		items := api.Group("items")
		{
			items.GET("/:id", h.getItemById)
			items.DELETE("/:id", h.deleteItem)
			items.PUT("/:id", h.updateItem)
		}
	}
 ```

I am planning to use clean architecture structures. So you could change UI, Databases to which you like it will not change my bussines logic.

There will be 5 tables in postgresql: 
users(id, name, username,password_hash),
users_tasks(id, user_id,list_id),
todo_list(id, title, description),
list_items(id, list_id, item_id),
todo_item(id, title,description, done)
Here is a diagramm it is also uploaded here in my git repository
![Untitled](https://github.com/ArnurTanirbergenov/golangToDoList/assets/123318070/1be25936-9f56-435a-b689-c4446899523f)

