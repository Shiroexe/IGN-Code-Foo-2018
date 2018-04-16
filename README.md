[Google Doc with better formatting here: https://docs.google.com/document/d/1w9T3gAq8IMMn6hp5w3tHdnUXzkqdChQrsJizG75v3aw/edit?usp=sharing]

1] Who am I?
Hi, I’m Aaron. Nice to e-meet you. I know this is a text document, but I’m sure you can sense the bond we’re forming already.

I’m a space and science nerd, through and through. The most damning evidence being that I’m
finishing up my master’s degree in astrophysics this spring at San Francisco State, and only slightly less damning that I’m a science communicator working in the California Academy of Sciences’ planetarium. The personality needed for both lines of work lies in a very small part of the Venn Diagram, so I fall into a weird space directly between outgoing public speaker and distant, ascetic researcher, depending on the environment and the work I need to get done. 

When I’m not lost in space, I’m also diving deep on media and pop culture. Comedians and movies have always been something I’ve enjoyed, but over the past five or so years I’ve been really paying attention to how the internet has been changing how we interact with culture, and who makes the media we’re seeing. More and more I see that what’s happening online isn’t just responding to what we experience, but it’s shaping and evolving it.

With a not-at-all-subtle segue, IGN caught my interest because it’s perching itself right in the middle of all those different fields. Video games of course, but the presence the company has in Movies, TV, comics, live shows, podcasts, quality interviews, developing internet personalities, and just general goings on of the world makes it really stand out. I’m interested in joining the IGN team to connect with that world more deeply, and also to help push it forward into new, less charted waters with my science and education experience. I suspect my background might be able to bring some unique perspectives and ideas to the team, though I’m not sure how many astrophysicists you have on staff already... 

The short of it is that IGN is doing really cool things, and it’s on the bleeding edge of even cooler things coming in the future, and I’d like to be a part of it. Code Foo lines up with the my technical background that I’ve developed as a scientist, and gives me an opportunity to get involved, so I thought it was well worth this sleepless night of learning Ruby from the ground up and throwing my application in. 

I hope you agree.

-- Aaron

(PS) I heard about Code Foo during a few First Fridays I got to attend. I think specifically Ryan, Mark, and Ginger were the pushers that convinced me to give it a shot.

2] How many Geomags would it take to remake the Eiffel tower after the Infinity War levels it?


If we’re going to replace the tower with Geomags, we’ll need at least the same volume of geomags as there was iron on the pre-Infinity War tower. 

Checking the tower’s official website here, there are 7,300 tonnes of wrought iron, which is about 16 million pounds (~7.3 million kg). Looking at a table of common metal properties (confidence in that site might wane since it looks straight out of 1993, but it’s supported here as well), wrought iron has a density of 7750 kilograms per cubic meter.

Dividing that total mass by the density, we get ourselves an Eiffel volume of about 942 cubic meters.

Taking a look at a single Geomag rod, it has dimensions of 27 mm in length, and 7.4 mm in diameter.
The volume of a single rod will be V= r2 L

V = π * .0272 mm2 * .0074 mm = 16900 mm3 = 1.69 * 10-5 m3

Comparing that volume of a single rod, and dividing the total Eiffel volume by it, we find: 

55.7 million Geomags

Some notes of interest, the weight for the whole geomag tower would be about 262,000 kg, which is comparable to the mass of a blue whale. The geomag wiki mentions that a chain of the rods falls apart under its own weight after about 65 units, or about 9 feet. You could change the tower’s architecture to better support against gravity marginally, but any structure of that size held up by magnets is going to last about as long as Hawkeye trying to 1v1 Thanos.

3] If a chicken crosses the road and no one is there to see it, would we know if it fell into a pothole or not?



First thing first: we need a function to build the road. I set it to generate the potholes randomly, with a tunable probability that determines the likelihood for spaces to have a hole or not, depending on the severity of the falling sky of course. We also need hard checks to see if:

1: There is no possible position on the left of the road to start from
2: There are no holes to avoid, making Henny’s trip trivial.

I decided to break out of the simulation in either case, allowing that iteration of Henny to go about his day unhindered by further changes to his universe.

In the non-trivial cases, the meat of the simulation is in the path finding. A recursive loop chooses every available path from the starting point and investigates it to completion. As we step through the possibilities, the ‘road’ array is updated to reflect the path taken thus far, and the ‘path’ array lets us keep track of the path we’ve gone down to keep from backtracking unproductively (trapped in circles). After we’ve reached the end of a line, success or no, the last changes to the ‘road’ and ‘path’ arrays are undone so the loop can step backwards in the recursion process. 

In the cases where Henny does make it to the other side, we display a message confirming the success, the full coordinate path that got there, a map that shows the safe path, and we add another talley onto ‘successcount’ to track the total paths he’s found.

The code is fully scalable to larger roads. I tried up to 10 x 10, but things chug pretty hard with ~ 30,000+ possible paths. This could be countered by upping the probability for a pothole to appear, but I’d feel bad dropping more sky on that poor chicken...
