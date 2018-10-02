---
title: Giriş saf işlevsel dönüşümlere (C#)
ms.date: 07/20/2015
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
ms.openlocfilehash: f04189c5ae6fc8f6c827f983357ab0126b2c086d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030489"
---
# <a name="introduction-to-pure-functional-transformations-c"></a><span data-ttu-id="142f4-102">Giriş saf işlevsel dönüşümlere (C#)</span><span class="sxs-lookup"><span data-stu-id="142f4-102">Introduction to Pure Functional Transformations (C#)</span></span>
<span data-ttu-id="142f4-103">Bu bölümde temel kavramları dahil olmak üzere işlevsel dönüşümlere tanıtır ve destekleyici dil oluşturur.</span><span class="sxs-lookup"><span data-stu-id="142f4-103">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="142f4-104">Bunu programlama için ikinci geçiş hakkında öneriler de dahil olmak üzere, nesne yönelimli ve işlevsel dönüşümü yaklaşımları karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="142f4-104">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="142f4-105">XML dönüştürme işlevsel dönüşümlere birçok programlama senaryolarda kullanılabilir olsa da, kullanılan somut bir örnek burada.</span><span class="sxs-lookup"><span data-stu-id="142f4-105">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="142f4-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="142f4-106">In This Section</span></span>  
  
|<span data-ttu-id="142f4-107">Konu</span><span class="sxs-lookup"><span data-stu-id="142f4-107">Topic</span></span>|<span data-ttu-id="142f4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="142f4-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="142f4-109">Kavramlar ve terimler (işlevsel dönüşüm) (C#)</span><span class="sxs-lookup"><span data-stu-id="142f4-109">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="142f4-110">Saf işlevsel dönüşümlere terimleri ve kavramları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="142f4-110">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="142f4-111">İşlevsel Programlama ve Kesin programlama karşılaştırması (C#)</span><span class="sxs-lookup"><span data-stu-id="142f4-111">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)|<span data-ttu-id="142f4-112">Karşılaştırır ve işlevsel programlama daha geleneksel buyurgan (yordamsal) programlamaya karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="142f4-112">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="142f4-113">Saf işlevler halinde (C#) yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="142f4-113">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)|<span data-ttu-id="142f4-114">Saf işlevler tanıtır ve örnekleri ve saf ve Hanuka işlevlerini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="142f4-114">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="142f4-115">(C#) işlev dönüşümün uygulanabilirliği</span><span class="sxs-lookup"><span data-stu-id="142f4-115">Applicability of Functional Transformation (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/applicability-of-functional-transformation.md)|<span data-ttu-id="142f4-116">İşlevsel dönüşümlere tipik senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="142f4-116">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="142f4-117">(Visual Basic) XML işlevsel dönüşümü</span><span class="sxs-lookup"><span data-stu-id="142f4-117">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="142f4-118">XML ağaçlarını dönüştürmek işlevsel dönüşümlere bağlamında açıklar.</span><span class="sxs-lookup"><span data-stu-id="142f4-118">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="142f4-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="142f4-119">See Also</span></span>

- [<span data-ttu-id="142f4-120">Saf işlevsel dönüşümlere XML (C#)</span><span class="sxs-lookup"><span data-stu-id="142f4-120">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
