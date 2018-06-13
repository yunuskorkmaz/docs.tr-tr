---
title: Yayımlanan çıktı dotnet vstest ile test
description: Yayımlanan çıktıyı dotnet vstest komutu ile testleri çalıştırma hakkında bilgi edinin.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: dbce1b6e616916e60e56318b773e8fcecbc55580
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33210259"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="b269c-103">Yayımlanan çıktı dotnet vstest ile test</span><span class="sxs-lookup"><span data-stu-id="b269c-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="b269c-104">Kullanarak, önceden yayımlanmış Çıkışta testleri çalıştırabilirsiniz `dotnet vstest` komutu.</span><span class="sxs-lookup"><span data-stu-id="b269c-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="b269c-105">Bu xUnit, mstest'i ve NUnit testleri çalışır.</span><span class="sxs-lookup"><span data-stu-id="b269c-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="b269c-106">Yalnızca yayımlanan çıkış parçası olan DLL dosyasını bulun ve çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="b269c-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="b269c-107">Burada `<MyPublishedTests>` yayımlanan test projenizin adıdır.</span><span class="sxs-lookup"><span data-stu-id="b269c-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="b269c-108">Örnek üzerinde yayımlanan bir DLL testleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b269c-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="b269c-109">Not: uygulamanızı bir çerçeve dışında hedefliyorsa `netcoreapp` yine de çalıştırılabilir `dotnet vstest` framework bayrağı hedef çerçeveyi geçirerek komutu.</span><span class="sxs-lookup"><span data-stu-id="b269c-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="b269c-110">Örneğin, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="b269c-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="b269c-111">Visual Studio 2017 güncelleştirme 5'te istenen framework otomatik olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="b269c-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="b269c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b269c-112">See also</span></span>
 [<span data-ttu-id="b269c-113">Birim test dotnet test ve xUnit</span><span class="sxs-lookup"><span data-stu-id="b269c-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)  
 [<span data-ttu-id="b269c-114">Dotnet test ve mstest'i birim sınama</span><span class="sxs-lookup"><span data-stu-id="b269c-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)  
