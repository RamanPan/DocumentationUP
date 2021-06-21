# BoFoRe Backend 
## SCHEME BD

![Scheme](.\Scheme.png "Scheme")

*Page 1  Scheme BD*

## Models


```
@Entity
@Table(name = "users")
data class User (
        @Id
        @GeneratedValue(strategy = GenerationType.AUTO)
        val id: Long? = 0,

        @Column(name="username")
        var username: String?=null,

        @Column(name="first_name")
        var firstName: String?=null,

        @Column(name="last_name")
        var lastName: String?=null,

        @Column(name="email")
        var email: String?=null,

        @Column(name="password")
        var password: String?=null,

        @Column(name="enabled")
        var enabled: Boolean = false,

        @ManyToMany(fetch = FetchType.EAGER)
        @JoinTable(
                name = "users_roles",
                joinColumns = [JoinColumn(name = "user_id", referencedColumnName = "id")],
                inverseJoinColumns = [JoinColumn(name = "role_id", referencedColumnName = "id")]
        )
        var roles: Collection<Role>? = null
)
```

```
@Entity
@Table(name = "roles")
data class Role (
        @Id
        @GeneratedValue(strategy = GenerationType.AUTO)
        val id: Long,
        @Column(name="name")
        val name: String
)

```

```
@Entity
@Table(name = "bok")
data class Book(
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO) var id: Long?,
    @Column(name = "author") var author: String?,
    @Column(name = "tittle") var tittle: String?,
    @Column(name = "genre") var genre: String?,
    @Column(name="comment")
    var commenta: String? = null,
    @Column(name="isread")
    var isRead: Boolean? = false
) {
    @ManyToMany(fetch = FetchType.EAGER)
        @JoinTable(
                name = "users_books",
                joinColumns = [JoinColumn(name = "user_id", referencedColumnName = "id")],
                inverseJoinColumns = [JoinColumn(name = "book_id", referencedColumnName = "id")]
        )
        var books: Collection<User>? = null
}
```
## URL's
```
routes: [
      {
        path: '/',
        name: 'Home',
        component: Home
      },
      {
        path: '/home',
        name: 'Home',
        component: Home
      },
      {
        path: '/login',
        name: 'SignIn',
        component: SignIn
      },
      {
        path: '/register',
        name: 'SignUp',
        component: SignUp
      },
      {
        path: '/user',
        name: 'UserPage',
        component: UserPage
      },
      {
        path: '/admin',
        name: 'AdminPage',
        component: AdminPage
      },
      {
        path: '/email',
        name: 'EmailPage',
        component: EmailPage
      },
      {
        path: '/book',
        name: 'Book',
        component: BookPage
      },
      {
        path: '/book/addnew',
        name: 'AddBook',
        component: AddBook
      },
      {
        path: '/book/showall',
        name: 'SeeBooks',
        component: SeeBooks
      },
      {
        path: '/book/rand',
        name: 'RandBook',
        component: RandBook
      },
      {
        path: '/book/allread',
        name: 'SeeReadBooks',
        component: SeeReadBooks
      },
      {
        path: '/book/allnotread',
        name: 'SeeNotReadBooks',
        component: SeeNotReadBooks
      }
      
    ]
}) 
```