---
title: Dim Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
caps.latest.revision: 72
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36e2d416e4653bfa6fe212b75b92ae2d90775d53
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="cc806-102">Dim Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc806-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="cc806-103">Bildirir ve depolama alanı için bir veya daha fazla değişken ayırır.</span><span class="sxs-lookup"><span data-stu-id="cc806-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc806-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc806-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="cc806-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="cc806-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="cc806-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-106">Optional.</span></span> <span data-ttu-id="cc806-107">Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="cc806-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-108">Optional.</span></span> <span data-ttu-id="cc806-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="cc806-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="cc806-110">Public</span><span class="sxs-lookup"><span data-stu-id="cc806-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="cc806-111">Protected</span><span class="sxs-lookup"><span data-stu-id="cc806-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="cc806-112">Friend</span><span class="sxs-lookup"><span data-stu-id="cc806-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="cc806-113">Private</span><span class="sxs-lookup"><span data-stu-id="cc806-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="cc806-114">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-114">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="cc806-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-115">Optional.</span></span> <span data-ttu-id="cc806-116">Bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-116">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="cc806-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-117">Optional.</span></span> <span data-ttu-id="cc806-118">Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-118">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="cc806-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-119">Optional.</span></span> <span data-ttu-id="cc806-120">Bkz: [statik](../../../visual-basic/language-reference/modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-120">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="cc806-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-121">Optional.</span></span> <span data-ttu-id="cc806-122">Bkz: [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-122">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="cc806-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-123">Optional.</span></span> <span data-ttu-id="cc806-124">Bu olaylar oluşturabilir bir sınıfın örneklerine bakın nesne değişkenleri olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc806-124">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="cc806-125">Bkz: [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-125">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="cc806-126">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="cc806-126">Required.</span></span> <span data-ttu-id="cc806-127">Bu deyim içinde bildirilen değişkenleri listesi.</span><span class="sxs-lookup"><span data-stu-id="cc806-127">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="cc806-128">Her `variable` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="cc806-128">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="cc806-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="cc806-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="cc806-130">Bölümü</span><span class="sxs-lookup"><span data-stu-id="cc806-130">Part</span></span>|<span data-ttu-id="cc806-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc806-131">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="cc806-132">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="cc806-132">Required.</span></span> <span data-ttu-id="cc806-133">Değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="cc806-133">Name of the variable.</span></span> <span data-ttu-id="cc806-134">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="cc806-135">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-135">Optional.</span></span> <span data-ttu-id="cc806-136">Bir dizi değişken her boyut sınırları listesi.</span><span class="sxs-lookup"><span data-stu-id="cc806-136">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="cc806-137">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-137">Optional.</span></span> <span data-ttu-id="cc806-138">Sınıfının yeni bir örneğini oluşturur, `Dim` deyimini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="cc806-138">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="cc806-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-139">Optional.</span></span> <span data-ttu-id="cc806-140">Değişken veri türü.</span><span class="sxs-lookup"><span data-stu-id="cc806-140">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="cc806-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-141">Optional.</span></span> <span data-ttu-id="cc806-142">Nesne başlatıcı listesi sunar.</span><span class="sxs-lookup"><span data-stu-id="cc806-142">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="cc806-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cc806-143">Optional.</span></span> <span data-ttu-id="cc806-144">Bir özelliğin adını örneği getirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-144">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="cc806-145">Sonra gerekli `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="cc806-145">Required after `propertyname` =.</span></span> <span data-ttu-id="cc806-146">Değerlendirilir ve özellik adına atanmış ifade.</span><span class="sxs-lookup"><span data-stu-id="cc806-146">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="cc806-147">İsteğe bağlı ise `New` belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="cc806-147">Optional if `New` is not specified.</span></span> <span data-ttu-id="cc806-148">Değerlendirilir ve oluşturulduğunda değişkenine atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="cc806-148">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc806-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc806-149">Remarks</span></span>  
 <span data-ttu-id="cc806-150">Visual Basic derleyici kullanan `Dim` değişkenin veri türü ve hangi kod değişkenine erişebileceği gibi diğer bilgileri belirlemek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="cc806-150">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="cc806-151">Aşağıdaki örnek tutmak için bir değişken bildiren bir `Integer` değeri.</span><span class="sxs-lookup"><span data-stu-id="cc806-151">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="cc806-152">Herhangi bir veri türü veya bir numaralandırma, yapısı, sınıf veya arabirim adını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-152">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="cc806-153">Bir başvuru türü için kullandığınız `New` sınıfının yeni bir örneğini oluşturun veya bu yapısı anahtar sözcüğü veri türü tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cc806-153">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="cc806-154">Kullanırsanız `New`, başlatıcı ifade kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="cc806-154">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="cc806-155">Bunun yerine, değişkeni oluşturmakta olduğunuz sınıfı oluşturucusu için gerekli iseler bağımsız değişken sağlayın.</span><span class="sxs-lookup"><span data-stu-id="cc806-155">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="cc806-156">Bir değişkende yordamı, blok, sınıf, yapı veya modülü bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-156">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="cc806-157">Bir değişkende kaynak dosya, ad alanı veya arabirimi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-157">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="cc806-158">Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="cc806-159">Herhangi bir yordam dışında modülü düzeyinde bildirilmiş bir değişkeni, bir *üye değişkeni* veya *alan*.</span><span class="sxs-lookup"><span data-stu-id="cc806-159">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="cc806-160">Üye değişkenleri kapsamında kendi sınıf, yapı veya modülü boyunca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc806-160">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="cc806-161">Yordam düzeyinde bildirilen bir değişkeni, bir *yerel değişken*.</span><span class="sxs-lookup"><span data-stu-id="cc806-161">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="cc806-162">Yalnızca kendi yordam veya bloğu içinde kapsamdaki yerel değişkenleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc806-162">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="cc806-163">Aşağıdaki erişim değiştiricileri yordam dışında değişkenleri bildirmek için kullanılır: `Public`, `Protected`, `Friend`, `Protected Friend`, ve `Private`.</span><span class="sxs-lookup"><span data-stu-id="cc806-163">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="cc806-164">Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-164">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="cc806-165">`Dim` Anahtar sözcüğü isteğe bağlıdır ve aşağıdaki değiştiricileri belirtirseniz genellikle atlanmış: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, veya `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="cc806-165">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="cc806-166">Varsa `Option Explicit` olduğunu (varsayılan), derleyici, kullandığınız her değişken için bir bildirimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cc806-166">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="cc806-167">Daha fazla bilgi için bkz: [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-167">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="cc806-168">Bir başlangıç değeri belirtme</span><span class="sxs-lookup"><span data-stu-id="cc806-168">Specifying an Initial Value</span></span>  
 <span data-ttu-id="cc806-169">Oluşturulduğunda bir değişkene bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-169">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="cc806-170">Değer türü için kullandığınız bir *Başlatıcı* değişkenine atanan bir ifade sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="cc806-170">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="cc806-171">İfade derleme zamanında hesaplanan bir sabit değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cc806-171">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="cc806-172">Bir başlatıcı belirtilirse ve bir veri türü olarak belirtilmemiş bir `As` yan tümcesi *türü çıkarımı* Başlatıcı veri türünden anlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc806-172">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="cc806-173">Aşağıdaki örnekte, her ikisi de `num1` ve `num2` tamsayı olarak kesin türü belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="cc806-173">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="cc806-174">İkinci bildiriminde tür çıkarımı 3 değerinden türü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc806-174">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="cc806-175">Tür çıkarımı yordamı düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cc806-175">Type inference applies at the procedure level.</span></span> <span data-ttu-id="cc806-176">Sınıf, yapı, modül veya arabirim yordam dışında uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="cc806-176">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="cc806-177">Tür çıkarımı hakkında daha fazla bilgi için bkz: [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-177">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="cc806-178">Veri türü veya Başlatıcı belirtilmediğinde neler olduğu hakkında daha fazla bilgi için bkz: [varsayılan veri türleri ve değerleri](../../../visual-basic/language-reference/statements/dim-statement.md#default) bu konuda daha sonra.</span><span class="sxs-lookup"><span data-stu-id="cc806-178">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="cc806-179">Kullanabileceğiniz bir *Başlatıcı nesne* adlandırılmış ve anonim türler örneklerini bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="cc806-179">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="cc806-180">Aşağıdaki kod örneği oluşturur bir `Student` sınıf ve nesne Başlatıcı özellikleri başlatmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc806-180">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="cc806-181">Nesne başlatıcıları hakkında daha fazla bilgi için bkz: [nasıl yapılır: nesne Başlatıcı kullanarak nesne bildirme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), ve [anonim türler ](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-181">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="cc806-182">Birden çok değişkenleri bildirme</span><span class="sxs-lookup"><span data-stu-id="cc806-182">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="cc806-183">Parantezler ile her biri için ve her bir dizi adı aşağıdaki değişken adını belirten bir bildirim deyiminde çeşitli değişkenler bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-183">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="cc806-184">Birden çok değişkenleri virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="cc806-184">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="cc806-185">Bir sahip birden fazla değişken bildirirseniz `As` yan tümcesi, değişkenlerin bu grup için bir başlatıcı sağlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="cc806-185">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="cc806-186">Ayrı bir kullanarak farklı veri türleri için farklı değişkenleri belirtebilirsiniz `As` yan tümcesi bildirdiğiniz her değişken için.</span><span class="sxs-lookup"><span data-stu-id="cc806-186">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="cc806-187">Her bir değişken ilk belirtilen veri türü alır `As` yan tümcesi karşılaştı sonra kendi `variablename` bölümü.</span><span class="sxs-lookup"><span data-stu-id="cc806-187">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="cc806-188">Diziler</span><span class="sxs-lookup"><span data-stu-id="cc806-188">Arrays</span></span>  
 <span data-ttu-id="cc806-189">Tutmak için bir değişken bildirebilir bir *dizi*, hangi birden fazla değer tutma.</span><span class="sxs-lookup"><span data-stu-id="cc806-189">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="cc806-190">Bir değişken dizisini tutan belirtmek için izleyin, `variablename` parantez olmadan hemen.</span><span class="sxs-lookup"><span data-stu-id="cc806-190">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="cc806-191">Dizileri hakkında daha fazla bilgi için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-191">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="cc806-192">Alt ve bir dizinin her boyut üst sınırını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-192">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="cc806-193">Bunu yapmak için içeren bir `boundslist` parantez içinde.</span><span class="sxs-lookup"><span data-stu-id="cc806-193">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="cc806-194">Her boyut için `boundslist` üst sınırı ve isteğe bağlı olarak alt sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc806-194">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="cc806-195">Olup olmadığını belirtin alt her zaman sıfır sınırdır.</span><span class="sxs-lookup"><span data-stu-id="cc806-195">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="cc806-196">Her dizin aracılığıyla üst sınır değeri sıfırdan farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="cc806-196">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="cc806-197">Aşağıdaki iki ifade eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="cc806-197">The following two statements are equivalent.</span></span> <span data-ttu-id="cc806-198">Her ifade 21 dizisi bildirir `Integer` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="cc806-198">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="cc806-199">Dizi eriştiğinizde, dizin 0 ile 20 arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="cc806-199">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="cc806-200">Aşağıdaki ifade, iki boyutlu bir dizi türü bildirir `Double`.</span><span class="sxs-lookup"><span data-stu-id="cc806-200">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="cc806-201">Dizi olan sütunların 6 (5 + 1) her 4 satırlar (3 + 1).</span><span class="sxs-lookup"><span data-stu-id="cc806-201">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="cc806-202">Bir üst sınır boyutu uzunluğunu değil dizin için olası en yüksek değere temsil ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cc806-202">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="cc806-203">Boyut uzunluğu üst sınırı artı bir taneyi olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc806-203">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="cc806-204">Bir dizi 1 ile 32 boyutlarına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc806-204">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="cc806-205">Tüm sınırların bir dizi bildiriminde boş bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-205">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="cc806-206">Bunu yaparsanız, dizi belirttiğiniz boyut sayısını gerekiyor, ancak bunu başlatılmamış.</span><span class="sxs-lookup"><span data-stu-id="cc806-206">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="cc806-207">Değerine sahip `Nothing` en az başlatma kadar bazı öğeleri.</span><span class="sxs-lookup"><span data-stu-id="cc806-207">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="cc806-208">`Dim` Deyimi tüm boyutları veya için hiç boyut sınırları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc806-208">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="cc806-209">Dizi birden fazla boyuta varsa, virgül boyut sayısını belirtmek için parantez içermelidir.</span><span class="sxs-lookup"><span data-stu-id="cc806-209">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="cc806-210">Bildirebilirsiniz bir *sıfır uzunluk dizisi* -1 olarak dizinin boyutlardan birini bildirme tarafından.</span><span class="sxs-lookup"><span data-stu-id="cc806-210">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="cc806-211">Sıfır uzunluklu dizi tutan bir değişken değeri yok `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="cc806-211">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="cc806-212">Sıfır uzunlukta diziler belirli ortak dil çalışma zamanı işlevleri tarafından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cc806-212">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="cc806-213">Bu tür bir dizi erişmeye çalışırsa, bir çalışma zamanı özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="cc806-213">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="cc806-214">Daha fazla bilgi için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-214">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="cc806-215">Değişmez değer bir dizi kullanarak bir dizi değerlerini başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-215">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="cc806-216">Bunu yapmak için başlatma değerleri köşeli parantez ile çevrelendiğinden (`{}`).</span><span class="sxs-lookup"><span data-stu-id="cc806-216">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="cc806-217">Çok boyutlu diziler için başlatma ayrı her boyut için dış boyutundaki köşeli parantez içine alınır.</span><span class="sxs-lookup"><span data-stu-id="cc806-217">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="cc806-218">Öğeleri ana satır sırasına göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cc806-218">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="cc806-219">Dizi değişmez değerleri hakkında daha fazla bilgi için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-219">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <a name="default"></a> <span data-ttu-id="cc806-220">Varsayılan veri türleri ve değerleri</span><span class="sxs-lookup"><span data-stu-id="cc806-220">Default Data Types and Values</span></span>  
 <span data-ttu-id="cc806-221">Veri türü ve Başlatıcı belirtmenin çeşitli birleşimleri sonuçları aşağıdaki tabloda açıklanmaktadır bir `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="cc806-221">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="cc806-222">Belirtilen veri türü?</span><span class="sxs-lookup"><span data-stu-id="cc806-222">Data type specified?</span></span>|<span data-ttu-id="cc806-223">Belirtilen başlatıcı?</span><span class="sxs-lookup"><span data-stu-id="cc806-223">Initializer specified?</span></span>|<span data-ttu-id="cc806-224">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc806-224">Example</span></span>|<span data-ttu-id="cc806-225">Sonuç</span><span class="sxs-lookup"><span data-stu-id="cc806-225">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="cc806-226">Hayır</span><span class="sxs-lookup"><span data-stu-id="cc806-226">No</span></span>|<span data-ttu-id="cc806-227">Hayır</span><span class="sxs-lookup"><span data-stu-id="cc806-227">No</span></span>|`Dim qty`|<span data-ttu-id="cc806-228">Varsa [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) olan kapalı (varsayılan), değişkenini ayarlamak `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="cc806-228">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="cc806-229">Varsa `Option Strict` olduğundan, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="cc806-229">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="cc806-230">Hayır</span><span class="sxs-lookup"><span data-stu-id="cc806-230">No</span></span>|<span data-ttu-id="cc806-231">Evet</span><span class="sxs-lookup"><span data-stu-id="cc806-231">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="cc806-232">Varsa [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) Başlatıcı değişken alır veri türü (varsayılan), olduğunda.</span><span class="sxs-lookup"><span data-stu-id="cc806-232">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="cc806-233">Bkz: [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-233">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="cc806-234">Varsa `Option Infer` kapalıdır ve `Option Strict` kapalıysa, değişken veri türü alır `Object`.</span><span class="sxs-lookup"><span data-stu-id="cc806-234">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="cc806-235">Varsa `Option Infer` kapalıdır ve `Option Strict` olduğundan, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="cc806-235">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="cc806-236">Evet</span><span class="sxs-lookup"><span data-stu-id="cc806-236">Yes</span></span>|<span data-ttu-id="cc806-237">Hayır</span><span class="sxs-lookup"><span data-stu-id="cc806-237">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="cc806-238">Değişken veri türü için varsayılan değer için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="cc806-238">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="cc806-239">Bu bölümde daha sonra tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="cc806-239">See the table later in this section.</span></span>|  
|<span data-ttu-id="cc806-240">Evet</span><span class="sxs-lookup"><span data-stu-id="cc806-240">Yes</span></span>|<span data-ttu-id="cc806-241">Evet</span><span class="sxs-lookup"><span data-stu-id="cc806-241">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="cc806-242">Başlatıcı'veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="cc806-242">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="cc806-243">Bir veri türü belirtin, ancak bir başlatıcı belirtmezseniz, Visual Basic veri türü için varsayılan değer değişkenine başlatır.</span><span class="sxs-lookup"><span data-stu-id="cc806-243">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="cc806-244">Aşağıdaki tabloda, varsayılan başlatma değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc806-244">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="cc806-245">Veri türü</span><span class="sxs-lookup"><span data-stu-id="cc806-245">Data type</span></span>|<span data-ttu-id="cc806-246">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="cc806-246">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="cc806-247">Tüm sayısal türler (de dahil olmak üzere `Byte` ve `SByte`)</span><span class="sxs-lookup"><span data-stu-id="cc806-247">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="cc806-248">0</span><span class="sxs-lookup"><span data-stu-id="cc806-248">0</span></span>|  
|`Char`|<span data-ttu-id="cc806-249">İkili 0</span><span class="sxs-lookup"><span data-stu-id="cc806-249">Binary 0</span></span>|  
|<span data-ttu-id="cc806-250">Tüm başvuru türleri (de dahil olmak üzere `Object`, `String`ve tüm Diziler)</span><span class="sxs-lookup"><span data-stu-id="cc806-250">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="cc806-251">12: 00'da, 1 yılının 1 Ocak (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="cc806-251">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="cc806-252">Ayrı bir değişken değilmiş gibi her bir yapı öğesinin başlatılır.</span><span class="sxs-lookup"><span data-stu-id="cc806-252">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="cc806-253">Bir dizi uzunluğu, bildirme, ancak öğeleri başlatma değil, her öğe ayrı bir değişken değilmiş gibi başlatılır.</span><span class="sxs-lookup"><span data-stu-id="cc806-253">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="cc806-254">Statik yerel değişken ömrü</span><span class="sxs-lookup"><span data-stu-id="cc806-254">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="cc806-255">A `Static` yerel değişken bu bildirilen yordamı daha uzun bir yaşam süresi yok.</span><span class="sxs-lookup"><span data-stu-id="cc806-255">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="cc806-256">Değişken ömrü sınırlarının yordamı olduğu bildirildi ve olup bağlı `Shared`.</span><span class="sxs-lookup"><span data-stu-id="cc806-256">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="cc806-257">Yordam bildirimi</span><span class="sxs-lookup"><span data-stu-id="cc806-257">Procedure declaration</span></span>|<span data-ttu-id="cc806-258">Değişkeni başlatılamadı</span><span class="sxs-lookup"><span data-stu-id="cc806-258">Variable initialized</span></span>|<span data-ttu-id="cc806-259">Varolan değişkeni durdurur</span><span class="sxs-lookup"><span data-stu-id="cc806-259">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="cc806-260">Bir modüle</span><span class="sxs-lookup"><span data-stu-id="cc806-260">In a module</span></span>|<span data-ttu-id="cc806-261">İlk kez yordamı çağrılır</span><span class="sxs-lookup"><span data-stu-id="cc806-261">The first time the procedure is called</span></span>|<span data-ttu-id="cc806-262">Program yürütme durduğunda</span><span class="sxs-lookup"><span data-stu-id="cc806-262">When your program stops execution</span></span>|  
|<span data-ttu-id="cc806-263">Sınıf veya yapı yordamdır `Shared`</span><span class="sxs-lookup"><span data-stu-id="cc806-263">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="cc806-264">İlk kez yordamı belirli bir örneğe veya sınıf veya yapı kendisini çağrılır</span><span class="sxs-lookup"><span data-stu-id="cc806-264">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="cc806-265">Program yürütme durduğunda</span><span class="sxs-lookup"><span data-stu-id="cc806-265">When your program stops execution</span></span>|  
|<span data-ttu-id="cc806-266">Sınıf veya yapı yordamı değil `Shared`</span><span class="sxs-lookup"><span data-stu-id="cc806-266">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="cc806-267">İlk kez yordamı belirli bir örneğinde çağrılır</span><span class="sxs-lookup"><span data-stu-id="cc806-267">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="cc806-268">Çöp toplama (GC) örneği serbest bırakıldığında</span><span class="sxs-lookup"><span data-stu-id="cc806-268">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="cc806-269">Öznitelikler ve değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="cc806-269">Attributes and Modifiers</span></span>  
 <span data-ttu-id="cc806-270">Öznitelikleri yalnızca üye değişkenleri için değil, yerel değişkenleri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-270">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="cc806-271">Bir öznitelik derlemenin meta verilerini, bilgileri yerel değişkenler gibi geçici depolama için anlamlı olmayan katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="cc806-271">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="cc806-272">Modül düzeyinde kullanamazsınız `Static` değiştiricisi üye değişkenleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="cc806-272">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="cc806-273">Yordam düzeyinde kullanamazsınız `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, veya herhangi bir erişim değiştiricileri yerel değişkenleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="cc806-273">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="cc806-274">Hangi kod sağlayarak bir değişkenine erişebileceği belirtebilirsiniz bir `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="cc806-274">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="cc806-275">Özel erişim için üye değişkenleri (dışında herhangi bir yordam) varsayılan sınıf ve modül ve yapısı üye değişkenleri varsayılan genel erişim için.</span><span class="sxs-lookup"><span data-stu-id="cc806-275">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="cc806-276">Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-276">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="cc806-277">Erişim değiştiricileri (yordam) içindeki yerel değişkenler kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="cc806-277">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="cc806-278">Belirleyebileceğiniz `WithEvents` yalnızca üye değişkenleri, yordam içindeki yerel değişkenler üzerinde değil.</span><span class="sxs-lookup"><span data-stu-id="cc806-278">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="cc806-279">Belirtirseniz `WithEvents`, değişken veri türü belirli bir sınıf türü olmamalıdır `Object`.</span><span class="sxs-lookup"><span data-stu-id="cc806-279">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="cc806-280">Bir dizi bildiremezsiniz `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="cc806-280">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="cc806-281">Olaylar hakkında daha fazla bilgi için bkz: [olayları](../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-281">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc806-282">Kod bir sınıf dışında yapısı veya modülü üye değişkenin adını bu sınıf, yapı veya modül adıyla nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc806-282">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="cc806-283">Bu yordam veya bloğu içinde herhangi bir yerel değişkeni için bir yordam veya blok başvuramaz dışındaki kod.</span><span class="sxs-lookup"><span data-stu-id="cc806-283">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="cc806-284">Yönetilen kaynakları serbest bırakma</span><span class="sxs-lookup"><span data-stu-id="cc806-284">Releasing Managed Resources</span></span>  
 <span data-ttu-id="cc806-285">.NET Framework Atık toplayıcısının bölümünüzün fazladan hiçbir kodlama olmadan yönetilen kaynakları siler.</span><span class="sxs-lookup"><span data-stu-id="cc806-285">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="cc806-286">Ancak, atık toplayıcının beklemek yerine yönetilen bir kaynağın elden uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-286">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="cc806-287">Bir sınıf, özellikle değerli ve olması kaynağı (örneğin, bir veritabanı bağlantısı veya dosya işleci) üzerine barındırıyorsa, artık kullanımda olmayan bir sınıf örneği temizlemek için sonraki çöp toplama kadar beklenecek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc806-287">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="cc806-288">Bir sınıf uygulayabilir <xref:System.IDisposable> arabirimi çöp toplama önce kaynakları serbest bırakmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc806-288">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="cc806-289">Arabirimi uygulayan bir sınıf kullanıma sunan bir `Dispose` hemen yayımlanacak değerli kaynakları zorlamak için çağrılan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc806-289">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="cc806-290">`Using` Deyimi bir kaynak alınırken, bir dizi deyimleri yürütme ve kaynak atma işlemini otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="cc806-290">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="cc806-291">Ancak, kaynak uygulamalıdır <xref:System.IDisposable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="cc806-291">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="cc806-292">Daha fazla bilgi için bkz: [kullanarak deyimi](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cc806-292">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc806-293">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc806-293">Example</span></span>  
 <span data-ttu-id="cc806-294">Aşağıdaki örnek kullanarak değişkenler bildirilmektedir `Dim` çeşitli seçenekler deyimiyle.</span><span class="sxs-lookup"><span data-stu-id="cc806-294">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="cc806-295">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc806-295">Example</span></span>  
 <span data-ttu-id="cc806-296">Aşağıdaki örnek, 1 ile 30 arasında asal sayılar listeler.</span><span class="sxs-lookup"><span data-stu-id="cc806-296">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="cc806-297">Yerel değişkenler kapsamını kodu açıklamaları açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cc806-297">The scope of local variables is described in code comments.</span></span>  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="cc806-298">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc806-298">Example</span></span>  
 <span data-ttu-id="cc806-299">Aşağıdaki örnekte, `speedValue` değişkeni sınıf düzeyinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cc806-299">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="cc806-300">`Private` Anahtar sözcüğü değişkeni bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc806-300">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="cc806-301">Değişkeni herhangi bir yordam tarafından erişilebilecek `Car` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cc806-301">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cc806-302">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc806-302">See Also</span></span>  
 [<span data-ttu-id="cc806-303">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="cc806-303">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="cc806-304">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="cc806-304">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="cc806-305">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="cc806-305">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="cc806-306">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="cc806-306">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="cc806-307">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="cc806-307">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="cc806-308">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc806-308">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="cc806-309">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="cc806-309">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="cc806-310">Diziler</span><span class="sxs-lookup"><span data-stu-id="cc806-310">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="cc806-311">Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="cc806-311">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="cc806-312">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="cc806-312">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="cc806-313">Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="cc806-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="cc806-314">Nasıl yapılır: Nesne Başlatıcısı Kullanarak Nesne Bildirme</span><span class="sxs-lookup"><span data-stu-id="cc806-314">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [<span data-ttu-id="cc806-315">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="cc806-315">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
