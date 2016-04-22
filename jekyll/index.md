---
layout: home
technologies:
 - scala: ["Scala", "Lorem ipsum dolor sit amet, conse ctetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolo…"]
 - android: ["Android", "Lorem ipsum dolor sit amet, conse ctetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolo…"]
 - database: ["Database", "Lorem ipsum dolor sit amet, conse ctetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolo…"]
---


* ## Feature one
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean mollis, enim quis mollis blandit, orci urna lobortis eros, quis tristique quam tellus sit amet nulla. Vivamus congue est quis magna vehicula lobortis. Pellentesque suscipit lectus eu mi vehicula, sed vehicula lectus porta. Aenean tempor metus ac viverra tempus.

* ```scala
object repositories {

      class Repository[F[_]](implicit D: DataSource[F]) {
        def add[A](a: A): FreeC[F, Option[A]] = D.add(a)
        def getAll[A]: FreeC[F, List[A]] = D.getAll
      }

      object Repository {
        implicit def repository[F[_]]
        (implicit D: DataSource[F]): Repository[F] = new Repository[F]
      }

    }
```


* ## Feature two
  Morbi mollis molestie vulputate. Quisque interdum maximus fringilla. Mauris id ligula eu lacus egestas euismod. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras in velit a lacus pellentesque interdum. Suspendisse ipsum massa, convallis in venenatis eleifend, congue vitae tellus

* ```scala
  def or[F[_], G[_], H[_]]
   (f: F ~> H, g: G ~> H):
   ({type cp[α] = Coproduct[F, G, α]})#cp ~> H =
      new NaturalTransformation[({type cp[α] =
        Coproduct[F, G, α]})#cp, H] {
          def apply[A](fa: Coproduct[F, G, A]): H[A] = fa.run match {
            case -\/(ff) => f(ff)
            case \/-(gg) => g(gg)
          }
    }
```


* ## Feature three
  Integer ante diam, faucibus at venenatis ullamcorper, tincidunt sed enim. Praesent in ante consectetur, vestibulum metus vel, dignissim diam. Sed vestibulum ac felis scelerisque pellentesque:

* ```scala
    type AgendaApp[A] = Coproduct[DataOp, Interact, A]
    type ACoyo[A] = Coyoneda[AgendaApp,A]
    type AFree[A] = Free[ACoyo,A]

    def prg(implicit CP : ContactsListPresenter[AgendaApp]) = for {
        _ <- CP.onInitialize
        _ <- Monad[AFree].replicateM(2, CP.onAddContactOptionSelected)
        _ <- CP.onStop
    } yield ()

    def runApp = prg.mapSuspension(coyoint)
```
