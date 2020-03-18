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
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="ea515-102">Ad/Değer Çiftlerinin Bakımı (C#)</span><span class="sxs-lookup"><span data-stu-id="ea515-102">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="ea515-103">Birçok uygulama, ad/değer çiftleri olarak en iyi tutulan bilgileri korumak zorunda.</span><span class="sxs-lookup"><span data-stu-id="ea515-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="ea515-104">Bu bilgiler yapılandırma bilgileri veya genel ayarlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="ea515-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ea515-105">ad/değer çiftleri kümesini tutmayı kolaylaştıran bazı yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="ea515-105">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="ea515-106">Bilgileri öznitelik olarak veya alt öğeler kümesi olarak saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea515-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="ea515-107">Bilgileri öznitelik olarak veya alt öğe olarak tutmak arasındaki fark, özniteliklerin bir öğe için belirli bir ada sahip yalnızca bir öznitelik olabileceği kısıtlaması olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ea515-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="ea515-108">Bu sınırlama alt öğeler için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="ea515-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="ea515-109">SetAttributeValue ve SetElementValue</span><span class="sxs-lookup"><span data-stu-id="ea515-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="ea515-110">Ad/değer çiftleri tutmayı kolaylaştıran <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> iki <xref:System.Xml.Linq.XElement.SetElementValue%2A>yöntem ve .</span><span class="sxs-lookup"><span data-stu-id="ea515-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="ea515-111">Bu iki yöntem benzer semantik var.</span><span class="sxs-lookup"><span data-stu-id="ea515-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="ea515-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>öğenin özniteliklerini ekleyebilir, değiştirebilir veya kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="ea515-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="ea515-113">Var olmayan <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> bir öznitelik adı ile çağırırsanız, yöntem yeni bir öznitelik oluşturur ve belirtilen öğeye ekler.</span><span class="sxs-lookup"><span data-stu-id="ea515-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="ea515-114">Varolan <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> bir özniteliğin adı ve bazı belirtilen içerikle arama yaptığınızda, özniteliğin içeriği belirtilen içerikle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="ea515-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="ea515-115">Varolan <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> bir özniteliğin adı ile çağırır ve içerik için null belirtirseniz, öznitelik üst öğesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ea515-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="ea515-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A>öğenin alt öğelerini ekleyebilir, değiştirebilir veya kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="ea515-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="ea515-117">Var olmayan <xref:System.Xml.Linq.XElement.SetElementValue%2A> bir alt öğenin adı ile çağırırsanız, yöntem yeni bir öğe oluşturur ve belirtilen öğeye ekler.</span><span class="sxs-lookup"><span data-stu-id="ea515-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="ea515-118">Varolan <xref:System.Xml.Linq.XElement.SetElementValue%2A> bir öğenin adı ve bazı belirtilen içerikle arama yaptığınızda, öğenin içeriği belirtilen içerikle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="ea515-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="ea515-119">Varolan <xref:System.Xml.Linq.XElement.SetElementValue%2A> bir öğenin adı ile çağırır ve içerik için null belirtirseniz, öğe üst öğesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ea515-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea515-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea515-120">Example</span></span>  
 <span data-ttu-id="ea515-121">Aşağıdaki örnek, öznitelik olmayan bir öğe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ea515-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="ea515-122">Daha sonra <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ad/değer çiftleri listesi oluşturmak ve korumak için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ea515-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="ea515-123">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ea515-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="ea515-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea515-124">Example</span></span>  
 <span data-ttu-id="ea515-125">Aşağıdaki örnek, alt öğe olmayan bir öğe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ea515-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="ea515-126">Daha sonra <xref:System.Xml.Linq.XElement.SetElementValue%2A> ad/değer çiftleri listesi oluşturmak ve korumak için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ea515-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="ea515-127">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ea515-127">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea515-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea515-128">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="ea515-129">XML Ağaçlarının Değiştirilmesi (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ea515-129">Modifying XML Trees (LINQ to XML) (C#)</span></span>](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
