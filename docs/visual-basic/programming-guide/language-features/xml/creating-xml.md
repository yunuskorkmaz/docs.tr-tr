---
title: Visual Basic'de XML Oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: a9131e62ad0a4f55a88c15a8e0efa9189026eca3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615487"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="e5d84-102">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5d84-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="e5d84-103">Visual Basic kullanmanıza olanak sağlar *XML sabit değerleri* kodunuzda doğrudan.</span><span class="sxs-lookup"><span data-stu-id="e5d84-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="e5d84-104">XML değişmez sözdiziminin temsil [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri ve XML 1.0 sözdizimine benzer.</span><span class="sxs-lookup"><span data-stu-id="e5d84-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="e5d84-105">Bu, kodunuzu son XML aynı yapıda olduğundan XML öğeleri, belgeleri ve parçaları programlı oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e5d84-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5d84-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e5d84-106">In This Section</span></span>  
  
|<span data-ttu-id="e5d84-107">Terim</span><span class="sxs-lookup"><span data-stu-id="e5d84-107">Term</span></span>|<span data-ttu-id="e5d84-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="e5d84-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="e5d84-109">XML Değişmez Değerlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e5d84-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="e5d84-110">XML değişmez değerleri ve için birbirleriyle giriş [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5d84-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="e5d84-111">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="e5d84-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="e5d84-112">XML değişmez değerlerine katıştırılmış ifadeler kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5d84-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="e5d84-113">Nasıl yapılır: XML değişmez değerleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5d84-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="e5d84-114">Bir XML öğesi değişmez değeri bir XML kullanarak kod içinde oluşturma işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5d84-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="e5d84-115">XML Değişmez Değerlerinde Boşluk</span><span class="sxs-lookup"><span data-stu-id="e5d84-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="e5d84-116">Visual Basic boşluk XML değişmez değerlerine nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5d84-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="e5d84-117">XML Değişmez Değerleri ve XML 1.0 Belirtimi</span><span class="sxs-lookup"><span data-stu-id="e5d84-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="e5d84-118">XML değişmez sözdiziminin Visual Basic'te XML 1.0 belirtimi için nasıl ilişkili olduğu açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e5d84-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="e5d84-119">Nasıl yapılır: XML değişmez değerlerine ifade katıştırma</span><span class="sxs-lookup"><span data-stu-id="e5d84-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="e5d84-120">Katıştırılmış ifadeler XML değişmez değerlerine çalışma zamanında içerik oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5d84-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="e5d84-121">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="e5d84-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="e5d84-122">XML öğeleri ve özniteliklerinin adlandırma yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5d84-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5d84-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5d84-123">See also</span></span>
- [<span data-ttu-id="e5d84-124">XML</span><span class="sxs-lookup"><span data-stu-id="e5d84-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
