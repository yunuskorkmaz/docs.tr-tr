---
title: Ad-Değer Çiftleri Sağlama
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: ed9c7f0aae2fe646cd723321f45455f89dd7c370
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331659"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>Ad/değer çiftlerini koruma (Visual Basic)
Birçok uygulamanın ad/değer çiftleri olarak en iyi şekilde tutulan bilgileri tutması gerekir. Bu bilgiler yapılandırma bilgileri veya genel ayarlar olabilir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bir ad/değer çiftleri kümesini saklamayı kolaylaştıran bazı yöntemler içerir. Bilgileri öznitelik olarak veya bir alt öğe kümesi olarak tutabilirsiniz.  
  
 Bilgileri öznitelik veya alt öğe olarak tutma arasındaki tek fark, özniteliklerin bir öğe için yalnızca belirli bir ada sahip tek bir öznitelik olabilecek kısıtlamaya sahip olduğu kısıtlamadır. Bu sınırlama alt öğeler için geçerlidir.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue ve SetElementValue  
 Ad/değer çiftlerini tutmaya yardımcı olan iki yöntem <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ve <xref:System.Xml.Linq.XElement.SetElementValue%2A>. Bu iki yöntem benzer anlamlara sahiptir.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> bir öğenin özniteliklerini ekleyebilir, değiştirebilir veya kaldırabilir.  
  
- Mevcut olmayan bir özniteliğin adıyla <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> çağırırsanız, yöntemi yeni bir öznitelik oluşturur ve belirtilen öğeye ekler.  
  
- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> var olan bir özniteliğin adı ve belirtilen içeriklerle çağırırsanız, özniteliğin içeriği belirtilen içerikle değiştirilmiştir.  
  
- Var olan bir özniteliğin adıyla <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> çağırırsanız ve içerik için null belirtirseniz, öznitelik üst öğesinden kaldırılır.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A> bir öğenin alt öğelerini ekleyebilir, değiştirebilir veya kaldırabilir.  
  
- Mevcut olmayan bir alt öğe adı ile <xref:System.Xml.Linq.XElement.SetElementValue%2A> çağırırsanız, yöntem yeni bir öğe oluşturur ve belirtilen öğeye ekler.  
  
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>, var olan bir öğenin adı ve belirtilen içeriklerle çağırırsanız, öğenin içeriği belirtilen içerikle değiştirilmiştir.  
  
- <xref:System.Xml.Linq.XElement.SetElementValue%2A> var olan bir öğenin adıyla çağırırsanız ve içerik için null belirtirseniz, öğe üst öğesinden kaldırılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öznitelikleri olmayan bir öğesi oluşturur. Daha sonra ad/değer çiftleri listesini oluşturmak ve korumak için <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> yöntemini kullanır.  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
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
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, alt öğeleri olmayan bir öğe oluşturur. Daha sonra ad/değer çiftleri listesini oluşturmak ve korumak için <xref:System.Xml.Linq.XElement.SetElementValue%2A> yöntemini kullanır.  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
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
- [XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
