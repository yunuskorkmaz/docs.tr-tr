---
title: "Nasıl yapılır: hatalar (C#) ayrıştırma Catch"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e541a004833ccd2aaecfd4ea13652b03a1270186
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="7e80d-102">Nasıl yapılır: hatalar (C#) ayrıştırma Catch</span><span class="sxs-lookup"><span data-stu-id="7e80d-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="7e80d-103">Bu konu, hatalı biçimlendirilmiş veya geçersiz XML algılamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7e80d-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7e80d-104">kullanılarak uygulanan <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="7e80d-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="7e80d-105">İçin hatalı biçimlendirilmiş veya geçersiz XML aktarılırsa [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], arka plandaki <xref:System.Xml.XmlReader> sınıfı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7e80d-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="7e80d-106">XML ayrıştırma gibi çeşitli yöntemler <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, özel durum catch değil; özel durum sonra uygulamanız tarafından yakalanan.</span><span class="sxs-lookup"><span data-stu-id="7e80d-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e80d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e80d-107">Example</span></span>  
 <span data-ttu-id="7e80d-108">Aşağıdaki kod, geçersiz XML Ayrıştırma dener:</span><span class="sxs-lookup"><span data-stu-id="7e80d-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="7e80d-109">Bu kodu çalıştırdığınızda, aşağıdaki özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="7e80d-109">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="7e80d-110">Bekleyebileceğiniz özel durumlar hakkında bilgi için <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, ve <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> atmak için bkz <xref:System.Xml.XmlReader> belgeleri.</span><span class="sxs-lookup"><span data-stu-id="7e80d-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e80d-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e80d-111">See Also</span></span>  
 [<span data-ttu-id="7e80d-112">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="7e80d-112">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
