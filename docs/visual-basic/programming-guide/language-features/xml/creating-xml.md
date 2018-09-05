---
title: Visual Basic'de XML Oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: 46f9174e78cc67c1e352d02ac6b5038f5da01086
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504675"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="896ff-102">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="896ff-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="896ff-103">Visual Basic kullanmanıza olanak sağlar *XML sabit değerleri* kodunuzda doğrudan.</span><span class="sxs-lookup"><span data-stu-id="896ff-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="896ff-104">XML değişmez sözdiziminin temsil [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri ve XML 1.0 sözdizimine benzer.</span><span class="sxs-lookup"><span data-stu-id="896ff-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="896ff-105">Bu, kodunuzu son XML aynı yapıda olduğundan XML öğeleri, belgeleri ve parçaları programlı oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="896ff-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="896ff-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="896ff-106">In This Section</span></span>  
  
|<span data-ttu-id="896ff-107">Terim</span><span class="sxs-lookup"><span data-stu-id="896ff-107">Term</span></span>|<span data-ttu-id="896ff-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="896ff-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="896ff-109">XML Değişmez Değerlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="896ff-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="896ff-110">XML değişmez değerleri ve için birbirleriyle giriş [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="896ff-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="896ff-111">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="896ff-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="896ff-112">XML değişmez değerlerine katıştırılmış ifadeler kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="896ff-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="896ff-113">Nasıl yapılır: XML Değişmez Değerleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="896ff-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="896ff-114">Bir XML öğesi değişmez değeri bir XML kullanarak kod içinde oluşturma işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="896ff-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="896ff-115">XML Değişmez Değerlerinde Boşluk</span><span class="sxs-lookup"><span data-stu-id="896ff-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="896ff-116">Visual Basic boşluk XML değişmez değerlerine nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="896ff-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="896ff-117">XML Değişmez Değerleri ve XML 1.0 Belirtimi</span><span class="sxs-lookup"><span data-stu-id="896ff-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="896ff-118">XML değişmez sözdiziminin Visual Basic'te XML 1.0 belirtimi için nasıl ilişkili olduğu açıklanır.</span><span class="sxs-lookup"><span data-stu-id="896ff-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="896ff-119">Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma</span><span class="sxs-lookup"><span data-stu-id="896ff-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="896ff-120">Katıştırılmış ifadeler XML değişmez değerlerine çalışma zamanında içerik oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="896ff-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="896ff-121">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="896ff-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="896ff-122">XML öğeleri ve özniteliklerinin adlandırma yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="896ff-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="896ff-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="896ff-123">See Also</span></span>  
 [<span data-ttu-id="896ff-124">XML</span><span class="sxs-lookup"><span data-stu-id="896ff-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
