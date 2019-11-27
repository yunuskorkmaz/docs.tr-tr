---
title: Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 12fbd1f4332391b1acdcf12e101d82627ebbeaff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335993"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="9acf6-102">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9acf6-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="9acf6-103">Bu konu, XML öğelerinin ve özniteliklerin XML sabit değerlerinde adlandırılması için Visual Basic yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9acf6-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="9acf6-104">Bir XML sabit değerinde yerel bir ad veya nitelikli bir ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9acf6-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="9acf6-105">Nitelikli bir ad, bir XML ad alanı öneki, iki nokta üst üste ve yerel bir ad içerir.</span><span class="sxs-lookup"><span data-stu-id="9acf6-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="9acf6-106">XML ad alanı önekleri hakkında daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="9acf6-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9acf6-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="9acf6-107">Rules</span></span>  
 <span data-ttu-id="9acf6-108">Visual Basic bir öğenin veya özniteliğin yerel adı aşağıdaki kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="9acf6-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
- <span data-ttu-id="9acf6-109">Bir ad alanı ile başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9acf6-109">It can begin with a namespace.</span></span> <span data-ttu-id="9acf6-110">Alfabetik bir karakter veya alt çizgi (`_`) ile başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9acf6-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="9acf6-111">Yalnızca alfabetik karakter, ondalık basamak, alt çizgi, nokta (.) ve kısa çizgi (-) içermelidir.</span><span class="sxs-lookup"><span data-stu-id="9acf6-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
- <span data-ttu-id="9acf6-112">En fazla 1.024 karakter uzunluğunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9acf6-112">It must not be more than 1,024 characters long.</span></span>  
  
- <span data-ttu-id="9acf6-113">Adlarda görünen iki nokta, ad alanı deyonumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9acf6-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="9acf6-114">Bu nedenle, yalnızca belirli bir ad için bir XML ad alanı belirtmek için iki nokta üst üste kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9acf6-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="9acf6-115">Ayrıca, aşağıdaki kılavuza uymalısınız.</span><span class="sxs-lookup"><span data-stu-id="9acf6-115">In addition, you should adhere to the following guideline.</span></span>  
  
- <span data-ttu-id="9acf6-116">XML 1,0 belirtimi, tüm büyük/küçük harf çeşitlerinin "xml" dizesiyle başlayan tüm adları ayırır.</span><span class="sxs-lookup"><span data-stu-id="9acf6-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="9acf6-117">Bu nedenle, bu adları öğe ve öznitelik adları için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="9acf6-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="9acf6-118">Ad uzunluğu yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9acf6-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="9acf6-119">Pratik bir şekilde, öğenin yapısını açıkça tanımlarken bir ad mümkün olduğunca kısa olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9acf6-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="9acf6-120">Bu, kodunuzun okunabilirliğini artırır ve satır uzunluğunu ve kaynak dosya boyutunu azaltır.</span><span class="sxs-lookup"><span data-stu-id="9acf6-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="9acf6-121">Bununla birlikte, adınız, öğeyi veya kodunuzun onu nasıl kullandığını yeterince tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9acf6-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="9acf6-122">Bu, kodunuzun okunabilirliğini açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9acf6-122">This is important for the readability of your code.</span></span> <span data-ttu-id="9acf6-123">Başka birisi bunu anlamaya çalışıyorsa veya siz onu yazdıktan sonra uzun bir süre arıyorsanız, uygun öğe adları zamandan tasarruf edebilir.</span><span class="sxs-lookup"><span data-stu-id="9acf6-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="9acf6-124">Adlarda büyük/küçük harf duyarlılığı</span><span class="sxs-lookup"><span data-stu-id="9acf6-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="9acf6-125">XML öğesi adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="9acf6-125">XML element names are case sensitive.</span></span> <span data-ttu-id="9acf6-126">Bu, Visual Basic derleyici yalnızca alfabetik durumda farklılık gösteren iki adı karşılaştırırken, bunları farklı adlar olarak yorumladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9acf6-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="9acf6-127">Örneğin, `ABC` ve `abc` ayrı öğelere başvuran olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="9acf6-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="9acf6-128">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="9acf6-128">XML Namespaces</span></span>  
 <span data-ttu-id="9acf6-129">XML öğesi değişmez değeri oluştururken, öğe adı için XML ad alanı önekini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9acf6-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="9acf6-130">Daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="9acf6-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9acf6-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9acf6-131">See also</span></span>

- [<span data-ttu-id="9acf6-132">Visual Basic XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="9acf6-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="9acf6-133">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="9acf6-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
