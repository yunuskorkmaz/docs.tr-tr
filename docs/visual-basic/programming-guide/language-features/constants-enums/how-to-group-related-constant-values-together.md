---
title: 'Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 151eefee4f69e1db8ba40f91334da8a051b95732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354038"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="ef7da-102">Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef7da-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="ef7da-103">Listeleme, ilgili sabitleri birlikte gruplandırmak için en iyi yoldur.</span><span class="sxs-lookup"><span data-stu-id="ef7da-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="ef7da-104">Bir sınıfın veya modülün Bildirimler bölümünde `Enum` ifadesiyle bir numaralandırma oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="ef7da-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="ef7da-105">Daha fazla bilgi için bkz. [nasıl yapılır: numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="ef7da-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="ef7da-106">İlgili sabit değerleri gruplandırmak için</span><span class="sxs-lookup"><span data-stu-id="ef7da-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="ef7da-107">Kod erişim düzeyini, `Enum` anahtar sözcüğünü ve geçerli bir adı içeren bir bildirim yazın.</span><span class="sxs-lookup"><span data-stu-id="ef7da-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="ef7da-108">Bu örnekte, `temperatureValues``Private` numaralandırması oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ef7da-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="ef7da-109">Sabit Listesi içindeki sabitleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ef7da-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="ef7da-110">Bu örnek `Public` numaralandırma `temperatureValues` oluşturur ve değerlerini atar.</span><span class="sxs-lookup"><span data-stu-id="ef7da-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ef7da-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef7da-111">See also</span></span>

- [<span data-ttu-id="ef7da-112">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="ef7da-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="ef7da-113">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="ef7da-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="ef7da-114">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="ef7da-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="ef7da-115">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ef7da-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="ef7da-116">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="ef7da-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="ef7da-117">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ef7da-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
