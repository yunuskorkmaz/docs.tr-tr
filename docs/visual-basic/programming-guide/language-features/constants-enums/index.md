---
title: "Visual Basic'de Sabitler ve Numaralandırmalar"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5bbba6434d8b0a5c02882d1ac858296fd8eeb346
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="fc429-102">Visual Basic'de Sabitler ve Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="fc429-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="fc429-103">Sabitler değişmez değer yerine anlamlı adlar kullanmak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="fc429-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="fc429-104">Adından da anlaşılacağı gibi bir uygulama yürütme sabit kalır değerleri sabitleri depolar.</span><span class="sxs-lookup"><span data-stu-id="fc429-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="fc429-105">Sabitler numaraları, kodunuzu daha okunabilir hale yerine anlamlı bir ad sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc429-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="fc429-106">Numaralandırmalar ilgili sabitleri kümeleriyle çalışmak ve sabit değerleri adlarıyla ilişkilendirmek için kolay bir yol sağlamak.</span><span class="sxs-lookup"><span data-stu-id="fc429-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="fc429-107">Örneğin, tamsayı sabitleri haftanın günleri ile ilişkilendirilmiş bir dizi için bir numaralandırma bildirme ve daha sonra kodunuzda tamsayı değerlerine yerine gün adlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc429-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc429-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fc429-108">In This Section</span></span>  
  
|<span data-ttu-id="fc429-109">Terim</span><span class="sxs-lookup"><span data-stu-id="fc429-109">Term</span></span>|<span data-ttu-id="fc429-110">Tanım</span><span class="sxs-lookup"><span data-stu-id="fc429-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="fc429-111">Sabitlere genel bakış</span><span class="sxs-lookup"><span data-stu-id="fc429-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="fc429-112">Bu bölümdeki konular, sabitleri ve kullanımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc429-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="fc429-113">Numaralandırmalara genel bakış</span><span class="sxs-lookup"><span data-stu-id="fc429-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="fc429-114">Bu bölümdeki konular, numaralandırmalar ve kullanımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc429-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="fc429-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="fc429-115">Related Sections</span></span>  
  
|<span data-ttu-id="fc429-116">Terim</span><span class="sxs-lookup"><span data-stu-id="fc429-116">Term</span></span>|<span data-ttu-id="fc429-117">Tanım</span><span class="sxs-lookup"><span data-stu-id="fc429-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="fc429-118">Const deyimi</span><span class="sxs-lookup"><span data-stu-id="fc429-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="fc429-119">Açıklar `Const` sabitleri bildirmek için kullanılan ifade.</span><span class="sxs-lookup"><span data-stu-id="fc429-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="fc429-120">Enum deyimi</span><span class="sxs-lookup"><span data-stu-id="fc429-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="fc429-121">Açıklar `Enum` numaralandırmalar oluşturmak için kullanılan ifade.</span><span class="sxs-lookup"><span data-stu-id="fc429-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="fc429-122">Option Explicit deyimi</span><span class="sxs-lookup"><span data-stu-id="fc429-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="fc429-123">Açıklar `Option Explicit` Modül düzeyinde bu modüldeki tüm değişkenlerin açıkça bildirilmesini zorlamak için kullanılan ifade.</span><span class="sxs-lookup"><span data-stu-id="fc429-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="fc429-124">Option Infer deyimi</span><span class="sxs-lookup"><span data-stu-id="fc429-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="fc429-125">Açıklar `Option Infer` değişkenleri bildirme içinde yerel türü çıkarımı kullanımını etkinleştirir deyimi.</span><span class="sxs-lookup"><span data-stu-id="fc429-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="fc429-126">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="fc429-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="fc429-127">Açıklar `Option Strict` yalnızca dönüşümleri için örtük veri türü dönüştürmelerini sınırlar, deyimi geç bağlama izin vermez ve örtük sonuçlanan yazmaya izin vermez bir `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="fc429-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
