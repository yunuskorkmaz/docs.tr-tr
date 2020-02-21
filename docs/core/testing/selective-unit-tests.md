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
# <a name="running-selective-unit-tests"></a>Seçmeli birim testleri çalıştırma

.NET Core 'daki `dotnet test` komutuyla, seçmeli testleri çalıştırmak için bir filtre ifadesi kullanabilirsiniz. Bu makalede hangi testin çalıştırılacağını nasıl filtreleneceği gösterilir. Aşağıdaki örneklerde `dotnet test`kullanılır. `vstest.console.exe`kullanıyorsanız `--filter` `--testcasefilter:`ile değiştirin.

> [!NOTE]
> `*nix` ünlem işareti (!) içeren filtrelerin kullanılması `!` ayrıldığından kaçış gerektirir. Örneğin, ad alanı ıntegrationtests içeriyorsa, bu filtre tüm testleri atlar: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.
> Ünlem işaretiyle önceki ters eğik çizgiyi unutmayın.

## <a name="mstest"></a>MSTest

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

| İfadeler | Sonuç |
| ---------- | ------ |
| `dotnet test --filter Method` | `FullyQualifiedName` `Method`içeren testleri çalıştırır. `vstest 15.1+`kullanılabilir. |
| `dotnet test --filter Name~TestMethod1` | Adında `TestMethod1`bulunan testleri çalıştırır. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | `MSTestNamespace.UnitTest1`sınıfında olan testleri çalıştırır.<br>**Note:** `ClassName` değeri bir ad alanına sahip olmalıdır, bu nedenle `ClassName=UnitTest1` çalışmaz. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | `MSTestNamespace.UnitTest1.TestMethod1`hariç tüm testleri çalıştırır. |
| `dotnet test --filter TestCategory=CategoryA` | `[TestCategory("CategoryA")]`ile açıklanmış testleri çalıştırır. |
| `dotnet test --filter Priority=2` | `[Priority(2)]`ile açıklanmış testleri çalıştırır.<br>

**Koşullu işleçleri kullanma | ve &amp;**

| İfadeler | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | `FullyQualifiedName` `UnitTest1` **veya** `TestCategory` `CategoryA`olan testleri çalıştırır. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | `FullyQualifiedName` `UnitTest1` **ve** `TestCategory` `CategoryA`olan testleri çalıştırır. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | `UnitTest1` içeren `FullyQualifiedName` **ve** `TestCategory` `CategoryA` **ya** da `Priority` 1 olan testleri çalıştırır. |

## <a name="xunit"></a>xUnit

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

| İfadeler | Sonuç |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Yalnızca bir test `XUnitNamespace.TestClass1.Test1`çalışır. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | `XUnitNamespace.TestClass1.Test1`hariç tüm testleri çalıştırır. |
| `dotnet test --filter DisplayName~TestClass1` | Görünen adında `TestClass1`bulunan testleri çalıştırır. |

Kod örneğinde, anahtarlar `Category` ve `Priority` ile tanımlanmış nitelikler filtreleme için kullanılabilir.

| İfadeler | Sonuç |
| ---------- | ------ |
| `dotnet test --filter XUnit` | `FullyQualifiedName` `XUnit`içeren testleri çalıştırır.  `vstest 15.1+`kullanılabilir. |
| `dotnet test --filter Category=CategoryA` | `[Trait("Category", "CategoryA")]`olan testleri çalıştırır. |

**Koşullu işleçleri kullanma | ve &amp;**

| İfadeler | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | `FullyQualifiedName` `TestClass1` **veya** `Category` `CategoryA`olan testleri çalıştırır. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | `FullyQualifiedName` `TestClass1` **ve** `Category` `CategoryA`olan testleri çalıştırır. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | `TestClass1` içeren `FullyQualifiedName` **ve** `Category` `CategoryA` **ya** da `Priority` 1 olan testleri çalıştırır. |

## <a name="nunit"></a>NUnit

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

| İfadeler | Sonuç |
| ---------- | ------ |
| `dotnet test --filter Method` | `FullyQualifiedName` `Method`içeren testleri çalıştırır. `vstest 15.1+`kullanılabilir. |
| `dotnet test --filter Name~TestMethod1` | Adında `TestMethod1`bulunan testleri çalıştırır. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | `NUnitNamespace.UnitTest1`sınıfında olan testleri çalıştırır.<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | `NUnitNamespace.UnitTest1.TestMethod1`hariç tüm testleri çalıştırır. |
| `dotnet test --filter TestCategory=CategoryA` | `[Category("CategoryA")]`ile açıklanmış testleri çalıştırır. |
| `dotnet test --filter Priority=2` | `[Priority(2)]`ile açıklanmış testleri çalıştırır.<br>

**Koşullu işleçleri kullanma | ve &amp;**

| İfadeler | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | `FullyQualifiedName` `UnitTest1` **veya** `TestCategory` `CategoryA`olan testleri çalıştırır. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | `FullyQualifiedName` `UnitTest1` **ve** `TestCategory` `CategoryA`olan testleri çalıştırır. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | `UnitTest1` içeren `FullyQualifiedName` **ve** `TestCategory` `CategoryA` **ya** da `Priority` 1 olan testleri çalıştırır. |
