---
title: Dosya, TextWriters ve XmlWriters3 seri hale getirme
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: 63577d955da89fde0a2320b4cf84414ccbb69c84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786795"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="51268-102">Dosya, TextWriters ve XmlWriters Serileştirme</span><span class="sxs-lookup"><span data-stu-id="51268-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="51268-103">XML ağaçlarını serileştirebilen bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="51268-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="51268-104">Herhangi bir XML bileşeni serileştirebiliyorsa dahil olmak üzere <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement>, kullanarak bir dizeye `ToString` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="51268-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="51268-105">Bir dizeye serileştirilirken biçimlendirme gizlemek istiyorsanız, kullanabileceğiniz <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="51268-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="51268-106">Bir dosyaya serileştirmek kullanırken varsayılan davranış (Girinti) elde edilen XML belgeyi Biçimlendir sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="51268-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="51268-107">Girintisini zaman anlamsız boşluk XML ağacındaki korunmaz.</span><span class="sxs-lookup"><span data-stu-id="51268-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="51268-108">Biçimlendirme ile seri hale getirmek için aşırı almaz aşağıdaki yöntemlerden birini kullanın: <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="51268-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="51268-109">Seçeneği değil girinti ve XML ağacındaki Önemsiz bölünemez boşluğu koruyacak istiyorsanız, alan aşırı yüklemeler aşağıdaki yöntemlerden birini kullanın <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="51268-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="51268-110">Örnekler için uygun bir başvuru konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="51268-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="51268-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51268-111">See also</span></span>

- [<span data-ttu-id="51268-112">(Visual Basic) XML ağaçlarını serileştirme</span><span class="sxs-lookup"><span data-stu-id="51268-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
