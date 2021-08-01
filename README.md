# RamaRunner
A Java oriented compilation unit with the goal of making an output Jar which can rely on inner dependencies (so you don't have to assume the end user has your dependencies!)

Essentially functions as the following:

ACTION: RamaRunner is invoked (by double-click or java command)

RESPONSE: RamaRunner inflates <jarRunnerIsInside.jar>!runner/ file to java.home/RamaRunner/

CONDITIONAL: if inflated file contains a RamaRunner instance

RESPONSE:
  - the "baton" (responsibility) of inflating is passed to the Inner RamaRunner recursively (continue until no RamaRunner instance exists)
  - Runner inflates java.home/RamaRunner/dependencies/<jarRunnerIsInside.jar>!runner/ to java.home/RamaRunner
  - Mark all non-RamaRunner instances as complete
  - Mark self as complete

OUTPUT: All RamaRunner instances will have any dependency available to them as long as the Manifest.mf file points to java.home/RamaRunner/dependencies/ (which the RamaRunner python scripts will incluce automatically)
