---
title: "Giriş saf işlevsel Dönüşümleri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 535d022b68fd4d08f04648fb98f5a7a7c53ed6e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-pure-functional-transformations-c"></a><span data-ttu-id="0aac2-102">Giriş saf işlevsel Dönüşümleri (C#)</span><span class="sxs-lookup"><span data-stu-id="0aac2-102">Introduction to Pure Functional Transformations (C#)</span></span>
<span data-ttu-id="0aac2-103">Bu bölümde işlevsel dönüştürmeleri, temel kavramları dahil olmak üzere tanıtır ve destekleyici dil oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0aac2-103">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="0aac2-104">İkincisi için geçiş hakkında öneriler dahil olmak üzere programlama, nesne yönelimli ve işlev dönüştürme yaklaşımları karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="0aac2-104">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="0aac2-105">İşlev dönüştürmeleri pek çok programlama senaryolarda kullanılabilir ancak XML dönüşümü kullanılır burada somut bir örnek olarak.</span><span class="sxs-lookup"><span data-stu-id="0aac2-105">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0aac2-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0aac2-106">In This Section</span></span>  
  
|<span data-ttu-id="0aac2-107">Konu</span><span class="sxs-lookup"><span data-stu-id="0aac2-107">Topic</span></span>|<span data-ttu-id="0aac2-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0aac2-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0aac2-109">Kavramları ve terminolojiyi (işlev dönüştürme) (C#)</span><span class="sxs-lookup"><span data-stu-id="0aac2-109">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="0aac2-110">Kavramları ve terminolojiyi saf işlevsel Dönüşümlerin tanıtır.</span><span class="sxs-lookup"><span data-stu-id="0aac2-110">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="0aac2-111">İşlevsel Programlama vs. Kesinlik temelli programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="0aac2-111">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)|<span data-ttu-id="0aac2-112">Karşılaştırır ve daha geleneksel kesinlik temelli (yordamsal) programlamaya işlevsel programlama karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="0aac2-112">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="0aac2-113">Saf işlevlerini (C#) yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="0aac2-113">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)|<span data-ttu-id="0aac2-114">Saf işlevleri tanıtır ve saf ve Hanuka işlevleri ve örnekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aac2-114">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="0aac2-115">Uygulanabilirlik işlev dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="0aac2-115">Applicability of Functional Transformation (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/applicability-of-functional-transformation.md)|<span data-ttu-id="0aac2-116">İşlev dönüştürmeleri için tipik senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0aac2-116">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="0aac2-117">İşlev dönüştürme XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0aac2-117">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="0aac2-118">XML ağaçları dönüştürme işlevsel dönüşümleri bağlamında açıklar.</span><span class="sxs-lookup"><span data-stu-id="0aac2-118">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0aac2-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0aac2-119">See Also</span></span>  
 [<span data-ttu-id="0aac2-120">Saf işlevsel dönüşümleri XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0aac2-120">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
