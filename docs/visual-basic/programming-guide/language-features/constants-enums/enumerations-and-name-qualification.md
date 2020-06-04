---
title: Sabit Listeleri ve Ad Niteliği
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
ms.openlocfilehash: 4b09284b8282c481e406050d37cbdb2f3c8686bc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414511"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="b2a2b-102">Numaralandırmalar ve Ad Niteliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2a2b-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="b2a2b-103">Normalde, bir numaralandırma üyesine başvuru yaparken, üye adını numaralandırma adıyla nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2a2b-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="b2a2b-104">Örneğin, `Sunday` numaralandırmanın üyesine başvurmak için `Days` aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="b2a2b-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="b2a2b-105">Imports Ifadesini kullanma</span><span class="sxs-lookup"><span data-stu-id="b2a2b-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="b2a2b-106">`Imports`Aşağıdaki örnekte olduğu gibi, kodunuzun ad alanı bildirimleri bölümüne bir ifade ekleyerek tam nitelikli adlar kullanmaktan kaçınabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b2a2b-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="b2a2b-107">Bir `Imports` ifade, Başvurulmuş projelerden ve derlemelerden ve aynı proje içinden, deyimin göründüğü modülle ad alanı adlarını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="b2a2b-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="b2a2b-108">Bu ifade eklendikten sonra, aşağıdaki örnekte olduğu gibi, nitelik olmadan sabit listesi üyelerinize başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b2a2b-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="b2a2b-109">Numaralandırmalar içindeki ilgili sabitlerin kümelerini düzenleyerek, farklı bağlamlarda aynı sabit adları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a2b-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="b2a2b-110">Örneğin, `Days` ve numaralandırmalar içindeki hafta içi sabitler için aynı adları kullanabilirsiniz `WorkDays` .</span><span class="sxs-lookup"><span data-stu-id="b2a2b-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="b2a2b-111">`Imports`İfadesini Numaralandırmalarla birlikte kullanıyorsanız, belirsiz başvuruların önüne geçmek için dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2a2b-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="b2a2b-112">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="b2a2b-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="b2a2b-113">`Monday`Hem numaralandırmanın hem de numaralandırmanın üyesi olduğu varsayılarak `Days` `Workdays` , bu kod bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2a2b-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="b2a2b-114">Tek bir Sabitte başvuru yaparken belirsiz başvuruların önüne geçmek için sabit adı kendi numaralandırmasına uygun hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a2b-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="b2a2b-115">Aşağıdaki kod `Saturday` , `Days` ve numaralandırmalar içindeki sabitleri ifade eder `WorkDays` .</span><span class="sxs-lookup"><span data-stu-id="b2a2b-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="b2a2b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2a2b-116">See also</span></span>

- [<span data-ttu-id="b2a2b-117">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b2a2b-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="b2a2b-118">Nasıl yapılır: numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="b2a2b-118">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="b2a2b-119">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="b2a2b-119">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="b2a2b-120">Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma</span><span class="sxs-lookup"><span data-stu-id="b2a2b-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="b2a2b-121">Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="b2a2b-121">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="b2a2b-122">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="b2a2b-122">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="b2a2b-123">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="b2a2b-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="b2a2b-124">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2a2b-124">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="b2a2b-125">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="b2a2b-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="b2a2b-126">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="b2a2b-126">Data Types</span></span>](../../../language-reference/data-types/index.md)
