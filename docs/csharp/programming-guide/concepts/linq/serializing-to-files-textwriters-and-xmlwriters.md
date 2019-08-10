---
title: Dosya, TextWriters ve XmlWriters Serileştirme
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868851"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="c5c0a-102">Dosya, TextWriters ve XmlWriters Serileştirme</span><span class="sxs-lookup"><span data-stu-id="c5c0a-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="c5c0a-103">XML ağaçlarını bir <xref:System.IO.File>, a <xref:System.IO.TextWriter>veya <xref:System.Xml.XmlWriter>olarak seri hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5c0a-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="c5c0a-104">Yöntemini kullanarak, ve <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement>dahil olmak üzere herhangi bir XML bileşenini bir dizeye seri hale getirebilirsiniz. `ToString`</span><span class="sxs-lookup"><span data-stu-id="c5c0a-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="c5c0a-105">Bir dizeye serileştirilirken biçimlendirmeyi bastırmak istiyorsanız <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5c0a-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c5c0a-106">Bir dosyaya serileştirilirken varsayılan davranış, elde edilen XML belgesini biçimlendirmek (Girintile).</span><span class="sxs-lookup"><span data-stu-id="c5c0a-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="c5c0a-107">Girinti yaptığınızda XML ağacındaki önemli boşluk korunmaz.</span><span class="sxs-lookup"><span data-stu-id="c5c0a-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="c5c0a-108">Biçimlendirme ile seri hale getirmek için, aşağıdaki yöntemlerin <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak olmayan aşırı yüklemelerinin birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="c5c0a-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="c5c0a-109">Seçeneği girintileme ve XML ağacındaki önemli boşlukları korumak istiyorsanız bağımsız değişken <xref:System.Xml.Linq.SaveOptions> olarak kullanılan aşağıdaki yöntemlerin aşırı yüklemelerinin birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="c5c0a-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="c5c0a-110">Örnekler için, ilgili başvuru konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="c5c0a-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5c0a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5c0a-111">See also</span></span>

- [<span data-ttu-id="c5c0a-112">XML ağaçlarını serileştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="c5c0a-112">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
