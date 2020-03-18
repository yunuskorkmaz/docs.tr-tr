---
title: Dosya, TextWriters ve XmlWriters Serileştirme
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68868851"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="c8b52-102">Dosya, TextWriters ve XmlWriters Serileştirme</span><span class="sxs-lookup"><span data-stu-id="c8b52-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="c8b52-103">XML ağaçlarını bir <xref:System.IO.File>, a <xref:System.IO.TextWriter>veya <xref:System.Xml.XmlWriter>bir .</span><span class="sxs-lookup"><span data-stu-id="c8b52-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="c8b52-104">Yöntemi kullanarak <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> `ToString` herhangi bir XML bileşenini bir dize dahil ve seri hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8b52-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="c8b52-105">Bir dize serihale zaman biçimlendirmebastırmak istiyorsanız, <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8b52-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c8b52-106">Bir dosyaya serileştirme yaparken varsayılan davranış, ortaya çıkan XML belgesini biçimlendirmek (girinti) yapmaktır.</span><span class="sxs-lookup"><span data-stu-id="c8b52-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="c8b52-107">Girintisi yaptığınızda, XML ağacındaki önemsiz beyaz boşluk korunmaz.</span><span class="sxs-lookup"><span data-stu-id="c8b52-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="c8b52-108">Biçimlendirme ile serihale getirmek için, bağımsız değişken olarak kabul <xref:System.Xml.Linq.SaveOptions> etmeyen aşağıdaki yöntemlerin aşırı yüklerinden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="c8b52-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="c8b52-109">XML ağacındaki önemsiz beyaz alanı girinti yapmama ve koruma seçeneğini zedelemiyorsanız, aşağıdaki yöntemlerin <xref:System.Xml.Linq.SaveOptions> aşırı yüklerinden birini kullanarak bağımsız değişken olarak alır:</span><span class="sxs-lookup"><span data-stu-id="c8b52-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="c8b52-110">Örnekler için, uygun başvuru konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="c8b52-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8b52-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8b52-111">See also</span></span>

- [<span data-ttu-id="c8b52-112">XML Ağaçlarını Serihale Getirme (C#)</span><span class="sxs-lookup"><span data-stu-id="c8b52-112">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
