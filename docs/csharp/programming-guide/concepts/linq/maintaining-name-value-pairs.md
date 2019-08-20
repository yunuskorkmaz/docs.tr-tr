---
title: Ad-değer çiftlerini koruma (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 9c42a154a4c3ed1463e428faab4c7d33197ef4a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591704"
---
# <a name="maintaining-namevalue-pairs-c"></a>Ad/değer çiftlerini koruma (C#)
Birçok uygulamanın ad/değer çiftleri olarak en iyi şekilde tutulan bilgileri tutması gerekir. Bu bilgiler yapılandırma bilgileri veya genel ayarlar olabilir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bir ad/değer çiftleri kümesini saklamayı kolaylaştıran bazı yöntemler içerir. Bilgileri öznitelik olarak veya bir alt öğe kümesi olarak tutabilirsiniz.  
  
 Bilgileri öznitelik veya alt öğe olarak tutma arasındaki tek fark, özniteliklerin bir öğe için yalnızca belirli bir ada sahip tek bir öznitelik olabilecek kısıtlamaya sahip olduğu kısıtlamadır. Bu sınırlama alt öğeler için geçerlidir.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue ve SetElementValue  
 Ad/değer çiftlerini tutmaya yardımcı olan iki yöntem ve ' <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> <xref:System.Xml.Linq.XElement.SetElementValue%2A>dir. Bu iki yöntem benzer anlamlara sahiptir.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>bir öğenin özniteliklerini ekleyebilir, değiştirebilir veya kaldırabilir.  
  
- Varolmayan bir özniteliğin <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> adıyla çağırırsanız, yöntemi yeni bir öznitelik oluşturur ve belirtilen öğeye ekler.  
  
- Var olan bir <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> özniteliğin adı ile ve belirtilen içeriklerde bir çağrı yaparsanız, özniteliğin içeriği belirtilen içerikle değiştirilmiştir.  
  
- Varolan bir özniteliğin <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> adıyla çağrı yaparsanız ve içerik için null belirtirseniz, öznitelik üst öğesinden kaldırılır.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>bir öğenin alt öğelerini ekleyebilir, değiştirebilir veya kaldırabilir.  
  
- Var olmayan bir <xref:System.Xml.Linq.XElement.SetElementValue%2A> alt öğe adı ile çağırırsanız, yöntemi yeni bir öğesi oluşturur ve belirtilen öğeye ekler.  
  
- Var olan bir <xref:System.Xml.Linq.XElement.SetElementValue%2A> öğenin adı ile ve belirtilen içeriklerle çağırırsanız, öğenin içeriği belirtilen içerikle değiştirilmiştir.  
  
- Varsa, varolan <xref:System.Xml.Linq.XElement.SetElementValue%2A> bir öğenin adıyla çağrı yaparsanız ve içerik için null belirtirseniz, öğe üst öğesinden kaldırılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öznitelikleri olmayan bir öğesi oluşturur. Daha sonra bir ad <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> /değer çiftleri listesi oluşturmak ve korumak için yöntemini kullanır.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, alt öğeleri olmayan bir öğe oluşturur. Daha sonra bir ad <xref:System.Xml.Linq.XElement.SetElementValue%2A> /değer çiftleri listesi oluşturmak ve korumak için yöntemini kullanır.  
  
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
- [XML ağaçlarını değiştirme (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
