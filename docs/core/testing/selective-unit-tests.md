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
# <a name="run-selective-unit-tests"></a>Seçmeli birim testleri çalıştırma

[`dotnet test`](../tools/dotnet-test.md).NET Core 'daki komutla, seçmeli testleri çalıştırmak için bir filtre ifadesi kullanabilirsiniz. Bu makalede hangi testlerin çalıştırılacağını nasıl filtreleneceği gösterilir. Aşağıdaki örnekler kullanır `dotnet test` . Kullanıyorsanız `vstest.console.exe` , `--filter` ile değiştirin `--testcasefilter:` .

## <a name="character-escaping"></a>Karakter kaçış

Ünlem işareti içeren filtrelerin kullanılması `!` `*nix` , ayrılmış olduğundan kaçış gerektirir `!` . Örneğin, ad alanı ıntegrationtests içeriyorsa, bu filtre tüm testleri atlar:

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> Ters eğik çizgi, kaçış karakteri olduğunu göstermek için ünlem işaretiyle önce gelir `\!` .

`FullyQualifiedName`Genel tür parametreleri için virgül içeren değerler için, virgülle kaçış `%2C` . Örnek:

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

| İfade | Sonuç |
|--|--|
| `dotnet test --filter Method` | İçeren testleri çalıştırır <xref:System.Reflection.Module.FullyQualifiedName> `Method` . Uygulamasında kullanılabilir `vstest 15.1+` . |
| `dotnet test --filter Name~TestMethod1` | Adında bulunan testleri çalıştırır `TestMethod1` . |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Sınıfında olan testleri çalıştırır `MSTestNamespace.UnitTest1` .<br>**Note:** `ClassName`Değer bir ad alanına sahip olmalıdır, bu nedenle `ClassName=UnitTest1` çalışmaz. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Hariç tüm testleri çalıştırır `MSTestNamespace.UnitTest1.TestMethod1` . |
| `dotnet test --filter TestCategory=CategoryA` | İle açıklamalı testleri çalıştırır `[TestCategory("CategoryA")]` . |
| `dotnet test --filter Priority=2` | İle açıklamalı testleri çalıştırır `[Priority(2)]` . |

Koşullu işleçleri kullanan örnekler `|` `&` :

Veya içinde olan testleri çalıştırmak için `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Ve içinde olan testleri çalıştırmak için `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **and** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<xref:System.Reflection.Module.FullyQualifiedName>İçeren `UnitTest1` **ve** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> önceliği olan veya `1` sahibi olan testleri çalıştırmak için.

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

| İfade | Sonuç |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Yalnızca bir test çalıştırır, `XUnitNamespace.TestClass1.Test1` . |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Hariç tüm testleri çalıştırır `XUnitNamespace.TestClass1.Test1` . |
| `dotnet test --filter DisplayName~TestClass1` | Görünen adı bulunan testleri çalıştırır `TestClass1` . |

Kod örneğinde, anahtarlar ile tanımlanmış nitelikler `"Category"` ve `"Priority"` filtreleme için kullanılabilir.

| İfade | Sonuç |
|--|--|
| `dotnet test --filter XUnit` | İçeren testleri çalıştırır <xref:System.Reflection.Module.FullyQualifiedName> `XUnit` .  Uygulamasında kullanılabilir `vstest 15.1+` . |
| `dotnet test --filter Category=CategoryA` | Olan testleri çalıştırır `[Trait("Category", "CategoryA")]` . |

Koşullu işleçleri kullanan örnekler `|` `&` :

İçinde olan veya ' ın `TestClass1` <xref:System.Reflection.Module.FullyQualifiedName> **or** `Trait` anahtarı `"Category"` ve değeri olan `"CategoryA"` Testleri çalıştırmak için.

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

`TestClass1`İçinde olan <xref:System.Reflection.Module.FullyQualifiedName> **ve** `Trait` `"Category"` değerleri ve değeri olan `"CategoryA"` Testleri çalıştırmak için.

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

<xref:System.Reflection.Module.FullyQualifiedName>İçeren `TestClass1` **ve** değerine sahip olan ve `Trait` değeri olan `"Category"` `"CategoryA"` **veya** anahtarı `Trait` `"Priority"` ve `1` değeri olan testleri çalıştırmak için.

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

| İfade | Sonuç |
|--|--|
| `dotnet test --filter Method` | İçeren testleri çalıştırır <xref:System.Reflection.Module.FullyQualifiedName> `Method` . Uygulamasında kullanılabilir `vstest 15.1+` . |
| `dotnet test --filter Name~TestMethod1` | Adında bulunan testleri çalıştırır `TestMethod1` . |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Sınıfında olan testleri çalıştırır `NUnitNamespace.UnitTest1` . |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Hariç tüm testleri çalıştırır `NUnitNamespace.UnitTest1.TestMethod1` . |
| `dotnet test --filter TestCategory=CategoryA` | İle açıklamalı testleri çalıştırır `[Category("CategoryA")]` . |
| `dotnet test --filter Priority=2` | İle açıklamalı testleri çalıştırır `[Priority(2)]` . |

Koşullu işleçleri kullanan örnekler `|` `&` :

Veya içinde olan testleri çalıştırmak için `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **or** `Category` `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Ve içinde olan testleri çalıştırmak için `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **and** `Category` `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<xref:System.Reflection.Module.FullyQualifiedName>İçeren `UnitTest1` **ve '** a sahip olan ve içeren testleri çalıştırmak için `Category` `"CategoryA"` **or** `Property` `"Priority"` `1` .

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

Daha fazla bilgi için bkz. [TestCase filtresi](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

:::zone-end

## <a name="see-also"></a>Ayrıca bkz.

- [dotnet test](../tools/dotnet-test.md)
- [DotNet test--filtre](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Birim testlerini Sırala](order-unit-tests.md)
