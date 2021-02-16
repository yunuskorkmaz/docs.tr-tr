---
description: 'Daha fazla bilgi edinin: Visual Basic XML oluşturma'
title: XML oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: 9511253791720d1f45e00669b0abc41a45237f63
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431652"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="d3632-103">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3632-103">Creating XML in Visual Basic</span></span>

<span data-ttu-id="d3632-104">Visual Basic, *XML sabit* değerlerini doğrudan kodunuzda kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3632-104">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="d3632-105">XML sabit sözdizimi nesneleri temsil eder [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve xml 1,0 söz dizimine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="d3632-105">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="d3632-106">Bu, kodunuzun son XML ile aynı yapıya sahip olması nedeniyle, programlama yoluyla XML öğeleri, belgeler ve parçalar oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d3632-106">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3632-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d3632-107">In This Section</span></span>  
  
|<span data-ttu-id="d3632-108">Süre</span><span class="sxs-lookup"><span data-stu-id="d3632-108">Term</span></span>|<span data-ttu-id="d3632-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="d3632-109">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="d3632-110">XML Değişmez Değerlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d3632-110">XML Literals Overview</span></span>](xml-literals-overview.md)|<span data-ttu-id="d3632-111">XML değişmez değerleri ve ile ilişkilerini giriş [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d3632-111">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="d3632-112">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="d3632-112">Embedded Expressions in XML</span></span>](embedded-expressions-in-xml.md)|<span data-ttu-id="d3632-113">XML değişmez değerlerinde gömülü ifadelerin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3632-113">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="d3632-114">Nasıl yapılır: XML Değişmez Değerleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3632-114">How to: Create XML Literals</span></span>](how-to-create-xml-literals.md)|<span data-ttu-id="d3632-115">XML sabit değeri kullanılarak kodda bir XML öğesinin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3632-115">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="d3632-116">XML Değişmez Değerlerinde Boşluk</span><span class="sxs-lookup"><span data-stu-id="d3632-116">White Space in XML Literals</span></span>](white-space-in-xml-literals.md)|<span data-ttu-id="d3632-117">Visual Basic, XML değişmez değerlerinde boşluğu nasıl ele aldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3632-117">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="d3632-118">XML Değişmez Değerleri ve XML 1.0 Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d3632-118">XML Literals and the XML 1.0 Specification</span></span>](xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="d3632-119">Visual Basic XML değişmez sözdiziminin XML 1,0 belirtimiyle nasıl ilişkili olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3632-119">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="d3632-120">Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma</span><span class="sxs-lookup"><span data-stu-id="d3632-120">How to: Embed Expressions in XML Literals</span></span>](how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="d3632-121">Çalışma zamanında içerik oluşturmak için katıştırılmış ifadelerin XML değişmez değerlerinde nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3632-121">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="d3632-122">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="d3632-122">Names of Declared XML Elements and Attributes</span></span>](names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="d3632-123">XML öğelerini ve özniteliklerini adlandırmaya yönelik yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3632-123">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3632-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3632-124">See also</span></span>

- [<span data-ttu-id="d3632-125">XML</span><span class="sxs-lookup"><span data-stu-id="d3632-125">XML</span></span>](index.md)
