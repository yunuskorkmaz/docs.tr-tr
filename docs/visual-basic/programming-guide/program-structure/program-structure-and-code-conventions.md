---
title: Program Yapısı ve Kod Kuralları (Visual Basic)
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
ms.openlocfilehash: b79e339ebe81a7228a02837e5c0c23c80a8132e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916948"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="f19d0-102">Program Yapısı ve Kod Kuralları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f19d0-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="f19d0-103">Bu bölümde tipik Visual Basic program yapısı sunar, basit bir Visual Basic program, "Hello, World" sağlar ve Visual Basic kod kurallarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f19d0-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="f19d0-104">Kod kuralları bir programın mantığı değil, ancak fiziksel yapısı ve görünüm odaklanan önerilerdir.</span><span class="sxs-lookup"><span data-stu-id="f19d0-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="f19d0-105">Bunların izlenmesi kodunuzun okuyun, anlamak ve bakımını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f19d0-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="f19d0-106">Kod kuralları, diğerlerinin yanı sıra şunları içerebilir:</span><span class="sxs-lookup"><span data-stu-id="f19d0-106">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="f19d0-107">Etiketleme ve açıklama kodu için standart biçimler.</span><span class="sxs-lookup"><span data-stu-id="f19d0-107">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="f19d0-108">Aralık, biçimlendirme ve girintileme kodu yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="f19d0-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="f19d0-109">Nesneler, değişkenler ve yordamlar için adlandırma kuralları.</span><span class="sxs-lookup"><span data-stu-id="f19d0-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="f19d0-110">Aşağıdaki konular, iyi kullanım örneklerinin yanı sıra Visual Basic programları için programlama yönergeleri kümesi sunar.</span><span class="sxs-lookup"><span data-stu-id="f19d0-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f19d0-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f19d0-111">In This Section</span></span>  
 [<span data-ttu-id="f19d0-112">Visual Basic programının yapısı</span><span class="sxs-lookup"><span data-stu-id="f19d0-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="f19d0-113">Visual Basic program öğeleri'ne genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f19d0-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="f19d0-114">Visual Basic'de ana yordam</span><span class="sxs-lookup"><span data-stu-id="f19d0-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="f19d0-115">Başlangıç olarak görev yapar ve uygulamanız için genel denetim yordamı açıklar.</span><span class="sxs-lookup"><span data-stu-id="f19d0-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="f19d0-116">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="f19d0-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="f19d0-117">Diğer derlemelerde nesnelere başvuru anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f19d0-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="f19d0-118">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="f19d0-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="f19d0-119">Ad alanları nesneleri derlemeler içinde nasıl düzenlediğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f19d0-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="f19d0-120">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="f19d0-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="f19d0-121">Yordamları, sabitleri, değişkenleri, bağımsız değişkenleri ve nesneleri adlandırmak için genel yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f19d0-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="f19d0-122">Visual Basic kodlama kuralları</span><span class="sxs-lookup"><span data-stu-id="f19d0-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="f19d0-123">Bu belgede örnek oluşturmak için kullanılan kılavuzları gözden geçirir.</span><span class="sxs-lookup"><span data-stu-id="f19d0-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="f19d0-124">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="f19d0-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="f19d0-125">Derleyici, diğerlerini yoksayması için yönlendirirken belirli kod bloklarının seçmeli olarak derlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="f19d0-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="f19d0-126">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="f19d0-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="f19d0-127">Uzun deyimlerin birkaç satıra bölebilir ve kısa deyimlerin bir satır birleştirme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f19d0-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="f19d0-128">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme</span><span class="sxs-lookup"><span data-stu-id="f19d0-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="f19d0-129">Daraltma ve gizleme Visual Basic kod bölümlerini Kod Düzenleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f19d0-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="f19d0-130">Nasıl yapılır: Etiket Deyimleri</span><span class="sxs-lookup"><span data-stu-id="f19d0-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="f19d0-131">Bir kullanım için ifadelerle gibi tanımlamak için kod satırı olarak işaretlemek gösterilmektedir `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="f19d0-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="f19d0-132">Code'daki Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="f19d0-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="f19d0-133">Nasıl ve nerede gösterir sayısal olmayan ve alfabetik olmayan karakterler kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="f19d0-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="f19d0-134">Code’daki Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f19d0-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="f19d0-135">Kodunuza nasıl açıklayıcı yorumlar ekleme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f19d0-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="f19d0-136">Code’da Öğe Adları Olarak Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f19d0-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="f19d0-137">Köşeli ayraçlar kullanılmasını açıklar (`[]`) Visual Basic anahtar sözcükleri olan değişken adlarının sınırlandırılması için.</span><span class="sxs-lookup"><span data-stu-id="f19d0-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="f19d0-138">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="f19d0-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="f19d0-139">Bir Visual Basic programının öğelerine başvurmaya yarayan çeşitli yolları açıklar.</span><span class="sxs-lookup"><span data-stu-id="f19d0-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="f19d0-140">Visual Basic sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="f19d0-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="f19d0-141">Visual Basic dahilindeki bilindik kodlama sınırlarının kaldırılmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f19d0-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f19d0-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f19d0-142">Related Sections</span></span>  
 [<span data-ttu-id="f19d0-143">Tipografi ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="f19d0-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="f19d0-144">Visual Basic için standart kodlama kuralları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f19d0-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="f19d0-145">Kod Yazma</span><span class="sxs-lookup"><span data-stu-id="f19d0-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="f19d0-146">Yazmak ve kodunuzu yönetmenizi kolaylaştıran özellikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f19d0-146">Describes features that make it easier for you to write and manage your code.</span></span>
