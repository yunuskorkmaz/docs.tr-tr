---
title: Test yayımlanmış çıktısı dotnet vstest ile
description: Testleri yayımlanan kitaplıklarındaki yerine dotnet vstest komutuyla bir kaynak kod üzerinde çalıştırmayı öğrenin.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 9d842f26336d0ddf5375d49676523086bb632684
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239533"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Test yayımlanmış çıktısı dotnet vstest ile

Kullanarak zaten yayımlanmış çıkışı üzerinde testler çalıştırabilirsiniz `dotnet vstest` komutu. Bu xUnit, MSTest ve NUnit testleri çalışır. Yalnızca yayımlanan çıkışınızı parçası olan DLL dosyasını bulun ve çalıştırın:

```
dotnet vstest <MyPublishedTests>.dll
```

Burada `<MyPublishedTests>` yayımlanan test projenizin adıdır.

## <a name="example"></a>Örnek

Aşağıdaki komutları yayımlanan bir DLL çalışan testler gösterilmiştir.

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
