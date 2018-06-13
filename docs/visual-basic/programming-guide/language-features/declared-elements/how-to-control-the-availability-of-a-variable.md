---
title: 'Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme (Visual Basic)'
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
ms.openlocfilehash: 27ee5d3405ea24c0754cffa85e9b89b2ac561e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652174"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="ce38a-102">Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce38a-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="ce38a-103">Belirterek bir değişkenin kullanılabilirliğini denetleme kendi *erişim düzeyine*.</span><span class="sxs-lookup"><span data-stu-id="ce38a-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="ce38a-104">Hangi kod okuma veya değişkenine yazma izni olan erişim düzeyini belirler.</span><span class="sxs-lookup"><span data-stu-id="ce38a-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
-   <span data-ttu-id="ce38a-105">*Üye değişkenleri* (Modül düzeyinde ve herhangi bir yordam dışında tanımlanan) görebileceği herhangi bir kod erişebilmeniz anlamına gelen genel erişim için varsayılan.</span><span class="sxs-lookup"><span data-stu-id="ce38a-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="ce38a-106">Bu, bir erişim değiştiricisi belirleyerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce38a-106">You can change this by specifying an access modifier.</span></span>  
  
-   <span data-ttu-id="ce38a-107">*Yerel değişkenler* (yordam içinde tanımlanmıştır) yalnızca kendi yordamı içindeki kod erişmesine olmamakla birlikte, ismen genel erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="ce38a-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="ce38a-108">Yerel değişkene erişim düzeyini değiştiremezsiniz, ancak içerdiği yordamı erişim düzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce38a-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="ce38a-109">Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ce38a-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="ce38a-110">Özel ve genel erişim</span><span class="sxs-lookup"><span data-stu-id="ce38a-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="ce38a-111">Bir değişken modülü, sınıf veya yapı içinde yalnızca erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="ce38a-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1.  <span data-ttu-id="ce38a-112">Yer [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) modülü, sınıf veya yapı içinde ancak herhangi bir yordam dışında değişken için.</span><span class="sxs-lookup"><span data-stu-id="ce38a-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="ce38a-113">Dahil [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcük `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ce38a-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ce38a-114">Okuma veya modül, sınıf veya yapı içinde istediğiniz yere değiştirebilir, ancak değişkeninden yazma dışı.</span><span class="sxs-lookup"><span data-stu-id="ce38a-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="ce38a-115">Bir değişken görebileceğiniz herhangi bir koddan erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="ce38a-115">To make a variable accessible from any code that can see it</span></span>  
  
1.  <span data-ttu-id="ce38a-116">Üye değişkeni için yerleştirin `Dim` modülü, sınıf veya yapı içinde ancak herhangi bir yordam dışında değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ce38a-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="ce38a-117">Dahil [ortak](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcük `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ce38a-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ce38a-118">Okuma ya da değişkenine derlemenizi ile birlikte çalışan herhangi bir kodda yazma.</span><span class="sxs-lookup"><span data-stu-id="ce38a-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="ce38a-119">-veya-</span><span class="sxs-lookup"><span data-stu-id="ce38a-119">-or-</span></span>  
  
1.  <span data-ttu-id="ce38a-120">Yerel bir değişken için yerleştirin `Dim` yordam içindeki değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ce38a-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2.  <span data-ttu-id="ce38a-121">İçermeyen `Public` anahtar sözcük `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ce38a-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ce38a-122">Okuma veya yordam içinde istediğiniz yere değiştirebilir, ancak değişkeninden yazma dışı.</span><span class="sxs-lookup"><span data-stu-id="ce38a-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="ce38a-123">Korumalı Friend erişim</span><span class="sxs-lookup"><span data-stu-id="ce38a-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="ce38a-124">Bir değişken, sınıf ve türetilen tüm sınıflar ya da kendi derleme erişim düzeyini sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce38a-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="ce38a-125">Türetilmiş bir sınıf veya başka bir yerde aynı bütünleştirilmiş kodundan erişim sağlayan aşağıdaki sınırlamalara birleşimi de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce38a-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="ce38a-126">Bu birleşim birleştirerek belirttiğiniz `Protected` ve `Friend` aynı bildiriminde anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="ce38a-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="ce38a-127">Bir değişken, sınıf ve türetilen tüm sınıflar içinde yalnızca erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="ce38a-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1.  <span data-ttu-id="ce38a-128">Yer `Dim` ifade değişkenin bir sınıf içinde ancak herhangi bir yordam dışında.</span><span class="sxs-lookup"><span data-stu-id="ce38a-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="ce38a-129">Dahil [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md) anahtar sözcük `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ce38a-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ce38a-130">Okuma veya dışarı değiştirebilir, ancak herhangi bir sınıf türetilmiş sınıf içinde istediğiniz yere yanı sıra içinden değişkeninden yazma türetme zincirindeki herhangi bir sınıf dışında.</span><span class="sxs-lookup"><span data-stu-id="ce38a-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="ce38a-131">Bir değişken aynı bütünleştirilmiş kod içinde yalnızca erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="ce38a-131">To make a variable accessible only from within the same assembly</span></span>  
  
1.  <span data-ttu-id="ce38a-132">Yer `Dim` modülü, sınıf veya yapı içinde ancak herhangi bir yordam dışında değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ce38a-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="ce38a-133">Dahil [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) anahtar sözcük `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ce38a-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="ce38a-134">Okuma veya modül, sınıf veya yapı içinde istediğiniz yere yanı sıra herhangi bir koddan aynı bütünleştirilmiş kodda değiştirebilir, ancak değişkeninden yazma derleme dışına.</span><span class="sxs-lookup"><span data-stu-id="ce38a-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce38a-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce38a-135">Example</span></span>  
 <span data-ttu-id="ce38a-136">Aşağıdaki örnek, değişkenlerle bildirimlerini gösterir `Public`, `Protected`, `Friend`, `Protected Friend`, ve `Private` erişim düzeyini.</span><span class="sxs-lookup"><span data-stu-id="ce38a-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="ce38a-137">Unutmayın `Dim` deyimi bir erişim düzeyini belirtir, dahil etmek zorunda değildir `Dim` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ce38a-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="ce38a-138">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ce38a-138">.NET Framework Security</span></span>  
 <span data-ttu-id="ce38a-139">Daha fazla kısıtlayıcı bir değişken erişim düzeyi, kötü amaçlı kod hatalı yapabilirsiniz küçük büyük olasılıkla bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ce38a-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce38a-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce38a-140">See Also</span></span>  
 [<span data-ttu-id="ce38a-141">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="ce38a-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="ce38a-142">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="ce38a-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="ce38a-143">Public</span><span class="sxs-lookup"><span data-stu-id="ce38a-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="ce38a-144">Protected</span><span class="sxs-lookup"><span data-stu-id="ce38a-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="ce38a-145">Friend</span><span class="sxs-lookup"><span data-stu-id="ce38a-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="ce38a-146">Private</span><span class="sxs-lookup"><span data-stu-id="ce38a-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
