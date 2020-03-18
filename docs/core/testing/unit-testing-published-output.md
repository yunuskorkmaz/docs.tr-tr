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
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="4d5ce-103">Test yayınlanan çıktı dotnet vstest ile</span><span class="sxs-lookup"><span data-stu-id="4d5ce-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="4d5ce-104">Zaten yayımlanmış çıktı üzerinde komutu `dotnet vstest` kullanarak testleri çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d5ce-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="4d5ce-105">Bu xUnit, MSTest ve NUnit testleri üzerinde çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="4d5ce-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="4d5ce-106">Yalnızca yayımlanmış çıktınızın bir parçası olan DLL dosyasını bulun ve çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4d5ce-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="4d5ce-107">Yayınlanan `<MyPublishedTests>` test projenizin adı nerededir?</span><span class="sxs-lookup"><span data-stu-id="4d5ce-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="4d5ce-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d5ce-108">Example</span></span>

<span data-ttu-id="4d5ce-109">Aşağıdaki komutlar, yayımlanmış bir DLL üzerinde çalışan testleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d5ce-109">The commands below demonstrate running tests on a published DLL.</span></span>

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="4d5ce-110">Not: Uygulamanız başka bir `netcoreapp`çerçeveyi hedefliyorsa, hedeflenen çerçeveyi çerçeve bayrağıyla geçirerek `dotnet vstest` komutu çalıştırmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d5ce-110">Note: If your app targets a framework other than `netcoreapp`, you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="4d5ce-111">Örneğin, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="4d5ce-111">For example, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="4d5ce-112">Visual Studio 2017 Update 5 ve sonraki durumlarda istenilen çerçeve otomatik olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="4d5ce-112">In Visual Studio 2017 Update 5 and later, the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d5ce-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d5ce-113">See also</span></span>

- [<span data-ttu-id="4d5ce-114">noktatesti ve xUnit ile Birim Testi</span><span class="sxs-lookup"><span data-stu-id="4d5ce-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="4d5ce-115">Noktanet Testi ve NUnit ile Birim Testi</span><span class="sxs-lookup"><span data-stu-id="4d5ce-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="4d5ce-116">Noktatnet testi ve MSTest ile Birim Testi</span><span class="sxs-lookup"><span data-stu-id="4d5ce-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
