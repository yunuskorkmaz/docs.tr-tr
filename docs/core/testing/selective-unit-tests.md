---
title: Seçmeli birim testleri çalıştırma
description: .NET Core 'da DotNet test komutuyla seçmeli birim testlerini çalıştırmak için bir filtre ifadesi kullanma.
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: 50642126f3b470180ddd303ed4a2d2d90bfa5b8f
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728190"
---
# <a name="run-selective-unit-tests"></a><span data-ttu-id="34407-103">Seçmeli birim testleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="34407-103">Run selective unit tests</span></span>

<span data-ttu-id="34407-104">.NET Core `dotnet test` 'daki komutla, seçmeli testleri çalıştırmak için bir filtre ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34407-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="34407-105">Bu makalede hangi testlerin çalıştırılacağını nasıl filtreleneceği gösterilir.</span><span class="sxs-lookup"><span data-stu-id="34407-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="34407-106">Aşağıdaki örnekler kullanır `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="34407-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="34407-107">Kullanıyorsanız `vstest.console.exe`, ile `--filter` `--testcasefilter:`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="34407-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="34407-108">Karakter kaçış</span><span class="sxs-lookup"><span data-stu-id="34407-108">Character escaping</span></span>

<span data-ttu-id="34407-109">' De `*nix` ünlem işareti (!) içeren filtrelerin kullanılması `!` , ayrılmış olduğundan kaçış gerektirir.</span><span class="sxs-lookup"><span data-stu-id="34407-109">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="34407-110">Örneğin, ad alanı ıntegrationtests içeriyorsa, bu filtre tüm testleri atlar: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span><span class="sxs-lookup"><span data-stu-id="34407-110">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
<span data-ttu-id="34407-111">Ünlem işaretiyle önceki ters eğik çizgiyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="34407-111">Note the backslash that precedes the exclamation mark.</span></span>

<span data-ttu-id="34407-112">Genel `FullyQualifiedName` tür parametreleri için virgül içeren değerler için, virgülle kaçış `%2C`.</span><span class="sxs-lookup"><span data-stu-id="34407-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="34407-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="34407-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a><span data-ttu-id="34407-114">MSTest</span><span class="sxs-lookup"><span data-stu-id="34407-114">MSTest</span></span>

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

| <span data-ttu-id="34407-115">İfadeler</span><span class="sxs-lookup"><span data-stu-id="34407-115">Expression</span></span> | <span data-ttu-id="34407-116">Sonuç</span><span class="sxs-lookup"><span data-stu-id="34407-116">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="34407-117">`FullyQualifiedName` İçeren `Method`testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-117">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="34407-118">Uygulamasında `vstest 15.1+`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34407-118">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="34407-119">Adında bulunan testleri çalıştırır `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="34407-119">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="34407-120">Sınıfında `MSTestNamespace.UnitTest1`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-120">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="34407-121">**Note:** `ClassName` Değer bir ad alanına sahip olmalıdır, bu `ClassName=UnitTest1` nedenle çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="34407-121">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="34407-122">Hariç `MSTestNamespace.UnitTest1.TestMethod1`tüm testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-122">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="34407-123">İle `[TestCategory("CategoryA")]`açıklamalı testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-123">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="34407-124">İle `[Priority(2)]`açıklamalı testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-124">Runs tests that are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="34407-125">**Koşullu işleçleri kullanma | '&amp;**</span><span class="sxs-lookup"><span data-stu-id="34407-125">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="34407-126">İfadeler</span><span class="sxs-lookup"><span data-stu-id="34407-126">Expression</span></span> | <span data-ttu-id="34407-127">Sonuç</span><span class="sxs-lookup"><span data-stu-id="34407-127">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="34407-128">`UnitTest1` `FullyQualifiedName` **or** Veya `TestCategory` olan testleri çalıştırır `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="34407-128">Runs tests that have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="34407-129">`UnitTest1` `FullyQualifiedName` **Ve** içinde olan testleri çalıştırır `CategoryA` `TestCategory`</span><span class="sxs-lookup"><span data-stu-id="34407-129">Runs tests that have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="34407-130">İçeren `FullyQualifiedName` `UnitTest1` **ve** `Priority` ya da 1 olan testleri çalıştırır. **or** `TestCategory` `CategoryA`</span><span class="sxs-lookup"><span data-stu-id="34407-130">Runs tests that have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="34407-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="34407-131">xUnit</span></span>

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

