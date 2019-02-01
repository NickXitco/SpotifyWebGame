# SpotifyWebGame


--[1/31/2019, 1:04PM]--

Alright I don't have time to code anything right now, but I'm having a bad day,
and I want to get something done that feels like work. Basically the current plan
for this website is to have a few things:

	- A navigable "cloud" "galaxy" thing of the entire Spotify Network. 
		> because of the limitations of modern computers/phones and most web
		> browser, we can't render all 1.x million nodes and ~20 million edges
		> at once, that's just not feasible and it would probably look dumb too
		>
		> I forget if I ended up completing this statistic or heuristic or whatever
		> you want to call it but the proposed solution for this was to basically
		> define clusters of the entire network. Possibly for each genre, possibly
		> for each "hub" of nodes. That, OR
		>
		> We could define effectively a Z layer as well. So instead of having all
		> 1.x million nodes on a single XY plane, we create a few, maybe idk 16
		> buckets to place each of the nodes in?
		>
		> So let's say that the top 500 artists or so (everything seemed to be able
		> to handle that number fine) are on Z=0. Alright? And then we put maybe, 
		> 5000 artists ***THAT ARE CONNECTED TO THE Z=0 LAYER**
			& See that's the rub here, is that we can't just take the top 500 artists
			& Randomly, and then just bascially sort everything by follower counts, no
			& we have to come up with a better heurstic than that, something
			& that takes into account linkages and such, so that when you generate the
			& Z=1 layer, you're seeing deeper connections of what is on the Z=0 layer
			&
			& So maybe what we first do is create the clusters, and define maybe 50-100
			& large groups of nodes, then take the best artist from each of those nodes.
			&
			& Defining best here might be something like:
				* What is the artist, from each cluster, that has the most followers
				* AND has a direct connection to another cluster with 
				* a large number of followers. We want these clusters to ideally be interconnected,
				* Maybe with some strings of lower-level artists connecting them.
			&
		> So then we take the best nodes from each of the clusters, those are Z=0,
		> Then we continue to cluster down lower and lower, taking the top 50-100
		> of each Z=n_x layer where n is the layer and x is the cluster
		> and making them into new Z=n+1_x layers.
		>
		> Because, in all reality, if you're looking at a Z=3_x cluster, you're
		> probably not going to want to see *every* Z=3 cluster, so we don't have
		> to render everything at once, all we have to do is render
		> Z=0, then Z=0 + Z=1_x + Z=2_x_y, and so on. We could probably have
		> some of the things derender based on the camera's position in the canvas
		> but that's a later optimization issue.
	
	- A side panel of artist information
	
	- A filter/search system
	
	- A "WikiGame"-style random search game.
		> Basically something like:
		>
		> You get two random artists, probably in the top 75000 or so artists
		> You're given the position of the two in the graph, like it zooms out to show it
		> and you basically have to quickly route from one artist to the another.
		> 
		> After you finish, it shows you your time, steps taken, genres visted, other interesting stats,
		> as well as the best possible path, which (I think, could be calculated by a BFS that starts
		> running client-side at the same time as the client starts.
		>
		> It's a sort of "race-the-CPU" sort of thing. We could also kinda capitalize on that and
		> have you *Actually* race your computer. I'd have to see how long the BFS takes.
		> Maybe I could implement different levels of difficulty, if the BFS isn't too fast.
		>
		> Depending on how long it takes, we could probably store best paths in an offline database to
		> just retrieve them on completion? idk that sounds dumb I'll have to see how long
		> everything takes on a normal system though.
		>
		> I think if I did this right, it will be the crown-jewel of this website.
		
anyways, gtg, this felt good to right, I'm excited to get to work, not really sure where to start,
I think a good place would be implementing the graph and search system in Python.
		
		
		
				
		
		