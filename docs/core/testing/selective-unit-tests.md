---
title: Seçmeli birim testleri çalıştırma
description: Dotnet testi komutu .NET core'da seçmeli birim testlerini çalıştırmak için bir filtre ifadesi kullanma
author: smadala
ms.date: 03/22/2017
ms.custom: seodec18
ms.openlocfilehash: 1a90438e3b0b2eb095124208010bbe9558424d91
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170211"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="49416-103">Seçmeli birim testleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="49416-103">Running selective unit tests</span></span>

<span data-ttu-id="49416-104">Aşağıdaki örneklerde `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="49416-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="49416-105">Kullanıyorsanız `vstest.console.exe`, değiştirin `--filter ` ile `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="49416-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="49416-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="49416-106">MSTest</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestCategory("CategoryA")]
        [Priority(1)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [Priority(2)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="49416-107">İfade</span><span class="sxs-lookup"><span data-stu-id="49416-107">Expression</span></span> | <span data-ttu-id="49416-108">Sonuç</span><span class="sxs-lookup"><span data-stu-id="49416-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="49416-109">Çalıştırmaları testleri `FullyQualifiedName` içeren `Method`.</span><span class="sxs-lookup"><span data-stu-id="49416-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="49416-110">Kullanılabilir `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="49416-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="49416-111">Adında içeren çalıştırdığında `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="49416-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="49416-112">Sınıfta olan testleri çalıştırır `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="49416-112">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="49416-113">**Not:** `ClassName` Değer olmalıdır bir ad alanı, bu nedenle `ClassName=UnitTest1` çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="49416-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="49416-114">Dışındaki tüm testleri çalıştırır `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="49416-114">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="49416-115">Hangi ile açıklamalı olan testleri çalıştırır `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="49416-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="49416-116">Hangi ile açıklamalı olan testleri çalıştırır `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="49416-116">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="49416-117">**Koşullu işleçler kullanarak | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="49416-117">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="49416-118">İfade</span><span class="sxs-lookup"><span data-stu-id="49416-118">Expression</span></span> | <span data-ttu-id="49416-119">Sonuç</span><span class="sxs-lookup"><span data-stu-id="49416-119">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="49416-120">Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **veya** `TestCategory` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="49416-120">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="49416-121">Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **ve** `TestCategory` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="49416-121">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="49416-122">Ya da olan testleri çalıştırır `FullyQualifiedName` içeren `UnitTest1` **ve** `TestCategory` olduğu `CategoryA` **veya** `Priority` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="49416-122">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="49416-123">xUnit</span><span class="sxs-lookup"><span data-stu-id="49416-123">xUnit</span></span>

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "CategoryA")]
        [Trait("Priority", "1")]
        [Fact]
        public void Test1()
        {
        }

        [Trait("Priority", "2")]
        [Fact]
        public void Test2()
        {
        }
    }
}
```

| <span data-ttu-id="49416-124">İfade</span><span class="sxs-lookup"><span data-stu-id="49416-124">Expression</span></span> | <span data-ttu-id="49416-125">Sonuç</span><span class="sxs-lookup"><span data-stu-id="49416-125">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="49416-126">Yalnızca bir test çalıştırmaları `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="49416-126">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="49416-127">Dışındaki tüm testleri çalıştırır `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="49416-127">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="49416-128">Çalıştırdığında, görünen adı içeren `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="49416-128">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="49416-129">Kod örneğinde, tanımlanan nitelikler anahtarlarla `Category` ve `Priority` filtrelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="49416-129">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="49416-130">İfade</span><span class="sxs-lookup"><span data-stu-id="49416-130">Expression</span></span> | <span data-ttu-id="49416-131">Sonuç</span><span class="sxs-lookup"><span data-stu-id="49416-131">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="49416-132">Çalıştırmaları testleri `FullyQualifiedName` içeren `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="49416-132">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="49416-133">Kullanılabilir `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="49416-133">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="49416-134">Olan testleri çalıştırır `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="49416-134">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="49416-135">**Koşullu işleçler kullanarak | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="49416-135">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="49416-136">İfade</span><span class="sxs-lookup"><span data-stu-id="49416-136">Expression</span></span> | <span data-ttu-id="49416-137">Sonuç</span><span class="sxs-lookup"><span data-stu-id="49416-137">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="49416-138">Sahip çalıştırmaları testleri `TestClass1` içinde `FullyQualifiedName` **veya** `Category` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="49416-138">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="49416-139">Sahip çalıştırmaları testleri `TestClass1` içinde `FullyQualifiedName` **ve** `Category` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="49416-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="49416-140">Ya da olan testleri çalıştırır `FullyQualifiedName` içeren `TestClass1` **ve** `Category` olduğu `CategoryA` **veya** `Priority` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="49416-140">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="49416-141">NUnit</span><span class="sxs-lookup"><span data-stu-id="49416-141">NUnit</span></span>

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Category("CategoryA")]
        [Property("Priority", 1)]
        [Test]
        public void TestMethod1()
        {
        }

        [Property("Priority", 2)]
        [Test]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="49416-142">İfade</span><span class="sxs-lookup"><span data-stu-id="49416-142">Expression</span></span> | <span data-ttu-id="49416-143">Sonuç</span><span class="sxs-lookup"><span data-stu-id="49416-143">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="49416-144">Çalıştırmaları testleri `FullyQualifiedName` içeren `Method`.</span><span class="sxs-lookup"><span data-stu-id="49416-144">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="49416-145">Kullanılabilir `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="49416-145">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="49416-146">Adında içeren çalıştırdığında `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="49416-146">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="49416-147">Sınıfta olan testleri çalıştırır `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="49416-147">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="49416-148">Dışındaki tüm testleri çalıştırır `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="49416-148">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="49416-149">Hangi ile açıklamalı olan testleri çalıştırır `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="49416-149">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="49416-150">Hangi ile açıklamalı olan testleri çalıştırır `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="49416-150">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="49416-151">**Koşullu işleçler kullanarak | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="49416-151">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="49416-152">İfade</span><span class="sxs-lookup"><span data-stu-id="49416-152">Expression</span></span> | <span data-ttu-id="49416-153">Sonuç</span><span class="sxs-lookup"><span data-stu-id="49416-153">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="49416-154">Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **veya** `TestCategory` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="49416-154">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="49416-155">Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **ve** `TestCategory` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="49416-155">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="49416-156">Ya da olan testleri çalıştırır `FullyQualifiedName` içeren `UnitTest1` **ve** `TestCategory` olduğu `CategoryA` **veya** `Priority` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="49416-156">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
