---
title: 'Nasıl yapılır: Bir dosya, dize veya akıştan XML yükleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: ba88ae19abc216a318d6c2069ab0846d5db8a346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054174"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="e8f1a-102">Nasıl yapılır: Bir dosya, dize veya akıştan XML yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8f1a-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>

<span data-ttu-id="e8f1a-103">Çeşitli yöntemler kullanarak, [XML değişmez değerleri](../../../../visual-basic/language-reference/xml-literals/index.md) oluşturabilir ve bunları bir dosya, dize veya akış gibi bir dış kaynaktaki içerikle doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="e8f1a-104">Bu yöntemler aşağıdaki örneklerde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-104">These methods are shown in the following examples.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a><span data-ttu-id="e8f1a-105">Bir dosyadan XML yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e8f1a-105">To load XML from a file</span></span>

<span data-ttu-id="e8f1a-106">Bir <xref:System.Xml.Linq.XElement> `Load` veya <xref:System.Xml.Linq.XDocument> nesnesi gibi bir XML sabit değerini bir dosyadan doldurmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="e8f1a-107">Bu yöntem, giriş olarak bir dosya yolu, metin akışı veya XML akışı alabilir.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-107">This method can take a file path, text stream, or XML stream as input.</span></span>

<span data-ttu-id="e8f1a-108">Aşağıdaki kod örneği, bir <xref:System.Xml.Linq.XDocument.Load%28System.String%29> <xref:System.Xml.Linq.XDocument> nesneyi bir metin dosyasından XML ile doldurmak için yönteminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a><span data-ttu-id="e8f1a-109">Bir dizeden XML yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e8f1a-109">To load XML from a string</span></span>

<span data-ttu-id="e8f1a-110">Bir <xref:System.Xml.Linq.XElement> `Parse` veya <xref:System.Xml.Linq.XDocument> nesnesi gibi bir XML sabit değerini bir dizeden doldurmak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>

<span data-ttu-id="e8f1a-111">Aşağıdaki kod örneği bir dizeden XML ile bir <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument> nesneyi doldurmak için yönteminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="e8f1a-112">Akıştan XML yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e8f1a-112">To load XML from a stream</span></span>

<span data-ttu-id="e8f1a-113">Bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi gibi bir XML sabit değerini bir akıştan doldurmak için `Load` yöntemini veya <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="e8f1a-114">Aşağıdaki kod örneği, bir <xref:System.Xml.Linq.XNode.ReadFrom%2A> <xref:System.Xml.Linq.XDocument> nesneyi XML akışından XML ile doldurmak için yönteminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a><span data-ttu-id="e8f1a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8f1a-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e8f1a-116">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="e8f1a-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="e8f1a-117">XML</span><span class="sxs-lookup"><span data-stu-id="e8f1a-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="e8f1a-118">Visual Basic XML 'yi düzenleme</span><span class="sxs-lookup"><span data-stu-id="e8f1a-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
