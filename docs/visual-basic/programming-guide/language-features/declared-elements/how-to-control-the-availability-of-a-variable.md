---
title: 'Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme'
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
ms.openlocfilehash: e6173a0eaa0bf84abb1979711c6df932533c5ce9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086120"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="551ec-102">Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="551ec-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>

<span data-ttu-id="551ec-103">Bir değişkenin kullanılabilirliğini, *erişim düzeyini*belirterek kontrol edersiniz.</span><span class="sxs-lookup"><span data-stu-id="551ec-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="551ec-104">Erişim düzeyi, hangi kodun değişkene okuma veya yazma izni olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="551ec-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="551ec-105">*Üye değişkenleri* (modül düzeyinde ve herhangi bir yordam dışında tanımlanır) varsayılan olarak genel erişim için, bu, bunlara erişebilen herhangi bir kod anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="551ec-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="551ec-106">Bu, bir erişim değiştiricisi belirterek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551ec-106">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="551ec-107">*Yerel değişkenler* (bir yordamda tanımlanan) genel erişime sahiptir, ancak yordamındaki yalnızca kod bunlara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="551ec-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="551ec-108">Yerel bir değişkenin erişim düzeyini değiştiremezsiniz, ancak onu içeren yordamın erişim düzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551ec-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="551ec-109">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="551ec-109">For more information, see [Access levels in Visual Basic](access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="551ec-110">Özel ve genel erişim</span><span class="sxs-lookup"><span data-stu-id="551ec-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="551ec-111">Bir değişkeni yalnızca kendi modülünün, sınıfının veya yapısının içinden erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="551ec-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="551ec-112">Değişken için [Dim ifadesini](../../../language-reference/statements/dim-statement.md) modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="551ec-112">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="551ec-113">Deyimdeki [Private](../../../language-reference/modifiers/private.md) anahtar sözcüğünü ekleyin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="551ec-113">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="551ec-114">Değişkeni modülün, sınıfın veya yapının içinden herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak dışından kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="551ec-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="551ec-115">Bir değişkeni, görebileceği koddan erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="551ec-115">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="551ec-116">Bir üye değişkeni için, `Dim` değişkenin ifadesini bir modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="551ec-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="551ec-117">Deyimdeki [Public](../../../language-reference/modifiers/public.md) anahtar sözcüğünü ekleyin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="551ec-117">Include the [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="551ec-118">Derlemeden birlikte çalışan herhangi bir koddan değişkeni okuyabilir veya yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551ec-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="551ec-119">-veya-</span><span class="sxs-lookup"><span data-stu-id="551ec-119">-or-</span></span>  
  
1. <span data-ttu-id="551ec-120">Yerel bir değişken için, `Dim` değişkenin ifadesini bir yordamın içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="551ec-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="551ec-121">`Public`Deyimdeki anahtar sözcüğünü eklemeyin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="551ec-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="551ec-122">Değişkeni yordamın içinden herhangi bir yerden okuyabilir veya yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551ec-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="551ec-123">Korumalı ve arkadaş erişimi</span><span class="sxs-lookup"><span data-stu-id="551ec-123">Protected and Friend Access</span></span>  

 <span data-ttu-id="551ec-124">Bir değişkenin erişim düzeyini sınıfı ve türetilmiş sınıflar ya da kendi derlemesi ile sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551ec-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="551ec-125">Ayrıca, herhangi bir türetilmiş sınıftaki koddan veya aynı derlemede bulunan başka bir yerde erişime izin veren bu kısıtlamaların birleşimini de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="551ec-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="551ec-126">`Protected`Aynı bildirimde ve anahtar sözcüklerini birleştirerek bu birleşimi belirtirsiniz `Friend` .</span><span class="sxs-lookup"><span data-stu-id="551ec-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="551ec-127">Bir değişkeni yalnızca kendi sınıfının ve türetilmiş sınıfların içinden erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="551ec-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="551ec-128">`Dim`Değişkenin ifadesini bir sınıfın içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="551ec-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="551ec-129">[Korumalı](../../../language-reference/modifiers/protected.md) anahtar sözcüğünü `Dim` deyime ekleyin.</span><span class="sxs-lookup"><span data-stu-id="551ec-129">Include the [Protected](../../../language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="551ec-130">Değişkeni sınıfın içinde herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak türetme zincirindeki herhangi bir sınıfın dışından değil, onun içinden türetilmiş herhangi bir sınıf içinden.</span><span class="sxs-lookup"><span data-stu-id="551ec-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="551ec-131">Bir değişkeni yalnızca aynı derlemenin içinden erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="551ec-131">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="551ec-132">`Dim`Değişkenin ifadesini bir modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="551ec-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="551ec-133">Deyime [arkadaş](../../../language-reference/modifiers/friend.md) anahtar sözcüğünü ekleyin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="551ec-133">Include the [Friend](../../../language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="551ec-134">Değişkeni modül, sınıf veya yapının içinden herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak derlemenin dışından değil, aynı derlemede bulunan herhangi bir koddan.</span><span class="sxs-lookup"><span data-stu-id="551ec-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="551ec-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="551ec-135">Example</span></span>  

 <span data-ttu-id="551ec-136">Aşağıdaki örnek,,,, `Public` `Protected` `Friend` `Protected Friend` ve `Private` erişim düzeylerindeki değişkenlerin bildirimlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="551ec-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="551ec-137">`Dim`İfade bir erişim düzeyi belirttiğinde, anahtar sözcüğünü eklemeniz gerekmediğini unutmayın `Dim` .</span><span class="sxs-lookup"><span data-stu-id="551ec-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="551ec-138">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="551ec-138">.NET Framework Security</span></span>  

 <span data-ttu-id="551ec-139">Bir değişkenin erişim düzeyi daha kısıtlayıcıysa, kötü amaçlı kodun yanlış kullanımı ihtimaline karşı daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="551ec-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="551ec-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="551ec-140">See also</span></span>

- [<span data-ttu-id="551ec-141">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="551ec-141">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="551ec-142">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="551ec-142">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="551ec-143">Geneldir</span><span class="sxs-lookup"><span data-stu-id="551ec-143">Public</span></span>](../../../language-reference/modifiers/public.md)
- [<span data-ttu-id="551ec-144">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="551ec-144">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="551ec-145">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="551ec-145">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="551ec-146">Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="551ec-146">Private</span></span>](../../../language-reference/modifiers/private.md)
