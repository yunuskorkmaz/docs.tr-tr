---
title: "Öğretici: Düzenleme içeriği WordprocessingML belgesinde (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: bc9815f8-13d2-4f50-a4d1-b1c0d50d37b3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dca728cf48c6af6437beb43bcb6a8c8b7283d639
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2018
---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-c"></a><span data-ttu-id="d660b-102">Öğretici: Düzenleme içeriği WordprocessingML belgesinde (C#)</span><span class="sxs-lookup"><span data-stu-id="d660b-102">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>
<span data-ttu-id="d660b-103">Bu öğretici, XML ve XML belgeleri işlemek için LINQ ve işlevsel transformational yaklaşımı uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d660b-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="d660b-104">C# örnekleri sorgulamak ve Microsoft Word tarafından kaydedilen Office Açık XML WordprocessingML belgelerde bilgiyi işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d660b-104">The C# examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="d660b-105">Daha fazla bilgi için bkz: [WordprocessingML giriş](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/).</span><span class="sxs-lookup"><span data-stu-id="d660b-105">For more information, see [Introduction to WordprocessingML](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d660b-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d660b-106">In This Section</span></span>  
  
|<span data-ttu-id="d660b-107">Konu</span><span class="sxs-lookup"><span data-stu-id="d660b-107">Topic</span></span>|<span data-ttu-id="d660b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d660b-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d660b-109">Şekil WordprocessingML belgelerin (C#)</span><span class="sxs-lookup"><span data-stu-id="d660b-109">Shape of WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)|<span data-ttu-id="d660b-110">WordprocessingML belgesinin ayrıntılarını hızlı bir açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d660b-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="d660b-111">Kaynak Office Açık XML belge (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="d660b-111">Creating the Source Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)|<span data-ttu-id="d660b-112">Bu öğreticide sorgular için kaynak belge oluşturmak için adım adım yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d660b-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="d660b-113">Varsayılan paragraf stili (C#) bulma</span><span class="sxs-lookup"><span data-stu-id="d660b-113">Finding the Default Paragraph Style (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)|<span data-ttu-id="d660b-114">Bir belge için varsayılan stili adını bulmak için bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d660b-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="d660b-115">Paragrafları ve bunların stilleri (C#)</span><span class="sxs-lookup"><span data-stu-id="d660b-115">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="d660b-116">Bir belge paragraflarını koleksiyonu alır bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d660b-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="d660b-117">Paragrafları (C#) metin alma</span><span class="sxs-lookup"><span data-stu-id="d660b-117">Retrieving the Text of the Paragraphs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="d660b-118">Her paragraf metni almak için önceki sorgu artırmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d660b-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="d660b-119">Bir genişletme yöntemi (C#) kullanarak yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="d660b-119">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)|<span data-ttu-id="d660b-120">Kod bir genişletme yöntemi yeniden düzenleme'ı kullanarak basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="d660b-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="d660b-121">Saf işlevi (C#) kullanarak yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="d660b-121">Refactoring Using a Pure Function (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)|<span data-ttu-id="d660b-122">Daha fazla kod saf işlevi kullanarak yeniden düzenleme tarafından basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="d660b-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="d660b-123">Farklı bir şekli (C#) XML'de yansıtma</span><span class="sxs-lookup"><span data-stu-id="d660b-123">Projecting XML in a Different Shape (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)|<span data-ttu-id="d660b-124">Farklı bir şekli özgün belgeye daha planlanması XML'de göre bir XML dönüşümü tamamlar.</span><span class="sxs-lookup"><span data-stu-id="d660b-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="d660b-125">Metin bulma Word belgelerinde (C#)</span><span class="sxs-lookup"><span data-stu-id="d660b-125">Finding Text in Word Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-text-in-word-documents.md)|<span data-ttu-id="d660b-126">Bir belgedeki belirli bir metin dizesinde bulmak için önceki sorgularını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d660b-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="d660b-127">Ayrıntılar Office Açık XML WordprocessingML belgeleri (C#)</span><span class="sxs-lookup"><span data-stu-id="d660b-127">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="d660b-128">Office Açık XML WordprocessingML belgelerin bazı ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="d660b-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d660b-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d660b-129">See Also</span></span>  
 [<span data-ttu-id="d660b-130">Saf işlevsel dönüşümleri XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d660b-130">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)  
 [<span data-ttu-id="d660b-131">Giriş saf işlevsel Dönüşümleri (C#)</span><span class="sxs-lookup"><span data-stu-id="d660b-131">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
