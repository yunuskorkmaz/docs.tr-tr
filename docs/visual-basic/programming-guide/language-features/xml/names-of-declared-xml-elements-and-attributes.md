---
title: Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07666ead0770c8055a62f75cb481648b0c72ef8b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="2c76e-102">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c76e-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="2c76e-103">Bu konu, XML öğeleri ve özniteliklerinin XML değişmez değerlerinde adlandırmak için Visual Basic yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c76e-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="2c76e-104">XML değişmez değer, bir yerel adı veya tam adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c76e-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="2c76e-105">Tam adı, bir XML ad alanı öneki, iki nokta ve yerel ad oluşur.</span><span class="sxs-lookup"><span data-stu-id="2c76e-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="2c76e-106">XML ad alanı önekleri hakkında daha fazla bilgi için bkz: [XML öğesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2c76e-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2c76e-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="2c76e-107">Rules</span></span>  
 <span data-ttu-id="2c76e-108">Öğe veya öznitelik Visual Basic'te bir yerel adı aşağıdaki kurallara uyması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c76e-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="2c76e-109">Bir ad alanı ile başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c76e-109">It can begin with a namespace.</span></span> <span data-ttu-id="2c76e-110">Alfabetik bir karakter veya alt çizgi ile başlaması gerekir (`_`).</span><span class="sxs-lookup"><span data-stu-id="2c76e-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="2c76e-111">Yalnızca alfabetik karakterler, ondalık sayılar, alt çizgi, nokta (.) ve kısa çizgi içermelidir (-).</span><span class="sxs-lookup"><span data-stu-id="2c76e-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="2c76e-112">Birden fazla 1024 karakterden uzun olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c76e-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="2c76e-113">Ad alanı düzenleme adlarında görünen iki nokta üst üste gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c76e-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="2c76e-114">Bu nedenle, yalnızca belirli bir adı için bir XML ad alanı belirtmek için iki nokta üst üste kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c76e-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="2c76e-115">Ayrıca, aşağıdaki kılavuz uyması.</span><span class="sxs-lookup"><span data-stu-id="2c76e-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="2c76e-116">XML 1.0 belirtimi "xml" büyük/küçük harf Çeşitleme dize ile başlayan tüm adları ayırır.</span><span class="sxs-lookup"><span data-stu-id="2c76e-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="2c76e-117">Bu nedenle, bu öğeyi adlarını ve öznitelik adları kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="2c76e-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="2c76e-118">Ad uzunluğu yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2c76e-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="2c76e-119">Pratik geçtiğinden bağımsız, bir ad öğesi yapısını hala açık bir şekilde tanımlanırken olabildiğinde kısa olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c76e-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="2c76e-120">Bu, kodunuzun okunabilirliğini artırır ve satır uzunluğu ve kaynak dosya boyutu azaltır.</span><span class="sxs-lookup"><span data-stu-id="2c76e-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="2c76e-121">Ancak, adınızı, yeterli öğesi veya nasıl kodunuzu kullanıyorsa açıklanmaz, bu nedenle kısa olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c76e-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="2c76e-122">Bu, kodunuzu okunabilirlik için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2c76e-122">This is important for the readability of your code.</span></span> <span data-ttu-id="2c76e-123">Başkası anladığınızı çalışıyor ya da sizin, uzun süre yazdığınız sonra arıyorsanız, uygun öğe adları zamandan tasarruf edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c76e-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="2c76e-124">Adları büyük/küçük harfe duyarlılık</span><span class="sxs-lookup"><span data-stu-id="2c76e-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="2c76e-125">XML öğe adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="2c76e-125">XML element names are case sensitive.</span></span> <span data-ttu-id="2c76e-126">Bu, Visual Basic derleyici yalnızca alfabetik durumlarda farklı iki ad karşılaştırır, bunları farklı adları olarak yorumlar olduğunu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2c76e-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="2c76e-127">Örneğin, Yorumlar `ABC` ve `abc` öğeleri ayırmak için başvuran olarak.</span><span class="sxs-lookup"><span data-stu-id="2c76e-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="2c76e-128">XML ad alanları</span><span class="sxs-lookup"><span data-stu-id="2c76e-128">XML Namespaces</span></span>  
 <span data-ttu-id="2c76e-129">Bir XML öğesi değişmez değer oluştururken, öğe adı için XML ad alanı öneki belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c76e-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="2c76e-130">Daha fazla bilgi için bkz: [XML öğesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2c76e-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c76e-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c76e-131">See Also</span></span>  
 [<span data-ttu-id="2c76e-132">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="2c76e-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="2c76e-133">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="2c76e-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
