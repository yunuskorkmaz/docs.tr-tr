---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: Ilgili sabit değerleri birlikte gruplandırma (Visual Basic)'
title: 'Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: ddd60696d2c751810e49ecbcb537589bedc58abf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471597"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="dcaed-103">Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcaed-103">How to: Group Related Constant Values Together (Visual Basic)</span></span>

<span data-ttu-id="dcaed-104">Listeleme, ilgili sabitleri birlikte gruplandırmak için en iyi yoldur.</span><span class="sxs-lookup"><span data-stu-id="dcaed-104">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="dcaed-105">`Enum`Bir sınıfın veya modülün Bildirimler bölümünde ifadesiyle bir numaralandırma oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="dcaed-105">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="dcaed-106">Daha fazla bilgi için bkz. [nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="dcaed-106">For more information, see [How to: Declare an Enumeration](how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="dcaed-107">İlgili sabit değerleri gruplandırmak için</span><span class="sxs-lookup"><span data-stu-id="dcaed-107">To group related constant values</span></span>  
  
1. <span data-ttu-id="dcaed-108">Kod erişim düzeyi, `Enum` anahtar sözcük ve geçerli bir ad içeren bir bildirim yazın.</span><span class="sxs-lookup"><span data-stu-id="dcaed-108">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="dcaed-109">Bu örnek `Private` , sabit listesini oluşturur `temperatureValues` ,.</span><span class="sxs-lookup"><span data-stu-id="dcaed-109">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="dcaed-110">Sabit Listesi içindeki sabitleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="dcaed-110">Define the constants in the enumeration.</span></span> <span data-ttu-id="dcaed-111">Bu örnek, `Public` sabit listesini oluşturur `temperatureValues` ve değerlerini atar.</span><span class="sxs-lookup"><span data-stu-id="dcaed-111">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dcaed-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcaed-112">See also</span></span>

- [<span data-ttu-id="dcaed-113">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="dcaed-113">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="dcaed-114">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="dcaed-114">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="dcaed-115">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="dcaed-115">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="dcaed-116">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dcaed-116">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="dcaed-117">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="dcaed-117">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="dcaed-118">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="dcaed-118">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
