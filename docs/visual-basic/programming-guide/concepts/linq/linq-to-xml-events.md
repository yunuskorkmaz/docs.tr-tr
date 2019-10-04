---
title: LINQ to XML olayları (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: d35f8063fe87ee4be3dd49a3c0221cb9c47cb22e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834976"
---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="6a113-102">LINQ to XML olayları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a113-102">LINQ to XML Events (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="6a113-103">olayları, bir XML ağacı değiştiğinde size bildirim gönderilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a113-103">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="6a113-104">Bir @no__t örneğine olay ekleyebilirsiniz-0.</span><span class="sxs-lookup"><span data-stu-id="6a113-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="6a113-105">Olay işleyicisi daha sonra bu <xref:System.Xml.Linq.XObject> ' a ve alt öğelerinden herhangi birine yapılan değişiklikler için olayları alır.</span><span class="sxs-lookup"><span data-stu-id="6a113-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="6a113-106">Örneğin, ağacın köküne bir olay işleyicisi ekleyebilir ve ağaçtaki tüm değişiklikleri bu olay işleyicisinden işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a113-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="6a113-107">@No__t-0 olaylarının örnekleri için bkz. <xref:System.Xml.Linq.XObject.Changing> ve <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="6a113-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="6a113-108">Türler ve olaylar</span><span class="sxs-lookup"><span data-stu-id="6a113-108">Types and Events</span></span>  
 <span data-ttu-id="6a113-109">Olaylarla çalışırken aşağıdaki türleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="6a113-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="6a113-110">Tür</span><span class="sxs-lookup"><span data-stu-id="6a113-110">Type</span></span>|<span data-ttu-id="6a113-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a113-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="6a113-112">@No__t-0 için bir olay oluşturulduğunda olay türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a113-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="6a113-113">@No__t-0 ve <xref:System.Xml.Linq.XObject.Changed> olayları için veri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a113-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="6a113-114">Bir XML ağacını değiştirirken aşağıdaki olaylar oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="6a113-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="6a113-115">Olay</span><span class="sxs-lookup"><span data-stu-id="6a113-115">Event</span></span>|<span data-ttu-id="6a113-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a113-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="6a113-117">Bu <xref:System.Xml.Linq.XObject> veya alt öğelerinden herhangi birinin değişmesinden hemen önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="6a113-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="6a113-118">@No__t-0 değiştirildiğinde veya alt öğelerinden herhangi biri değiştiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="6a113-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a113-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a113-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6a113-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a113-120">Description</span></span>  
 <span data-ttu-id="6a113-121">Olaylar, bir XML ağacındaki bazı toplu bilgileri korumak istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a113-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="6a113-122">Örneğin, faturanın satır öğelerinin toplamı olan bir fatura toplamı korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a113-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="6a113-123">Bu örnek, `Items` karmaşık öğesi altındaki tüm alt öğelerin toplamını korumak için olayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a113-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6a113-124">Kodlayın</span><span class="sxs-lookup"><span data-stu-id="6a113-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="6a113-125">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="6a113-125">Comments</span></span>  
 <span data-ttu-id="6a113-126">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6a113-126">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a113-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a113-127">See also</span></span>

- [<span data-ttu-id="6a113-128">Gelişmiş LINQ to XML Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a113-128">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
