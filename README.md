# Hello-world
% !TeX spellcheck = en_GB
\documentclass[a4paper,12pt,english]{article}
\usepackage{amsmath,amssymb,amsfonts,mathrsfs,accents} %important math packages
\usepackage{enumerate} % package for making different lists
\usepackage[T1]{fontenc} % Encoding of fonts
\usepackage{lmodern} % Latin modern font - needed for fontenc
\usepackage[utf8]{inputenc} % Encoding of input text
\usepackage[kerning]{microtype} % Better looking text
\usepackage[babel]{csquotes} % Better looking quotes
\usepackage{booktabs} % Better looking tables
\usepackage{babel} % Language control, for hyphenation etc
\usepackage{amsthm} % Package for theorem and definition enviroments
\usepackage{hyperref} % URLs 
\usepackage{graphicx}

\usepackage{caption}

\usepackage{subfig}

\usepackage{xcolor}

\usepackage[margin=1.0in]{geometry}

% Package for drawing in Latex. Depending on your installation you might need compat=1.12 or 1.11 uncommented.  
% Package for drawing in Latex. Depending on your installation you might need compat=1.12 or 1.11 uncommented.  
\usepackage{tikz}
\usetikzlibrary{patterns}
\usetikzlibrary{calc}
\usepackage{pgfplots}
%\pgfplotsset{compat=1.12}
\pgfplotsset{compat=1.11}

% For better figure placement in documents. Use [H] instead of the usual [htbp]. Inserted at the same place as in the code, as you normally want it to. 
\usepackage{float}

% Row break and not indent for new paragraph. 
\usepgfplotslibrary{fillbetween}
\setlength{\parskip}{10pt plus 1pt minus 1pt}
\setlength{\parindent}{0in}

% Personal commands I use to simplify writing stuff I use often. 
\newcommand{\reals}{\mathbb{R}} 
\newcommand{\rtwo}{\mathbb{R}^2}
\newcommand{\ints}{\mathbb{Z}}
\newcommand{\nats}{\mathbb{N}}

\newcommand\Tau{\mathcal{T}}
\newcommand\Lau{\mathcal{L}}

\DeclareMathOperator*{\argmin}{arg\,min}
\DeclareMathOperator*{\argmax}{arg\,max}


\title{Reputation on Networks}
\author{David Jackson}
\date{\today}
\begin{document}
	\maketitle 
	
	%%%%%%%%%%%%%%%%%% Q1 %%%%%%%%%
	
\section{Introduction}
``Virtually every commercial transaction has within itself an element of trust, certainly any transaction conducted over a period of time. It can be argued that much of the economic backwardness of the world can be explained by lack of mutual confidence''
\\[5pt]
\rightline{{\rm  Kenneth Arrow}}\\



``It takes twenty years to build a reputation and five minutes to ruin it. If you think about that, you will do things differently''
\\[5pt]
\rightline{{\rm  Warren Buffet}}\\

It is widely accepted that many economic transactions would never take place without some form of trust. This requirement may be due to the costs imposed by the complexity and timing of certain financial and commercial transactions, excessive enforcement costs, the lack of formal contracting or the fundamental incompleteness of contracts. 

As is clear form Arrow's introductory quote, this trust is not ubiquitous. It varies at all levels, across countries, communities, organisations, groups and individuals. Much of the literature considers trust a cultural phenomenon associated with the norms in place within any particular context. However experiments show that trust is fragile, eroding quickly in the face of defection, suggesting that these norms are subject to enforcement. Naturally trust is closely linked to the extensive literature on cooperation which outlines an array of possible enforcement mechanisms. While quid pro quo is an obvious way of enforcing behaviour in bilateral relations, a widely accepted theory in sociology is that agents behave 'well' in order to maintain their reputation within a wider community. This mechanism of indirect reciprocity allows agents to expect trustworthy behaviour by extending the 'shadow of the future' beyond ones bilateral dealings, to encompass a greater proportion of future interactions. The focus of this chapter is how this reputation mechanism generates trust in low frequency, or one off transactions and the role network structure plays in facilitating this.\footnote{For clarity, in the following analysis we shall assume trust is synonymous with the expectation that ones counterparty in a transaction behave cooperatively in spite of incentives to defect. This definition encompasses cooperation in social dilemmas however as we shall see by linking action with reputation the model structure can enforce any kind of behaviour and so may be applicable to a much broader definition of trust. } 

Remarkably this has not been analysed in the theoretical literature connecting social capital and social networks. Except for a few exceptions, existing analyses' generally consider agents leveraging their bilateral relations on a network that couples patterns of transaction and communication. While this has some foundation in reality it is far from being a general truth that the people we are socially connected to are our main transaction partners. Indeed it is often argued that when this is the case, strong social ties limit interaction with a wider network and that this is an impediment to development. Consequently it is of some interest to understand how trust can be extended to more distant partners. 

In this paper I develop a framework which sketches out the basic mechanics of a system of reputation. Rather than being a general model of how reputation operates, the setup of the model focuses on how an agents position in the network effects the level of trust engendered by their 'Good' reputation. 

The model contributes to the existing literature by providing a theoretical framework of how a system of reputation based on social norms can generate trust in transactions beyond ones immediate network. It illustrates that while network structure can limit trust when an agents information environment is subdivided into isolated components, this gatekeeper can still act as to facilitate high trust transactions between other agents in the network. It is also novel in it's attempt to explicitly incorporate norms and the effect that 'knowing of' someone has on how  information about them is transmitted.
 
