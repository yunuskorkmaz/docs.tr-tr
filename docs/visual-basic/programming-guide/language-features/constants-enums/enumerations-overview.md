---
title: Numaralandırmalara Genel Bakış (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, enumerations
- enumerations [Visual Basic], about enumerations
ms.assetid: b42a38ee-5e77-4f99-a037-e3a127ead89c
ms.openlocfilehash: 1c3465a3b2d12b110096ceedf2602d6560b82f4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821848"
---
# <a name="enumerations-overview-visual-basic"></a><span data-ttu-id="77e9c-102">Numaralandırmalara Genel Bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77e9c-102">Enumerations Overview (Visual Basic)</span></span>
<span data-ttu-id="77e9c-103">Numaralandırmalar ilgili sabitlerinin kümeleri ile birlikte çalışır ve adları ile sabit değerleri ilişkilendirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="77e9c-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="77e9c-104">Örneğin, tamsayı sabitleri haftanın günleri ile ilişkilendirilmiş bir dizi için bir numaralandırmayı bildirmek ve daha sonra kodunuzda tamsayı değerleri yerine gün adlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="77e9c-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="tasks-involving-enumerations"></a><span data-ttu-id="77e9c-105">Sabit listeleri ile ilgili görevleri</span><span class="sxs-lookup"><span data-stu-id="77e9c-105">Tasks involving Enumerations</span></span>  
 <span data-ttu-id="77e9c-106">Aşağıdaki tabloda, sabit listeleri içeren ortak görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="77e9c-106">The following table lists common tasks involving enumerations.</span></span>  
  
|<span data-ttu-id="77e9c-107">Bunu yapmak için</span><span class="sxs-lookup"><span data-stu-id="77e9c-107">To do this</span></span>|<span data-ttu-id="77e9c-108">Bkz. </span><span class="sxs-lookup"><span data-stu-id="77e9c-108">See</span></span>|  
|----------------|---------|  
|<span data-ttu-id="77e9c-109">Önceden tanımlanmış bir sabit listesi Bul</span><span class="sxs-lookup"><span data-stu-id="77e9c-109">Find a pre-defined enumeration</span></span>|[<span data-ttu-id="77e9c-110">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="77e9c-110">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)|  
|<span data-ttu-id="77e9c-111">Bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="77e9c-111">Declare an enumeration</span></span>|[<span data-ttu-id="77e9c-112">Nasıl yapılır: Bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="77e9c-112">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)|  
|<span data-ttu-id="77e9c-113">Bir sabit listesinin adı tam olarak nitelemek</span><span class="sxs-lookup"><span data-stu-id="77e9c-113">Fully qualify an enumeration's name</span></span>|[<span data-ttu-id="77e9c-114">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="77e9c-114">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)|  
|<span data-ttu-id="77e9c-115">Bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="77e9c-115">Refer to an enumeration member</span></span>|[<span data-ttu-id="77e9c-116">Nasıl yapılır: Bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="77e9c-116">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)|  
|<span data-ttu-id="77e9c-117">Bir sabit listesi yoluyla yineleme</span><span class="sxs-lookup"><span data-stu-id="77e9c-117">Iterate through an enumeration</span></span>|[<span data-ttu-id="77e9c-118">Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme yapma</span><span class="sxs-lookup"><span data-stu-id="77e9c-118">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)|  
|<span data-ttu-id="77e9c-119">Bir numaralandırma ile ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="77e9c-119">Determine the string associated with an enumeration</span></span>|[<span data-ttu-id="77e9c-120">Nasıl yapılır: Bir numaralandırma değeriyle ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="77e9c-120">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)|  
|<span data-ttu-id="77e9c-121">Bir numaralandırmanın ne zaman kullanılacağı karar verin</span><span class="sxs-lookup"><span data-stu-id="77e9c-121">Decide when to use an enumeration</span></span>|[<span data-ttu-id="77e9c-122">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="77e9c-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)|  
  
## <a name="see-also"></a><span data-ttu-id="77e9c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77e9c-123">See also</span></span>

- [<span data-ttu-id="77e9c-124">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="77e9c-124">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="77e9c-125">Kullanıcı Tanımlı Sabitler</span><span class="sxs-lookup"><span data-stu-id="77e9c-125">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [<span data-ttu-id="77e9c-126">Nasıl yapılır: Bir sabit bildirme</span><span class="sxs-lookup"><span data-stu-id="77e9c-126">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [<span data-ttu-id="77e9c-127">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="77e9c-127">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="77e9c-128">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="77e9c-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
