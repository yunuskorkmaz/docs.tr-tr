---
title: Inherits Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 6e6e9cc9210232059210862f2bda691c57b372d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353234"
---
# <a name="inherits-statement"></a><span data-ttu-id="bc85e-102">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="bc85e-102">Inherits Statement</span></span>
<span data-ttu-id="bc85e-103">Geçerli sınıfın ya da arabirimin öznitelikleri, değişkenleri, özellikleri, yordamları ve olayları başka bir sınıf veya arabirim kümesinden devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc85e-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc85e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc85e-104">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="bc85e-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="bc85e-105">Parts</span></span>  
  
|<span data-ttu-id="bc85e-106">Terim</span><span class="sxs-lookup"><span data-stu-id="bc85e-106">Term</span></span>|<span data-ttu-id="bc85e-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="bc85e-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="bc85e-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bc85e-108">Required.</span></span> <span data-ttu-id="bc85e-109">Bu sınıfın türetildiği sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="bc85e-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="bc85e-110">veya</span><span class="sxs-lookup"><span data-stu-id="bc85e-110">-or-</span></span><br /><br /> <span data-ttu-id="bc85e-111">Bu arabirimin türettiği arabirimlerin adları.</span><span class="sxs-lookup"><span data-stu-id="bc85e-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="bc85e-112">Birden çok adı ayırmak için virgül kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc85e-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc85e-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc85e-113">Remarks</span></span>  
 <span data-ttu-id="bc85e-114">Kullanıldıysa, `Inherits` deyimin bir sınıf veya arabirim tanımında ilk boş olmayan, yorum olmayan satırı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc85e-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="bc85e-115">`Class` veya `Interface` deyiminizi hemen izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="bc85e-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="bc85e-116">Yalnızca bir sınıf veya arabirimde `Inherits` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc85e-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="bc85e-117">Bu, devralma için bildirim bağlamının kaynak dosya, ad alanı, yapı, modül, yordam veya blok olamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bc85e-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="bc85e-118">Kurallar</span><span class="sxs-lookup"><span data-stu-id="bc85e-118">Rules</span></span>  
  
- <span data-ttu-id="bc85e-119">**Sınıf devralma.**</span><span class="sxs-lookup"><span data-stu-id="bc85e-119">**Class Inheritance.**</span></span> <span data-ttu-id="bc85e-120">Bir sınıf `Inherits` ifadesini kullanıyorsa yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc85e-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="bc85e-121">Bir sınıf, içinde iç içe geçmiş bir sınıftan devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="bc85e-121">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="bc85e-122">**Arabirim devralma.**</span><span class="sxs-lookup"><span data-stu-id="bc85e-122">**Interface Inheritance.**</span></span> <span data-ttu-id="bc85e-123">Bir arabirim `Inherits` ifadesini kullanıyorsa, bir veya daha fazla temel arabirim belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc85e-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="bc85e-124">Her biri aynı ada sahip bir üye tanımlasa bile iki arabirimden devralma yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc85e-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="bc85e-125">Bunu yaparsanız, uygulama kodunun hangi üyeyi uygulamakta olduğunu belirtmek için ad nitelemesini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc85e-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="bc85e-126">Arabirim, daha kısıtlayıcı erişim düzeyine sahip başka bir arabirimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="bc85e-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="bc85e-127">Örneğin, bir `Public` arabirimi `Friend` arabiriminden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="bc85e-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="bc85e-128">Arabirim, içinde iç içe geçmiş bir arabirimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="bc85e-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="bc85e-129">.NET Framework sınıf devralma örneği, <xref:System.SystemException> sınıfından devralan <xref:System.ArgumentException> sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="bc85e-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="bc85e-130">Bu, <xref:System.Exception.Message%2A> özelliği ve <xref:System.Exception.ToString%2A> yöntemi gibi sistem özel durumları için gerekli tüm önceden tanımlanmış özellikleri ve yordamları <xref:System.ArgumentException> sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc85e-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="bc85e-131">.NET Framework bir arabirim devralım örneği, <xref:System.Collections.IEnumerable> arabiriminden devralan <xref:System.Collections.ICollection> arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="bc85e-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="bc85e-132">Bu <xref:System.Collections.ICollection>, bir koleksiyonun çapraz geçişini yapmak için gereken Numaralandırıcı tanımını devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc85e-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc85e-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc85e-133">Example</span></span>  
 <span data-ttu-id="bc85e-134">Aşağıdaki örnek, `thisClass` adlı bir sınıfın `anotherClass`adlı bir temel sınıfın tüm üyelerini nasıl devralmasını göstermek için `Inherits` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc85e-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="bc85e-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc85e-135">Example</span></span>  
 <span data-ttu-id="bc85e-136">Aşağıdaki örnek, birden çok arabirimin devralınmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc85e-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="bc85e-137">`thisInterface` adlı arabirim artık, devralınan üyelerin,, ayrılmış kaynakları serbest bırakarak ve bir nesnenin değerini bir `String`ifade etmek için sırasıyla, <xref:System.IComparable>, <xref:System.IDisposable>ve <xref:System.IFormattable> arabirimlerinden tüm tanımları içerir.</span><span class="sxs-lookup"><span data-stu-id="bc85e-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="bc85e-138">`thisInterface` uygulayan bir sınıf, her temel arabirimin her üyesini uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc85e-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc85e-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc85e-139">See also</span></span>

- [<span data-ttu-id="bc85e-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="bc85e-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="bc85e-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="bc85e-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="bc85e-142">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="bc85e-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="bc85e-143">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="bc85e-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="bc85e-144">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bc85e-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
