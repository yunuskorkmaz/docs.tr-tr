---
title: Inherits deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: c39272d53fea136c83a5a09444b65a594fe3b7a7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625518"
---
# <a name="inherits-statement"></a><span data-ttu-id="b7c98-102">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="b7c98-102">Inherits Statement</span></span>
<span data-ttu-id="b7c98-103">Geçerli sınıfın ya da arabirimin öznitelikleri, değişkenleri, özellikleri, yordamları ve olayları başka bir sınıf veya arabirim kümesini devralan neden olur.</span><span class="sxs-lookup"><span data-stu-id="b7c98-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7c98-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7c98-104">Syntax</span></span>  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="b7c98-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="b7c98-105">Parts</span></span>  
  
|<span data-ttu-id="b7c98-106">Terim</span><span class="sxs-lookup"><span data-stu-id="b7c98-106">Term</span></span>|<span data-ttu-id="b7c98-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="b7c98-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="b7c98-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b7c98-108">Required.</span></span> <span data-ttu-id="b7c98-109">Bu sınıfın türetildiği sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="b7c98-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="b7c98-110">-veya-</span><span class="sxs-lookup"><span data-stu-id="b7c98-110">-or-</span></span><br /><br /> <span data-ttu-id="b7c98-111">Bu arabirim türetildiği arayüzlerin adları.</span><span class="sxs-lookup"><span data-stu-id="b7c98-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="b7c98-112">Birden çok adını ayırmak için virgül kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7c98-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7c98-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7c98-113">Remarks</span></span>  
 <span data-ttu-id="b7c98-114">Kullandıysanız, `Inherits` deyimi, bir sınıf veya arabirim tanımı ilk boş olmayan, olmayan açıklama satırı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7c98-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="b7c98-115">Hemen izlemelidir `Class` veya `Interface` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b7c98-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="b7c98-116">Kullanabileceğiniz `Inherits` yalnızca bir sınıf veya arabirim olarak.</span><span class="sxs-lookup"><span data-stu-id="b7c98-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="b7c98-117">Başka bir deyişle, bir devralma için bildirim içeriğinin bir kaynak dosyası, ad alanı, yapı, modül, yordam veya blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="b7c98-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b7c98-118">Kurallar</span><span class="sxs-lookup"><span data-stu-id="b7c98-118">Rules</span></span>  
  
- <span data-ttu-id="b7c98-119">**Sınıf devralma.**</span><span class="sxs-lookup"><span data-stu-id="b7c98-119">**Class Inheritance.**</span></span> <span data-ttu-id="b7c98-120">Bir sınıf kullanıyorsa `Inherits` deyimi, yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7c98-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="b7c98-121">Bir sınıf içinde iç içe geçmiş bir sınıfı devralamaz.</span><span class="sxs-lookup"><span data-stu-id="b7c98-121">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="b7c98-122">**Devralma arabirim.**</span><span class="sxs-lookup"><span data-stu-id="b7c98-122">**Interface Inheritance.**</span></span> <span data-ttu-id="b7c98-123">Bir arabirim kullanıyorsa `Inherits` deyimi, bir veya daha fazla temel arabirimde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7c98-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="b7c98-124">Bunların hepsi aynı ada sahip bir üye tanımlarsanız bile iki ara birimden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="b7c98-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="b7c98-125">Bunu yaparsanız uyguladığı üye belirtmek için uygulanan kodun ad niteliği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7c98-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="b7c98-126">Bir arabirim daha kısıtlayıcı bir erişim düzeyi olan başka bir arabirimden devralamaz.</span><span class="sxs-lookup"><span data-stu-id="b7c98-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="b7c98-127">Örneğin, bir `Public` arabirimi öğesinden özellik devralamaz bir `Friend` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b7c98-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="b7c98-128">Bir arabirim, kendi içinde iç içe bir arabirimden devralamaz.</span><span class="sxs-lookup"><span data-stu-id="b7c98-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="b7c98-129">.NET Framework içinde sınıf Devralmanın örneğidir <xref:System.ArgumentException> öğesinden devralan sınıf <xref:System.SystemException> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b7c98-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="b7c98-130">Bu sağlayan <xref:System.ArgumentException> önceden tanımlanmış özellikler ve yordamlar gibi sistem özel durumların gerekli <xref:System.Exception.Message%2A> özelliği ve <xref:System.Exception.ToString%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b7c98-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="b7c98-131">.NET Framework'teki arabirimi devralma örneğidir <xref:System.Collections.ICollection> öğesinden devralan bir arayüzü <xref:System.Collections.IEnumerable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b7c98-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="b7c98-132">Bu neden <xref:System.Collections.ICollection> bir koleksiyonu geçirmek için gereken Numaralandırıcı tanımını devralmak için.</span><span class="sxs-lookup"><span data-stu-id="b7c98-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7c98-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7c98-133">Example</span></span>  
 <span data-ttu-id="b7c98-134">Aşağıdaki örnekte `Inherits` nasıl adlı bir sınıf gösterilecek deyimi `thisClass` adlı bir temel sınıf tüm üyelerini devralabilir `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="b7c98-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="b7c98-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7c98-135">Example</span></span>  
 <span data-ttu-id="b7c98-136">Aşağıdaki örnek, birden çok arabirim devralma gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7c98-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="b7c98-137">Adlı arabirim `thisInterface` artık tüm tanımlar içeren <xref:System.IComparable>, <xref:System.IDisposable>, ve <xref:System.IFormattable> devralınan üyeleri sağlamak sırasıyla iki nesne, türe özgü karşılaştırma için serbest arabirimleri ayrılan kaynaklar ve bir nesne olarak değerini ifade bir `String`.</span><span class="sxs-lookup"><span data-stu-id="b7c98-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="b7c98-138">Uygulayan bir sınıf `thisInterface` her üyesi temel her arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7c98-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c98-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7c98-139">See also</span></span>

- [<span data-ttu-id="b7c98-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="b7c98-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="b7c98-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="b7c98-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="b7c98-142">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b7c98-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="b7c98-143">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="b7c98-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="b7c98-144">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b7c98-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
