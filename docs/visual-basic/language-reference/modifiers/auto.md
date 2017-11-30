---
title: Otomatik (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e32c4c910567829a4f5c59b48020db4dfbbeb7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="auto-visual-basic"></a><span data-ttu-id="b18cb-102">Otomatik (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b18cb-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="b18cb-103">Visual Basic dizeleri bildirilen dış yordamı dış adını temel alarak .NET Framework kurallarına göre sıralama belirtir.</span><span class="sxs-lookup"><span data-stu-id="b18cb-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="b18cb-104">Projenizin dışında tanımlı bir yordam çağrısı, Visual Basic derleyici doğru yordam çağrısı için gereken bilgilere erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="b18cb-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="b18cb-105">Bu bilgiler yordamı bulunduğu, nasıl tanımlanır, kendi arama sırası ve dönüş türü içerir ve dize karakter kullanır ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b18cb-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="b18cb-106">[Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) dış bir yordam için bir başvuru oluşturur ve bu gerekli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b18cb-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="b18cb-107">`charsetmodifier` Bölümün `Declare` deyimi dış yordamı yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b18cb-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="b18cb-108">Visual Basic dış yordamı adı için dış dosyasını nasıl arayacağını etkiler.</span><span class="sxs-lookup"><span data-stu-id="b18cb-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="b18cb-109">`Auto` Değiştiricisi belirtir Visual Basic .NET Framework kurallarına göre dizeleri sıralama ve gerekir temel karakter çalışma zamanı platform ve muhtemelen kümesini belirlemelisiniz ilk arıyorsanız dış yordam adı değiştirin, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b18cb-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="b18cb-110">Daha fazla bilgi için bkz: "Karakter kümesi" [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b18cb-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="b18cb-111">Herhangi bir karakter kümesi değiştiricisi belirtilirse, `Ansi` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b18cb-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b18cb-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b18cb-112">Remarks</span></span>  
 <span data-ttu-id="b18cb-113">`Auto` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b18cb-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="b18cb-114">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="b18cb-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="b18cb-115">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="b18cb-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="b18cb-116">Bu anahtar sözcük desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="b18cb-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b18cb-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b18cb-117">See Also</span></span>  
 [<span data-ttu-id="b18cb-118">ANSI</span><span class="sxs-lookup"><span data-stu-id="b18cb-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="b18cb-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="b18cb-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="b18cb-120">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b18cb-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
