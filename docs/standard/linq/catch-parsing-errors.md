---
title: Ayrıştırma hatalarını yakalama-LINQ to XML
description: C# veya Visual Basic programınızda, XElement. Parse gibi bir yöntemle geçersiz XML ayrıştırmaya çalışırsa bir özel durum oluşabilir. Bu özel durumları yakalamak ve yanıtlamak için programı yazabilirsiniz.
ms.date: 7/20/2015
dev_langs:
- csharp
- vb
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: f7679bd5a0726c669eb47ad6ad66e0f64259264b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553022"
---
# <a name="how-to-catch-parsing-errors-linq-to-xml"></a>Ayrıştırma hatalarını yakalama (LINQ to XML)

Bu makalede, C# veya Visual Basic hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağı gösterilir.

LINQ to XML, kullanılarak uygulanır <xref:System.Xml.XmlReader> . Hatalı biçimlendirilmiş veya geçersiz XML LINQ to XML geçirilirse, temeldeki <xref:System.Xml.XmlReader> sınıf bir özel durum oluşturur. XML 'yi ayrıştırmaya yönelik çeşitli yöntemler <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> özel durumu yakalamayın; özel durum daha sonra uygulamanız tarafından yakalanamaz.

## <a name="example-parse-invalid-xml"></a>Örnek: Parse geçersiz XML

Aşağıdaki kod geçersiz XML ayrıştırmaya çalışıyor.

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

Geçersiz bitiş etiketi nedeniyle `</Contcts>` , örnek aşağıdaki özel durumu oluşturur:

```output
The 'Contacts' start tag on line 1 doesn't match the end tag of 'Contcts'. Line 5, position 13.
```

,, Ve yöntemlerinin oluşturduğunu özel durumlar hakkında daha fazla bilgi için <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> <xref:System.Xml.XmlReader> belgelerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Dizeyi ayrıştırma](parse-string.md)
