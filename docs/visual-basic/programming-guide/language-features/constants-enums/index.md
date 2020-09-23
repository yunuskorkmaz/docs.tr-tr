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
ms.openlocfilehash: aad4f8b24a43ecc51c372916b438daee72adc405
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058696"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="2cb57-102">Visual Basic'de Sabitler ve Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="2cb57-102">Constants and Enumerations in Visual Basic</span></span>

<span data-ttu-id="2cb57-103">Sabitler, değişmez bir değer yerine anlamlı adlar kullanmanın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="2cb57-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="2cb57-104">Adın gösterdiği gibi sabitler depolama değerleri, bir uygulamanın yürütülmesi boyunca sabit kalır.</span><span class="sxs-lookup"><span data-stu-id="2cb57-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="2cb57-105">Sabitleri, sayılar yerine anlamlı adlar sağlamak için kullanabilirsiniz, böylece kodunuzun daha okunabilir olmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cb57-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="2cb57-106">Numaralandırmalar ilgili sabitler kümesiyle çalışmanın kolay bir yolunu sağlar ve sabit değerleri adlarla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="2cb57-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="2cb57-107">Örneğin, haftanın günleriyle ilişkili bir tamsayı sabitleri kümesi için bir sabit listesi belirtebilir ve ardından kodunuzda tamsayı değerleri yerine günlerin adlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cb57-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2cb57-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2cb57-108">In This Section</span></span>  
  
|<span data-ttu-id="2cb57-109">Terim</span><span class="sxs-lookup"><span data-stu-id="2cb57-109">Term</span></span>|<span data-ttu-id="2cb57-110">Tanım</span><span class="sxs-lookup"><span data-stu-id="2cb57-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="2cb57-111">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2cb57-111">Constants Overview</span></span>](constants-overview.md)|<span data-ttu-id="2cb57-112">Bu bölümdeki konularda sabitler ve kullanımları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2cb57-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="2cb57-113">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2cb57-113">Enumerations Overview</span></span>](enumerations-overview.md)|<span data-ttu-id="2cb57-114">Bu bölümdeki konularda, numaralandırmalar ve kullanımları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2cb57-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="2cb57-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2cb57-115">Related Sections</span></span>  
  
|<span data-ttu-id="2cb57-116">Terim</span><span class="sxs-lookup"><span data-stu-id="2cb57-116">Term</span></span>|<span data-ttu-id="2cb57-117">Tanım</span><span class="sxs-lookup"><span data-stu-id="2cb57-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="2cb57-118">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="2cb57-118">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)|<span data-ttu-id="2cb57-119">`Const`Sabitleri bildirmek için kullanılan ifadesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2cb57-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="2cb57-120">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="2cb57-120">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)|<span data-ttu-id="2cb57-121">`Enum`Numaralandırmalar oluşturmak için kullanılan ifadesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2cb57-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="2cb57-122">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="2cb57-122">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="2cb57-123">`Option Explicit`Bu modüldeki tüm değişkenlerin açık bildirimini zorlamak için modül düzeyinde kullanılan ifadesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2cb57-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="2cb57-124">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="2cb57-124">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)|<span data-ttu-id="2cb57-125">`Option Infer`Değişkenleri bildirirken yerel tür çıkarımı kullanımını sağlayan ifadesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2cb57-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="2cb57-126">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="2cb57-126">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)|<span data-ttu-id="2cb57-127">`Option Strict`Örtük veri türü dönüştürmelerini yalnızca genişletme dönüştürmelerine kısıtlayan, geç bağlamaya izin vermeyen ve bir tür ile sonuçlanan örtülü yazmaya izin vermeyen ifadesini açıklar `Object` .</span><span class="sxs-lookup"><span data-stu-id="2cb57-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
