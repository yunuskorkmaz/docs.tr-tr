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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646398"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="45b92-102">Visual Basic'de Sabitler ve Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="45b92-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="45b92-103">Sabitler değişmez değer yerine anlamlı adlar kullanmak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="45b92-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="45b92-104">Adından da anlaşılacağı gibi bir uygulama yürütme sabit kalır değerleri sabitleri depolar.</span><span class="sxs-lookup"><span data-stu-id="45b92-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="45b92-105">Sabitler numaraları, kodunuzu daha okunabilir hale yerine anlamlı bir ad sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45b92-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="45b92-106">Numaralandırmalar ilgili sabitleri kümeleriyle çalışmak ve sabit değerleri adlarıyla ilişkilendirmek için kolay bir yol sağlamak.</span><span class="sxs-lookup"><span data-stu-id="45b92-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="45b92-107">Örneğin, tamsayı sabitleri haftanın günleri ile ilişkilendirilmiş bir dizi için bir numaralandırma bildirme ve daha sonra kodunuzda tamsayı değerlerine yerine gün adlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="45b92-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45b92-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="45b92-108">In This Section</span></span>  
  
|<span data-ttu-id="45b92-109">Terim</span><span class="sxs-lookup"><span data-stu-id="45b92-109">Term</span></span>|<span data-ttu-id="45b92-110">Tanım</span><span class="sxs-lookup"><span data-stu-id="45b92-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="45b92-111">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="45b92-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="45b92-112">Bu bölümdeki konular, sabitleri ve kullanımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45b92-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="45b92-113">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="45b92-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="45b92-114">Bu bölümdeki konular, numaralandırmalar ve kullanımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45b92-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="45b92-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="45b92-115">Related Sections</span></span>  
  
|<span data-ttu-id="45b92-116">Terim</span><span class="sxs-lookup"><span data-stu-id="45b92-116">Term</span></span>|<span data-ttu-id="45b92-117">Tanım</span><span class="sxs-lookup"><span data-stu-id="45b92-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="45b92-118">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="45b92-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="45b92-119">Açıklar `Const` sabitleri bildirmek için kullanılan ifade.</span><span class="sxs-lookup"><span data-stu-id="45b92-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="45b92-120">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="45b92-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="45b92-121">Açıklar `Enum` numaralandırmalar oluşturmak için kullanılan ifade.</span><span class="sxs-lookup"><span data-stu-id="45b92-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="45b92-122">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="45b92-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="45b92-123">Açıklar `Option Explicit` Modül düzeyinde bu modüldeki tüm değişkenlerin açıkça bildirilmesini zorlamak için kullanılan ifade.</span><span class="sxs-lookup"><span data-stu-id="45b92-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="45b92-124">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="45b92-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="45b92-125">Açıklar `Option Infer` değişkenleri bildirme içinde yerel türü çıkarımı kullanımını etkinleştirir deyimi.</span><span class="sxs-lookup"><span data-stu-id="45b92-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="45b92-126">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="45b92-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="45b92-127">Açıklar `Option Strict` yalnızca dönüşümleri için örtük veri türü dönüştürmelerini sınırlar, deyimi geç bağlama izin vermez ve örtük sonuçlanan yazmaya izin vermez bir `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="45b92-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
