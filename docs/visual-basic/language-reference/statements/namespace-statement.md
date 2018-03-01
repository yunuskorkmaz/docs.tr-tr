---
title: Namespace Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9863286a8eda2559ab678c77a81cc7d6063c3e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-statement"></a><span data-ttu-id="342f9-102">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="342f9-102">Namespace Statement</span></span>
<span data-ttu-id="342f9-103">Bir ad alanı bildirir ve ad alanında derlenmesi için bildirimini izleyen kaynak kodunu neden olur.</span><span class="sxs-lookup"><span data-stu-id="342f9-103">Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="342f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="342f9-104">Syntax</span></span>  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a><span data-ttu-id="342f9-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="342f9-105">Parts</span></span>  
 <span data-ttu-id="342f9-106">Global</span><span class="sxs-lookup"><span data-stu-id="342f9-106">Global</span></span>  
 <span data-ttu-id="342f9-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="342f9-107">Optional.</span></span> <span data-ttu-id="342f9-108">Kök ad alanı projenizin dışında bir ad alanı tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="342f9-108">Allows you to define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="342f9-109">Bkz: [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="342f9-109">See [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 `name`  
 <span data-ttu-id="342f9-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="342f9-110">Required.</span></span> <span data-ttu-id="342f9-111">Ad alanını tanımlayan benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="342f9-111">A unique name that identifies the namespace.</span></span> <span data-ttu-id="342f9-112">Geçerli bir Visual Basic tanımlayıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="342f9-112">Must be a valid Visual Basic identifier.</span></span> <span data-ttu-id="342f9-113">Daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="342f9-113">For more information, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `componenttypes`  
 <span data-ttu-id="342f9-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="342f9-114">Optional.</span></span> <span data-ttu-id="342f9-115">Ad alanı olun öğeleri.</span><span class="sxs-lookup"><span data-stu-id="342f9-115">Elements that make up the namespace.</span></span> <span data-ttu-id="342f9-116">Bunlar arasında ancak numaralandırmalar, yapıları, arabirimleri, sınıflar, modüller, temsilciler ve diğer ad alanları için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="342f9-116">These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.</span></span>  
  
 `End Namespace`  
 <span data-ttu-id="342f9-117">Sonlandırır bir `Namespace` bloğu.</span><span class="sxs-lookup"><span data-stu-id="342f9-117">Terminates a `Namespace` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="342f9-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="342f9-118">Remarks</span></span>  
 <span data-ttu-id="342f9-119">Ad alanları, bir kuruluş sistemi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="342f9-119">Namespaces are used as an organizational system.</span></span> <span data-ttu-id="342f9-120">Bunlar, sınıflandırmak ve diğer programları ve uygulamaları sunulan programlama öğeleri sunmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="342f9-120">They provide a way to classify and present programming elements that are exposed to other programs and applications.</span></span> <span data-ttu-id="342f9-121">Bir ad değil Not bir *türü* bir sınıf veya yapı herkese açık — bir ad alanı veri türüne sahip bir programlama öğesi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="342f9-121">Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.</span></span>  
  
 <span data-ttu-id="342f9-122">Sonra tüm programlama öğeleri bildirilen bir `Namespace` deyimi bu ad alanına ait.</span><span class="sxs-lookup"><span data-stu-id="342f9-122">All programming elements declared after a `Namespace` statement belong to that namespace.</span></span> <span data-ttu-id="342f9-123">Visual Basic devam eder ya da bulduğu kadar öğeleri son bildirilen ad alanına derlemek bir `End Namespace` deyimi veya başka bir `Namespace` deyimi.</span><span class="sxs-lookup"><span data-stu-id="342f9-123">Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.</span></span>  
  
 <span data-ttu-id="342f9-124">Bir ad alanı zaten, hatta projenizi dışında tanımlanmışsa, programlama öğeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="342f9-124">If a namespace is already defined, even outside your project, you can add programming elements to it.</span></span> <span data-ttu-id="342f9-125">Bunu yapmak için kullandığınız bir `Namespace` öğeleri bu ad alanına derlemek için Visual Basic yönlendirmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="342f9-125">To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.</span></span>  
  
 <span data-ttu-id="342f9-126">Kullanabileceğiniz bir `Namespace` dosya veya ad alanı düzeyinde yalnızca deyimi.</span><span class="sxs-lookup"><span data-stu-id="342f9-126">You can use a `Namespace` statement only at the file or namespace level.</span></span> <span data-ttu-id="342f9-127">Yani *bildirimi bağlam* için bir ad alanı kaynak dosyası veya başka bir ad olmalıdır ve bir sınıf, yapı, modülü, arabirimi veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="342f9-127">This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure.</span></span> <span data-ttu-id="342f9-128">Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="342f9-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="342f9-129">İçinde başka bir ad alanı bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="342f9-129">You can declare one namespace within another.</span></span> <span data-ttu-id="342f9-130">Declare, ancak başka bir kod en içteki ad alanında bildirilen öğeler eriştiğinde, iç içe geçmiş hiyerarşideki tüm ad alanı adlarını içeren bir niteliği dize kullanması gerektiğini unutmayın iç içe geçme düzeyleri katı bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="342f9-130">There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.</span></span>  
  
