---
title: Test yayınlanan çıktı dotnet vstest ile
description: Dotnet vstest komutuyla kaynak kodu yerine yayımlanmış kitaplıklarda testleri nasıl çalıştırlayacağınızı öğrenin.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714262"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Test yayınlanan çıktı dotnet vstest ile

Zaten yayımlanmış çıktı üzerinde komutu `dotnet vstest` kullanarak testleri çalıştırabilirsiniz. Bu xUnit, MSTest ve NUnit testleri üzerinde çalışacaktır. Yalnızca yayımlanmış çıktınızın bir parçası olan DLL dosyasını bulun ve çalıştırın:

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

Yayınlanan `<MyPublishedTests>` test projenizin adı nerededir?

## <a name="example"></a>Örnek

Aşağıdaki komutlar, yayımlanmış bir DLL üzerinde çalışan testleri gösterir.

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Not: Uygulamanız başka bir `netcoreapp`çerçeveyi hedefliyorsa, hedeflenen çerçeveyi çerçeve bayrağıyla geçirerek `dotnet vstest` komutu çalıştırmaya devam edebilirsiniz. Örneğin, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`. Visual Studio 2017 Update 5 ve sonraki durumlarda istenilen çerçeve otomatik olarak algılanır.

## <a name="see-also"></a>Ayrıca bkz.

- [noktatesti ve xUnit ile Birim Testi](unit-testing-with-dotnet-test.md)
- [Noktanet Testi ve NUnit ile Birim Testi](unit-testing-with-nunit.md)
- [Noktatnet testi ve MSTest ile Birim Testi](unit-testing-with-mstest.md)
