---
title: Bakımı ad-değer çiftleri (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: ac1e6464618c00cba4ded92492fe4a687e1a25f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="maintaining-namevalue-pairs-c"></a>Bakımı ad/değer çiftleri (C#)
Birçok uygulama, ad/değer çiftleri olarak en iyi şekilde tutulur Bilgi korumanız gerekir. Bu bilgiler, yapılandırma bilgileri veya genel ayarlar olabilir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kolaylaştıran bir ad/değer çifti kümesi tutmak bazı yöntemler içerir. Öğeleri öznitelikler veya alt kümesi olarak bilgi ya da koruyabilir.  
  
 Öznitelikler veya alt öğeleri olarak bilgi tutma arasındaki tek fark öznitelikleri yalnızca bir özniteliği olan bir öğe için belirli bir ad olabilir kısıtlaması olmasıdır. Bu sınırlama alt öğeler için geçerli değildir.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue ve SetElementValue  
 Tutma kolaylaştırmak iki yöntem ad/değer çiftlerine olan <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ve <xref:System.Xml.Linq.XElement.SetElementValue%2A>. Bu iki yöntem benzer bir semantik vardır.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ekleyebilir, değiştirme veya bir öğenin öznitelikleri kaldırabilirsiniz.  
  
-   Çağırırsanız <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> var olmayan bir öznitelik adı, yöntem yeni bir öznitelik oluşturur ve belirtilen öğeyi ekler.  
  
-   Çağırırsanız <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> varolan bir özniteliğe adıyla ve bazı belirtilen içerik, öznitelik içeriğini belirtilen içerikle değiştirilir.  
  
-   Çağırırsanız <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> varolan bir adla özniteliği ve belirtmek içerik için null öznitelik üst öğesinden da kaldırılır.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A> ekleme, değiştirme ve bir öğenin alt öğeleri kaldırın.  
  
-   Çağırırsanız <xref:System.Xml.Linq.XElement.SetElementValue%2A> yöntemi var olmayan bir alt öğesi olan bir adla yeni bir öğesi oluşturur ve belirtilen öğeyi ekler.  
  
-   Çağırırsanız <xref:System.Xml.Linq.XElement.SetElementValue%2A> varolan bir öğenin bir adla ve bazı belirtilen içeriği, öğenin içeriğini belirtilen içerikle değiştirilir.  
  
-   Çağırırsanız <xref:System.Xml.Linq.XElement.SetElementValue%2A> varolan bir öğenin bir adla ve içerik için null belirtin, üst öğesinden öğe kaldırılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özniteliklere bir öğe oluşturur. Daha sonra kullanır <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> oluşturmak ve ad/değer çiftlerinin listesini güncelleştirmek için yöntem.  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as attributes.  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir öğe ile hiçbir alt öğeleri oluşturur. Daha sonra kullanır <xref:System.Xml.Linq.XElement.SetElementValue%2A> oluşturmak ve ad/değer çiftlerinin listesini güncelleştirmek için yöntem.  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as elements.  
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
  
 Bu örnek şu çıkışı üretir:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>  
 [XML ağaçları (LINQ-XML) değiştirme (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
