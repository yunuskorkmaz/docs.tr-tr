---
title: DotNet VSTest ile yayımlanan çıktıyı test etme
description: Kaynak kodu yerine,, DotNet VSTest komutuyla testlerin yayımlanmış kitaplıklarda nasıl çalıştırılacağını öğrenin.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: e4fd25dc9ff30bdfe85cd1167a1dc41ea20a5f80
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771932"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="d0562-103">DotNet VSTest ile yayımlanan çıktıyı test etme</span><span class="sxs-lookup"><span data-stu-id="d0562-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="d0562-104">@No__t_0 komutunu kullanarak, zaten yayınlanmış çıkış üzerinde testler çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0562-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="d0562-105">Bu işlem xUnit, MSTest ve NUnit testlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="d0562-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="d0562-106">Yalnızca yayınlanmış çıktılarınızın parçası olan DLL dosyasını bulun ve çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d0562-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="d0562-107">Burada `<MyPublishedTests>`, yayımlanan test projenizin adıdır.</span><span class="sxs-lookup"><span data-stu-id="d0562-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="d0562-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0562-108">Example</span></span>

<span data-ttu-id="d0562-109">Aşağıdaki komutlar, yayımlanmış bir DLL üzerinde testleri çalıştırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0562-109">The commands below demonstrate running tests on a published DLL.</span></span>

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="d0562-110">Note: uygulamanız `netcoreapp` dışında bir çerçeveyi hedefliyorsa, bir çerçeve bayrağıyla hedeflenen çerçeveye geçirerek `dotnet vstest` komutunu yine de çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0562-110">Note: If your app targets a framework other than `netcoreapp`, you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="d0562-111">Örneğin, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="d0562-111">For example, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="d0562-112">Visual Studio 2017 güncelleştirme 5 ve sonraki sürümlerde, istenen çerçeve otomatik olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="d0562-112">In Visual Studio 2017 Update 5 and later, the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0562-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0562-113">See also</span></span>

- [<span data-ttu-id="d0562-114">DotNet test ve xUnit ile birim testi</span><span class="sxs-lookup"><span data-stu-id="d0562-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="d0562-115">DotNet test ve NUnit ile birim testi</span><span class="sxs-lookup"><span data-stu-id="d0562-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="d0562-116">DotNet test ve MSTest ile birim testi</span><span class="sxs-lookup"><span data-stu-id="d0562-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
