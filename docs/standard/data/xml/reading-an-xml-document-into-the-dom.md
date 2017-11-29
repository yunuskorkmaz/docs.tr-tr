---
title: Bir XML belgesi DOM okuma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b8844705b492574443ff4f37de33ccaf1f5fedd7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="c77c0-102">Bir XML belgesi DOM okuma</span><span class="sxs-lookup"><span data-stu-id="c77c0-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="c77c0-103">Farklı biçimlerden belleğe XML bilgileri okuyun.</span><span class="sxs-lookup"><span data-stu-id="c77c0-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="c77c0-104">Bir dize, akışı, URL, metin okuyucu veya türetilmiş bir sınıf okunabilir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c77c0-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="c77c0-105"><xref:System.Xml.XmlDocument.Load%2A> Yöntemi belge belleğe getirir ve her biri farklı biçimlerde verileri almak için kullanılabilen yöntemler aşırı yüklü.</span><span class="sxs-lookup"><span data-stu-id="c77c0-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="c77c0-106">Ayrıca bir <xref:System.Xml.XmlDocument.LoadXml%2A> bir dizeden XML okur yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c77c0-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="c77c0-107">Farklı <xref:System.Xml.XmlDocument.Load%2A> yöntemleri etkileyen XML belge nesne modeli (DOM) yüklendiğinde hangi düğümlerin oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c77c0-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="c77c0-108">Aşağıdaki tabloda bazı arasındaki farklar listelenmektedir <xref:System.Xml.XmlDocument.Load%2A> yöntemleri ve bunları adres Konular.</span><span class="sxs-lookup"><span data-stu-id="c77c0-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="c77c0-109">Konu</span><span class="sxs-lookup"><span data-stu-id="c77c0-109">Subject</span></span>|<span data-ttu-id="c77c0-110">Konu</span><span class="sxs-lookup"><span data-stu-id="c77c0-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="c77c0-111">Beyaz alan düğümlerinin oluşturma</span><span class="sxs-lookup"><span data-stu-id="c77c0-111">Creation of white space nodes</span></span>|<span data-ttu-id="c77c0-112">DOM yükleme için kullanılan nesne boşluk ve DOM içinde oluşturulan önemli boşluk düğümleri üzerinde bir etkisi</span><span class="sxs-lookup"><span data-stu-id="c77c0-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="c77c0-113">Daha fazla bilgi için bkz: [boşluk ve önemli boşluk DOM yüklenirken işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="c77c0-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="c77c0-114">Belirli bir düğümünden başlayan XML yüklenirken veya tüm XML belgesi yüklenirken</span><span class="sxs-lookup"><span data-stu-id="c77c0-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="c77c0-115">Kullanarak <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> yöntemi veri yüklenebilir belirli bir düğümden DOM</span><span class="sxs-lookup"><span data-stu-id="c77c0-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="c77c0-116">Daha fazla bilgi için bkz: [bir okuyucu yük verileri](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="c77c0-116">For more information, see [Load Data from a Reader](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="c77c0-117">XML olarak doğrulama yüklendi</span><span class="sxs-lookup"><span data-stu-id="c77c0-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="c77c0-118">Yüklendiği gibi DOM yüklenen XML veriler doğrulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="c77c0-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="c77c0-119">Bu bir doğrulama kullanılarak gerçekleştirilir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c77c0-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="c77c0-120">Yüklendiği gibi XML doğrulama hakkında daha fazla bilgi için bkz: [XML belgesi DOM içinde doğrulama](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="c77c0-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="c77c0-121">Aşağıdaki örnek ile yüklenen XML gösterir <xref:System.Xml.XmlDocument.LoadXml%2A> yöntemi ve daha sonra bir metin dosyasına kaydedilen verileri adlı `data.xml`.</span><span class="sxs-lookup"><span data-stu-id="c77c0-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c77c0-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c77c0-122">See Also</span></span>  
 [<span data-ttu-id="c77c0-123">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="c77c0-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
