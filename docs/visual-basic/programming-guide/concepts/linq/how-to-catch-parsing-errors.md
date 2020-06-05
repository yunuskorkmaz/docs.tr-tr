---
title: 'Nasıl yapılır: Ayrıştırma Hatalarını Yakalama'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: c0b46d7df270dd6f081a0c736b6978088cfbd9c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375154"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Nasıl yapılır: ayrıştırma hatalarını yakalama (Visual Basic)
Bu konu, hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağını göstermektedir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanılarak uygulanır <xref:System.Xml.XmlReader> . Hatalı biçimlendirilmiş veya geçersiz XML öğesine geçirilirse [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , temeldeki <xref:System.Xml.XmlReader> sınıf bir özel durum oluşturur. XML 'yi Ayrıştır gibi çeşitli yöntemler <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> özel durumu yakalamayın; özel durum daha sonra uygulamanız tarafından yakalanamaz.  
  
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
  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>,, Ve için oluşturmak istediğiniz özel durumlar hakkında daha fazla bilgi için <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> <xref:System.Xml.XmlReader> belgelerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML 'yi ayrıştırma (Visual Basic)](parsing-xml.md)
