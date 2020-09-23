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
ms.openlocfilehash: ee61c676f3ff554267f6659453ec55e45df69aee
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072125"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="e1d7c-102">Program Yapısı ve Kod Kuralları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1d7c-102">Program Structure and Code Conventions (Visual Basic)</span></span>

<span data-ttu-id="e1d7c-103">Bu bölüm, tipik Visual Basic program yapısını tanıtır, "Hello, World" basit bir Visual Basic programı sağlar ve Visual Basic kod kurallarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="e1d7c-104">Kod kuralları, bir programın mantığı üzerinde değil, fiziksel yapısı ve görünümünde odaklanılmış önerilerdir.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="e1d7c-105">Bunlar, kodunuzun okunmasını, anlaşılmasını ve bakımını daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="e1d7c-106">Kod kuralları, diğerleri arasında şunlar olabilir:</span><span class="sxs-lookup"><span data-stu-id="e1d7c-106">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="e1d7c-107">Kodu etiketlemek ve açıklama eklemek için standartlaştırılmış biçimler.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-107">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="e1d7c-108">Aralık, biçimlendirme ve girintileme kodu için yönergeler.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="e1d7c-109">Nesneler, değişkenler ve yordamlar için adlandırma kuralları.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="e1d7c-110">Aşağıdaki konular, Visual Basic programlar için, iyi kullanım örnekleri ile birlikte bir dizi Programlama Kılavuzu sunar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1d7c-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e1d7c-111">In This Section</span></span>  

 [<span data-ttu-id="e1d7c-112">Bir Visual Basic Programının Yapısı</span><span class="sxs-lookup"><span data-stu-id="e1d7c-112">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="e1d7c-113">Visual Basic programını oluşturan öğelere genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="e1d7c-114">Visual Basic'de Ana Yordam</span><span class="sxs-lookup"><span data-stu-id="e1d7c-114">Main Procedure in Visual Basic</span></span>](main-procedure.md)  
 <span data-ttu-id="e1d7c-115">Uygulamanız için başlangıç noktası ve genel denetim görevi gören yordamı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="e1d7c-116">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="e1d7c-116">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)  
 <span data-ttu-id="e1d7c-117">Diğer derlemelerdeki nesnelere nasıl başvurulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="e1d7c-118">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="e1d7c-118">Namespaces in Visual Basic</span></span>](namespaces.md)  
 <span data-ttu-id="e1d7c-119">Ad alanlarının derlemelerin içindeki nesneleri nasıl düzenlei açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="e1d7c-120">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="e1d7c-120">Visual Basic Naming Conventions</span></span>](naming-conventions.md)  
 <span data-ttu-id="e1d7c-121">, Adlandırma yordamları, sabitler, değişkenler, bağımsız değişkenler ve nesneler için genel yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="e1d7c-122">Visual Basic Kodlama Kuralları</span><span class="sxs-lookup"><span data-stu-id="e1d7c-122">Visual Basic Coding Conventions</span></span>](coding-conventions.md)  
 <span data-ttu-id="e1d7c-123">Bu belgelerde örnek geliştirme konusunda kullanılan yönergeleri inceler.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="e1d7c-124">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="e1d7c-124">Conditional Compilation</span></span>](conditional-compilation.md)  
 <span data-ttu-id="e1d7c-125">Derleyiciyi diğerlerini yoksayacak şekilde yönlendirirken belirli kod bloklarının seçmeli olarak nasıl derlendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="e1d7c-126">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="e1d7c-126">How to: Break and Combine Statements in Code</span></span>](how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="e1d7c-127">Uzun deyimlerin birden çok satıra nasıl bölüneceği ve kısa deyimlerin tek bir satırda nasıl birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="e1d7c-128">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme</span><span class="sxs-lookup"><span data-stu-id="e1d7c-128">How to: Collapse and Hide Sections of Code</span></span>](how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="e1d7c-129">Visual Basic kod düzenleyicisinde kodun bölümlerini daraltma ve gizleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="e1d7c-130">Nasıl yapılır: Etiket Deyimleri</span><span class="sxs-lookup"><span data-stu-id="e1d7c-130">How to: Label Statements</span></span>](how-to-label-statements.md)  
 <span data-ttu-id="e1d7c-131">Bir kod satırını, gibi deyimlerle kullanılmak üzere tanımlamak için nasıl işaretleneceğini gösterir `On Error Goto` .</span><span class="sxs-lookup"><span data-stu-id="e1d7c-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="e1d7c-132">Koddaki Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="e1d7c-132">Special Characters in Code</span></span>](special-characters-in-code.md)  
 <span data-ttu-id="e1d7c-133">Sayısal olmayan ve alfabetik olmayan karakterlerin nasıl ve nerede kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="e1d7c-134">Kod Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="e1d7c-134">Comments in Code</span></span>](comments-in-code.md)  
 <span data-ttu-id="e1d7c-135">Kodunuza açıklayıcı yorumların nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="e1d7c-136">Code’da Öğe Adları Olarak Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e1d7c-136">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)  
 <span data-ttu-id="e1d7c-137">`[]`Anahtar sözcükleri de Visual Basic değişken adlarını sınırlandırmak için köşeli ayraçların () nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="e1d7c-138">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="e1d7c-138">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)  
 <span data-ttu-id="e1d7c-139">Visual Basic programın öğelerine başvurmak için çeşitli yollar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="e1d7c-140">Visual Basic Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="e1d7c-140">Visual Basic Limitations</span></span>](limitations.md)  
 <span data-ttu-id="e1d7c-141">Visual Basic içinde bilinen kodlama sınırlarının kaldırılmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e1d7c-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e1d7c-142">Related Sections</span></span>  

 [<span data-ttu-id="e1d7c-143">Tipografi ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="e1d7c-143">Typographic and Code Conventions</span></span>](../../language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="e1d7c-144">Visual Basic için standart kodlama kuralları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="e1d7c-145">Kod yazma</span><span class="sxs-lookup"><span data-stu-id="e1d7c-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="e1d7c-146">Kodunuzu yazmanızı ve yönetmenizi kolaylaştıran özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1d7c-146">Describes features that make it easier for you to write and manage your code.</span></span>
