---
title: 'Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 4138759bfbb049b77406fc536219b40d3ed9e2a5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058775"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="d1eb5-102">Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1eb5-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>

<span data-ttu-id="d1eb5-103"><xref:System.Enum.GetValues%2A>Ve <xref:System.Enum.GetNames%2A> yöntemleri, numaralandırma üyeleriyle ilişkili dizeleri ve değerleri belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1eb5-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="d1eb5-104">Bir sabit listesi ile ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="d1eb5-104">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="d1eb5-105"><xref:System.Enum.GetNames%2A>Numaralandırma üyeleriyle ilişkili dizeleri almak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1eb5-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="d1eb5-106">Bu örnek bir sabit listesi bildirir, `flavorEnum` sonra <xref:System.Enum.GetNames%2A> her üyeyle ilişkili dizeleri göstermek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1eb5-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d1eb5-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1eb5-107">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="d1eb5-108">Nasıl yapılır: numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="d1eb5-108">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="d1eb5-109">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="d1eb5-109">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="d1eb5-110">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="d1eb5-110">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="d1eb5-111">Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma</span><span class="sxs-lookup"><span data-stu-id="d1eb5-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="d1eb5-112">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="d1eb5-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="d1eb5-113">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="d1eb5-113">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
