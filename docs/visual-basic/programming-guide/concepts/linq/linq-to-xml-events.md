---
title: LINQ to XML Olayları
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: d00f6f1b2a14ac73c1bcd4a1f74b9714ca304da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368822"
---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="70bfd-102">LINQ to XML olayları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70bfd-102">LINQ to XML Events (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="70bfd-103">olaylar, bir XML ağacı değiştiğinde size bildirim gönderilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="70bfd-103">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="70bfd-104">Herhangi bir örneğine olay ekleyebilirsiniz <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="70bfd-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="70bfd-105">Olay işleyicisi daha sonra bu <xref:System.Xml.Linq.XObject> ve alt öğelerinden herhangi birine değişiklikler için olaylar alır.</span><span class="sxs-lookup"><span data-stu-id="70bfd-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="70bfd-106">Örneğin, ağacın köküne bir olay işleyicisi ekleyebilir ve ağaçtaki tüm değişiklikleri bu olay işleyicisinden işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70bfd-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="70bfd-107">Olay örnekleri için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bkz <xref:System.Xml.Linq.XObject.Changing> <xref:System.Xml.Linq.XObject.Changed> . ve.</span><span class="sxs-lookup"><span data-stu-id="70bfd-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="70bfd-108">Türler ve olaylar</span><span class="sxs-lookup"><span data-stu-id="70bfd-108">Types and Events</span></span>  
 <span data-ttu-id="70bfd-109">Olaylarla çalışırken aşağıdaki türleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="70bfd-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="70bfd-110">Tür</span><span class="sxs-lookup"><span data-stu-id="70bfd-110">Type</span></span>|<span data-ttu-id="70bfd-111">Description</span><span class="sxs-lookup"><span data-stu-id="70bfd-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="70bfd-112">Bir olay oluşturulduğunda olay türünü belirtir <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="70bfd-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="70bfd-113">Ve olayları için veri <xref:System.Xml.Linq.XObject.Changing> sağlar <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="70bfd-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="70bfd-114">Bir XML ağacını değiştirirken aşağıdaki olaylar oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="70bfd-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="70bfd-115">Olay</span><span class="sxs-lookup"><span data-stu-id="70bfd-115">Event</span></span>|<span data-ttu-id="70bfd-116">Description</span><span class="sxs-lookup"><span data-stu-id="70bfd-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="70bfd-117">Bu <xref:System.Xml.Linq.XObject> veya alt öğelerinden herhangi birinin değişmesinden hemen önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="70bfd-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="70bfd-118">Bir değiştiğinde <xref:System.Xml.Linq.XObject> veya alt öğelerinden herhangi biri değiştiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="70bfd-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="70bfd-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="70bfd-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="70bfd-120">Description</span><span class="sxs-lookup"><span data-stu-id="70bfd-120">Description</span></span>  
 <span data-ttu-id="70bfd-121">Olaylar, bir XML ağacındaki bazı toplu bilgileri korumak istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="70bfd-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="70bfd-122">Örneğin, faturanın satır öğelerinin toplamı olan bir fatura toplamı korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70bfd-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="70bfd-123">Bu örnek, karmaşık öğe altındaki tüm alt öğelerinin toplamını korumak için olayları kullanır `Items` .</span><span class="sxs-lookup"><span data-stu-id="70bfd-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="70bfd-124">Kod</span><span class="sxs-lookup"><span data-stu-id="70bfd-124">Code</span></span>  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="70bfd-125">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="70bfd-125">Comments</span></span>  
 <span data-ttu-id="70bfd-126">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="70bfd-126">This code produces the following output:</span></span>  
  
```console  
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
  
## <a name="see-also"></a><span data-ttu-id="70bfd-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70bfd-127">See also</span></span>

- [<span data-ttu-id="70bfd-128">Gelişmiş LINQ to XML Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70bfd-128">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
