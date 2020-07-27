---
title: Ad-değer çiftlerini koruma (C#)
description: LINQ to XML, ad/değer çiftlerinin öznitelik olarak veya bir alt öğe kümesi olarak korunmasını kolaylaştıran yöntemler içerir.
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 92a45d160cbb1ef470d93bf740d0b6f584681e72
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165277"
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="11f0b-103">Ad/değer çiftlerini koruma (C#)</span><span class="sxs-lookup"><span data-stu-id="11f0b-103">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="11f0b-104">Birçok uygulamanın ad/değer çiftleri olarak en iyi şekilde tutulan bilgileri tutması gerekir.</span><span class="sxs-lookup"><span data-stu-id="11f0b-104">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="11f0b-105">Bu bilgiler yapılandırma bilgileri veya genel ayarlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="11f0b-105">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="11f0b-106">bir ad/değer çiftleri kümesini saklamayı kolaylaştıran bazı yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="11f0b-106">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="11f0b-107">Bilgileri öznitelik olarak veya bir alt öğe kümesi olarak tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11f0b-107">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="11f0b-108">Bilgileri öznitelik veya alt öğe olarak tutma arasındaki tek fark, özniteliklerin bir öğe için yalnızca belirli bir ada sahip tek bir öznitelik olabilecek kısıtlamaya sahip olduğu kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="11f0b-108">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="11f0b-109">Bu sınırlama alt öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="11f0b-109">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="11f0b-110">SetAttributeValue ve SetElementValue</span><span class="sxs-lookup"><span data-stu-id="11f0b-110">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="11f0b-111">Ad/değer çiftlerini tutmaya yardımcı olan iki yöntem <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ve ' dir <xref:System.Xml.Linq.XElement.SetElementValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="11f0b-111">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="11f0b-112">Bu iki yöntem benzer anlamlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="11f0b-112">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="11f0b-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>bir öğenin özniteliklerini ekleyebilir, değiştirebilir veya kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="11f0b-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="11f0b-114"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>Varolmayan bir özniteliğin adıyla çağırırsanız, yöntemi yeni bir öznitelik oluşturur ve belirtilen öğeye ekler.</span><span class="sxs-lookup"><span data-stu-id="11f0b-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="11f0b-115"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>Var olan bir özniteliğin adı ile ve belirtilen içeriklerde bir çağrı yaparsanız, özniteliğin içeriği belirtilen içerikle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="11f0b-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="11f0b-116"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>Varolan bir özniteliğin adıyla çağrı yaparsanız ve içerik için null belirtirseniz, öznitelik üst öğesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="11f0b-116">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="11f0b-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A>bir öğenin alt öğelerini ekleyebilir, değiştirebilir veya kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="11f0b-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="11f0b-118"><xref:System.Xml.Linq.XElement.SetElementValue%2A>Var olmayan bir alt öğe adı ile çağırırsanız, yöntemi yeni bir öğesi oluşturur ve belirtilen öğeye ekler.</span><span class="sxs-lookup"><span data-stu-id="11f0b-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="11f0b-119">Var olan bir <xref:System.Xml.Linq.XElement.SetElementValue%2A> öğenin adı ile ve belirtilen içeriklerle çağırırsanız, öğenin içeriği belirtilen içerikle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="11f0b-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="11f0b-120">Varsa <xref:System.Xml.Linq.XElement.SetElementValue%2A> , varolan bir öğenin adıyla çağrı yaparsanız ve içerik için null belirtirseniz, öğe üst öğesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="11f0b-120">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11f0b-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="11f0b-121">Example</span></span>  
 <span data-ttu-id="11f0b-122">Aşağıdaki örnek, öznitelikleri olmayan bir öğesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="11f0b-122">The following example creates an element with no attributes.</span></span> <span data-ttu-id="11f0b-123">Daha sonra <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> bir ad/değer çiftleri listesi oluşturmak ve korumak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="11f0b-123">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="11f0b-124">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="11f0b-124">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="11f0b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="11f0b-125">Example</span></span>  
 <span data-ttu-id="11f0b-126">Aşağıdaki örnek, alt öğeleri olmayan bir öğe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="11f0b-126">The following example creates an element with no child elements.</span></span> <span data-ttu-id="11f0b-127">Daha sonra <xref:System.Xml.Linq.XElement.SetElementValue%2A> bir ad/değer çiftleri listesi oluşturmak ve korumak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="11f0b-127">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="11f0b-128">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="11f0b-128">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11f0b-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11f0b-129">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="11f0b-130">XML ağaçlarını değiştirme (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="11f0b-130">Modifying XML Trees (LINQ to XML) (C#)</span></span>](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
