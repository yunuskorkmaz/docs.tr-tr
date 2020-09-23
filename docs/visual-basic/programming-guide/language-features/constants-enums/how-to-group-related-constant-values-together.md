---
title: 'Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 0f694aee722e8ce31f663ec9fe52a09a2eb2a958
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058735"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="f9e1c-102">Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9e1c-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>

<span data-ttu-id="f9e1c-103">Listeleme, ilgili sabitleri birlikte gruplandırmak için en iyi yoldur.</span><span class="sxs-lookup"><span data-stu-id="f9e1c-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="f9e1c-104">`Enum`Bir sınıfın veya modülün Bildirimler bölümünde ifadesiyle bir numaralandırma oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="f9e1c-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="f9e1c-105">Daha fazla bilgi için bkz. [nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="f9e1c-105">For more information, see [How to: Declare an Enumeration](how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="f9e1c-106">İlgili sabit değerleri gruplandırmak için</span><span class="sxs-lookup"><span data-stu-id="f9e1c-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="f9e1c-107">Kod erişim düzeyi, `Enum` anahtar sözcük ve geçerli bir ad içeren bir bildirim yazın.</span><span class="sxs-lookup"><span data-stu-id="f9e1c-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="f9e1c-108">Bu örnek `Private` , sabit listesini oluşturur `temperatureValues` ,.</span><span class="sxs-lookup"><span data-stu-id="f9e1c-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="f9e1c-109">Sabit Listesi içindeki sabitleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f9e1c-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="f9e1c-110">Bu örnek, `Public` sabit listesini oluşturur `temperatureValues` ve değerlerini atar.</span><span class="sxs-lookup"><span data-stu-id="f9e1c-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f9e1c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9e1c-111">See also</span></span>

- [<span data-ttu-id="f9e1c-112">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="f9e1c-112">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="f9e1c-113">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="f9e1c-113">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="f9e1c-114">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="f9e1c-114">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="f9e1c-115">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f9e1c-115">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="f9e1c-116">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f9e1c-116">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="f9e1c-117">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="f9e1c-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
