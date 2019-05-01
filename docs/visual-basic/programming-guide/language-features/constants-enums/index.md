---
title: Visual Basic'de Sabitler ve Numaralandırmalar
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- Visual Basic code, constants
- constants [Visual Basic]
- object libraries, Object Browser
- Visual Basic code, enumerations
- declaring constants [Visual Basic], enumerations
- naming conventions [Visual Basic], constants
- Visual Basic code, improving readability with constants
ms.assetid: c8aba36e-fa47-4a33-8b68-cb2009218270
ms.openlocfilehash: dfd9330210dd748d739cd8da2985795099beacd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907302"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="88bdf-102">Visual Basic'de Sabitler ve Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="88bdf-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="88bdf-103">Sabitler değişmez bir değer yerine anlamlı adlar bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="88bdf-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="88bdf-104">Sabitler adından da anlaşılacağı gibi bir uygulamanın yürütülmesini sabit kalması değerlerini depolar.</span><span class="sxs-lookup"><span data-stu-id="88bdf-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="88bdf-105">Sabitler, sayılar, kodunuzu daha okunabilir yapmak yerine anlamlı adlar sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88bdf-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="88bdf-106">Numaralandırmalar ilgili sabitlerinin kümeleri ile birlikte çalışır ve adları ile sabit değerleri ilişkilendirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="88bdf-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="88bdf-107">Örneğin, tamsayı sabitleri haftanın günleri ile ilişkilendirilmiş bir dizi için bir numaralandırmayı bildirmek ve daha sonra kodunuzda tamsayı değerleri yerine gün adlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="88bdf-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88bdf-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="88bdf-108">In This Section</span></span>  
  
|<span data-ttu-id="88bdf-109">Terim</span><span class="sxs-lookup"><span data-stu-id="88bdf-109">Term</span></span>|<span data-ttu-id="88bdf-110">Tanım</span><span class="sxs-lookup"><span data-stu-id="88bdf-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="88bdf-111">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="88bdf-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="88bdf-112">Bu bölümdeki konular, sabitleri ve kullanımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="88bdf-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="88bdf-113">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="88bdf-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="88bdf-114">Bu bölümdeki konular, numaralandırmalar ve kullanımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88bdf-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="88bdf-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="88bdf-115">Related Sections</span></span>  
  
|<span data-ttu-id="88bdf-116">Terim</span><span class="sxs-lookup"><span data-stu-id="88bdf-116">Term</span></span>|<span data-ttu-id="88bdf-117">Tanım</span><span class="sxs-lookup"><span data-stu-id="88bdf-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="88bdf-118">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="88bdf-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="88bdf-119">Açıklar `Const` deyimi sabitleri bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88bdf-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="88bdf-120">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="88bdf-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="88bdf-121">Açıklar `Enum` sabit listeleri oluşturmak için kullanılan ifade.</span><span class="sxs-lookup"><span data-stu-id="88bdf-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="88bdf-122">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="88bdf-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="88bdf-123">Açıklar `Option Explicit` Modül düzeyinde bu modüldeki tüm değişkenleri açık bildirimini zorlamak için kullanılan ifade.</span><span class="sxs-lookup"><span data-stu-id="88bdf-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="88bdf-124">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="88bdf-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="88bdf-125">Açıklar `Option Infer` deyimi değişkenleri bildirme içinde yerel tür çıkarımı kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="88bdf-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="88bdf-126">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="88bdf-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="88bdf-127">Açıklar `Option Strict` örtük veri türü dönüşümünü sadece genişletme dönüştürmeleri için sınırlar, deyimi geç bağlamaya izin vermez ve örtük sonuçlanan yazmaya izin vermeyen bir `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="88bdf-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
