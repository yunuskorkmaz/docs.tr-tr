---
title: Seçmeli birim testleri çalıştırma
description: .NET Core 'da DotNet test komutuyla seçmeli birim testlerini çalıştırmak için bir filtre ifadesi kullanma.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: 57428dad2de6c2507ca2cdc42e3df9e83a1edd69
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715455"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="880a8-103">Seçmeli birim testleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="880a8-103">Running selective unit tests</span></span>

<span data-ttu-id="880a8-104">.NET Core 'daki `dotnet test` komutuyla, seçmeli testleri çalıştırmak için bir filtre ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="880a8-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="880a8-105">Bu makalede hangi testin çalıştırılacağını nasıl filtreleneceği gösterilir.</span><span class="sxs-lookup"><span data-stu-id="880a8-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="880a8-106">Aşağıdaki örneklerde `dotnet test`kullanılır.</span><span class="sxs-lookup"><span data-stu-id="880a8-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="880a8-107">`vstest.console.exe`kullanıyorsanız `--filter` `--testcasefilter:`ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="880a8-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="880a8-108">MSTest</span><span class="sxs-lookup"><span data-stu-id="880a8-108">MSTest</span></span>

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

| <span data-ttu-id="880a8-109">İfade</span><span class="sxs-lookup"><span data-stu-id="880a8-109">Expression</span></span> | <span data-ttu-id="880a8-110">Sonuç</span><span class="sxs-lookup"><span data-stu-id="880a8-110">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="880a8-111">`FullyQualifiedName` `Method`içeren testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-111">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="880a8-112">`vstest 15.1+`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="880a8-112">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="880a8-113">Adında `TestMethod1`bulunan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-113">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="880a8-114">`MSTestNamespace.UnitTest1`sınıfında olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-114">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="880a8-115">**Note:** `ClassName` değeri bir ad alanına sahip olmalıdır, bu nedenle `ClassName=UnitTest1` çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="880a8-115">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="880a8-116">`MSTestNamespace.UnitTest1.TestMethod1`hariç tüm testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-116">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="880a8-117">`[TestCategory("CategoryA")]`ile açıklanmış testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-117">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="880a8-118">`[Priority(2)]`ile açıklanmış testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-118">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="880a8-119">**Koşullu işleçleri kullanma | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="880a8-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="880a8-120">İfade</span><span class="sxs-lookup"><span data-stu-id="880a8-120">Expression</span></span> | <span data-ttu-id="880a8-121">Sonuç</span><span class="sxs-lookup"><span data-stu-id="880a8-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="880a8-122">`FullyQualifiedName` `UnitTest1` **veya** `TestCategory` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-122">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="880a8-123">`FullyQualifiedName` `UnitTest1` **ve** `TestCategory` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-123">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="880a8-124">`UnitTest1` içeren `FullyQualifiedName` **ve** `TestCategory` `CategoryA` **ya** da `Priority` 1 olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-124">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="880a8-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="880a8-125">xUnit</span></span>

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

| <span data-ttu-id="880a8-126">İfade</span><span class="sxs-lookup"><span data-stu-id="880a8-126">Expression</span></span> | <span data-ttu-id="880a8-127">Sonuç</span><span class="sxs-lookup"><span data-stu-id="880a8-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="880a8-128">Yalnızca bir test `XUnitNamespace.TestClass1.Test1`çalışır.</span><span class="sxs-lookup"><span data-stu-id="880a8-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="880a8-129">`XUnitNamespace.TestClass1.Test1`hariç tüm testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="880a8-130">Görünen adında `TestClass1`bulunan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="880a8-131">Kod örneğinde, anahtarlar `Category` ve `Priority` ile tanımlanmış nitelikler filtreleme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="880a8-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="880a8-132">İfade</span><span class="sxs-lookup"><span data-stu-id="880a8-132">Expression</span></span> | <span data-ttu-id="880a8-133">Sonuç</span><span class="sxs-lookup"><span data-stu-id="880a8-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="880a8-134">`FullyQualifiedName` `XUnit`içeren testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="880a8-135">`vstest 15.1+`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="880a8-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="880a8-136">`[Trait("Category", "CategoryA")]`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-136">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="880a8-137">**Koşullu işleçleri kullanma | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="880a8-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="880a8-138">İfade</span><span class="sxs-lookup"><span data-stu-id="880a8-138">Expression</span></span> | <span data-ttu-id="880a8-139">Sonuç</span><span class="sxs-lookup"><span data-stu-id="880a8-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="880a8-140">`FullyQualifiedName` `TestClass1` **veya** `Category` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="880a8-141">`FullyQualifiedName` `TestClass1` **ve** `Category` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="880a8-142">`TestClass1` içeren `FullyQualifiedName` **ve** `Category` `CategoryA` **ya** da `Priority` 1 olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="880a8-143">NUnit</span><span class="sxs-lookup"><span data-stu-id="880a8-143">NUnit</span></span>

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

| <span data-ttu-id="880a8-144">İfade</span><span class="sxs-lookup"><span data-stu-id="880a8-144">Expression</span></span> | <span data-ttu-id="880a8-145">Sonuç</span><span class="sxs-lookup"><span data-stu-id="880a8-145">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="880a8-146">`FullyQualifiedName` `Method`içeren testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-146">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="880a8-147">`vstest 15.1+`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="880a8-147">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="880a8-148">Adında `TestMethod1`bulunan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-148">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="880a8-149">`NUnitNamespace.UnitTest1`sınıfında olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-149">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="880a8-150">`NUnitNamespace.UnitTest1.TestMethod1`hariç tüm testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-150">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="880a8-151">`[Category("CategoryA")]`ile açıklanmış testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-151">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="880a8-152">`[Priority(2)]`ile açıklanmış testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-152">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="880a8-153">**Koşullu işleçleri kullanma | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="880a8-153">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="880a8-154">İfade</span><span class="sxs-lookup"><span data-stu-id="880a8-154">Expression</span></span> | <span data-ttu-id="880a8-155">Sonuç</span><span class="sxs-lookup"><span data-stu-id="880a8-155">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="880a8-156">`FullyQualifiedName` `UnitTest1` **veya** `TestCategory` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-156">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="880a8-157">`FullyQualifiedName` `UnitTest1` **ve** `TestCategory` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-157">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="880a8-158">`UnitTest1` içeren `FullyQualifiedName` **ve** `TestCategory` `CategoryA` **ya** da `Priority` 1 olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="880a8-158">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
