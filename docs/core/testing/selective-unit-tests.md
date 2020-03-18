---
title: Seçmeli birim testleri çalıştırma
description: .NET Core'daki dotnet test komutuyla seçici birim testleri çalıştırmak için filtre ifadesi nasıl kullanılır?
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543514"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="6bce6-103">Seçmeli birim testleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="6bce6-103">Running selective unit tests</span></span>

<span data-ttu-id="6bce6-104">.NET `dotnet test` Core komutuyla, seçici testleri çalıştırmak için bir filtre ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bce6-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="6bce6-105">Bu makalede, hangi testin çalıştırıldığı filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="6bce6-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="6bce6-106">Aşağıdaki örneklerde `dotnet test`kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6bce6-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="6bce6-107">`vstest.console.exe`Kullanıyorsanız, değiştirin. `--filter` `--testcasefilter:`</span><span class="sxs-lookup"><span data-stu-id="6bce6-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

> [!NOTE]
> <span data-ttu-id="6bce6-108">Ünlem işareti (!) içeren filtrelerin `*nix` kullanılması, `!` rezerve edildiği için kaçma gerektiğini sürürüyor.</span><span class="sxs-lookup"><span data-stu-id="6bce6-108">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="6bce6-109">Örneğin, ad alanı IntegrationTests içeriyorsa, bu `dotnet test --filter FullyQualifiedName\!~IntegrationTests`filtre tüm testleri atlar: .</span><span class="sxs-lookup"><span data-stu-id="6bce6-109">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
> <span data-ttu-id="6bce6-110">Ünlem işaretinden önce gelen ters çizgiye dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6bce6-110">Note the backslash that precedes the exclamation mark.</span></span>

## <a name="mstest"></a><span data-ttu-id="6bce6-111">MSTest</span><span class="sxs-lookup"><span data-stu-id="6bce6-111">MSTest</span></span>

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

| <span data-ttu-id="6bce6-112">İfadeler</span><span class="sxs-lookup"><span data-stu-id="6bce6-112">Expression</span></span> | <span data-ttu-id="6bce6-113">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bce6-113">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="6bce6-114">İçinde `FullyQualifiedName` bulunduğu `Method`testleri çalıştırAn.</span><span class="sxs-lookup"><span data-stu-id="6bce6-114">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="6bce6-115">' `vstest 15.1+`de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="6bce6-115">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="6bce6-116">Adı içeren `TestMethod1`testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-116">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="6bce6-117">Sınıfta `MSTestNamespace.UnitTest1`olan testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-117">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="6bce6-118">**Not:** Değerin `ClassName` bir ad alanı `ClassName=UnitTest1` olması gerekir, bu nedenle çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="6bce6-118">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="6bce6-119">Hariç `MSTestNamespace.UnitTest1.TestMethod1`tüm testleri çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6bce6-119">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="6bce6-120">Açıklamalı testleri `[TestCategory("CategoryA")]`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-120">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="6bce6-121">Açıklamalı testleri `[Priority(2)]`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-121">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="6bce6-122">**Koşullu işleçleri kullanma | Ve&amp;**</span><span class="sxs-lookup"><span data-stu-id="6bce6-122">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="6bce6-123">İfadeler</span><span class="sxs-lookup"><span data-stu-id="6bce6-123">Expression</span></span> | <span data-ttu-id="6bce6-124">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bce6-124">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="6bce6-125">Var olan `UnitTest1` `FullyQualifiedName` **veya** `TestCategory` olan `CategoryA`testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-125">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="6bce6-126">Var `UnitTest1` `FullyQualifiedName` **ve** `TestCategory` olan testleri `CategoryA`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-126">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="6bce6-127">`FullyQualifiedName` `UnitTest1` İçerdiği **ve** `TestCategory` `CategoryA` 1 olan veya **or** `Priority` olan testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-127">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="6bce6-128">xBirim</span><span class="sxs-lookup"><span data-stu-id="6bce6-128">xUnit</span></span>

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

