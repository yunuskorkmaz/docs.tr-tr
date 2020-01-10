---
title: DotNet VSTest ile yayımlanan çıktıyı test etme
description: Kaynak kodu yerine,, DotNet VSTest komutuyla testlerin yayımlanmış kitaplıklarda nasıl çalıştırılacağını öğrenin.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714262"
---
# <a name="test-published-output-with-dotnet-vstest"></a>DotNet VSTest ile yayımlanan çıktıyı test etme

`dotnet vstest` komutunu kullanarak, zaten yayınlanmış çıkış üzerinde testler çalıştırabilirsiniz. Bu işlem xUnit, MSTest ve NUnit testlerinde çalışır. Yalnızca yayınlanmış çıktılarınızın parçası olan DLL dosyasını bulun ve çalıştırın:

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

Burada `<MyPublishedTests>`, yayımlanan test projenizin adıdır.

## <a name="example"></a>Örnek

Aşağıdaki komutlar, yayımlanmış bir DLL üzerinde testleri çalıştırmayı gösterir.

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Note: uygulamanız `netcoreapp`dışında bir çerçeveyi hedefliyorsa, bir çerçeve bayrağıyla hedeflenen çerçeveye geçirerek `dotnet vstest` komutunu yine de çalıştırabilirsiniz. Örneğin: `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`. Visual Studio 2017 güncelleştirme 5 ve sonraki sürümlerde, istenen çerçeve otomatik olarak algılanır.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet test ve xUnit ile birim testi](unit-testing-with-dotnet-test.md)
- [DotNet test ve NUnit ile birim testi](unit-testing-with-nunit.md)
- [DotNet test ve MSTest ile birim testi](unit-testing-with-mstest.md)
