---
title: Serileştirme yaparken Beyaz Boşluğu Koruma3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d357d40c13a66a152b3c8bb5f61e3a3374c4055
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484083"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="1c1ca-102">Serileştirirken Boşlukları Koruma</span><span class="sxs-lookup"><span data-stu-id="1c1ca-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="1c1ca-103">Bu konu, bir XML ağacını seri hale alırken beyaz alanı nasıl denetleriz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="1c1ca-104">Ortak bir senaryo girintisi XML okumak, herhangi bir beyaz boşluk metin düğümleri olmadan bir bellek XML ağacı oluşturmak (yani, beyaz boşluk koruyarak değil), XML bazı işlemler gerçekleştirmek ve sonra girintiyle XML kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-104">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="1c1ca-105">XML'yi biçimlendirme yle seri hale aldığınızda, XML ağacında yalnızca önemli beyaz boşluk korunur.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="1c1ca-106">Bu, '' [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="1c1ca-107">Başka bir yaygın senaryo okumak ve zaten kasıtlı olarak girintilmiş xml değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="1c1ca-108">Bu girintiyi herhangi bir şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="1c1ca-109">Bunu yapmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için, XML'i yüklerken veya ayrıştırırken beyaz alanı korur ve XML'i seri hale rirken biçimlendirmeyi devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="1c1ca-110">XML Ağaçlarını SeriHale Getiren Yöntemlerin Beyaz Alan Davranışı</span><span class="sxs-lookup"><span data-stu-id="1c1ca-110">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="1c1ca-111">Aşağıdaki yöntemler <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıflar da bir XML ağacı serihale.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="1c1ca-112">Bir XML ağacını bir dosyaya, <xref:System.IO.TextReader>bir <xref:System.Xml.XmlReader>dosyaya veya bir ' ye seri leştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="1c1ca-113">Yöntem `ToString` seri bir dize içinize.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-113">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="1c1ca-114">XElement.ToString()</span><span class="sxs-lookup"><span data-stu-id="1c1ca-114">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="1c1ca-115">XDocument.ToString()</span><span class="sxs-lookup"><span data-stu-id="1c1ca-115">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="1c1ca-116">Yöntem bir bağımsız <xref:System.Xml.Linq.SaveOptions> değişken olarak almazsa, yöntem serileştirilmiş XML biçimlendir (girintisi) olur.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-116">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="1c1ca-117">Bu durumda, XML ağacındaki tüm önemsiz beyaz boşluk atılır.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-117">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="1c1ca-118">Yöntem bir bağımsız <xref:System.Xml.Linq.SaveOptions> değişken olarak alırsa, o zaman yöntem indenist (girintisi) seri xml biçimlendirmek değil belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-118">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="1c1ca-119">Bu durumda, XML ağacındaki tüm beyaz boşluk korunur.</span><span class="sxs-lookup"><span data-stu-id="1c1ca-119">In this case, all white space in the XML tree is preserved.</span></span>  
