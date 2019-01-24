---
title: 'Nasıl yapılır: Grup ilgili sabit değerleri birlikte (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 04697092534daa6f83a29e69dcdc509644fa6147
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558689"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="5ff80-102">Nasıl yapılır: Grup ilgili sabit değerleri birlikte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ff80-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="5ff80-103">Bir sabit listesi, ilgili sabit değerleri birlikte gruplamak için en iyi bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="5ff80-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="5ff80-104">Numaralandırma ile oluşturma `Enum` bir sınıf veya modül bildirimleri bölümünde bildirimi.</span><span class="sxs-lookup"><span data-stu-id="5ff80-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="5ff80-105">Daha fazla bilgi için [nasıl yapılır: Bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="5ff80-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="5ff80-106">Gruba ilgili sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="5ff80-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="5ff80-107">Kod erişim düzeyi içeren bir bildirimi yazma `Enum` anahtar sözcük ve geçerli bir ad.</span><span class="sxs-lookup"><span data-stu-id="5ff80-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="5ff80-108">Bu örnekte `Private` numaralandırma `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="5ff80-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  <span data-ttu-id="5ff80-109">Sabitleri sabit listesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5ff80-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="5ff80-110">Bu örnekte `Public` numaralandırma `temperatureValues` ve değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="5ff80-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5ff80-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ff80-111">See also</span></span>
- [<span data-ttu-id="5ff80-112">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="5ff80-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="5ff80-113">Nasıl yapılır: Bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="5ff80-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="5ff80-114">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="5ff80-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="5ff80-115">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5ff80-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="5ff80-116">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="5ff80-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="5ff80-117">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="5ff80-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
