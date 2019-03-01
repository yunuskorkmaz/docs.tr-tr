---
title: 'Nasıl yapılır: (Visual Basic) bir numaralandırma üyesine başvurma'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: e4f7ede26329ed97c65be8218be78aa40b1294e9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976271"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="e0a5b-102">Nasıl yapılır: (Visual Basic) bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="e0a5b-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="e0a5b-103">Numaralandırmalar ilgili sabitlerinin kümeleri ile birlikte çalışır ve adları ile sabit değerleri ilişkilendirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0a5b-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="e0a5b-104">Örneğin, tamsayı sabitleri haftanın günleri ile ilişkilendirilmiş bir dizi için bir numaralandırmayı bildirmek ve daha sonra kodunuzda tamsayı değerleri yerine gün adlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0a5b-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="e0a5b-105">İle tam olarak nitelenmiş adlar kullanmaktan `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e0a5b-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="e0a5b-106">Daha fazla bilgi için [numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="e0a5b-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="e0a5b-107">Bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="e0a5b-107">To refer to an enumeration member</span></span>  
  
-   <span data-ttu-id="e0a5b-108">Sabit üye adıyla niteleyin.</span><span class="sxs-lookup"><span data-stu-id="e0a5b-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="e0a5b-109">Örneğin, aşağıdaki örnekte atar `Saturday` üyesi `FirstDayOfWeek` numaralandırma değişkenine `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="e0a5b-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="e0a5b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0a5b-110">See also</span></span>
- [<span data-ttu-id="e0a5b-111">Nasıl yapılır: Bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="e0a5b-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="e0a5b-112">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="e0a5b-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="e0a5b-113">Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme yapma</span><span class="sxs-lookup"><span data-stu-id="e0a5b-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="e0a5b-114">Nasıl yapılır: Bir numaralandırma değeriyle ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="e0a5b-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="e0a5b-115">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="e0a5b-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
