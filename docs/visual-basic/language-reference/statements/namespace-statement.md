---
description: 'Daha fazla bilgi edinin: ad alanı ekstresi'
title: Namespace Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 2c315947a26f72a90e03bc1f4bf1b5f647866b33
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768863"
---
# <a name="namespace-statement"></a><span data-ttu-id="84557-103">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="84557-103">Namespace Statement</span></span>

<span data-ttu-id="84557-104">Bir ad alanının adını bildirir ve bildirimi takip eden kaynak kodunun bu ad alanı içinde derlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="84557-104">Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84557-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="84557-105">Syntax</span></span>  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a><span data-ttu-id="84557-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="84557-106">Parts</span></span>  

 <span data-ttu-id="84557-107">Genel</span><span class="sxs-lookup"><span data-stu-id="84557-107">Global</span></span>  
 <span data-ttu-id="84557-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="84557-108">Optional.</span></span> <span data-ttu-id="84557-109">Projenizin kök ad alanından bir ad alanı tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="84557-109">Allows you to define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="84557-110">Bkz. [Visual Basic ad alanları](../../programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="84557-110">See [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 `name`  
 <span data-ttu-id="84557-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="84557-111">Required.</span></span> <span data-ttu-id="84557-112">Ad alanını tanımlayan benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="84557-112">A unique name that identifies the namespace.</span></span> <span data-ttu-id="84557-113">Geçerli bir Visual Basic tanımlayıcısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="84557-113">Must be a valid Visual Basic identifier.</span></span> <span data-ttu-id="84557-114">Daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="84557-114">For more information, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `componenttypes`  
 <span data-ttu-id="84557-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="84557-115">Optional.</span></span> <span data-ttu-id="84557-116">Ad alanını oluşturan öğeler.</span><span class="sxs-lookup"><span data-stu-id="84557-116">Elements that make up the namespace.</span></span> <span data-ttu-id="84557-117">Bunlar arasında, numaralandırmalar, yapılar, arabirimler, sınıflar, modüller, temsilciler ve diğer ad alanları bunlarla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="84557-117">These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.</span></span>  
  
 `End Namespace`  
 <span data-ttu-id="84557-118">Bir `Namespace` bloğu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="84557-118">Terminates a `Namespace` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84557-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84557-119">Remarks</span></span>  

 <span data-ttu-id="84557-120">Ad alanları bir kuruluş sistemi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84557-120">Namespaces are used as an organizational system.</span></span> <span data-ttu-id="84557-121">Diğer programlar ve uygulamalar tarafından sunulan programlama öğelerini sınıflandırmak ve sunmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="84557-121">They provide a way to classify and present programming elements that are exposed to other programs and applications.</span></span> <span data-ttu-id="84557-122">Bir ad alanı, bir sınıf veya yapının olduğu anlamda bir *tür* değildir; bir ad alanı veri türüne sahip olacak bir programlama öğesi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="84557-122">Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.</span></span>  
  
 <span data-ttu-id="84557-123">Bir deyimden sonra belirtilen tüm programlama öğeleri `Namespace` Bu ad alanına ait.</span><span class="sxs-lookup"><span data-stu-id="84557-123">All programming elements declared after a `Namespace` statement belong to that namespace.</span></span> <span data-ttu-id="84557-124">Visual Basic, bir `End Namespace` deyimle veya başka bir deyimle karşılaşana kadar öğeleri en son tanımlanan ad alanıyla derlemeye devam eder `Namespace` .</span><span class="sxs-lookup"><span data-stu-id="84557-124">Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.</span></span>  
  
 <span data-ttu-id="84557-125">Bir ad alanı zaten tanımlanmışsa, projeniz dışında bile buna programlama öğeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84557-125">If a namespace is already defined, even outside your project, you can add programming elements to it.</span></span> <span data-ttu-id="84557-126">Bunu yapmak için, bu `Namespace` ad alanına öğeleri derlemek üzere Visual Basic yönlendirmek üzere bir ifade kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="84557-126">To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.</span></span>  
  
 <span data-ttu-id="84557-127">Bir `Namespace` ifadesini yalnızca dosya veya ad alanı düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84557-127">You can use a `Namespace` statement only at the file or namespace level.</span></span> <span data-ttu-id="84557-128">Diğer bir deyişle, bir ad alanı için *Bildirim bağlamı* bir kaynak dosyası veya başka bir ad alanı olmalıdır ve bir sınıf, yapı, modül, arabirim veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="84557-128">This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure.</span></span> <span data-ttu-id="84557-129">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="84557-129">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="84557-130">Bir ad alanını başka bir ad alanı içinde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84557-130">You can declare one namespace within another.</span></span> <span data-ttu-id="84557-131">Bildirebileceğiniz iç içe geçme düzeylerine yönelik kesin bir sınır yoktur, ancak başka bir kod, iç içe geçmiş hiyerarşisinde belirtilen tüm ad alanı adlarını içeren bir nitelik dizesi kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="84557-131">There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.</span></span>  
  
