---
title: "Numaralandırmalara Genel Bakış (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, enumerations
- enumerations [Visual Basic], about enumerations
ms.assetid: b42a38ee-5e77-4f99-a037-e3a127ead89c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d50e6bae880e5dc4dcde203708c6b07c05bb4e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="enumerations-overview-visual-basic"></a><span data-ttu-id="5e5b1-102">Numaralandırmalara Genel Bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e5b1-102">Enumerations Overview (Visual Basic)</span></span>
<span data-ttu-id="5e5b1-103">Numaralandırmalar ilgili sabitleri kümeleriyle çalışmak ve sabit değerleri adlarıyla ilişkilendirmek için kolay bir yol sağlamak.</span><span class="sxs-lookup"><span data-stu-id="5e5b1-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="5e5b1-104">Örneğin, tamsayı sabitleri haftanın günleri ile ilişkilendirilmiş bir dizi için bir numaralandırma bildirme ve daha sonra kodunuzda tamsayı değerlerine yerine gün adlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e5b1-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="tasks-involving-enumerations"></a><span data-ttu-id="5e5b1-105">Numaralandırmalar içeren görevler</span><span class="sxs-lookup"><span data-stu-id="5e5b1-105">Tasks involving Enumerations</span></span>  
 <span data-ttu-id="5e5b1-106">Aşağıdaki tabloda numaralandırmalar içeren ortak görevler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e5b1-106">The following table lists common tasks involving enumerations.</span></span>  
  
|<span data-ttu-id="5e5b1-107">Bunu yapmak için</span><span class="sxs-lookup"><span data-stu-id="5e5b1-107">To do this</span></span>|<span data-ttu-id="5e5b1-108">Bkz. </span><span class="sxs-lookup"><span data-stu-id="5e5b1-108">See</span></span>|  
|----------------|---------|  
|<span data-ttu-id="5e5b1-109">Önceden tanımlanmış bir numaralandırma Bul</span><span class="sxs-lookup"><span data-stu-id="5e5b1-109">Find a pre-defined enumeration</span></span>|[<span data-ttu-id="5e5b1-110">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="5e5b1-110">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)|  
|<span data-ttu-id="5e5b1-111">Bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="5e5b1-111">Declare an enumeration</span></span>|[<span data-ttu-id="5e5b1-112">Nasıl yapılır: bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="5e5b1-112">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)|  
|<span data-ttu-id="5e5b1-113">Bir numaralandırmanın adını tam olarak nitelemek</span><span class="sxs-lookup"><span data-stu-id="5e5b1-113">Fully qualify an enumeration's name</span></span>|[<span data-ttu-id="5e5b1-114">Numaralandırmalar ve ad niteliği</span><span class="sxs-lookup"><span data-stu-id="5e5b1-114">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)|  
|<span data-ttu-id="5e5b1-115">Bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="5e5b1-115">Refer to an enumeration member</span></span>|[<span data-ttu-id="5e5b1-116">Nasıl yapılır: bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="5e5b1-116">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)|  
|<span data-ttu-id="5e5b1-117">Bir numaralandırma yineleme</span><span class="sxs-lookup"><span data-stu-id="5e5b1-117">Iterate through an enumeration</span></span>|[<span data-ttu-id="5e5b1-118">Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme</span><span class="sxs-lookup"><span data-stu-id="5e5b1-118">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)|  
|<span data-ttu-id="5e5b1-119">Bir numaralandırma ile ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="5e5b1-119">Determine the string associated with an enumeration</span></span>|[<span data-ttu-id="5e5b1-120">Nasıl yapılır: bir numaralandırma değeriyle ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="5e5b1-120">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)|  
|<span data-ttu-id="5e5b1-121">Bir numaralandırmanın ne zaman kullanılacağı karar verin</span><span class="sxs-lookup"><span data-stu-id="5e5b1-121">Decide when to use an enumeration</span></span>|[<span data-ttu-id="5e5b1-122">Bir numaralandırmanın ne zaman kullanılacağı</span><span class="sxs-lookup"><span data-stu-id="5e5b1-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)|  
  
## <a name="see-also"></a><span data-ttu-id="5e5b1-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e5b1-123">See Also</span></span>  
 [<span data-ttu-id="5e5b1-124">Sabitlere genel bakış</span><span class="sxs-lookup"><span data-stu-id="5e5b1-124">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="5e5b1-125">Kullanıcı tanımlı sabitler</span><span class="sxs-lookup"><span data-stu-id="5e5b1-125">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [<span data-ttu-id="5e5b1-126">Nasıl yapılır: bir sabit bildirme</span><span class="sxs-lookup"><span data-stu-id="5e5b1-126">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [<span data-ttu-id="5e5b1-127">Sabit ve değişmez değerli veri türleri</span><span class="sxs-lookup"><span data-stu-id="5e5b1-127">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="5e5b1-128">Enum deyimi</span><span class="sxs-lookup"><span data-stu-id="5e5b1-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
