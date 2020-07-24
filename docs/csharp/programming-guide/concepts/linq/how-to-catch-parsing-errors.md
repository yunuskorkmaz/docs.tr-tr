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
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="529b1-104">Ayrıştırma hatalarını yakalama (C#)</span><span class="sxs-lookup"><span data-stu-id="529b1-104">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="529b1-105">Bu konu, hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="529b1-105">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="529b1-106">kullanılarak uygulanır <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="529b1-106">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="529b1-107">Hatalı biçimlendirilmiş veya geçersiz XML öğesine geçirilirse [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , temeldeki <xref:System.Xml.XmlReader> sınıf bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="529b1-107">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="529b1-108">XML 'yi Ayrıştır gibi çeşitli yöntemler <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> özel durumu yakalamayın; özel durum daha sonra uygulamanız tarafından yakalanamaz.</span><span class="sxs-lookup"><span data-stu-id="529b1-108">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="529b1-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="529b1-109">Example</span></span>  
 <span data-ttu-id="529b1-110">Aşağıdaki kod geçersiz XML 'i ayrıştırmayı dener:</span><span class="sxs-lookup"><span data-stu-id="529b1-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="529b1-111">Bu kodu çalıştırdığınızda, aşağıdaki özel durumu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="529b1-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="529b1-112"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>,, Ve için oluşturmak istediğiniz özel durumlar hakkında daha fazla bilgi için <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> <xref:System.Xml.XmlReader> belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="529b1-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  