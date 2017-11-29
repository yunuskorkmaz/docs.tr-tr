---
title: "Yayımlanan çıktı dotnet vstest ile test"
description: "Yayımlanan çıktıyı dotnet vstest komutu ile testleri çalıştırma hakkında bilgi edinin."
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3965e4ca-75b8-4969-b3af-ca993c397a15
ms.openlocfilehash: 217787d41a9da6000941ded6caaa4f44d124644b
ms.sourcegitcommit: 8a4f8e6a7f1341764abcd188a332cc28d1e2d8ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a>Yayımlanan çıktı dotnet vstest ile test

Kullanarak, önceden yayımlanmış Çıkışta testleri çalıştırabilirsiniz `dotnet vstest` komutu. Bu xUnit, mstest'i ve NUnit testleri çalışır. Yalnızca yayımlanan çıkış parçası olan DLL dosyasını bulun ve çalıştırın:
```
dotnet vstest <MyPublishedTests>.dll
```
Burada `<MyPublishedTests>` yayımlanan test projenizin adıdır.

### <a name="example-of-running-tests-on-a-published-dll"></a>Örnek üzerinde yayımlanan bir DLL testleri çalıştırma

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] Not: uygulamanızı bir çerçeve dışında hedefliyorsa `netcoreapp` yine de çalıştırılabilir `dotnet vstest` framework bayrağı hedef çerçeveyi geçirerek komutu. Örneğin, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. Visual Studio 2017 güncelleştirme 5'te istenen framework otomatik olarak algılanır.

### <a name="related-topics"></a>İlgili konular
- [Birim test dotnet test ve xUnit](unit-testing-with-dotnet-test.md)
- [Dotnet test ve mstest'i birim sınama](unit-testing-with-mstest.md)
