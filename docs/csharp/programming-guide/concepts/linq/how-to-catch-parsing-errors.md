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
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="a257d-102">Ayrıştırma hataları nasıl yakanız (C#)</span><span class="sxs-lookup"><span data-stu-id="a257d-102">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="a257d-103">Bu konu, kötü biçimlendirilmiş veya geçersiz XML'in nasıl algılanılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a257d-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="a257d-104">kullanılarak <xref:System.Xml.XmlReader>uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a257d-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="a257d-105">Kötü biçimlendirilmiş veya geçersiz XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]geçirilirse, temel <xref:System.Xml.XmlReader> sınıf bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a257d-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="a257d-106">XML ayrışdırmak çeşitli yöntemler, <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>gibi , özel durum yakalamak değil; özel durum daha sonra uygulamanız tarafından yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="a257d-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a257d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a257d-107">Example</span></span>  
 <span data-ttu-id="a257d-108">Aşağıdaki kod geçersiz XML ayrıştırmak için çalışır:</span><span class="sxs-lookup"><span data-stu-id="a257d-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="a257d-109">Bu kodu çalıştırdığınızda, aşağıdaki özel durum atar:</span><span class="sxs-lookup"><span data-stu-id="a257d-109">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="a257d-110"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , , atmak için beklediğiniz özel durumlar hakkında <xref:System.Xml.XmlReader> bilgi için, belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="a257d-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  