The mechanism of the model is based on the interaction of three main elements. Network Structure, which determines the flow of information, Economic Environment which is given by the distribution of transaction opportunities, and Normative Environment which depends on the norms at play in any particular context. When matched, individuals estimate how much they should trust their partner by assessing who in their partners network would find out if they cheated (determined by Network Structure), how their partner values these people (given their Economic Environment), and how this value would be affected by the news of their defection (depending on their Normative Environment)\footnote{While this seems like an intuitively obvious approach it is surprisingly one that hasn't been developed in the literature. This is perhaps due to the problems of contagion that arise with private information in almost all self interested, rational agent models of indirect reciprocity.}. 

The incorporation of normative context is a novel feature of the model. This is motivated by the widely accepted and experimentally demonstrated fact that humans not only care about material outcomes, but about the process by which these outcomes are achieved (eg. Charness and Rabin 2002). These preferences and additional emotional and behavioural responses, are often shaped by perceptions of morality based on culture and the set of norms adhered to. It is this underlying sense of right and wrong that gives legitimacy to both formal and informal punishment (Fafchamps 2018). Consequently moral culture and it's associated norms are intimately connected to how a system of reputation operates. 

The model does not explicitly consider these preferences or associated emotions, but represents the Normative Environment using the device of a $Reputation \ Norm$ combined with agent's $Reputation \ Strategy's$. A Reputation Norm captures the process translating an agents actions into their reputation. This explicitly identifies the relationship between an agents history and the way his actions are received by the community. The reputation generated by this norm then acts as a coordination device upon which agents base a 'Reputation Strategy'. This effectively divides the Normative Environment into a group level component, how reputation is generated in a community, and an individual level component, how agents respond to the reputation signal. While not the focus of this paper, this endows the model with flexibility to analyse when it is optimal for agents to coordinate on a particular norm or defect from it. This may be applied to understand the stability of different cultural environments, why some are characterised by high trust and norms of good conduct, while others are notably less so.

In the set up version of the model I develop here, we consider a uniformly held Reputation Norm and a flat Economic Environment where bilateral transaction opportunities arise uniformly across each agents accessible network. To give some intuition of setting, consider a network of financial investors who maintain regular social links with their friends and colleagues in the industry. Agents use their network to access opportunities but, because of a thin market in investment attributes, they frequently transact beyond it. Conditional on the normative environment, individuals can reduce negotiation times and transaction costs by using reputational information provided by their friends in order to assess how much to trust their partners. More generally the model is applicable to a wide range of scenarios, however in many instances we need to adapt the model to fit details of the particular setting.\\


\subsection{Description of the model}



The analysis considers each agent embedded in a network that both disseminates reputational information via gossip and facilitates access to potential opportunities that arise within some limited path length or $Salience \ Distance$ $\mathbf{z}$ of themselves. This defines an agent's Economic Environment as consisting of a set of potential partners  which constitutes their $Reputation \ Set$.

Agents are randomly matched to transact with those in their Reputation Set. Transaction opportunities take the form of variable stakes Prisoners Dilemma's so that value of each potential match depends on agents choice of stakes. In addition we assume implicit link values are zero so that heterogeneous stakes reflect how the structure of an agents network effects the value of their reputation. 

A central feature of the model is that it attempts to incorporate the effect 'salience' has on how reputational information about a person spreads. The intuition behind this is that we are far more likely to be both interested in and to share information about those we know of and may potentially interact with, than those we've never heard of and consider unlikely to meet. This is implemented in the model with the $Information \ Transmission \ Rule$ that only potential partners, those within Salience Distance of each other and hence in each others Reputation Set, will pass on information about each other. This results in an agents Reputation Set being potentially divided into informationally independent sub components, dubbed $Reputation \ Components$ \footnote{A similar information transmission setup is developed by Bloch, Genecott and Ray (2009) looking at enforcement of informal insurance. They implement a system of q-level punishment that carries information to linked agents via paths of length q or less, however intermediaries and their links are not valued.}

An agents actions when transacting are translated into reputation according to a specified $Reputation \ Norm$. Updates to reputation are in turn shared with other potential partners according to the Information Transmission Rule. Reputation acts as a coordination device on which agents implement a '$Reputation \ Strategy$' analogous to a trigger strategy in infinitely repeated games. \footnote{In this setting the agents could coordinate on shared history of play, however the addition of the translation device allows the model to be extended to look at the enforcement of a more general range of behaviours}
 
From initial conditions of everyone holding 'Good' reputation I show there exists a Nash Equilibrium consisting of a triplet including the Reputation Norm, the Reputation Strategy and a set of $Consistent \ valuations$ dictating the expected stakes of every potential transaction in the network. This set of valuations provides a trust ranking of every match that depends solely on the structure of the network and the choice of Salience Distance.
 
\subsubsection{Example:}
Consider the following network where each link represents a channel of frequent communication;

\begin{figure}[H]
	\centering
\begin{center}
		\begin{tikzpicture}[node distance=1.5cm]
		
		\node[draw,shape=circle](n1)at (0,0){i};
		
		\node[draw,shape=circle](n2)[right of=n1]{j};
		\node[draw,shape=circle](n3)[above left of=n1]{a};
		\node[draw,shape=circle](n4)[below left of=n1]{b};
		\node[draw,shape=circle](n5)[above right of=n2]{c};
		\node[draw,shape=circle](n6)[below right of=n2]{d};
		
		
		\draw[-](n1)to(n2);
		\draw[-](n1)to(n3);
		\draw[-](n1)to(n4);
		\draw[-](n2)to(n5);
		\draw[-](n2)to(n6);
		
		
		\end{tikzpicture}
	\end{center}
\end{figure}
	
Assume that $\mathbf{z}=2$, so that agents can interact with their friends and their friend's friends. 

The Reputation Norm is such that an agents defection updates his reputation to 'Bad' permanently. Those who are updated about this implement a Reputation Strategy that entails rejecting any positive stakes when matched with a partner of Bad reputation.

The cooperative pay-off of each Prisoners Dilemma is given by the stakes $v$ and that the excess pay-off agents receive from defection is a function of the stakes, given by $\Tau (v)=v^2$

	
Note that if we couple the communication network with the transactions opportunities by setting $\mathbf{z}=1$, because all agents Reputation Components consist of only one partner, the maximum cooperative stakes any match can achieve is determined by bilateral enforcement such that;
$$\Tau(v^{bl})=\frac{\alpha}{1-\delta}v^{bl} \implies v^{bl}=\frac{\alpha}{1-\delta}$$
Where $\alpha$ is the matching probability and $\delta$ is an common discount factor.
We normalise $v^{bl}=1$


Now consider $a$ matched to transact with $i$.
\begin{figure}[H]
	\centering
\begin{center}
	\begin{tikzpicture}[node distance=1.5cm]
	
	\node[draw,shape=circle, fill=red](n1)at (0,0){i};
	
	\node[draw,shape=circle, fill=red](n2)[right of=n1]{j};
	\node[draw,shape=circle, fill=yellow](n3)[above left of=n1]{a};
	\node[draw,shape=circle, fill=red](n4)[below left of=n1]{b};
	\node[draw,shape=circle](n5)[above right of=n2]{c};
	\node[draw,shape=circle](n6)[below right of=n2]{d};
	
	
	
	\draw[-](n1)to(n2);
	\draw[<->, thick, color=green](n1)to(n3);
	\draw[-](n1)to(n4);
	\draw[-](n2)to(n5);
	\draw[-](n2)to(n6);
	
	
	\end{tikzpicture}
\end{center}
\end{figure}


$a$'s Reputation Set under $\mathbf{z}=2$ consists of $i,j$ and $b$. This is also $a$'s Reputation Component (shown in red) when dealing with $i$ as $i$ is effectively a gatekeeper to all $a$'s potential transactions and so is in a position to spread information about $a$'s defection to all of her potential partners. 




$i$ on the other hand has a Reputation Set consisting of $a,b,c,d$ and $j$. This is made up of three Reputation Components, one for each link. When dealing with $a$, $i$'s Reputation Component (in yellow) is simply $a$. 

This limits the stakes for the transaction to $v_1=v^{bl}=1$ because $a$ has nobody to spread the information to. At any higher stakes $i$ is better off cheating and then cutting $a$ off from the network. Note that it is the defector rather than the victim that has the incentive to sever ties here. 

Due to symmetry we know that all the links coloured green will have this same expected value.
\begin{figure}[H]
	\centering
	\begin{center}
	\begin{tikzpicture}[node distance=1.5cm]
	
	\node[draw,shape=circle](n1)at (0,0){i};
	
	\node[draw,shape=circle](n2)[right of=n1]{j};
	\node[draw,shape=circle](n3)[above left of=n1]{a};
	\node[draw,shape=circle](n4)[below left of=n1]{b};
	\node[draw,shape=circle](n5)[above right of=n2]{c};
	\node[draw,shape=circle](n6)[below right of=n2]{d};
	
	
	\draw[-](n1)to(n2);
	\draw[-, thick, color=green](n1)to(n3);
	\draw[-, thick, color=green](n1)to(n4);
	\draw[-, thick, color=green](n2)to(n5);
	\draw[-, thick, color=green](n2)to(n6);
	
	
	\end{tikzpicture}
\end{center}
\end{figure}

Now consider $a$ matched to $j$. 
\begin{figure}[H]
	\centering
	\begin{center}
	\begin{tikzpicture}[node distance=1.5cm]
	
	\node[draw,shape=circle, fill=green](n1)at (0,0){i};
	
	\node[draw,shape=circle, fill=red](n2)[right of=n1]{j};
	\node[draw,shape=circle, fill=yellow](n3)[above left of=n1]{a};
	\node[draw,shape=circle, fill=green](n4)[below left of=n1]{b};
	\node[draw,shape=circle](n5)[above right of=n2]{c};
	\node[draw,shape=circle](n6)[below right of=n2]{d};
	
	\draw[-](n1)to(n2);
	\draw[-, thick, color=green](n1)to(n3);
	\draw[-, thick, color=green](n1)to(n4);
	\draw[-, thick, color=green](n2)to(n5);
	\draw[-, thick, color=green](n2)to(n6);
	\draw[<->, thick, color=blue](n3)to(n2);
	
	
	
	
	\end{tikzpicture}
\end{center}
\end{figure}

Like $i$, $j$'s Reputation Set is the entire network and consists of three Reputation Components. When dealing with $a$ his Reputation Component is made up of $a,b$ and $i$. While $a$'s includes $b,i$ and $j$. Both Reputation Components are the same size, however $a$'s link with $i$ is only valued at $1$. This must be less than $j$'s link with $i$ as $i$'s Reputation Component with $j$ contains three agents rather than one. 

From this we can infer that the maximal stakes will be determined by $a$'s incentive constraint such that;

	$$(v_2)^2= v_1 + 2v_2 \implies v_2= 1+\sqrt{2}=2.4$$

From symmetry this solves for all the blue dashed potential transactions. 

\begin{figure}[H]
	\centering
	\begin{center}
		\begin{tikzpicture}[node distance=1.5cm]
		
	
	\node[draw,shape=circle](n1)at (0,0){i};
	
	\node[draw,shape=circle](n2)[right of=n1]{j};
	\node[draw,shape=circle](n3)[above left of=n1]{a};
	\node[draw,shape=circle](n4)[below left of=n1]{b};
	\node[draw,shape=circle](n5)[above right of=n2]{c};
	\node[draw,shape=circle](n6)[below right of=n2]{d};
	
	
	\draw[-](n1)to(n2);
	\draw[-, thick, color=green](n1)to(n3);
	\draw[-, thick, color=green](n1)to(n4);
	\draw[-, thick, color=green](n2)to(n5);
	\draw[-, thick, color=green](n2)to(n6);
	
	
	\draw[dashed, thick, color=blue](n3)to(n2);
	\draw[dashed, thick, color=blue](n4)to(n2);		
	\draw[dashed, thick, color=blue](n1)to(n5);
	\draw[dashed, thick, color=blue](n1)to(n6);
	\draw[dashed, thick, color=blue](n5)to(n6);
	\draw[dashed, thick, color=blue](n3)to(n4);
	
		
		
		\end{tikzpicture}
	\end{center}
\end{figure}

This leaves only the transaction between $i$ and $j$ to solve for.
\begin{figure}[H]
	\centering
\begin{center}
	\begin{tikzpicture}[node distance=1.5cm]
	
	
	
	\node[draw,shape=circle, fill=yellow](n1)at (0,0){i};
	
	\node[draw,shape=circle, fill=red](n2)[right of=n1]{j};
	\node[draw,shape=circle, fill=yellow](n3)[above left of=n1]{a};
	\node[draw,shape=circle, fill=yellow](n4)[below left of=n1]{b};
	\node[draw,shape=circle, fill=red](n5)[above right of=n2]{c};
	\node[draw,shape=circle, fill=red](n6)[below right of=n2]{d};
	
	
	\draw[<->, thick, color=red](n1)to(n2);
	\draw[-, thick, color=green](n1)to(n3);
	\draw[-, thick, color=green](n1)to(n4);
	\draw[-, thick, color=green](n2)to(n5);
	\draw[-, thick, color=green](n2)to(n6);
	
	
	\draw[dashed, thick, color=blue](n3)to(n2);
	\draw[dashed, thick, color=blue](n4)to(n2);		
	\draw[dashed, thick, color=blue](n1)to(n5);
	\draw[dashed, thick, color=blue](n1)to(n6);
	\draw[dashed, thick, color=blue](n5)to(n6);
	\draw[dashed, thick, color=blue](n3)to(n4);
	
	
	
	\end{tikzpicture}
\end{center}
\end{figure}

Both are in a symmetrical situation and will lose an additional two blue links if they defect on each other. Hence we can solve for this value such that;

 	$$(v_3)^2= v_3 + 2v_2 \implies v_3=2.75$$
 	
Despite it simplicity this example demonstrates how the potential to connect to opportunities beyond ones immediate network can significantly alter the level of trust a network supports. \\ 
	

I develop a Sequential Value Algorithm that solves for the set of Consistent Valuations on a general network. This algorithm may be extended to deal with unilateral trust and more realistic Information Transmission Rules but these require a numerical approach to solve efficiently on realistic sized networks.

The analysis provides a distribution of maximal stakes reflecting how each agents position in the network determines the level of trust their 'Good' reputation receives. This is dependent on both the size of agents Reputation Components and on the level of trustworthiness of those within these components. It is also conditional on the given normative and economic environments.

If transaction opportunities and salience are limited to an agents immediate neighbourhood ($z=1$) those with multiple disjoint subnetworks enjoy a lower level of trust than those whose neighbourhood forms a connected component because news of their defection only spreads to a limited part of their network. In this transaction environment existing network measures such as clustering and transitivity, will be positively correlated with the amount of trust associated with reputation. As transactions beyond ones immediate links become more common however ($z>1$), reputation becomes salient on a wider network and the news of a defection travels further. Now the existence of longer cycles within the network can connect disjoint neighbourhood subnetworks, creating larger Reputation Components. In this context, given limitations to degree, large amounts of clustering can generate lower levels of trust because they limit an agents interaction with a wider network. \footnote{While this might remind the reader of the contrast between Bridging and Bonding Social Capital discussed by Coleman and Putnam (ref) this is only a partial explanation. A more in depth analysis in the following chapter elucidates how these concepts may be more intimately connected to patterns of interaction and the stability of different norms. } 
 
 
Far from being a complete description of the role our socio-economic context plays in generating trust, the aim of the model is to understand the structures where reputational trust is robust to self interest. While this may in truth be a cultural phenomenon, and real people unlikely to calculate exactly how much to trust others in the way laid out in the model, the culture of trust that survives in a particular environment should be related to these patterns of enforcement.\\






\subsection{Related Literature}

Reputation is a form of indirect reciprocity which is one of the primary enforcement mechanisms for cooperation. The literature is therefore extensive and comes from many fields including sociology, evolutionary biology, neuroscience and computer science. There is however a relatively limited literature of how cooperation is supported in a network setting. This is either purely theoretical, a combination of theory and empirical analysis or experimental. 

Of the theoretical contributions several (Ali and Miller 2009, Raub and Weesie 1990, Wolitzky 2012) consider contagion based equilibria where information is restricted to individual observation. Cooperation is enforced because any defection causes a chain of further defections that eventually spreads through the entire network (if it forms one component). Under these conditions cliques are important for enforcing cooperation because they speed up punishment by reducing the time it takes for contagion to spread through the network.

In a companion paper (Ali and Miller 2016) Ali and Miller show that contagion is the only option under permanent trigger strategies because victims have no incentive to report defectors, preferring to in turn defect themselves. They then demonstrate that by adopting Multilateral Repentance strategies, where by defecting agents are punished for a limited amount of time, incentives off the equilibrium path are such that agents will report truthfully when defected on and punishment can be targeted at the perpetrator. 

This idea is developed by Lippert and Spagnolo (2011), in a paper which looks at strategic communication on a network of directed links. Outgoing links represent 'deficient' relationships where cooperation costs more than an agent benefits. These links are sustained by at least one incoming link that must be path connected to each of the out going link partners. Information is passed along these links with some finite number of transmissions per period. This allows agents to coordinate strategies to punish an individual defector, again this is only for a limited period to ensure agents have an incentive to pass on information truthfully. 

Mihm, Toth and Lang (2009), propose a very similar model but based on contagion rather than explicit communication. As in Ali and Miller (2009) they show that denser network structure  facilitates cooperation by speeding up the spread of contagion, though in this case it may be limited to only parts of the network by gatekeepers who are the sole link between two otherwise unconnected components. 

Both these model have a different focus than the one presented here in that they take into account the strategic relationship between profitable incoming and costly outgoing links and that Lippert and Spagnolo (2011) take into consideration strategic communication. They both generate similar insights in that denser networks with shorter cycles speed up punishment, either directed via information or in the form of contagion, and so support more cooperation. Both also identify gatekeeping effects where bottlenecks in the network impede cooperation. In these models sustainable patterns of interaction require the existence of cycles. Gatekeepers are those agents critical to these cycles and require specific patterns of incoming and outgoing links for the network to be sustainable. 

The conclusions of this paper are similar but arise for different reasons. Instead of assuming a pre-existing set of relationships and asking whether the network can support these, the analysis considers the effect of network structure on the level of trust supported in an environment where relationships are ex-ante uniform. 
As in Lippert and Spagnolo (2011) punishment is directed, however information transfer is limited by salience rather than time. This is essentially rules out punishment via cycles longer than those dictated by the transmission rule and consequently many agents become gatekeepers to the different Reputation Components of their Reputation Set. 
As in Ali and Miller (2009) variable stakes ensure all transactions are mutually beneficial and hence any network configuration sustainable. So here the existence of gatekeepers lowers the amount of trust others place in their reputation. Unlike other models, because agents are interested in transacting with those beyond their network, the existence of gatekeepers does not rule out significant levels of trust in transactions a gatekeeper mediates. 

This decoupling of the communication and transaction network is a crucial difference with existing literature. One paper that considers this is Mobius et al (2009) who propose an alternative mechanism of informal trust that facilitates borrowing from potentially socially distant lenders. Agents are able to trust each other via a chain of obligations that leverage the bilateral value of their links as collateral. The maximum value of loan supported is given by the sum of minimum bilateral values over independent paths between borrower and lender. In the face of default by the borrower each agent in the chain of collateralized links prefers to pay rather than lose the value of the link. This relies critically on the assumption that the threat of link severance is credible. 

This approach is fundamentally different from that of reputation, however the model I present here can be seen as an alternative mechanism to achieve the same ends. In addition by extending the model to include bilateral value, one could look at the credibility of link severance. This being motivated by what it is worth to signal your remaining partners that you are willing to sever ties in the face of default. 

The inclusion of interactions with a wider network means that the trust ranking generated by the model takes into account the degree to which your network provides you access to more distant opportunities and how much trust is present in each of these potential transactions. This relates to the literature on network formation in that how much you trust someone in an initial interaction could play an important role in how you choose to form a more long lasting connection. This is arguably particularly relevant to understanding reputations role in generating social capital. Experiments that introduce the possibility of reputation being developed find little effect under static network conditions when agents don't have the ability to ostracise REf, and it is only when agents are able to sever and form new connections that reputation significantly affects levels of cooperation REffs.

Another prominent contribution is Jackson et al (2009) who provide theoretical foundations of robust renegotiation proof networks of favour exchange in full information environment. Along with the proposal of Social Quilts as structures satisfying these requirements they show empirical evidence for 'Support' in networks of favour exchange in India. This relates to this paper which provides a different reason why we might see high levels of Support, which is the probability that two friends have a friend in common, in that it is more effective than clustering in ensuring informationally efficient networks of high value. 
	



	
\section{Model Setup}


	
	A finite set of identical, infinitely lived, risk neutral agents are represented by nodes in an undirected network $G\subset G^n$ where $G^n$ denotes the family of undirected graphs with $n$ nodes. $G=(N,E)$ where $N=\{1...n\}$ is the set of nodes and $E\subset N\text{x}N$ defines the set of edges $(i,j)$ between \textit{ordered} pairs $ij:i,j \in N$. 
	
	Each link $(i,j)$ in the network $G$ represents an information path. To capture the effect of network structure on the value of reputation alone we assume the intrinsic value of the relationship to be zero. 
	
	$\mathbf{Assumption \ 1: Full \ Network \ Information};$ Agents have complete knowledge of the network. 
	
	$\mathbf{Assumption \ 2: Zero \ Implicit \ Link \ Value};$ In absence of transactions the value of a link $(i,j)$ is zero for both $i$ and $j$.
	
	The (first order) $Neighbourhood$ of node $i$ is the set $\mathcal{N}_i=\{j\in N :(i,j) \in E\}$.
	
	The $Second \ Order \ Neighbourhood$ of $i$ is the set  $\mathcal{N}^2_i=\bigcup_{j\in \mathcal{N}_i} \mathcal{N}_j \backslash  (\mathcal{N}_i \cup {i} )$.
	
	The $n'th \ Order \ Neighbourhood$ of $i$ is the set  $\mathcal{N}^n_i=\bigcup_{j\in \mathcal{N}^{n-1}_i} \mathcal{N}_j \backslash  (\mathcal{N}^{n-1}_i \cup\mathcal{N}^{n-2}_i \cup ...\mathcal{N}_i \cup {i} )$.

To approximate the networks limited ability to provide access to transaction opportunities we make the following assumption;	

$\mathbf{Assumption \ 3: Limited \ Potential \ Partners}$; Transactions are limited to occur between agents connected by a path of length $\mathbf{z}$ or less . This defines a subnetwork of an agents \textit{Potential Partners}.

$\mathbf{Definition: Reputation \ Set}$; Limiting Potential Partners to distance $z$, $i$'s \textit{Reputation Set}, $RS_{i}=\{\mathcal{N}^z_i \cup \mathcal{N}^{z-1}_i...  \cup \mathcal{N}_i\}$  consists of all agents $i$ may potentially transact with. 

Now consider the sub-graph of the Reputation Set;

$\mathbf{Definition:  G_i};$ Let the sub-graph $G_i(N',E') \subset G$ be the graph of the subset of nodes  $N'=\{j \in N:j \in RS_i\}$ and links $E'=\{(j,k) \in E:j,k \in RS_i\}$ 

This graph $G_i$ may consist of multiple disjoint components;

$\mathbf{Definition: Reputation \ Component};$ A \textit{Reputation Component} $RC_{ij} \subseteq RS_{i}$ consists of all nodes in the connected component of $G_i$ containing $j$ such that $(i,j)\in E$. 




$\mathbf{Example:}$ Figure 1 illustrates $i$'s $RS$ and $RC$'s for $z=2$

\begin{figure}[H]
	\centering
\begin{center}
	\begin{tikzpicture}[node distance=0.9cm]
	
	\node[draw,shape=circle](n1)at (0,0){x};
	\node[draw,fill=white,shape=circle](n2)[above left of=n1]{};
	
	\node[draw,fill=white,shape=circle](n3)[above left of=n2]{};
	
	\node[draw,fill=white,shape=circle](n4)[above right of=n2]{};
	
	\node[draw=none,shape=circle](n100)[above right of=n1]{};
	\node[draw,shape=circle](n5)[below right of=n100]{i};
	\node[draw,shape=circle](n6)[below right of=n1]{y};
	\draw[-](n1)to(n2);
	\draw[-](n2)to(n3);
	\draw[-](n2)to(n4);
	\draw[-](n1)to(n5);
	\draw[-](n1)to(n6);
	\draw[-](n5)to(n6);
	
	\node[draw,fill=white,shape=circle](n7)[below left of=n1]{};
	\node[draw,fill=white,shape=circle](n8)[below left of=n7]{};
	\node[draw,fill=white,shape=circle](n9)[above left of=n7]{};
	\draw[-](n1)to(n7);
	\draw[-](n7)to(n8);
	\draw[-](n7)to(n9);
	
	\node[draw,fill=white,shape=circle](n10)[below left of=n6]{};
	
	\draw[-](n6)to(n10);

	
	\node[draw,shape=circle](n13)[above right of=n5]{k};
	
	\node[draw=none,shape=circle](n22)[above left of=n5]{$G$};
	
	\node[draw,fill=white,shape=circle](n14)[right of=n13]{};
	\node[draw,fill=white,shape=circle](n15)[above right of=n13]{};
	\draw[-](n5)to(n13);
	\draw[-](n13)to(n14);
	\draw[-](n13)to(n15);
	
	\node[draw,shape=circle](n16)[below right of=n5]{j};
	\node[draw,fill=white,shape=circle](n17) [right of=n16]{};
	\node[draw,fill=white,shape=circle](n18)[below right of=n16]{};
	\draw[-](n5)to(n16);
	\draw[-](n16)to(n17);
	\draw[-](n16)to(n18);
	\draw[-](n14)to(n17);
	
	\node[draw,fill=white,shape=circle](n19)[above right of=n14]{};
	\node[draw,fill=white,shape=circle](n20)[above right of=n17]{};	
	\node[draw,fill=white,shape=circle](n21)[below right of=n17]{};
	\draw[-](n14)to(n19);
	\draw[-](n17)to(n20);
	\draw[-](n17)to(n21);
	
	
	
	\end{tikzpicture}
\end{center}


\begin{center}
	\begin{tikzpicture}[node distance=0.9cm]
	
	\node[draw,shape=circle](n1)at (0,0){x};
	\node[draw,fill=white,shape=circle](n2)[above left of=n1]{};
	
	\node[draw=none,fill=white,shape=circle](n3)[above left of=n2]{};
	
	\node[draw=none,fill=white,shape=circle](n4)[above right of=n2]{};
	
	\node[draw=none,shape=circle](n100)[above right of=n1]{};
	\node[draw=none,shape=circle](n5)[below right of=n100]{i};
	\node[draw,shape=circle](n6)[below right of=n1]{y};
	\draw[-](n1)to(n2);
	\draw[dashed](n2)to(n3);
	\draw[dashed](n2)to(n4);
	\draw[dashed](n1)to(n5);
	\draw[-](n1)to(n6);
	\draw[dashed](n5)to(n6);
	
	\node[draw,fill=white,shape=circle](n7)[below left of=n1]{};
	\node[draw=none,fill=white,shape=circle](n8)[below left of=n7]{};
	\node[draw=none,fill=white,shape=circle](n9)[above left of=n7]{};
	\draw[-](n1)to(n7);
	\draw[dashed](n7)to(n8);
	\draw[dashed](n7)to(n9);
	
	\node[draw,fill=white,shape=circle](n10)[below left of=n6]{};

	\draw[-](n6)to(n10);

	
	\node[draw,shape=circle](n13)[above right of=n5]{k};
	
	\node[draw=none,shape=circle](n22)[above left of=n5]{$RS_i$};
	
	\node[draw,fill=white,shape=circle](n14)[right of=n13]{};
	\node[draw,fill=white,shape=circle](n15)[above right of=n13]{};
	\draw[dashed](n5)to(n13);
	\draw[-](n13)to(n14);
	\draw[-](n13)to(n15);
	
	\node[draw,shape=circle](n16)[below right of=n5]{j};
	\node[draw,fill=white,shape=circle](n17) [right of=n16]{};
	\node[draw,fill=white,shape=circle](n18)[below right of=n16]{};
	\draw[dashed](n5)to(n16);
	\draw[-](n16)to(n17);
	\draw[-](n16)to(n18);
	\draw[-](n14)to(n17);
	
	\node[draw=none,fill=white,shape=circle](n19)[above right of=n14]{};
	\node[draw=none,fill=white,shape=circle](n20)[above right of=n17]{};	
	\node[draw=none,fill=white,shape=circle](n21)[below right of=n17]{};
	\draw[dashed](n14)to(n19);
	\draw[dashed](n17)to(n20);
	\draw[dashed](n17)to(n21);
	
	
	
	\end{tikzpicture}
\end{center}

\begin{center}
	\begin{tikzpicture}[node distance=0.9cm]
	
	\node[draw,shape=circle](n1)at (0,0){x};
	\node[draw,fill=white,shape=circle](n2)[above left of=n1]{};
	
	\node[draw=none,fill=white,shape=circle](n3)[above left of=n2]{};
	
	\node[draw=none,fill=white,shape=circle](n4)[above right of=n2]{};
	
	\node[draw=none,shape=circle](n100)[above right of=n1]{};
	\node[draw=none,shape=circle](n5)[below right of=n100]{};
	\node[draw,shape=circle](n6)[below right of=n1]{y};
	\draw[-](n1)to(n2);
	
	
	\draw[-](n1)to(n6);
	
	
	\node[draw,fill=white,shape=circle](n7)[below left of=n1]{};
	\node[draw=none,fill=white,shape=circle](n8)[below left of=n7]{};
	\node[draw=none,fill=white,shape=circle](n9)[above left of=n7]{};
	\draw[-](n1)to(n7);
	
	\node[draw,fill=white,shape=circle](n10)[below left of=n6]{};

	\draw[-](n6)to(n10);
	
	
	
	\node[draw,shape=circle](n13)[above right of=n5]{k};
	
	\node[draw=none,shape=circle](n22)[above left of=n5]{$G_i$};
	
	\node[draw,fill=white,shape=circle](n14)[right of=n13]{};
	\node[draw,fill=white,shape=circle](n15)[above right of=n13]{};
	
	\draw[-](n13)to(n14);
	\draw[-](n13)to(n15);
	
	\node[draw,shape=circle](n16)[below right of=n5]{j};
	\node[draw,fill=white,shape=circle](n17) [right of=n16]{};
	\node[draw,fill=white,shape=circle](n18)[below right of=n16]{};
	
	\draw[-](n16)to(n17);
	\draw[-](n16)to(n18);
	\draw[-](n14)to(n17);
	
	\node[draw=none,fill=white,shape=circle](n19)[above right of=n14]{};
	\node[draw=none,fill=white,shape=circle](n20)[above right of=n17]{};	
	\node[draw=none,fill=white,shape=circle](n21)[below right of=n17]{};
	
	\node[draw=none,shape=circle](n101)[left of =n10]{};
	\node[draw=none,shape=circle](n23)[below right of =n101]{$RC_{ix}=RC_{iy}$};
	\node[draw=none,shape=circle](n102)[right of =n18]{};
	
	\node[draw=none,shape=circle](n24)[below left of =n102]{$RC_{ij}=RC_{ik}$};
	\end{tikzpicture}
\end{center}

	\caption{$i$'s Reputation Set and Components for $z=2$}
\end{figure}


\subsection{Time, Discounting and the Matching Process}

Agents have a continuous preference relation reflected by discounted future pay-off's and have a common discount factor $\delta \in (0,1)$. 

Time is continuous and transaction opportunities between pairs of agents within each others \textit{Reputation Sets} are governed by a Poisson Arrival process for each possible pairing. 

$\mathbf{Assumption \ 4: Uniform \ Transaction \ Frequency}:$ The Poisson arrival process has a common rate $\alpha > 0$ for all Potential Partner matchings.

\subsection{Agent Reputation}

In this section we formalise a system of Reputation which takes each agents privately observed history, translates this into Reputation via a 'Reputation Norm' and, using a Transmission Rule that regulates how reputation information is transmitted between agents, generates an information set for each agent.  This details the reputation of each of their Potential Partners, and the agents own reputation held by each of these partners at a time $t$ after history $H^t$ 

Each player $i$ observes his own private history $H^t_i$ when matched at time $t$. This consists of  a set of interactions up to but not including time $t$ such that:

$H^t_i= \bigcup_{j \in RS_i}H^t_{ij}$ and $H^t_{ij}= \bigcup_{\tau \in [0,t)}h^{\tau}_{ij}$


Where $h^{t}_{ij}=\{a_{ij},a_{ji}\}$ are the actions taken by $i$ and $j$ in their match at time $t$.

Let $H_{i}=\bigcup_{t \in [0,\infty)}H^t_{i}$ 

$\mathbf{Definition: Reputation \ Norm}$; Let the $Reputation \ Norm \ \mathcal{R}$ as applied to $i$ be a function of some subset $S$ of agents histories with $i$ at time $t$ such that:

$$\mathcal{R}_i:\bigcup_{k \in S}H^t_{ik} \rightarrow r $$

Where $r$ is an element of the set of all possible reputations an agent can hold. In general this may be a complex object containing not only information on how trustworthy an agent is, but what kinds of relationships this trust extends to. For example an agent may be considered trustworthy in dealings with his friends but not with those he is not directly connected to. In addition a reputation norm has the potential to be heterogeneous in that different sets of agents may translate actions into reputation differently.

For simplicity we make the following assumptions: 

$\mathbf{Assumption \ 5: Binary \ Reputation}$: $r \in \{g,b\}$ where $g$ implies $good$ reputation and $b$ corresponds to $bad$ reputation.

$\mathbf{Assumption \ 6: Uniform \ Norm}$; $\mathcal{R}$ is uniformly applied across all $i \in N$.



\subsubsection{Information Transmission}

Consider $i$ takes an action at time $t$ which according to the Norm $\mathcal{R}$ means his reputation will be updated to $b$. A key assumption of the model is that any update of $i's$ reputation are passed on only to  agents who find this information relevant. The intuition behind this is that information about those you know and/or are likely to interact with, is much more salient than that about those you don't know and are unlikely to meet. We assume salient information is much more likely to be remembered and shared with others who also find it salient.

In the model $i's$ Potential Partners define the set of agents who find updates on $i$'s reputation of interest. The assumption of full network information means agents can reliably pass such information along a chain of $i$'s Potential Partners with probability 1, while those for whom the information is irrelevant are not updated. 

$\mathbf{Assumption \ 7: Transmission  \ Rule}$; The Probability of Reputational information on $i$ being transmitted over the link $(j,k)$ is given by;

 \[
Pr=\left\{
\begin{array}{ll}
1 \ \ \ \ if \ j, k \in RS_i\\
\\
0 \ \ \ \ if \ j \ or \ k \notin RS_i
\end{array}
\right.
\]\\

The time frame over which information is transmitted is assumed to be much shorter than that expected between transactions so that effectively it can be taken as instantaneous. 

$\mathbf{Assumption \ 8: Truthful \ Reporting};$ Any update to $i$'s reputation is communicated truthfully and instantaneously according to the above transmission rule.

$\mathbf{Proposition \ 1}$:  Any reputation updates about $i$ stemming from an interaction with $x$ will only update all agents within the $Reputation \ Component$ of $i$ that $x$ belongs to.

$\mathbf{Proof}$: Consider $x \in RC_{ij}$. As $RC_{ij} \subset RS_i \ \forall \ j \in \mathcal{N}_i$ updates originating from $x$ will pass with probability 1 along any link that exist between agents in $G_i$.
By definition there exists a sequence of links between any $w \in RC_{ij}$ and $x$ so all such $w$ will be updated with probability 1. Alternatively there does not exist a path in between any $y \notin RC_{ij}$ hence no way for any update of $x$'s to reach $y$.\qed  


 Consequently $i$'s Reputation will effectively be independent between $i$'s Reputation Components. Hence $i$'s reputation held by all agents in $RC_{ij}$ at time $t$ is given by:

$$R^t_{ij}=\mathcal{R}:\bigcup_{k \in RC_{ij}}H^t_{ik} \rightarrow r \in \{g,b\}$$



Let the reputation of $i$ held by $k$ at time $t$ be given by;

 $$r^t_{ik}=R^t_{ij} \ \forall \ k \in RC_{ij}$$

By definition this reflects $i$'s history of actions in  transactions with any agent $k \in RC_{ij}$ up to but not including time $t$.


$\mathbf{Definition: Information \ Set}$; An agents $Information \ Set$  at time $t$ consists of the information about Reputations of all agents in their Reputation Set ($r^t_{ji}$), and about their own Reputation held by these agents ($r^t_{ij}$) such that:
 
 $$I^t_i=\{(r^t_{ij},r^t_{ji}) : j \ \in RS_i\}$$
 
and 
$$I_{i}=\bigcup_{t \in [0,\infty)}I^t_{i} $$


Hence, depending on how the Reputation Norm translates action into reputation, each agent $i$ at time $t$ can infer a partial history of actions taken by each agent $j$ within their Reputation Set. This history is partial in that it only includes actions taken by $j$ in transactions with partners in the Reputation Component of $j$ to which $i$ belongs.

\subsection{The Constituent Game}

When agents $i$ and $j$ are matched at time $t$ they engage in a two stage game at that time. 

$\mathbf{Stage \ 1:Stake \ Proposal \ and \ Acceptance }$; An agent is randomly selected to propose stakes $\mathcal{V}^t_{ij} \ or \ \mathcal{V}^t_{ji} \in \mathbb{R}^+$. The proposal is made and the other agent chooses $s^t_{i/j} \in S$  where $S \equiv \{ Accept,Reject\}$ with regard to the proposed stakes. If the stakes are rejected the game stops there and all payoffs are zero, otherwise the game proceeds with Stage 2 at Accepted Stakes $v^t_{ij}=\mathcal{V}^t_{ij} \ or \ \mathcal{V}^t_{ji}$.

 
  
$\mathbf{Stage \ 2:Prisoners \ Dilemma}$; Players engage in a Prisoners Dilemma, $i$ choosing an actions $a^t_{ij}$ and $j$ choosing $a^t_{ji}$ from $A \equiv \{C,D\}$, where $C$ corresponds to cooperation and $D$ with defection. The payoffs  are determined by the stakes accepted in $\mathbf{Stage 1}$ such that:

\begin{center}
	\begin{tabular}{ c c c c  }
		& & \ \ \ \ \ \ \ \ \ \ \ \ \ Agent j\\ \\
		& & C & D \\ 
	Agent i \ \	& C & ($ \ \ v^t_{ij} \ \ , \ \ v^t_{ij} \ \ $) & (-$X(v^t_{ij})$ ,$D(v^t_{ij})$) \\  \\
	&	D & ($D(v^t_{ij})$, -$X(v^t_{ij})$)	 & (  0  ,  0  ) \\
		
	\end{tabular}
\end{center}
Where  $D(v)= \Tau(v)+v$ with both $\Tau(v)>0$ and $X(v)\geq 0\ \forall \ v>0$. In addition $\Tau (0)=0$ and $X(0)= 0$ so that at zero stakes there is effectively no transaction.

$\mathbf{Assumption \ 9}:$ $\Tau(v)$ is strictly increasing and strictly convex with  $\Tau'(0)<\alpha$ and $\mathit{lim}_{v\to\infty} \Tau'(v) \rightarrow \infty$. \\


$\mathbf{Stage \ Game \ Nash \ Equilibrium}:$ As a Prisoners Dilemma, $\mathbf{Stage 2}$ of the Constituent game has a unique Nash Equilibrium for any positive selected stakes $v_{ij} >0$ where both players defect. 

Backward induction implies any $\mathbf{Stage 1}$ strategy resulting in positive accepted stakes is irrelevant to the outcome in $\mathbf{Stage 3}$, so that there are a continuum of Nash equilibrium strategies where any positive stakes are proposed, proposals are accepted and both players defect.

When either the proposed stakes are zero or the proposal is rejected then  actions in $\mathbf{Stage 2}$ become irrelevant. So there exists another set of equilibria where either the proposal is zero or is rejected and $\mathbf{Stage 2}$ action is either $C$ or $D$.

All Constituent game Nash equilibrium payoffs are zero. 

\subsection{Bilateral Strategies without Reputation} 

$\mathbf{Definition:}$ A $Bilateral \ Srategy, \ \sigma^{bl}$  of any agent $i$ transacting with $j \in RS_i$ at time $t$ is given by the triplet $(\sigma^{P}_i,\sigma^{S}_i,\sigma^A_i)$ where;

$\sigma^{P}_i:H^t_i \rightarrow \mathbb{R}^+$   \ \ is $i$'s Stake Proposal strategy

$\sigma^{S}_i: H^t_i \times \mathbb{R}^+ \rightarrow \mathcal{S}$  \ \ is $i$'s Stake Acceptance strategy

$\sigma^A_i: \mathbb{R}^+  \rightarrow A$  \ \   is $i$'s Action strategy\\

Because each player is effectively playing an infinitely repeated game with every agent in their Reputation Set, Nash Folk Theorems apply. 

Folk Theorems imply that mutual cooperation can be achieved for any stakes so long as the players are sufficiently patient. However for a given $\delta$ the maximum cooperative stakes can be achieved using a (grim) trigger strategy where both agents in a match cooperate as long as neither have defected against the other, but revert to playing a stage game Nash equilibria forever after if either player defects.

Under this strategy cooperation requires the extra gain from $i$'s defection today be less than or equal to the loss of discounted expected value from $i$'s transactions with $j$ in the future. Hence both $i$ and $j$'s incentive constraint is given by;

$$\Tau(v_{ij}) \leq  \int_{0}^{\infty} e^{-(1-\delta)t} \alpha v_{ij}dt$$

Where $\alpha$ is the common rate of the Poisson process governing matching and $\delta$ is a common discount rate.


$\mathbf{Assumption \ 10}$: Agents cooperate when they are indifferent between cooperation and defection. 

This assumption is necessary for the existence of a Nash equilibrium.\\



To implement this trigger strategy each agent $i$ when matched with $j \in RS_i$ at time $t$, adopts the following Bilateral Strategy, $\sigma^{tr}_i=(\sigma^P_i,\sigma^S_i,\sigma^A_i)$ such that the stake proposal strategy is given by:

\[
\sigma^{P}_i:\mathcal{V}^t_{ij}=\left\{
\begin{array}{ll}
v^{bl} \ \ \ \ if \  a^{\tau}_{ji}=C \ \ \forall \  H^{\tau}_{ij} , \ \tau \leq t\\
\\
0 \ \ \ \ Otherwise
\end{array}
\right.
\]
Where $v^{bl}$ is the maximum bilateral stakes compatible with cooperation determined by the binding incentive constraint:

$$\Tau(v^{bl}) = \int_{0}^{\infty} e^{-(1-\delta)t} \alpha v^{bl}dt =\frac{\alpha}{(1-\delta)}v^{bl}$$

The stake acceptance strategy is;

\[
\sigma^{S}_i:s_i=\left\{
\begin{array}{ll}
Accept \ \ \ \ if \  \mathcal{V}^t_{ji}\leq v_{bl}  \\
\\
Reject \ \ \ \ Otherwise
\end{array}
\right.
\]

and the agents action strategy in stage 2 is;

\[
\sigma^A_i:a_{ij}=\left\{
\begin{array}{ll}
C \ \ \ \ if \  v^t_{ij}\leq v^{bl}  \\
\\
D \ \ \ \ Otherwise
\end{array}
\right.
\]




$\sigma^{tr}_i$ is a best response to itself and because all matches are symmetric the strategy profile $\sigma =\sigma^{tr}_i \ \forall \ i \in N$ and $ t \in [0,\infty)$ constitutes a Nash equilibrium where all agents transact with their Potential Partners at stakes $v^{bl}$.

Because the trigger strategy implements the worst punishment for defection that is possible $v^{bl}$ is the maximum stakes that any match can achieve without using Reputation.  

	


\subsection{Reputation Strategies }

 

$\mathbf{Definition:}$ a $\textit{Reputation Strategy}$ for agent $i$ is a function $\sigma_i = (\sigma^P_i, \sigma^S_i, \sigma^A_i)$ such that:
$$\sigma^P_i: I^t_i \rightarrow \mathbb{R}^+ \ \forall \ t \in [0,\infty) $$ is $i$'s stake proposal strategy that dictates what stakes $i$ is prepared to transact at given their Information Set at every time $t$.
 
$$\sigma^S_i: I^t_i \times \mathbb{R}^+ \rightarrow S \ \forall \ t \in [0,\infty) $$ 
is $i$'s stake acceptance strategy, and

$$\sigma^A_i: I^t_i\times \mathbb{R}^+ \rightarrow  A \ \forall \ t \in [0,\infty) $$ 

is their action strategy detailing their actions if stage 2 is reached given the accepted stakes and their Information Set. 

Linking agents strategic decisions with the reputational information they have in their Information Set depends explicitly on the Reputation Norm in operation, i.e. how an agents actions are translated into a reputation for that individual. 

In addition to reputation being binary and the norm being uniformly applied we assume a particular Reputation Norm given by:

\[
\mathcal{R}^*:R^t_{ij}=\left\{
\begin{array}{ll}
b \ \ \ \ if \  a_{ik}=D \ for \ any \ h^\tau_{ik} \in \bigcup_{k \in RC_{ij}} H^t_{ik}, \ \tau \in [0,t) \\
\\
g \ \ \ \ Otherwise
\end{array}
\right.
\]

$\mathbf{Assumption \ 11: \mathcal{R}=\mathcal{R}^*} \ \forall \ i \in N \ and \ t \in [0,\infty) $

$\mathcal{R}^*$ essentially implies that if $i$ defects on any agent in one of his Reputation Components his reputation within that component is permanently updated to $b$.  

\subsubsection{Trigger Strategies using Reputation}

Given $\mathcal{R}^*$ each agent can implement the following Reputation strategy $\sigma^{\mathcal{R}^*}_i$ such that for each $ij$ match at time $t$;
 

\[
\sigma^{\mathcal{R}^*}_{ij}= (\sigma^P_{ij},\sigma^S_{ij}, \sigma^A_{ij})=\left\{
\begin{array}{ll}
(0,Reject,C) \ \ \ \ if \  r^t_{ji}=b \ \textit{or} \ r^t_{ij}=b \\
\\
(\mathcal{V}_{ij},Accept,C) \ \ \ \ if \  r^t_{ji}=g  \ \textit{and} \  r^t_{ij}=g \ \textit{and} \ \mathcal{V}_{ji}\leq \mathcal{V}_{ij} \\
\end{array}
\right.
\]

This combination of Reputation Norm and Strategy is analogous to a Trigger Strategy in infinitely repeated games where agents punish defectors by min-maxing them forever. \footnote{Note that this is the most severe punishment and that a continuum of equilibrium strategies exist where agents play stakes $v \in [0,v^bl]$ when matched with an agent of bad reputation. Because Reputation is binary no stakes above $v^{bl}$ constitute a possible equilibrium.}


\subsection{Equilibrium}

Consider the strategy profile $\sigma:\sigma_i =  \sigma^{\mathcal{R}^*}_i \ \forall \ i\in N$. For this to constitute a Nash equilibrium where all agents cooperate on the equilibrium path the following conditions must hold;

$\mathbf{Initial \ Condition:}$ At $t=0$ all agents have good reputations,  $r^0_{ij}=g \ \forall \ i \in N, \ j \in RS_i$ 

This condition is essentially assumes the network has reached a steady state after the process of adjustment the network undergoes following a defection.  

$\mathbf{Incentive \ Constraint:}$ The expected stakes for each match must be such that the incentive constraint for cooperation must be satisfied for every $i$ transacting with $j \in RC_{ix}$ at stakes $v_{ij}$ at some time $t$:

$$v_{ij} + \Tau(v_{ij}) + \sum_{k \in RS_{i}\backslash RC_{ix}} \int_{0}^{\infty}e^{-(1-\delta)t}\alpha v'_{ik}dt\leq v_{ij} + \sum_{k \in RS_{i}} \int_{0}^{\infty}e^{-(1-\delta)t}\alpha v_{ik}dt$$

That is the value of defection today is at least outweighed by the loss of expected future value of the reputation component the defection took place in.

In general $v'_{ik} \neq v_{ik}$ and to solve for $v_{ij}$ we would need agents to form expectations about the exact sequence in which transaction opportunities arrive in the future. This is related to the adjustment process the network undergoes after a defection. It is clear this process takes time and adds unnecessary complexity. To avoid this complication we make the following assumption;

$\mathbf{Assumption \ 12: Bounded \ Rationality}$: Agents are $Rationally \ Bounded$ in that they assume that the continuation payoffs/stakes are independent between Reputation Components. Hence  $\mathbb{E}(v'_{ik}) =\mathbb{E}(v_{ik})$ for $k \in RS_{i}\backslash RC_{ix}$ after a defection by $i$ in $RC_{ix}$

This means that we can ignore the adjustment process in calculating the equilibrium. A justification for this assumption and an informal outline of the process can be found in Appendix B.

Under this assumption $v'_{ik} = v_{ik}$ and the incentive constraint simplifies to;
$$ \Tau(v_{ij})\leq \sum_{k \in RC_{jx}} \frac{\alpha }{(1-\delta)} v_{jk}$$

For agent $i \in RC_{jx}$ to be best responding to $\sigma^\mathcal{R}_{-i}$  his stake proposal strategy $\sigma^S_{ij}$ should be such that this incentive constraint is binding for $j$. For any greater proposal accepted by $j$, $i$ would expect $j$ to defect, while any lower proposal does not maximise $i$'s expected value from the transaction. Hence $i$'s best response stake proposal $\mathcal{V}^*_{ij}$ solves;

$$ \Tau(\mathcal{V}^*_{ij})= \sum_{k \in RC_{jx}} \frac{\alpha }{(1-\delta)} v_{jk}$$



Similarly $j \in RC_{iy}$ such that  $ x=i \Leftrightarrow y=j$ otherwise $ x=y $ (to take into account when $j$ is linked to $i$), has the best response stake proposal $\mathcal{V}^*_{ji}$ solving;

$$ \Tau(\mathcal{V}^*_{ji})= \sum_{k \in RC_{iy}} \frac{\alpha }{(1-\delta)} v_{ik}$$


\subsubsection{Selected Stakes}

Because $\mathcal{V}^*_{ij}$ defines the maximum stakes that $i$ will offer or accept, proposed stakes will be $\mathcal{V}_{ij}=\mathcal{V}_{ji}=min(\mathcal{V}^*_{ij},\mathcal{V}^*_{ji})$. And these will always be accepted. Hence $ v_{ji}=v_{ij}=min(\mathcal{V}^*_{ij},\mathcal{V}^*_{ji})$.


$\mathbf{Example:}$ Consider $i$ is matched with $l$ in the network from Figure 1. With $z=2$ so that Potential Partners are limited to $\mathcal{N}^1 \bigcup \mathcal{N}^2$. 
 
\begin{figure}[H]
	\centering
	\begin{center}
		\begin{tikzpicture}[node distance=0.95cm]
		
		\node[draw,shape=circle](n1)at (0,0){x};
		\node[draw,fill=white,shape=circle](n2)[above left of=n1]{};
		
		\node[draw,fill=white,shape=circle](n3)[above left of=n2]{};
		
		\node[draw,fill=white,shape=circle](n4)[above right of=n2]{};
		
		\node[draw=none,shape=circle](n100)[above right of=n1]{};
		\node[draw,shape=circle](n5)[below right of=n100]{i};
		\node[draw,shape=circle](n6)[below right of=n1]{y};
		\draw[-](n1)to(n2);
		\draw[-](n2)to(n3);
		\draw[-](n2)to(n4);
		\draw[-](n1)to(n5);
		\draw[-](n1)to(n6);
		\draw[-](n5)to(n6);
		
		\node[draw,fill=white,shape=circle](n7)[below left of=n1]{l};
		\node[draw,fill=white,shape=circle](n8)[below left of=n7]{};
		\node[draw,fill=white,shape=circle](n9)[above left of=n7]{};
		\draw[-](n1)to(n7);
		\draw[-](n7)to(n8);
		\draw[-](n7)to(n9);
		
		\node[draw,fill=white,shape=circle](n10)[below left of=n6]{};
		
		\draw[-](n6)to(n10);
		
		
		\node[draw,shape=circle](n13)[above right of=n5]{k};
		
		\node[draw=none,shape=circle](n22)[above left of=n5]{$G$};
		
		\node[draw,fill=white,shape=circle](n14)[right of=n13]{};
		\node[draw,fill=white,shape=circle](n15)[above right of=n13]{};
		\draw[-](n5)to(n13);
		\draw[-](n13)to(n14);
		\draw[-](n13)to(n15);
		
		\node[draw,shape=circle](n16)[below right of=n5]{j};
		\node[draw,fill=white,shape=circle](n17) [right of=n16]{};
		\node[draw,fill=white,shape=circle](n18)[below right of=n16]{};
		\draw[-](n5)to(n16);
		\draw[-](n16)to(n17);
		\draw[-](n16)to(n18);
		\draw[-](n14)to(n17);
		
		\node[draw,fill=white,shape=circle](n19)[above right of=n14]{};
		\node[draw,fill=white,shape=circle](n20)[above right of=n17]{};	
		\node[draw,fill=white,shape=circle](n21)[below right of=n17]{};
		\draw[-](n14)to(n19);
		\draw[-](n17)to(n20);
		\draw[-](n17)to(n21);
		
		
		
		\end{tikzpicture}
	\end{center}

	\begin{center}
		\begin{tikzpicture}[node distance=0.95cm]
		
		\node[draw,shape=circle](n1)at (0,0){x};
		\node[draw,fill=white,shape=circle](n2)[above left of=n1]{};
		
		\node[draw=none,fill=white,shape=circle](n3)[above left of=n2]{};
		
		\node[draw=none,fill=white,shape=circle](n4)[above right of=n2]{};
		
		\node[draw=none,shape=circle](n100)[above right of=n1]{};
		\node[draw,shape=circle](n5)[below right of=n100]{i};
		\node[draw,shape=circle](n6)[below right of=n1]{y};
		\draw[-](n1)to(n2);
	
		\draw[-](n1)to(n5);
		\draw[-](n1)to(n6);
		\draw[-](n5)to(n6);
		
		\node[draw=none,fill=white,shape=circle](n7)[below left of=n1]{l};
		\node[draw=none,fill=white,shape=circle](n8)[below left of=n7]{};
		\node[draw=none,fill=white,shape=circle](n9)[above left of=n7]{};
		\draw[dashed](n1)to(n7);
	
		
		
		
	
		
		
		
		
		\node[draw=none,shape=circle](n22)[above left of=n5]{$RC_{lx}$};
		
	
		
		
		
	
		
		
		\end{tikzpicture}
	\end{center}
\end{figure}	

\begin{figure}[H]
\centering	
		\begin{center}
		\begin{tikzpicture}[node distance=0.95cm]
		
		\node[draw,shape=circle](n1)at (0,0){x};
		\node[draw,fill=white,shape=circle](n2)[above left of=n1]{};
		
		\node[draw=none,fill=white,shape=circle](n3)[above left of=n2]{};
		
		\node[draw=none,fill=white,shape=circle](n4)[above right of=n2]{};
		
		\node[draw=none,shape=circle](n100)[above right of=n1]{};
		\node[draw=none,shape=circle](n5)[below right of=n100]{i};
		\node[draw,shape=circle](n6)[below right of=n1]{y};
		\draw[-](n1)to(n2);
		\draw[dashed](n1)to(n5);
		\draw[dashed](n6)to(n5);
		\draw[-](n1)to(n6);
		
		
		\node[draw,fill=white,shape=circle](n7)[below left of=n1]{l};
		\node[draw=none,fill=white,shape=circle](n8)[below left of=n7]{};
		\node[draw=none,fill=white,shape=circle](n9)[above left of=n7]{};
		\draw[-](n1)to(n7);
		
		\node[draw,fill=white,shape=circle](n10)[below left of=n6]{};
		
		\draw[-](n6)to(n10);
		
		
		
	
		
		\node[draw=none,shape=circle](n22)[above left of=n5]{$RC_{ix}$};
		
	
		
	
		
		
	
		\node[draw=none,shape=circle](n101)[left of =n10]{};
		
		\node[draw=none,shape=circle](n102)[right of =n18]{};
		
	
		\end{tikzpicture}
	\end{center}
	
	\caption{Relevant Reputation Components for $i$ transacting with $l$, $z=2$}
\end{figure}

When matched with $l$, $i$ makes his stake proposal based on the sum of discounted future values $l$ expects from transactions with Potential Partners in his Reputation Component $RC_{lx}$. Similarly $l$'s proposal is based on $i$'s valuation of $RC_{ix}$. Note that while $|RC_{lx}|<|RC_{ix}|$, under certain network architectures the sum of the valuations in each of these components may mean $\mathcal{V}^*_{il}>\mathcal{V}^*_{li}$ so it's possible that $i$'s trustworthiness is what limits the stakes of their transaction.  \\

$\mathbf{Proposition \ 2}$: Given all agents initially hold good reputations, there exists a Nash Equilibrium, where all agents cooperate on the equilibrium path, consisting of the triplet $(\mathcal{R}^*, \sigma^{\mathcal{R}^*}, \mathcal{\mathbf{v}})$ where $\mathbf{v}$ is a unique set of $Consistent \ Valuations$ $\{v_{ij}:  i \in N, j \in RS_i\}$ such that  $v_{ij} =v_{ji}= min(\mathcal{V}^*_{ij},\mathcal{V}^*_{ji})$ for the set of all possible matches.

$\mathbf{Proof}$: Sketch: By showing that $f:R^n \rightarrow R^n: f_{ij}=\Tau^{-1}[min(\mathcal{V}^*_{ij},\mathcal{V}^*_{ji})]$ is a continuous function, (rather than a correspondence) then show that this function is a contraction above a threshold region. Because of the restrictions we place on $\Tau$ the solution must be above this threshold. So by the contraction theorem a unique fixed point must exist. 


\subsubsection{Algorithm 1; Sequential Valuation Algorithm (SVA)}
Consider the set of agents with the minimum $|RC_{ij}|$ in the entire network $G$. Because each of these agents has an isolated information component of size $|RC_{ij}|$ in terms of potential partners, this sets the maximum value for every transaction between $i$ and any agent in this component to the same level. 


$\mathbf{Step \ 1:}$ Construct the following sets;

$rc_1 =\{ij:|RC_{ij}|= min(|RC_{xy}| \ \forall \ xy \in E)\}$

This gives all the Reputation Components index's $ij$ of agents $i$ connected to $j$ with the minimum number of agents. The size of $i$'s component must limit every possible transaction between $i$ and those partners in it. 

$s_1=\{iz: z\in RC_{ij}  \  \forall \ ij \in rc_1,\}$ 

This is the set of all potential matches $i$ to $z$ in all the minimal $RC_{ij}'s$

Let	$v_{iz}=A^*_{ij} \ \ \forall \ iz\in s_1$ where $A^*_{ij}$ solves 
$$\Tau(A^*_{ij}) = \frac{\alpha}{1-\delta} |RC_{ij}|A^*_{ij} \ \  \forall \ ij \in rc_1$$ 

This determines the value of all the matches in $s_1$.

$v_1=\{v_{iz}:iz\in s_1\}$ and 	$\mathbb{V}_1=v_1$ 

Where 	$\mathbb{V}_1$ is the set of all values that have been determined at $t=1$.

$\mathbb{S}_1=s_1$ 


$\mathbb{RC}_1=rc_1$ \\

Similarly $\mathbb{S}_1$ and $\mathbb{RC}_1$ are the set of all valued matches and fully valued Reputation Components.

At this point we have valued the smallest reputation component. These values must be included in the calculations of larger components because proposed stakes are determined by the minimum of two maximal stakes. 

$\mathbf{Step \ t+1:}$

Let $\mathbb{P}_{xy}=\{zx:z \in RC_{xy} \}$  

This gives all the potential partner pairings with $x$ from any $RC_{xy}$ 

$rc_{t+1}=\{ij:A^*_{ij} = min (A_{xy}) \ \forall \ xy \in E\backslash \mathbb{RC}_t\}$ where $A_{xy}$ solves;

$$\Tau(A_{xy}) = \frac{\alpha}{1-\delta} \big[ (|RC_{xy}|-|\mathbb{P}_{xy} \cap \mathbb{S}_t|)A_{xy} + \sum_{zx\in \mathbb{P}_{xy} \cap \mathbb{S}_t } v_{zx}\big]$$

Where $\mathbb{P}_{xy} \cap \mathbb{S}_t$ gives all the pairings that have already been evaluated in $RC_{xy}$. The minimum values $A^*_{ij}$ here will be the remaining values for pairings between $i$ and those not already valued in $RC_{ij}$

Then
$s_{t+1}=\{iz: z\in RC_{ij} \ \forall \ ij \in rc_{t+1} \ and \ zi \notin \mathbb{S}_{t}\}$ is the set of newly valued pairings.

Set these values  $v_{iz}=A^*_{ij} \ \forall \ iz \in s_{t+1}$ 

$v_{t+1}=\{v_{iz} \ \forall  \ iz \in s_{t+1}\}$ 

and  $\mathbb{V}_{t+1}=\mathbb{V}_{t} \cup v_{t+1}$

$\mathbb{S}_{t+1}=\mathbb{S}_{t} \cup s_{t+1}$ 

$\mathbb{RC}_{t+1}=\mathbb{RC}_{t} \cup rc_{t+1}$\\


Iterate until $\mathbb{RC}_{t+1}=E $ so that the components associated with all edges have been evaluated.\\


$\mathbf{Example:}$ For simplicity we evaluate a sub-network of that shown in Figure 1. Again we limit Potential Partners to friends of friends, i.e. $z=2$.

	

\begin{figure}[H]
	\centering
	\begin{center}
		\begin{tikzpicture}[node distance=1.9cm]
		
		\node[draw,shape=circle](n1)at (0,0){3};
		\node[draw,fill=white,shape=circle](n2)[above left of=n1]{8};
		
		
		
		\node[draw=none,shape=circle](n100)[above right of=n1]{};
		\node[draw,shape=circle](n5)[below right of=n100]{4};
		\node[draw,shape=circle](n6)[below right of=n1]{2};
		\draw[-](n1)to(n2);
		
		\draw[-](n1)to(n5);
		\draw[-](n1)to(n6);
		\draw[-](n5)to(n6);
		
		\node[draw,fill=white,shape=circle](n7)[below left of=n1]{7};
		
		\draw[-](n1)to(n7);
		
		
		\node[draw,fill=white,shape=circle](n10)[below left of=n6]{1};
		
		\draw[-](n6)to(n10);
		
		
		\node[draw,shape=circle](n13)[above right of=n5]{6};
		
		\node[draw=none,shape=circle](n22)[above left of=n5]{};
		
		
		\draw[-](n5)to(n13);
		
		
		
		\node[draw,shape=circle](n16)[below right of=n5]{5};
		
		\draw[-](n5)to(n16);
		
		
		
		
		
		
		\end{tikzpicture}
	\end{center}
	\caption{Network to be Evaluated}
\end{figure}



In Figure 3 the nodes are numbered $1$ through $8$. There are 8 edges and hence 16 Reputation Components some of which are equivalent.

We assume $\Tau(v) =v^2$.

Tables 1,2 and 3 run through the SVA for this network. 
In table 1 the first column lists the Reputation components which are indexed by an ordered pair. This corresponds to the directed edge such that $RC_{ij}$, identified by the edge $(ij)$ is all those Potential Partners that would be informed of $i$'s defection on $j$ or any friend of $j$'s. 

The second column list the number of Potential Partners in each Reputation Component. 

The third column lists the possible potential matches $(x,y)$ that exist between  $i$ and agents within $RC_{ij}$. 

At the first iteration we take the minimum $|RC_{ij}|$'s and solve the incentive constraint $v1: v1^2=\frac{\alpha}{1-\delta} v1 \implies v1=\frac{\alpha}{1-\delta}$ Let $\gamma=\frac{\alpha}{1-\delta}$  so $v1=\gamma$. These are the values highlighted in blue and take the place of each $(i,k)$ matching which this value solves for. Given these we can replace the corresponding $(k,i)$ matchings with the same value. These substitutions are highlighted in red.

\begin{table}[H]
	\caption{Potential Partners in each RC and Iteration 1}
	
	\centering
	\begin{tabular}{ c c c c  }
		RC(i,j)	&	|RC(ij)|	&	PP in RC(i,j)	&	Iteration 1\\
		(1,2)	&	3	&	(1,2)(1,4)(1,3)	&	\textcolor{red}{(v1)}(1,4)(1,3)\\
		(2,1)	&	1	&	(2,1)	&	\textcolor{blue}{(v1)}\\
		(2,4)=(2,3)	&	6	&	(2,4)(2,3)(2,5)(2,6)(2,7)(2,8)	&	(2,4)(2,3)(2,5)(2,6)(2,7)(2,8)\\
		(3,2)=(3,4)	&	5	&	(3,2)(3,1)(3,4)(3,5)(3,6)	&	(3,2)(3,1)(3,4)(3,5)(3,6)\\
		(3,7)	&	1	&	(3,7)	&	\textcolor{blue}{(v1)}\\
		(3,8)	&	1	&	(3,8)	&	\textcolor{blue}{(v1)}\\
		(4,2)=(4,3)	&	5	&	(4,3)(4,1)(4,2)(4,7)(4,8)	&	(4,3)(4,1)(4,2)(4,7)(4,8)\\
		(4,5)	&	1	&	(4,5)	&	\textcolor{blue}{(v1)}\\
		(4,6)	&	1	&	(4,6)	&	\textcolor{blue}{(v1)}\\
		(5,4)	&	4	&	(5,4)(5,2)(5,3)(5,6)	&	\textcolor{red}{(v1)}(5,2)(5,3)(5,6)\\
		(6,4)	&	4	&	(6,4)(6,2)(6,3)(6,5)	&	\textcolor{red}{(v1)}(6,2)(6,3)(6,5)\\
		(7,3)	&	4	&	(7,3)(7,2)(7,4)(7,8)	&	\textcolor{red}{(v1)}(7,2)(7,4)(7,8)\\
		(8,3)	&	4	&	(8,3)(8,4)(8,2)(8,7)	&	\textcolor{red}{(v1)}(8,4)(8,2)(8,7)\\
		
		
	\end{tabular}
\end{table}




The second iteration takes the next lowest valued component, which in this case is $RC_{12}$ and solve for all the remaining values within it for $v2: v2=\frac{\alpha}{1-\delta}(2v2+v1) \implies v2=\gamma(1+\sqrt{2})$ (note we ignore the negative root). Again the solved for values are in blue and replace the appropriate Potential Partner matchings. The red values are where these relationships contribute value to another component. 

From the values computed in iteration 2 we can infer that $RC_{5,4},RC_{6,4},RC_{7,3}$ and $RC_{8,3}$ are the next smallest valued components and all remaining values in these are solved for such that  $v3=\frac{\alpha}{1-\delta}(3v3+v1)\implies v3=\gamma(\frac{3}{2}+\sqrt{3})$.
$v3$ then replaces the reciprocal pairings in other higher valued components. 

\begin{table}[H]
	\caption{Iteration 2 and 3}
	
	\begin{tabular}{ c c c c  }
		RC(i,j)	&	|RC(ij)|	&	Iteration 2	&	Iteration 3\\
		(1,2)	&	3	&	(v1)\textcolor{blue}{(v2)}\textcolor{blue}{(v2)}	&	(v1)(v2)(v2)\\
		(2,1)	&	1	&	(v1)	&	(v1)\\
		(2,4)=(2,3)	&	6	&	(2,4)(2,3)(2,5)(2,6)(2,7)(2,8)	&	(2,4)(2,3)\textcolor{red}{(v3)}\textcolor{red}{(v3)}\textcolor{red}{(v3)}\textcolor{red}{(v3)}\\
		(3,2)=(3,4)	&	5	&	(3,2)\textcolor{red}{(v2)}(3,4)(3,5)(3,6)	&	(3,2)(v2)(3,4)\textcolor{red}{(v3)}\textcolor{red}{(v3)}\\
		(3,7)	&	1	&	(v1)	&	(v1)\\
		(3,8)	&	1	&	(v1)	&	(v1)\\
		(4,2)=(4,3)	&	5	&	(4,3)\textcolor{red}{(v2)}(4,2)(4,7)(4,8)	&	(4,3)(v2)(4,2)\textcolor{red}{(v3)}\textcolor{red}{(v3)}\\
		(4,5)	&	1	&	(v1)	&	(v1)\\
		(4,6)	&	1	&	(v1)	&	(v1)\\\
		(5,4)	&	4	&	(v1)(5,2)(5,3)(5,6)	&	(v1)\textcolor{blue}{(v3)}\textcolor{blue}{(v3)}\textcolor{blue}{(v3)}\\
		(6,4)	&	4	&	(v1)(6,2)(6,3)(6,5)	&	(v1)\textcolor{blue}{(v3)}\textcolor{blue}{(v3)}\textcolor{blue}{(v3)}\\
		(7,3)	&	4	&	(v1)(7,2)(7,4)(7,8)	&	(v1)\textcolor{blue}{(v3)}\textcolor{blue}{(v3)}\textcolor{blue}{(v3)}\\
		(8,3)	&	4	&	(v1)(8,4)(8,2)(8,7)	&	(v1)\textcolor{blue}{(v3)}\textcolor{blue}{(v3)}\textcolor{blue}{(v3)}\\
		
	\end{tabular}
	\label{Tab:Tcr}
\end{table}

In Table 3 the final iteration takes the next lowest valued components $RC_{3,2}=RC_{3,4}$ and $RC_{4,2}=RC_{4,3}$ and solves for $v4$ such that $v4^2=\frac{\alpha}{1-\delta}(2A4+2v3+v2) \implies v4=\gamma (1+\sqrt{5+2\sqrt{3}+\sqrt{2}})$. These values then account for all the remaining reciprocal Potential Partner values in  $RC_{2,4}=RC_{2,3}$ so that every possible transaction value has been solved for.

\begin{table}[H]
	\caption{Iteration 4}
	\begin{tabular}{ c c c c  }
		RC(I,j)	&	|RC(ij)|	&	Iteration4\\
		(1,2)	&	3	&	(v1)(v2)(v2)\\
		(2,1)	&	1	&	(v1)\\
		(2,4)=(2,3)	&	6	&	\textcolor{red}{(v4)}\textcolor{red}{(v4)}(v3)(v3)(v3)(v3)\\
		(3,2)=(3,4)	&	5	&	\textcolor{blue}{(v4)}(v2)\textcolor{blue}{(v4)}(v3)(v3)\\
		(3,7)	&	1	&	(v1)\\
		(3,8)	&	1	&	(v1)\\
		(4,2)=(4,3)	&	5	&	\textcolor{blue}{(v4)}(v2)\textcolor{blue}{(v4)}(v3)(v3)\\
		(4,5)	&	1	&	(v1)\\
		(4,6)	&	1	&	(v1)\\
		(5,4)	&	4	&	(v1)(v3)(v3)(v3)\\
		(6,4)	&	4	&	(v1)(v3)(v3)(v3)\\
		(7,3)	&	4	&	(v1)(v3)(v3)(v3)\\
		(8,3)	&	4	&	(v1)(v3)(v3)(v3)\\
		
		
	\end{tabular}
\end{table}
Note that the agent with the highest valued Reputation is $2$ as his lower number of connections lowers the value of $3$ and $4$'s reputations.
