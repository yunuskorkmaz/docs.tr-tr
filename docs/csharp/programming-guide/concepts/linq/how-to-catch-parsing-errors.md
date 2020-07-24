---
title: Ayrıştırma hatalarını yakalama (C#)
description: C# ' deki bu LINQ to XML örneği hatalı biçimlendirilmiş veya geçersiz XML algılar. LINQ to XML hatalı oluşturulmuş veya geçersiz XML için bir özel durum oluşturan XmlReader 'yi kullanır.
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 0a891097322ef6acce062ea927692b01cc425e6c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105406"
---
# <a name="how-to-catch-parsing-errors-c"></a>Ayrıştırma hatalarını yakalama (C#)
Bu konu, hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağını göstermektedir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanılarak uygulanır <xref:System.Xml.XmlReader> . Hatalı biçimlendirilmiş veya geçersiz XML öğesine geçirilirse [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , temeldeki <xref:System.Xml.XmlReader> sınıf bir özel durum oluşturur. XML 'yi Ayrıştır gibi çeşitli yöntemler <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> özel durumu yakalamayın; özel durum daha sonra uygulamanız tarafından yakalanamaz.  
  
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
  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>,, Ve için oluşturmak istediğiniz özel durumlar hakkında daha fazla bilgi için <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> <xref:System.Xml.XmlReader> belgelerine bakın.  
  