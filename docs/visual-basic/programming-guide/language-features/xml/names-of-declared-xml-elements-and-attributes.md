---
description: 'Hakkında daha fazla bilgi edinin: belirtilen XML öğelerinin ve özniteliklerin adları (Visual Basic)'
title: Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 0c5d049a7d877a23562b91c5d7b3306d8e68ea3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422737"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="3fe47-103">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fe47-103">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>

<span data-ttu-id="3fe47-104">Bu konu, XML öğelerinin ve özniteliklerin XML sabit değerlerinde adlandırılması için Visual Basic yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fe47-104">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="3fe47-105">Bir XML sabit değerinde yerel bir ad veya nitelikli bir ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fe47-105">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="3fe47-106">Nitelikli bir ad, bir XML ad alanı öneki, iki nokta üst üste ve yerel bir ad içerir.</span><span class="sxs-lookup"><span data-stu-id="3fe47-106">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="3fe47-107">XML ad alanı önekleri hakkında daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../../../language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="3fe47-107">For more information about XML namespace prefixes, see [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3fe47-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="3fe47-108">Rules</span></span>  

 <span data-ttu-id="3fe47-109">Visual Basic bir öğenin veya özniteliğin yerel adı aşağıdaki kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fe47-109">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
- <span data-ttu-id="3fe47-110">Bir ad alanı ile başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="3fe47-110">It can begin with a namespace.</span></span> <span data-ttu-id="3fe47-111">Alfabetik bir karakter veya alt çizgi () ile başlamalıdır `_` .</span><span class="sxs-lookup"><span data-stu-id="3fe47-111">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="3fe47-112">Yalnızca alfabetik karakter, ondalık basamak, alt çizgi, nokta (.) ve kısa çizgi (-) içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3fe47-112">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
- <span data-ttu-id="3fe47-113">En fazla 1.024 karakter uzunluğunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fe47-113">It must not be more than 1,024 characters long.</span></span>  
  
- <span data-ttu-id="3fe47-114">Adlarda görünen iki nokta, ad alanı deyonumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fe47-114">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="3fe47-115">Bu nedenle, yalnızca belirli bir ad için bir XML ad alanı belirtmek için iki nokta üst üste kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fe47-115">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="3fe47-116">Ayrıca, aşağıdaki kılavuza uymalısınız.</span><span class="sxs-lookup"><span data-stu-id="3fe47-116">In addition, you should adhere to the following guideline.</span></span>  
  
- <span data-ttu-id="3fe47-117">XML 1,0 belirtimi, tüm büyük/küçük harf çeşitlerinin "xml" dizesiyle başlayan tüm adları ayırır.</span><span class="sxs-lookup"><span data-stu-id="3fe47-117">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="3fe47-118">Bu nedenle, bu adları öğe ve öznitelik adları için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="3fe47-118">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="3fe47-119">Ad uzunluğu yönergeleri</span><span class="sxs-lookup"><span data-stu-id="3fe47-119">Name Length Guidelines</span></span>  

 <span data-ttu-id="3fe47-120">Pratik bir şekilde, öğenin yapısını açıkça tanımlarken bir ad mümkün olduğunca kısa olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fe47-120">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="3fe47-121">Bu, kodunuzun okunabilirliğini artırır ve satır uzunluğunu ve kaynak dosya boyutunu azaltır.</span><span class="sxs-lookup"><span data-stu-id="3fe47-121">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="3fe47-122">Bununla birlikte, adınız, öğeyi veya kodunuzun onu nasıl kullandığını yeterince tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="3fe47-122">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="3fe47-123">Bu, kodunuzun okunabilirliğini açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3fe47-123">This is important for the readability of your code.</span></span> <span data-ttu-id="3fe47-124">Başka birisi bunu anlamaya çalışıyorsa veya siz onu yazdıktan sonra uzun bir süre arıyorsanız, uygun öğe adları zamandan tasarruf edebilir.</span><span class="sxs-lookup"><span data-stu-id="3fe47-124">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="3fe47-125">Adlarda büyük/küçük harf duyarlılığı</span><span class="sxs-lookup"><span data-stu-id="3fe47-125">Case Sensitivity in Names</span></span>  

 <span data-ttu-id="3fe47-126">XML öğesi adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fe47-126">XML element names are case sensitive.</span></span> <span data-ttu-id="3fe47-127">Bu, Visual Basic derleyici yalnızca alfabetik durumda farklılık gösteren iki adı karşılaştırırken, bunları farklı adlar olarak yorumladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3fe47-127">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="3fe47-128">Örneğin, `ABC` ve `abc` ayrı öğelere başvuran olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="3fe47-128">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="3fe47-129">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="3fe47-129">XML Namespaces</span></span>  

 <span data-ttu-id="3fe47-130">XML öğesi değişmez değeri oluştururken, öğe adı için XML ad alanı önekini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fe47-130">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="3fe47-131">Daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../../../language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="3fe47-131">For more information, see [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe47-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fe47-132">See also</span></span>

- [<span data-ttu-id="3fe47-133">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3fe47-133">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="3fe47-134">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="3fe47-134">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
