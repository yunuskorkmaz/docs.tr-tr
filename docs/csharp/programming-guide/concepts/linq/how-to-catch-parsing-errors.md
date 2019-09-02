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
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="97b3c-102">Nasıl yapılır: Catch Ayrıştırma hataları (C#)</span><span class="sxs-lookup"><span data-stu-id="97b3c-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="97b3c-103">Bu konu, hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="97b3c-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="97b3c-104">kullanılarak <xref:System.Xml.XmlReader>uygulanır.</span><span class="sxs-lookup"><span data-stu-id="97b3c-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="97b3c-105">Hatalı biçimlendirilmiş veya geçersiz XML öğesine [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]geçirilirse, temeldeki <xref:System.Xml.XmlReader> sınıf bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97b3c-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="97b3c-106">XML <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>'yi Ayrıştır gibi çeşitli yöntemler özel durumu yakalamayın; özel durum daha sonra uygulamanız tarafından yakalanamaz.</span><span class="sxs-lookup"><span data-stu-id="97b3c-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97b3c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="97b3c-107">Example</span></span>  
 <span data-ttu-id="97b3c-108">Aşağıdaki kod geçersiz XML 'i ayrıştırmayı dener:</span><span class="sxs-lookup"><span data-stu-id="97b3c-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="97b3c-109">Bu kodu çalıştırdığınızda, aşağıdaki özel durumu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="97b3c-109">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="97b3c-110"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.XmlReader> , ,<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>Ve içinoluşturmakistediğinizözeldurumlarhakkındadahafazlabilgiiçinbelgelerinebakın.<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="97b3c-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  