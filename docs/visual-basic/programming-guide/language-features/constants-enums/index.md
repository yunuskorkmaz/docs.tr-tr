---
title: Sabitler ve Numaralandırmalar
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
ms.openlocfilehash: 858f22df26d44f47848921ee862c1d4c1ca1fc60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353979"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="b18b9-102">Visual Basic'de Sabitler ve Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b18b9-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="b18b9-103">Sabitler, değişmez bir değer yerine anlamlı adlar kullanmanın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="b18b9-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="b18b9-104">Adın gösterdiği gibi sabitler depolama değerleri, bir uygulamanın yürütülmesi boyunca sabit kalır.</span><span class="sxs-lookup"><span data-stu-id="b18b9-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="b18b9-105">Sabitleri, sayılar yerine anlamlı adlar sağlamak için kullanabilirsiniz, böylece kodunuzun daha okunabilir olmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b18b9-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="b18b9-106">Numaralandırmalar ilgili sabitler kümesiyle çalışmanın kolay bir yolunu sağlar ve sabit değerleri adlarla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="b18b9-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="b18b9-107">Örneğin, haftanın günleriyle ilişkili bir tamsayı sabitleri kümesi için bir sabit listesi belirtebilir ve ardından kodunuzda tamsayı değerleri yerine günlerin adlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b18b9-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b18b9-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b18b9-108">In This Section</span></span>  
  
|<span data-ttu-id="b18b9-109">Terim</span><span class="sxs-lookup"><span data-stu-id="b18b9-109">Term</span></span>|<span data-ttu-id="b18b9-110">Tanım</span><span class="sxs-lookup"><span data-stu-id="b18b9-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="b18b9-111">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b18b9-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="b18b9-112">Bu bölümdeki konularda sabitler ve kullanımları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b18b9-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="b18b9-113">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b18b9-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="b18b9-114">Bu bölümdeki konularda, numaralandırmalar ve kullanımları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b18b9-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="b18b9-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b18b9-115">Related Sections</span></span>  
  
|<span data-ttu-id="b18b9-116">Terim</span><span class="sxs-lookup"><span data-stu-id="b18b9-116">Term</span></span>|<span data-ttu-id="b18b9-117">Tanım</span><span class="sxs-lookup"><span data-stu-id="b18b9-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="b18b9-118">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="b18b9-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="b18b9-119">Sabitleri bildirmek için kullanılan `Const` ifadesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b18b9-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="b18b9-120">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="b18b9-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="b18b9-121">Numaralandırmalar oluşturmak için kullanılan `Enum` ifadesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b18b9-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="b18b9-122">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="b18b9-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="b18b9-123">Bu modüldeki tüm değişkenlerin açık bildirimini zorlamak için modül düzeyinde kullanılan `Option Explicit` ifadesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b18b9-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="b18b9-124">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="b18b9-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="b18b9-125">Değişkenleri bildirirken yerel tür çıkarımı kullanımını sağlayan `Option Infer` ifadesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b18b9-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="b18b9-126">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="b18b9-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="b18b9-127">Örtük veri türü dönüştürmelerini yalnızca genişletme dönüştürmelerine kısıtlayan, geç bağlamaya izin vermeyen ve `Object` bir tür ile sonuçlanan örtülü yazmaya izin vermeyen `Option Strict` ifadesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b18b9-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
