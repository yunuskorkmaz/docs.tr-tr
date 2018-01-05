---
title: "Çalışan seçmeli birim testleri"
description: "Bir filtre ifadesi dotnet test komutuyla seçmeli birim testleri çalıştırmak için nasıl kullanılacağını gösterir."
keywords: ".NET, .NET core birim testi, seçmeli test"
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13d01272-bbf8-456c-a97a-560001d1a7f2
ms.workload: dotnetcore
ms.openlocfilehash: a650e971afd63171b0cc12f679d81bc222a609a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="6bbe9-104">Çalışan seçmeli birim testleri</span><span class="sxs-lookup"><span data-stu-id="6bbe9-104">Running selective unit tests</span></span>

<span data-ttu-id="6bbe9-105">Aşağıdaki örneklerde `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-105">The following examples use `dotnet test`.</span></span> <span data-ttu-id="6bbe9-106">Kullanıyorsanız, `vstest.console.exe`, yerine `--filter ` ile `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-106">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="6bbe9-107">MSTest</span><span class="sxs-lookup"><span data-stu-id="6bbe9-107">MSTest</span></span>

```csharp
namespace MSTestNamespace
{
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    [TestClass]
    public class UnitTestClass1
    {
        [Priority(2)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [TestCategory("CategoryA")]
        [Priority(3)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="6bbe9-108">İfade</span><span class="sxs-lookup"><span data-stu-id="6bbe9-108">Expression</span></span> | <span data-ttu-id="6bbe9-109">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bbe9-109">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="6bbe9-110">Çalışmalarını test `FullyQualifiedName` içeren `Method`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-110">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="6bbe9-111">Kullanılabilir `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-111">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="6bbe9-112">Adında içeren testleri çalıştırır `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-112">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="6bbe9-113">Sınıfında olan testleri çalıştırır `MSTestNamespace.UnitTestClass1`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-113">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="6bbe9-114">**Not:** `ClassName` değeri olması gerektiğini bir ad alanı, bu nedenle `ClassName=UnitTestClass1` çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-114">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="6bbe9-115">Dışındaki tüm testleri çalıştırır `MSTestNamespace.UnitTestClass1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-115">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="6bbe9-116">İle Açıklama testleri çalıştırır `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-116">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="6bbe9-117">İle Açıklama testleri çalıştırır `[Priority(3)]`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-117">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="6bbe9-118">**Not:** `Priority~3` geçersiz bir değer bir dize değil aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-118">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="6bbe9-119">**Koşullu işleçler kullanarak | ve&amp;**</span><span class="sxs-lookup"><span data-stu-id="6bbe9-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="6bbe9-120">İfade</span><span class="sxs-lookup"><span data-stu-id="6bbe9-120">Expression</span></span> | <span data-ttu-id="6bbe9-121">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bbe9-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="6bbe9-122">Olan testleri çalıştırır `UnitTestClass1` içinde `FullyQualifiedName` **veya** `TestCategory` olan `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="6bbe9-123">Olan testleri çalıştırır `UnitTestClass1` içinde `FullyQualifiedName` **ve** `TestCategory` olan `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-123">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="6bbe9-124">Ya da testleri çalıştırır `FullyQualifiedName` içeren `UnitTestClass1` **ve** `TestCategory` olan `CategoryA` **veya** `Priority` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-124">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="6bbe9-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="6bbe9-125">xUnit</span></span>

```csharp
namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "bvt")]
        [Trait("Priority", "1")]
        [Fact]
        public void foo()
        {
        }

        [Trait("Category", "Nightly")]
        [Trait("Priority", "2")]
        [Fact]
        public void bar()
        {
        }
    }
}
```

| <span data-ttu-id="6bbe9-126">İfade</span><span class="sxs-lookup"><span data-stu-id="6bbe9-126">Expression</span></span> | <span data-ttu-id="6bbe9-127">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bbe9-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="6bbe9-128">Yalnızca bir test çalışmaları `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="6bbe9-129">Dışındaki tüm testleri çalıştırır `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="6bbe9-130">Görünen adında içeren testleri çalıştırır `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="6bbe9-131">Kod örneğinde, tanımlı nitelikler anahtarlarla `Category` ve `Priority` filtrelemesi için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="6bbe9-132">İfade</span><span class="sxs-lookup"><span data-stu-id="6bbe9-132">Expression</span></span> | <span data-ttu-id="6bbe9-133">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bbe9-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="6bbe9-134">Çalışmalarını test `FullyQualifiedName` içeren `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="6bbe9-135">Kullanılabilir `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="6bbe9-136">Olan testleri çalıştırır `[Trait("Category", "bvt")]`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-136">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="6bbe9-137">**Koşullu işleçler kullanarak | ve&amp;**</span><span class="sxs-lookup"><span data-stu-id="6bbe9-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="6bbe9-138">İfade</span><span class="sxs-lookup"><span data-stu-id="6bbe9-138">Expression</span></span> | <span data-ttu-id="6bbe9-139">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bbe9-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="6bbe9-140">Sahip çalıştırır testleri `TestClass1` içinde `FullyQualifiedName` **veya** `Category` olan `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="6bbe9-141">Sahip çalıştırır testleri `TestClass1` içinde `FullyQualifiedName` **ve** `Category` olan `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="6bbe9-142">Ya da testleri çalıştırır `FullyQualifiedName` içeren `TestClass1` **ve** `Category` olan `CategoryA` **veya** `Priority` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="6bbe9-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |
