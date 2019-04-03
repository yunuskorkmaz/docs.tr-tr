---
title: "Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme yapma"
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 63597145e96b04affc5f0e80e05a56b3fdf27278
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833366"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="8fe73-102">Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme yapma</span><span class="sxs-lookup"><span data-stu-id="8fe73-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="8fe73-103">Numaralandırmalar ilgili sabitlerinin kümeleri ile birlikte çalışır ve adları ile sabit değerleri ilişkilendirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fe73-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="8fe73-104">Sabit listesi yoluyla yineleme yapmak için bir dizi kullanarak taşıyabilirsiniz <xref:System.Enum.GetValues%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8fe73-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="8fe73-105">Bir listeleme kullanarak aracılığıyla da yineleme bir `For...Each` deyimini kullanarak <xref:System.Enum.GetNames%2A> veya <xref:System.Enum.GetValues%2A> dize veya sayısal değeri ayıklamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8fe73-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="8fe73-106">Sabit listesi yoluyla yineleme yapmak için</span><span class="sxs-lookup"><span data-stu-id="8fe73-106">To iterate through an enumeration</span></span>  
  
-   <span data-ttu-id="8fe73-107">Bir diziyi bildirmek ve onunla numaralandırma dönüştürmek <xref:System.Enum.GetValues%2A> yöntemi, dizi geçirmeden önce başka bir değişken gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fe73-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="8fe73-108">Aşağıdaki örnek, her bir numaralandırma üyesi görüntüler <xref:Microsoft.VisualBasic.FirstDayOfWeek> olarak sabit listesi yinelenir.</span><span class="sxs-lookup"><span data-stu-id="8fe73-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="8fe73-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fe73-109">See also</span></span>

- [<span data-ttu-id="8fe73-110">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8fe73-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="8fe73-111">Nasıl yapılır: Bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="8fe73-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="8fe73-112">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="8fe73-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="8fe73-113">Nasıl yapılır: Bir numaralandırma değeriyle ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="8fe73-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="8fe73-114">Nasıl yapılır: Bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="8fe73-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="8fe73-115">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="8fe73-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="8fe73-116">Diziler</span><span class="sxs-lookup"><span data-stu-id="8fe73-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
