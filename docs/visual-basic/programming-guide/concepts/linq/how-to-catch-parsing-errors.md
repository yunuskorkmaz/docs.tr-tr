---
title: "Nasıl yapılır: hatalar (Visual Basic) ayrıştırma Catch"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82b7c51aa8d0f9f64094211c56875e6595607c00
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="2811b-102">Nasıl yapılır: hatalar (Visual Basic) ayrıştırma Catch</span><span class="sxs-lookup"><span data-stu-id="2811b-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="2811b-103">Bu konu, hatalı biçimlendirilmiş veya geçersiz XML algılamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2811b-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2811b-104">kullanılarak uygulanan <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="2811b-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="2811b-105">İçin hatalı biçimlendirilmiş veya geçersiz XML aktarılırsa [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], arka plandaki <xref:System.Xml.XmlReader> sınıfı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2811b-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="2811b-106">XML ayrıştırma gibi çeşitli yöntemler <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, özel durum catch değil; özel durum sonra uygulamanız tarafından yakalanan.</span><span class="sxs-lookup"><span data-stu-id="2811b-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="2811b-107">XML değişmez değerleri kullanıyorsanız elde edilemiyor Not ayrıştırma hataları.</span><span class="sxs-lookup"><span data-stu-id="2811b-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="2811b-108">Visual Basic derleyici hataları hatalı biçimlendirilmiş veya geçersiz XML yakalar.</span><span class="sxs-lookup"><span data-stu-id="2811b-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2811b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="2811b-109">Example</span></span>  
 <span data-ttu-id="2811b-110">Aşağıdaki kod, geçersiz XML Ayrıştırma dener:</span><span class="sxs-lookup"><span data-stu-id="2811b-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="2811b-111">Bu kodu çalıştırdığınızda, aşağıdaki özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2811b-111">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="2811b-112">Bekleyebileceğiniz özel durumlar hakkında bilgi için <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, ve <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> atmak için bkz <xref:System.Xml.XmlReader> belgeleri.</span><span class="sxs-lookup"><span data-stu-id="2811b-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2811b-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2811b-113">See Also</span></span>  
 [<span data-ttu-id="2811b-114">Ayrıştırma XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2811b-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
