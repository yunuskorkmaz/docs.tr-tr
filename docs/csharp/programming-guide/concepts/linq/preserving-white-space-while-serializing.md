---
title: While Serializing3 boşluk koruma
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 7fd0a38d2a9ed8c4712b8e9a03a24a23b408f38a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44267095"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="68301-102">Serileştirirken boşlukları koruma</span><span class="sxs-lookup"><span data-stu-id="68301-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="68301-103">Bu konuda, bir XML ağacı serileştirilirken boşluk denetlemek nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68301-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="68301-104">Sık karşılaşılan bir senaryodur girintili XML oku, herhangi bir boşluk metin düğümleri (diğer bir deyişle, beyaz boşluk olmayan koruma) olmadan bir bellek içi XML ağacı oluşturmak, bazı XML işlemleri ve XML girintilemeli kaydedin sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="68301-104">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="68301-105">Biçimlendirme ile XML serileştirme, yalnızca önemli boşluk XML ağacındaki korunur.</span><span class="sxs-lookup"><span data-stu-id="68301-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="68301-106">Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="68301-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="68301-107">Başka bir yaygın bir senaryo, okuma ve değiştirme kasıtlı olarak girintili zaten XML sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="68301-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="68301-108">Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68301-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="68301-109">Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma ve XML serileştirme seçildiğinde biçimlendirmeyi devre dışı olduğunda bölünemez boşluğu koruyacak.</span><span class="sxs-lookup"><span data-stu-id="68301-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="68301-110">XML ağaçlarını serileştirme yöntemleri boşluk davranışını</span><span class="sxs-lookup"><span data-stu-id="68301-110">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="68301-111">Aşağıdaki yöntemleri <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıfların serileştirmek bir XML ağacı.</span><span class="sxs-lookup"><span data-stu-id="68301-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="68301-112">Bir dosyaya bir XML ağacı serileştirebilen bir <xref:System.IO.TextReader>, veya bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="68301-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="68301-113">`ToString` Yöntemi bir dizeye serileştirir.</span><span class="sxs-lookup"><span data-stu-id="68301-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="68301-114">Yöntem değil izlerseniz <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak, ardından yöntemi biçimlendirir (Girinti) serileştirilmiş XML.</span><span class="sxs-lookup"><span data-stu-id="68301-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="68301-115">Bu durumda, XML ağacı Önemsiz tüm bölünemez boşluğu göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="68301-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="68301-116">Yöntem alırsanız <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak, ardından yöntemi olmayan biçimlendirme belirtebilirsiniz (Girinti) serileştirilmiş XML.</span><span class="sxs-lookup"><span data-stu-id="68301-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="68301-117">Bu durumda, XML ağacındaki tüm boşluk korunur.</span><span class="sxs-lookup"><span data-stu-id="68301-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68301-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68301-118">See Also</span></span>

- [<span data-ttu-id="68301-119">Serileştirmek XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="68301-119">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
