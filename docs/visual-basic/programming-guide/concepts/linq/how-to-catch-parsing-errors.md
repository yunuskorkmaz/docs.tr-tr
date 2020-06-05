---
title: 'Nasıl yapılır: Ayrıştırma Hatalarını Yakalama'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: c0b46d7df270dd6f081a0c736b6978088cfbd9c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375154"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="95713-102">Nasıl yapılır: ayrıştırma hatalarını yakalama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95713-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="95713-103">Bu konu, hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="95713-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="95713-104">kullanılarak uygulanır <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="95713-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="95713-105">Hatalı biçimlendirilmiş veya geçersiz XML öğesine geçirilirse [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , temeldeki <xref:System.Xml.XmlReader> sınıf bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95713-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="95713-106">XML 'yi Ayrıştır gibi çeşitli yöntemler <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> özel durumu yakalamayın; özel durum daha sonra uygulamanız tarafından yakalanamaz.</span><span class="sxs-lookup"><span data-stu-id="95713-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="95713-107">XML değişmez değerlerini kullanırsanız ayrıştırma hatalarını alamazsanız.</span><span class="sxs-lookup"><span data-stu-id="95713-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="95713-108">Visual Basic Derleyicisi hatalı biçimlendirilmiş veya geçersiz XML hatalarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="95713-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95713-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="95713-109">Example</span></span>  
 <span data-ttu-id="95713-110">Aşağıdaki kod geçersiz XML 'i ayrıştırmayı dener:</span><span class="sxs-lookup"><span data-stu-id="95713-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="95713-111">Bu kodu çalıştırdığınızda, aşağıdaki özel durumu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="95713-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="95713-112"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>,, Ve için oluşturmak istediğiniz özel durumlar hakkında daha fazla bilgi için <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> <xref:System.Xml.XmlReader> belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="95713-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95713-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95713-113">See also</span></span>

- [<span data-ttu-id="95713-114">XML 'yi ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95713-114">Parsing XML (Visual Basic)</span></span>](parsing-xml.md)
