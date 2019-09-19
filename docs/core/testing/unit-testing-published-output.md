---
title: DotNet VSTest ile yayımlanan çıktıyı test etme
description: Kaynak kodu yerine,, DotNet VSTest komutuyla testlerin yayımlanmış kitaplıklarda nasıl çalıştırılacağını öğrenin.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 93b2e1a433b5d5b9694257d4d12e47d9107f4cd7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117031"
---
# <a name="test-published-output-with-dotnet-vstest"></a>DotNet VSTest ile yayımlanan çıktıyı test etme

`dotnet vstest` Komutunu kullanarak, zaten yayınlanmış çıkış üzerinde testler çalıştırabilirsiniz. Bu işlem xUnit, MSTest ve NUnit testlerinde çalışır. Yalnızca yayınlanmış çıktılarınızın parçası olan DLL dosyasını bulun ve çalıştırın:

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

`<MyPublishedTests>` , Yayımlanan test projenizin adıdır.

## <a name="example"></a>Örnek

Aşağıdaki komutlar, yayımlanmış bir DLL üzerinde testleri çalıştırmayı gösterir.

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Not: Uygulamanız dışında `netcoreapp` bir çerçeveyi hedefliyorsanız, bir Framework bayrağıyla hedeflenen Çerçeveyi geçirerek `dotnet vstest` komutunu yine de çalıştırabilirsiniz. Örneğin, uygulamasında yönetilen Hyper-V konakları olarak eklemek için aşağıdaki yordamı kullanabilirsiniz. Visual Studio 2017 güncelleştirme 5 ' te istenen çerçeve otomatik olarak algılanır.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet test ve xUnit ile birim testi](unit-testing-with-dotnet-test.md)
- [DotNet test ve NUnit ile birim testi](unit-testing-with-nunit.md)
- [DotNet test ve MSTest ile birim testi](unit-testing-with-mstest.md)
