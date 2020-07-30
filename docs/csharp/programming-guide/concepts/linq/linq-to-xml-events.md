---
title: LINQ to XML olayları (C#)
description: C# içinde herhangi bir XObject örneğine LINQ to XML olaylar ekleyin. Olay işleyicisi, söz konusu XObject için XML ağacı değiştirildiğinde olayları alır.
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 576b0a5d0472bddd66e01d3bef8f3affa1c9458b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165419"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="44eea-104">LINQ to XML olayları (C#)</span><span class="sxs-lookup"><span data-stu-id="44eea-104">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="44eea-105">olaylar, bir XML ağacı değiştiğinde size bildirim gönderilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="44eea-105">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="44eea-106">Herhangi bir örneğine olay ekleyebilirsiniz <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="44eea-106">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="44eea-107">Olay işleyicisi daha sonra bu <xref:System.Xml.Linq.XObject> ve alt öğelerinden herhangi birine değişiklikler için olaylar alır.</span><span class="sxs-lookup"><span data-stu-id="44eea-107">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="44eea-108">Örneğin, ağacın köküne bir olay işleyicisi ekleyebilir ve ağaçtaki tüm değişiklikleri bu olay işleyicisinden işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44eea-108">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="44eea-109">Olay örnekleri için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bkz <xref:System.Xml.Linq.XObject.Changing> <xref:System.Xml.Linq.XObject.Changed> . ve.</span><span class="sxs-lookup"><span data-stu-id="44eea-109">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="44eea-110">Türler ve olaylar</span><span class="sxs-lookup"><span data-stu-id="44eea-110">Types and Events</span></span>  
 <span data-ttu-id="44eea-111">Olaylarla çalışırken aşağıdaki türleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="44eea-111">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="44eea-112">Tür</span><span class="sxs-lookup"><span data-stu-id="44eea-112">Type</span></span>|<span data-ttu-id="44eea-113">Description</span><span class="sxs-lookup"><span data-stu-id="44eea-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="44eea-114">Bir olay oluşturulduğunda olay türünü belirtir <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="44eea-114">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="44eea-115">Ve olayları için veri <xref:System.Xml.Linq.XObject.Changing> sağlar <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="44eea-115">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="44eea-116">Bir XML ağacını değiştirirken aşağıdaki olaylar oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="44eea-116">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="44eea-117">Olay</span><span class="sxs-lookup"><span data-stu-id="44eea-117">Event</span></span>|<span data-ttu-id="44eea-118">Description</span><span class="sxs-lookup"><span data-stu-id="44eea-118">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="44eea-119">Bu <xref:System.Xml.Linq.XObject> veya alt öğelerinden herhangi birinin değişmesinden hemen önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="44eea-119">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="44eea-120">Bir değiştiğinde <xref:System.Xml.Linq.XObject> veya alt öğelerinden herhangi biri değiştiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="44eea-120">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="44eea-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="44eea-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="44eea-122">Description</span><span class="sxs-lookup"><span data-stu-id="44eea-122">Description</span></span>  
 <span data-ttu-id="44eea-123">Olaylar, bir XML ağacındaki bazı toplu bilgileri korumak istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="44eea-123">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="44eea-124">Örneğin, faturanın satır öğelerinin toplamı olan bir fatura toplamı korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44eea-124">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="44eea-125">Bu örnek, karmaşık öğe altındaki tüm alt öğelerinin toplamını korumak için olayları kullanır `Items` .</span><span class="sxs-lookup"><span data-stu-id="44eea-125">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="44eea-126">Kod</span><span class="sxs-lookup"><span data-stu-id="44eea-126">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="44eea-127">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="44eea-127">Comments</span></span>  
 <span data-ttu-id="44eea-128">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="44eea-128">This code produces the following output:</span></span>  
  
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
  