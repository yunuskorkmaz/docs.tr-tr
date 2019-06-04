---
title: 'Nasıl yapılır: Ayrıştırma hatalarını yakalama (C#)'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 094485b24cdccee7898bd0344aa7c100e26bf4e9
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487478"
---
# <a name="how-to-catch-parsing-errors-c"></a>Nasıl yapılır: Ayrıştırma hatalarını yakalama (C#)
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
  