---
title: "Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 572e34b1cd4813fad35e6afaf2ec3d0d9dac470a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="9fcbe-102">Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fcbe-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="9fcbe-103">Oluşturabileceğiniz [XML değişmez değerleri](../../../../visual-basic/language-reference/xml-literals/index.md) ve bunları bir dosya, dize veya bir akış gibi bir dış kaynaktan içeriğiyle birkaç yöntem kullanarak doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fcbe-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="9fcbe-104">Bu yöntemler aşağıdaki örneklerde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9fcbe-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="9fcbe-105">Bir dosyadan XML yüklemek için</span><span class="sxs-lookup"><span data-stu-id="9fcbe-105">To load XML from a file</span></span>  
  
-   <span data-ttu-id="9fcbe-106">Değişmez değer gibi bir XML doldurmak için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> dosyadan, kullanım nesne `Load` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9fcbe-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="9fcbe-107">Bu yöntem, giriş olarak bir dosya yolu, metin akış veya XML akışı alabilir.</span><span class="sxs-lookup"><span data-stu-id="9fcbe-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="9fcbe-108">Aşağıdaki kod örneğinde kullanımı gösterilmiştir <xref:System.Xml.Linq.XDocument.Load%28System.String%29> doldurmak için yöntemi bir <xref:System.Xml.Linq.XDocument> bir metin dosyasından XML nesnesiyle.</span><span class="sxs-lookup"><span data-stu-id="9fcbe-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="9fcbe-109">Bir dizeden XML yüklemek için</span><span class="sxs-lookup"><span data-stu-id="9fcbe-109">To load XML from a string</span></span>  
  
-   <span data-ttu-id="9fcbe-110">Değişmez değer gibi bir XML doldurmak için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> kullanabileceğiniz bir dizeden nesne `Parse` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9fcbe-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="9fcbe-111">Aşağıdaki kod örneğinde kullanımı gösterilmiştir <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> doldurmak için yöntemi bir <xref:System.Xml.Linq.XDocument> bir dizeden XML ile nesne.</span><span class="sxs-lookup"><span data-stu-id="9fcbe-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="9fcbe-112">Bir akıştan XML yüklemek için</span><span class="sxs-lookup"><span data-stu-id="9fcbe-112">To load XML from a stream</span></span>  
  
-   <span data-ttu-id="9fcbe-113">Değişmez değer gibi bir XML doldurmak için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> kullanabileceğiniz bir akıştan nesne `Load` yöntemi veya <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9fcbe-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="9fcbe-114">Aşağıdaki kod örneğinde kullanımı gösterilmiştir <xref:System.Xml.Linq.XNode.ReadFrom%2A> doldurmak için yöntemi bir <xref:System.Xml.Linq.XDocument> bir XML akışı XML'den nesnesiyle.</span><span class="sxs-lookup"><span data-stu-id="9fcbe-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9fcbe-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fcbe-115">See Also</span></span>  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="9fcbe-116">XML değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="9fcbe-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="9fcbe-117">XML</span><span class="sxs-lookup"><span data-stu-id="9fcbe-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="9fcbe-118">Visual Basic'te XML düzenleme</span><span class="sxs-lookup"><span data-stu-id="9fcbe-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
