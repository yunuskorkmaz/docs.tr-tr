---
title: 'Nasıl yapılır: ayrıştırma (C#) hatalarını yakalama'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 037e490fa7b0600b906ec310201e5d33c2f55baa
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198483"
---
# <a name="how-to-catch-parsing-errors-c"></a>Nasıl yapılır: ayrıştırma (C#) hatalarını yakalama
Bu konu, hatalı biçimlendirilmiş veya geçersiz XML nasıl gösterir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanılarak uygulanan <xref:System.Xml.XmlReader>. Hatalı biçimlendirilmiş veya geçersiz XML iletilmezse [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], arka plandaki <xref:System.Xml.XmlReader> sınıfı bir özel durum oluşturur. XML gibi ayrıştırma çeşitli yöntemleri <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, özel durum yakalamayın; özel durumun daha sonra uygulamanız tarafından yakalanabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, geçersiz XML ayrıştırmak çalışır:  
  
```csharp  
try {  
    XElement contacts = XElement.Parse(  
        @"<Contacts>  
            <Contact>  
                <Name>Jim Wilson</Name>  
            </Contact>  
          </Contcts>");  
  
    Console.WriteLine(contacts);  
}  
catch (System.Xml.XmlException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
 Bu kodu çalıştırdığınızda, şu özel durum oluşturur:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Bekleyebileceğiniz özel durumları hakkında bilgi <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, ve <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> oluşturmak için bkz <xref:System.Xml.XmlReader> belgeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Ayrıştırma (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
