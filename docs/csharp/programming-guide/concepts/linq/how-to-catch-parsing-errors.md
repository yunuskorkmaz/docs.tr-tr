---
title: 'Nasıl yapılır: hatalar (C#) ayrıştırma Catch'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 037e490fa7b0600b906ec310201e5d33c2f55baa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333391"
---
# <a name="how-to-catch-parsing-errors-c"></a>Nasıl yapılır: hatalar (C#) ayrıştırma Catch
Bu konu, hatalı biçimlendirilmiş veya geçersiz XML algılamak gösterilmektedir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanılarak uygulanan <xref:System.Xml.XmlReader>. İçin hatalı biçimlendirilmiş veya geçersiz XML aktarılırsa [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], arka plandaki <xref:System.Xml.XmlReader> sınıfı bir özel durum oluşturur. XML ayrıştırma gibi çeşitli yöntemler <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, özel durum catch değil; özel durum sonra uygulamanız tarafından yakalanan.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, geçersiz XML Ayrıştırma dener:  
  
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
  
 Bu kodu çalıştırdığınızda, aşağıdaki özel durum oluşturur:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Bekleyebileceğiniz özel durumlar hakkında bilgi için <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, ve <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> atmak için bkz <xref:System.Xml.XmlReader> belgeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Ayrıştırma (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
