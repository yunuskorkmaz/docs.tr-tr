---
title: 'Nasıl yapılır: Grup ilgili sabit değerleri birlikte (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 9174bcd2385103cf7fa1daf3133e388f9b4998a4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843769"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="b8af3-102">Nasıl yapılır: Grup ilgili sabit değerleri birlikte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8af3-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="b8af3-103">Bir sabit listesi, ilgili sabit değerleri birlikte gruplamak için en iyi bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="b8af3-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="b8af3-104">Numaralandırma ile oluşturma `Enum` bir sınıf veya modül bildirimleri bölümünde bildirimi.</span><span class="sxs-lookup"><span data-stu-id="b8af3-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="b8af3-105">Daha fazla bilgi için [nasıl yapılır: Bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="b8af3-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="b8af3-106">Gruba ilgili sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="b8af3-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="b8af3-107">Kod erişim düzeyi içeren bir bildirimi yazma `Enum` anahtar sözcük ve geçerli bir ad.</span><span class="sxs-lookup"><span data-stu-id="b8af3-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="b8af3-108">Bu örnekte `Private` numaralandırma `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="b8af3-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2.  <span data-ttu-id="b8af3-109">Sabitleri sabit listesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b8af3-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="b8af3-110">Bu örnekte `Public` numaralandırma `temperatureValues` ve değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="b8af3-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b8af3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8af3-111">See also</span></span>

- [<span data-ttu-id="b8af3-112">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="b8af3-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="b8af3-113">Nasıl yapılır: Bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="b8af3-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="b8af3-114">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="b8af3-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="b8af3-115">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b8af3-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="b8af3-116">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="b8af3-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="b8af3-117">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b8af3-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