| <span data-ttu-id="6bce6-129">İfadeler</span><span class="sxs-lookup"><span data-stu-id="6bce6-129">Expression</span></span> | <span data-ttu-id="6bce6-130">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bce6-130">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="6bce6-131">Sadece bir test `XUnitNamespace.TestClass1.Test1`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-131">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="6bce6-132">Hariç `XUnitNamespace.TestClass1.Test1`tüm testleri çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6bce6-132">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="6bce6-133">Görüntü adı içeren `TestClass1`testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-133">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="6bce6-134">Kod örneğinde, anahtarlarla `Category` tanımlanan `Priority` özellikler ve filtreleme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6bce6-134">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="6bce6-135">İfadeler</span><span class="sxs-lookup"><span data-stu-id="6bce6-135">Expression</span></span> | <span data-ttu-id="6bce6-136">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bce6-136">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="6bce6-137">İçinde `FullyQualifiedName` bulunduğu `XUnit`testleri çalıştırAn.</span><span class="sxs-lookup"><span data-stu-id="6bce6-137">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="6bce6-138">' `vstest 15.1+`de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="6bce6-138">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="6bce6-139">Var `[Trait("Category", "CategoryA")]`testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-139">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="6bce6-140">**Koşullu işleçleri kullanma | Ve&amp;**</span><span class="sxs-lookup"><span data-stu-id="6bce6-140">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="6bce6-141">İfadeler</span><span class="sxs-lookup"><span data-stu-id="6bce6-141">Expression</span></span> | <span data-ttu-id="6bce6-142">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bce6-142">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="6bce6-143">Var `TestClass1` `FullyQualifiedName` **olan veya** `Category` olan `CategoryA`testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-143">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="6bce6-144">Olan `TestClass1` `FullyQualifiedName` **ve** `Category` olan `CategoryA`testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-144">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="6bce6-145">`FullyQualifiedName` `TestClass1` İçerdiği **ve** `Category` `CategoryA` 1 olan veya **or** `Priority` olan testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-145">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="6bce6-146">NUnit</span><span class="sxs-lookup"><span data-stu-id="6bce6-146">NUnit</span></span>

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

| <span data-ttu-id="6bce6-147">İfadeler</span><span class="sxs-lookup"><span data-stu-id="6bce6-147">Expression</span></span> | <span data-ttu-id="6bce6-148">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bce6-148">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="6bce6-149">İçinde `FullyQualifiedName` bulunduğu `Method`testleri çalıştırAn.</span><span class="sxs-lookup"><span data-stu-id="6bce6-149">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="6bce6-150">' `vstest 15.1+`de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="6bce6-150">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="6bce6-151">Adı içeren `TestMethod1`testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-151">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="6bce6-152">Sınıfta `NUnitNamespace.UnitTest1`olan testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-152">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="6bce6-153">Hariç `NUnitNamespace.UnitTest1.TestMethod1`tüm testleri çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6bce6-153">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="6bce6-154">Açıklamalı testleri `[Category("CategoryA")]`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-154">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="6bce6-155">Açıklamalı testleri `[Priority(2)]`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-155">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="6bce6-156">**Koşullu işleçleri kullanma | Ve&amp;**</span><span class="sxs-lookup"><span data-stu-id="6bce6-156">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="6bce6-157">İfadeler</span><span class="sxs-lookup"><span data-stu-id="6bce6-157">Expression</span></span> | <span data-ttu-id="6bce6-158">Sonuç</span><span class="sxs-lookup"><span data-stu-id="6bce6-158">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="6bce6-159">Var olan `UnitTest1` `FullyQualifiedName` **veya** `TestCategory` olan `CategoryA`testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-159">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="6bce6-160">Var `UnitTest1` `FullyQualifiedName` **ve** `TestCategory` olan testleri `CategoryA`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-160">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="6bce6-161">`FullyQualifiedName` `UnitTest1` İçerdiği **ve** `TestCategory` `CategoryA` 1 olan veya **or** `Priority` olan testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6bce6-161">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