| <span data-ttu-id="34407-132">İfadeler</span><span class="sxs-lookup"><span data-stu-id="34407-132">Expression</span></span> | <span data-ttu-id="34407-133">Sonuç</span><span class="sxs-lookup"><span data-stu-id="34407-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="34407-134">Yalnızca bir test çalıştırır, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="34407-134">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="34407-135">Hariç `XUnitNamespace.TestClass1.Test1`tüm testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-135">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="34407-136">Görünen adı bulunan testleri çalıştırır `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="34407-136">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="34407-137">Kod örneğinde, anahtarlar `Category` ile tanımlanmış nitelikler ve `Priority` filtreleme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34407-137">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="34407-138">İfadeler</span><span class="sxs-lookup"><span data-stu-id="34407-138">Expression</span></span> | <span data-ttu-id="34407-139">Sonuç</span><span class="sxs-lookup"><span data-stu-id="34407-139">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="34407-140">`FullyQualifiedName` İçeren `XUnit`testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-140">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="34407-141">Uygulamasında `vstest 15.1+`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34407-141">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="34407-142">Olan testleri çalıştırır `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="34407-142">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="34407-143">**Koşullu işleçleri kullanma | '&amp;**</span><span class="sxs-lookup"><span data-stu-id="34407-143">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="34407-144">İfadeler</span><span class="sxs-lookup"><span data-stu-id="34407-144">Expression</span></span> | <span data-ttu-id="34407-145">Sonuç</span><span class="sxs-lookup"><span data-stu-id="34407-145">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="34407-146">`TestClass1` `FullyQualifiedName` **or** Veya `Category` olan testleri çalıştırır `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="34407-146">Runs tests that have `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="34407-147">`TestClass1` `FullyQualifiedName` **Ve** içinde olan testleri çalıştırır `CategoryA` `Category`</span><span class="sxs-lookup"><span data-stu-id="34407-147">Runs tests that have `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="34407-148">İçeren `FullyQualifiedName` `TestClass1` **ve** `Priority` ya da 1 olan testleri çalıştırır. **or** `Category` `CategoryA`</span><span class="sxs-lookup"><span data-stu-id="34407-148">Runs tests that have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="34407-149">NUnit</span><span class="sxs-lookup"><span data-stu-id="34407-149">NUnit</span></span>

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

| <span data-ttu-id="34407-150">İfadeler</span><span class="sxs-lookup"><span data-stu-id="34407-150">Expression</span></span> | <span data-ttu-id="34407-151">Sonuç</span><span class="sxs-lookup"><span data-stu-id="34407-151">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="34407-152">`FullyQualifiedName` İçeren `Method`testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-152">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="34407-153">Uygulamasında `vstest 15.1+`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34407-153">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="34407-154">Adında bulunan testleri çalıştırır `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="34407-154">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="34407-155">Sınıfında `NUnitNamespace.UnitTest1`olan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-155">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="34407-156">Hariç `NUnitNamespace.UnitTest1.TestMethod1`tüm testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-156">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="34407-157">İle `[Category("CategoryA")]`açıklamalı testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-157">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="34407-158">İle `[Priority(2)]`açıklamalı testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="34407-158">Runs tests that are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="34407-159">**Koşullu işleçleri kullanma | '&amp;**</span><span class="sxs-lookup"><span data-stu-id="34407-159">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="34407-160">İfadeler</span><span class="sxs-lookup"><span data-stu-id="34407-160">Expression</span></span> | <span data-ttu-id="34407-161">Sonuç</span><span class="sxs-lookup"><span data-stu-id="34407-161">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="34407-162">`UnitTest1` `FullyQualifiedName` **or** Veya `TestCategory` olan testleri çalıştırır `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="34407-162">Runs tests that have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="34407-163">`UnitTest1` `FullyQualifiedName` **Ve** içinde olan testleri çalıştırır `CategoryA` `TestCategory`</span><span class="sxs-lookup"><span data-stu-id="34407-163">Runs tests that have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="34407-164">İçeren `FullyQualifiedName` `UnitTest1` **ve** `Priority` ya da 1 olan testleri çalıştırır. **or** `TestCategory` `CategoryA`</span><span class="sxs-lookup"><span data-stu-id="34407-164">Runs tests that have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

<span data-ttu-id="34407-165">Daha fazla bilgi için bkz. [TestCase filtresi](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="34407-165">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>
