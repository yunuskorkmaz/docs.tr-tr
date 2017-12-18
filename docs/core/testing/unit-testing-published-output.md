---
title: "Yayımlanan çıktı dotnet vstest ile test"
description: "Yayımlanan çıktıyı dotnet vstest komutu ile testleri çalıştırma hakkında bilgi edinin."
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 6651d41d4d60194aec035107e3a65df6a5f70a51
ms.sourcegitcommit: 4a96a0fe9f87de70291245d71b76c7d1b15127ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="3d056-103">Yayımlanan çıktı dotnet vstest ile test</span><span class="sxs-lookup"><span data-stu-id="3d056-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="3d056-104">Kullanarak, önceden yayımlanmış Çıkışta testleri çalıştırabilirsiniz `dotnet vstest` komutu.</span><span class="sxs-lookup"><span data-stu-id="3d056-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="3d056-105">Bu xUnit, mstest'i ve NUnit testleri çalışır.</span><span class="sxs-lookup"><span data-stu-id="3d056-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="3d056-106">Yalnızca yayımlanan çıkış parçası olan DLL dosyasını bulun ve çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3d056-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="3d056-107">Burada `<MyPublishedTests>` yayımlanan test projenizin adıdır.</span><span class="sxs-lookup"><span data-stu-id="3d056-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="3d056-108">Örnek üzerinde yayımlanan bir DLL testleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3d056-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="3d056-109">Not: uygulamanızı bir çerçeve dışında hedefliyorsa `netcoreapp` yine de çalıştırılabilir `dotnet vstest` framework bayrağı hedef çerçeveyi geçirerek komutu.</span><span class="sxs-lookup"><span data-stu-id="3d056-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="3d056-110">Örneğin, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="3d056-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="3d056-111">Visual Studio 2017 güncelleştirme 5'te istenen framework otomatik olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="3d056-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d056-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d056-112">See also</span></span>
 [<span data-ttu-id="3d056-113">Birim test dotnet test ve xUnit</span><span class="sxs-lookup"><span data-stu-id="3d056-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)  
 [<span data-ttu-id="3d056-114">Dotnet test ve mstest'i birim sınama</span><span class="sxs-lookup"><span data-stu-id="3d056-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)  
