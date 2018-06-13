---
title: LINQ-XML olaylar (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: 216c2af87d2ae3a767548ccaa1efe118215cc6a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645996"
---
# <a name="linq-to-xml-events-visual-basic"></a>LINQ-XML olaylar (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] olayları bir XML ağacı değiştirildiğinde bildirim almak etkinleştirin.  
  
 Herhangi bir örneğine olayları ekleyebilirsiniz <xref:System.Xml.Linq.XObject>. Olay işleyicisi sonra değişiklikler için olayları alacak <xref:System.Xml.Linq.XObject> ve tüm alt öğeleri. Örneğin, olay işleyici ağaç kök dizinine ekleyin ve bu olay işleyicisinden ağaç yapılan tüm değişiklikler işlemek.  
  
 Örnekler için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] olayları görmek <xref:System.Xml.Linq.XObject.Changing> ve <xref:System.Xml.Linq.XObject.Changed>.  
  
## <a name="types-and-events"></a>Türleri ve olaylar  
 Olaylar ile çalışırken aşağıdaki türlerini kullanın:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|İçin bir olay oluşturulduğunda olay türünü belirten bir <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Veriler için sağlar <xref:System.Xml.Linq.XObject.Changing> ve <xref:System.Xml.Linq.XObject.Changed> olaylar.|  
  
 Bir XML ağacı değişiklik yaptığınızda aşağıdaki olaylar oluşturulur:  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Yalnızca bu önce oluşur <xref:System.Xml.Linq.XObject> veya alt öğelerinden birini değiştirmek için olduğuna.|  
|<xref:System.Xml.Linq.XObject.Changed>|Oluşur, bir <xref:System.Xml.Linq.XObject> değişti veya alt öğelerinden birini değiştirilmiştir.|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Olayların bir XML ağacında toplama bazı bilgileri korumak istediğinizde kullanışlıdır. Örneğin, fatura satır öğelerin toplamı bir fatura toplam korumak isteyebilirsiniz. Bu örnek, karmaşık bir öğe altındaki tüm alt öğeleri toplamı korumak için olayları kullanır `Items`.  
  
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
  
### <a name="comments"></a>Açıklamalar  
 Bu kod aşağıdaki çıktıyı üretir:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş LINQ-XML programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