## <a name="access-level"></a><span data-ttu-id="84557-132">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="84557-132">Access Level</span></span>  

 <span data-ttu-id="84557-133">Ad alanları erişim düzeyine sahip oldukları gibi değerlendirilir `Public` .</span><span class="sxs-lookup"><span data-stu-id="84557-133">Namespaces are treated as if they have a `Public` access level.</span></span> <span data-ttu-id="84557-134">Bir ad alanına, aynı projede yer alan koddan, projeye başvuran diğer projelerden ve projeden oluşturulan herhangi bir derlemeden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="84557-134">A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.</span></span>  
  
 <span data-ttu-id="84557-135">Ad alanı düzeyinde tanımlanan, bir ad alanında anlamı olan, ancak başka bir öğe içinde olmayan programlama öğeleri `Public` veya `Friend` erişimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="84557-135">Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access.</span></span> <span data-ttu-id="84557-136">Belirtilmemişse, böyle bir öğenin erişim düzeyi `Friend` Varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="84557-136">If unspecified, the access level of such an element uses `Friend` by default.</span></span> <span data-ttu-id="84557-137">Ad alanı düzeyinde bildirebileceğiniz öğeler sınıflar, yapılar, modüller, arabirimler, numaralandırmalar ve temsilciler içerir.</span><span class="sxs-lookup"><span data-stu-id="84557-137">Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates.</span></span> <span data-ttu-id="84557-138">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="84557-138">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="root-namespace"></a><span data-ttu-id="84557-139">Kök ad alanı</span><span class="sxs-lookup"><span data-stu-id="84557-139">Root Namespace</span></span>  

 <span data-ttu-id="84557-140">Projenizdeki tüm ad alanı adları bir *kök ad alanını* temel alır.</span><span class="sxs-lookup"><span data-stu-id="84557-140">All namespace names in your project are based on a *root namespace*.</span></span> <span data-ttu-id="84557-141">Visual Studio, projenizdeki tüm kodlar için proje adınızı varsayılan kök ad alanı olarak atar.</span><span class="sxs-lookup"><span data-stu-id="84557-141">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="84557-142">Örneğin, projeniz adlandırılmışsa `Payroll` , programlama öğeleri ad alanına aittir `Payroll` .</span><span class="sxs-lookup"><span data-stu-id="84557-142">For example, if your project is named `Payroll`, its programming elements belong to namespace `Payroll`.</span></span> <span data-ttu-id="84557-143">Bildirirseniz `Namespace funding` , bu ad alanının tam adı olur `Payroll.funding` .</span><span class="sxs-lookup"><span data-stu-id="84557-143">If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.</span></span>  
  
 <span data-ttu-id="84557-144">`Namespace`Genel liste sınıfı örneğinde olduğu gibi, bir bildirimde mevcut bir ad alanı belirtmek istiyorsanız, kök ad alanınızı null bir değer olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84557-144">If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value.</span></span> <span data-ttu-id="84557-145">Bunu yapmak için **Proje** menüsünden **Proje özellikleri** ' ne tıklayın ve ardından kutunun boş olması için **kök ad alanı** girişini temizleyin.</span><span class="sxs-lookup"><span data-stu-id="84557-145">To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty.</span></span> <span data-ttu-id="84557-146">Bunu genel liste sınıfı örneğinde yapmadıysanız, Visual Basic Derleyicisi `System.Collections.Generic` proje içinde `Payroll` , tam adıyla birlikte yeni bir ad alanı olarak alır `Payroll.System.Collections.Generic` .</span><span class="sxs-lookup"><span data-stu-id="84557-146">If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.</span></span>  
  
 <span data-ttu-id="84557-147">Alternatif olarak, `Global` anahtar sözcüğünü, projenizin dışında tanımlanan ad alanları öğelerine başvurmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84557-147">Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project.</span></span> <span data-ttu-id="84557-148">Bunun yapılması, proje adınızı kök ad alanı olarak korumanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="84557-148">Doing so lets you retain your project name as the root namespace.</span></span> <span data-ttu-id="84557-149">Bu, programlama öğelerinizi, varolan ad uzaylarınızla birlikte yanlışlıkla birleştirme olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="84557-149">This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces.</span></span> <span data-ttu-id="84557-150">Daha fazla bilgi için [Visual Basic ad alanları](../../programming-guide/program-structure/namespaces.md)Içindeki "tam adlarda genel anahtar sözcük" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="84557-150">For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="84557-151">`Global`Anahtar sözcüğü bir ad uzayı ifadesinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="84557-151">The `Global` keyword can also be used in a Namespace statement.</span></span> <span data-ttu-id="84557-152">Bu, projenizin kök ad alanından bir ad alanı tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="84557-152">This lets you define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="84557-153">Daha fazla bilgi için [Visual Basic ad alanları](../../programming-guide/program-structure/namespaces.md)Içindeki "ad alanı deyimlerine genel anahtar sözcüğü" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="84557-153">For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="84557-154">**Sorunu.**</span><span class="sxs-lookup"><span data-stu-id="84557-154">**Troubleshooting.**</span></span> <span data-ttu-id="84557-155">Kök ad alanı, ad alanı adlarının beklenmedik birleştirmeleri oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="84557-155">The root namespace can lead to unexpected concatenations of namespace names.</span></span> <span data-ttu-id="84557-156">Projenizin dışında tanımlanan ad alanlarına başvuru yaparsanız, Visual Basic derleyici bunları kök ad alanında iç içe geçmiş ad alanları olarak construe.</span><span class="sxs-lookup"><span data-stu-id="84557-156">If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace.</span></span> <span data-ttu-id="84557-157">Böyle bir durumda, derleyici dış ad alanlarında zaten tanımlanmış olan herhangi bir türü tanımaz.</span><span class="sxs-lookup"><span data-stu-id="84557-157">In such a case, the compiler does not recognize any types that have been already defined in the external namespaces.</span></span> <span data-ttu-id="84557-158">Bunu önlemek için, kök ad alanınızı "kök ad alanı" içinde açıklandığı şekilde null bir değer olarak ayarlayın veya `Global` dış ad alanlarının öğelerine erişmek için anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="84557-158">To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.</span></span>  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="84557-159">Öznitelikler ve değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="84557-159">Attributes and Modifiers</span></span>  

 <span data-ttu-id="84557-160">Bir ad alanına öznitelikler uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="84557-160">You cannot apply attributes to a namespace.</span></span> <span data-ttu-id="84557-161">Bir öznitelik, verileri, ad alanları gibi kaynak sınıflandırıcılar için anlamlı olmayan derlemenin meta verilerine katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="84557-161">An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.</span></span>  
  
 <span data-ttu-id="84557-162">Herhangi bir erişim veya yordam değiştiricisi ya da başka bir değiştirici, bir ad alanına uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="84557-162">You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace.</span></span> <span data-ttu-id="84557-163">Bir tür olmadığından, bu değiştiriciler anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="84557-163">Because it is not a type, these modifiers are not meaningful.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84557-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="84557-164">Example</span></span>  

 <span data-ttu-id="84557-165">Aşağıdaki örnek, diğeri diğeri olan iki ad alanını bildirir.</span><span class="sxs-lookup"><span data-stu-id="84557-165">The following example declares two namespaces, one nested in the other.</span></span>  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a><span data-ttu-id="84557-166">Örnek</span><span class="sxs-lookup"><span data-stu-id="84557-166">Example</span></span>  

 <span data-ttu-id="84557-167">Aşağıdaki örnek, birden çok iç içe ad alanını tek bir satırda bildirir ve bu, önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="84557-167">The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.</span></span>  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="84557-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="84557-168">Example</span></span>  

 <span data-ttu-id="84557-169">Aşağıdaki örnek, önceki örneklerde tanımlanan sınıfa erişir.</span><span class="sxs-lookup"><span data-stu-id="84557-169">The following example accesses the class defined in the previous examples.</span></span>  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a><span data-ttu-id="84557-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="84557-170">Example</span></span>  

 <span data-ttu-id="84557-171">Aşağıdaki örnek, yeni bir genel liste sınıfının iskelet 'sini tanımlar ve <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanına ekler.</span><span class="sxs-lookup"><span data-stu-id="84557-171">The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="84557-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84557-172">See also</span></span>

- [<span data-ttu-id="84557-173">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="84557-173">Imports Statement (.NET Namespace and Type)</span></span>](imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="84557-174">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="84557-174">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="84557-175">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="84557-175">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
