---
title: 'Nasıl yapılır: Catch Ayrıştırma hataları (C#)'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 4195ff50d1b4d23cd9eb07fc27f20861d1504672
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204142"
---
# <a name="how-to-catch-parsing-errors-c"></a>Nasıl yapılır: Catch Ayrıştırma hataları (C#)
Bu konu, hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağını göstermektedir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanılarak <xref:System.Xml.XmlReader>uygulanır. Hatalı biçimlendirilmiş veya geçersiz XML öğesine [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]geçirilirse, temeldeki <xref:System.Xml.XmlReader> sınıf bir özel durum oluşturur. XML <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>'yi Ayrıştır gibi çeşitli yöntemler özel durumu yakalamayın; özel durum daha sonra uygulamanız tarafından yakalanamaz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod geçersiz XML 'i ayrıştırmayı dener:  
  
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
  
 Bu kodu çalıştırdığınızda, aşağıdaki özel durumu oluşturur:  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.XmlReader> , ,<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>Ve içinoluşturmakistediğinizözeldurumlarhakkındadahafazlabilgiiçinbelgelerinebakın.<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  