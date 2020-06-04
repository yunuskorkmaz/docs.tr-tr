---
title: Dosyalara serileştirme, TextWriters ve XmlWriters3
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: d8b929ef02b8fd9c6a9f29ea997a754699a6e1c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403569"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="61542-102">Dosya, TextWriters ve XmlWriters Serileştirme</span><span class="sxs-lookup"><span data-stu-id="61542-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="61542-103">XML ağaçlarını bir, a veya olarak seri hale getirebilirsiniz <xref:System.IO.File> <xref:System.IO.TextWriter> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="61542-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="61542-104">Yöntemini kullanarak, ve dahil olmak üzere herhangi bir XML bileşenini bir dizeye seri hale getirebilirsiniz <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> `ToString` .</span><span class="sxs-lookup"><span data-stu-id="61542-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="61542-105">Bir dizeye serileştirilirken biçimlendirmeyi bastırmak istiyorsanız <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61542-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="61542-106">Bir dosyaya serileştirilirken varsayılan davranış, elde edilen XML belgesini biçimlendirmek (Girintile).</span><span class="sxs-lookup"><span data-stu-id="61542-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="61542-107">Girinti yaptığınızda XML ağacındaki önemli boşluk korunmaz.</span><span class="sxs-lookup"><span data-stu-id="61542-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="61542-108">Biçimlendirme ile seri hale getirmek için, aşağıdaki yöntemlerin bağımsız değişken olarak olmayan aşırı yüklemelerinin birini kullanın <xref:System.Xml.Linq.SaveOptions> :</span><span class="sxs-lookup"><span data-stu-id="61542-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="61542-109">Seçeneği girintileme ve XML ağacındaki önemli boşlukları korumak istiyorsanız bağımsız değişken olarak kullanılan aşağıdaki yöntemlerin aşırı yüklemelerinin birini kullanın <xref:System.Xml.Linq.SaveOptions> :</span><span class="sxs-lookup"><span data-stu-id="61542-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="61542-110">Örnekler için, ilgili başvuru konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="61542-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="61542-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61542-111">See also</span></span>

- [<span data-ttu-id="61542-112">XML ağaçlarını serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61542-112">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
