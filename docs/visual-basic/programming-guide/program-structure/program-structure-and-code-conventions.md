---
title: Program Yapısı ve Kod Kuralları (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9980a815d83b21214f1be441d641c3da38c1b541
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="dedcf-102">Program Yapısı ve Kod Kuralları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dedcf-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="dedcf-103">Bu bölümde, tipik Visual Basic program yapısı sunar, basit bir Visual Basic program, "Hello, World" sağlar ve Visual Basic kod kuralları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="dedcf-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="dedcf-104">Kod kuralları bir programın mantığı değil, ancak kendi fiziksel yapısı ve görünümünü odaklanan önerilerdir.</span><span class="sxs-lookup"><span data-stu-id="dedcf-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="dedcf-105">Bunları aşağıdaki kodunuzu okuyun, anlamak ve bakımını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="dedcf-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="dedcf-106">Kod kuralları, diğerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="dedcf-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="dedcf-107">Etiketleme ve kod açıklama eklemek için standartlaştırılmış biçimleri.</span><span class="sxs-lookup"><span data-stu-id="dedcf-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="dedcf-108">Aralık, biçimlendirme ve kod girintileme için yönergeler.</span><span class="sxs-lookup"><span data-stu-id="dedcf-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="dedcf-109">Adlandırma kuralları nesneleri, değişkenler ve yordamlar.</span><span class="sxs-lookup"><span data-stu-id="dedcf-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="dedcf-110">Aşağıdaki konular iyi kullanım örnekleri ile birlikte Visual Basic programları için programlama kılavuzları kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dedcf-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dedcf-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dedcf-111">In This Section</span></span>  
 [<span data-ttu-id="dedcf-112">Visual Basic programının yapısı</span><span class="sxs-lookup"><span data-stu-id="dedcf-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="dedcf-113">Visual Basic program olun öğeleri genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="dedcf-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="dedcf-114">Visual Basic'de ana yordam</span><span class="sxs-lookup"><span data-stu-id="dedcf-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="dedcf-115">Başlangıç olarak hizmet etmesi işaret eden ve uygulamanız için genel denetim yordam açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dedcf-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="dedcf-116">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="dedcf-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="dedcf-117">Başvuru diğer derlemelerde nesnelerine nasıl açıklanır.</span><span class="sxs-lookup"><span data-stu-id="dedcf-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="dedcf-118">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="dedcf-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="dedcf-119">Ad alanları nesneleri derlemeler içinde nasıl düzenlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="dedcf-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="dedcf-120">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="dedcf-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="dedcf-121">Yordamlar, sabitleri, değişkenleri, bağımsız değişkenler ve nesneleri adlandırma genel yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dedcf-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="dedcf-122">Visual Basic kodlama kuralları</span><span class="sxs-lookup"><span data-stu-id="dedcf-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="dedcf-123">Bu belge örneklerinde geliştirmede kullanılan yönergeleri gözden geçirir.</span><span class="sxs-lookup"><span data-stu-id="dedcf-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="dedcf-124">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="dedcf-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="dedcf-125">Başkalarının yoksay derleyici yönlendirerek sırasında belirli kod bloklarını seçmeli derleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="dedcf-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="dedcf-126">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="dedcf-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="dedcf-127">Birden çok satıra uzun deyimleri bölme ve tek bir satırı kısa deyimleri birleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dedcf-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="dedcf-128">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme</span><span class="sxs-lookup"><span data-stu-id="dedcf-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="dedcf-129">Daraltma ve gizleme Visual Basic kod bölümlerini Kod düzenleyicisinde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dedcf-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="dedcf-130">Nasıl yapılır: Etiket Deyimleri</span><span class="sxs-lookup"><span data-stu-id="dedcf-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="dedcf-131">Bir kullanım için ifadelerle gibi tanımlamak için kod satırı işaretlemek gösterilmektedir `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="dedcf-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="dedcf-132">Code'daki Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="dedcf-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="dedcf-133">Nasıl ve nerede gösterir sayısal olmayan ve alfabetik olmayan karakterler kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="dedcf-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="dedcf-134">Code’daki Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dedcf-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="dedcf-135">Kodunuzu açıklayıcı açıklamaları ekleme konusunda anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dedcf-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="dedcf-136">Code’da Öğe Adları Olarak Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="dedcf-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="dedcf-137">Köşeli ayraçlar kullanmayı açıklar (`[]`) de Visual Basic anahtar sözcükleri değişken adları sınırlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="dedcf-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="dedcf-138">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="dedcf-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="dedcf-139">Visual Basic programının öğelerine başvurmak için çeşitli yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dedcf-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="dedcf-140">Visual Basic sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="dedcf-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="dedcf-141">Visual Basic kodlama bilinen sınırlarda kaldırılmasını açıklanır.</span><span class="sxs-lookup"><span data-stu-id="dedcf-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dedcf-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="dedcf-142">Related Sections</span></span>  
 [<span data-ttu-id="dedcf-143">Tipografi ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="dedcf-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="dedcf-144">Standart kodlama kuralları için Visual Basic sağlar.</span><span class="sxs-lookup"><span data-stu-id="dedcf-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="dedcf-145">Kod yazma</span><span class="sxs-lookup"><span data-stu-id="dedcf-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="dedcf-146">Yazma ve kodunuzu yönetmek kolaylaştırmak özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="dedcf-146">Describes features that make it easier for you to write and manage your code.</span></span>
