!SLIDE

# Deface

<img src="defaced.jpg" height="300" />


!SLIDE

# Do rzeczy!

<img src="robert_burneika.jpg" height="300" />


!SLIDE code
    @@@ Ruby
    Deface::Override.new(
      :virtual_path  => "shared/_products",
      :insert_bottom => "#products_list_item",
      :text => '<div class="availability">
                  <%= product.on_hand %> in stock
                </div>',
      :name    => "products_list_item_availability")


!SLIDE bullets

* podczas renderowania pliku "shared/\_products"
* weź element z id "products\_list\_item"
* i na samym dole
* wstaw kod pokazujący stany magazynowe


!SLIDE bullets

* https://github.com/railsdog/deface
* http://deface.heroku.com/


!SLIDE bullets

## view customization is now 20% cooler

* ✓ łatwe w utrzymaniu i aktualizacji
* ✓ tylko ważny kod
* ✓ dokumentacja
* ✓ zero-bullshit


!SLIDE

# Zastosowania oprócz Spree?

## dowolny engine

"I've tested Deface with Refinery a while ago and it worked no problem. It's really just a matter of including the gem and creating the overrides in the relevant app/overrides directory."
-- Brian Quinn, autor Deface


!SLIDE

<img src="commits.png" height="447" />


!SLIDE code
    @@@ Ruby
    Deface::Override.new(
      :virtual_path => "posts/index",  
      :surround => "ul.posts",
      :text => "<% cache('foo') do %>
                  <%= render_original %>
                <% end %>",
      :name => "Posts#index")

