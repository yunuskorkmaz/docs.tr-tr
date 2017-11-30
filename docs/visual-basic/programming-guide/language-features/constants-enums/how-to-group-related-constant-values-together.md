---
title: "Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be57b56047654d6eb3536bb0b8f63eca27decdb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="1d883-102">Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d883-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="1d883-103">Numaralandırma, ilgili sabitleri gruplamak için en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="1d883-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="1d883-104">Bir numaralandırma ile oluşturduğunuz `Enum` deyiminin bildirimleri bölümünde bir sınıf veya bir modül.</span><span class="sxs-lookup"><span data-stu-id="1d883-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="1d883-105">Daha fazla bilgi için bkz: [nasıl yapılır: bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="1d883-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="1d883-106">Grup için ilgili sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="1d883-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="1d883-107">Kod erişim düzeyi içeren bir bildirim yazma `Enum` anahtar sözcük ve geçerli bir ad.</span><span class="sxs-lookup"><span data-stu-id="1d883-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="1d883-108">Bu örnekte `Private` numaralandırma, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="1d883-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  <span data-ttu-id="1d883-109">Sabitler numaralandırmada tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1d883-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="1d883-110">Bu örnekte `Public` numaralandırma `temperatureValues` ve değerlerini atar.</span><span class="sxs-lookup"><span data-stu-id="1d883-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1d883-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d883-111">See Also</span></span>  
 [<span data-ttu-id="1d883-112">Numaralandırmalar ve ad niteliği</span><span class="sxs-lookup"><span data-stu-id="1d883-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="1d883-113">Nasıl yapılır: bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="1d883-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="1d883-114">Bir numaralandırmanın ne zaman kullanılacağı</span><span class="sxs-lookup"><span data-stu-id="1d883-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="1d883-115">Sabitlere genel bakış</span><span class="sxs-lookup"><span data-stu-id="1d883-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="1d883-116">Sabit ve değişmez değerli veri türleri</span><span class="sxs-lookup"><span data-stu-id="1d883-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="1d883-117">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="1d883-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
