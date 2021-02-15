---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir numaralandırma üyesine başvurma (Visual Basic)'
title: 'Nasıl yapılır: Bir Numaralandırma Üyesine Başvurma'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 339ea8292eea1b39e2c6e5879b98a083800fb1fc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471532"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="5ddb2-103">Nasıl yapılır: Bir Numaralandırma Üyesine Başvurma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ddb2-103">How to: Refer to an Enumeration Member (Visual Basic)</span></span>

<span data-ttu-id="5ddb2-104">Numaralandırmalar ilgili sabitler kümesiyle çalışmak ve sabit değerleri adlarla ilişkilendirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ddb2-104">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="5ddb2-105">Örneğin, haftanın günleriyle ilişkili bir tamsayı sabitleri kümesi için bir sabit listesi belirtebilir ve ardından kodunuzda tamsayı değerleri yerine günlerin adlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ddb2-105">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="5ddb2-106">İfadesiyle tam nitelikli adlar kullanmaktan kaçınabilirsiniz `Imports` .</span><span class="sxs-lookup"><span data-stu-id="5ddb2-106">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="5ddb2-107">Daha fazla bilgi için bkz. [numaralandırmalar ve ad niteliği](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="5ddb2-107">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="5ddb2-108">Bir numaralandırma üyesine başvurmak için</span><span class="sxs-lookup"><span data-stu-id="5ddb2-108">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="5ddb2-109">Üye adını listeleme ile niteleyin.</span><span class="sxs-lookup"><span data-stu-id="5ddb2-109">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="5ddb2-110">Örneğin, aşağıdaki örnek, `Saturday` `FirstDayOfWeek` numaralandırmanın üyesini değişkenine atar `DayValue` .</span><span class="sxs-lookup"><span data-stu-id="5ddb2-110">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="5ddb2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ddb2-111">See also</span></span>

- [<span data-ttu-id="5ddb2-112">Nasıl yapılır: numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="5ddb2-112">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="5ddb2-113">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="5ddb2-113">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="5ddb2-114">Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma</span><span class="sxs-lookup"><span data-stu-id="5ddb2-114">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="5ddb2-115">Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="5ddb2-115">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="5ddb2-116">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="5ddb2-116">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
