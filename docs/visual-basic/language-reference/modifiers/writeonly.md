---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dab9115c31e538bd28583b9f0591ae0c9611e2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="cd27c-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd27c-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="cd27c-103">Bir özellik yazılmış ancak okunamıyor belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd27c-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd27c-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd27c-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="cd27c-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="cd27c-105">Rules</span></span>  
 <span data-ttu-id="cd27c-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="cd27c-106">**Declaration Context.**</span></span> <span data-ttu-id="cd27c-107">Kullanabileceğiniz `WriteOnly` yalnızca modülü düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="cd27c-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="cd27c-108">Bu bildirimi bağlamının anlamına gelir bir `WriteOnly` özelliği bir sınıf, yapı veya modülü olmalıdır ve bir kaynak dosyasını, ad alanı veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="cd27c-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="cd27c-109">Bir özellik olarak bildirebilir `WriteOnly`, ancak bir değişken değil.</span><span class="sxs-lookup"><span data-stu-id="cd27c-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="cd27c-110">WriteOnly kullanma zamanı</span><span class="sxs-lookup"><span data-stu-id="cd27c-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="cd27c-111">Bazen bir değere ayarlayın ancak nedir Bul değil Süren kod istersiniz.</span><span class="sxs-lookup"><span data-stu-id="cd27c-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="cd27c-112">Örneğin, bir sosyal kayıt numarası veya bir parola gibi hassas verileri, ayarlamamış herhangi bir bileşenin erişime karşı korunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd27c-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="cd27c-113">Bu durumlarda, kullanabileceğiniz bir `WriteOnly` özellik değeri ayarlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="cd27c-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cd27c-114">Ne zaman tanımlama ve kullanma bir `WriteOnly` özelliği, aşağıdaki ek koruyucu ölçüleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="cd27c-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
-   <span data-ttu-id="cd27c-115">**Geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="cd27c-115">**Overriding.**</span></span> <span data-ttu-id="cd27c-116">Özellik bir sınıf üyesi ise, varsayılan olarak izin [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)ve bunu bildirme `Overridable` veya `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="cd27c-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="cd27c-117">Bu, türetilmiş bir sınıf bir geçersiz kılma istenmeyen erişimin yapmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="cd27c-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
-   <span data-ttu-id="cd27c-118">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="cd27c-118">**Access Level.**</span></span> <span data-ttu-id="cd27c-119">Bir veya daha fazla değişkenlerde özelliğin hassas verileri tutarsanız, bunları bildirme [özel](../../../visual-basic/language-reference/modifiers/private.md) başka bir kod bunlara erişebilmesi için.</span><span class="sxs-lookup"><span data-stu-id="cd27c-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
-   <span data-ttu-id="cd27c-120">**Şifreleme.**</span><span class="sxs-lookup"><span data-stu-id="cd27c-120">**Encryption.**</span></span> <span data-ttu-id="cd27c-121">Şifrelenmiş biçimde yerine düz metin tüm hassas verileri depolar.</span><span class="sxs-lookup"><span data-stu-id="cd27c-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="cd27c-122">Kötü amaçlı kod şekilde bellek alanı erişim sağlarsa, yapmak daha zor olduğundan verileri kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd27c-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="cd27c-123">Şifreleme de hassas verileri seri hale getirmek gerekliyse, yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="cd27c-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
-   <span data-ttu-id="cd27c-124">**Sıfırlanıyor.**</span><span class="sxs-lookup"><span data-stu-id="cd27c-124">**Resetting.**</span></span> <span data-ttu-id="cd27c-125">Sınıf, yapı veya özellik tanımlama modülü sonlandırılıyor, hassas verileri varsayılan değerleri veya diğer anlamsız değerlere sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="cd27c-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="cd27c-126">Genel erişim için bellek alanı Boşaltıldığında bu ek koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd27c-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
-   <span data-ttu-id="cd27c-127">**Kalıcılık.**</span><span class="sxs-lookup"><span data-stu-id="cd27c-127">**Persistence.**</span></span> <span data-ttu-id="cd27c-128">Bunu önlemek, örneğin diskteki herhangi bir duyarlı veri devam etmez.</span><span class="sxs-lookup"><span data-stu-id="cd27c-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="cd27c-129">Ayrıca, herhangi bir duyarlı veri panoya yazma.</span><span class="sxs-lookup"><span data-stu-id="cd27c-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="cd27c-130">`WriteOnly` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="cd27c-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="cd27c-131">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="cd27c-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cd27c-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd27c-132">See Also</span></span>  
 [<span data-ttu-id="cd27c-133">Salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd27c-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="cd27c-134">Özel</span><span class="sxs-lookup"><span data-stu-id="cd27c-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="cd27c-135">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="cd27c-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
