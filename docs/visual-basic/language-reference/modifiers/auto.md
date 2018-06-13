---
title: Otomatik (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 414998b4bef526060e7ba4f584fa071fbd0acaa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595881"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="57b5c-102">Otomatik (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57b5c-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="57b5c-103">Visual Basic dizeleri bildirilen dış yordamı dış adını temel alarak .NET Framework kurallarına göre sıralama belirtir.</span><span class="sxs-lookup"><span data-stu-id="57b5c-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="57b5c-104">Projenizin dışında tanımlı bir yordam çağrısı, Visual Basic derleyici doğru yordam çağrısı için gereken bilgilere erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="57b5c-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="57b5c-105">Bu bilgiler yordamı bulunduğu, nasıl tanımlanır, kendi arama sırası ve dönüş türü içerir ve dize karakter kullanır ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="57b5c-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="57b5c-106">[Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) dış bir yordam için bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="57b5c-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="57b5c-107">`charsetmodifier` Bölümün `Declare` deyimi dış yordamı yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="57b5c-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="57b5c-108">Visual Basic dış yordamı adı için dış dosyasını nasıl arayacağını etkiler.</span><span class="sxs-lookup"><span data-stu-id="57b5c-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="57b5c-109">`Auto` Değiştiricisi belirtir Visual Basic .NET Framework kurallarına göre dizeleri sıralama ve gerekir temel karakter çalışma zamanı platform ve muhtemelen kümesini belirlemelisiniz ilk arıyorsanız dış yordam adı değiştirin, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="57b5c-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="57b5c-110">Daha fazla bilgi için bkz: "Karakter kümesi" [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="57b5c-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="57b5c-111">Herhangi bir karakter kümesi değiştiricisi belirtilirse, `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="57b5c-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57b5c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57b5c-112">Remarks</span></span>  
 <span data-ttu-id="57b5c-113">`Auto` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="57b5c-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="57b5c-114">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="57b5c-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="57b5c-115">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="57b5c-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="57b5c-116">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="57b5c-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b5c-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57b5c-117">See Also</span></span>  
 [<span data-ttu-id="57b5c-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="57b5c-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="57b5c-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="57b5c-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="57b5c-120">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="57b5c-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
