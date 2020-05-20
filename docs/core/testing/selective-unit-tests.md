---
title: Seçmeli birim testleri çalıştırma
description: .NET Core 'da DotNet test komutuyla seçmeli birim testlerini çalıştırmak için bir filtre ifadesi kullanma.
author: smadala
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 6a6bbb0687742d1e3288d64fb88f6825dc678e28
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702986"
---
# <a name="run-selective-unit-tests"></a><span data-ttu-id="dda73-103">Seçmeli birim testleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dda73-103">Run selective unit tests</span></span>

<span data-ttu-id="dda73-104">[`dotnet test`](../tools/dotnet-test.md).NET Core 'daki komutla, seçmeli testleri çalıştırmak için bir filtre ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dda73-104">With the [`dotnet test`](../tools/dotnet-test.md) command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="dda73-105">Bu makalede hangi testlerin çalıştırılacağını nasıl filtreleneceği gösterilir.</span><span class="sxs-lookup"><span data-stu-id="dda73-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="dda73-106">Aşağıdaki örnekler kullanır `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="dda73-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="dda73-107">Kullanıyorsanız `vstest.console.exe` , `--filter` ile değiştirin `--testcasefilter:` .</span><span class="sxs-lookup"><span data-stu-id="dda73-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="dda73-108">Karakter kaçış</span><span class="sxs-lookup"><span data-stu-id="dda73-108">Character escaping</span></span>

<span data-ttu-id="dda73-109">Ünlem işareti içeren filtrelerin kullanılması `!` `*nix` , ayrılmış olduğundan kaçış gerektirir `!` .</span><span class="sxs-lookup"><span data-stu-id="dda73-109">Using filters that include exclamation mark `!` on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="dda73-110">Örneğin, ad alanı ıntegrationtests içeriyorsa, bu filtre tüm testleri atlar:</span><span class="sxs-lookup"><span data-stu-id="dda73-110">For example, this filter skips all tests if the namespace contains IntegrationTests:</span></span>

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> <span data-ttu-id="dda73-111">Ters eğik çizgi, kaçış karakteri olduğunu göstermek için ünlem işaretiyle önce gelir `\!` .</span><span class="sxs-lookup"><span data-stu-id="dda73-111">The backslash precedes the exclamation mark to indicate it is an escaped character `\!`.</span></span>

<span data-ttu-id="dda73-112">`FullyQualifiedName`Genel tür parametreleri için virgül içeren değerler için, virgülle kaçış `%2C` .</span><span class="sxs-lookup"><span data-stu-id="dda73-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="dda73-113">Örnek:</span><span class="sxs-lookup"><span data-stu-id="dda73-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

