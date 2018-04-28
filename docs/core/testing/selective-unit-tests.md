---
title: Çalışan seçmeli birim testleri
description: Bir filtre ifadesi dotnet test komutuyla seçmeli birim testleri çalıştırmak için nasıl kullanılacağını gösterir.
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 77ac7ab5a46150bd3654d50e6686087c804b8440
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="700b7-103">Çalışan seçmeli birim testleri</span><span class="sxs-lookup"><span data-stu-id="700b7-103">Running selective unit tests</span></span>

<span data-ttu-id="700b7-104">Aşağıdaki örneklerde `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="700b7-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="700b7-105">Kullanıyorsanız, `vstest.console.exe`, yerine `--filter ` ile `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="700b7-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="700b7-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="700b7-106">MSTest</span></span>

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

| <span data-ttu-id="700b7-107">İfade</span><span class="sxs-lookup"><span data-stu-id="700b7-107">Expression</span></span> | <span data-ttu-id="700b7-108">Sonuç</span><span class="sxs-lookup"><span data-stu-id="700b7-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="700b7-109">Çalışmalarını test `FullyQualifiedName` içeren `Method`.</span><span class="sxs-lookup"><span data-stu-id="700b7-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="700b7-110">Kullanılabilir `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="700b7-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="700b7-111">Adında içeren testleri çalıştırır `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="700b7-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="700b7-112">Sınıfında olan testleri çalıştırır `MSTestNamespace.UnitTestClass1`.</span><span class="sxs-lookup"><span data-stu-id="700b7-112">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="700b7-113">**Not:** `ClassName` değeri olması gerektiğini bir ad alanı, bu nedenle `ClassName=UnitTestClass1` çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="700b7-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="700b7-114">Dışındaki tüm testleri çalıştırır `MSTestNamespace.UnitTestClass1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="700b7-114">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="700b7-115">İle Açıklama testleri çalıştırır `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="700b7-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="700b7-116">İle Açıklama testleri çalıştırır `[Priority(3)]`.</span><span class="sxs-lookup"><span data-stu-id="700b7-116">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="700b7-117">**Not:** `Priority~3` geçersiz bir değer bir dize değil aynıdır.</span><span class="sxs-lookup"><span data-stu-id="700b7-117">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="700b7-118">**Koşullu işleçler kullanarak | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="700b7-118">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="700b7-119">İfade</span><span class="sxs-lookup"><span data-stu-id="700b7-119">Expression</span></span> | <span data-ttu-id="700b7-120">Sonuç</span><span class="sxs-lookup"><span data-stu-id="700b7-120">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="700b7-121">Olan testleri çalıştırır `UnitTestClass1` içinde `FullyQualifiedName` **veya** `TestCategory` olan `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="700b7-121">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="700b7-122">Olan testleri çalıştırır `UnitTestClass1` içinde `FullyQualifiedName` **ve** `TestCategory` olan `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="700b7-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="700b7-123">Ya da testleri çalıştırır `FullyQualifiedName` içeren `UnitTestClass1` **ve** `TestCategory` olan `CategoryA` **veya** `Priority` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="700b7-123">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="700b7-124">xUnit</span><span class="sxs-lookup"><span data-stu-id="700b7-124">xUnit</span></span>

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

| <span data-ttu-id="700b7-125">İfade</span><span class="sxs-lookup"><span data-stu-id="700b7-125">Expression</span></span> | <span data-ttu-id="700b7-126">Sonuç</span><span class="sxs-lookup"><span data-stu-id="700b7-126">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="700b7-127">Yalnızca bir test çalışmaları `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="700b7-127">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="700b7-128">Dışındaki tüm testleri çalıştırır `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="700b7-128">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="700b7-129">Görünen adında içeren testleri çalıştırır `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="700b7-129">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="700b7-130">Kod örneğinde, tanımlı nitelikler anahtarlarla `Category` ve `Priority` filtrelemesi için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="700b7-130">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="700b7-131">İfade</span><span class="sxs-lookup"><span data-stu-id="700b7-131">Expression</span></span> | <span data-ttu-id="700b7-132">Sonuç</span><span class="sxs-lookup"><span data-stu-id="700b7-132">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="700b7-133">Çalışmalarını test `FullyQualifiedName` içeren `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="700b7-133">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="700b7-134">Kullanılabilir `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="700b7-134">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="700b7-135">Olan testleri çalıştırır `[Trait("Category", "bvt")]`.</span><span class="sxs-lookup"><span data-stu-id="700b7-135">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="700b7-136">**Koşullu işleçler kullanarak | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="700b7-136">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="700b7-137">İfade</span><span class="sxs-lookup"><span data-stu-id="700b7-137">Expression</span></span> | <span data-ttu-id="700b7-138">Sonuç</span><span class="sxs-lookup"><span data-stu-id="700b7-138">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="700b7-139">Sahip çalıştırır testleri `TestClass1` içinde `FullyQualifiedName` **veya** `Category` olan `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="700b7-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="700b7-140">Sahip çalıştırır testleri `TestClass1` içinde `FullyQualifiedName` **ve** `Category` olan `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="700b7-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="700b7-141">Ya da testleri çalıştırır `FullyQualifiedName` içeren `TestClass1` **ve** `Category` olan `CategoryA` **veya** `Priority` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="700b7-141">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |
