---
title: LINQ to XML dinamik özellikler başvurusu
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 48b51e92eb78786b2cc189e3e7daa00875b41585
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197046"
---
# <a name="linq-to-xml-dynamic-properties"></a><span data-ttu-id="4eeb8-102">LINQ to XML dinamik özellikleri</span><span class="sxs-lookup"><span data-stu-id="4eeb8-102">LINQ to XML dynamic properties</span></span>

<span data-ttu-id="4eeb8-103">Bu bölüm LINQ to XML içindeki dinamik özelliklerle ilgili başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4eeb8-103">This section provides reference information about the dynamic properties in LINQ to XML.</span></span> <span data-ttu-id="4eeb8-104">Özellikle, bu özellikler <xref:System.Xml.Linq> ad alanındaki <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> sınıfları tarafından gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4eeb8-104">Specifically, these properties are exposed by the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, which are in the <xref:System.Xml.Linq> namespace.</span></span>

<span data-ttu-id="4eeb8-105">[LINQ to XML Ile WPF veri bağlamaya genel bakış](wpf-data-binding-with-linq-to-xml-overview.md)konusunda açıklandığı gibi, dinamik özelliklerin her biri aynı sınıftaki standart ortak bir özellik veya yönteme eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="4eeb8-105">As explained in the topic [Overview of WPF data binding with LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), each of the dynamic properties is equivalent to a standard public property or method in the same class.</span></span> <span data-ttu-id="4eeb8-106">Bu standart Üyeler çoğu amaçla kullanılmalıdır; dinamik özellikler, LINQ to XML veri bağlama senaryoları için özel olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4eeb8-106">These standard members should be used for most purposes; dynamic properties are provided specifically for LINQ to XML data binding scenarios.</span></span> <span data-ttu-id="4eeb8-107">Bu sınıfların standart üyeleri hakkında daha fazla bilgi için, <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> başvuru konularına bakın.</span><span class="sxs-lookup"><span data-stu-id="4eeb8-107">For more information about the standard members of these classes, see the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> reference topics.</span></span>

<span data-ttu-id="4eeb8-108">Çözümlenme değerlerine göre, bu bölümdeki dinamik özellikler iki kategoriye ayrılır:</span><span class="sxs-lookup"><span data-stu-id="4eeb8-108">With respect to their resolved values, the dynamic properties in this section fall into two categories:</span></span>

- <span data-ttu-id="4eeb8-109">Tek bir değere çözüm veren <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> sınıflarında `Value` özellikleri gibi basit olanlar.</span><span class="sxs-lookup"><span data-stu-id="4eeb8-109">Simple ones, such as the `Value` properties in the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, that resolve to a single value.</span></span>

- <span data-ttu-id="4eeb8-110">Dizin Oluşturucu türünde çözümlenilen <xref:System.Xml.Linq.XElement> [öğeleri](elements-xelement-dynamic-property.md) ve [alt](descendants-xelement-dynamic-property.md) öğeler gibi dizinli değerler.</span><span class="sxs-lookup"><span data-stu-id="4eeb8-110">Indexed values, such as the [Elements](elements-xelement-dynamic-property.md) and [Descendants](descendants-xelement-dynamic-property.md) properties of <xref:System.Xml.Linq.XElement>, that resolve into an indexer type.</span></span> <span data-ttu-id="4eeb8-111">Dizin Oluşturucu türlerinin istenen değere veya koleksiyona çözümlenmesi için, bir genişletilmiş ad parametresi geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4eeb8-111">For indexer types to be resolved to the desired value or collection, an expanded name parameter must be passed to them.</span></span>

<span data-ttu-id="4eeb8-112"><xref:System.Collections.Generic.IEnumerable%601> türünde dizinli bir değer döndüren tüm dinamik özellikler ertelenmiş yürütmeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="4eeb8-112">All the dynamic properties that return an indexed value of type <xref:System.Collections.Generic.IEnumerable%601> use deferred execution.</span></span> <span data-ttu-id="4eeb8-113">Ertelenmiş yürütme hakkında daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="4eeb8-113">For more information about deferred execution, see [Introduction to LINQ queries (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="reference"></a><span data-ttu-id="4eeb8-114">Başvuru</span><span class="sxs-lookup"><span data-stu-id="4eeb8-114">Reference</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a><span data-ttu-id="4eeb8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4eeb8-115">See also</span></span>

- [<span data-ttu-id="4eeb8-116">LINQ to XML ile WPF verilerini bağlama</span><span class="sxs-lookup"><span data-stu-id="4eeb8-116">WPF data binding with LINQ to XML</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="4eeb8-117">LINQ to XML genel bakış ile WPF veri bağlama</span><span class="sxs-lookup"><span data-stu-id="4eeb8-117">WPF data binding with LINQ to XML overview</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="4eeb8-118">LINQ Sorgularına Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="4eeb8-118">Introduction to LINQ queries (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
