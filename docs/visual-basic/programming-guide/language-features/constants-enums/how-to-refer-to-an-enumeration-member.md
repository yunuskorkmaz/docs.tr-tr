---
title: 'Nasıl yapılır: Bir Numaralandırma Üyesine Başvurma'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 66c527bd4ba4721065de8fca8534fe652d0139be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414420"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="3feb7-102">Nasıl yapılır: Bir Numaralandırma Üyesine Başvurma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3feb7-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="3feb7-103">Numaralandırmalar ilgili sabitler kümesiyle çalışmak ve sabit değerleri adlarla ilişkilendirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3feb7-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="3feb7-104">Örneğin, haftanın günleriyle ilişkili bir tamsayı sabitleri kümesi için bir sabit listesi belirtebilir ve ardından kodunuzda tamsayı değerleri yerine günlerin adlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3feb7-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="3feb7-105">İfadesiyle tam nitelikli adlar kullanmaktan kaçınabilirsiniz `Imports` .</span><span class="sxs-lookup"><span data-stu-id="3feb7-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="3feb7-106">Daha fazla bilgi için bkz. [numaralandırmalar ve ad niteliği](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="3feb7-106">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="3feb7-107">Bir numaralandırma üyesine başvurmak için</span><span class="sxs-lookup"><span data-stu-id="3feb7-107">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="3feb7-108">Üye adını listeleme ile niteleyin.</span><span class="sxs-lookup"><span data-stu-id="3feb7-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="3feb7-109">Örneğin, aşağıdaki örnek, `Saturday` `FirstDayOfWeek` numaralandırmanın üyesini değişkenine atar `DayValue` .</span><span class="sxs-lookup"><span data-stu-id="3feb7-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="3feb7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3feb7-110">See also</span></span>

- [<span data-ttu-id="3feb7-111">Nasıl yapılır: numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="3feb7-111">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="3feb7-112">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="3feb7-112">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="3feb7-113">Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma</span><span class="sxs-lookup"><span data-stu-id="3feb7-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="3feb7-114">Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="3feb7-114">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="3feb7-115">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="3feb7-115">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
