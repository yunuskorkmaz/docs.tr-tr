---
title: Dim Deyimi (Visual Basic)
ms.date: 05/12/2018
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
ms.openlocfilehash: cab1cc07d23a44e57bdb0962a323b014308cb1e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836564"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="abf95-102">Dim Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abf95-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="abf95-103">Bildirir ve değişkenleri bir veya daha fazla depolama alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="abf95-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf95-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abf95-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="abf95-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="abf95-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="abf95-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-106">Optional.</span></span> <span data-ttu-id="abf95-107">Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="abf95-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-108">Optional.</span></span> <span data-ttu-id="abf95-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="abf95-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="abf95-110">Public</span><span class="sxs-lookup"><span data-stu-id="abf95-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="abf95-111">Protected</span><span class="sxs-lookup"><span data-stu-id="abf95-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="abf95-112">Friend</span><span class="sxs-lookup"><span data-stu-id="abf95-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="abf95-113">Private</span><span class="sxs-lookup"><span data-stu-id="abf95-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [<span data-ttu-id="abf95-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="abf95-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="abf95-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="abf95-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

     <span data-ttu-id="abf95-116">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="abf95-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-117">Optional.</span></span> <span data-ttu-id="abf95-118">Bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-118">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="abf95-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-119">Optional.</span></span> <span data-ttu-id="abf95-120">Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="abf95-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-121">Optional.</span></span> <span data-ttu-id="abf95-122">Bkz: [statik](../../../visual-basic/language-reference/modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-122">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="abf95-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-123">Optional.</span></span> <span data-ttu-id="abf95-124">Bkz: [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-124">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="abf95-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-125">Optional.</span></span> <span data-ttu-id="abf95-126">Bunlar, olayları tetikleyebilen bir sınıf örneklerine bakın nesne değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="abf95-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="abf95-127">Bkz: [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-127">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="abf95-128">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="abf95-128">Required.</span></span> <span data-ttu-id="abf95-129">Bu deyiminde bildirilen değişkenlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="abf95-129">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="abf95-130">Her `variable` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="abf95-130">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="abf95-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="abf95-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="abf95-132">Bölümü</span><span class="sxs-lookup"><span data-stu-id="abf95-132">Part</span></span>|<span data-ttu-id="abf95-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abf95-133">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="abf95-134">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="abf95-134">Required.</span></span> <span data-ttu-id="abf95-135">Değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="abf95-135">Name of the variable.</span></span> <span data-ttu-id="abf95-136">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-136">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="abf95-137">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-137">Optional.</span></span> <span data-ttu-id="abf95-138">Her boyut bir dizi değişkeni sınırlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="abf95-138">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="abf95-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-139">Optional.</span></span> <span data-ttu-id="abf95-140">Sınıfının yeni bir örneğini oluşturur, `Dim` deyimi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="abf95-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="abf95-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-141">Optional.</span></span> <span data-ttu-id="abf95-142">Değişken veri türü.</span><span class="sxs-lookup"><span data-stu-id="abf95-142">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="abf95-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-143">Optional.</span></span> <span data-ttu-id="abf95-144">Nesne başlatıcı listesi tanıtır.</span><span class="sxs-lookup"><span data-stu-id="abf95-144">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="abf95-145">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="abf95-145">Optional.</span></span> <span data-ttu-id="abf95-146">Bir sınıf özelliği adı örneği hale getiriyoruz.</span><span class="sxs-lookup"><span data-stu-id="abf95-146">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="abf95-147">Sonra gerekli `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="abf95-147">Required after `propertyname` =.</span></span> <span data-ttu-id="abf95-148">Değerlendirilir ve özellik adına atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="abf95-148">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="abf95-149">İsteğe bağlı ise `New` belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="abf95-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="abf95-150">Değerlendirilir ve oluşturulduğu sırada değişkene atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="abf95-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abf95-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abf95-151">Remarks</span></span>  
 <span data-ttu-id="abf95-152">Visual Basic Derleyicisi kullanan `Dim` değişkenin veri türü ve hangi kod değişkenine erişebileceği gibi diğer bilgileri belirlemek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="abf95-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="abf95-153">Aşağıdaki örnek, tutacak bir değişken bildirir. bir `Integer` değeri.</span><span class="sxs-lookup"><span data-stu-id="abf95-153">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="abf95-154">Herhangi bir veri türü veya bir sabit listesi, yapısı, sınıf veya arabirim adını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="abf95-155">Bir başvuru türü için kullandığınız `New` sınıfının yeni bir örneğini oluşturmak veya bu yapı için anahtar sözcüğü veri türü tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="abf95-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="abf95-156">Kullanırsanız `New`, bir başlatıcı ifadesinin kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="abf95-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="abf95-157">Bunun yerine, değişken oluşturmakta olduğunuz sınıf oluşturucusuna gerekli iseler bağımsız değişken sağlayın.</span><span class="sxs-lookup"><span data-stu-id="abf95-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="abf95-158">Yordamı, blok, sınıf, yapı veya modül bir değişkende bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="abf95-159">İçinde bir değişken bir kaynak dosyası, ad alanı veya arabirimi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="abf95-160">Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-160">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="abf95-161">Dışında herhangi bir yordam Modül düzeyinde bildirilmiş bir değişken bir *üye değişkeni* veya *alan*.</span><span class="sxs-lookup"><span data-stu-id="abf95-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="abf95-162">Üye değişkenleri kendi sınıf, yapı veya modül boyunca kapsamına dahildir.</span><span class="sxs-lookup"><span data-stu-id="abf95-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="abf95-163">Yordam düzeyinde bildirilen bir değişken bir *yerel değişken*.</span><span class="sxs-lookup"><span data-stu-id="abf95-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="abf95-164">Yerel değişkenler yalnızca kendi yordam veya blok içinde kapsamına dahildir.</span><span class="sxs-lookup"><span data-stu-id="abf95-164">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="abf95-165">Aşağıdaki erişim değiştiriciler yordam dışında değişkenler bildirmek için kullanılır: `Public`, `Protected`, `Friend`, `Protected Friend`, ve `Private`.</span><span class="sxs-lookup"><span data-stu-id="abf95-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="abf95-166">Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-166">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="abf95-167">`Dim` Anahtar sözcüğü, isteğe bağlıdır ve aşağıdaki değiştiriciler belirtirseniz, genellikle atlanmış: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, veya `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="abf95-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="abf95-168">Varsa `Option Explicit` olduğunu (varsayılan), derleyici bir bildirimi kullandığınız her değişken için gerektirir.</span><span class="sxs-lookup"><span data-stu-id="abf95-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="abf95-169">Daha fazla bilgi için [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-169">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="abf95-170">Bir başlangıç değeri belirtme</span><span class="sxs-lookup"><span data-stu-id="abf95-170">Specifying an Initial Value</span></span>  
 <span data-ttu-id="abf95-171">Oluşturulduğunda bir değişkene bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="abf95-172">Bir değer türü için kullandığınız bir *Başlatıcı* değişkene atanmış bir ifade sağlamanız için.</span><span class="sxs-lookup"><span data-stu-id="abf95-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="abf95-173">Derleme zamanında hesaplanabilen bir sabit ifade değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="abf95-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="abf95-174">Bir başlatıcı belirtilirse ve bir veri türü belirtilmedi bir `As` yan tümcesi *anlam çıkarma* veri türü başlatıcıdan çıkarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abf95-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="abf95-175">Aşağıdaki örnekte, her ikisi de `num1` ve `num2` tamsayı olarak kesin olarak belirlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="abf95-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="abf95-176">İkinci bildiriminde tür çıkarımını 3 değeri türünden çıkarır.</span><span class="sxs-lookup"><span data-stu-id="abf95-176">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="abf95-177">Tür çıkarımı yordam düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="abf95-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="abf95-178">Bir yordamda bir sınıf, yapı, modül veya arabirimi dışından uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="abf95-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="abf95-179">Tür çıkarımı hakkında daha fazla bilgi için bkz: [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-179">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="abf95-180">Bir veri türü veya Başlatıcı belirtilmediğinde neler olduğu hakkında daha fazla bilgi için bkz: [varsayılan veri türleri ve değerleri](../../../visual-basic/language-reference/statements/dim-statement.md#default) bu konuda.</span><span class="sxs-lookup"><span data-stu-id="abf95-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="abf95-181">Kullanabileceğiniz bir *nesne Başlatıcı* adlandırılmış ve anonim türlerin örneklerini bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="abf95-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="abf95-182">Aşağıdaki kod örneği oluşturur. bir `Student` sınıfı ve özellikleri başlatmak için bir nesne Başlatıcı kullanır.</span><span class="sxs-lookup"><span data-stu-id="abf95-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="abf95-183">Nesne başlatıcıları hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir nesne Başlatıcı kullanarak nesne bildirme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), ve [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="abf95-184">Birden fazla değişken bildirme</span><span class="sxs-lookup"><span data-stu-id="abf95-184">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="abf95-185">Parantezler ile her biri için ve her dizi adı aşağıdaki değişken adını belirten bir bildirim deyiminde, çeşitli değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="abf95-186">Birden fazla değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="abf95-186">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="abf95-187">Bir sahip birden fazla değişken bildirirseniz `As` yan tümcesi, o grubu değişkenlerin bir başlatıcı sağlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="abf95-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="abf95-188">Ayrı bir kullanarak farklı veri türleri için farklı değişkenleri belirtebilirsiniz `As` bildirdiğiniz her bir değişken yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="abf95-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="abf95-189">Her bir değişken ilk belirtilen veri türü alan `As` yan tümcesi karşılaştı sonra kendi `variablename` bölümü.</span><span class="sxs-lookup"><span data-stu-id="abf95-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="abf95-190">Diziler</span><span class="sxs-lookup"><span data-stu-id="abf95-190">Arrays</span></span>  
 <span data-ttu-id="abf95-191">Tutacak bir değişken bildirmek bir *dizi*, birden çok değer tutabilir.</span><span class="sxs-lookup"><span data-stu-id="abf95-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="abf95-192">Bir değişken bir dizi tutan belirtmek için izleyin, `variablename` parantez olmadan hemen.</span><span class="sxs-lookup"><span data-stu-id="abf95-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="abf95-193">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-193">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="abf95-194">Alt ve bir dizinin her boyutunun üst sınırını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="abf95-195">Bunu yapmak için dahil bir `boundslist` parantez içinde.</span><span class="sxs-lookup"><span data-stu-id="abf95-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="abf95-196">Her boyut için `boundslist` üst sınırı ve isteğe bağlı alt sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="abf95-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="abf95-197">Olup olmadığını belirtin alt sınırı her zaman sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="abf95-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="abf95-198">Her dizin aracılığıyla üst sınır değeri sıfırdan farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="abf95-198">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="abf95-199">Aşağıdaki iki deyimi eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="abf95-199">The following two statements are equivalent.</span></span> <span data-ttu-id="abf95-200">Her deyim 21 dizisi bildirir `Integer` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="abf95-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="abf95-201">Dizi eriştiğinizde, dizin 0 ile 20 arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="abf95-201">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="abf95-202">Aşağıdaki deyim türünde iki boyutlu bir dizi bildirir `Double`.</span><span class="sxs-lookup"><span data-stu-id="abf95-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="abf95-203">Dizi 6 sütunlar (5 + 1) her biri 4 satır (3 + 1) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="abf95-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="abf95-204">Bir üst sınır boyutun uzunluğu dizini için olası en yüksek değere temsil ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="abf95-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="abf95-205">Boyutun uzunluğu üst sınırı artı bir taneyi ' dir.</span><span class="sxs-lookup"><span data-stu-id="abf95-205">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="abf95-206">Bir dizi 1 ila 32 boyutlara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="abf95-206">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="abf95-207">Tüm sınırların bir dizi bildirimi boş bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="abf95-208">Bunu yaparsanız, belirttiğiniz boyutların sayısı dizi sahiptir, ancak başlatılmamış.</span><span class="sxs-lookup"><span data-stu-id="abf95-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="abf95-209">Değerine sahip `Nothing` en az başlatmak kadar bazı alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="abf95-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="abf95-210">`Dim` Deyimi tüm boyutlar veya hiç boyut sınırları belirtin.</span><span class="sxs-lookup"><span data-stu-id="abf95-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="abf95-211">Dizi boyut birden fazla varsa, virgül boyut sayısını göstermek için parantez içermelidir.</span><span class="sxs-lookup"><span data-stu-id="abf95-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="abf95-212">Bildirebilirsiniz bir *sıfır uzunluklu dizi* göre -1 olarak dizi boyutlarından birini bildirme.</span><span class="sxs-lookup"><span data-stu-id="abf95-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="abf95-213">Sıfır uzunluğunda diziyi tutan değişken değeri yok `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="abf95-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="abf95-214">Sıfır uzunlukta diziler bazı ortak dil çalışma zamanı işlevleri tarafından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="abf95-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="abf95-215">Böyle bir dizi erişmeye çalışırsanız bir çalışma zamanı özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="abf95-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="abf95-216">Daha fazla bilgi için [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-216">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="abf95-217">Dizi değişmez değeri kullanarak dizi değerlerini başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="abf95-218">Bunu yapmak için Küme ayraçları başlatma değerlerle çevreleyen (`{}`).</span><span class="sxs-lookup"><span data-stu-id="abf95-218">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="abf95-219">Çok boyutlu diziler için başlatma ayrı her boyut için dış boyutundaki köşeli ayraçlar içine alınır.</span><span class="sxs-lookup"><span data-stu-id="abf95-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="abf95-220">Öğeler satır ağırlıklı sırada belirtilir.</span><span class="sxs-lookup"><span data-stu-id="abf95-220">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="abf95-221">Dizi değişmez değerleri hakkında daha fazla bilgi için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-221">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="default"></a> <span data-ttu-id="abf95-222">Varsayılan veri türleri ve değerleri</span><span class="sxs-lookup"><span data-stu-id="abf95-222">Default Data Types and Values</span></span>  
 <span data-ttu-id="abf95-223">Aşağıdaki tabloda çeşitli birleşimlerini başlatıcısında ve veri türünü belirtmenin sonuçlarını açıklar bir `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="abf95-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="abf95-224">Belirtilen veri türü?</span><span class="sxs-lookup"><span data-stu-id="abf95-224">Data type specified?</span></span>|<span data-ttu-id="abf95-225">Belirtilen başlatıcı?</span><span class="sxs-lookup"><span data-stu-id="abf95-225">Initializer specified?</span></span>|<span data-ttu-id="abf95-226">Örnek</span><span class="sxs-lookup"><span data-stu-id="abf95-226">Example</span></span>|<span data-ttu-id="abf95-227">Sonuç</span><span class="sxs-lookup"><span data-stu-id="abf95-227">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="abf95-228">Hayır</span><span class="sxs-lookup"><span data-stu-id="abf95-228">No</span></span>|<span data-ttu-id="abf95-229">Hayır</span><span class="sxs-lookup"><span data-stu-id="abf95-229">No</span></span>|`Dim qty`|<span data-ttu-id="abf95-230">Varsa [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) olan kapalı (varsayılan), değişkeni ayarlanır `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="abf95-230">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="abf95-231">Varsa `Option Strict` açıktır, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="abf95-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="abf95-232">Hayır</span><span class="sxs-lookup"><span data-stu-id="abf95-232">No</span></span>|<span data-ttu-id="abf95-233">Evet</span><span class="sxs-lookup"><span data-stu-id="abf95-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="abf95-234">Varsa [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) değişken alır veri öğesinin başlatıcısını yazın (varsayılan), olan.</span><span class="sxs-lookup"><span data-stu-id="abf95-234">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="abf95-235">Bkz: [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-235">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="abf95-236">Varsa `Option Infer` kapalıdır ve `Option Strict` kapalıysa, değişken veri türünü alan `Object`.</span><span class="sxs-lookup"><span data-stu-id="abf95-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="abf95-237">Varsa `Option Infer` kapalıdır ve `Option Strict` açıktır, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="abf95-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="abf95-238">Evet</span><span class="sxs-lookup"><span data-stu-id="abf95-238">Yes</span></span>|<span data-ttu-id="abf95-239">Hayır</span><span class="sxs-lookup"><span data-stu-id="abf95-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="abf95-240">Değişken veri türü için varsayılan değer için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="abf95-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="abf95-241">Bu bölümdeki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="abf95-241">See the table later in this section.</span></span>|  
|<span data-ttu-id="abf95-242">Evet</span><span class="sxs-lookup"><span data-stu-id="abf95-242">Yes</span></span>|<span data-ttu-id="abf95-243">Evet</span><span class="sxs-lookup"><span data-stu-id="abf95-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="abf95-244">Başlatıcı veri türü belirtilen veri türüne dönüştürülebilir değil, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="abf95-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="abf95-245">Bir veri türü belirtin, ancak bir başlatıcı belirtmezseniz, Visual Basic veri türü için varsayılan değer değişkenine başlatır.</span><span class="sxs-lookup"><span data-stu-id="abf95-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="abf95-246">Aşağıdaki tabloda, varsayılan başlatma değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="abf95-246">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="abf95-247">Veri türü</span><span class="sxs-lookup"><span data-stu-id="abf95-247">Data type</span></span>|<span data-ttu-id="abf95-248">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="abf95-248">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="abf95-249">Tüm sayısal türlerin (dahil olmak üzere `Byte` ve `SByte`)</span><span class="sxs-lookup"><span data-stu-id="abf95-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="abf95-250">0</span><span class="sxs-lookup"><span data-stu-id="abf95-250">0</span></span>|  
|`Char`|<span data-ttu-id="abf95-251">İkili 0</span><span class="sxs-lookup"><span data-stu-id="abf95-251">Binary 0</span></span>|  
|<span data-ttu-id="abf95-252">Tüm başvuru türleri (dahil olmak üzere `Object`, `String`ve tüm Diziler)</span><span class="sxs-lookup"><span data-stu-id="abf95-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="abf95-253">12: 00'da, 1 yılının 1 Ocak (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="abf95-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="abf95-254">Bir yapının her öğe ayrı bir değişken gibi başlatılır.</span><span class="sxs-lookup"><span data-stu-id="abf95-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="abf95-255">Bir dizinin uzunluğu bildirmek, ancak öğeleri başlatmayın, her öğe ayrı bir değişken gibi başlatılır.</span><span class="sxs-lookup"><span data-stu-id="abf95-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="abf95-256">Statik yerel değişken ömrü</span><span class="sxs-lookup"><span data-stu-id="abf95-256">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="abf95-257">A `Static` yerel değişken bu bildirilen yordamın daha uzun bir ömrü vardır.</span><span class="sxs-lookup"><span data-stu-id="abf95-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="abf95-258">Değişkenin ömrü sınırları yordamı burada bildirilir ve olmasına bağlıdır `Shared`.</span><span class="sxs-lookup"><span data-stu-id="abf95-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="abf95-259">Yordam bildirimi</span><span class="sxs-lookup"><span data-stu-id="abf95-259">Procedure declaration</span></span>|<span data-ttu-id="abf95-260">Değişken başlatılmamış</span><span class="sxs-lookup"><span data-stu-id="abf95-260">Variable initialized</span></span>|<span data-ttu-id="abf95-261">Değişkeni mevcut durdurur.</span><span class="sxs-lookup"><span data-stu-id="abf95-261">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="abf95-262">Bir modülde</span><span class="sxs-lookup"><span data-stu-id="abf95-262">In a module</span></span>|<span data-ttu-id="abf95-263">İlk kez yordamı çağrılır</span><span class="sxs-lookup"><span data-stu-id="abf95-263">The first time the procedure is called</span></span>|<span data-ttu-id="abf95-264">Programınızı yürütme durduğunda</span><span class="sxs-lookup"><span data-stu-id="abf95-264">When your program stops execution</span></span>|  
|<span data-ttu-id="abf95-265">Bir sınıf veya yapı yordamdır `Shared`</span><span class="sxs-lookup"><span data-stu-id="abf95-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="abf95-266">İlk kez yordamı belirli bir örneğine veya sınıf veya yapının kendisi üzerinde çağrılır</span><span class="sxs-lookup"><span data-stu-id="abf95-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="abf95-267">Programınızı yürütme durduğunda</span><span class="sxs-lookup"><span data-stu-id="abf95-267">When your program stops execution</span></span>|  
|<span data-ttu-id="abf95-268">Bir sınıf veya yapı yordamı değil `Shared`</span><span class="sxs-lookup"><span data-stu-id="abf95-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="abf95-269">İlk kez yordamı belirli bir örneği üzerinde çağrılır</span><span class="sxs-lookup"><span data-stu-id="abf95-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="abf95-270">Çöp toplama (GC) örneği yayınlandığında</span><span class="sxs-lookup"><span data-stu-id="abf95-270">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="abf95-271">Öznitelikler ve değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="abf95-271">Attributes and Modifiers</span></span>  
 <span data-ttu-id="abf95-272">Öznitelikleri yalnızca değişkenlere, yerel değişkenler için uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="abf95-273">Bir öznitelik bilgileri derlemenin meta verilerini, geçici depolama gibi yerel değişkenleri için anlamlı değil katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="abf95-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="abf95-274">Modül düzeyinde kullanamazsınız `Static` değiştiricisi üye değişkenleri bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="abf95-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="abf95-275">Yordam düzeyinde kullanamazsınız `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, ya da herhangi bir erişim değiştiricilerine yerel değişkenler bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="abf95-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="abf95-276">Hangi kod sağlayarak bir değişkenine erişebileceği belirtebileceğiniz bir `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="abf95-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="abf95-277">Özel erişim için üye değişkenleri (dışında herhangi bir yordam) varsayılan sınıf ve modül ve yapı üyesi değişkenleri varsayılan genel erişim için.</span><span class="sxs-lookup"><span data-stu-id="abf95-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="abf95-278">Erişim değiştiricileri ile kullanıcıların erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="abf95-279">Erişim değiştiricileri (içinde bir yordam) yerel değişkenler kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="abf95-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="abf95-280">Belirtebileceğiniz `WithEvents` yalnızca değişkenlere, yordam içindeki yerel değişkenlere göre değil.</span><span class="sxs-lookup"><span data-stu-id="abf95-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="abf95-281">Belirtirseniz `WithEvents`, değişkenin veri türü, belirli bir sınıf türü olmamalıdır `Object`.</span><span class="sxs-lookup"><span data-stu-id="abf95-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="abf95-282">Bir dizi bildiremezsiniz `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="abf95-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="abf95-283">Olaylar hakkında daha fazla bilgi için bkz. [olayları](../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-283">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abf95-284">Kod bir sınıf dışında yapısını veya modülünü bir üye değişkeninin adı bu sınıf, yapı veya modül adıyla nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="abf95-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="abf95-285">Bir yordam veya blok Bu yordam veya blok içinde herhangi bir yerel değişkenlere başvuruda bulunamaz dışındaki kod.</span><span class="sxs-lookup"><span data-stu-id="abf95-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="abf95-286">Yönetilen kaynakları serbest bırakma</span><span class="sxs-lookup"><span data-stu-id="abf95-286">Releasing Managed Resources</span></span>  
 <span data-ttu-id="abf95-287">Ek kodlamaya bulunmanıza gerek kalmadan, .NET Framework atık toplayıcı yönetilen kaynakları siler.</span><span class="sxs-lookup"><span data-stu-id="abf95-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="abf95-288">Bununla birlikte, çöp toplayıcının beklemek yerine bir yönetilen kaynak elden zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="abf95-289">Bir sınıf, özellikle değerli ve nadir bir kaynak (örneğin, bir veritabanı bağlantısı veya dosya tanıtıcısı) üzerine tutuyorsa artık kullanımda olmayan bir sınıf örneğini temizlemek için bir sonraki atık koleksiyonuna kadar beklemek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf95-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="abf95-290">Bir sınıf uygulayabilir <xref:System.IDisposable> çöp toplama önce kaynakları serbest bırakmak için bir yol sağlamak üzere arabirimi.</span><span class="sxs-lookup"><span data-stu-id="abf95-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="abf95-291">Arabirimi uygulayan bir sınıfı gösterir bir `Dispose` değerli kaynakları hemen serbest bırakılması zorlamak için çağrılabilen bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="abf95-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="abf95-292">`Using` Deyimi bir kaynağı alma, bir dizi deyimleri yürütme ve ardından kaynak disposing işlemini otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="abf95-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="abf95-293">Ancak, kaynak uygulamalıdır <xref:System.IDisposable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="abf95-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="abf95-294">Daha fazla bilgi için [Using deyimi](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="abf95-294">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="abf95-295">Örnek</span><span class="sxs-lookup"><span data-stu-id="abf95-295">Example</span></span>  
 <span data-ttu-id="abf95-296">Aşağıdaki örneği kullanarak değişkenler bildirilmektedir `Dim` çeşitli seçeneklerle deyimi.</span><span class="sxs-lookup"><span data-stu-id="abf95-296">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 [!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]  
  
## <a name="example"></a><span data-ttu-id="abf95-297">Örnek</span><span class="sxs-lookup"><span data-stu-id="abf95-297">Example</span></span>  
 <span data-ttu-id="abf95-298">Aşağıdaki örnek, 1 ile 30 arasında asal sayıları listeler.</span><span class="sxs-lookup"><span data-stu-id="abf95-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="abf95-299">Yerel değişkenler kapsamını, kod açıklamaları açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="abf95-299">The scope of local variables is described in code comments.</span></span>  
  
 [!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]  
  
## <a name="example"></a><span data-ttu-id="abf95-300">Örnek</span><span class="sxs-lookup"><span data-stu-id="abf95-300">Example</span></span>  
 <span data-ttu-id="abf95-301">Aşağıdaki örnekte, `speedValue` sınıf düzeyinde bildirilen değişkenin.</span><span class="sxs-lookup"><span data-stu-id="abf95-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="abf95-302">`Private` Anahtar sözcüğü bir değişken bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abf95-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="abf95-303">Değişken, herhangi bir yordam tarafından erişilebilen `Car` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="abf95-303">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 [!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]  
  
 [!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]  
  
## <a name="see-also"></a><span data-ttu-id="abf95-304">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abf95-304">See also</span></span>

- [<span data-ttu-id="abf95-305">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="abf95-305">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="abf95-306">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="abf95-306">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="abf95-307">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="abf95-307">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="abf95-308">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="abf95-308">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="abf95-309">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="abf95-309">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="abf95-310">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abf95-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="abf95-311">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="abf95-311">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="abf95-312">Diziler</span><span class="sxs-lookup"><span data-stu-id="abf95-312">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="abf95-313">Nesne başlatıcıları: Adlandırılmış ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="abf95-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="abf95-314">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="abf95-314">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="abf95-315">Nesne başlatıcıları: Adlandırılmış ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="abf95-315">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="abf95-316">Nasıl yapılır: Bir nesne Başlatıcı kullanarak nesne bildirme</span><span class="sxs-lookup"><span data-stu-id="abf95-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="abf95-317">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="abf95-317">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
