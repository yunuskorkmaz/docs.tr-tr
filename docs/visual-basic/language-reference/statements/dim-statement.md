---
title: Dim deyimi
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
ms.openlocfilehash: 1b0c3089c366c417af926c8c0703cea021674432
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744730"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="8ff20-102">Dim ekstresi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ff20-102">Dim statement (Visual Basic)</span></span>

<span data-ttu-id="8ff20-103">Bir veya daha fazla değişken için depolama alanı bildirir ve ayırır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-103">Declares and allocates storage space for one or more variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="8ff20-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ff20-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a><span data-ttu-id="8ff20-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8ff20-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="8ff20-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-106">Optional.</span></span> <span data-ttu-id="8ff20-107">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="8ff20-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-108">Optional.</span></span> <span data-ttu-id="8ff20-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="8ff20-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="8ff20-110">Public</span><span class="sxs-lookup"><span data-stu-id="8ff20-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="8ff20-111">Protected</span><span class="sxs-lookup"><span data-stu-id="8ff20-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="8ff20-112">Friend</span><span class="sxs-lookup"><span data-stu-id="8ff20-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="8ff20-113">Private</span><span class="sxs-lookup"><span data-stu-id="8ff20-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="8ff20-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="8ff20-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="8ff20-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="8ff20-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="8ff20-116">[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8ff20-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `Shared`

  <span data-ttu-id="8ff20-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-117">Optional.</span></span> <span data-ttu-id="8ff20-118">Bkz. [paylaşılan](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-118">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="8ff20-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-119">Optional.</span></span> <span data-ttu-id="8ff20-120">Bkz. [gölgeler](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-120">See [Shadows](../modifiers/shadows.md).</span></span>

- `Static`

  <span data-ttu-id="8ff20-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-121">Optional.</span></span> <span data-ttu-id="8ff20-122">Bkz. [statik](../modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-122">See [Static](../modifiers/static.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="8ff20-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-123">Optional.</span></span> <span data-ttu-id="8ff20-124">Bkz. [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-124">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WithEvents`

  <span data-ttu-id="8ff20-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-125">Optional.</span></span> <span data-ttu-id="8ff20-126">Bunların, olayları yükseltebileceği bir sınıfın örneklerine başvuran nesne değişkenleri olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="8ff20-127">Bkz. [WithEvents](../modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-127">See [WithEvents](../modifiers/withevents.md).</span></span>

- `variablelist`

  <span data-ttu-id="8ff20-128">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8ff20-128">Required.</span></span> <span data-ttu-id="8ff20-129">Bu bildirimde bildirildiği değişkenlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="8ff20-129">List of variables being declared in this statement.</span></span>

  `variable [ , variable ... ]`

  <span data-ttu-id="8ff20-130">Her `variable` aşağıdaki söz dizimi ve bölümlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8ff20-130">Each `variable` has the following syntax and parts:</span></span>

  <span data-ttu-id="8ff20-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="8ff20-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>

  |<span data-ttu-id="8ff20-132">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="8ff20-132">Part</span></span>|<span data-ttu-id="8ff20-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ff20-133">Description</span></span>|
  |---|---|
  |`variablename`|<span data-ttu-id="8ff20-134">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8ff20-134">Required.</span></span> <span data-ttu-id="8ff20-135">Değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-135">Name of the variable.</span></span> <span data-ttu-id="8ff20-136">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-136">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
  |`boundslist`|<span data-ttu-id="8ff20-137">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-137">Optional.</span></span> <span data-ttu-id="8ff20-138">Bir dizi değişkeninin her boyutunun sınırları listesi.</span><span class="sxs-lookup"><span data-stu-id="8ff20-138">List of bounds of each dimension of an array variable.</span></span>|
  |`New`|<span data-ttu-id="8ff20-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-139">Optional.</span></span> <span data-ttu-id="8ff20-140">`Dim` deyimleri çalıştırıldığında, sınıfının yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ff20-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|
  |`datatype`|<span data-ttu-id="8ff20-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-141">Optional.</span></span> <span data-ttu-id="8ff20-142">Değişkenin veri türü.</span><span class="sxs-lookup"><span data-stu-id="8ff20-142">Data type of the variable.</span></span>|
  |`With`|<span data-ttu-id="8ff20-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-143">Optional.</span></span> <span data-ttu-id="8ff20-144">Nesne Başlatıcısı listesini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-144">Introduces the object initializer list.</span></span>|
  |`propertyname`|<span data-ttu-id="8ff20-145">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-145">Optional.</span></span> <span data-ttu-id="8ff20-146">Örneği yaptığınız sınıftaki bir özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="8ff20-146">The name of a property in the class you are making an instance of.</span></span>|
  |`propinitializer`|<span data-ttu-id="8ff20-147">`propertyname` = sonra gerekli.</span><span class="sxs-lookup"><span data-stu-id="8ff20-147">Required after `propertyname` =.</span></span> <span data-ttu-id="8ff20-148">Değerlendirilen ve özellik adına atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="8ff20-148">The expression that is evaluated and assigned to the property name.</span></span>|
  |`initializer`|<span data-ttu-id="8ff20-149">`New` belirtilmemişse isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="8ff20-150">Değerlendirilen ve değişken oluşturulduğunda değişkene atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="8ff20-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8ff20-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ff20-151">Remarks</span></span>

<span data-ttu-id="8ff20-152">Visual Basic derleyici, değişkenin veri türünü ve hangi kodun değişkene erişebileceği gibi diğer bilgileri belirlemek için `Dim` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="8ff20-153">Aşağıdaki örnek bir `Integer` değerini tutacak bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-153">The following example declares a variable to hold an `Integer` value.</span></span>

```vb
Dim numberOfStudents As Integer
```

<span data-ttu-id="8ff20-154">Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

<span data-ttu-id="8ff20-155">Bir başvuru türü için, veri türü tarafından belirtilen sınıf veya yapının yeni bir örneğini oluşturmak üzere `New` anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8ff20-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="8ff20-156">`New`kullanıyorsanız, başlatıcı ifadesi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="8ff20-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="8ff20-157">Bunun yerine, varsa bağımsız değişkenleri değişkeni oluşturduğunuz sınıfın oluşturucusuna sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="8ff20-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

<span data-ttu-id="8ff20-158">Bir yordam, blok, sınıf, yapı veya modülde bir değişken bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="8ff20-159">Bir kaynak dosyasında, ad alanında veya arabirimde bir değişken bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="8ff20-160">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-160">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="8ff20-161">Modül düzeyinde belirtilen bir değişken, herhangi bir yordam dışında, bir *üye değişkeni* veya *alanıdır*.</span><span class="sxs-lookup"><span data-stu-id="8ff20-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="8ff20-162">Üye değişkenleri, sınıfları, yapısı veya modülleri genelinde kapsamdadır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="8ff20-163">Yordam düzeyinde belirtilen bir değişken *yerel bir değişkendir*.</span><span class="sxs-lookup"><span data-stu-id="8ff20-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="8ff20-164">Yerel değişkenler yalnızca kendi yordamı veya blokları içinde kapsamdadır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-164">Local variables are in scope only within their procedure or block.</span></span>

<span data-ttu-id="8ff20-165">Aşağıdaki erişim değiştiricileri, değişkenleri bir yordam dışında bildirmek için kullanılır: `Public`, `Protected`, `Friend`, `Protected Friend`ve `Private`.</span><span class="sxs-lookup"><span data-stu-id="8ff20-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="8ff20-166">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-166">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="8ff20-167">`Dim` anahtar sözcüğü isteğe bağlıdır ve aşağıdaki değiştiricilerin herhangi birini belirtirseniz genellikle atlanır: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`veya `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="8ff20-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

<span data-ttu-id="8ff20-168">`Option Explicit` açık ise (varsayılan), derleyici kullandığınız her değişken için bir bildirim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="8ff20-169">Daha fazla bilgi için bkz. [Option Explicit deyimdir](option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-169">For more information, see [Option Explicit Statement](option-explicit-statement.md).</span></span>

## <a name="specifying-an-initial-value"></a><span data-ttu-id="8ff20-170">Bir başlangıç değeri belirtme</span><span class="sxs-lookup"><span data-stu-id="8ff20-170">Specifying an initial value</span></span>

<span data-ttu-id="8ff20-171">Bir değişkene, oluşturulduğunda bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="8ff20-172">Değer türü için, değişkene atanacak bir ifade sağlamak üzere bir *Başlatıcı* kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8ff20-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="8ff20-173">İfade, derleme zamanında hesaplanabilecek bir sabit olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

<span data-ttu-id="8ff20-174">Bir başlatıcı belirtilmişse ve bir `As` yan tümcesinde veri türü belirtilmemişse, veri türünü başlatıcıdan çıkarsmak için *tür çıkarımı* kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="8ff20-175">Aşağıdaki örnekte, hem `num1` hem de `num2` kesin olarak tam sayı olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="8ff20-176">İkinci bildirimde, tür çıkarımı tür 3 ' ten yazın.</span><span class="sxs-lookup"><span data-stu-id="8ff20-176">In the second declaration, type inference infers the type from the value 3.</span></span>

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

<span data-ttu-id="8ff20-177">Tür çıkarımı yordam düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="8ff20-178">Bir sınıf, yapı, modül veya arabirimdeki bir yordamın dışında uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="8ff20-179">Tür çıkarımı hakkında daha fazla bilgi için bkz. [Option Infer deyimleri](option-infer-statement.md) ve [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-179">For more information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="8ff20-180">Veri türü veya Başlatıcı belirtilmediğinde ne olacağı hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alarak [varsayılan veri türleri ve değerleri](dim-statement.md#default) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8ff20-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](dim-statement.md#default) later in this topic.</span></span>

<span data-ttu-id="8ff20-181">Adlandırılmış ve anonim türlerin örneklerini bildirmek için bir *nesne Başlatıcısı* kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="8ff20-182">Aşağıdaki kod `Student` sınıfının bir örneğini oluşturur ve özellikleri başlatmak için bir nesne Başlatıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

<span data-ttu-id="8ff20-183">Nesne başlatıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: nesne Başlatıcısı](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [nesne başlatıcıları: adlandırılmış ve anonim türler](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)ve [anonim türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)kullanarak nesne bildirme.</span><span class="sxs-lookup"><span data-stu-id="8ff20-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="declaring-multiple-variables"></a><span data-ttu-id="8ff20-184">Birden çok değişken bildirme</span><span class="sxs-lookup"><span data-stu-id="8ff20-184">Declaring multiple variables</span></span>

<span data-ttu-id="8ff20-185">Tek bir bildirim ifadesinde, her biri için değişken adını belirterek ve her dizi adını parantez ile izleyerek birkaç değişken bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="8ff20-186">Birden çok değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-186">Multiple variables are separated by commas.</span></span>

```vb
Dim lastTime, nextTime, allTimes() As Date
```

<span data-ttu-id="8ff20-187">Bir `As` yan tümcesiyle birden fazla değişken bildirirseniz, bu değişken grubu için bir başlatıcı sağlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8ff20-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>

<span data-ttu-id="8ff20-188">Farklı değişkenler için, bildirdiğiniz her değişken için ayrı bir `As` yan tümcesi kullanarak farklı veri türleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="8ff20-189">Her değişken, `variablename` bölümünün ardından karşılaşılan ilk `As` yan tümcesinde belirtilen veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a><span data-ttu-id="8ff20-190">Diziler</span><span class="sxs-lookup"><span data-stu-id="8ff20-190">Arrays</span></span>

<span data-ttu-id="8ff20-191">Birden çok değer içerebilen bir *diziyi*tutacak bir değişken bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="8ff20-192">Bir değişkenin bir diziyi bulundurduğunu belirtmek için, parantez ile hemen `variablename` izleyin.</span><span class="sxs-lookup"><span data-stu-id="8ff20-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="8ff20-193">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-193">For more information about arrays, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="8ff20-194">Bir dizinin her boyutunun alt ve üst sınırını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="8ff20-195">Bunu yapmak için, parantez içine bir `boundslist` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8ff20-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="8ff20-196">Her boyut için `boundslist` üst sınırı ve isteğe bağlı olarak alt sınırı belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="8ff20-197">Alt sınır, sizin belirtmeksizin her zaman sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="8ff20-198">Her dizin, üst sınır değeri ile sıfırdan farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-198">Each index can vary from zero through its upper bound value.</span></span>

<span data-ttu-id="8ff20-199">Aşağıdaki iki deyim eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-199">The following two statements are equivalent.</span></span> <span data-ttu-id="8ff20-200">Her bir ifade 21 `Integer` öğelerinden oluşan bir dizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="8ff20-201">Diziye eriştiğinizde, dizin 0 ile 20 arasında farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-201">When you access the array, the index can vary from 0 through 20.</span></span>

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

<span data-ttu-id="8ff20-202">Aşağıdaki ifade `Double`türünde iki boyutlu bir dizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="8ff20-203">Dizide 4 satır (3 + 1) 6 sütun (5 + 1) bulunur.</span><span class="sxs-lookup"><span data-stu-id="8ff20-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="8ff20-204">Üst sınır, boyutun uzunluğunu değil, dizin için mümkün olan en yüksek değeri temsil ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ff20-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="8ff20-205">Boyutun uzunluğu üst sınır artı bir değer.</span><span class="sxs-lookup"><span data-stu-id="8ff20-205">The length of the dimension is the upper bound plus one.</span></span>

```vb
Dim matrix2(3, 5) As Double
```

<span data-ttu-id="8ff20-206">Bir dizi 1 ile 32 arasında boyutlara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-206">An array can have from 1 to 32 dimensions.</span></span>

<span data-ttu-id="8ff20-207">Bir dizi bildiriminde tüm sınırların boş kalmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="8ff20-208">Bunu yaparsanız dizi, belirttiğiniz boyut sayısına sahiptir ancak başlatılmamış olur.</span><span class="sxs-lookup"><span data-stu-id="8ff20-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="8ff20-209">Öğelerinin en az bir kısmını başlatana kadar bir `Nothing` değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="8ff20-210">`Dim` deyimin tüm boyutlar veya hiçbir boyut için sınır belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

<span data-ttu-id="8ff20-211">Dizide birden fazla boyut varsa, boyut sayısını göstermek için parantez arasına virgül eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

<span data-ttu-id="8ff20-212">Dizinin boyutlarından birini-1 olarak bildirerek *sıfır uzunluklu bir dizi* bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="8ff20-213">Sıfır uzunluklu bir diziyi tutan bir değişken `Nothing`değerine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="8ff20-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="8ff20-214">Belirli ortak dil çalışma zamanı işlevleri için sıfır uzunluklu diziler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="8ff20-215">Böyle bir diziye erişmeyi denerseniz, bir çalışma zamanı özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="8ff20-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="8ff20-216">Daha fazla bilgi için bkz. [diziler](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-216">For more information, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="8ff20-217">Bir dizinin değerlerini bir dizi değişmez değeri kullanarak başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="8ff20-218">Bunu yapmak için, başlatma değerlerini küme ayraçları (`{}`) ile çevreleyin.</span><span class="sxs-lookup"><span data-stu-id="8ff20-218">To do this, surround the initialization values with braces (`{}`).</span></span>

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

<span data-ttu-id="8ff20-219">Çok boyutlu diziler için, her ayrı boyut için başlatma, dış boyuttaki küme ayraçları içine alınır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="8ff20-220">Öğeler satır birincil sırada belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-220">The elements are specified in row-major order.</span></span>

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

<span data-ttu-id="8ff20-221">Dizi değişmez değerleri hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-221">For more information about array literals, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

## <a name="default"></a><span data-ttu-id="8ff20-222">Varsayılan veri türleri ve değerleri</span><span class="sxs-lookup"><span data-stu-id="8ff20-222">Default data types and values</span></span>

<span data-ttu-id="8ff20-223">Aşağıdaki tabloda, bir `Dim` bildiriminde veri türünü ve başlatıcıyı belirtmenin çeşitli birleşimlerinin sonuçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="8ff20-224">Veri türü belirtildi mi?</span><span class="sxs-lookup"><span data-stu-id="8ff20-224">Data type specified?</span></span>|<span data-ttu-id="8ff20-225">Başlatıcı belirtildi mi?</span><span class="sxs-lookup"><span data-stu-id="8ff20-225">Initializer specified?</span></span>|<span data-ttu-id="8ff20-226">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ff20-226">Example</span></span>|<span data-ttu-id="8ff20-227">Sonuç</span><span class="sxs-lookup"><span data-stu-id="8ff20-227">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="8ff20-228">Hayır</span><span class="sxs-lookup"><span data-stu-id="8ff20-228">No</span></span>|<span data-ttu-id="8ff20-229">Hayır</span><span class="sxs-lookup"><span data-stu-id="8ff20-229">No</span></span>|`Dim qty`|<span data-ttu-id="8ff20-230">[Option Strict](option-strict-statement.md) kapalıysa (varsayılan), değişken `Nothing`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-230">If [Option Strict](option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="8ff20-231">`Option Strict` açık ise, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="8ff20-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="8ff20-232">Hayır</span><span class="sxs-lookup"><span data-stu-id="8ff20-232">No</span></span>|<span data-ttu-id="8ff20-233">Evet</span><span class="sxs-lookup"><span data-stu-id="8ff20-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="8ff20-234">[Seçenek çıkarımı](option-infer-statement.md) açık ise (varsayılan), değişkeni başlatıcının veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-234">If [Option Infer](option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="8ff20-235">Bkz. [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-235">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="8ff20-236">`Option Infer` kapalıysa ve `Option Strict` kapalıysa, değişken `Object`veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="8ff20-237">`Option Infer` kapalıysa ve `Option Strict` açık ise, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="8ff20-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="8ff20-238">Evet</span><span class="sxs-lookup"><span data-stu-id="8ff20-238">Yes</span></span>|<span data-ttu-id="8ff20-239">Hayır</span><span class="sxs-lookup"><span data-stu-id="8ff20-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="8ff20-240">Değişken, veri türü için varsayılan değer olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="8ff20-241">Bu bölümün ilerleyen kısımlarında tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="8ff20-241">See the table later in this section.</span></span>|
|<span data-ttu-id="8ff20-242">Evet</span><span class="sxs-lookup"><span data-stu-id="8ff20-242">Yes</span></span>|<span data-ttu-id="8ff20-243">Evet</span><span class="sxs-lookup"><span data-stu-id="8ff20-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="8ff20-244">Başlatıcının veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="8ff20-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

<span data-ttu-id="8ff20-245">Bir veri türü belirtirseniz ancak Başlatıcı belirtmezseniz, Visual Basic değişkeni, veri türü için varsayılan değer olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="8ff20-246">Aşağıdaki tabloda varsayılan başlatma değerleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-246">The following table shows the default initialization values.</span></span>

|<span data-ttu-id="8ff20-247">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8ff20-247">Data type</span></span>|<span data-ttu-id="8ff20-248">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="8ff20-248">Default value</span></span>|
|---|---|
|<span data-ttu-id="8ff20-249">Tüm sayısal türler (`Byte` ve `SByte`dahil)</span><span class="sxs-lookup"><span data-stu-id="8ff20-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="8ff20-250">0</span><span class="sxs-lookup"><span data-stu-id="8ff20-250">0</span></span>|
|`Char`|<span data-ttu-id="8ff20-251">İkili 0</span><span class="sxs-lookup"><span data-stu-id="8ff20-251">Binary 0</span></span>|
|<span data-ttu-id="8ff20-252">Tüm başvuru türleri (`Object`, `String`ve tüm diziler dahil)</span><span class="sxs-lookup"><span data-stu-id="8ff20-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|
|`Boolean`|`False`|
|`Date`|<span data-ttu-id="8ff20-253">1 yılın 1 Ocak 12:00 (01/01/0001 12:00:00)</span><span class="sxs-lookup"><span data-stu-id="8ff20-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|

<span data-ttu-id="8ff20-254">Bir yapının her öğesi ayrı bir değişken gibi başlatılır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="8ff20-255">Bir dizinin uzunluğunu bildirir ancak öğelerini başlatmayın, her öğe ayrı bir değişken gibi başlatılır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>

## <a name="static-local-variable-lifetime"></a><span data-ttu-id="8ff20-256">Statik yerel değişken ömrü</span><span class="sxs-lookup"><span data-stu-id="8ff20-256">Static local variable lifetime</span></span>

<span data-ttu-id="8ff20-257">`Static` yerel bir değişken, bildirildiği yordamın süresinden daha uzun bir süre içinde.</span><span class="sxs-lookup"><span data-stu-id="8ff20-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="8ff20-258">Değişkenin yaşam süresinin sınırları yordamın bildirildiği yere ve `Shared`olup olmadığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>

|<span data-ttu-id="8ff20-259">Yordam bildirimi</span><span class="sxs-lookup"><span data-stu-id="8ff20-259">Procedure declaration</span></span>|<span data-ttu-id="8ff20-260">Değişken başlatıldı</span><span class="sxs-lookup"><span data-stu-id="8ff20-260">Variable initialized</span></span>|<span data-ttu-id="8ff20-261">Değişken var olanı durduruyor</span><span class="sxs-lookup"><span data-stu-id="8ff20-261">Variable stops existing</span></span>|
|---|---|---|
|<span data-ttu-id="8ff20-262">Bir modülde</span><span class="sxs-lookup"><span data-stu-id="8ff20-262">In a module</span></span>|<span data-ttu-id="8ff20-263">Yordamın ilk çağrılışında</span><span class="sxs-lookup"><span data-stu-id="8ff20-263">The first time the procedure is called</span></span>|<span data-ttu-id="8ff20-264">Programınız yürütmeyi durduruyor</span><span class="sxs-lookup"><span data-stu-id="8ff20-264">When your program stops execution</span></span>|
|<span data-ttu-id="8ff20-265">Bir sınıf veya yapıda, yordam `Shared`</span><span class="sxs-lookup"><span data-stu-id="8ff20-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="8ff20-266">Yordamın, belirli bir örnek veya sınıf ya da yapının kendisindeki ilk kez çağrılması</span><span class="sxs-lookup"><span data-stu-id="8ff20-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="8ff20-267">Programınız yürütmeyi durduruyor</span><span class="sxs-lookup"><span data-stu-id="8ff20-267">When your program stops execution</span></span>|
|<span data-ttu-id="8ff20-268">Bir sınıf veya yapıda, yordam `Shared` değildir</span><span class="sxs-lookup"><span data-stu-id="8ff20-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="8ff20-269">Yordamın belirli bir örnek üzerinde ilk çağrılışında</span><span class="sxs-lookup"><span data-stu-id="8ff20-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="8ff20-270">Örnek, atık toplama (GC) için bırakıldığında</span><span class="sxs-lookup"><span data-stu-id="8ff20-270">When the instance is released for garbage collection (GC)</span></span>|

## <a name="attributes-and-modifiers"></a><span data-ttu-id="8ff20-271">Öznitelikler ve değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="8ff20-271">Attributes and modifiers</span></span>

<span data-ttu-id="8ff20-272">Öznitelikleri, yerel değişkenlere değil yalnızca üye değişkenlerine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="8ff20-273">Bir öznitelik, bilgileri derlemenin meta verilerine katkıda bulunur ve bu, yerel değişkenler gibi geçici depolama için anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>

<span data-ttu-id="8ff20-274">Modül düzeyinde, üye değişkenlerini bildirmek için `Static` değiştiricisini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8ff20-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="8ff20-275">Yordam düzeyinde, yerel değişkenleri bildirmek için `Shared`, `Shadows`, `ReadOnly`, `WithEvents`veya herhangi bir erişim değiştiricilerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8ff20-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>

<span data-ttu-id="8ff20-276">Bir `accessmodifier`sağlayarak hangi kodun bir değişkene erişebileceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="8ff20-277">Sınıf ve modül üye değişkenleri (herhangi bir yordam dışında), varsayılan olarak özel erişim ve yapı üye değişkenlerini genel erişime varsayılan olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ff20-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="8ff20-278">Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="8ff20-279">Yerel değişkenlerde erişim değiştiricilerini kullanamazsınız (bir yordam içinde).</span><span class="sxs-lookup"><span data-stu-id="8ff20-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>

<span data-ttu-id="8ff20-280">Yalnızca üye değişkenlerinde `WithEvents`, bir yordamın içindeki yerel değişkenlerde değil, ' ı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="8ff20-281">`WithEvents`belirtirseniz, değişkenin veri türü, `Object`değil, belirli bir sınıf türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="8ff20-282">`WithEvents`bir dizi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="8ff20-283">Olaylar hakkında daha fazla bilgi için bkz. [Olaylar](../../programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-283">For more information about events, see [Events](../../programming-guide/language-features/events/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8ff20-284">Bir sınıf, yapı veya modülün dışındaki kodun, bir üye değişkeninin adını bu sınıf, yapı veya modülün adı ile nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="8ff20-285">Bir yordamın veya bloğun dışındaki kod, bu yordam veya blok içindeki herhangi bir yerel değişkene başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>

## <a name="releasing-managed-resources"></a><span data-ttu-id="8ff20-286">Yönetilen kaynakları serbest bırakma</span><span class="sxs-lookup"><span data-stu-id="8ff20-286">Releasing managed resources</span></span>

<span data-ttu-id="8ff20-287">.NET Framework atık toplayıcı, sizin bölüminizdeki ek kodlama yapmadan yönetilen kaynakları ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="8ff20-288">Ancak, atık toplayıcıyı beklemek yerine, yönetilen bir kaynağın elden çıkarılmasını zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

<span data-ttu-id="8ff20-289">Bir sınıf özellikle değerli ve nadir kaynağına (veritabanı bağlantısı veya dosya tanıtıcısı gibi) sahip olursa, artık kullanımda olmayan bir sınıf örneğini temizleyebilmek için sonraki atık toplamaya kadar beklemek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="8ff20-290">Bir sınıf, bir atık toplama işleminden önce kaynakları serbest bırakmak için <xref:System.IDisposable> arabirimini uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="8ff20-291">Bu arabirimi uygulayan bir sınıf, değerli kaynakların hemen yayınlanmasını zorlamak için çağrılabilecek bir `Dispose` yöntemi sunar.</span><span class="sxs-lookup"><span data-stu-id="8ff20-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>

<span data-ttu-id="8ff20-292">`Using` deyimi, kaynak alma, bir deyim kümesi yürütme ve sonra kaynağı atma sürecini otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="8ff20-293">Ancak, kaynağın <xref:System.IDisposable> arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="8ff20-294">Daha fazla bilgi için bkz. [using deyimleri](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8ff20-294">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="8ff20-295">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ff20-295">Example</span></span>

<span data-ttu-id="8ff20-296">Aşağıdaki örnek, çeşitli seçeneklerle `Dim` ifadesini kullanarak değişkenleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-296">The following example declares variables by using the `Dim` statement with various options.</span></span>

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a><span data-ttu-id="8ff20-297">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ff20-297">Example</span></span>

<span data-ttu-id="8ff20-298">Aşağıdaki örnekte 1 ile 30 arasında asal sayılar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="8ff20-299">Yerel değişkenlerin kapsamı kod açıklamalarında açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-299">The scope of local variables is described in code comments.</span></span>

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a><span data-ttu-id="8ff20-300">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ff20-300">Example</span></span>

<span data-ttu-id="8ff20-301">Aşağıdaki örnekte `speedValue` değişkeni sınıf düzeyinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="8ff20-302">`Private` anahtar sözcüğü değişkeni bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ff20-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="8ff20-303">Değişkenine `Car` sınıfındaki herhangi bir yordam tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ff20-303">The variable can be accessed by any procedure in the `Car` class.</span></span>

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a><span data-ttu-id="8ff20-304">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ff20-304">See also</span></span>

- [<span data-ttu-id="8ff20-305">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ff20-305">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="8ff20-306">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ff20-306">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="8ff20-307">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ff20-307">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="8ff20-308">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ff20-308">Option Infer Statement</span></span>](option-infer-statement.md)
- [<span data-ttu-id="8ff20-309">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ff20-309">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="8ff20-310">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ff20-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="8ff20-311">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="8ff20-311">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="8ff20-312">Diziler</span><span class="sxs-lookup"><span data-stu-id="8ff20-312">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="8ff20-313">Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="8ff20-313">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="8ff20-314">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="8ff20-314">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="8ff20-315">Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="8ff20-315">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="8ff20-316">Nasıl yapılır: Nesne Başlatıcısı Kullanarak Nesne Bildirme</span><span class="sxs-lookup"><span data-stu-id="8ff20-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="8ff20-317">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="8ff20-317">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
