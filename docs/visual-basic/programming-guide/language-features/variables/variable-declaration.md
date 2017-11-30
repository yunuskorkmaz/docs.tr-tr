---
title: "Visual Basic'de Değişken Bildirimi"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7f7b924aed1da7db816aa5c11239e301428770b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="30c6d-102">Visual Basic'de Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="30c6d-102">Variable Declaration in Visual Basic</span></span>
<span data-ttu-id="30c6d-103">Ad ve özelliklerini belirtmek için bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="30c6d-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="30c6d-104">Değişken bildirimi deyimi [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="30c6d-104">The declaration statement for variables is the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="30c6d-105">Konumuna ve içeriği değişkenin özellikleri belirler.</span><span class="sxs-lookup"><span data-stu-id="30c6d-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="30c6d-106">Değişken adlandırma kuralları ve hususlar için bkz: [bildirilen öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="30c6d-106">For variable naming rules and considerations, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="30c6d-107">Bildirim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="30c6d-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="30c6d-108">Yerel ve üye değişkenleri</span><span class="sxs-lookup"><span data-stu-id="30c6d-108">Local and Member Variables</span></span>  
 <span data-ttu-id="30c6d-109">A *yerel değişken* bir yordam içinde bildirilen biridir.</span><span class="sxs-lookup"><span data-stu-id="30c6d-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="30c6d-110">A *üye değişkeni* üyesi olan bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] yazın; sınıf, yapı veya modül içinde ancak bu sınıf, yapı veya modülü iç herhangi bir yordam içinde değil modülü düzeyinde bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="30c6d-110">A *member variable* is a member of a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="30c6d-111">Paylaşılan ve örnek değişkenleri</span><span class="sxs-lookup"><span data-stu-id="30c6d-111">Shared and Instance Variables</span></span>  
 <span data-ttu-id="30c6d-112">Sınıf veya yapı olsun veya olmasın, paylaşılan üzerinde bir üye değişkenine kategorisini bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="30c6d-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="30c6d-113">İle bildirilirse [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) olmasından anahtar sözcüğü bir *paylaşılan değişken*, ve sınıf veya yapı tüm örnekleri arasında paylaşılan tek bir kopya bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30c6d-113">If it is declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="30c6d-114">Aksi durumda olduğu bir *örnek değişkeni*, ve sınıf veya yapı her örneği için ayrı bir kopyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="30c6d-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="30c6d-115">Belirli bir örnek değişkeni kopyasını yalnızca örneği sınıf veya yapı içinde oluşturulduğu için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="30c6d-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="30c6d-116">Diğer örneklerini sınıf veya yapı örnek değişkeninde bir kopyasını bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="30c6d-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="30c6d-117">Veri türü bildirme</span><span class="sxs-lookup"><span data-stu-id="30c6d-117">Declaring Data Type</span></span>  
 <span data-ttu-id="30c6d-118">[Olarak](../../../../visual-basic/language-reference/statements/as-clause.md) bildirim deyiminin yan tümcesinde veri türü veya nesne türü bildirme değişkenin tanımlamanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="30c6d-118">The [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="30c6d-119">Şu türler için bir değişken belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30c6d-119">You can specify any of the following types for a variable:</span></span>  
  
-   <span data-ttu-id="30c6d-120">Başlangıç veri türü, gibi `Boolean`, `Long`, veya`Decimal`</span><span class="sxs-lookup"><span data-stu-id="30c6d-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
-   <span data-ttu-id="30c6d-121">Bir dizi ya da yapısı gibi bir bileşik veri türü</span><span class="sxs-lookup"><span data-stu-id="30c6d-121">A composite data type, such as an array or structure</span></span>  
  
-   <span data-ttu-id="30c6d-122">Bir nesne türü ya da uygulamanızı veya başka bir uygulama tanımlı sınıfı</span><span class="sxs-lookup"><span data-stu-id="30c6d-122">An object type, or class, defined either in your application or in another application</span></span>  
  
-   <span data-ttu-id="30c6d-123">A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] gibi sınıfı <xref:System.Windows.Forms.Label> veya<xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="30c6d-123">A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
-   <span data-ttu-id="30c6d-124">Arabirim türü, gibi <xref:System.IComparable> veya<xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="30c6d-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="30c6d-125">Veri türü yinelemek zorunda kalmadan bir deyim birkaç değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30c6d-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="30c6d-126">Değişkenleri aşağıdaki deyimlerinde `i`, `j`, ve `k` türü olarak bildirilmiş `Integer`, `l` ve `m` olarak `Long`, ve `x` ve `y` olarak`Single`:</span><span class="sxs-lookup"><span data-stu-id="30c6d-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="30c6d-127">Veri türleri hakkında daha fazla bilgi için bkz: [veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="30c6d-127">For more information on data types, see [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md).</span></span> <span data-ttu-id="30c6d-128">Nesneleri hakkında daha fazla bilgi için bkz: [nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) ve [bileşenlerle programlama](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span><span class="sxs-lookup"><span data-stu-id="30c6d-128">For more information on objects, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) and [Programming with Components](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="30c6d-129">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30c6d-129">Local Type Inference</span></span>  
 <span data-ttu-id="30c6d-130">*Tür çıkarımı* olmadan bildirilen yerel değişkenleri veri türlerini belirlemek için kullanılan bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="30c6d-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="30c6d-131">Derleyici başlatma ifade türü değişkeninden türü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30c6d-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="30c6d-132">Bu, açıkça bir türü bildirmeden değişkenleri bildirin olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="30c6d-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="30c6d-133">Aşağıdaki örnekte, her ikisi de `num1` ve `num2` tamsayı olarak kesin türü belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="30c6d-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 <span data-ttu-id="30c6d-134">Yerel türü çıkarımı kullanmak istiyorsanız, `Option Infer` ayarlanmalıdır `On`.</span><span class="sxs-lookup"><span data-stu-id="30c6d-134">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="30c6d-135">Daha fazla bilgi için bkz: [yerel türü çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) ve [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="30c6d-135">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="30c6d-136">Bildirilen değişkenlerin özellikleri</span><span class="sxs-lookup"><span data-stu-id="30c6d-136">Characteristics of Declared Variables</span></span>  
 <span data-ttu-id="30c6d-137">*Ömrü* bir değişken süre hangi BT sırasında kullanılmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="30c6d-137">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="30c6d-138">Genel olarak, (yordamı veya sınıfı gibi) bildirir öğesi var olmaya devam eder sürece bir değişken mevcut.</span><span class="sxs-lookup"><span data-stu-id="30c6d-138">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="30c6d-139">Değişkenini içeren öğe ömür varolan devam gerekmez, bildiriminde özel bir şey yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="30c6d-139">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="30c6d-140">Değişkenini içeren kendi öğesinin daha uzun var olmaya devam gerekiyorsa içerebilir `Static` veya `Shared` anahtar sözcük, `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="30c6d-140">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="30c6d-141">Daha fazla bilgi için bkz: [Visual Basic'de ömür](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span><span class="sxs-lookup"><span data-stu-id="30c6d-141">For more information, see [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="30c6d-142">*Kapsam* bir değişken adı niteleme olmadan başvurduğu tüm kod kümesidir.</span><span class="sxs-lookup"><span data-stu-id="30c6d-142">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="30c6d-143">Bir değişkenin kapsamını burada bildirilmeden tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="30c6d-143">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="30c6d-144">Belirli bir bölgede bulunan koduna adlarını nitelemek gerek kalmadan bu bölgede tanımlanan değişkenler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30c6d-144">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="30c6d-145">Daha fazla bilgi için bkz: [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="30c6d-145">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="30c6d-146">Bir değişkenin *erişim düzeyine* erişmek için izne sahip code uzantı'dır.</span><span class="sxs-lookup"><span data-stu-id="30c6d-146">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="30c6d-147">Bu erişim değiştiricisi tarafından belirlenir (gibi [ortak](../../../../visual-basic/language-reference/modifiers/public.md) veya [özel](../../../../visual-basic/language-reference/modifiers/private.md)) kullandığınız `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="30c6d-147">This is determined by the access modifier (such as [Public](../../../../visual-basic/language-reference/modifiers/public.md) or [Private](../../../../visual-basic/language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="30c6d-148">Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="30c6d-148">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c6d-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30c6d-149">See Also</span></span>  
 [<span data-ttu-id="30c6d-150">Nasıl yapılır: yeni değişken oluşturma</span><span class="sxs-lookup"><span data-stu-id="30c6d-150">How to: Create a New Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)  
 [<span data-ttu-id="30c6d-151">Nasıl yapılır: içine ve dışına bir değişken veri taşıma</span><span class="sxs-lookup"><span data-stu-id="30c6d-151">How to: Move Data Into and Out of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [<span data-ttu-id="30c6d-152">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="30c6d-152">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="30c6d-153">Korumalı</span><span class="sxs-lookup"><span data-stu-id="30c6d-153">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="30c6d-154">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="30c6d-154">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="30c6d-155">Statik</span><span class="sxs-lookup"><span data-stu-id="30c6d-155">Static</span></span>](../../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="30c6d-156">Bildirilen öğe özellikleri</span><span class="sxs-lookup"><span data-stu-id="30c6d-156">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="30c6d-157">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="30c6d-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="30c6d-158">Option Infer deyimi</span><span class="sxs-lookup"><span data-stu-id="30c6d-158">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
