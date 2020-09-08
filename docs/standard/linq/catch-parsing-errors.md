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
# <a name="how-to-catch-parsing-errors-linq-to-xml"></a><span data-ttu-id="5976e-104">Ayrıştırma hatalarını yakalama (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5976e-104">How to catch parsing errors (LINQ to XML)</span></span>

<span data-ttu-id="5976e-105">Bu makalede, C# veya Visual Basic hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5976e-105">This article shows how to detect badly formed or invalid XML in C# or Visual Basic.</span></span>

<span data-ttu-id="5976e-106">LINQ to XML, kullanılarak uygulanır <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="5976e-106">LINQ to XML is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="5976e-107">Hatalı biçimlendirilmiş veya geçersiz XML LINQ to XML geçirilirse, temeldeki <xref:System.Xml.XmlReader> sınıf bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5976e-107">If badly formed or invalid XML is passed to LINQ to XML, the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="5976e-108">XML 'yi ayrıştırmaya yönelik çeşitli yöntemler <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> özel durumu yakalamayın; özel durum daha sonra uygulamanız tarafından yakalanamaz.</span><span class="sxs-lookup"><span data-stu-id="5976e-108">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, don't catch the exception; the exception can then be caught by your application.</span></span>

## <a name="example-parse-invalid-xml"></a><span data-ttu-id="5976e-109">Örnek: Parse geçersiz XML</span><span class="sxs-lookup"><span data-stu-id="5976e-109">Example: Parse invalid XML</span></span>

<span data-ttu-id="5976e-110">Aşağıdaki kod geçersiz XML ayrıştırmaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="5976e-110">The following code tries to parse invalid XML.</span></span>

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

<span data-ttu-id="5976e-111">Geçersiz bitiş etiketi nedeniyle `</Contcts>` , örnek aşağıdaki özel durumu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5976e-111">Because of the invalid end tag `</Contcts>`, the example throws the following exception:</span></span>

```output
The 'Contacts' start tag on line 1 doesn't match the end tag of 'Contcts'. Line 5, position 13.
```

<span data-ttu-id="5976e-112">,, Ve yöntemlerinin oluşturduğunu özel durumlar hakkında daha fazla bilgi için <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> <xref:System.Xml.XmlReader> belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="5976e-112">For information about the exceptions that the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="5976e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5976e-113">See also</span></span>

- [<span data-ttu-id="5976e-114">Dizeyi ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="5976e-114">How to parse a string</span></span>](parse-string.md)
