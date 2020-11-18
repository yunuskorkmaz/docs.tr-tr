---
title: DOM’da XML Belgesi Okuma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 40efccba86f1bca8af838961dccdc7f98f8c93c2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820403"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="8f718-102">DOM’da XML Belgesi Okuma</span><span class="sxs-lookup"><span data-stu-id="8f718-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="8f718-103">XML bilgileri farklı biçimlerden belleğe okundu.</span><span class="sxs-lookup"><span data-stu-id="8f718-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="8f718-104">Bir dize, akış, URL, metin okuyucu veya öğesinden türetilmiş bir sınıftan okunabilir <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="8f718-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="8f718-105"><xref:System.Xml.XmlDocument.Load%2A>Yöntemi, belgeyi belleğe getirir ve farklı biçimlerden her birinden veri almak için kullanılabilir yöntemler daha fazla bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="8f718-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="8f718-106">Ayrıca, <xref:System.Xml.XmlDocument.LoadXml%2A> bir DIZEDEN XML okuyan bir yöntem de vardır.</span><span class="sxs-lookup"><span data-stu-id="8f718-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="8f718-107">Farklı <xref:System.Xml.XmlDocument.Load%2A> Yöntemler, XML belge nesne modeli (DOM) yüklendiğinde hangi düğümlerin oluşturulduğunu etkiler.</span><span class="sxs-lookup"><span data-stu-id="8f718-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="8f718-108">Aşağıdaki tabloda, <xref:System.Xml.XmlDocument.Load%2A> bunları ele alan bazı yöntemler ve konular arasındaki farklılıklar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8f718-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="8f718-109">Konu</span><span class="sxs-lookup"><span data-stu-id="8f718-109">Subject</span></span>|<span data-ttu-id="8f718-110">Konu</span><span class="sxs-lookup"><span data-stu-id="8f718-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="8f718-111">Boşluk düğümleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f718-111">Creation of white space nodes</span></span>|<span data-ttu-id="8f718-112">DOM 'ı yüklemek için kullanılan nesnenin, DOM 'da oluşturulan, boşluk ve önemli boşluk düğümleri üzerinde bir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="8f718-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="8f718-113">Daha fazla bilgi için bkz. [Dom yüklenirken beyaz boşluk ve önemli boşluk işleme](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="8f718-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="8f718-114">Belirli bir düğümden başlayarak XML yükleme veya tüm XML belgesi yükleme</span><span class="sxs-lookup"><span data-stu-id="8f718-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="8f718-115"><xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType>Yöntem verilerinin kullanılması, belirli bir DÜĞÜMDEN Dom 'a yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8f718-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="8f718-116">Daha fazla bilgi için bkz. [okuyucudan veri yükleme](load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="8f718-116">For more information, see [Load Data from a Reader](load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="8f718-117">XML yüklendiği için doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="8f718-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="8f718-118">DOM 'a yüklenen XML verileri, yüklendiği için doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8f718-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="8f718-119">Bu, doğrulama kullanılarak gerçekleştirilir <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="8f718-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="8f718-120">XML 'nin yüklendiği şekilde doğrulanması hakkında daha fazla bilgi için bkz. [Dom 'da BIR XML belgesini doğrulama](validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="8f718-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="8f718-121">Aşağıdaki örnek, yöntemi ile yüklenmekte olan XML <xref:System.Xml.XmlDocument.LoadXml%2A> ve daha sonra adlı bir metin dosyasına kaydedilen verileri gösterir `data.xml` .</span><span class="sxs-lookup"><span data-stu-id="8f718-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f718-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f718-122">See also</span></span>

- [<span data-ttu-id="8f718-123">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="8f718-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
