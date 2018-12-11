---
title: Test yayımlanmış çıktısı dotnet vstest ile
description: Dotnet vstest komutu ile yayımlanan çıktıyı testleri çalıştırmayı öğrenin.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 8930ec5c19254423fcdc9f0790ccf6748c595d6b
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170307"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Test yayımlanmış çıktısı dotnet vstest ile

Kullanarak zaten yayımlanmış çıkışı üzerinde testler çalıştırabilirsiniz `dotnet vstest` komutu. Bu xUnit, MSTest ve NUnit testleri çalışır. Yalnızca yayımlanan çıkışınızı parçası olan DLL dosyasını bulun ve çalıştırın:

```
dotnet vstest <MyPublishedTests>.dll
```

Burada `<MyPublishedTests>` yayımlanan test projenizin adıdır.

## <a name="example-of-running-tests-on-a-published-dll"></a>Yayımlanan bir DLL testleri çalıştırma örneği

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Not: Uygulama dışındaki bir çerçeve hedefleme, `netcoreapp` çalıştırmaya devam `dotnet vstest` framework bayrakla hedeflenen çerçevenin geçirerek komutu. Örneğin: `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"` Visual Studio 2017 güncelleştirme 5'te istenen framework otomatik olarak algılanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Dotnet testi ve xUnit ile birim testi](unit-testing-with-dotnet-test.md)
- [Dotnet testi ve NUnit ile birim testi](unit-testing-with-nunit.md)
- [Dotnet testi ve MSTest ile birim testi](unit-testing-with-mstest.md)
