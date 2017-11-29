---
title: Inherits Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae9ba54c3fd1ec3332c9f6260bc19a1293270ad8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="inherits-statement"></a><span data-ttu-id="e81d1-102">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="e81d1-102">Inherits Statement</span></span>
<span data-ttu-id="e81d1-103">Geçerli sınıf veya başka bir sınıf veya arabirim kümesine öznitelikleri, değişkenleri, özellikleri, yordamlar ve olayları devralmak için arabirimi neden olur.</span><span class="sxs-lookup"><span data-stu-id="e81d1-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e81d1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e81d1-104">Syntax</span></span>  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="e81d1-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e81d1-105">Parts</span></span>  
  
|<span data-ttu-id="e81d1-106">Terim</span><span class="sxs-lookup"><span data-stu-id="e81d1-106">Term</span></span>|<span data-ttu-id="e81d1-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="e81d1-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="e81d1-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e81d1-108">Required.</span></span> <span data-ttu-id="e81d1-109">Bu sınıf türetilen sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="e81d1-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="e81d1-110">veya</span><span class="sxs-lookup"><span data-stu-id="e81d1-110">-or-</span></span><br /><br /> <span data-ttu-id="e81d1-111">Bu arabirim türetilen arabirimleri adları.</span><span class="sxs-lookup"><span data-stu-id="e81d1-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="e81d1-112">Birden çok ad ayırmak için virgül kullanın.</span><span class="sxs-lookup"><span data-stu-id="e81d1-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e81d1-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e81d1-113">Remarks</span></span>  
 <span data-ttu-id="e81d1-114">Kullandıysanız, `Inherits` deyimi bir sınıf veya arabirim tanımı ilk boş olmayan ve yorum olmayan satır olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e81d1-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="e81d1-115">Hemen izlemeniz gereken `Class` veya `Interface` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e81d1-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="e81d1-116">Kullanabileceğiniz `Inherits` yalnızca bir sınıf veya arabirim olarak.</span><span class="sxs-lookup"><span data-stu-id="e81d1-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="e81d1-117">Başka bir deyişle, bir devralma bildirimi bağlamının bir kaynak dosyasını, ad alanı, yapısı, modülü, yordam veya blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="e81d1-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e81d1-118">Kurallar</span><span class="sxs-lookup"><span data-stu-id="e81d1-118">Rules</span></span>  
  
-   <span data-ttu-id="e81d1-119">**Sınıf devralma.**</span><span class="sxs-lookup"><span data-stu-id="e81d1-119">**Class Inheritance.**</span></span> <span data-ttu-id="e81d1-120">Bir sınıf kullanıyorsa `Inherits` deyimi, yalnızca bir taban sınıf belirtin.</span><span class="sxs-lookup"><span data-stu-id="e81d1-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="e81d1-121">Bir sınıf içinde iç içe bir sınıftan devralınan olamaz.</span><span class="sxs-lookup"><span data-stu-id="e81d1-121">A class cannot inherit from a class nested within it.</span></span>  
  
-   <span data-ttu-id="e81d1-122">**Devralma arabirim.**</span><span class="sxs-lookup"><span data-stu-id="e81d1-122">**Interface Inheritance.**</span></span> <span data-ttu-id="e81d1-123">Arabirim kullanıyorsa `Inherits` deyimi, bir veya daha fazla temel arabirimleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e81d1-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="e81d1-124">Bunların hepsi aynı ada sahip bir üye tanımlayın olsa bile, iki arabirimlerinden devralabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e81d1-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="e81d1-125">Bunu yapmak, uygulama kodu ad niteliği uyguladığı hangi üye belirtmek için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e81d1-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="e81d1-126">Bir arabirim daha kısıtlayıcı erişim düzeyine sahip başka bir arabirim devralınmalıdır olamaz.</span><span class="sxs-lookup"><span data-stu-id="e81d1-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="e81d1-127">Örneğin, bir `Public` olamaz arabirimi devralan bir `Friend` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e81d1-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="e81d1-128">Bir arabirim içinde iç içe bir arabirimden devralan olamaz.</span><span class="sxs-lookup"><span data-stu-id="e81d1-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="e81d1-129">.NET Framework sınıf devralma örneğidir <xref:System.ArgumentException> devraldığı sınıfı <xref:System.SystemException> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e81d1-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="e81d1-130">Bu sağlayan <xref:System.ArgumentException> tüm gibi gerekli sistem durumlarını tarafından yordamlar ve önceden tanımlanmış özellikler <xref:System.Exception.Message%2A> özelliği ve <xref:System.Exception.ToString%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e81d1-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="e81d1-131">.NET Framework'teki arabirimi devralma örneğidir <xref:System.Collections.ICollection> devraldığı arabirimi <xref:System.Collections.IEnumerable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e81d1-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="e81d1-132">Bu neden <xref:System.Collections.ICollection> koleksiyonu geçiş için gereken Numaralandırıcı tanımını devralmak için.</span><span class="sxs-lookup"><span data-stu-id="e81d1-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e81d1-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="e81d1-133">Example</span></span>  
 <span data-ttu-id="e81d1-134">Aşağıdaki örnek kullanır `Inherits` nasıl adlı bir sınıf göstermek için deyimi `thisClass` adlı bir taban sınıfın tüm üyeleri devrettiği `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="e81d1-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="e81d1-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="e81d1-135">Example</span></span>  
 <span data-ttu-id="e81d1-136">Aşağıdaki örnek, birden çok arabirimlerinin devralma gösterir.</span><span class="sxs-lookup"><span data-stu-id="e81d1-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 <span data-ttu-id="e81d1-137">Adlı arabirim `thisInterface` artık tüm tanımlarında içerir <xref:System.IComparable>, <xref:System.IDisposable>, ve <xref:System.IFormattable> devralınan üyeleri sağlamak sırasıyla iki nesne türüne özgü karşılaştırma için serbest arabirimleri ayrılan kaynaklar ve bir nesne olarak değeri ifade bir `String`.</span><span class="sxs-lookup"><span data-stu-id="e81d1-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="e81d1-138">Uygulayan bir sınıf `thisInterface` her üyesinin her temel arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e81d1-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e81d1-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e81d1-139">See Also</span></span>  
 [<span data-ttu-id="e81d1-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="e81d1-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="e81d1-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="e81d1-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="e81d1-142">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="e81d1-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="e81d1-143">Devralma temelleri</span><span class="sxs-lookup"><span data-stu-id="e81d1-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="e81d1-144">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e81d1-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
