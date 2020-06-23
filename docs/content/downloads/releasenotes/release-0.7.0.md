---
title: "0.7.0"
menu:
  main:
    parent: "ReleaseNotes"
    weight: 70
---

* [Release log](https://projects.eclipse.org/projects/modeling.elk/releases/0.7.0)
* [Documentation](https://download.eclipse.org/elk/updates/releases/0.6.1/elk-0.7.0-docs.zip)
* [Update site](https://download.eclipse.org/elk/updates/releases/0.7.0/)
* [Zipped update site](https://download.eclipse.org/elk/updates/releases/0.7.0/elk-0.7.0.zip) (for offline use)
* [Maven central](https://repo.maven.apache.org/maven2/org/eclipse/elk/) (for building pure Java projects that use ELK)



## Details

This is a major release which comes with quite a number of changes. Some of those are breaking changes, either in the usual API-breaking sense or in the sense that default layouts might look different. Those [issues](https://github.com/eclipse/elk/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%22Release+0.7.0%22+label%3Abreaking) and [pull requests](https://github.com/eclipse/elk/pulls?q=is%3Apr+is%3Aclosed+milestone%3A%22Release+0.7.0%22+label%3Abreaking) are now labeled with "breaking" to make such changes easier to spot.

Here's a list of the most noteworthy changes. Head over to GitHub for [the full list](https://github.com/eclipse/elk/milestone/12?closed=1).


### New Features and Enhancements

* [#362](https://github.com/eclipse/elk/issues/362), [#613](https://github.com/eclipse/elk/pull/613): Most importantly, we finally have a new logo which appears on all of our websites. Joy!
* [#105](https://github.com/eclipse/elk/issues/105), [#598](https://github.com/eclipse/elk/pull/598): Configuring spacings properly is one of the most complex things to get right. We thus added [a utility class](https://github.com/eclipse/elk/blob/master/plugins/org.eclipse.elk.core/src/org/eclipse/elk/core/util/ElkSpacings.java) to help ease the pain a little.
* [#533](https://github.com/eclipse/elk/issues/533), [#535](https://github.com/eclipse/elk/pull/535): _ELK Box_ and _ELK Rectangle Packing_ now support [content alignment](https://www.eclipse.org/elk/reference/options/org-eclipse-elk-contentalignment.html).
* [#593](https://github.com/eclipse/elk/pull/593): _ELK Rectangle Packing_ now supports a configurable target width that the algorithm will try to achieve.
* [#344](https://github.com/eclipse/elk/issues/344): ELK's JSON support nur supports a more relaxed JSON style.


### Changes

* [#500](https://github.com/eclipse/elk/issues/500): The Xtext version ELK uses was upgraded to 2.20.
* [#626](https://github.com/eclipse/elk/issues/626), [#634](https://github.com/eclipse/elk/pull/634): We changed the way port label placement is configured. Previously, there was a choice between inside and outside port labels, with other details configured in other options. We have now made the option an `EnumSet` to move port label options out of the `SizeOptions` enumeration and the `nextToPortIfPossible` option.
* [#646](https://github.com/eclipse/elk/issues/646), [#647](https://github.com/eclipse/elk/pull/647): _ELK Layered_'s layout options `layering.layerID` and `crossingMinimization.positionID` were renamed to `layering.layerId` and `crossingMinimization.positionId`, respectively. This also impacts the associated layout option constants.
* [#605](https://github.com/eclipse/elk/issues/605), [#619](https://github.com/eclipse/elk/pull/619): Since _ELK Layered_'s `northOrSouthPort` option caused some confusion with vertical layout directions, it was renamed to `allowNonFlowPortsToSwitchSides`, which incidentally also does a better job of describing what the option actually does.
* [#516](https://github.com/eclipse/elk/pull/516): Our `ELKServicePlugin` class had its super class changed from `AbstractUIPlugin` to `Plugin`.


### Removals

* [#577](https://github.com/eclipse/elk/issues/577), [#581](https://github.com/eclipse/elk/pull/581): We finally removed the legacy IDs of a whole number of layout options that were renamed over the years. If you relied on those exact IDs, it's high time to transition to their new IDs.
* [#536](https://github.com/eclipse/elk/issues/536), [#571](https://github.com/eclipse/elk/pull/571): We removed the Graphiti layout connector, which was buggy and did not seem to be used a lot.


### Bugfixes

* [#530](https://github.com/eclipse/elk/issues/530), [#546](https://github.com/eclipse/elk/issues/546), [#596](https://github.com/eclipse/elk/issues/596), [#597](https://github.com/eclipse/elk/pull/597), [#595](https://github.com/eclipse/elk/pull/595), [#610](https://github.com/eclipse/elk/pull/610): We fixed quite a few problems _ELK Layered_ had with hierarchical graphs.
* [#515](https://github.com/eclipse/elk/issues/515), [#569](https://github.com/eclipse/elk/pull/569): Under certain conditions, _ELK Layered_'s polyline edge router could end up routing edges through nodes.
* [#552](https://github.com/eclipse/elk/issues/552), [#561](https://github.com/eclipse/elk/pull/561): _ELK Layered_ would not always place self loop ports of hierarchical nodes properly.
* [#528](https://github.com/eclipse/elk/issues/528): _ELK Layered_'s semi-interactive crossing minimisation could end up yielding wrong node orders.
* [#583](https://github.com/eclipse/elk/issues/583), [#584](https://github.com/eclipse/elk/pull/584): _ELK Rectangle Packing_ sometimes left compound nodes larger than necessary.
* [#559](https://github.com/eclipse/elk/issues/559), [#567](https://github.com/eclipse/elk/issues/567), [#568](https://github.com/eclipse/elk/pull/568), [#633](https://github.com/eclipse/elk/pull/633): The JSON exporter has seen some love in the form of several smaller bug fixes.