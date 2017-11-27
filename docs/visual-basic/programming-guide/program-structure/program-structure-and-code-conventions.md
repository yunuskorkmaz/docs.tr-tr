---
title: "Program Yapısı ve Kod Kuralları (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b38ba9623a20dcd1be4bc96f4aff1eb646b0a053
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="6447a-102">Program Yapısı ve Kod Kuralları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6447a-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="6447a-103">Bu bölüm tipik tanıtır [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program yapısı, basit bir sağlar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programı, "Hello, World" ve anlatılmaktadır [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kod kuralları.</span><span class="sxs-lookup"><span data-stu-id="6447a-103">This section introduces the typical [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program structure, provides a simple [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program, "Hello, World", and discusses [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code conventions.</span></span> <span data-ttu-id="6447a-104">Kod kuralları bir programın mantığı değil, ancak kendi fiziksel yapısı ve görünümünü odaklanan önerilerdir.</span><span class="sxs-lookup"><span data-stu-id="6447a-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="6447a-105">Bunları aşağıdaki kodunuzu okuyun, anlamak ve bakımını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6447a-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="6447a-106">Kod kuralları, diğerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="6447a-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="6447a-107">Etiketleme ve kod açıklama eklemek için standartlaştırılmış biçimleri.</span><span class="sxs-lookup"><span data-stu-id="6447a-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="6447a-108">Aralık, biçimlendirme ve kod girintileme için yönergeler.</span><span class="sxs-lookup"><span data-stu-id="6447a-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="6447a-109">Adlandırma kuralları nesneleri, değişkenler ve yordamlar.</span><span class="sxs-lookup"><span data-stu-id="6447a-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="6447a-110">Aşağıdaki konular kılavuzu için programlama kümesi sunmak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] iyi kullanım örnekleri ile birlikte programlar.</span><span class="sxs-lookup"><span data-stu-id="6447a-110">The following topics present a set of programming guidelines for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6447a-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6447a-111">In This Section</span></span>  
 [<span data-ttu-id="6447a-112">Visual Basic programının yapısı</span><span class="sxs-lookup"><span data-stu-id="6447a-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="6447a-113">Oluşturan öğelere genel bakış sağlayan bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="6447a-113">Provides an overview of the elements that make up a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 [<span data-ttu-id="6447a-114">Visual Basic'de ana yordam</span><span class="sxs-lookup"><span data-stu-id="6447a-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="6447a-115">Başlangıç olarak hizmet etmesi işaret eden ve uygulamanız için genel denetim yordam açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6447a-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="6447a-116">References ve Imports deyimi</span><span class="sxs-lookup"><span data-stu-id="6447a-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="6447a-117">Başvuru diğer derlemelerde nesnelerine nasıl açıklanır.</span><span class="sxs-lookup"><span data-stu-id="6447a-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="6447a-118">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="6447a-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="6447a-119">Ad alanları nesneleri derlemeler içinde nasıl düzenlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="6447a-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="6447a-120">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="6447a-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="6447a-121">Yordamlar, sabitleri, değişkenleri, bağımsız değişkenler ve nesneleri adlandırma genel yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6447a-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="6447a-122">Visual Basic kodlama kuralları</span><span class="sxs-lookup"><span data-stu-id="6447a-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="6447a-123">Bu belge örneklerinde geliştirmede kullanılan yönergeleri gözden geçirir.</span><span class="sxs-lookup"><span data-stu-id="6447a-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="6447a-124">Koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="6447a-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="6447a-125">Başkalarının yoksay derleyici yönlendirerek sırasında belirli kod bloklarını seçmeli derleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="6447a-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="6447a-126">Nasıl yapılır: kodda deyimleri bölme ve birleştirme</span><span class="sxs-lookup"><span data-stu-id="6447a-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="6447a-127">Birden çok satıra uzun deyimleri bölme ve tek bir satırı kısa deyimleri birleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6447a-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="6447a-128">Nasıl yapılır: daraltma ve gizleme kodun bölümlerini</span><span class="sxs-lookup"><span data-stu-id="6447a-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="6447a-129">Daraltma ve kod bölümlerini gizleme gösterilmektedir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kod Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6447a-129">Shows how to collapse and hide sections of code in the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code editor.</span></span>  
  
 [<span data-ttu-id="6447a-130">Nasıl yapılır: Etiket deyimleri</span><span class="sxs-lookup"><span data-stu-id="6447a-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="6447a-131">Bir kullanım için ifadelerle gibi tanımlamak için kod satırı işaretlemek gösterilmektedir `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="6447a-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="6447a-132">Kod'da özel karakterler</span><span class="sxs-lookup"><span data-stu-id="6447a-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="6447a-133">Nasıl ve nerede gösterir sayısal olmayan ve alfabetik olmayan karakterler kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="6447a-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="6447a-134">Kod açıklamaları</span><span class="sxs-lookup"><span data-stu-id="6447a-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="6447a-135">Kodunuzu açıklayıcı açıklamaları ekleme konusunda anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6447a-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="6447a-136">Kodda öğe adları olarak anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="6447a-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="6447a-137">Köşeli ayraçlar kullanmayı açıklar (`[]`) da değişken adları sınırlandırmak için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="6447a-137">Describes how to use brackets (`[]`) to delimit variable names that are also [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] keywords.</span></span>  
  
 [<span data-ttu-id="6447a-138">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="6447a-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="6447a-139">Öğelerine başvurmak için çeşitli yolları açıklanmaktadır bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="6447a-139">Describes various ways to refer to elements of a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 [<span data-ttu-id="6447a-140">Visual Basic sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="6447a-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="6447a-141">Bilinen kodlama sınırlarda kaldırılmasını ele [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6447a-141">Discusses the removal of known coding limits within [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6447a-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6447a-142">Related Sections</span></span>  
 [<span data-ttu-id="6447a-143">Tipografi ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="6447a-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="6447a-144">İçin standart kodlama kuralları sağlar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6447a-144">Provides standard coding conventions for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [<span data-ttu-id="6447a-145">Kod yazma</span><span class="sxs-lookup"><span data-stu-id="6447a-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="6447a-146">Yazma ve kodunuzu yönetmek kolaylaştırmak özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="6447a-146">Describes features that make it easier for you to write and manage your code.</span></span>
