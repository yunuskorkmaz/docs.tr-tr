---
title: Ad-değer çiftleri (C#) sağlama
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 28c01ce17881ffe7e8fcc35e2c23dec85d50955d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216561"
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="91358-102">Ad/değer çiftleri Bakımı (C#)</span><span class="sxs-lookup"><span data-stu-id="91358-102">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="91358-103">Çoğu uygulama iyi ad/değer çiftleri tutulur bilgileri korumak sahip.</span><span class="sxs-lookup"><span data-stu-id="91358-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="91358-104">Bu bilgiler, yapılandırma bilgileri veya genel ayarlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="91358-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="91358-105"> ad/değer çiftleri kümesini tutmak kolaylaştıran bazı yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="91358-105"> contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="91358-106">Öğeleri bilgilerin öznitelikleri veya bir alt kümesi olarak ya da koruyabilir.</span><span class="sxs-lookup"><span data-stu-id="91358-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="91358-107">Öznitelikleri veya alt öğeleri olarak bilgi tutma arasında bir fark öznitelikleri bir öğe için belirli bir ada sahip yalnızca bir özniteliği olabilir kısıtlaması olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="91358-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="91358-108">Alt öğeler bu sınırlama geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="91358-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="91358-109">SetAttributeValue ve SetElementValue</span><span class="sxs-lookup"><span data-stu-id="91358-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="91358-110">Tutma kolaylaştıran iki yöntem adı/değer çiftleri olan <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ve <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="91358-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="91358-111">Bu iki yöntem, benzer semantiğe sahip.</span><span class="sxs-lookup"><span data-stu-id="91358-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="91358-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ekleme, değiştirme veya bir öğenin öznitelikleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="91358-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
-   <span data-ttu-id="91358-113">Eğer <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> yöntemi var olmayan bir öznitelik bir adla yeni bir öznitelik oluşturur ve belirtilen öğeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="91358-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="91358-114">Eğer <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> varolan bir özniteliği olan bir ada sahip ve belirtilen bazı içerik, öznitelik içeriğini belirtilen içerik ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="91358-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="91358-115">Çağırırsanız <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> varolan bir ad özniteliği ve belirtmek için içeriği null öznitelik üst öğesinden da kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="91358-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="91358-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> ekleme, değiştirme veya bir öğenin alt öğeleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="91358-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
-   <span data-ttu-id="91358-117">Eğer <xref:System.Xml.Linq.XElement.SetElementValue%2A> yöntemi bir alt öğenin var olmayan bir adla yeni bir öğe oluşturur ve belirtilen öğeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="91358-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="91358-118">Eğer <xref:System.Xml.Linq.XElement.SetElementValue%2A> var olan bir öğenin bir ada sahip ve belirtilen bazı içerik, öğenin içeriğini belirtilen içerik ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="91358-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="91358-119">Eğer <xref:System.Xml.Linq.XElement.SetElementValue%2A> var olan bir öğe adı ve içerik için null belirtin, üst öğesinden öğe kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="91358-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91358-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="91358-120">Example</span></span>  
 <span data-ttu-id="91358-121">Aşağıdaki örnek, özniteliklere bir öğe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91358-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="91358-122">Ardından kullanır <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> oluşturmak ve ad/değer çiftlerinin listesini güncelleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="91358-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="91358-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="91358-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="91358-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="91358-124">Example</span></span>  
 <span data-ttu-id="91358-125">Aşağıdaki örnek, bir öğe ile hiçbir alt öğeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91358-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="91358-126">Ardından kullanır <xref:System.Xml.Linq.XElement.SetElementValue%2A> oluşturmak ve ad/değer çiftlerinin listesini güncelleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="91358-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="91358-127">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="91358-127">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91358-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91358-128">See Also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>  
- [<span data-ttu-id="91358-129">(LINQ to XML) XML ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="91358-129">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
