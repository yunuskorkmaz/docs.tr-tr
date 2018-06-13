---
title: Bakımı ad-değer çiftleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: 6d842adb1e21a7744f03f4a7e7fb0785ffb6a119
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646883"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a><span data-ttu-id="30fee-102">Bakımı ad/değer çiftleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30fee-102">Maintaining Name/Value Pairs (Visual Basic)</span></span>
<span data-ttu-id="30fee-103">Birçok uygulama, ad/değer çiftleri olarak en iyi şekilde tutulur Bilgi korumanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="30fee-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="30fee-104">Bu bilgiler, yapılandırma bilgileri veya genel ayarlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="30fee-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="30fee-105"> kolaylaştıran bir ad/değer çifti kümesi tutmak bazı yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="30fee-105"> contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="30fee-106">Öğeleri öznitelikler veya alt kümesi olarak bilgi ya da koruyabilir.</span><span class="sxs-lookup"><span data-stu-id="30fee-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="30fee-107">Öznitelikler veya alt öğeleri olarak bilgi tutma arasındaki tek fark öznitelikleri yalnızca bir özniteliği olan bir öğe için belirli bir ad olabilir kısıtlaması olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="30fee-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="30fee-108">Bu sınırlama alt öğeler için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="30fee-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="30fee-109">SetAttributeValue ve SetElementValue</span><span class="sxs-lookup"><span data-stu-id="30fee-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="30fee-110">Tutma kolaylaştırmak iki yöntem ad/değer çiftlerine olan <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ve <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="30fee-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="30fee-111">Bu iki yöntem benzer bir semantik vardır.</span><span class="sxs-lookup"><span data-stu-id="30fee-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="30fee-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> ekleyebilir, değiştirme veya bir öğenin öznitelikleri kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30fee-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
-   <span data-ttu-id="30fee-113">Çağırırsanız <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> var olmayan bir öznitelik adı, yöntem yeni bir öznitelik oluşturur ve belirtilen öğeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="30fee-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="30fee-114">Çağırırsanız <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> varolan bir özniteliğe adıyla ve bazı belirtilen içerik, öznitelik içeriğini belirtilen içerikle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="30fee-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="30fee-115">Çağırırsanız <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> varolan bir adla özniteliği ve belirtmek içerik için null öznitelik üst öğesinden da kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="30fee-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="30fee-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> ekleme, değiştirme ve bir öğenin alt öğeleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="30fee-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
-   <span data-ttu-id="30fee-117">Çağırırsanız <xref:System.Xml.Linq.XElement.SetElementValue%2A> yöntemi var olmayan bir alt öğesi olan bir adla yeni bir öğesi oluşturur ve belirtilen öğeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="30fee-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="30fee-118">Çağırırsanız <xref:System.Xml.Linq.XElement.SetElementValue%2A> varolan bir öğenin bir adla ve bazı belirtilen içeriği, öğenin içeriğini belirtilen içerikle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="30fee-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="30fee-119">Çağırırsanız <xref:System.Xml.Linq.XElement.SetElementValue%2A> varolan bir öğenin bir adla ve içerik için null belirtin, üst öğesinden öğe kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="30fee-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30fee-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="30fee-120">Example</span></span>  
 <span data-ttu-id="30fee-121">Aşağıdaki örnek, özniteliklere bir öğe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30fee-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="30fee-122">Daha sonra kullanır <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> oluşturmak ve ad/değer çiftlerinin listesini güncelleştirmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="30fee-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="30fee-123">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="30fee-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="30fee-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="30fee-124">Example</span></span>  
 <span data-ttu-id="30fee-125">Aşağıdaki örnekte bir öğe ile hiçbir alt öğeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30fee-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="30fee-126">Daha sonra kullanır <xref:System.Xml.Linq.XElement.SetElementValue%2A> oluşturmak ve ad/değer çiftlerinin listesini güncelleştirmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="30fee-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="30fee-127">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="30fee-127">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30fee-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30fee-128">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>  
 [<span data-ttu-id="30fee-129">XML ağaçları (LINQ-XML) değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30fee-129">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
