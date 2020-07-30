---
title: Dosya, TextWriters ve XmlWriters Serileştirme
description: ToString veya Save yöntemlerini kullanarak XML ağaçlarını bir dosyaya, bir TextWriter 'a veya bir XmlWriter 'a seri hale getirme seçenekleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 43c51ae7e9bf1a7848d45fd900424d6186671e53
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302392"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="94433-103">Dosya, TextWriters ve XmlWriters Serileştirme</span><span class="sxs-lookup"><span data-stu-id="94433-103">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="94433-104">XML ağaçlarını bir, a veya olarak seri hale getirebilirsiniz <xref:System.IO.File> <xref:System.IO.TextWriter> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="94433-104">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="94433-105">Yöntemini kullanarak, ve dahil olmak üzere herhangi bir XML bileşenini bir dizeye seri hale getirebilirsiniz <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> `ToString` .</span><span class="sxs-lookup"><span data-stu-id="94433-105">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="94433-106">Bir dizeye serileştirilirken biçimlendirmeyi bastırmak istiyorsanız <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94433-106">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="94433-107">Bir dosyaya serileştirilirken varsayılan davranış, elde edilen XML belgesini biçimlendirmek (Girintile).</span><span class="sxs-lookup"><span data-stu-id="94433-107">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="94433-108">Girinti yaptığınızda XML ağacındaki önemli boşluk korunmaz.</span><span class="sxs-lookup"><span data-stu-id="94433-108">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="94433-109">Biçimlendirme ile seri hale getirmek için, aşağıdaki yöntemlerin bağımsız değişken olarak olmayan aşırı yüklemelerinin birini kullanın <xref:System.Xml.Linq.SaveOptions> :</span><span class="sxs-lookup"><span data-stu-id="94433-109">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="94433-110">Seçeneği girintileme ve XML ağacındaki önemli boşlukları korumak istiyorsanız bağımsız değişken olarak kullanılan aşağıdaki yöntemlerin aşırı yüklemelerinin birini kullanın <xref:System.Xml.Linq.SaveOptions> :</span><span class="sxs-lookup"><span data-stu-id="94433-110">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="94433-111">Örnekler için, ilgili başvuru konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="94433-111">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="94433-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94433-112">See also</span></span>

- [<span data-ttu-id="94433-113">XML ağaçlarını serileştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="94433-113">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
