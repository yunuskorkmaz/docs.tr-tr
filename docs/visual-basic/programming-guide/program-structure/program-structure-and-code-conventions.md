---
title: Program Yapısı ve Kod Kuralları
ms.date: 07/20/2015
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
ms.openlocfilehash: bacd532361de18936bac96c631f7f7247246b1de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347292"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="f0c42-102">Program Yapısı ve Kod Kuralları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0c42-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="f0c42-103">Bu bölüm, tipik Visual Basic program yapısını tanıtır, "Hello, World" basit bir Visual Basic programı sağlar ve Visual Basic kod kurallarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="f0c42-104">Kod kuralları, bir programın mantığı üzerinde değil, fiziksel yapısı ve görünümünde odaklanılmış önerilerdir.</span><span class="sxs-lookup"><span data-stu-id="f0c42-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="f0c42-105">Bunlar, kodunuzun okunmasını, anlaşılmasını ve bakımını daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f0c42-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="f0c42-106">Kod kuralları, diğerleri arasında şunlar olabilir:</span><span class="sxs-lookup"><span data-stu-id="f0c42-106">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="f0c42-107">Kodu etiketlemek ve açıklama eklemek için standartlaştırılmış biçimler.</span><span class="sxs-lookup"><span data-stu-id="f0c42-107">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="f0c42-108">Aralık, biçimlendirme ve girintileme kodu için yönergeler.</span><span class="sxs-lookup"><span data-stu-id="f0c42-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="f0c42-109">Nesneler, değişkenler ve yordamlar için adlandırma kuralları.</span><span class="sxs-lookup"><span data-stu-id="f0c42-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="f0c42-110">Aşağıdaki konular, Visual Basic programlar için, iyi kullanım örnekleri ile birlikte bir dizi Programlama Kılavuzu sunar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f0c42-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f0c42-111">In This Section</span></span>  
 [<span data-ttu-id="f0c42-112">Visual Basic programın yapısı</span><span class="sxs-lookup"><span data-stu-id="f0c42-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="f0c42-113">Visual Basic programını oluşturan öğelere genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="f0c42-114">Visual Basic ana yordam</span><span class="sxs-lookup"><span data-stu-id="f0c42-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="f0c42-115">Uygulamanız için başlangıç noktası ve genel denetim görevi gören yordamı açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="f0c42-116">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="f0c42-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="f0c42-117">Diğer derlemelerdeki nesnelere nasıl başvurulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="f0c42-118">Visual Basic ad alanları</span><span class="sxs-lookup"><span data-stu-id="f0c42-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="f0c42-119">Ad alanlarının derlemelerin içindeki nesneleri nasıl düzenlei açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="f0c42-120">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="f0c42-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="f0c42-121">, Adlandırma yordamları, sabitler, değişkenler, bağımsız değişkenler ve nesneler için genel yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f0c42-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="f0c42-122">Visual Basic kodlama kuralları</span><span class="sxs-lookup"><span data-stu-id="f0c42-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="f0c42-123">Bu belgelerde örnek geliştirme konusunda kullanılan yönergeleri inceler.</span><span class="sxs-lookup"><span data-stu-id="f0c42-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="f0c42-124">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="f0c42-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="f0c42-125">Derleyiciyi diğerlerini yoksayacak şekilde yönlendirirken belirli kod bloklarının seçmeli olarak nasıl derlendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="f0c42-126">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="f0c42-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="f0c42-127">Uzun deyimlerin birden çok satıra nasıl bölüneceği ve kısa deyimlerin tek bir satırda nasıl birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0c42-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="f0c42-128">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme</span><span class="sxs-lookup"><span data-stu-id="f0c42-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="f0c42-129">Visual Basic kod düzenleyicisinde kodun bölümlerini daraltma ve gizleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0c42-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="f0c42-130">Nasıl yapılır: Etiket Deyimleri</span><span class="sxs-lookup"><span data-stu-id="f0c42-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="f0c42-131">`On Error Goto`gibi deyimlerle kullanılmak üzere tanımlamak için bir kod satırının nasıl işaretleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0c42-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="f0c42-132">Code'daki Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="f0c42-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="f0c42-133">Sayısal olmayan ve alfabetik olmayan karakterlerin nasıl ve nerede kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0c42-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="f0c42-134">Kod Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="f0c42-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="f0c42-135">Kodunuza açıklayıcı yorumların nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="f0c42-136">Code’da Öğe Adları Olarak Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f0c42-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="f0c42-137">Anahtar sözcükleri de Visual Basic değişken adlarını sınırlandırmak için köşeli ayraçların (`[]`) nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="f0c42-138">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="f0c42-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="f0c42-139">Visual Basic programın öğelerine başvurmak için çeşitli yollar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0c42-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="f0c42-140">Visual Basic sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="f0c42-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="f0c42-141">Visual Basic içinde bilinen kodlama sınırlarının kaldırılmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f0c42-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f0c42-142">Related Sections</span></span>  
 [<span data-ttu-id="f0c42-143">Tipografi ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="f0c42-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="f0c42-144">Visual Basic için standart kodlama kuralları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="f0c42-145">Kod Yazma</span><span class="sxs-lookup"><span data-stu-id="f0c42-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="f0c42-146">Kodunuzu yazmanızı ve yönetmenizi kolaylaştıran özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0c42-146">Describes features that make it easier for you to write and manage your code.</span></span>
