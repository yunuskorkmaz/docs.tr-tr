---
title: 'Nasıl yapılır: Catch Ayrıştırma hataları (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: a0c0749e8bc6d3fb1a71595778bfc5effaaf8533
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352934"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Nasıl yapılır: Catch Ayrıştırma hataları (Visual Basic)
Bu konu, hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağını göstermektedir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.XmlReader> kullanılarak uygulanır. Hatalı biçimlendirilmiş veya geçersiz XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ' a geçirilirse, temeldeki <xref:System.Xml.XmlReader> sınıfı bir özel durum oluşturur. @No__t-0 gibi XML 'yi ayrıştırmaya yönelik çeşitli yöntemler özel durumu yakalayamaz; özel durum daha sonra uygulamanız tarafından yakalanarak.  
  
 XML değişmez değerlerini kullanırsanız ayrıştırma hatalarını alamazsanız. Visual Basic Derleyicisi hatalı biçimlendirilmiş veya geçersiz XML hatalarını yakalar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod geçersiz XML 'i ayrıştırmayı dener:  
  
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
  
 Bu kodu çalıştırdığınızda, aşağıdaki özel durumu oluşturur:  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 @No__t-0, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> ve <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> yöntemlerinin throw olarak beklendiğini belirten özel durumlar hakkında daha fazla bilgi için, <xref:System.Xml.XmlReader> belgelerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML 'yi ayrıştırma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
