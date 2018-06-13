---
title: 'Nasıl yapılır: Bir Numaralandırma Üyesine Başvurma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: f995a0ef69c503360a5d709551a7f0ccfd67ce40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646329"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="8483c-102">Nasıl yapılır: Bir Numaralandırma Üyesine Başvurma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8483c-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="8483c-103">Numaralandırmalar ilgili sabitleri kümeleriyle çalışmak ve sabit değerleri adlarıyla ilişkilendirmek için kolay bir yol sağlamak.</span><span class="sxs-lookup"><span data-stu-id="8483c-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="8483c-104">Örneğin, tamsayı sabitleri haftanın günleri ile ilişkilendirilmiş bir dizi için bir numaralandırma bildirme ve daha sonra kodunuzda tamsayı değerlerine yerine gün adlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8483c-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="8483c-105">İle tam olarak nitelenmiş adlar kullanmaktan kaçınabilirsiniz `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8483c-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="8483c-106">Daha fazla bilgi için bkz: [numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="8483c-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="8483c-107">Bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="8483c-107">To refer to an enumeration member</span></span>  
  
-   <span data-ttu-id="8483c-108">Numaralandırma üyesi adıyla hakkını kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="8483c-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="8483c-109">Örneğin, aşağıdaki örnekte atar `Saturday` üyesi `FirstDayOfWeek` değişkenine numaralandırma `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="8483c-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8483c-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8483c-110">See Also</span></span>  
 [<span data-ttu-id="8483c-111">Nasıl yapılır: bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="8483c-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="8483c-112">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="8483c-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="8483c-113">Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme</span><span class="sxs-lookup"><span data-stu-id="8483c-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="8483c-114">Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="8483c-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="8483c-115">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="8483c-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
