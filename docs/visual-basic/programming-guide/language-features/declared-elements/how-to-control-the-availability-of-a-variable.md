---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir değişkenin kullanılabilirliğini denetleme (Visual Basic)'
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
ms.openlocfilehash: 3fa21a804008f31da9003aa847752f749154d602
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429890"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="0db0b-103">Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0db0b-103">How to: Control the Availability of a Variable (Visual Basic)</span></span>

<span data-ttu-id="0db0b-104">Bir değişkenin kullanılabilirliğini, *erişim düzeyini* belirterek kontrol edersiniz.</span><span class="sxs-lookup"><span data-stu-id="0db0b-104">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="0db0b-105">Erişim düzeyi, hangi kodun değişkene okuma veya yazma izni olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="0db0b-105">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="0db0b-106">*Üye değişkenleri* (modül düzeyinde ve herhangi bir yordam dışında tanımlanır) varsayılan olarak genel erişim için, bu, bunlara erişebilen herhangi bir kod anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0db0b-106">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="0db0b-107">Bu, bir erişim değiştiricisi belirterek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0db0b-107">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="0db0b-108">*Yerel değişkenler* (bir yordamda tanımlanan) genel erişime sahiptir, ancak yordamındaki yalnızca kod bunlara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="0db0b-108">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="0db0b-109">Yerel bir değişkenin erişim düzeyini değiştiremezsiniz, ancak onu içeren yordamın erişim düzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0db0b-109">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="0db0b-110">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0db0b-110">For more information, see [Access levels in Visual Basic](access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="0db0b-111">Özel ve genel erişim</span><span class="sxs-lookup"><span data-stu-id="0db0b-111">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="0db0b-112">Bir değişkeni yalnızca kendi modülünün, sınıfının veya yapısının içinden erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="0db0b-112">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="0db0b-113">Değişken için [Dim ifadesini](../../../language-reference/statements/dim-statement.md) modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0db0b-113">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="0db0b-114">Deyimdeki [Private](../../../language-reference/modifiers/private.md) anahtar sözcüğünü ekleyin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="0db0b-114">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="0db0b-115">Değişkeni modülün, sınıfın veya yapının içinden herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak dışından kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0db0b-115">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="0db0b-116">Bir değişkeni, görebileceği koddan erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="0db0b-116">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="0db0b-117">Bir üye değişkeni için, `Dim` değişkenin ifadesini bir modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0db0b-117">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="0db0b-118">Deyimdeki [Public](../../../language-reference/modifiers/public.md) anahtar sözcüğünü ekleyin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="0db0b-118">Include the [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="0db0b-119">Derlemeden birlikte çalışan herhangi bir koddan değişkeni okuyabilir veya yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0db0b-119">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="0db0b-120">-veya-</span><span class="sxs-lookup"><span data-stu-id="0db0b-120">-or-</span></span>  
  
1. <span data-ttu-id="0db0b-121">Yerel bir değişken için, `Dim` değişkenin ifadesini bir yordamın içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0db0b-121">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="0db0b-122">`Public`Deyimdeki anahtar sözcüğünü eklemeyin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="0db0b-122">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="0db0b-123">Değişkeni yordamın içinden herhangi bir yerden okuyabilir veya yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0db0b-123">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="0db0b-124">Korumalı ve arkadaş erişimi</span><span class="sxs-lookup"><span data-stu-id="0db0b-124">Protected and Friend Access</span></span>  

 <span data-ttu-id="0db0b-125">Bir değişkenin erişim düzeyini sınıfı ve türetilmiş sınıflar ya da kendi derlemesi ile sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0db0b-125">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="0db0b-126">Ayrıca, herhangi bir türetilmiş sınıftaki koddan veya aynı derlemede bulunan başka bir yerde erişime izin veren bu kısıtlamaların birleşimini de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0db0b-126">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="0db0b-127">`Protected`Aynı bildirimde ve anahtar sözcüklerini birleştirerek bu birleşimi belirtirsiniz `Friend` .</span><span class="sxs-lookup"><span data-stu-id="0db0b-127">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="0db0b-128">Bir değişkeni yalnızca kendi sınıfının ve türetilmiş sınıfların içinden erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="0db0b-128">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="0db0b-129">`Dim`Değişkenin ifadesini bir sınıfın içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0db0b-129">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="0db0b-130">[Korumalı](../../../language-reference/modifiers/protected.md) anahtar sözcüğünü `Dim` deyime ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0db0b-130">Include the [Protected](../../../language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="0db0b-131">Değişkeni sınıfın içinde herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak türetme zincirindeki herhangi bir sınıfın dışından değil, onun içinden türetilmiş herhangi bir sınıf içinden.</span><span class="sxs-lookup"><span data-stu-id="0db0b-131">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="0db0b-132">Bir değişkeni yalnızca aynı derlemenin içinden erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="0db0b-132">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="0db0b-133">`Dim`Değişkenin ifadesini bir modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0db0b-133">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="0db0b-134">Deyime [arkadaş](../../../language-reference/modifiers/friend.md) anahtar sözcüğünü ekleyin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="0db0b-134">Include the [Friend](../../../language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="0db0b-135">Değişkeni modül, sınıf veya yapının içinden herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak derlemenin dışından değil, aynı derlemede bulunan herhangi bir koddan.</span><span class="sxs-lookup"><span data-stu-id="0db0b-135">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0db0b-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="0db0b-136">Example</span></span>  

 <span data-ttu-id="0db0b-137">Aşağıdaki örnek,,,, `Public` `Protected` `Friend` `Protected Friend` ve `Private` erişim düzeylerindeki değişkenlerin bildirimlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0db0b-137">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="0db0b-138">`Dim`İfade bir erişim düzeyi belirttiğinde, anahtar sözcüğünü eklemeniz gerekmediğini unutmayın `Dim` .</span><span class="sxs-lookup"><span data-stu-id="0db0b-138">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="0db0b-139">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0db0b-139">.NET Framework Security</span></span>  

 <span data-ttu-id="0db0b-140">Bir değişkenin erişim düzeyi daha kısıtlayıcıysa, kötü amaçlı kodun yanlış kullanımı ihtimaline karşı daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="0db0b-140">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db0b-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0db0b-141">See also</span></span>

- [<span data-ttu-id="0db0b-142">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="0db0b-142">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="0db0b-143">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="0db0b-143">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="0db0b-144">Genel</span><span class="sxs-lookup"><span data-stu-id="0db0b-144">Public</span></span>](../../../language-reference/modifiers/public.md)
- [<span data-ttu-id="0db0b-145">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="0db0b-145">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="0db0b-146">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="0db0b-146">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="0db0b-147">Özel</span><span class="sxs-lookup"><span data-stu-id="0db0b-147">Private</span></span>](../../../language-reference/modifiers/private.md)
