---
title: 'Nasıl yapılır: ayrıştırma hatalarını yakalama'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: 14c4f76c5f10616f9346084cda276e2862b2b41d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353351"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Nasıl yapılır: ayrıştırma hatalarını yakalama (Visual Basic)
Bu konu, hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağını göstermektedir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], <xref:System.Xml.XmlReader>kullanılarak uygulanır. Hatalı biçimlendirilmiş veya geçersiz XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]geçirilirse, temel alınan <xref:System.Xml.XmlReader> sınıfı bir özel durum oluşturur. <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>gibi XML 'yi ayrıştırmaya yönelik çeşitli yöntemler özel durumu yakalayamaz; özel durum daha sonra uygulamanız tarafından yakalanarak.  
  
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
  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>ve <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> yöntemlerini oluşturmak için beklediğinizi belirten özel durumlar hakkında daha fazla bilgi için, bkz. <xref:System.Xml.XmlReader> belgeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML 'yi ayrıştırma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
