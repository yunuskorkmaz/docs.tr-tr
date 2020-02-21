---
title: Seçmeli birim testleri çalıştırma
description: .NET Core 'da DotNet test komutuyla seçmeli birim testlerini çalıştırmak için bir filtre ifadesi kullanma.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543514"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="74093-103">Seçmeli birim testleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="74093-103">Running selective unit tests</span></span>

<span data-ttu-id="74093-104">.NET Core 'daki `dotnet test` komutuyla, seçmeli testleri çalıştırmak için bir filtre ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74093-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="74093-105">Bu makalede hangi testin çalıştırılacağını nasıl filtreleneceği gösterilir.</span><span class="sxs-lookup"><span data-stu-id="74093-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="74093-106">Aşağıdaki örneklerde `dotnet test`kullanılır.</span><span class="sxs-lookup"><span data-stu-id="74093-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="74093-107">`vstest.console.exe`kullanıyorsanız `--filter` `--testcasefilter:`ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="74093-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

> [!NOTE]
> <span data-ttu-id="74093-108">`*nix` ünlem işareti (!) içeren filtrelerin kullanılması `!` ayrıldığından kaçış gerektirir.</span><span class="sxs-lookup"><span data-stu-id="74093-108">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="74093-109">Örneğin, ad alanı ıntegrationtests içeriyorsa, bu filtre tüm testleri atlar: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span><span class="sxs-lookup"><span data-stu-id="74093-109">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
> <span data-ttu-id="74093-110">Ünlem işaretiyle önceki ters eğik çizgiyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="74093-110">Note the backslash that precedes the exclamation mark.</span></span>

## <a name="mstest"></a><span data-ttu-id="74093-111">MSTest</span><span class="sxs-lookup"><span data-stu-id="74093-111">MSTest</span></span>

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

| <span data-ttu-id="74093-112">İfadeler</span><span class="sxs-lookup"><span data-stu-id="74093-112">Expression</span></span> | <span data-ttu-id="74093-113">Sonuç</span><span class="sxs-lookup"><span data-stu-id="74093-113">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="74093-114">`FullyQualifiedName` `Method`içeren testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-114">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="74093-115">`vstest 15.1+`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74093-115">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="74093-116">Adında `TestMethod1`bulunan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-116">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="74093-117">`MSTestNamespace.UnitTest1`sınıfında olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-117">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="74093-118">**Note:** `ClassName` değeri bir ad alanına sahip olmalıdır, bu nedenle `ClassName=UnitTest1` çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="74093-118">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="74093-119">`MSTestNamespace.UnitTest1.TestMethod1`hariç tüm testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-119">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="74093-120">`[TestCategory("CategoryA")]`ile açıklanmış testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-120">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="74093-121">`[Priority(2)]`ile açıklanmış testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-121">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="74093-122">**Koşullu işleçleri kullanma | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="74093-122">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="74093-123">İfadeler</span><span class="sxs-lookup"><span data-stu-id="74093-123">Expression</span></span> | <span data-ttu-id="74093-124">Sonuç</span><span class="sxs-lookup"><span data-stu-id="74093-124">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="74093-125">`FullyQualifiedName` `UnitTest1` **veya** `TestCategory` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-125">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="74093-126">`FullyQualifiedName` `UnitTest1` **ve** `TestCategory` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-126">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="74093-127">`UnitTest1` içeren `FullyQualifiedName` **ve** `TestCategory` `CategoryA` **ya** da `Priority` 1 olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-127">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="74093-128">xUnit</span><span class="sxs-lookup"><span data-stu-id="74093-128">xUnit</span></span>

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

| <span data-ttu-id="74093-129">İfadeler</span><span class="sxs-lookup"><span data-stu-id="74093-129">Expression</span></span> | <span data-ttu-id="74093-130">Sonuç</span><span class="sxs-lookup"><span data-stu-id="74093-130">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="74093-131">Yalnızca bir test `XUnitNamespace.TestClass1.Test1`çalışır.</span><span class="sxs-lookup"><span data-stu-id="74093-131">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="74093-132">`XUnitNamespace.TestClass1.Test1`hariç tüm testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-132">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="74093-133">Görünen adında `TestClass1`bulunan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-133">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="74093-134">Kod örneğinde, anahtarlar `Category` ve `Priority` ile tanımlanmış nitelikler filtreleme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74093-134">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="74093-135">İfadeler</span><span class="sxs-lookup"><span data-stu-id="74093-135">Expression</span></span> | <span data-ttu-id="74093-136">Sonuç</span><span class="sxs-lookup"><span data-stu-id="74093-136">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="74093-137">`FullyQualifiedName` `XUnit`içeren testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-137">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="74093-138">`vstest 15.1+`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74093-138">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="74093-139">`[Trait("Category", "CategoryA")]`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-139">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="74093-140">**Koşullu işleçleri kullanma | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="74093-140">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="74093-141">İfadeler</span><span class="sxs-lookup"><span data-stu-id="74093-141">Expression</span></span> | <span data-ttu-id="74093-142">Sonuç</span><span class="sxs-lookup"><span data-stu-id="74093-142">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="74093-143">`FullyQualifiedName` `TestClass1` **veya** `Category` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-143">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="74093-144">`FullyQualifiedName` `TestClass1` **ve** `Category` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-144">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="74093-145">`TestClass1` içeren `FullyQualifiedName` **ve** `Category` `CategoryA` **ya** da `Priority` 1 olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-145">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="74093-146">NUnit</span><span class="sxs-lookup"><span data-stu-id="74093-146">NUnit</span></span>

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

| <span data-ttu-id="74093-147">İfadeler</span><span class="sxs-lookup"><span data-stu-id="74093-147">Expression</span></span> | <span data-ttu-id="74093-148">Sonuç</span><span class="sxs-lookup"><span data-stu-id="74093-148">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="74093-149">`FullyQualifiedName` `Method`içeren testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-149">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="74093-150">`vstest 15.1+`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74093-150">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="74093-151">Adında `TestMethod1`bulunan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-151">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="74093-152">`NUnitNamespace.UnitTest1`sınıfında olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-152">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="74093-153">`NUnitNamespace.UnitTest1.TestMethod1`hariç tüm testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-153">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="74093-154">`[Category("CategoryA")]`ile açıklanmış testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-154">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="74093-155">`[Priority(2)]`ile açıklanmış testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-155">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="74093-156">**Koşullu işleçleri kullanma | ve &amp;**</span><span class="sxs-lookup"><span data-stu-id="74093-156">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="74093-157">İfadeler</span><span class="sxs-lookup"><span data-stu-id="74093-157">Expression</span></span> | <span data-ttu-id="74093-158">Sonuç</span><span class="sxs-lookup"><span data-stu-id="74093-158">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="74093-159">`FullyQualifiedName` `UnitTest1` **veya** `TestCategory` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-159">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="74093-160">`FullyQualifiedName` `UnitTest1` **ve** `TestCategory` `CategoryA`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-160">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="74093-161">`UnitTest1` içeren `FullyQualifiedName` **ve** `TestCategory` `CategoryA` **ya** da `Priority` 1 olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74093-161">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
