---
title: Seçmeli birim testleri çalıştırma
description: .NET Core 'da DotNet test komutuyla seçmeli birim testlerini çalıştırmak için bir filtre ifadesi kullanma.
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: e66455b5ac012114c45d998fae11da7ee769fbe2
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624923"
---
# <a name="running-selective-unit-tests"></a>Seçmeli birim testleri çalıştırma

.NET Core `dotnet test` 'daki komutla, seçmeli testleri çalıştırmak için bir filtre ifadesi kullanabilirsiniz. Bu makalede hangi testin çalıştırılacağını nasıl filtreleneceği gösterilir. Aşağıdaki örnekler kullanır `dotnet test`. Kullanıyorsanız `vstest.console.exe`, ile `--filter` `--testcasefilter:`değiştirin.

## <a name="character-escaping"></a>Karakter kaçış

' De `*nix` ünlem işareti (!) içeren filtrelerin kullanılması `!` , ayrılmış olduğundan kaçış gerektirir. Örneğin, ad alanı ıntegrationtests içeriyorsa, bu filtre tüm testleri atlar: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.
Ünlem işaretiyle önceki ters eğik çizgiyi unutmayın.

Genel `FullyQualifiedName` tür parametreleri için virgül içeren değerler için, virgülle kaçış `%2C`. Örneğin:

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

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
| `dotnet test --filter Method` | `FullyQualifiedName` İçeren `Method`testleri çalıştırır. Uygulamasında `vstest 15.1+`kullanılabilir. |
| `dotnet test --filter Name~TestMethod1` | Adında bulunan testleri çalıştırır `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Sınıfında `MSTestNamespace.UnitTest1`olan testleri çalıştırır.<br>**Note:** `ClassName` Değer bir ad alanına sahip olmalıdır, bu `ClassName=UnitTest1` nedenle çalışmaz. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Hariç `MSTestNamespace.UnitTest1.TestMethod1`tüm testleri çalıştırır. |
| `dotnet test --filter TestCategory=CategoryA` | İle `[TestCategory("CategoryA")]`açıklama eklenen testleri çalıştırır. |
| `dotnet test --filter Priority=2` | İle `[Priority(2)]`açıklama eklenen testleri çalıştırır.<br>

**Koşullu işleçleri kullanma | '&amp;**

| İfadeler | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | `UnitTest1` `FullyQualifiedName` **Veya** içinde olan testleri çalıştırır `CategoryA` `TestCategory` |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | `UnitTest1` `FullyQualifiedName` **Ve** içinde olan testleri çalıştırır `CategoryA` `TestCategory` |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | İçeren `FullyQualifiedName` `UnitTest1` **ve** `Priority` ya da 1 olan testleri çalıştırır. **or** `TestCategory` `CategoryA` |

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
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Yalnızca bir test çalıştırır, `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Hariç `XUnitNamespace.TestClass1.Test1`tüm testleri çalıştırır. |
| `dotnet test --filter DisplayName~TestClass1` | Görünen adı bulunan testleri çalıştırır `TestClass1`. |

Kod örneğinde, anahtarlar `Category` ile tanımlanmış nitelikler ve `Priority` filtreleme için kullanılabilir.

| İfadeler | Sonuç |
| ---------- | ------ |
| `dotnet test --filter XUnit` | `FullyQualifiedName` İçeren `XUnit`testleri çalıştırır.  Uygulamasında `vstest 15.1+`kullanılabilir. |
| `dotnet test --filter Category=CategoryA` | Olan testleri çalıştırır `[Trait("Category", "CategoryA")]`. |

**Koşullu işleçleri kullanma | '&amp;**

| İfadeler | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | `TestClass1` `FullyQualifiedName` **Veya** içinde olan testleri çalıştırır `CategoryA` `Category` |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | `TestClass1` `FullyQualifiedName` **Ve** içinde olan testleri çalıştırır `CategoryA` `Category` |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | İçeren `FullyQualifiedName` `TestClass1` **ve** `Priority` ya da 1 olan testleri çalıştırır. **or** `Category` `CategoryA` |

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
| `dotnet test --filter Method` | `FullyQualifiedName` İçeren `Method`testleri çalıştırır. Uygulamasında `vstest 15.1+`kullanılabilir. |
| `dotnet test --filter Name~TestMethod1` | Adında bulunan testleri çalıştırır `TestMethod1`. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Sınıfında `NUnitNamespace.UnitTest1`olan testleri çalıştırır.<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Hariç `NUnitNamespace.UnitTest1.TestMethod1`tüm testleri çalıştırır. |
| `dotnet test --filter TestCategory=CategoryA` | İle `[Category("CategoryA")]`açıklama eklenen testleri çalıştırır. |
| `dotnet test --filter Priority=2` | İle `[Priority(2)]`açıklama eklenen testleri çalıştırır.<br>

**Koşullu işleçleri kullanma | '&amp;**

| İfadeler | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | `UnitTest1` `FullyQualifiedName` **Veya** içinde olan testleri çalıştırır `CategoryA` `TestCategory` |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | `UnitTest1` `FullyQualifiedName` **Ve** içinde olan testleri çalıştırır `CategoryA` `TestCategory` |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | İçeren `FullyQualifiedName` `UnitTest1` **ve** `Priority` ya da 1 olan testleri çalıştırır. **or** `TestCategory` `CategoryA` |

Daha fazla bilgi için bkz. [TestCase filtresi](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).
