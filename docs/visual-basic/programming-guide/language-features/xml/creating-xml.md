---
title: Visual Basic'de XML Oluşturma
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
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 029ff0a2120809fd4637de5910adaffa60e3b8a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="38b98-102">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="38b98-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="38b98-103">Visual Basic kullanmanıza olanak sağlayan *XML değişmez değerleri* kodunuzda doğrudan.</span><span class="sxs-lookup"><span data-stu-id="38b98-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="38b98-104">XML değişmez sözdizimini temsil eden [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri ve XML 1.0 sözdizimine benzer.</span><span class="sxs-lookup"><span data-stu-id="38b98-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="38b98-105">Bu, kodunuzu son XML aynı yapısını olduğundan XML öğeleri, belgeler ve parçaları program aracılığıyla oluşturma kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="38b98-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38b98-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="38b98-106">In This Section</span></span>  
  
|<span data-ttu-id="38b98-107">Terim</span><span class="sxs-lookup"><span data-stu-id="38b98-107">Term</span></span>|<span data-ttu-id="38b98-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="38b98-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="38b98-109">XML Değişmez Değerlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="38b98-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="38b98-110">XML değişmez değerleri ve nasıl ilişkili oldukları giriş [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="38b98-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="38b98-111">XML'de Katıştırılmış İfadeler</span><span class="sxs-lookup"><span data-stu-id="38b98-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="38b98-112">XML değişmez değerlerine katıştırılmış ifadeler kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="38b98-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="38b98-113">Nasıl yapılır: XML Değişmez Değerleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="38b98-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="38b98-114">Bir XML öğesi değişmez değer XML kullanarak kod içinde oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="38b98-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="38b98-115">XML Değişmez Değerlerinde Boşluk</span><span class="sxs-lookup"><span data-stu-id="38b98-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="38b98-116">Visual Basic boşlukları XML değişmez değerlerine nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="38b98-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="38b98-117">XML Değişmez Değerleri ve XML 1.0 Belirtimi</span><span class="sxs-lookup"><span data-stu-id="38b98-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="38b98-118">XML değişmez sözdizimini Visual Basic'te XML 1.0 belirtimi ilişkilendirilme şekli açıklar.</span><span class="sxs-lookup"><span data-stu-id="38b98-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="38b98-119">Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma</span><span class="sxs-lookup"><span data-stu-id="38b98-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="38b98-120">Katıştırılmış ifadeler XML değişmez değerlerine çalışma zamanında içeriği oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="38b98-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="38b98-121">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları</span><span class="sxs-lookup"><span data-stu-id="38b98-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="38b98-122">XML öğeleri ve özniteliklerinin adlandırma yönergelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="38b98-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38b98-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38b98-123">See Also</span></span>  
 [<span data-ttu-id="38b98-124">XML</span><span class="sxs-lookup"><span data-stu-id="38b98-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
