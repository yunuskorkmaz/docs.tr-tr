---
title: 'Nasıl yapılır: Ayrıştırma hatalarını yakalama (C#)'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 2f56ca48278f9ad8b38f8564f54a379cc09f94ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515868"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="8af53-102">Nasıl yapılır: Ayrıştırma hatalarını yakalama (C#)</span><span class="sxs-lookup"><span data-stu-id="8af53-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="8af53-103">Bu konu, hatalı biçimlendirilmiş veya geçersiz XML nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="8af53-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="8af53-104">kullanılarak uygulanan <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="8af53-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="8af53-105">Hatalı biçimlendirilmiş veya geçersiz XML iletilmezse [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], arka plandaki <xref:System.Xml.XmlReader> sınıfı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8af53-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="8af53-106">XML gibi ayrıştırma çeşitli yöntemleri <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, özel durum yakalamayın; özel durumun daha sonra uygulamanız tarafından yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="8af53-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8af53-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8af53-107">Example</span></span>  
 <span data-ttu-id="8af53-108">Aşağıdaki kod, geçersiz XML ayrıştırmak çalışır:</span><span class="sxs-lookup"><span data-stu-id="8af53-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="8af53-109">Bu kodu çalıştırdığınızda, şu özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8af53-109">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="8af53-110">Bekleyebileceğiniz özel durumları hakkında bilgi <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, ve <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> oluşturmak için bkz <xref:System.Xml.XmlReader> belgeleri.</span><span class="sxs-lookup"><span data-stu-id="8af53-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af53-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8af53-111">See also</span></span>

- [<span data-ttu-id="8af53-112">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="8af53-112">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
