# Rails API Relationships Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  Describe a reason why a join tables may be valuable.

  ```md
the joint table help us to make a relationship between other tables. it will help to reuse the id of some other thinsg on the tables and help us to assign them to multuple items  ```

1.  Provide a database table structure and explain the Entity Relationship that
  describes a many-to-many relationship for `Profiles`, `Movies` and `Favorites`
  (Think of Netflix). A `Profile` has a `given_name`, `surname` and `email` and a
  `Movies` have `title`, `release_date`, and `length` and `Favorites` would be the
  join table with references to `Movies` and `Profiles`.

  ```md
    # < Your Response Here >
  ```

1.  For the above example, what needs to be added to the Model files?

  ```rb
  class Profile < ActiveRecord::Base
    has_many :favorites, through: :movies
    has_many :movies

    validates :given_name, presence: true
    validates :surname, presence: true
    validates :email, presence: true
  end
  ```

  ```rb
  class Movie < ActiveRecord::Base
    has_many :profiles, through: :favorites
    has_many :profiles

    validates :title, presence: true
    validates :release_date, presence: true
    validates :length, presence: true
  end
  ```

  ```rb
  class Favorite < ActiveRecord::Base
    belongs_to :movies
    belongs_to :favorites
  end
  ```

1.  What is the purpose of a serializer? What would our `Profile` serializer look
like to show all movies favorited by a profile on
`http://localhost:3000/profiles/1`

  ```md
    serializer help up to choose what we want to show
  ```

  ```rb
  class ProfileSerializer < ActiveModel::Serializer
    attributes :id, :movie, :profile, :Favorite, :doctor
  end
  ```

1.  What would the command be to _scaffold_ out a **join table** for Favorites from
the above `Movies` and `Profiles`.

  ```sh
i will create a favorites Serializer, model and controller files
```

1.  What is `Dependent: Destroy` and where/why would we use it?

  ```md
  destroy is to remove files.

  ```

1.  Think of **ANY** example where you would have a one-to-many relationship as well
as a many-to-many relationship in an application. You only need to list the
description about the resources and how they relate to one another.

  ```md

food_service - has_many :clients, through: :delivereis
               has_many :clients

delivery - belongs_to :food_service :client

client - has_many :food_services, through: deliveries
         has_many :food_services
  ```
