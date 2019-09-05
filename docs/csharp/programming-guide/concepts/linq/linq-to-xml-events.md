---
title: LINQ to XML olayları (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 8e0cb4519dd0fc2bed443d9a62b9a2545d10e161
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253168"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="34cdb-102">LINQ to XML olayları (C#)</span><span class="sxs-lookup"><span data-stu-id="34cdb-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="34cdb-103">olaylar, bir XML ağacı değiştiğinde size bildirim gönderilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="34cdb-103">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="34cdb-104">Herhangi <xref:System.Xml.Linq.XObject>bir örneğine olay ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34cdb-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="34cdb-105">Olay işleyicisi daha sonra bu <xref:System.Xml.Linq.XObject> ve alt öğelerinden herhangi birine değişiklikler için olaylar alır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="34cdb-106">Örneğin, ağacın köküne bir olay işleyicisi ekleyebilir ve ağaçtaki tüm değişiklikleri bu olay işleyicisinden işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34cdb-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="34cdb-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Olay örnekleri için bkz <xref:System.Xml.Linq.XObject.Changing> . ve <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="34cdb-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="34cdb-108">Türler ve olaylar</span><span class="sxs-lookup"><span data-stu-id="34cdb-108">Types and Events</span></span>  
 <span data-ttu-id="34cdb-109">Olaylarla çalışırken aşağıdaki türleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="34cdb-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="34cdb-110">Tür</span><span class="sxs-lookup"><span data-stu-id="34cdb-110">Type</span></span>|<span data-ttu-id="34cdb-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34cdb-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="34cdb-112">Bir <xref:System.Xml.Linq.XObject>olay oluşturulduğunda olay türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="34cdb-113"><xref:System.Xml.Linq.XObject.Changing> Ve<xref:System.Xml.Linq.XObject.Changed> olayları için veri sağlar.</span><span class="sxs-lookup"><span data-stu-id="34cdb-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="34cdb-114">Bir XML ağacını değiştirirken aşağıdaki olaylar oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="34cdb-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="34cdb-115">Olay</span><span class="sxs-lookup"><span data-stu-id="34cdb-115">Event</span></span>|<span data-ttu-id="34cdb-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34cdb-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="34cdb-117">Bu <xref:System.Xml.Linq.XObject> veya alt öğelerinden herhangi birinin değişmesinden hemen önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="34cdb-118">Bir <xref:System.Xml.Linq.XObject> değiştiğinde veya alt öğelerinden herhangi biri değiştiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="34cdb-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="34cdb-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="34cdb-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="34cdb-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34cdb-120">Description</span></span>  
 <span data-ttu-id="34cdb-121">Olaylar, bir XML ağacındaki bazı toplu bilgileri korumak istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="34cdb-122">Örneğin, faturanın satır öğelerinin toplamı olan bir fatura toplamı korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34cdb-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="34cdb-123">Bu örnek, karmaşık öğe `Items`altındaki tüm alt öğelerinin toplamını korumak için olayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="34cdb-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="34cdb-124">Kod</span><span class="sxs-lookup"><span data-stu-id="34cdb-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="34cdb-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34cdb-125">Comments</span></span>  
 <span data-ttu-id="34cdb-126">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="34cdb-126">This code produces the following output:</span></span>  
  
```output  
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
  