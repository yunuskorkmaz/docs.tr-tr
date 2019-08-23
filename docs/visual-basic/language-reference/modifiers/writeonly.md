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
ms.openlocfilehash: 43507ac8e9b5843e8fa9496737a3d77b3a425a7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963765"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="3f357-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f357-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="3f357-103">Bir özelliğin yazılabileceğini ancak okunlamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f357-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f357-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f357-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3f357-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="3f357-105">Rules</span></span>  
 <span data-ttu-id="3f357-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="3f357-106">**Declaration Context.**</span></span> <span data-ttu-id="3f357-107">Yalnızca modül düzeyinde `WriteOnly` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f357-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="3f357-108">Yani, bir `WriteOnly` özelliğin bildirim bağlamı bir sınıf, yapı veya modül olmalıdır ve kaynak dosya, ad alanı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="3f357-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="3f357-109">Bir özelliği bir değişken değil, `WriteOnly`olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f357-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="3f357-110">WriteOnly ne zaman kullanılır?</span><span class="sxs-lookup"><span data-stu-id="3f357-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="3f357-111">Bazen, tüketen kodun bir değer ayarlayabilmesini, ancak ne olduğunu bulamayacağını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f357-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="3f357-112">Örneğin, sosyal kayıt numarası veya parola gibi hassas verilerin, onu ayarlanmamış herhangi bir bileşene erişiminin korunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f357-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="3f357-113">Bu durumlarda, değeri ayarlamak için bir `WriteOnly` özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f357-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3f357-114">Bir `WriteOnly` özelliği tanımlayıp kullandığınızda, aşağıdaki ek koruyucu ölçüleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3f357-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="3f357-115">**Si.**</span><span class="sxs-lookup"><span data-stu-id="3f357-115">**Overriding.**</span></span> <span data-ttu-id="3f357-116">Özelliği bir sınıfın üyesiyse, [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)' ın varsayılan yapmasına izin verin ve bunu `Overridable` veya `MustOverride`bildirmeyin.</span><span class="sxs-lookup"><span data-stu-id="3f357-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="3f357-117">Bu, türetilmiş bir sınıfın bir geçersiz kılma aracılığıyla istenmeyen erişim yapmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="3f357-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="3f357-118">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="3f357-118">**Access Level.**</span></span> <span data-ttu-id="3f357-119">Özelliğin hassas verilerini bir veya daha fazla değişkenlerde tutarsanız, başka hiçbir kodun erişemez olması için bunları [özel](../../../visual-basic/language-reference/modifiers/private.md) olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="3f357-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="3f357-120">**Şifreleme.**</span><span class="sxs-lookup"><span data-stu-id="3f357-120">**Encryption.**</span></span> <span data-ttu-id="3f357-121">Tüm hassas verileri düz metin yerine şifreli biçimde depolayın.</span><span class="sxs-lookup"><span data-stu-id="3f357-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="3f357-122">Kötü amaçlı kod, bu bellek alanına bir şekilde erişim kazanıyorsa, verilerin kullanılması daha zordur.</span><span class="sxs-lookup"><span data-stu-id="3f357-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="3f357-123">Şifreleme, hassas verileri serileştirmek için gerekliyse da yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3f357-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="3f357-124">**Sıfırlanması.**</span><span class="sxs-lookup"><span data-stu-id="3f357-124">**Resetting.**</span></span> <span data-ttu-id="3f357-125">Özelliği tanımlayan sınıf, yapı veya modül sonlandırıldığı zaman, hassas verileri varsayılan değerlere veya daha anlamlı değerlere sıfırlayın.</span><span class="sxs-lookup"><span data-stu-id="3f357-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="3f357-126">Bu, bellek alanı genel erişim için serbest bırakıldığında daha fazla koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f357-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="3f357-127">**Kalıcılığı.**</span><span class="sxs-lookup"><span data-stu-id="3f357-127">**Persistence.**</span></span> <span data-ttu-id="3f357-128">Herhangi bir hassas verileri (örneğin, disk üzerinde) kalıcı olarak kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="3f357-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="3f357-129">Ayrıca, panoya gizli veriler eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="3f357-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="3f357-130">`WriteOnly` Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="3f357-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="3f357-131">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="3f357-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3f357-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f357-132">See also</span></span>

- [<span data-ttu-id="3f357-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="3f357-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="3f357-134">Private</span><span class="sxs-lookup"><span data-stu-id="3f357-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="3f357-135">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="3f357-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
