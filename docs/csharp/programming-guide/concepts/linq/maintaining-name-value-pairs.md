---
title: Ad Değeri Çiftlerini Koruma (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 9c42a154a4c3ed1463e428faab4c7d33197ef4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591704"
---
# <a name="maintaining-namevalue-pairs-c"></a>Ad/Değer Çiftlerinin Bakımı (C#)
Birçok uygulama, ad/değer çiftleri olarak en iyi tutulan bilgileri korumak zorunda. Bu bilgiler yapılandırma bilgileri veya genel ayarlar olabilir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ad/değer çiftleri kümesini tutmayı kolaylaştıran bazı yöntemler içerir. Bilgileri öznitelik olarak veya alt öğeler kümesi olarak saklayabilirsiniz.  
  
 Bilgileri öznitelik olarak veya alt öğe olarak tutmak arasındaki fark, özniteliklerin bir öğe için belirli bir ada sahip yalnızca bir öznitelik olabileceği kısıtlaması olmasıdır. Bu sınırlama alt öğeler için geçerli değildir.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue ve SetElementValue  
 Ad/değer çiftleri tutmayı kolaylaştıran <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> iki <xref:System.Xml.Linq.XElement.SetElementValue%2A>yöntem ve . Bu iki yöntem benzer semantik var.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>öğenin özniteliklerini ekleyebilir, değiştirebilir veya kaldırabilir.  
  
- Var olmayan <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> bir öznitelik adı ile çağırırsanız, yöntem yeni bir öznitelik oluşturur ve belirtilen öğeye ekler.  
  
- Varolan <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> bir özniteliğin adı ve bazı belirtilen içerikle arama yaptığınızda, özniteliğin içeriği belirtilen içerikle değiştirilir.  
  
- Varolan <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> bir özniteliğin adı ile çağırır ve içerik için null belirtirseniz, öznitelik üst öğesinden kaldırılır.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>öğenin alt öğelerini ekleyebilir, değiştirebilir veya kaldırabilir.  
  
- Var olmayan <xref:System.Xml.Linq.XElement.SetElementValue%2A> bir alt öğenin adı ile çağırırsanız, yöntem yeni bir öğe oluşturur ve belirtilen öğeye ekler.  
  
- Varolan <xref:System.Xml.Linq.XElement.SetElementValue%2A> bir öğenin adı ve bazı belirtilen içerikle arama yaptığınızda, öğenin içeriği belirtilen içerikle değiştirilir.  
  
- Varolan <xref:System.Xml.Linq.XElement.SetElementValue%2A> bir öğenin adı ile çağırır ve içerik için null belirtirseniz, öğe üst öğesinden kaldırılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öznitelik olmayan bir öğe oluşturur. Daha sonra <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ad/değer çiftleri listesi oluşturmak ve korumak için yöntemi kullanır.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, alt öğe olmayan bir öğe oluşturur. Daha sonra <xref:System.Xml.Linq.XElement.SetElementValue%2A> ad/değer çiftleri listesi oluşturmak ve korumak için yöntemi kullanır.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
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
- [XML Ağaçlarının Değiştirilmesi (LINQ - XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
