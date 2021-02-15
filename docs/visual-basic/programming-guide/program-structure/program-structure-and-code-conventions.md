---
description: 'Hakkında daha fazla bilgi edinin: program yapısı ve kod kuralları (Visual Basic)'
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
ms.openlocfilehash: 7d4202ead0550cf54a80eac89c4a4274a22d0315
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468492"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="e1aab-103">Program Yapısı ve Kod Kuralları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1aab-103">Program Structure and Code Conventions (Visual Basic)</span></span>

<span data-ttu-id="e1aab-104">Bu bölüm, tipik Visual Basic program yapısını tanıtır, "Hello, World" basit bir Visual Basic programı sağlar ve Visual Basic kod kurallarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-104">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="e1aab-105">Kod kuralları, bir programın mantığı üzerinde değil, fiziksel yapısı ve görünümünde odaklanılmış önerilerdir.</span><span class="sxs-lookup"><span data-stu-id="e1aab-105">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="e1aab-106">Bunlar, kodunuzun okunmasını, anlaşılmasını ve bakımını daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e1aab-106">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="e1aab-107">Kod kuralları, diğerleri arasında şunlar olabilir:</span><span class="sxs-lookup"><span data-stu-id="e1aab-107">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="e1aab-108">Kodu etiketlemek ve açıklama eklemek için standartlaştırılmış biçimler.</span><span class="sxs-lookup"><span data-stu-id="e1aab-108">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="e1aab-109">Aralık, biçimlendirme ve girintileme kodu için yönergeler.</span><span class="sxs-lookup"><span data-stu-id="e1aab-109">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="e1aab-110">Nesneler, değişkenler ve yordamlar için adlandırma kuralları.</span><span class="sxs-lookup"><span data-stu-id="e1aab-110">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="e1aab-111">Aşağıdaki konular, Visual Basic programlar için, iyi kullanım örnekleri ile birlikte bir dizi Programlama Kılavuzu sunar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-111">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1aab-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e1aab-112">In This Section</span></span>  

 [<span data-ttu-id="e1aab-113">Bir Visual Basic Programının Yapısı</span><span class="sxs-lookup"><span data-stu-id="e1aab-113">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="e1aab-114">Visual Basic programını oluşturan öğelere genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-114">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="e1aab-115">Visual Basic'de Ana Yordam</span><span class="sxs-lookup"><span data-stu-id="e1aab-115">Main Procedure in Visual Basic</span></span>](main-procedure.md)  
 <span data-ttu-id="e1aab-116">Uygulamanız için başlangıç noktası ve genel denetim görevi gören yordamı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-116">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="e1aab-117">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="e1aab-117">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)  
 <span data-ttu-id="e1aab-118">Diğer derlemelerdeki nesnelere nasıl başvurulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-118">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="e1aab-119">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="e1aab-119">Namespaces in Visual Basic</span></span>](namespaces.md)  
 <span data-ttu-id="e1aab-120">Ad alanlarının derlemelerin içindeki nesneleri nasıl düzenlei açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-120">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="e1aab-121">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="e1aab-121">Visual Basic Naming Conventions</span></span>](naming-conventions.md)  
 <span data-ttu-id="e1aab-122">, Adlandırma yordamları, sabitler, değişkenler, bağımsız değişkenler ve nesneler için genel yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e1aab-122">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="e1aab-123">Visual Basic Kodlama Kuralları</span><span class="sxs-lookup"><span data-stu-id="e1aab-123">Visual Basic Coding Conventions</span></span>](coding-conventions.md)  
 <span data-ttu-id="e1aab-124">Bu belgelerde örnek geliştirme konusunda kullanılan yönergeleri inceler.</span><span class="sxs-lookup"><span data-stu-id="e1aab-124">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="e1aab-125">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="e1aab-125">Conditional Compilation</span></span>](conditional-compilation.md)  
 <span data-ttu-id="e1aab-126">Derleyiciyi diğerlerini yoksayacak şekilde yönlendirirken belirli kod bloklarının seçmeli olarak nasıl derlendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-126">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="e1aab-127">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="e1aab-127">How to: Break and Combine Statements in Code</span></span>](how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="e1aab-128">Uzun deyimlerin birden çok satıra nasıl bölüneceği ve kısa deyimlerin tek bir satırda nasıl birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1aab-128">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="e1aab-129">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme</span><span class="sxs-lookup"><span data-stu-id="e1aab-129">How to: Collapse and Hide Sections of Code</span></span>](how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="e1aab-130">Visual Basic kod düzenleyicisinde kodun bölümlerini daraltma ve gizleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1aab-130">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="e1aab-131">Nasıl yapılır: Etiket Deyimleri</span><span class="sxs-lookup"><span data-stu-id="e1aab-131">How to: Label Statements</span></span>](how-to-label-statements.md)  
 <span data-ttu-id="e1aab-132">Bir kod satırını, gibi deyimlerle kullanılmak üzere tanımlamak için nasıl işaretleneceğini gösterir `On Error Goto` .</span><span class="sxs-lookup"><span data-stu-id="e1aab-132">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="e1aab-133">Koddaki Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="e1aab-133">Special Characters in Code</span></span>](special-characters-in-code.md)  
 <span data-ttu-id="e1aab-134">Sayısal olmayan ve alfabetik olmayan karakterlerin nasıl ve nerede kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1aab-134">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="e1aab-135">Kod Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="e1aab-135">Comments in Code</span></span>](comments-in-code.md)  
 <span data-ttu-id="e1aab-136">Kodunuza açıklayıcı yorumların nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-136">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="e1aab-137">Code’da Öğe Adları Olarak Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e1aab-137">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)  
 <span data-ttu-id="e1aab-138">`[]`Anahtar sözcükleri de Visual Basic değişken adlarını sınırlandırmak için köşeli ayraçların () nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-138">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="e1aab-139">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="e1aab-139">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)  
 <span data-ttu-id="e1aab-140">Visual Basic programın öğelerine başvurmak için çeşitli yollar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e1aab-140">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="e1aab-141">Visual Basic Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="e1aab-141">Visual Basic Limitations</span></span>](limitations.md)  
 <span data-ttu-id="e1aab-142">Visual Basic içinde bilinen kodlama sınırlarının kaldırılmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-142">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e1aab-143">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e1aab-143">Related Sections</span></span>  

 [<span data-ttu-id="e1aab-144">Tipografi ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="e1aab-144">Typographic and Code Conventions</span></span>](../../language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="e1aab-145">Visual Basic için standart kodlama kuralları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-145">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="e1aab-146">Kod yazma</span><span class="sxs-lookup"><span data-stu-id="e1aab-146">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="e1aab-147">Kodunuzu yazmanızı ve yönetmenizi kolaylaştıran özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e1aab-147">Describes features that make it easier for you to write and manage your code.</span></span>
