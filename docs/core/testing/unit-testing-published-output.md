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
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="01706-103">Test yayımlanmış çıktısı dotnet vstest ile</span><span class="sxs-lookup"><span data-stu-id="01706-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="01706-104">Kullanarak zaten yayımlanmış çıkışı üzerinde testler çalıştırabilirsiniz `dotnet vstest` komutu.</span><span class="sxs-lookup"><span data-stu-id="01706-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="01706-105">Bu xUnit, MSTest ve NUnit testleri çalışır.</span><span class="sxs-lookup"><span data-stu-id="01706-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="01706-106">Yalnızca yayımlanan çıkışınızı parçası olan DLL dosyasını bulun ve çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="01706-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="01706-107">Burada `<MyPublishedTests>` yayımlanan test projenizin adıdır.</span><span class="sxs-lookup"><span data-stu-id="01706-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="01706-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="01706-108">Example</span></span>

<span data-ttu-id="01706-109">Aşağıdaki komutları yayımlanan bir DLL çalışan testler gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01706-109">The commands below demonstrate running tests on a published DLL.</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="01706-110">Not: Uygulama dışındaki bir çerçeve hedefleme, `netcoreapp` çalıştırmaya devam `dotnet vstest` framework bayrakla hedeflenen çerçevenin geçirerek komutu.</span><span class="sxs-lookup"><span data-stu-id="01706-110">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="01706-111">Örneğin: `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`</span><span class="sxs-lookup"><span data-stu-id="01706-111">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="01706-112">Visual Studio 2017 güncelleştirme 5'te istenen framework otomatik olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="01706-112">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="01706-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01706-113">See also</span></span>
- [<span data-ttu-id="01706-114">Dotnet testi ve xUnit ile birim testi</span><span class="sxs-lookup"><span data-stu-id="01706-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="01706-115">Dotnet testi ve NUnit ile birim testi</span><span class="sxs-lookup"><span data-stu-id="01706-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="01706-116">Dotnet testi ve MSTest ile birim testi</span><span class="sxs-lookup"><span data-stu-id="01706-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
