---
title: 'Nasıl yapılır: Ayrıştırma (Visual Basic) hatalarını yakalama'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: f438a247866fdea8935be2b881a77f97c152b98f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667095"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Nasıl yapılır: Ayrıştırma (Visual Basic) hatalarını yakalama
Bu konu, hatalı biçimlendirilmiş veya geçersiz XML nasıl gösterir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanılarak uygulanan <xref:System.Xml.XmlReader>. Hatalı biçimlendirilmiş veya geçersiz XML iletilmezse [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], arka plandaki <xref:System.Xml.XmlReader> sınıfı bir özel durum oluşturur. XML gibi ayrıştırma çeşitli yöntemleri <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, özel durum yakalamayın; özel durumun daha sonra uygulamanız tarafından yakalanabilir.  
  
 XML değişmez değerleri kullanırsanız elde edilemiyor Not ayrıştırma hataları. Visual Basic Derleyicisi, hatalı biçimlendirilmiş veya geçersiz XML hataları yakalar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, geçersiz XML ayrıştırmak çalışır:  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 Bu kodu çalıştırdığınızda, şu özel durum oluşturur:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Bekleyebileceğiniz özel durumları hakkında bilgi <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, ve <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> oluşturmak için bkz <xref:System.Xml.XmlReader> belgeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Ayrıştırma XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
