---
title: XML oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: 1c720bc2aca4cec3dd10656d924cf2413fc18a2d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351731"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="65006-102">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="65006-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="65006-103">Visual Basic, *XML sabit* değerlerini doğrudan kodunuzda kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="65006-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="65006-104">XML sabit sözdizimi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri temsil eder ve XML 1,0 söz dizimine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="65006-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="65006-105">Bu, kodunuzun son XML ile aynı yapıya sahip olması nedeniyle, programlama yoluyla XML öğeleri, belgeler ve parçalar oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="65006-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="65006-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="65006-106">In This Section</span></span>  
  
|<span data-ttu-id="65006-107">Terim</span><span class="sxs-lookup"><span data-stu-id="65006-107">Term</span></span>|<span data-ttu-id="65006-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="65006-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="65006-109">XML Değişmez Değerlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="65006-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="65006-110">XML değişmez değerleri ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]birbirleriyle ilişkilerini giriş.</span><span class="sxs-lookup"><span data-stu-id="65006-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="65006-111">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="65006-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="65006-112">XML değişmez değerlerinde gömülü ifadelerin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="65006-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="65006-113">Nasıl yapılır: XML Değişmez Değerleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="65006-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="65006-114">XML sabit değeri kullanılarak kodda bir XML öğesinin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="65006-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="65006-115">XML Değişmez Değerlerinde Boşluk</span><span class="sxs-lookup"><span data-stu-id="65006-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="65006-116">Visual Basic, XML değişmez değerlerinde boşluğu nasıl ele aldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="65006-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="65006-117">XML Değişmez Değerleri ve XML 1.0 Belirtimi</span><span class="sxs-lookup"><span data-stu-id="65006-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="65006-118">Visual Basic XML değişmez sözdiziminin XML 1,0 belirtimiyle nasıl ilişkili olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="65006-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="65006-119">Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma</span><span class="sxs-lookup"><span data-stu-id="65006-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="65006-120">Çalışma zamanında içerik oluşturmak için katıştırılmış ifadelerin XML değişmez değerlerinde nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="65006-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="65006-121">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="65006-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="65006-122">XML öğelerini ve özniteliklerini adlandırmaya yönelik yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="65006-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65006-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65006-123">See also</span></span>

- [<span data-ttu-id="65006-124">XML</span><span class="sxs-lookup"><span data-stu-id="65006-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