## <a name="access-level"></a><span data-ttu-id="342f9-131">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="342f9-131">Access Level</span></span>  
 <span data-ttu-id="342f9-132">Ad alanları sanki sahip oldukları kabul edilir bir `Public` erişim düzeyi.</span><span class="sxs-lookup"><span data-stu-id="342f9-132">Namespaces are treated as if they have a `Public` access level.</span></span> <span data-ttu-id="342f9-133">Bir ad alanı, aynı proje başka bir yerindeki kod projesine başvuru diğer projeler ve projesinden derleme erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="342f9-133">A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.</span></span>  
  
 <span data-ttu-id="342f9-134">Bir ad alanı, ancak diğer herhangi bir öğe içinde değil anlamı ad alanı düzeyinde bildirilen programlama öğeleri olabilir `Public` veya `Friend` erişim.</span><span class="sxs-lookup"><span data-stu-id="342f9-134">Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access.</span></span> <span data-ttu-id="342f9-135">Belirtilmezse, bu tür erişim düzeyi bir öğeyi kullanan `Friend` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="342f9-135">If unspecified, the access level of such an element uses `Friend` by default.</span></span> <span data-ttu-id="342f9-136">Ad alanı düzeyinde bildirebilir öğeler, sınıflar, yapılar, modüller, arabirimler, numaralandırmalar ve temsilciler içerir.</span><span class="sxs-lookup"><span data-stu-id="342f9-136">Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates.</span></span> <span data-ttu-id="342f9-137">Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="342f9-137">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="root-namespace"></a><span data-ttu-id="342f9-138">Kök Namespace</span><span class="sxs-lookup"><span data-stu-id="342f9-138">Root Namespace</span></span>  
 <span data-ttu-id="342f9-139">Projenizdeki tüm ad alanı adlarını temel alan bir *kök ad alanı*.</span><span class="sxs-lookup"><span data-stu-id="342f9-139">All namespace names in your project are based on a *root namespace*.</span></span> <span data-ttu-id="342f9-140">Visual Studio Proje adına projenizdeki tüm kodları için varsayılan kök ad alanı olarak atar.</span><span class="sxs-lookup"><span data-stu-id="342f9-140">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="342f9-141">Örneğin, projenizin adlı `Payroll`, programlama öğeleri ad alanına ait `Payroll`.</span><span class="sxs-lookup"><span data-stu-id="342f9-141">For example, if your project is named `Payroll`, its programming elements belong to namespace `Payroll`.</span></span> <span data-ttu-id="342f9-142">Bildirirseniz `Namespace funding`, bu ad alanının tam adı `Payroll.funding`.</span><span class="sxs-lookup"><span data-stu-id="342f9-142">If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.</span></span>  
  
 <span data-ttu-id="342f9-143">Varolan bir ad alanında belirtmek istiyorsanız bir `Namespace` deyimi, gibi genel liste sınıfı örnekte, kök ad alanı null bir değere ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="342f9-143">If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value.</span></span> <span data-ttu-id="342f9-144">Bunu yapmak için tıklatın **proje özelliklerini** gelen **proje** menüsüne ve ardından Temizle **kök ad alanı** giriş kutusu boş olmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="342f9-144">To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty.</span></span> <span data-ttu-id="342f9-145">Bu genel liste sınıfı örnekte yapmadınız, Visual Basic derleyici götürecek `System.Collections.Generic` proje içindeki yeni bir ad alanı olarak `Payroll`, tam adıyla `Payroll.System.Collections.Generic`.</span><span class="sxs-lookup"><span data-stu-id="342f9-145">If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.</span></span>  
  
 <span data-ttu-id="342f9-146">Alternatif olarak, kullanabileceğiniz `Global` anahtar projeniz dışında tanımlanan ad alanları öğelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="342f9-146">Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project.</span></span> <span data-ttu-id="342f9-147">Bunun yapılması, kök ad alanı olarak projenizin adına korumak olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="342f9-147">Doing so lets you retain your project name as the root namespace.</span></span> <span data-ttu-id="342f9-148">Bu, istemeden programlama öğelerinizi olanlar var olan ad alanları ile birlikte birleştirme olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="342f9-148">This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces.</span></span> <span data-ttu-id="342f9-149">Daha fazla bilgi için "Genel anahtar sözcüğü içinde tam olarak nitelenmiş adlar" bölümüne bakın [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="342f9-149">For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="342f9-150">`Global` Anahtar sözcüğü bir Namespace deyimi içinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="342f9-150">The `Global` keyword can also be used in a Namespace statement.</span></span> <span data-ttu-id="342f9-151">Bu, bir ad alanı, projenin kök ad alanı dışında tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="342f9-151">This lets you define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="342f9-152">Daha fazla bilgi için "Genel anahtar sözcüğü içinde arama Namespace deyimleri" bölümüne bakın [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="342f9-152">For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="342f9-153">**Sorun giderme.**</span><span class="sxs-lookup"><span data-stu-id="342f9-153">**Troubleshooting.**</span></span> <span data-ttu-id="342f9-154">Kök ad alanı için ad alanı adlarının beklenmeyen birleştirmeler yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="342f9-154">The root namespace can lead to unexpected concatenations of namespace names.</span></span> <span data-ttu-id="342f9-155">Projenizi dışında tanımlanan ad alanları için başvuru yaparsanız, Visual Basic derleyici bunları kök ad alanı iç içe geçmiş ad alanları olarak construe.</span><span class="sxs-lookup"><span data-stu-id="342f9-155">If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace.</span></span> <span data-ttu-id="342f9-156">Böyle bir durumda, dış ad alanları ile önceden tanımlanmış herhangi bir türünün derleyici tanımıyor.</span><span class="sxs-lookup"><span data-stu-id="342f9-156">In such a case, the compiler does not recognize any types that have been already defined in the external namespaces.</span></span> <span data-ttu-id="342f9-157">Bu durumu önlemek için kök ad alanı "Kök Namespace" açıklandığı gibi null bir değere ayarlayın veya kullanmak `Global` erişim öğeleri dış ad alanları için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="342f9-157">To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.</span></span>  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="342f9-158">Öznitelikler ve değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="342f9-158">Attributes and Modifiers</span></span>  
 <span data-ttu-id="342f9-159">Bir ad alanına öznitelikleri uygulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="342f9-159">You cannot apply attributes to a namespace.</span></span> <span data-ttu-id="342f9-160">Öznitelik, kaynak sınıflandırıcı ad alanları gibi anlamlı olmayan derlemenin meta verilerini, bilgileri katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="342f9-160">An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.</span></span>  
  
 <span data-ttu-id="342f9-161">Bir ad alanına herhangi bir erişim veya yordam değiştiricileri veya diğer değiştiricileri uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="342f9-161">You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace.</span></span> <span data-ttu-id="342f9-162">Bir tür olduğundan, bu değiştiricileri anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="342f9-162">Because it is not a type, these modifiers are not meaningful.</span></span>  
  
## <a name="example"></a><span data-ttu-id="342f9-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="342f9-163">Example</span></span>  
 <span data-ttu-id="342f9-164">Aşağıdaki örnekte, iki ad alanı, bir diğer iç içe geçmiş bildirir.</span><span class="sxs-lookup"><span data-stu-id="342f9-164">The following example declares two namespaces, one nested in the other.</span></span>  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="342f9-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="342f9-165">Example</span></span>  
 <span data-ttu-id="342f9-166">Aşağıdaki örnek, tek bir satıra birden çok iç içe geçmiş ad bildirir ve önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="342f9-166">The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.</span></span>  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="342f9-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="342f9-167">Example</span></span>  
 <span data-ttu-id="342f9-168">Aşağıdaki örnek, önceki örneklerde tanımlanmış sınıf erişir.</span><span class="sxs-lookup"><span data-stu-id="342f9-168">The following example accesses the class defined in the previous examples.</span></span>  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="342f9-169">Örnek</span><span class="sxs-lookup"><span data-stu-id="342f9-169">Example</span></span>  
 <span data-ttu-id="342f9-170">Aşağıdaki örnek yeni bir genel liste sınıf çatıyı tanımlar ve ona ekler <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="342f9-170">The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="342f9-171">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="342f9-171">See Also</span></span>  
 [<span data-ttu-id="342f9-172">Imports deyimi (.NET Namespace ve türü)</span><span class="sxs-lookup"><span data-stu-id="342f9-172">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="342f9-173">Bildirilen öğe adları</span><span class="sxs-lookup"><span data-stu-id="342f9-173">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="342f9-174">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="342f9-174">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
