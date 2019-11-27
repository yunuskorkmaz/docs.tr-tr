---
title: 'Nasıl yapılır: sabit listesi üzerinden yineleme yapma'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 6e8fd6760565a73d9d3b3d1d02fc872992eea354
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354018"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="5c821-102">Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma</span><span class="sxs-lookup"><span data-stu-id="5c821-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="5c821-103">Numaralandırmalar ilgili sabitler kümesiyle çalışmanın kolay bir yolunu sağlar ve sabit değerleri adlarla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="5c821-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="5c821-104">Bir sabit listesi üzerinden yinelemek için <xref:System.Enum.GetValues%2A> yöntemini kullanarak onu bir diziye taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c821-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="5c821-105">Ayrıca, dize veya sayısal değeri ayıklamak için <xref:System.Enum.GetNames%2A> veya <xref:System.Enum.GetValues%2A> metodunu kullanarak `For...Each` bir sıralama kullanarak bir sabit listesi üzerinden de yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c821-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="5c821-106">Bir sabit listesi üzerinden yinelemek için</span><span class="sxs-lookup"><span data-stu-id="5c821-106">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="5c821-107">Diziyi başka herhangi bir değişken gibi geçirmeden önce bir diziyi bildirin ve <xref:System.Enum.GetValues%2A> yöntemi ile numaralandırmayı buna dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="5c821-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="5c821-108">Aşağıdaki örnek, sabit listesinin her bir üyesini numaralandırma boyunca yineleme <xref:Microsoft.VisualBasic.FirstDayOfWeek> görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5c821-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="5c821-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c821-109">See also</span></span>

- [<span data-ttu-id="5c821-110">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5c821-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="5c821-111">Nasıl yapılır: numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="5c821-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="5c821-112">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="5c821-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="5c821-113">Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="5c821-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="5c821-114">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="5c821-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="5c821-115">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="5c821-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="5c821-116">Diziler</span><span class="sxs-lookup"><span data-stu-id="5c821-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
