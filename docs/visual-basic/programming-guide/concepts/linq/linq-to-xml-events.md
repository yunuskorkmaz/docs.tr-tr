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
# <a name="linq-to-xml-events-visual-basic"></a>LINQ to XML olayları (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]olaylar, bir XML ağacı değiştiğinde size bildirim gönderilmesini sağlar.  
  
 Herhangi bir örneğine olay ekleyebilirsiniz <xref:System.Xml.Linq.XObject> . Olay işleyicisi daha sonra bu <xref:System.Xml.Linq.XObject> ve alt öğelerinden herhangi birine değişiklikler için olaylar alır. Örneğin, ağacın köküne bir olay işleyicisi ekleyebilir ve ağaçtaki tüm değişiklikleri bu olay işleyicisinden işleyebilirsiniz.  
  
 Olay örnekleri için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bkz <xref:System.Xml.Linq.XObject.Changing> <xref:System.Xml.Linq.XObject.Changed> . ve.  
  
## <a name="types-and-events"></a>Türler ve olaylar  
 Olaylarla çalışırken aşağıdaki türleri kullanın:  
  
|Tür|Description|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Bir olay oluşturulduğunda olay türünü belirtir <xref:System.Xml.Linq.XObject> .|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Ve olayları için veri <xref:System.Xml.Linq.XObject.Changing> sağlar <xref:System.Xml.Linq.XObject.Changed> .|  
  
 Bir XML ağacını değiştirirken aşağıdaki olaylar oluşturulur:  
  
|Olay|Description|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Bu <xref:System.Xml.Linq.XObject> veya alt öğelerinden herhangi birinin değişmesinden hemen önce gerçekleşir.|  
|<xref:System.Xml.Linq.XObject.Changed>|Bir değiştiğinde <xref:System.Xml.Linq.XObject> veya alt öğelerinden herhangi biri değiştiğinde gerçekleşir.|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Olaylar, bir XML ağacındaki bazı toplu bilgileri korumak istediğinizde faydalıdır. Örneğin, faturanın satır öğelerinin toplamı olan bir fatura toplamı korumak isteyebilirsiniz. Bu örnek, karmaşık öğe altındaki tüm alt öğelerinin toplamını korumak için olayları kullanır `Items` .  
  
### <a name="code"></a>Kod  
  
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
  
### <a name="comments"></a>Yorumlar  
 Bu kod aşağıdaki çıktıyı üretir:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş LINQ to XML Programlama (Visual Basic)](advanced-linq-to-xml-programming.md)
