# e007_flutter_reorderable_listview_e004base

## Based On e004

- [elrashid-flutter-examples/e004_flutter_listview_crud_app_using_nonsecure_rest_api](https://github.com/elrashid-flutter-examples/e004_flutter_listview_crud_app_using_nonsecure_rest_api)

## Screen Record

![app screen record](docs/screen_record.gif)

## What

- ReorderableListView for tasks in flutter Task app (e004)

- must run with :

  - [elrashid-flutter-examples/e002-aspcore-rest-api-server-for-flutter](https://github.com/elrashid-flutter-examples/e002-aspcore-rest-api-server-for-flutter)

## Step 1

    ReorderableListView(
    children: <Widget>[
    ],

## Step 2

    children: <Widget>[
        for (final task in tasks)
        TaskWidget(
            key: Key(task.guid),
            taskOpj: task,
            notifyParent: refresh,
        ),
    ], 

## Step 3

    onReorder: (oldIndex, newIndex) {
        if (newIndex > oldIndex) {
        newIndex -= 1;
        }
        setState(() {
        if (newIndex > oldIndex) {
            newIndex -= 1;
        }
        final TaskOpj item = tasks.removeAt(oldIndex);
        tasks.insert(newIndex, item);
        });
    },

## Full code

    ReorderableListView(
    children: <Widget>[
        for (final task in tasks)
        TaskWidget(
            key: Key(task.guid),
            taskOpj: task,
            notifyParent: refresh,
        ),
    ],
    onReorder: (oldIndex, newIndex) {
        if (newIndex > oldIndex) {
        newIndex -= 1;
        }
        setState(() {
        if (newIndex > oldIndex) {
            newIndex -= 1;
        }
        final TaskOpj item = tasks.removeAt(oldIndex);
        tasks.insert(newIndex, item);
        });
    },
    )

## Note

- key must be unique

      key: Key(task.guid)

- from [API Docs](https://api.flutter.dev/flutter/material/ReorderableListView-class.html) :

  > All children must have a key.

- For more understanding of **key** watch:

  - [When to Use Keys - Flutter Widgets 101 Ep. 4 - YouTube](https://www.youtube.com/watch?v=kn0EOS-ZiIc)


## Ref

- [ReorderableListView (Flutter Widget of the Week) - YouTube](https://www.youtube.com/watch?v=3fB1mxOsqJE&list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG&index=43)

- [ReorderableListView class - material library - Dart API](https://api.flutter.dev/flutter/material/ReorderableListView-class.html)

- [Search · ReorderableListView](https://github.com/flutter/flutter/search?q=ReorderableListView&unscoped_q=ReorderableListView)

- [flutter/reorderable_list_test.dart at 3c93b65a9bcc8aa723231eff4eb0a7e19b2daccf · flutter/flutter](https://github.com/flutter/flutter/blob/3c93b65a9bcc8aa723231eff4eb0a7e19b2daccf/packages/flutter/test/material/reorderable_list_test.dart)

- [flutter/reorderable_list_demo.dart at 8c5a41113e2c0731147fe62a941ca33b9a1e8e8a · flutter/flutter](https://github.com/flutter/flutter/blob/8c5a41113e2c0731147fe62a941ca33b9a1e8e8a/examples/flutter_gallery/lib/demo/material/reorderable_list_demo.dart)