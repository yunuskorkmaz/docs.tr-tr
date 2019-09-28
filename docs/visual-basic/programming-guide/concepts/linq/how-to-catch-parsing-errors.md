---
title: 'Nasıl yapılır: Catch Ayrıştırma hataları (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: a0c0749e8bc6d3fb1a71595778bfc5effaaf8533
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352934"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="9f08f-102">Nasıl yapılır: Catch Ayrıştırma hataları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f08f-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="9f08f-103">Bu konu, hatalı biçimlendirilmiş veya geçersiz XML 'nin nasıl algılanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9f08f-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="9f08f-104"><xref:System.Xml.XmlReader> kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9f08f-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="9f08f-105">Hatalı biçimlendirilmiş veya geçersiz XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ' a geçirilirse, temeldeki <xref:System.Xml.XmlReader> sınıfı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f08f-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="9f08f-106">@No__t-0 gibi XML 'yi ayrıştırmaya yönelik çeşitli yöntemler özel durumu yakalayamaz; özel durum daha sonra uygulamanız tarafından yakalanarak.</span><span class="sxs-lookup"><span data-stu-id="9f08f-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="9f08f-107">XML değişmez değerlerini kullanırsanız ayrıştırma hatalarını alamazsanız.</span><span class="sxs-lookup"><span data-stu-id="9f08f-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="9f08f-108">Visual Basic Derleyicisi hatalı biçimlendirilmiş veya geçersiz XML hatalarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="9f08f-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f08f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f08f-109">Example</span></span>  
 <span data-ttu-id="9f08f-110">Aşağıdaki kod geçersiz XML 'i ayrıştırmayı dener:</span><span class="sxs-lookup"><span data-stu-id="9f08f-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="9f08f-111">Bu kodu çalıştırdığınızda, aşağıdaki özel durumu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="9f08f-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="9f08f-112">@No__t-0, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> ve <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> yöntemlerinin throw olarak beklendiğini belirten özel durumlar hakkında daha fazla bilgi için, <xref:System.Xml.XmlReader> belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="9f08f-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f08f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f08f-113">See also</span></span>

- [<span data-ttu-id="9f08f-114">XML 'yi ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f08f-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
