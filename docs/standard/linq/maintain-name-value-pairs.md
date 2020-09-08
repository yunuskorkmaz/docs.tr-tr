---
title: Ad-değer çiftlerini koruma-LINQ to XML
description: LINQ to XML yöntemlerinin bir ad-değer çiftleri kümesini sürdürmek için nasıl kullanılacağını öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 681df91d42f8bdb403dcf6f735104301c4a0c9ba
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553278"
---
# <a name="maintain-name-value-pairs-linq-to-xml"></a>Ad-değer çiftlerini koru (LINQ to XML)

Birçok uygulamanın, ad-değer çiftleri olarak en iyi şekilde tutulan bilgileri tutması gerekir. Bu bilgiler yapılandırma bilgileri veya genel ayarlar olabilir. LINQ to XML, bir ad-değer çiftleri kümesinin korunmasını kolaylaştıran yöntemler içerir. Bilgileri öznitelik olarak veya bir alt öğe kümesi olarak tutabilirsiniz.

Bilgileri öznitelik veya alt öğe olarak tutma arasındaki tek fark, özniteliklerin bir öğe için yalnızca belirli bir ada sahip tek bir öznitelik olabilecek kısıtlamaya sahip olduğu kısıtlamadır. Bu sınırlama alt öğeler için geçerlidir.

## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue ve SetElementValue

Ad-değer çiftlerini tutmaya yardımcı olan iki yöntem <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ve ' dir <xref:System.Xml.Linq.XElement.SetElementValue%2A> . Bu iki yöntem benzer anlamlara sahiptir.

<xref:System.Xml.Linq.XElement.SetAttributeValue%2A> bir öğenin özniteliklerini ekleyebilir, değiştirebilir ve kaldırabilir.

- Mevcut olmayan bir <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> özniteliğin adıyla çağırırsanız, yöntemi yeni bir öznitelik oluşturur ve belirtilen öğeye ekler.
- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>Var olan bir özniteliğin adı ile ve belirtilen içeriklerde bir çağrı yaparsanız, özniteliğin içeriği belirtilen içerikle değiştirilmiştir.
- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>Var olan bir özniteliğin adıyla çağrı yaparsanız ve `null` içerik için öğesini belirtirseniz, özniteliği üst öğesinden kaldırılır.

<xref:System.Xml.Linq.XElement.SetElementValue%2A> bir öğenin alt öğelerini ekleyebilir, değiştirebilir ve kaldırabilir.

- Mevcut olmayan bir <xref:System.Xml.Linq.XElement.SetElementValue%2A> alt öğe adı ile çağırırsanız, yöntemi yeni bir öğesi oluşturur ve belirtilen öğeye ekler.
- Var olan bir <xref:System.Xml.Linq.XElement.SetElementValue%2A> öğenin adı ile ve belirtilen içeriklerle çağırırsanız, öğenin içeriği belirtilen içerikle değiştirilmiştir.
- ' İ <xref:System.Xml.Linq.XElement.SetElementValue%2A> varolan bir öğenin adıyla çağırıp `null` içerik için belirtirseniz, öğesi üst öğesinden kaldırılır.

## <a name="example-use-setattributevalue-to-create-and-maintain-a-list-of-name-value-pairs"></a>Örnek: `SetAttributeValue` ad-değer çiftleri listesini oluşturmak ve korumak Için kullanın

Aşağıdaki örnek, öznitelikleri olmayan bir öğesi oluşturur. Daha sonra, <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ad-değer çiftleri listesini oluşturmak ve korumak için yöntemini kullanır.

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22);
root.SetAttributeValue("Left", 20);
root.SetAttributeValue("Bottom", 122);
root.SetAttributeValue("Right", 300);
root.SetAttributeValue("DefaultColor", "Color.Red");
Console.WriteLine(root);

// Replace the value of Top.
root.SetAttributeValue("Top", 10);
Console.WriteLine(root);

// Remove DefaultColor.
root.SetAttributeValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22)
root.SetAttributeValue("Left", 20)
root.SetAttributeValue("Bottom", 122)
root.SetAttributeValue("Right", 300)
root.SetAttributeValue("DefaultColor", "Color.Red")
Console.WriteLine(root)

' Replace the value of Top.
root.SetAttributeValue("Top", 10)
Console.WriteLine(root)

' Remove DefaultColor.
root.SetAttributeValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" />
```

## <a name="example-use-setelementvalue-to-create-and-maintain-a-list-of-name-value-pairs"></a>Örnek: `SetElementValue` ad-değer çiftleri listesini oluşturmak ve korumak Için kullanın

Aşağıdaki örnek, alt öğeleri olmayan bir öğe oluşturur. Daha sonra, <xref:System.Xml.Linq.XElement.SetElementValue%2A> ad-değer çiftleri listesini oluşturmak ve korumak için yöntemini kullanır.

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22);
root.SetElementValue("Left", 20);
root.SetElementValue("Bottom", 122);
root.SetElementValue("Right", 300);
root.SetElementValue("DefaultColor", "Color.Red");
Console.WriteLine(root);
Console.WriteLine("----");

// Replace the value of Top.
root.SetElementValue("Top", 10);
Console.WriteLine(root);
Console.WriteLine("----");

// Remove DefaultColor.
root.SetElementValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22)
root.SetElementValue("Left", 20)
root.SetElementValue("Bottom", 122)
root.SetElementValue("Right", 300)
root.SetElementValue("DefaultColor", "Color.Red")
Console.WriteLine(root)
Console.WriteLine("----")

' Replace the value of Top.
root.SetElementValue("Top", 10)
Console.WriteLine(root)
Console.WriteLine("----")

' Remove DefaultColor.
root.SetElementValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root>
  <Top>22</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
</Root>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
