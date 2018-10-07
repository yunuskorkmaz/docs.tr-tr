---
title: DOM'da XML belgesi okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9031f5df0d0f48dc2844cdfd0654ee4ab876cc22
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842534"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="fcee7-102">DOM'da XML belgesi okuma</span><span class="sxs-lookup"><span data-stu-id="fcee7-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="fcee7-103">Farklı biçimler belleğe XML bilgileri okuyun.</span><span class="sxs-lookup"><span data-stu-id="fcee7-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="fcee7-104">Bir dize, akış, URL, metin okuyucuyu ya da türetilen bir sınıf okunabilir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="fcee7-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="fcee7-105"><xref:System.Xml.XmlDocument.Load%2A> Yöntemi her farklı biçimlerde veri almak için kullanılabilen yöntemler aşırı yüklü ve belleğe belge getirir.</span><span class="sxs-lookup"><span data-stu-id="fcee7-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="fcee7-106">Ayrıca bir <xref:System.Xml.XmlDocument.LoadXml%2A> XML bir dizeden okur yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fcee7-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="fcee7-107">Farklı <xref:System.Xml.XmlDocument.Load%2A> yöntemleri etkileyen XML belge nesne modeli (DOM) yüklendiğinde hangi düğümleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fcee7-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="fcee7-108">Aşağıdaki tabloda bazı arasındaki farklar listelenmektedir <xref:System.Xml.XmlDocument.Load%2A> yöntemleri ve onları adreslemek konuları.</span><span class="sxs-lookup"><span data-stu-id="fcee7-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="fcee7-109">Konu</span><span class="sxs-lookup"><span data-stu-id="fcee7-109">Subject</span></span>|<span data-ttu-id="fcee7-110">Konu</span><span class="sxs-lookup"><span data-stu-id="fcee7-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="fcee7-111">Boşluk düğümleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="fcee7-111">Creation of white space nodes</span></span>|<span data-ttu-id="fcee7-112">DOM yükleme için kullanılan nesne boşluk ve DOM oluşturulan önemli boşluk düğümleri üzerinde bir etkisi</span><span class="sxs-lookup"><span data-stu-id="fcee7-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="fcee7-113">Daha fazla bilgi için [boşluk ve önemli boşluk DOM yüklerken işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="fcee7-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="fcee7-114">Belirli bir düğümünden başlayan XML yüklenirken veya tüm XML belgesi yüklenirken</span><span class="sxs-lookup"><span data-stu-id="fcee7-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="fcee7-115">Kullanarak <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> yöntemi veri yüklenebilir belirli bir düğüm DOM'a</span><span class="sxs-lookup"><span data-stu-id="fcee7-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="fcee7-116">Daha fazla bilgi için [bir okuyucudan veri yükleme](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="fcee7-116">For more information, see [Load Data from a Reader](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="fcee7-117">XML olarak doğrulama yüklendi</span><span class="sxs-lookup"><span data-stu-id="fcee7-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="fcee7-118">Yüklü olduğu gibi DOM'a XML verileri doğrulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="fcee7-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="fcee7-119">Bu bir doğrulama kullanılarak gerçekleştirilir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="fcee7-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="fcee7-120">Yüklü olduğu gibi XML doğrulama hakkında daha fazla bilgi için bkz. [doğrulama bir XML belgesi DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="fcee7-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="fcee7-121">Aşağıdaki örnek, XML ile yüklenen gösterir <xref:System.Xml.XmlDocument.LoadXml%2A> yöntemi ve daha sonra bir metin dosyasına kaydedilmiş veri adlı `data.xml`.</span><span class="sxs-lookup"><span data-stu-id="fcee7-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fcee7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcee7-122">See also</span></span>

- [<span data-ttu-id="fcee7-123">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="fcee7-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
