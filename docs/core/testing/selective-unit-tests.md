---
title: "Çalışan seçmeli birim testleri"
description: "Bir filtre ifadesi dotnet test komutuyla seçmeli birim testleri çalıştırmak için nasıl kullanılacağını gösterir."
keywords: ".NET, .NET core birim testi, seçmeli test"
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13d01272-bbf8-456c-a97a-560001d1a7f2
ms.openlocfilehash: af832d04d2cba530a93710a90701ab119a66deef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="running-selective-unit-tests"></a>Çalışan seçmeli birim testleri

Aşağıdaki örneklerde `dotnet test`. Kullanıyorsanız, `vstest.console.exe`, yerine `--filter ` ile `--testcasefilter:`.

## <a name="mstest"></a>MSTest

```csharp
namespace MSTestNamespace
{
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    [TestClass]
    public class UnitTestClass1
    {
        [Priority(2)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [TestCategory("CategoryA")]
        [Priority(3)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| İfade | Sonuç |
| ---------- | ------ |
| `dotnet test --filter Method` | Çalışmalarını test `FullyQualifiedName` içeren `Method`. Kullanılabilir `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Adında içeren testleri çalıştırır `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | Sınıfında olan testleri çalıştırır `MSTestNamespace.UnitTestClass1`.<br>**Not:** `ClassName` değeri olması gerektiğini bir ad alanı, bu nedenle `ClassName=UnitTestClass1` çalışmaz. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | Dışındaki tüm testleri çalıştırır `MSTestNamespace.UnitTestClass1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | İle Açıklama testleri çalıştırır `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=3` | İle Açıklama testleri çalıştırır `[Priority(3)]`.<br>**Not:** `Priority~3` geçersiz bir değer bir dize değil aynıdır. |

**Koşullu işleçler kullanarak | ve&amp;**

| İfade | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | Olan testleri çalıştırır `UnitTestClass1` içinde `FullyQualifiedName` **veya** `TestCategory` olan `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | Olan testleri çalıştırır `UnitTestClass1` içinde `FullyQualifiedName` **ve** `TestCategory` olan `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | Ya da testleri çalıştırır `FullyQualifiedName` içeren `UnitTestClass1` **ve** `TestCategory` olan `CategoryA` **veya** `Priority` 1'dir. |

## <a name="xunit"></a>xUnit

```csharp
namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "bvt")]
        [Trait("Priority", "1")]
        [Fact]
        public void foo()
        {
        }

        [Trait("Category", "Nightly")]
        [Trait("Priority", "2")]
        [Fact]
        public void bar()
        {
        }
    }
}
```

| İfade | Sonuç |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Yalnızca bir test çalışmaları `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Dışındaki tüm testleri çalıştırır `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Görünen adında içeren testleri çalıştırır `TestClass1`. |

Kod örneğinde, tanımlı nitelikler anahtarlarla `Category` ve `Priority` filtrelemesi için kullanılabilir.

| İfade | Sonuç |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Çalışmalarını test `FullyQualifiedName` içeren `XUnit`.  Kullanılabilir `vstest 15.1+`. |
| `dotnet test --filter Category=bvt` | Olan testleri çalıştırır `[Trait("Category", "bvt")]`. |

**Koşullu işleçler kullanarak | ve&amp;**

| İfade | Sonuç |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | Sahip çalıştırır testleri `TestClass1` içinde `FullyQualifiedName` **veya** `Category` olan `Nightly`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | Sahip çalıştırır testleri `TestClass1` içinde `FullyQualifiedName` **ve** `Category` olan `Nightly`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | Ya da testleri çalıştırır `FullyQualifiedName` içeren `TestClass1` **ve** `Category` olan `CategoryA` **veya** `Priority` 1'dir. |
