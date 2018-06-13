---
title: "Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma"
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 06609d38c805e5f073a2f3a299ecc3aa7cf7be01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646584"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="c644a-102">Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma</span><span class="sxs-lookup"><span data-stu-id="c644a-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="c644a-103">Numaralandırmalar ilgili sabitleri kümeleriyle çalışmak ve sabit değerleri adlarıyla ilişkilendirmek için kolay bir yol sağlamak.</span><span class="sxs-lookup"><span data-stu-id="c644a-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="c644a-104">Bir numaralandırma yineleme yapmak için bir dizi kullanarak taşıyabilirsiniz <xref:System.Enum.GetValues%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c644a-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="c644a-105">Bir numaralandırma kullanarak aracılığıyla da yinelemek bir `For...Each` deyimi kullanarak <xref:System.Enum.GetNames%2A> veya <xref:System.Enum.GetValues%2A> yöntemi dizeyi veya sayı değerini ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="c644a-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="c644a-106">Bir numaralandırma yineleme</span><span class="sxs-lookup"><span data-stu-id="c644a-106">To iterate through an enumeration</span></span>  
  
-   <span data-ttu-id="c644a-107">Bir dizi bildirme ve onunla numaralandırması dönüştürmek <xref:System.Enum.GetValues%2A> yöntemi, dizi geçirmeden önce başka bir değişken gerekir.</span><span class="sxs-lookup"><span data-stu-id="c644a-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="c644a-108">Aşağıdaki örnek her bir numaralandırma üyesi görüntüler <xref:Microsoft.VisualBasic.FirstDayOfWeek> numaralandırma yineleme olarak.</span><span class="sxs-lookup"><span data-stu-id="c644a-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c644a-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c644a-109">See Also</span></span>  
 [<span data-ttu-id="c644a-110">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c644a-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="c644a-111">Nasıl yapılır: bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="c644a-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="c644a-112">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="c644a-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="c644a-113">Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="c644a-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="c644a-114">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="c644a-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="c644a-115">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="c644a-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="c644a-116">Diziler</span><span class="sxs-lookup"><span data-stu-id="c644a-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
