---
description: 'Daha fazla bilgi edinin: nasıl yapılır: bir dosyadan, dizeden veya akıştan XML yükleme (Visual Basic)'
title: 'Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 375190642c93d929abe2ae10bb6ccba927e3bc8a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480069"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="d26e0-103">Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d26e0-103">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>

<span data-ttu-id="d26e0-104">Çeşitli yöntemler kullanarak, [XML değişmez değerleri](../../../language-reference/xml-literals/index.md) oluşturabilir ve bunları bir dosya, dize veya akış gibi bir dış kaynaktaki içerikle doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d26e0-104">You can create [XML Literals](../../../language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="d26e0-105">Bu yöntemler aşağıdaki örneklerde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d26e0-105">These methods are shown in the following examples.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a><span data-ttu-id="d26e0-106">Bir dosyadan XML yüklemek için</span><span class="sxs-lookup"><span data-stu-id="d26e0-106">To load XML from a file</span></span>

<span data-ttu-id="d26e0-107">Bir veya nesnesi gibi bir XML sabit değerini bir dosyadan doldurmak için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> `Load` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d26e0-107">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="d26e0-108">Bu yöntem, giriş olarak bir dosya yolu, metin akışı veya XML akışı alabilir.</span><span class="sxs-lookup"><span data-stu-id="d26e0-108">This method can take a file path, text stream, or XML stream as input.</span></span>

<span data-ttu-id="d26e0-109">Aşağıdaki kod örneği, <xref:System.Xml.Linq.XDocument.Load%28System.String%29> <xref:System.Xml.Linq.XDocument> bir nesneyi bir metın dosyasından XML ile doldurmak için yönteminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d26e0-109">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a><span data-ttu-id="d26e0-110">Bir dizeden XML yüklemek için</span><span class="sxs-lookup"><span data-stu-id="d26e0-110">To load XML from a string</span></span>

<span data-ttu-id="d26e0-111">Bir veya nesnesi gibi bir XML sabit değerini <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> bir dizeden doldurmak için `Parse` yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d26e0-111">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>

<span data-ttu-id="d26e0-112">Aşağıdaki kod örneği <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument> BIR dizeden XML ile bir nesneyi doldurmak için yönteminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d26e0-112">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="d26e0-113">Akıştan XML yüklemek için</span><span class="sxs-lookup"><span data-stu-id="d26e0-113">To load XML from a stream</span></span>

<span data-ttu-id="d26e0-114">Bir veya nesnesi gibi bir XML sabit değerini bir akıştan doldurmak için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> `Load` yöntemini veya <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d26e0-114">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="d26e0-115">Aşağıdaki kod örneği, bir <xref:System.Xml.Linq.XNode.ReadFrom%2A> nesneyi XML AKıŞıNDAN XML ile doldurmak için yönteminin kullanımını gösterir <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="d26e0-115">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a><span data-ttu-id="d26e0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d26e0-116">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d26e0-117">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="d26e0-117">XML Literals</span></span>](../../../language-reference/xml-literals/index.md)
- [<span data-ttu-id="d26e0-118">XML</span><span class="sxs-lookup"><span data-stu-id="d26e0-118">XML</span></span>](index.md)
- [<span data-ttu-id="d26e0-119">Visual Basic'de XML'i Düzenleme</span><span class="sxs-lookup"><span data-stu-id="d26e0-119">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
