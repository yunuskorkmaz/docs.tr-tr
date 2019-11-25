---
title: Ayrıştırma hatalarını yakalama (C#)
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 1a05037892061dec85e7837472e8ec13e076724b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141485"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="fbe8f-102">Ayrıştırma hatalarını yakalama (C#)</span><span class="sxs-lookup"><span data-stu-id="fbe8f-102">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="fbe8f-103">Bu konu, hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fbe8f-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fbe8f-104">, <xref:System.Xml.XmlReader>kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fbe8f-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="fbe8f-105">Hatalı biçimlendirilmiş veya geçersiz XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]geçirilirse, temel alınan <xref:System.Xml.XmlReader> sınıfı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fbe8f-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="fbe8f-106"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>gibi XML 'yi ayrıştırmaya yönelik çeşitli yöntemler özel durumu yakalayamaz; özel durum daha sonra uygulamanız tarafından yakalanarak.</span><span class="sxs-lookup"><span data-stu-id="fbe8f-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbe8f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbe8f-107">Example</span></span>  
 <span data-ttu-id="fbe8f-108">Aşağıdaki kod geçersiz XML 'i ayrıştırmayı dener:</span><span class="sxs-lookup"><span data-stu-id="fbe8f-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="fbe8f-109">Bu kodu çalıştırdığınızda, aşağıdaki özel durumu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="fbe8f-109">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="fbe8f-110"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>ve <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> yöntemlerini oluşturmak için beklediğinizi belirten özel durumlar hakkında daha fazla bilgi için, bkz. <xref:System.Xml.XmlReader> belgeleri.</span><span class="sxs-lookup"><span data-stu-id="fbe8f-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  