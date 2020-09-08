---
title: Serileştirilirken boşluğu koru-LINQ to XML
description: Bir XML ağacını serileştirmede çeşitli yollarla boşluk denetimi yapabilirsiniz.
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d907e68a2df3905794b555954330f31b5e75655
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553075"
---
# <a name="preserve-white-space-while-serializing-linq-to-xml"></a><span data-ttu-id="a01dd-103">Serileştirilirken boşluğu koru (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a01dd-103">Preserve white space while serializing (LINQ to XML)</span></span>

<span data-ttu-id="a01dd-104">Bu makalede, bir XML ağacı serileştirilirken beyaz boşluğun nasıl denetleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="a01dd-104">This article describes how to control white space when serializing an XML tree.</span></span>

<span data-ttu-id="a01dd-105">Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (yani, beyaz boşluğu korumadan), XML üzerinde bazı işlemler yapın ve ardından XML 'i girintilemeli olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a01dd-105">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="a01dd-106">XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur.</span><span class="sxs-lookup"><span data-stu-id="a01dd-106">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="a01dd-107">Bu, LINQ to XML için varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="a01dd-107">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="a01dd-108">Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="a01dd-108">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="a01dd-109">Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a01dd-109">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="a01dd-110">Bunu LINQ to XML yapmak için, XML 'yi yüklerken veya ayrıştırdığınızda veya XML 'yi seri hale alırken biçimlendirmeyi devre dışı bıraktığınızda boşluğu koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a01dd-110">To do this in LINQ to XML, you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>

## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="a01dd-111">XML ağaçlarını seri hale getirme yöntemlerinin beyaz boşluk davranışı</span><span class="sxs-lookup"><span data-stu-id="a01dd-111">White-space behavior of methods that serialize XML trees</span></span>

<span data-ttu-id="a01dd-112"><xref:System.Xml.Linq.XElement>Ve sınıflarında aşağıdaki yöntemler <xref:System.Xml.Linq.XDocument> bir xml ağacını serileştirin.</span><span class="sxs-lookup"><span data-stu-id="a01dd-112">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="a01dd-113">Bir XML ağacını bir dosyaya, a 'ya veya bir dosyasına seri hale getirebilirsiniz <xref:System.IO.TextReader> <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="a01dd-113">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="a01dd-114">`ToString`Yöntemi bir dizeye seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a01dd-114">The `ToString` method serializes to a string.</span></span>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a01dd-115">XElement. ToString ()</span><span class="sxs-lookup"><span data-stu-id="a01dd-115">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
- [<span data-ttu-id="a01dd-116">XDocument. ToString ()</span><span class="sxs-lookup"><span data-stu-id="a01dd-116">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)

<span data-ttu-id="a01dd-117">Yöntem <xref:System.Xml.Linq.SaveOptions> bir bağımsız değişken olarak ele yaramazsa, yöntemi SERILEŞTIRILMIŞ XML 'i biçimlendirir (girintili).</span><span class="sxs-lookup"><span data-stu-id="a01dd-117">If the method doesn't take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="a01dd-118">Bu durumda, XML ağacındaki tüm önemli boşluklar atılır.</span><span class="sxs-lookup"><span data-stu-id="a01dd-118">In this case, all insignificant white space in the XML tree is discarded.</span></span>

<span data-ttu-id="a01dd-119">Yöntemi <xref:System.Xml.Linq.SaveOptions> bir bağımsız değişken olarak ele alıyorsa, yöntemin SERILEŞTIRILMIŞ XML 'yi biçimlendirme (girintileme) seçeneğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a01dd-119">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="a01dd-120">Bu durumda, XML ağacındaki tüm boşluklar korunur.</span><span class="sxs-lookup"><span data-stu-id="a01dd-120">In this case, all white space in the XML tree is preserved.</span></span>
