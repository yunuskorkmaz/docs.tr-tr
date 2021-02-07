---
description: 'Daha fazla bilgi edinin: WriteOnly (Visual Basic)'
title: WriteOnly
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
ms.openlocfilehash: 514a1de3c8c2cfbde6a9cffc5c235d92454dd966
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674746"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="9956d-103">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9956d-103">WriteOnly (Visual Basic)</span></span>

<span data-ttu-id="9956d-104">Bir özelliğin yazılabileceğini ancak okunlamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9956d-104">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9956d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9956d-105">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9956d-106">Kurallar</span><span class="sxs-lookup"><span data-stu-id="9956d-106">Rules</span></span>  

 <span data-ttu-id="9956d-107">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="9956d-107">**Declaration Context.**</span></span> <span data-ttu-id="9956d-108">`WriteOnly`Yalnızca modül düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9956d-108">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="9956d-109">Yani, bir özelliğin bildirim bağlamı `WriteOnly` bir sınıf, yapı veya modül olmalıdır ve kaynak dosya, ad alanı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="9956d-109">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="9956d-110">Bir özelliği `WriteOnly` bir değişken değil, olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9956d-110">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="9956d-111">WriteOnly ne zaman kullanılır?</span><span class="sxs-lookup"><span data-stu-id="9956d-111">When to Use WriteOnly</span></span>  

 <span data-ttu-id="9956d-112">Bazen, tüketen kodun bir değer ayarlayabilmesini, ancak ne olduğunu bulamayacağını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9956d-112">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="9956d-113">Örneğin, sosyal kayıt numarası veya parola gibi hassas verilerin, onu ayarlanmamış herhangi bir bileşene erişiminin korunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9956d-113">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="9956d-114">Bu durumlarda, `WriteOnly` değeri ayarlamak için bir özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9956d-114">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9956d-115">Bir özelliği tanımlayıp kullandığınızda `WriteOnly` , aşağıdaki ek koruyucu ölçüleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9956d-115">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="9956d-116">**Si.**</span><span class="sxs-lookup"><span data-stu-id="9956d-116">**Overriding.**</span></span> <span data-ttu-id="9956d-117">Özelliği bir sınıfın üyesiyse, [NotOverridable](notoverridable.md)' ın varsayılan yapmasına izin verin ve bunu veya bildirmeyin `Overridable` `MustOverride` .</span><span class="sxs-lookup"><span data-stu-id="9956d-117">If the property is a member of a class, allow it to default to [NotOverridable](notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="9956d-118">Bu, türetilmiş bir sınıfın bir geçersiz kılma aracılığıyla istenmeyen erişim yapmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="9956d-118">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="9956d-119">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="9956d-119">**Access Level.**</span></span> <span data-ttu-id="9956d-120">Özelliğin hassas verilerini bir veya daha fazla değişkenlerde tutarsanız, başka hiçbir kodun erişemez olması için bunları [özel](private.md) olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="9956d-120">If you hold the property's sensitive data in one or more variables, declare them [Private](private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="9956d-121">**Şifreleme.**</span><span class="sxs-lookup"><span data-stu-id="9956d-121">**Encryption.**</span></span> <span data-ttu-id="9956d-122">Tüm hassas verileri düz metin yerine şifreli biçimde depolayın.</span><span class="sxs-lookup"><span data-stu-id="9956d-122">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="9956d-123">Kötü amaçlı kod, bu bellek alanına bir şekilde erişim kazanıyorsa, verilerin kullanılması daha zordur.</span><span class="sxs-lookup"><span data-stu-id="9956d-123">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="9956d-124">Şifreleme, hassas verileri serileştirmek için gerekliyse da yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9956d-124">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="9956d-125">**Sıfırlanması.**</span><span class="sxs-lookup"><span data-stu-id="9956d-125">**Resetting.**</span></span> <span data-ttu-id="9956d-126">Özelliği tanımlayan sınıf, yapı veya modül sonlandırıldığı zaman, hassas verileri varsayılan değerlere veya daha anlamlı değerlere sıfırlayın.</span><span class="sxs-lookup"><span data-stu-id="9956d-126">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="9956d-127">Bu, bellek alanı genel erişim için serbest bırakıldığında daha fazla koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9956d-127">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="9956d-128">**Kalıcılığı.**</span><span class="sxs-lookup"><span data-stu-id="9956d-128">**Persistence.**</span></span> <span data-ttu-id="9956d-129">Herhangi bir hassas verileri (örneğin, disk üzerinde) kalıcı olarak kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="9956d-129">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="9956d-130">Ayrıca, panoya gizli veriler eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="9956d-130">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="9956d-131">`WriteOnly`Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9956d-131">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="9956d-132">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="9956d-132">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9956d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9956d-133">See also</span></span>

- [<span data-ttu-id="9956d-134">Özelliğinin</span><span class="sxs-lookup"><span data-stu-id="9956d-134">ReadOnly</span></span>](readonly.md)
- [<span data-ttu-id="9956d-135">Özel</span><span class="sxs-lookup"><span data-stu-id="9956d-135">Private</span></span>](private.md)
- [<span data-ttu-id="9956d-136">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="9956d-136">Keywords</span></span>](../keywords/index.md)
