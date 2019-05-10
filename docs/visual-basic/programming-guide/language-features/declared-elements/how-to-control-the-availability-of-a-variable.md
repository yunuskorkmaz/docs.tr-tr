---
title: 'Nasıl yapılır: (Visual Basic) bir değişkenin kullanılabilirliğini denetleme'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 419f3eed30a5d4b35bcb9dde5242b9092ee9cb79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610493"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="e5728-102">Nasıl yapılır: (Visual Basic) bir değişkenin kullanılabilirliğini denetleme</span><span class="sxs-lookup"><span data-stu-id="e5728-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="e5728-103">Belirterek bir değişkenin kullanılabilirliğini denetleme kendi *erişim düzeyi*.</span><span class="sxs-lookup"><span data-stu-id="e5728-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="e5728-104">Hangi kod okuma veya değişkenine yazma izni olan erişim düzeyini belirler.</span><span class="sxs-lookup"><span data-stu-id="e5728-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="e5728-105">*Üye değişkenleri* (Modül düzeyinde ve her türlü yordam dışında tanımlanan) varsayılan görebileceği herhangi bir kod erişebileceği anlamına gelir genel erişim için.</span><span class="sxs-lookup"><span data-stu-id="e5728-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="e5728-106">Bu, bir erişim değiştiricisidir belirterek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5728-106">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="e5728-107">*Yerel değişkenler* (bir yordam içinde tanımlanmıştır) olup genel erişim sahip ancak yalnızca kendi yordamdaki kodu erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e5728-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="e5728-108">Yerel bir değişken erişim düzeyini değiştiremezsiniz, ancak içerdiği yordamı erişim düzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5728-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="e5728-109">Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e5728-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="e5728-110">Özel ve genel erişim</span><span class="sxs-lookup"><span data-stu-id="e5728-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="e5728-111">Bir değişkenin kendi modül, sınıf veya yapı içinde yalnızca erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="e5728-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="e5728-112">Bir yerde [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) değişken modülü, sınıf veya yapı içinde ancak dışında herhangi bir yordam için.</span><span class="sxs-lookup"><span data-stu-id="e5728-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="e5728-113">Dahil [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e5728-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e5728-114">Okuma veya değişkeninden değil, ancak, modül, sınıf veya yapı içinde herhangi bir yere yazmak, dışında.</span><span class="sxs-lookup"><span data-stu-id="e5728-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="e5728-115">Bir değişken görebileceğiniz herhangi bir koddan erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="e5728-115">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="e5728-116">Bir üye değişkeni için yerleştirin `Dim` bir modül, sınıf veya yapı içinde ancak her türlü yordam dışındaki değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="e5728-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="e5728-117">Dahil [genel](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğünü `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e5728-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e5728-118">Okuma veya değişkene derlemenizi ile birlikte çalışan herhangi bir kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="e5728-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="e5728-119">-veya-</span><span class="sxs-lookup"><span data-stu-id="e5728-119">-or-</span></span>  
  
1. <span data-ttu-id="e5728-120">Yerel bir değişken için yerleştirin `Dim` bir yordam içinde değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="e5728-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="e5728-121">Dahil etmezseniz `Public` anahtar sözcüğünü `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e5728-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e5728-122">Okuma veya değişkeninden değil, ancak yordam içinde herhangi bir yere yazmak, dışında.</span><span class="sxs-lookup"><span data-stu-id="e5728-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="e5728-123">Korumalı ve öğesine Friend erişimi</span><span class="sxs-lookup"><span data-stu-id="e5728-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="e5728-124">Bir değişken sınıfına ve tüm türetilmiş sınıfları veya kendi derlemesi için erişim düzeyini sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5728-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="e5728-125">Türetilmiş bir sınıf ya da başka bir yerde aynı bütünleştirilmiş kodundan erişim sağlayan Bu sınırlamalar birleşimi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5728-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="e5728-126">Bu birleşim birleştirerek belirttiğiniz `Protected` ve `Friend` aynı bildirimde anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="e5728-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="e5728-127">Bir değişken sınıfına ve tüm türetilmiş sınıflar içinde yalnızca erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="e5728-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="e5728-128">Bir yerde `Dim` bir sınıf içinde ancak her türlü yordam dışındaki değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="e5728-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="e5728-129">Dahil [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md) anahtar sözcüğünü `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e5728-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e5728-130">Okuma veya herhangi bir sınıf değil, ancak ondan türetilen sınıf içinde herhangi bir yere yanı sıra içinden değişkeninden yazma türetme zincirindeki herhangi bir sınıfın dışında.</span><span class="sxs-lookup"><span data-stu-id="e5728-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="e5728-131">Bir değişken aynı bütünleştirilmiş kod içinde yalnızca erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="e5728-131">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="e5728-132">Bir yerde `Dim` bir modül, sınıf veya yapı içinde ancak her türlü yordam dışındaki değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="e5728-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="e5728-133">Dahil [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) anahtar sözcüğünü `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e5728-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e5728-134">Okuma veya modül, sınıf veya yapı içinde herhangi bir yere yanı sıra herhangi bir koddan değil, ancak aynı bütünleştirilmiş kodun değişkeninden yazma derleme dışından.</span><span class="sxs-lookup"><span data-stu-id="e5728-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5728-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5728-135">Example</span></span>  
 <span data-ttu-id="e5728-136">Aşağıdaki örnek, içeren değişken bildirimlerini gösterir `Public`, `Protected`, `Friend`, `Protected Friend`, ve `Private` erişim düzeyi.</span><span class="sxs-lookup"><span data-stu-id="e5728-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="e5728-137">Dikkat edin `Dim` eklemek gerekmez, deyimi belirtir bir erişim düzeyi `Dim` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e5728-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="e5728-138">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e5728-138">.NET Framework Security</span></span>  
 <span data-ttu-id="e5728-139">Daha kısıtlayıcı bir değişken erişim düzeyi, kötü amaçlı kod hatalı yapabilirsiniz daha küçük büyük olasılıkla bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5728-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5728-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5728-140">See also</span></span>

- [<span data-ttu-id="e5728-141">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="e5728-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="e5728-142">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="e5728-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="e5728-143">Public</span><span class="sxs-lookup"><span data-stu-id="e5728-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="e5728-144">Protected</span><span class="sxs-lookup"><span data-stu-id="e5728-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="e5728-145">Friend</span><span class="sxs-lookup"><span data-stu-id="e5728-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="e5728-146">Private</span><span class="sxs-lookup"><span data-stu-id="e5728-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
