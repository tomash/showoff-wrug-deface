!SLIDE title-slide

# Engines: potrzeba adaptacji widoków


!SLIDE

# "dorzućmy tu jeszcze jeden link"


!SLIDE title-slide

<img src="angry-frown.png" height="400px" />


!SLIDE

# skopiowanie i nadpisanie widoku


!SLIDE title-slide

### "we have updated our views"

<img src="angry-desk-flip.png" height="400px" />


!SLIDE

# uchwyty ("hooks")


!SLIDE code

    @@@ HTML
    <tbody>
      <% @users.each do |user|%>
        <tr id="<%= dom_id user %>">
          <%- locals = {:user => user} %>
          <%= hook :admin_users_index_rows, locals do %>
            <td width="350px"><%=link_to user.email, object_url(user) %></td>
          <% end %>
          <td>
            <%= hook :admin_users_index_row_actions, locals do %>
              <%= link_to_edit user %> &nbsp;
              <%= link_to_delete user %>
            <% end %>
          </td>
        </tr>
      <% end %>
    </tbody>



!SLIDE title-slide

<img src="rage-unhappy.png" height="400px" />


!SLIDE

# "obiektowe" generatory widoków


!SLIDE code

    @@@ Ruby
    class Cart::Login < User::Form
      def to_html
        h3 :'.login'
        p :'.blurbs.login'
        p :'.blurbs.register'
        super
      end

      protected

        def form_arguments
          [User.new, { :as => resource_name, :url => session_path(resource_name), :html => { :class => 'sign_in' } }]
        end
    end


!SLIDE title-slide

<img src="neutral-why.png" height="400px" />


!SLIDE

# naprawdę nie da się inaczej?


!SLIDE

## manipulacja drzewem DOM po stronie javascriptu


!SLIDE code
    

    @@@ Javascript
    $('h3').insertBefore($('.prehead'));


!SLIDE title-slide

## poważnie myślałem o bibliotece do adaptacji widoków z Engines poprzez manipulację DOM w javascripcie

<img src="cool_story_bro.jpg" height="400px" />


!SLIDE

# Podstawowy problem

## DOM jest *drzewem*
### zignorowanie tego faktu jest kursem na porażkę

<img src="failroad.jpg" height="300px" />