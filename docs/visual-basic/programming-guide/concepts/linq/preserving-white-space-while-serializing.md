---
title: Serializing2 sırasında boşluk koruma
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: e9b73089830bf7e6cb0ea9e469bf667f12c571d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396408"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="48436-102">Serileştirirken Boşlukları Koruma</span><span class="sxs-lookup"><span data-stu-id="48436-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="48436-103">Bu konu, bir XML ağacı serileştirilirken boşluk denetimini nasıl denetleyebileceğinizi açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="48436-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="48436-104">Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (diğer bir deyişle, beyaz alanı korumadan), XML üzerinde bazı işlemleri gerçekleştirir ve ardından XML 'i girintilemeli olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="48436-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="48436-105">XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur.</span><span class="sxs-lookup"><span data-stu-id="48436-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="48436-106">Bu varsayılan davranıştır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48436-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="48436-107">Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="48436-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="48436-108">Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48436-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="48436-109">Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , XML 'i yüklediğinizde veya ayrıştırdığınızda veya XML 'yi seri hale alırken biçimlendirmeyi devre dışı bıraktığınızda boşluğu koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48436-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="48436-110">XML ağaçlarını seri hale getirme yöntemlerinin boşluk davranışı</span><span class="sxs-lookup"><span data-stu-id="48436-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="48436-111"><xref:System.Xml.Linq.XElement>Ve sınıflarında aşağıdaki yöntemler <xref:System.Xml.Linq.XDocument> bir xml ağacını serileştirin.</span><span class="sxs-lookup"><span data-stu-id="48436-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="48436-112">Bir XML ağacını bir dosyaya, a 'ya veya bir dosyasına seri hale getirebilirsiniz <xref:System.IO.TextReader> <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="48436-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="48436-113">`ToString`Yöntemi bir dizeye seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="48436-113">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="48436-114">XElement. ToString ()</span><span class="sxs-lookup"><span data-stu-id="48436-114">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="48436-115">XDocument. ToString ()</span><span class="sxs-lookup"><span data-stu-id="48436-115">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="48436-116">Yöntem <xref:System.Xml.Linq.SaveOptions> bir bağımsız değişken olarak kullanmıyorsa, yöntemi SERILEŞTIRILMIŞ XML 'i biçimlendirir (girintili).</span><span class="sxs-lookup"><span data-stu-id="48436-116">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="48436-117">Bu durumda, XML ağacındaki tüm önemli boşluklar atılır.</span><span class="sxs-lookup"><span data-stu-id="48436-117">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="48436-118">Yöntemi <xref:System.Xml.Linq.SaveOptions> bir bağımsız değişken olarak ele alıyorsa, yöntemin SERILEŞTIRILMIŞ XML 'yi biçimlendirme (girintileme) seçeneğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48436-118">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="48436-119">Bu durumda, XML ağacındaki tüm boşluklar korunur.</span><span class="sxs-lookup"><span data-stu-id="48436-119">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48436-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48436-120">See also</span></span>

- [<span data-ttu-id="48436-121">XML ağaçlarını serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48436-121">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
