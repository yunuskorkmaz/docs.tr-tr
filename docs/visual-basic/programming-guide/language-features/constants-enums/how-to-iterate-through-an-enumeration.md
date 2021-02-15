---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic bir numaralandırma aracılığıyla yineleme'
title: 'Nasıl yapılır: Sabit Listesi Yoluyla Yineleme'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: a14d65a33e8a2f7872203a6a332dec1e753704f8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471571"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="762e9-103">Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma</span><span class="sxs-lookup"><span data-stu-id="762e9-103">How to: Iterate Through An Enumeration in Visual Basic</span></span>

<span data-ttu-id="762e9-104">Numaralandırmalar ilgili sabitler kümesiyle çalışmanın kolay bir yolunu sağlar ve sabit değerleri adlarla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="762e9-104">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="762e9-105">Bir numaralandırma boyunca yinelemek için yöntemini kullanarak bir diziye taşıyabilirsiniz <xref:System.Enum.GetValues%2A> .</span><span class="sxs-lookup"><span data-stu-id="762e9-105">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="762e9-106">Ayrıca, `For...Each` <xref:System.Enum.GetNames%2A> <xref:System.Enum.GetValues%2A> dize veya sayısal değeri ayıklamak için veya yöntemini kullanarak bir sıralama kullanarak bir numaralandırma aracılığıyla yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="762e9-106">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="762e9-107">Bir sabit listesi üzerinden yinelemek için</span><span class="sxs-lookup"><span data-stu-id="762e9-107">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="762e9-108">Diziyi <xref:System.Enum.GetValues%2A> başka herhangi bir değişken gibi geçirmeden önce bir diziyi bildirin ve bu öğeyi bu yönteme dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="762e9-108">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="762e9-109">Aşağıdaki örnek, sabit listesinin her bir üyesini <xref:Microsoft.VisualBasic.FirstDayOfWeek> numaralandırma boyunca yineleme yaparken görüntüler.</span><span class="sxs-lookup"><span data-stu-id="762e9-109">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="762e9-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="762e9-110">See also</span></span>

- [<span data-ttu-id="762e9-111">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="762e9-111">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="762e9-112">Nasıl yapılır: numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="762e9-112">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="762e9-113">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="762e9-113">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="762e9-114">Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="762e9-114">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="762e9-115">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="762e9-115">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="762e9-116">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="762e9-116">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="762e9-117">Diziler</span><span class="sxs-lookup"><span data-stu-id="762e9-117">Arrays</span></span>](../arrays/index.md)
