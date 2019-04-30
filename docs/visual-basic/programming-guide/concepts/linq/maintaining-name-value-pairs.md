---
title: Ad-değer çiftleri (Visual Basic) sağlama
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: 67bde0954b74b7e5145dd2d930e16feb3371a881
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650950"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>Ad/değer çiftleri (Visual Basic) sağlama
Çoğu uygulama iyi ad/değer çiftleri tutulur bilgileri korumak sahip. Bu bilgiler, yapılandırma bilgileri veya genel ayarlar olabilir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ad/değer çiftleri kümesini tutmak kolaylaştıran bazı yöntemler içerir. Öğeleri bilgilerin öznitelikleri veya bir alt kümesi olarak ya da koruyabilir.  
  
 Öznitelikleri veya alt öğeleri olarak bilgi tutma arasında bir fark öznitelikleri bir öğe için belirli bir ada sahip yalnızca bir özniteliği olabilir kısıtlaması olmasıdır. Alt öğeler bu sınırlama geçerli değildir.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue ve SetElementValue  
 Tutma kolaylaştıran iki yöntem adı/değer çiftleri olan <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ve <xref:System.Xml.Linq.XElement.SetElementValue%2A>. Bu iki yöntem, benzer semantiğe sahip.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ekleme, değiştirme veya bir öğenin öznitelikleri kaldırın.  
  
- Eğer <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> yöntemi var olmayan bir öznitelik bir adla yeni bir öznitelik oluşturur ve belirtilen öğeyi ekler.  
  
- Eğer <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> varolan bir özniteliği olan bir ada sahip ve belirtilen bazı içerik, öznitelik içeriğini belirtilen içerik ile değiştirilir.  
  
- Çağırırsanız <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> varolan bir ad özniteliği ve belirtmek için içeriği null öznitelik üst öğesinden da kaldırılır.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A> ekleme, değiştirme veya bir öğenin alt öğeleri kaldırın.  
  
- Eğer <xref:System.Xml.Linq.XElement.SetElementValue%2A> yöntemi bir alt öğenin var olmayan bir adla yeni bir öğe oluşturur ve belirtilen öğeyi ekler.  
  
- Eğer <xref:System.Xml.Linq.XElement.SetElementValue%2A> var olan bir öğenin bir ada sahip ve belirtilen bazı içerik, öğenin içeriğini belirtilen içerik ile değiştirilir.  
  
- Eğer <xref:System.Xml.Linq.XElement.SetElementValue%2A> var olan bir öğe adı ve içerik için null belirtin, üst öğesinden öğe kaldırılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özniteliklere bir öğe oluşturur. Ardından kullanır <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> oluşturmak ve ad/değer çiftlerinin listesini güncelleştirmek için yöntemi.  
  
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
 Aşağıdaki örnek, bir öğe ile hiçbir alt öğeleri oluşturur. Ardından kullanır <xref:System.Xml.Linq.XElement.SetElementValue%2A> oluşturmak ve ad/değer çiftlerinin listesini güncelleştirmek için yöntemi.  
  
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
- [(LINQ to XML) XML ağaçlarını değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
