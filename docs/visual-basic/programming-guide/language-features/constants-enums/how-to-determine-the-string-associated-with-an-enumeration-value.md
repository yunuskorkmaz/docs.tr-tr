---
title: 'Nasıl yapılır: Bir sabit listesi değeri (Visual Basic) ile ilişkili dizeyi belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 92d2e9918429c9cf408f288f832e4615b95ad423
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690195"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="503ca-102">Nasıl yapılır: Bir sabit listesi değeri (Visual Basic) ile ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="503ca-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="503ca-103"><xref:System.Enum.GetValues%2A> Ve <xref:System.Enum.GetNames%2A> yöntemler dizeleri ve numaralandırma üyeleri ile ilişkilendirilmiş değerlerini belirlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="503ca-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="503ca-104">Bir numaralandırma ile ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="503ca-104">To determine the string associated with an enumeration</span></span>  
  
-   <span data-ttu-id="503ca-105">Kullanım <xref:System.Enum.GetNames%2A> numaralandırma üyeleri ile ilişkilendirilmiş dizeler almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="503ca-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="503ca-106">Bu örnek, bir sabit listesi bildirir `flavorEnum`, ardından <xref:System.Enum.GetNames%2A> her üye ile ilişkili dizelerin görüntülemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="503ca-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="503ca-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="503ca-107">See also</span></span>
- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="503ca-108">Nasıl yapılır: Bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="503ca-108">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="503ca-109">Nasıl yapılır: Bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="503ca-109">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="503ca-110">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="503ca-110">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="503ca-111">Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme yapma</span><span class="sxs-lookup"><span data-stu-id="503ca-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="503ca-112">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="503ca-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="503ca-113">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="503ca-113">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
