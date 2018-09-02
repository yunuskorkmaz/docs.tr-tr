---
title: Test yayımlanmış çıktısı dotnet vstest ile
description: Dotnet vstest komutu ile yayımlanan çıktıyı testleri çalıştırmayı öğrenin.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: e99000996f5dfa9f9d4f9b823e36ecbe325da835
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404721"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="484e5-103">Test yayımlanmış çıktısı dotnet vstest ile</span><span class="sxs-lookup"><span data-stu-id="484e5-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="484e5-104">Kullanarak zaten yayımlanmış çıkışı üzerinde testler çalıştırabilirsiniz `dotnet vstest` komutu.</span><span class="sxs-lookup"><span data-stu-id="484e5-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="484e5-105">Bu xUnit, MSTest ve NUnit testleri çalışır.</span><span class="sxs-lookup"><span data-stu-id="484e5-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="484e5-106">Yalnızca yayımlanan çıkışınızı parçası olan DLL dosyasını bulun ve çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="484e5-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="484e5-107">Burada `<MyPublishedTests>` yayımlanan test projenizin adıdır.</span><span class="sxs-lookup"><span data-stu-id="484e5-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="484e5-108">Yayımlanan bir DLL testleri çalıştırma örneği</span><span class="sxs-lookup"><span data-stu-id="484e5-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="484e5-109">Not: uygulamanızı dışındaki bir çerçeve hedefleme, `netcoreapp` çalıştırmaya devam `dotnet vstest` framework bayrakla hedeflenen çerçevenin geçirerek komutu.</span><span class="sxs-lookup"><span data-stu-id="484e5-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="484e5-110">Örneğin, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="484e5-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="484e5-111">Visual Studio 2017 güncelleştirme 5'te istenen framework otomatik olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="484e5-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="484e5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="484e5-112">See also</span></span>
- [<span data-ttu-id="484e5-113">Dotnet testi ve xUnit ile birim testi</span><span class="sxs-lookup"><span data-stu-id="484e5-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="484e5-114">Dotnet testi ve NUnit ile birim testi</span><span class="sxs-lookup"><span data-stu-id="484e5-114">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="484e5-115">Dotnet testi ve MSTest ile birim testi</span><span class="sxs-lookup"><span data-stu-id="484e5-115">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
