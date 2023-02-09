# README

Maintenant que ta BDD est prête, tu vas répondre aux questions ci-dessous :

## a) Niveau facile

Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
```
Album.all.count
```

Qui est l'auteur de la chanson "White Room" ?
```
Track.find_by(title:"White Room").artist
```

Quelle chanson dure exactement 188133 milliseconds ?
```
Track.find_by(duration: 188133)
```

Quel groupe a sorti l'album "Use Your Illusion II" ?
```
Album.find_by(title: "Use Your Illusion II").artist
```


## b) Niveau Moyen

Combien y a t'il d'albums dont le titre contient "Great" ? (indice)
```
Album.where("title like ?", "%Great%").count
```

Supprime tous les albums dont le nom contient "music".
```
Album.where("title like ?", "%music%").destroy_all
```

Combien y a t'il d'albums écrits par AC/DC ?
```
Album.where(artist:"AC/DC").count
```

Combien de chanson durent exactement 158589 millisecondes ?
```
Track.where(duration:158589).count
```

## c) Niveau Difficile

Pour ces questions, tu vas devoir effectuer des boucles dans la console Rails. C'est peu commun mais c'est faisable, tout comme dans IRB.

puts en console tous les titres de AC/DC.
```
Track.where(artist:"AC/DC").each do |track|
    puts track.title
end
```

puts en console tous les titres de l'album "Let There Be Rock".
```
Track.where(album:"Let There Be Rock").each do |track|
    puts track.title
end
```

Calcule le prix total de cet album ainsi que sa durée totale.
```
price_arr = []
duration_arr =[]
Track.where(album:"Let There Be Rock").each do |track|
    price_arr << track.price
    duration_arr << track.duration
end
puts "Price of album : #{price_arr.sum}"
puts "Duration of album : #{duration_arr.sum}"
```

Calcule le coût de l'intégralité de la discographie de "Deep Purple".
```
price_arr = []
Track.where(artist:"Deep Purple").each do |track|
    price_arr << track.price
end
puts price_arr.sum
```

Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
```
Track.where(artist:"Eric Clapton").each do |track|
    puts track.update!(artist:"Britney Spears")
end
```