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
ms.openlocfilehash: 9edb809624727aba5c40b410d0356804257bf516
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964664"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="b3d9b-102">Numaralandırmalar ve Ad Niteliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3d9b-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="b3d9b-103">Normalde, bir sabit listesi üyesi için söz konusu olduğunda, üye adını sabit listesi adıyla nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3d9b-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="b3d9b-104">Örneğin, başvurmak için `Sunday` üyesi, `Days` numaralandırma, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="b3d9b-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="b3d9b-105">Imports deyimi kullanarak</span><span class="sxs-lookup"><span data-stu-id="b3d9b-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="b3d9b-106">Ekleyerek tam olarak nitelenmiş adlar kullanmaktan kaçınabilirsiniz bir `Imports` ad alanı bildirimleri bölümüne aşağıdaki örnekte olduğu gibi kodunuzun deyimi:</span><span class="sxs-lookup"><span data-stu-id="b3d9b-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="b3d9b-107">Bir `Imports` başvurulan projeleri ve derlemeleri ve içinden ad alanı adları Imports deyimi deyim göründüğü modül olarak aynı proje.</span><span class="sxs-lookup"><span data-stu-id="b3d9b-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="b3d9b-108">Bu bildirimi eklendikten sonra aşağıdaki örnekte olduğu gibi bir nitelik olmadan numaralandırma üyeleri başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="b3d9b-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="b3d9b-109">İlişkili numaralandırmalar sabitlerle kümesi düzenleyerek, farklı bağlamlardaki aynı sabit adları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3d9b-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="b3d9b-110">Örneğin, hafta içi sabitlerle için aynı adları kullanabilirsiniz `Days` ve `WorkDays` numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="b3d9b-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="b3d9b-111">Kullanırsanız `Imports` ifadesi, sabit listeleri ile olmalısınız belirsiz başvuru kaçınmak dikkatli.</span><span class="sxs-lookup"><span data-stu-id="b3d9b-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="b3d9b-112">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b3d9b-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="b3d9b-113">Varsayarak `Monday` hem de bir üyesi `Days` numaralandırma ve `Workdays` sabit listesi, bu kod bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b3d9b-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="b3d9b-114">Tek bir sabite söz konusu olduğunda belirsiz başvuru kaçınmak için sabit, sabit listesi adıyla niteleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d9b-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="b3d9b-115">Aşağıdaki kod başvurduğu `Saturday` sabitlerle `Days` ve `WorkDays` numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="b3d9b-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="b3d9b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3d9b-116">See also</span></span>
- [<span data-ttu-id="b3d9b-117">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b3d9b-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="b3d9b-118">Nasıl yapılır: Bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="b3d9b-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="b3d9b-119">Nasıl yapılır: Bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="b3d9b-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="b3d9b-120">Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme yapma</span><span class="sxs-lookup"><span data-stu-id="b3d9b-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="b3d9b-121">Nasıl yapılır: Bir numaralandırma değeriyle ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="b3d9b-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="b3d9b-122">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="b3d9b-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="b3d9b-123">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="b3d9b-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="b3d9b-124">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="b3d9b-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="b3d9b-125">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="b3d9b-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="b3d9b-126">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="b3d9b-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
