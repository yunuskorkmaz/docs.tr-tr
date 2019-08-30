---
title: DotNet VSTest ile yayımlanan çıktıyı test etme
description: Kaynak kodu yerine,, DotNet VSTest komutuyla testlerin yayımlanmış kitaplıklarda nasıl çalıştırılacağını öğrenin.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 9ac03053bc762d0176e087545871ca8a145cd41e
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168287"
---
# <a name="test-published-output-with-dotnet-vstest"></a>DotNet VSTest ile yayımlanan çıktıyı test etme

`dotnet vstest` Komutunu kullanarak, zaten yayınlanmış çıkış üzerinde testler çalıştırabilirsiniz. Bu işlem xUnit, MSTest ve NUnit testlerinde çalışır. Yalnızca yayınlanmış çıktılarınızın parçası olan DLL dosyasını bulun ve çalıştırın:

```console
dotnet vstest <MyPublishedTests>.dll
```

`<MyPublishedTests>` , Yayımlanan test projenizin adıdır.

## <a name="example"></a>Örnek

Aşağıdaki komutlar, yayımlanmış bir DLL üzerinde testleri çalıştırmayı gösterir.

```console
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Not: Uygulamanız dışında `netcoreapp` bir çerçeveyi hedefliyorsanız, bir Framework bayrağıyla hedeflenen Çerçeveyi geçirerek `dotnet vstest` komutunu yine de çalıştırabilirsiniz. Örneğin: `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. Visual Studio 2017 güncelleştirme 5 ' te istenen çerçeve otomatik olarak algılanır.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet test ve xUnit ile birim testi](unit-testing-with-dotnet-test.md)
- [DotNet test ve NUnit ile birim testi](unit-testing-with-nunit.md)
- [DotNet test ve MSTest ile birim testi](unit-testing-with-mstest.md)
