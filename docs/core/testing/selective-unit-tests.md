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
# <a name="running-selective-unit-tests"></a>Seçmeli birim testleri çalıştırma

.NET `dotnet test` Core komutuyla, seçici testleri çalıştırmak için bir filtre ifadesi kullanabilirsiniz. Bu makalede, hangi testin çalıştırıldığı filtrelenir. Aşağıdaki örneklerde `dotnet test`kullanılır. `vstest.console.exe`Kullanıyorsanız, değiştirin. `--filter` `--testcasefilter:`

> [!NOTE]
> Ünlem işareti (!) içeren filtrelerin `*nix` kullanılması, `!` rezerve edildiği için kaçma gerektiğini sürürüyor. Örneğin, ad alanı IntegrationTests içeriyorsa, bu `dotnet test --filter FullyQualifiedName\!~IntegrationTests`filtre tüm testleri atlar: .
> Ünlem işaretinden önce gelen ters çizgiye dikkat edin.

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
| `dotnet test --filter Method` | İçinde `FullyQualifiedName` bulunduğu `Method`testleri çalıştırAn. ' `vstest 15.1+`de mevcuttur. |
| `dotnet test --filter Name~TestMethod1` | Adı içeren `TestMethod1`testleri çalıştırın. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Sınıfta `MSTestNamespace.UnitTest1`olan testleri çalıştırın.<br>**Not:** Değerin `ClassName` bir ad alanı `ClassName=UnitTest1` olması gerekir, bu nedenle çalışmaz. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Hariç `MSTestNamespace.UnitTest1.TestMethod1`tüm testleri çalıştırın |
| `dotnet test --filter TestCategory=CategoryA` | Açıklamalı testleri `[TestCategory("CategoryA")]`çalıştırın. |
| `dotnet test --filter Priority=2` | Açıklamalı testleri `[Priority(2)]`çalıştırın.<br>

**Koşullu işleçleri kullanma | Ve&amp;**

| İfadeler | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Var olan `UnitTest1` `FullyQualifiedName` **veya** `TestCategory` olan `CategoryA`testleri çalıştırın. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Var `UnitTest1` `FullyQualifiedName` **ve** `TestCategory` olan testleri `CategoryA`çalıştırın. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | `FullyQualifiedName` `UnitTest1` İçerdiği **ve** `TestCategory` `CategoryA` 1 olan veya **or** `Priority` olan testleri çalıştırın. |

## <a name="xunit"></a>xBirim

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
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Sadece bir test `XUnitNamespace.TestClass1.Test1`çalıştırın. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Hariç `XUnitNamespace.TestClass1.Test1`tüm testleri çalıştırın |
| `dotnet test --filter DisplayName~TestClass1` | Görüntü adı içeren `TestClass1`testleri çalıştırın. |

Kod örneğinde, anahtarlarla `Category` tanımlanan `Priority` özellikler ve filtreleme için kullanılabilir.

| İfadeler | Sonuç |
| ---------- | ------ |
| `dotnet test --filter XUnit` | İçinde `FullyQualifiedName` bulunduğu `XUnit`testleri çalıştırAn.  ' `vstest 15.1+`de mevcuttur. |
| `dotnet test --filter Category=CategoryA` | Var `[Trait("Category", "CategoryA")]`testleri çalıştırın. |

**Koşullu işleçleri kullanma | Ve&amp;**

| İfadeler | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Var `TestClass1` `FullyQualifiedName` **olan veya** `Category` olan `CategoryA`testleri çalıştırın. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Olan `TestClass1` `FullyQualifiedName` **ve** `Category` olan `CategoryA`testleri çalıştırın. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | `FullyQualifiedName` `TestClass1` İçerdiği **ve** `Category` `CategoryA` 1 olan veya **or** `Priority` olan testleri çalıştırın. |

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
| `dotnet test --filter Method` | İçinde `FullyQualifiedName` bulunduğu `Method`testleri çalıştırAn. ' `vstest 15.1+`de mevcuttur. |
| `dotnet test --filter Name~TestMethod1` | Adı içeren `TestMethod1`testleri çalıştırın. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Sınıfta `NUnitNamespace.UnitTest1`olan testleri çalıştırın.<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Hariç `NUnitNamespace.UnitTest1.TestMethod1`tüm testleri çalıştırın |
| `dotnet test --filter TestCategory=CategoryA` | Açıklamalı testleri `[Category("CategoryA")]`çalıştırın. |
| `dotnet test --filter Priority=2` | Açıklamalı testleri `[Priority(2)]`çalıştırın.<br>

**Koşullu işleçleri kullanma | Ve&amp;**

| İfadeler | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Var olan `UnitTest1` `FullyQualifiedName` **veya** `TestCategory` olan `CategoryA`testleri çalıştırın. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Var `UnitTest1` `FullyQualifiedName` **ve** `TestCategory` olan testleri `CategoryA`çalıştırın. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | `FullyQualifiedName` `UnitTest1` İçerdiği **ve** `TestCategory` `CategoryA` 1 olan veya **or** `Priority` olan testleri çalıştırın. |
