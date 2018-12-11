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
# <a name="running-selective-unit-tests"></a>Seçmeli birim testleri çalıştırma

İle `dotnet test` komutu'de .NET Core, seçmeli testleri çalıştırmak için bir filtre ifadesi kullanabilirsiniz. Bu makalede, test çalışması filtrelemek gösterilmektedir. Aşağıdaki örneklerde `dotnet test`. Kullanıyorsanız `vstest.console.exe`, değiştirin `--filter ` ile `--testcasefilter:`.

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

| İfade | Sonuç |
| ---------- | ------ |
| `dotnet test --filter Method` | Çalıştırmaları testleri `FullyQualifiedName` içeren `Method`. Kullanılabilir `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Adında içeren çalıştırdığında `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Sınıfta olan testleri çalıştırır `MSTestNamespace.UnitTest1`.<br>**Not:** `ClassName` Değer olmalıdır bir ad alanı, bu nedenle `ClassName=UnitTest1` çalışmaz. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Dışındaki tüm testleri çalıştırır `MSTestNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Hangi ile açıklamalı olan testleri çalıştırır `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Hangi ile açıklamalı olan testleri çalıştırır `[Priority(2)]`.<br>

**Koşullu işleçler kullanarak | ve &amp;**

| İfade | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **veya** `TestCategory` olduğu `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **ve** `TestCategory` olduğu `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Ya da olan testleri çalıştırır `FullyQualifiedName` içeren `UnitTest1` **ve** `TestCategory` olduğu `CategoryA` **veya** `Priority` 1'dir. |

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

| İfade | Sonuç |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Yalnızca bir test çalıştırmaları `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Dışındaki tüm testleri çalıştırır `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Çalıştırdığında, görünen adı içeren `TestClass1`. |

Kod örneğinde, tanımlanan nitelikler anahtarlarla `Category` ve `Priority` filtrelemek için kullanılabilir.

| İfade | Sonuç |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Çalıştırmaları testleri `FullyQualifiedName` içeren `XUnit`.  Kullanılabilir `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Olan testleri çalıştırır `[Trait("Category", "CategoryA")]`. |

**Koşullu işleçler kullanarak | ve &amp;**

| İfade | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Sahip çalıştırmaları testleri `TestClass1` içinde `FullyQualifiedName` **veya** `Category` olduğu `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Sahip çalıştırmaları testleri `TestClass1` içinde `FullyQualifiedName` **ve** `Category` olduğu `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | Ya da olan testleri çalıştırır `FullyQualifiedName` içeren `TestClass1` **ve** `Category` olduğu `CategoryA` **veya** `Priority` 1'dir. |

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

| İfade | Sonuç |
| ---------- | ------ |
| `dotnet test --filter Method` | Çalıştırmaları testleri `FullyQualifiedName` içeren `Method`. Kullanılabilir `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Adında içeren çalıştırdığında `TestMethod1`. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Sınıfta olan testleri çalıştırır `NUnitNamespace.UnitTest1`.<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Dışındaki tüm testleri çalıştırır `NUnitNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Hangi ile açıklamalı olan testleri çalıştırır `[Category("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Hangi ile açıklamalı olan testleri çalıştırır `[Priority(2)]`.<br>

**Koşullu işleçler kullanarak | ve &amp;**

| İfade | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **veya** `TestCategory` olduğu `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Olan testleri çalıştırır `UnitTest1` içinde `FullyQualifiedName` **ve** `TestCategory` olduğu `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Ya da olan testleri çalıştırır `FullyQualifiedName` içeren `UnitTest1` **ve** `TestCategory` olduğu `CategoryA` **veya** `Priority` 1'dir. |
