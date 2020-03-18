---
title: Ayrıştırma hataları nasıl yakanız (C#)
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 1a05037892061dec85e7837472e8ec13e076724b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141485"
---
# <a name="how-to-catch-parsing-errors-c"></a>Ayrıştırma hataları nasıl yakanız (C#)
Bu konu, kötü biçimlendirilmiş veya geçersiz XML'in nasıl algılanılabildiğini gösterir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanılarak <xref:System.Xml.XmlReader>uygulanır. Kötü biçimlendirilmiş veya geçersiz XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]geçirilirse, temel <xref:System.Xml.XmlReader> sınıf bir özel durum oluşturur. XML ayrışdırmak çeşitli yöntemler, <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>gibi , özel durum yakalamak değil; özel durum daha sonra uygulamanız tarafından yakalanabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod geçersiz XML ayrıştırmak için çalışır:  
  
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
  
 Bu kodu çalıştırdığınızda, aşağıdaki özel durum atar:  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , , atmak için beklediğiniz özel durumlar hakkında <xref:System.Xml.XmlReader> bilgi için, belgelere bakın.  
  