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
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="ec6f4-103">DotNet VSTest ile yayımlanan çıktıyı test etme</span><span class="sxs-lookup"><span data-stu-id="ec6f4-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="ec6f4-104">`dotnet vstest` Komutunu kullanarak, zaten yayınlanmış çıkış üzerinde testler çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec6f4-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="ec6f4-105">Bu işlem xUnit, MSTest ve NUnit testlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="ec6f4-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="ec6f4-106">Yalnızca yayınlanmış çıktılarınızın parçası olan DLL dosyasını bulun ve çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ec6f4-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="ec6f4-107">`<MyPublishedTests>` , Yayımlanan test projenizin adıdır.</span><span class="sxs-lookup"><span data-stu-id="ec6f4-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="ec6f4-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec6f4-108">Example</span></span>

<span data-ttu-id="ec6f4-109">Aşağıdaki komutlar, yayımlanmış bir DLL üzerinde testleri çalıştırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec6f4-109">The commands below demonstrate running tests on a published DLL.</span></span>

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="ec6f4-110">Not: Uygulamanız dışında `netcoreapp` bir çerçeveyi hedefliyorsanız, bir Framework bayrağıyla hedeflenen Çerçeveyi geçirerek `dotnet vstest` komutunu yine de çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec6f4-110">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="ec6f4-111">Örneğin, uygulamasında yönetilen Hyper-V konakları olarak eklemek için aşağıdaki yordamı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec6f4-111">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="ec6f4-112">Visual Studio 2017 güncelleştirme 5 ' te istenen çerçeve otomatik olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="ec6f4-112">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec6f4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec6f4-113">See also</span></span>

- [<span data-ttu-id="ec6f4-114">DotNet test ve xUnit ile birim testi</span><span class="sxs-lookup"><span data-stu-id="ec6f4-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="ec6f4-115">DotNet test ve NUnit ile birim testi</span><span class="sxs-lookup"><span data-stu-id="ec6f4-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="ec6f4-116">DotNet test ve MSTest ile birim testi</span><span class="sxs-lookup"><span data-stu-id="ec6f4-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
