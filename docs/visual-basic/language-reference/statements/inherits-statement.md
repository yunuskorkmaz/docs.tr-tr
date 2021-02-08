---
description: 'Daha fazla bilgi edinin: Inherits ekstresi'
title: Inherits Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: fba574ec207b384c1e7219341526a4a89c8a619c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768928"
---
# <a name="inherits-statement"></a><span data-ttu-id="ad1e3-103">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="ad1e3-103">Inherits Statement</span></span>

<span data-ttu-id="ad1e3-104">Geçerli sınıfın ya da arabirimin öznitelikleri, değişkenleri, özellikleri, yordamları ve olayları başka bir sınıf veya arabirim kümesinden devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-104">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad1e3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ad1e3-105">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="ad1e3-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ad1e3-106">Parts</span></span>  
  
|<span data-ttu-id="ad1e3-107">Süre</span><span class="sxs-lookup"><span data-stu-id="ad1e3-107">Term</span></span>|<span data-ttu-id="ad1e3-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="ad1e3-108">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="ad1e3-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-109">Required.</span></span> <span data-ttu-id="ad1e3-110">Bu sınıfın türetildiği sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-110">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="ad1e3-111">-veya-</span><span class="sxs-lookup"><span data-stu-id="ad1e3-111">-or-</span></span><br /><br /> <span data-ttu-id="ad1e3-112">Bu arabirimin türettiği arabirimlerin adları.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-112">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="ad1e3-113">Birden çok adı ayırmak için virgül kullanın.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-113">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad1e3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad1e3-114">Remarks</span></span>  

 <span data-ttu-id="ad1e3-115">Kullanıldıysa, `Inherits` bir sınıf veya arabirim tanımında deyimin ilk boş olmayan, yorum olmayan satırı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-115">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="ad1e3-116">Hemen `Class` veya `Interface` ifadesini izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-116">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="ad1e3-117">`Inherits`Yalnızca bir sınıf veya arabirim için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-117">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="ad1e3-118">Bu, devralma için bildirim bağlamının kaynak dosya, ad alanı, yapı, modül, yordam veya blok olamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-118">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ad1e3-119">Kurallar</span><span class="sxs-lookup"><span data-stu-id="ad1e3-119">Rules</span></span>  
  
- <span data-ttu-id="ad1e3-120">**Sınıf devralma.**</span><span class="sxs-lookup"><span data-stu-id="ad1e3-120">**Class Inheritance.**</span></span> <span data-ttu-id="ad1e3-121">Bir sınıf, ifadesini kullanıyorsa `Inherits` yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-121">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="ad1e3-122">Bir sınıf, içinde iç içe geçmiş bir sınıftan devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-122">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="ad1e3-123">**Arabirim devralma.**</span><span class="sxs-lookup"><span data-stu-id="ad1e3-123">**Interface Inheritance.**</span></span> <span data-ttu-id="ad1e3-124">Bir arabirim, ifadesini kullanıyorsa `Inherits` , bir veya daha fazla temel arabirim belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-124">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="ad1e3-125">Her biri aynı ada sahip bir üye tanımlasa bile iki arabirimden devralma yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-125">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="ad1e3-126">Bunu yaparsanız, uygulama kodunun hangi üyeyi uygulamakta olduğunu belirtmek için ad nitelemesini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-126">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="ad1e3-127">Arabirim, daha kısıtlayıcı erişim düzeyine sahip başka bir arabirimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-127">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="ad1e3-128">Örneğin, bir `Public` arabirim `Friend` arabiriminden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-128">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="ad1e3-129">Arabirim, içinde iç içe geçmiş bir arabirimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-129">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="ad1e3-130">.NET Framework sınıf devralma örneği <xref:System.ArgumentException> , sınıfından devralan sınıftır <xref:System.SystemException> .</span><span class="sxs-lookup"><span data-stu-id="ad1e3-130">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="ad1e3-131">Bu, <xref:System.ArgumentException> özelliği ve yöntemi gibi sistem özel durumları için gerekli tüm önceden tanımlanmış özellikleri ve yordamları sağlar <xref:System.Exception.Message%2A> <xref:System.Exception.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="ad1e3-131">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="ad1e3-132">.NET Framework arabirim devralım örneği <xref:System.Collections.ICollection> arabiriminden devralan arabirimdir <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="ad1e3-132">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="ad1e3-133">Bu, <xref:System.Collections.ICollection> bir koleksiyonun çapraz geçişini yapmak için gereken Numaralandırıcı tanımını devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-133">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad1e3-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad1e3-134">Example</span></span>  

 <span data-ttu-id="ad1e3-135">Aşağıdaki örnek, adlı `Inherits` bir sınıfın `thisClass` adlı bir temel sınıfın tüm üyelerini nasıl devralmasını göstermek için ifadesini kullanır `anotherClass` .</span><span class="sxs-lookup"><span data-stu-id="ad1e3-135">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="ad1e3-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad1e3-136">Example</span></span>  

 <span data-ttu-id="ad1e3-137">Aşağıdaki örnek, birden çok arabirimin devralınmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-137">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="ad1e3-138">Artık adlı arabirim,, `thisInterface` ve ' deki tüm tanımları içerir, <xref:System.IComparable> <xref:System.IDisposable> ve <xref:System.IFormattable> devralınan üyelerin, iki nesnenin türüne özgü karşılaştırmasına, ayrılan kaynakları serbest bırakarak ve bir nesnenin değerini olarak ifade eder `String` .</span><span class="sxs-lookup"><span data-stu-id="ad1e3-138">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="ad1e3-139">Uygulayan bir sınıf `thisInterface` , her temel arabirimin her üyesini uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-139">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad1e3-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad1e3-140">See also</span></span>

- [<span data-ttu-id="ad1e3-141">MustInherit</span><span class="sxs-lookup"><span data-stu-id="ad1e3-141">MustInherit</span></span>](../modifiers/mustinherit.md)
- [<span data-ttu-id="ad1e3-142">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="ad1e3-142">NotInheritable</span></span>](../modifiers/notinheritable.md)
- [<span data-ttu-id="ad1e3-143">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="ad1e3-143">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="ad1e3-144">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="ad1e3-144">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="ad1e3-145">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ad1e3-145">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
