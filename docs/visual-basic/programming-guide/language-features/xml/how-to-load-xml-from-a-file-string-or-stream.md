---
title: 'Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 241f6552e46d7689b42a409ba44bc747984773ca
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258410"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="41f51-102">Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41f51-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="41f51-103">Oluşturabileceğiniz [XML sabit değerleri](../../../../visual-basic/language-reference/xml-literals/index.md) ve bunları bir dosyaya, bir dize veya bir akışa gibi bir dış kaynaktan içeriğiyle çeşitli yöntemler kullanarak doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41f51-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="41f51-104">Bu yöntemler aşağıdaki örneklerde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="41f51-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="41f51-105">Bir dosyadan XML yüklenmedi</span><span class="sxs-lookup"><span data-stu-id="41f51-105">To load XML from a file</span></span>  
  
-   <span data-ttu-id="41f51-106">XML değişmez değer gibi doldurmak için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> dosyadan, kullanım nesne `Load` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="41f51-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="41f51-107">Bu yöntem, giriş olarak bir dosya yolu, metin akışına veya XML akışı alabilir.</span><span class="sxs-lookup"><span data-stu-id="41f51-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="41f51-108">Aşağıdaki kod örneği, kullanımını gösterir <xref:System.Xml.Linq.XDocument.Load%28System.String%29> doldurmak için yöntemi bir <xref:System.Xml.Linq.XDocument> bir metin dosyasındaki XML nesne.</span><span class="sxs-lookup"><span data-stu-id="41f51-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="41f51-109">Bir dizedeki XML yüklenmedi</span><span class="sxs-lookup"><span data-stu-id="41f51-109">To load XML from a string</span></span>  
  
-   <span data-ttu-id="41f51-110">XML değişmez değer gibi doldurmak için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> kullanabileceğiniz bir dizeden nesne `Parse` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="41f51-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="41f51-111">Aşağıdaki kod örneği, kullanımını gösterir <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> doldurmak için yöntemi bir <xref:System.Xml.Linq.XDocument> XML ile nesneden bir dize.</span><span class="sxs-lookup"><span data-stu-id="41f51-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="41f51-112">Bir akıştan XML yükleme için</span><span class="sxs-lookup"><span data-stu-id="41f51-112">To load XML from a stream</span></span>  
  
-   <span data-ttu-id="41f51-113">XML değişmez değer gibi doldurmak için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> kullanabileceğiniz bir akıştan nesne `Load` yöntemi veya <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="41f51-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="41f51-114">Aşağıdaki kod örneği, kullanımını gösterir <xref:System.Xml.Linq.XNode.ReadFrom%2A> doldurmak için yöntemi bir <xref:System.Xml.Linq.XDocument> bir XML akışı XML'den nesne.</span><span class="sxs-lookup"><span data-stu-id="41f51-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="41f51-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41f51-115">See Also</span></span>  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="41f51-116">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="41f51-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="41f51-117">XML</span><span class="sxs-lookup"><span data-stu-id="41f51-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="41f51-118">Visual Basic'de XML düzenleme</span><span class="sxs-lookup"><span data-stu-id="41f51-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
