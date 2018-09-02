---
title: 'Nasıl yapılır: ayrıştırma (Visual Basic) hatalarını yakalama'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: aa72b914d4640410a4d47ba49e774dcee31a54c0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406554"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="0bebe-102">Nasıl yapılır: ayrıştırma (Visual Basic) hatalarını yakalama</span><span class="sxs-lookup"><span data-stu-id="0bebe-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="0bebe-103">Bu konu, hatalı biçimlendirilmiş veya geçersiz XML nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bebe-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0bebe-104"> kullanılarak uygulanan <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="0bebe-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="0bebe-105">Hatalı biçimlendirilmiş veya geçersiz XML iletilmezse [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], arka plandaki <xref:System.Xml.XmlReader> sınıfı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0bebe-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="0bebe-106">XML gibi ayrıştırma çeşitli yöntemleri <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, özel durum yakalamayın; özel durumun daha sonra uygulamanız tarafından yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="0bebe-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="0bebe-107">XML değişmez değerleri kullanırsanız elde edilemiyor Not ayrıştırma hataları.</span><span class="sxs-lookup"><span data-stu-id="0bebe-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="0bebe-108">Visual Basic Derleyicisi, hatalı biçimlendirilmiş veya geçersiz XML hataları yakalar.</span><span class="sxs-lookup"><span data-stu-id="0bebe-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bebe-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0bebe-109">Example</span></span>  
 <span data-ttu-id="0bebe-110">Aşağıdaki kod, geçersiz XML ayrıştırmak çalışır:</span><span class="sxs-lookup"><span data-stu-id="0bebe-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="0bebe-111">Bu kodu çalıştırdığınızda, şu özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0bebe-111">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="0bebe-112">Bekleyebileceğiniz özel durumları hakkında bilgi <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, ve <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> oluşturmak için bkz <xref:System.Xml.XmlReader> belgeleri.</span><span class="sxs-lookup"><span data-stu-id="0bebe-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bebe-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0bebe-113">See Also</span></span>  
 [<span data-ttu-id="0bebe-114">Ayrıştırma XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bebe-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
