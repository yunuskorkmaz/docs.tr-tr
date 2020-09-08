---
title: Dosyalar, TextWriters ve Xmlyazıcılarında serileştirme-LINQ to XML
description: XML ağaçlarını bir dosya, bir TextWriter veya XmlWriter 'a seri hale getirebilirsiniz ve XDocument ve XElement dahil XML bileşenlerini ToString yöntemini kullanarak bir dizeye seri hale getirebilirsiniz.
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20651c06a759d83934c4b035a42eac7c2700eb9f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553929"
---
# <a name="serialize-to-files-textwriters-and-xmlwriters-linq-to-xml"></a><span data-ttu-id="4db1c-103">Dosyalar, TextWriters ve Xmlyazıcılarında serileştirme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4db1c-103">Serialize to files, TextWriters, and XmlWriters (LINQ to XML)</span></span>

<span data-ttu-id="4db1c-104">XML ağaçlarını bir, a veya olarak seri hale getirebilirsiniz <xref:System.IO.File> <xref:System.IO.TextWriter> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="4db1c-104">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="4db1c-105">Yöntemini kullanarak, ve dahil olmak üzere herhangi bir XML bileşenini bir dizeye seri hale getirebilirsiniz <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> `ToString` .</span><span class="sxs-lookup"><span data-stu-id="4db1c-105">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="4db1c-106">Bir dizeye serileştirilirken biçimlendirmeyi bastırmak istiyorsanız <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4db1c-106">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4db1c-107">Bir dosyaya serileştirilirken varsayılan davranış, elde edilen XML belgesini biçimlendirmek (Girintile).</span><span class="sxs-lookup"><span data-stu-id="4db1c-107">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="4db1c-108">Girinti yaptığınızda XML ağacındaki önemli boşluk korunmaz.</span><span class="sxs-lookup"><span data-stu-id="4db1c-108">When you indent, the insignificant white space in the XML tree isn't preserved.</span></span> <span data-ttu-id="4db1c-109">Biçimlendirme ile seri hale getirmek için, aşağıdaki yöntemlerin bağımsız değişken olarak olmayan aşırı yüklemelerinin birini kullanın <xref:System.Xml.Linq.SaveOptions> :</span><span class="sxs-lookup"><span data-stu-id="4db1c-109">To serialize with formatting, use one of the overloads of the following methods that don't take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="4db1c-110">Seçeneği girintileme ve XML ağacındaki önemli boşlukları korumak istiyorsanız bağımsız değişken olarak kullanılan aşağıdaki yöntemlerin aşırı yüklemelerinin birini kullanın <xref:System.Xml.Linq.SaveOptions> :</span><span class="sxs-lookup"><span data-stu-id="4db1c-110">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="4db1c-111">Örnekler için ilgili başvuru makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="4db1c-111">For examples, see the appropriate reference article.</span></span>
