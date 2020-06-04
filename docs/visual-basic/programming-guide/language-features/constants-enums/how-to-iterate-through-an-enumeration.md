---
title: 'Nasıl yapılır: Sabit Listesi Yoluyla Yineleme'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: fb6fbdd45ca0e84ccb9fc55296d78e3867d5fe25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414433"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="b08f6-102">Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma</span><span class="sxs-lookup"><span data-stu-id="b08f6-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="b08f6-103">Numaralandırmalar ilgili sabitler kümesiyle çalışmanın kolay bir yolunu sağlar ve sabit değerleri adlarla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="b08f6-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="b08f6-104">Bir numaralandırma boyunca yinelemek için yöntemini kullanarak bir diziye taşıyabilirsiniz <xref:System.Enum.GetValues%2A> .</span><span class="sxs-lookup"><span data-stu-id="b08f6-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="b08f6-105">Ayrıca, `For...Each` <xref:System.Enum.GetNames%2A> <xref:System.Enum.GetValues%2A> dize veya sayısal değeri ayıklamak için veya yöntemini kullanarak bir sıralama kullanarak bir numaralandırma aracılığıyla yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b08f6-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="b08f6-106">Bir sabit listesi üzerinden yinelemek için</span><span class="sxs-lookup"><span data-stu-id="b08f6-106">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="b08f6-107">Diziyi <xref:System.Enum.GetValues%2A> başka herhangi bir değişken gibi geçirmeden önce bir diziyi bildirin ve bu öğeyi bu yönteme dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="b08f6-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="b08f6-108">Aşağıdaki örnek, sabit listesinin her bir üyesini <xref:Microsoft.VisualBasic.FirstDayOfWeek> numaralandırma boyunca yineleme yaparken görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b08f6-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b08f6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b08f6-109">See also</span></span>

- [<span data-ttu-id="b08f6-110">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b08f6-110">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="b08f6-111">Nasıl yapılır: numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="b08f6-111">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="b08f6-112">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="b08f6-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="b08f6-113">Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="b08f6-113">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="b08f6-114">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="b08f6-114">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="b08f6-115">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="b08f6-115">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="b08f6-116">Diziler</span><span class="sxs-lookup"><span data-stu-id="b08f6-116">Arrays</span></span>](../arrays/index.md)
