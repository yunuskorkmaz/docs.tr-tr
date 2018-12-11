---
title: Seçmeli birim testleri çalıştırma
description: Dotnet testi komutu .NET core'da seçmeli birim testlerini çalıştırmak için bir filtre ifadesi kullanma
author: smadala
ms.date: 03/22/2017
ms.custom: seodec18
ms.openlocfilehash: 2ec6dc770f33acc4acea79e60cf6f9c33f1077d8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239949"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="821d7-103">Seçmeli birim testleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="821d7-103">Running selective unit tests</span></span>

<span data-ttu-id="821d7-104">İle `dotnet test` komutu'de .NET Core, seçmeli testleri çalıştırmak için bir filtre ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="821d7-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="821d7-105">Bu makalede, test çalışması filtrelemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="821d7-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="821d7-106">Aşağıdaki örneklerde `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="821d7-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="821d7-107">Kullanıyorsanız `vstest.console.exe`, değiştirin `--filter ` ile `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="821d7-107">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="821d7-108">MSTest</span><span class="sxs-lookup"><span data-stu-id="821d7-108">MSTest</span></span>

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

| <span data-ttu-id="821d7-109">İfade</span><span class="sxs-lookup"><span data-stu-id="821d7-109">Expression</span></span> | <span data-ttu-id="821d7-110">Sonuç</span><span class="sxs-lookup"><span data-stu-id="821d7-110">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="821d7-111">Çalıştırmaları testleri `FullyQualifiedName` içeren `Method`.</span><span class="sxs-lookup"><span data-stu-id="821d7-111">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="821d7-112">Kullanılabilir `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="821d7-112">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="821d7-113">Adında içeren çalıştırdığında `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="821d7-113">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="821d7-114">Sınıfta olan testleri çalıştırır `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="821d7-114">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="821d7-115">**Not:** `ClassName` Değer olmalıdır bir ad alanı, bu nedenle `ClassName=UnitTest1` çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="821d7-115">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="821d7-116">Dışındaki tüm testleri çalıştırır `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="821d7-116">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="821d7-117">Hangi ile açıklamalı olan testleri çalıştırır `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="821d7-117">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="821d7-118">Hangi ile açıklamalı olan testleri çalıştırır `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="821d7-118">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="821d7-119">**Koşullu işleçler kullanarak | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="821d7-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="821d7-120">İfade</span><span class="sxs-lookup"><span data-stu-id="821d7-120">Expression</span></span> | <span data-ttu-id="821d7-121">Sonuç</span><span class="sxs-lookup"><span data-stu-id="821d7-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="821d7-122">Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **veya** `TestCategory` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="821d7-122">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="821d7-123">Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **ve** `TestCategory` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="821d7-123">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="821d7-124">Ya da olan testleri çalıştırır `FullyQualifiedName` içeren `UnitTest1` **ve** `TestCategory` olduğu `CategoryA` **veya** `Priority` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="821d7-124">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="821d7-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="821d7-125">xUnit</span></span>

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

| <span data-ttu-id="821d7-126">İfade</span><span class="sxs-lookup"><span data-stu-id="821d7-126">Expression</span></span> | <span data-ttu-id="821d7-127">Sonuç</span><span class="sxs-lookup"><span data-stu-id="821d7-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="821d7-128">Yalnızca bir test çalıştırmaları `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="821d7-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="821d7-129">Dışındaki tüm testleri çalıştırır `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="821d7-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="821d7-130">Çalıştırdığında, görünen adı içeren `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="821d7-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="821d7-131">Kod örneğinde, tanımlanan nitelikler anahtarlarla `Category` ve `Priority` filtrelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="821d7-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="821d7-132">İfade</span><span class="sxs-lookup"><span data-stu-id="821d7-132">Expression</span></span> | <span data-ttu-id="821d7-133">Sonuç</span><span class="sxs-lookup"><span data-stu-id="821d7-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="821d7-134">Çalıştırmaları testleri `FullyQualifiedName` içeren `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="821d7-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="821d7-135">Kullanılabilir `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="821d7-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="821d7-136">Olan testleri çalıştırır `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="821d7-136">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="821d7-137">**Koşullu işleçler kullanarak | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="821d7-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="821d7-138">İfade</span><span class="sxs-lookup"><span data-stu-id="821d7-138">Expression</span></span> | <span data-ttu-id="821d7-139">Sonuç</span><span class="sxs-lookup"><span data-stu-id="821d7-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="821d7-140">Sahip çalıştırmaları testleri `TestClass1` içinde `FullyQualifiedName` **veya** `Category` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="821d7-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="821d7-141">Sahip çalıştırmaları testleri `TestClass1` içinde `FullyQualifiedName` **ve** `Category` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="821d7-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="821d7-142">Ya da olan testleri çalıştırır `FullyQualifiedName` içeren `TestClass1` **ve** `Category` olduğu `CategoryA` **veya** `Priority` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="821d7-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="821d7-143">NUnit</span><span class="sxs-lookup"><span data-stu-id="821d7-143">NUnit</span></span>

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

| <span data-ttu-id="821d7-144">İfade</span><span class="sxs-lookup"><span data-stu-id="821d7-144">Expression</span></span> | <span data-ttu-id="821d7-145">Sonuç</span><span class="sxs-lookup"><span data-stu-id="821d7-145">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="821d7-146">Çalıştırmaları testleri `FullyQualifiedName` içeren `Method`.</span><span class="sxs-lookup"><span data-stu-id="821d7-146">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="821d7-147">Kullanılabilir `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="821d7-147">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="821d7-148">Adında içeren çalıştırdığında `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="821d7-148">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="821d7-149">Sınıfta olan testleri çalıştırır `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="821d7-149">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="821d7-150">Dışındaki tüm testleri çalıştırır `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="821d7-150">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="821d7-151">Hangi ile açıklamalı olan testleri çalıştırır `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="821d7-151">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="821d7-152">Hangi ile açıklamalı olan testleri çalıştırır `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="821d7-152">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="821d7-153">**Koşullu işleçler kullanarak | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="821d7-153">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="821d7-154">İfade</span><span class="sxs-lookup"><span data-stu-id="821d7-154">Expression</span></span> | <span data-ttu-id="821d7-155">Sonuç</span><span class="sxs-lookup"><span data-stu-id="821d7-155">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="821d7-156">Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **veya** `TestCategory` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="821d7-156">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="821d7-157">Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **ve** `TestCategory` olduğu `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="821d7-157">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="821d7-158">Ya da olan testleri çalıştırır `FullyQualifiedName` içeren `UnitTest1` **ve** `TestCategory` olduğu `CategoryA` **veya** `Priority` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="821d7-158">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
