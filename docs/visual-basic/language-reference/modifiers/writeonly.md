---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 163ec17f3ea96744290c54a73054ab132f842127
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647670"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="a86ce-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a86ce-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="a86ce-103">Bir özellik yazılabileceğini ancak okunamayacağını olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86ce-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a86ce-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a86ce-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a86ce-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="a86ce-105">Rules</span></span>  
 <span data-ttu-id="a86ce-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="a86ce-106">**Declaration Context.**</span></span> <span data-ttu-id="a86ce-107">Kullanabileceğiniz `WriteOnly` yalnızca Modül düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="a86ce-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="a86ce-108">Bildirim bağlamı başka bir deyişle bir `WriteOnly` özellik bir sınıf, yapı veya modül olmalıdır ve bir kaynak dosyası, ad alanı ya da yordamın olamaz.</span><span class="sxs-lookup"><span data-stu-id="a86ce-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="a86ce-109">Bir özellik olarak bildirebilirsiniz `WriteOnly`, ancak bir değişken değil.</span><span class="sxs-lookup"><span data-stu-id="a86ce-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="a86ce-110">WriteOnly kullanıldığı durumlar</span><span class="sxs-lookup"><span data-stu-id="a86ce-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="a86ce-111">Bazen bir değeri ayarlandı, ancak bunun ne olduğunu Bul değil yapabilmek için kullanan kodu istersiniz.</span><span class="sxs-lookup"><span data-stu-id="a86ce-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="a86ce-112">Örneğin, sosyal kayıt numarası veya parola gibi hassas verilerin, ayarlamamış herhangi bir bileşeni erişime karşı korunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a86ce-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="a86ce-113">Bu durumlarda, kullandığınız bir `WriteOnly` değeri ayarlamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="a86ce-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a86ce-114">Ne zaman tanımlama ve kullanma bir `WriteOnly` özelliği, aşağıdaki ek koruyucu ölçüleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a86ce-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="a86ce-115">**Geçersiz kılma.**</span><span class="sxs-lookup"><span data-stu-id="a86ce-115">**Overriding.**</span></span> <span data-ttu-id="a86ce-116">Özellik bir sınıf üyesi ise, varsayılan olarak izin [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)ve onu bildirmeyin `Overridable` veya `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="a86ce-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="a86ce-117">Bu, türetilmiş bir sınıf bir geçersiz kılma yoluyla istenmeyen erişim bulunmasını önler.</span><span class="sxs-lookup"><span data-stu-id="a86ce-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="a86ce-118">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="a86ce-118">**Access Level.**</span></span> <span data-ttu-id="a86ce-119">Bir veya daha fazla değişkenlerinde özelliğin hassas verileri tutarsanız, bunları bildirdiğinizde [özel](../../../visual-basic/language-reference/modifiers/private.md) böylece başka bir kod onlara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="a86ce-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="a86ce-120">**Şifreleme.**</span><span class="sxs-lookup"><span data-stu-id="a86ce-120">**Encryption.**</span></span> <span data-ttu-id="a86ce-121">Tüm hassas verileri, şifreli biçimde yerine düz metin Store.</span><span class="sxs-lookup"><span data-stu-id="a86ce-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="a86ce-122">Kötü amaçlı kod şekilde bellek alanı erişim kazanırsa, yapmak daha zor olan verilerin kullanın.</span><span class="sxs-lookup"><span data-stu-id="a86ce-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="a86ce-123">Şifreleme de hassas verileri seri hale getirmek gerekli olması durumunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a86ce-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="a86ce-124">**Sıfırlanıyor.**</span><span class="sxs-lookup"><span data-stu-id="a86ce-124">**Resetting.**</span></span> <span data-ttu-id="a86ce-125">Sınıf, yapı veya modül özellik tanımlama Sonlandırılmakta, hassas verileri varsayılan değerlerine veya diğer anlamsız değerlere sıfırlayın.</span><span class="sxs-lookup"><span data-stu-id="a86ce-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="a86ce-126">Genel erişim için bellek alanı Boşaltıldığında bu ek koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a86ce-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="a86ce-127">**Kalıcılık.**</span><span class="sxs-lookup"><span data-stu-id="a86ce-127">**Persistence.**</span></span> <span data-ttu-id="a86ce-128">Bunu önlemek, örneğin diskte hassas verilerin kalıcı olarak tutmaz.</span><span class="sxs-lookup"><span data-stu-id="a86ce-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="a86ce-129">Aynı zamanda, hassas verileri panoya yazma değil.</span><span class="sxs-lookup"><span data-stu-id="a86ce-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="a86ce-130">`WriteOnly` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a86ce-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="a86ce-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="a86ce-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a86ce-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a86ce-132">See also</span></span>

- [<span data-ttu-id="a86ce-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="a86ce-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="a86ce-134">Private</span><span class="sxs-lookup"><span data-stu-id="a86ce-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="a86ce-135">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="a86ce-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