:::zone pivot="mstest"

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod, Priority(1), TestCategory("CategoryA")]
        public void TestMethod1()
        {
        }

        [TestMethod, Priority(2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="dda73-114">İfade</span><span class="sxs-lookup"><span data-stu-id="dda73-114">Expression</span></span> | <span data-ttu-id="dda73-115">Sonuç</span><span class="sxs-lookup"><span data-stu-id="dda73-115">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="dda73-116">İçeren testleri çalıştırır <xref:System.Reflection.Module.FullyQualifiedName> `Method` .</span><span class="sxs-lookup"><span data-stu-id="dda73-116">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="dda73-117">Uygulamasında kullanılabilir `vstest 15.1+` .</span><span class="sxs-lookup"><span data-stu-id="dda73-117">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="dda73-118">Adında bulunan testleri çalıştırır `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="dda73-118">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="dda73-119">Sınıfında olan testleri çalıştırır `MSTestNamespace.UnitTest1` .</span><span class="sxs-lookup"><span data-stu-id="dda73-119">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="dda73-120">**Note:** `ClassName`Değer bir ad alanına sahip olmalıdır, bu nedenle `ClassName=UnitTest1` çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="dda73-120">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="dda73-121">Hariç tüm testleri çalıştırır `MSTestNamespace.UnitTest1.TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="dda73-121">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="dda73-122">İle açıklamalı testleri çalıştırır `[TestCategory("CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="dda73-122">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="dda73-123">İle açıklamalı testleri çalıştırır `[Priority(2)]` .</span><span class="sxs-lookup"><span data-stu-id="dda73-123">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="dda73-124">Koşullu işleçleri kullanan örnekler `|` `&` :</span><span class="sxs-lookup"><span data-stu-id="dda73-124">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="dda73-125">Veya içinde olan testleri çalıştırmak için `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="dda73-125">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> is `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="dda73-126">Ve içinde olan testleri çalıştırmak için `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **and** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="dda73-126">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="dda73-127"><xref:System.Reflection.Module.FullyQualifiedName>İçeren `UnitTest1` **ve** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> önceliği olan veya `1` sahibi olan testleri çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="dda73-127">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"` **or** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> with a priority of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="xunit"

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Fact, Trait("Priority", "1"), Trait("Category", "CategoryA")]
        public void Test1()
        {
        }

        [Fact, Trait("Priority", "2")]
        public void Test2()
        {
        }
    }
}
```

| <span data-ttu-id="dda73-128">İfade</span><span class="sxs-lookup"><span data-stu-id="dda73-128">Expression</span></span> | <span data-ttu-id="dda73-129">Sonuç</span><span class="sxs-lookup"><span data-stu-id="dda73-129">Result</span></span> |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="dda73-130">Yalnızca bir test çalıştırır, `XUnitNamespace.TestClass1.Test1` .</span><span class="sxs-lookup"><span data-stu-id="dda73-130">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="dda73-131">Hariç tüm testleri çalıştırır `XUnitNamespace.TestClass1.Test1` .</span><span class="sxs-lookup"><span data-stu-id="dda73-131">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="dda73-132">Görünen adı bulunan testleri çalıştırır `TestClass1` .</span><span class="sxs-lookup"><span data-stu-id="dda73-132">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="dda73-133">Kod örneğinde, anahtarlar ile tanımlanmış nitelikler `"Category"` ve `"Priority"` filtreleme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dda73-133">In the code example, the defined traits with keys `"Category"` and `"Priority"` can be used for filtering.</span></span>

| <span data-ttu-id="dda73-134">İfade</span><span class="sxs-lookup"><span data-stu-id="dda73-134">Expression</span></span> | <span data-ttu-id="dda73-135">Sonuç</span><span class="sxs-lookup"><span data-stu-id="dda73-135">Result</span></span> |
|--|--|
| `dotnet test --filter XUnit` | <span data-ttu-id="dda73-136">İçeren testleri çalıştırır <xref:System.Reflection.Module.FullyQualifiedName> `XUnit` .</span><span class="sxs-lookup"><span data-stu-id="dda73-136">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `XUnit`.</span></span>  <span data-ttu-id="dda73-137">Uygulamasında kullanılabilir `vstest 15.1+` .</span><span class="sxs-lookup"><span data-stu-id="dda73-137">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="dda73-138">Olan testleri çalıştırır `[Trait("Category", "CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="dda73-138">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="dda73-139">Koşullu işleçleri kullanan örnekler `|` `&` :</span><span class="sxs-lookup"><span data-stu-id="dda73-139">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="dda73-140">İçinde olan veya ' ın `TestClass1` <xref:System.Reflection.Module.FullyQualifiedName> **or** `Trait` anahtarı `"Category"` ve değeri olan `"CategoryA"` Testleri çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="dda73-140">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

<span data-ttu-id="dda73-141">`TestClass1`İçinde olan <xref:System.Reflection.Module.FullyQualifiedName> **ve** `Trait` `"Category"` değerleri ve değeri olan `"CategoryA"` Testleri çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="dda73-141">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

<span data-ttu-id="dda73-142"><xref:System.Reflection.Module.FullyQualifiedName>İçeren `TestClass1` **ve** değerine sahip olan ve `Trait` değeri olan `"Category"` `"CategoryA"` **veya** anahtarı `Trait` `"Priority"` ve `1` değeri olan testleri çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="dda73-142">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `TestClass1` **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"` **or** have a `Trait` with a key of `"Priority"` and value of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="nunit"

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Test, Property("Priority", 1), Category("CategoryA")]
        public void TestMethod1()
        {
        }

        [Test, Property("Priority", 2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="dda73-143">İfade</span><span class="sxs-lookup"><span data-stu-id="dda73-143">Expression</span></span> | <span data-ttu-id="dda73-144">Sonuç</span><span class="sxs-lookup"><span data-stu-id="dda73-144">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="dda73-145">İçeren testleri çalıştırır <xref:System.Reflection.Module.FullyQualifiedName> `Method` .</span><span class="sxs-lookup"><span data-stu-id="dda73-145">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="dda73-146">Uygulamasında kullanılabilir `vstest 15.1+` .</span><span class="sxs-lookup"><span data-stu-id="dda73-146">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="dda73-147">Adında bulunan testleri çalıştırır `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="dda73-147">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="dda73-148">Sınıfında olan testleri çalıştırır `NUnitNamespace.UnitTest1` .</span><span class="sxs-lookup"><span data-stu-id="dda73-148">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="dda73-149">Hariç tüm testleri çalıştırır `NUnitNamespace.UnitTest1.TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="dda73-149">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="dda73-150">İle açıklamalı testleri çalıştırır `[Category("CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="dda73-150">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="dda73-151">İle açıklamalı testleri çalıştırır `[Priority(2)]` .</span><span class="sxs-lookup"><span data-stu-id="dda73-151">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="dda73-152">Koşullu işleçleri kullanan örnekler `|` `&` :</span><span class="sxs-lookup"><span data-stu-id="dda73-152">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="dda73-153">Veya içinde olan testleri çalıştırmak için `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **or** `Category` `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="dda73-153">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="dda73-154">Ve içinde olan testleri çalıştırmak için `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **and** `Category` `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="dda73-154">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="dda73-155"><xref:System.Reflection.Module.FullyQualifiedName>İçeren `UnitTest1` **ve '** a sahip olan ve içeren testleri çalıştırmak için `Category` `"CategoryA"` **or** `Property` `"Priority"` `1` .</span><span class="sxs-lookup"><span data-stu-id="dda73-155">To run tests that have either a <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a `Category` of `"CategoryA"` **or** have a `Property` with a `"Priority"` of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

<span data-ttu-id="dda73-156">Daha fazla bilgi için bkz. [TestCase filtresi](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="dda73-156">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

:::zone-end

## <a name="see-also"></a><span data-ttu-id="dda73-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dda73-157">See also</span></span>

- [<span data-ttu-id="dda73-158">dotnet test</span><span class="sxs-lookup"><span data-stu-id="dda73-158">dotnet test</span></span>](../tools/dotnet-test.md)
- [<span data-ttu-id="dda73-159">DotNet test--filtre</span><span class="sxs-lookup"><span data-stu-id="dda73-159">dotnet test --filter</span></span>](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a><span data-ttu-id="dda73-160">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="dda73-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dda73-161">Birim testlerini Sırala</span><span class="sxs-lookup"><span data-stu-id="dda73-161">Order unit tests</span></span>](order-unit-tests.md)
