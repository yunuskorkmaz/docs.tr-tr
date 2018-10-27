---
title: LINQ to XML olayları (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 6308d81eac830e11b6d58f8e460dfa377663cd21
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453313"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="35808-102">LINQ to XML olayları (C#)</span><span class="sxs-lookup"><span data-stu-id="35808-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="35808-103">olayları bir XML ağacı değiştirildiğinde bildirim almak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="35808-103">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="35808-104">Herhangi bir örneği için olayları ekleyebilirsiniz <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="35808-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="35808-105">Olay işleyicisi, ardından, değişiklikler için olayları alacaksınız <xref:System.Xml.Linq.XObject> ve tüm alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="35808-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="35808-106">Örneğin, ağacının kökü için bir olay işleyicisi ekleme ve ağaç yapılan tüm değişiklikler bu olay işleyicisinden tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="35808-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="35808-107">Örnekler için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] olayları görmek <xref:System.Xml.Linq.XObject.Changing> ve <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="35808-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="35808-108">Türleri ve olaylar</span><span class="sxs-lookup"><span data-stu-id="35808-108">Types and Events</span></span>  
 <span data-ttu-id="35808-109">Olaylar ile çalışırken aşağıdaki türlerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="35808-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="35808-110">Tür</span><span class="sxs-lookup"><span data-stu-id="35808-110">Type</span></span>|<span data-ttu-id="35808-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35808-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="35808-112">Olay türü için bir olay oluştuğunda belirtir bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="35808-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="35808-113">İçin veri sağlayan <xref:System.Xml.Linq.XObject.Changing> ve <xref:System.Xml.Linq.XObject.Changed> olayları.</span><span class="sxs-lookup"><span data-stu-id="35808-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="35808-114">Bir XML ağacı değiştirdiğinizde, aşağıdaki olaylar oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="35808-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="35808-115">Olay</span><span class="sxs-lookup"><span data-stu-id="35808-115">Event</span></span>|<span data-ttu-id="35808-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35808-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="35808-117">Hemen önce gerçekleşir <xref:System.Xml.Linq.XObject> veya alt öğelerinden birini gittiğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="35808-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="35808-118">Gerçekleşir, bir <xref:System.Xml.Linq.XObject> değiştirildi veya alt öğelerinden birini değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="35808-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="35808-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="35808-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="35808-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35808-120">Description</span></span>  
 <span data-ttu-id="35808-121">Olayları toplama bazı bilgiler XML ağacındaki bulundurmak istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="35808-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="35808-122">Örneğin, toplam fatura satır öğelerini bir fatura toplamı korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35808-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="35808-123">Bu örnekte, toplam karmaşık öğesinin altındaki tüm alt öğeleri tutmak için olayları kullanır. `Items`.</span><span class="sxs-lookup"><span data-stu-id="35808-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="35808-124">Kod</span><span class="sxs-lookup"><span data-stu-id="35808-124">Code</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a><span data-ttu-id="35808-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35808-125">Comments</span></span>  
 <span data-ttu-id="35808-126">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="35808-126">This code produces the following output:</span></span>  
  
```  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35808-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35808-127">See Also</span></span>

- [<span data-ttu-id="35808-128">Gelişmiş LINQ to XML programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="35808-128">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
