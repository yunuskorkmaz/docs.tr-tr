---
title: Numaralandırmalar ve Ad Niteliği (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: eb1f5653d968e81168833cd57813219e8f049b70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648586"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="f923b-102">Numaralandırmalar ve Ad Niteliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f923b-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="f923b-103">Normalde, bir numaralandırma üyesi için söz konusu olduğunda numaralandırması adıyla üye nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f923b-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="f923b-104">Örneğin, başvurmak için `Sunday` üyesi, `Days` numaralandırma, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="f923b-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="f923b-105">Imports deyimi kullanarak</span><span class="sxs-lookup"><span data-stu-id="f923b-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="f923b-106">Ekleyerek tam olarak nitelenmiş adlar kullanmaktan kaçınabilirsiniz bir `Imports` ad alanı bildirimleri bölümüne aşağıdaki örnekte olduğu gibi kodunuzu deyimi:</span><span class="sxs-lookup"><span data-stu-id="f923b-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 <span data-ttu-id="f923b-107">Bir `Imports` başvurulan projeleri ve derlemeler ve içinden ad alanı adları Imports deyimi aynı projesi deyim göründüğü modülü olarak.</span><span class="sxs-lookup"><span data-stu-id="f923b-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="f923b-108">Bu bildirimi eklendikten sonra aşağıdaki örnekte olduğu gibi nitelik olmadan numaralandırma üyeleri başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="f923b-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 <span data-ttu-id="f923b-109">Numaralandırmalar ilgili sabitler kümesi düzenleyerek farklı bağlamlarda aynı sabit adlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f923b-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="f923b-110">Örneğin, haftanın günü sabitler için aynı adlarını kullanabilirsiniz `Days` ve `WorkDays` numaralandırmalar.</span><span class="sxs-lookup"><span data-stu-id="f923b-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="f923b-111">Kullanırsanız `Imports` deyimi, numaralandırmalar sahip olmanız gerekir belirsiz başvuruları kaçınmak için dikkatli.</span><span class="sxs-lookup"><span data-stu-id="f923b-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="f923b-112">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f923b-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 <span data-ttu-id="f923b-113">Varsayılarak `Monday` her ikisi de üyesi `Days` numaralandırma ve `Workdays` numaralandırma, bu kod bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f923b-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="f923b-114">Tek bir sabite başvururken belirsiz başvuruları önlemek için kendi numaralandırma sabit adıyla nitelemek.</span><span class="sxs-lookup"><span data-stu-id="f923b-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="f923b-115">Aşağıdaki kod başvurduğu `Saturday` sabitler `Days` ve `WorkDays` numaralandırmalar.</span><span class="sxs-lookup"><span data-stu-id="f923b-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f923b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f923b-116">See Also</span></span>  
 [<span data-ttu-id="f923b-117">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f923b-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="f923b-118">Nasıl yapılır: bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="f923b-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="f923b-119">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="f923b-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="f923b-120">Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme</span><span class="sxs-lookup"><span data-stu-id="f923b-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="f923b-121">Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="f923b-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="f923b-122">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="f923b-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="f923b-123">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f923b-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="f923b-124">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="f923b-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="f923b-125">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="f923b-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="f923b-126">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f923b-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
