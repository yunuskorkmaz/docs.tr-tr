---
title: Dosya, TextWriters ve XmlWriters1 seri hale getirme
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: c74dc7f429e4ae27f08f7acb6b3a6c39161aac71
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483539"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="03388-102">Dosya, TextWriters ve XmlWriters Serileştirme</span><span class="sxs-lookup"><span data-stu-id="03388-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="03388-103">XML ağaçlarını serileştirebilen bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="03388-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="03388-104">Herhangi bir XML bileşeni serileştirebiliyorsa dahil olmak üzere <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement>, kullanarak bir dizeye `ToString` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03388-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="03388-105">Bir dizeye serileştirilirken biçimlendirme gizlemek istiyorsanız, kullanabileceğiniz <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03388-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="03388-106">Bir dosyaya serileştirmek kullanırken varsayılan davranış (Girinti) elde edilen XML belgeyi Biçimlendir sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="03388-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="03388-107">Girintisini zaman anlamsız boşluk XML ağacındaki korunmaz.</span><span class="sxs-lookup"><span data-stu-id="03388-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="03388-108">Biçimlendirme ile seri hale getirmek için aşırı almaz aşağıdaki yöntemlerden birini kullanın: <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="03388-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="03388-109">Seçeneği değil girinti ve XML ağacındaki Önemsiz bölünemez boşluğu koruyacak istiyorsanız, alan aşırı yüklemeler aşağıdaki yöntemlerden birini kullanın <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="03388-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="03388-110">Örnekler için uygun bir başvuru konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="03388-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="03388-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03388-111">See also</span></span>

- [<span data-ttu-id="03388-112">Serileştirmek XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="03388-112">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
