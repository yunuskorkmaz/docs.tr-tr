---
description: 'Daha fazla bilgi edinin: Dim deyimleri (Visual Basic)'
title: Dim ekstresi
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
ms.openlocfilehash: b950ae95af01be4e064ac9177300f144e0cc08b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795202"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="70103-103">Dim ekstresi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70103-103">Dim statement (Visual Basic)</span></span>

<span data-ttu-id="70103-104">Bir veya daha fazla değişken için depolama alanı bildirir ve ayırır.</span><span class="sxs-lookup"><span data-stu-id="70103-104">Declares and allocates storage space for one or more variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="70103-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="70103-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a><span data-ttu-id="70103-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="70103-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="70103-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-107">Optional.</span></span> <span data-ttu-id="70103-108">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="70103-108">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="70103-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-109">Optional.</span></span> <span data-ttu-id="70103-110">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="70103-110">Can be one of the following:</span></span>

  - [<span data-ttu-id="70103-111">Genel</span><span class="sxs-lookup"><span data-stu-id="70103-111">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="70103-112">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="70103-112">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="70103-113">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="70103-113">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="70103-114">Özel</span><span class="sxs-lookup"><span data-stu-id="70103-114">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="70103-115">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="70103-115">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="70103-116">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="70103-116">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="70103-117">[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="70103-117">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `Shared`

  <span data-ttu-id="70103-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-118">Optional.</span></span> <span data-ttu-id="70103-119">Bkz. [paylaşılan](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="70103-119">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="70103-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-120">Optional.</span></span> <span data-ttu-id="70103-121">Bkz. [gölgeler](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="70103-121">See [Shadows](../modifiers/shadows.md).</span></span>

- `Static`

  <span data-ttu-id="70103-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-122">Optional.</span></span> <span data-ttu-id="70103-123">Bkz. [statik](../modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="70103-123">See [Static](../modifiers/static.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="70103-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-124">Optional.</span></span> <span data-ttu-id="70103-125">Bkz. [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="70103-125">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WithEvents`

  <span data-ttu-id="70103-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-126">Optional.</span></span> <span data-ttu-id="70103-127">Bunların, olayları yükseltebileceği bir sınıfın örneklerine başvuran nesne değişkenleri olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="70103-127">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="70103-128">Bkz. [WithEvents](../modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="70103-128">See [WithEvents](../modifiers/withevents.md).</span></span>

- `variablelist`

  <span data-ttu-id="70103-129">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="70103-129">Required.</span></span> <span data-ttu-id="70103-130">Bu bildirimde bildirildiği değişkenlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="70103-130">List of variables being declared in this statement.</span></span>

  `variable [ , variable ... ]`

  <span data-ttu-id="70103-131">Her birinin `variable` aşağıdaki söz dizimi ve parçaları vardır:</span><span class="sxs-lookup"><span data-stu-id="70103-131">Each `variable` has the following syntax and parts:</span></span>

  <span data-ttu-id="70103-132">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="70103-132">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>

  |<span data-ttu-id="70103-133">Bölüm</span><span class="sxs-lookup"><span data-stu-id="70103-133">Part</span></span>|<span data-ttu-id="70103-134">Description</span><span class="sxs-lookup"><span data-stu-id="70103-134">Description</span></span>|
  |---|---|
  |`variablename`|<span data-ttu-id="70103-135">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="70103-135">Required.</span></span> <span data-ttu-id="70103-136">Değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="70103-136">Name of the variable.</span></span> <span data-ttu-id="70103-137">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="70103-137">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
  |`boundslist`|<span data-ttu-id="70103-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-138">Optional.</span></span> <span data-ttu-id="70103-139">Bir dizi değişkeninin her boyutunun sınırları listesi.</span><span class="sxs-lookup"><span data-stu-id="70103-139">List of bounds of each dimension of an array variable.</span></span>|
  |`New`|<span data-ttu-id="70103-140">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-140">Optional.</span></span> <span data-ttu-id="70103-141">Deyimin çalıştırıldığı zaman sınıfının yeni bir örneğini oluşturur `Dim` .</span><span class="sxs-lookup"><span data-stu-id="70103-141">Creates a new instance of the class when the `Dim` statement runs.</span></span>|
  |`datatype`|<span data-ttu-id="70103-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-142">Optional.</span></span> <span data-ttu-id="70103-143">Değişkenin veri türü.</span><span class="sxs-lookup"><span data-stu-id="70103-143">Data type of the variable.</span></span>|
  |`With`|<span data-ttu-id="70103-144">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-144">Optional.</span></span> <span data-ttu-id="70103-145">Nesne Başlatıcısı listesini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="70103-145">Introduces the object initializer list.</span></span>|
  |`propertyname`|<span data-ttu-id="70103-146">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="70103-146">Optional.</span></span> <span data-ttu-id="70103-147">Örneği yaptığınız sınıftaki bir özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="70103-147">The name of a property in the class you are making an instance of.</span></span>|
  |`propinitializer`|<span data-ttu-id="70103-148">Şu tarihten sonra gereklidir `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="70103-148">Required after `propertyname` =.</span></span> <span data-ttu-id="70103-149">Değerlendirilen ve özellik adına atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="70103-149">The expression that is evaluated and assigned to the property name.</span></span>|
  |`initializer`|<span data-ttu-id="70103-150">`New`Belirtilmemişse, isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="70103-150">Optional if `New` is not specified.</span></span> <span data-ttu-id="70103-151">Değerlendirilen ve değişken oluşturulduğunda değişkene atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="70103-151">Expression that is evaluated and assigned to the variable when it is created.</span></span>|

## <a name="remarks"></a><span data-ttu-id="70103-152">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70103-152">Remarks</span></span>

<span data-ttu-id="70103-153">Visual Basic derleyici, değişkenin `Dim` veri türünü ve değişkene hangi kodun erişebileceği gibi diğer bilgileri belirlemek için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="70103-153">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="70103-154">Aşağıdaki örnek, bir değeri tutacak bir değişken bildirir `Integer` .</span><span class="sxs-lookup"><span data-stu-id="70103-154">The following example declares a variable to hold an `Integer` value.</span></span>

```vb
Dim numberOfStudents As Integer
```

<span data-ttu-id="70103-155">Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-155">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

<span data-ttu-id="70103-156">Bir başvuru türü için, `New` veri türü tarafından belirtilen sınıf veya yapının yeni bir örneğini oluşturmak için anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="70103-156">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="70103-157">Kullanırsanız `New` , bir başlatıcı ifadesi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="70103-157">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="70103-158">Bunun yerine, varsa bağımsız değişkenleri değişkeni oluşturduğunuz sınıfın oluşturucusuna sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="70103-158">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

<span data-ttu-id="70103-159">Bir yordam, blok, sınıf, yapı veya modülde bir değişken bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-159">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="70103-160">Bir kaynak dosyasında, ad alanında veya arabirimde bir değişken bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-160">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="70103-161">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="70103-161">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="70103-162">Modül düzeyinde belirtilen bir değişken, herhangi bir yordam dışında, bir *üye değişkeni* veya *alanıdır*.</span><span class="sxs-lookup"><span data-stu-id="70103-162">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="70103-163">Üye değişkenleri, sınıfları, yapısı veya modülleri genelinde kapsamdadır.</span><span class="sxs-lookup"><span data-stu-id="70103-163">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="70103-164">Yordam düzeyinde belirtilen bir değişken *yerel bir değişkendir*.</span><span class="sxs-lookup"><span data-stu-id="70103-164">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="70103-165">Yerel değişkenler yalnızca kendi yordamı veya blokları içinde kapsamdadır.</span><span class="sxs-lookup"><span data-stu-id="70103-165">Local variables are in scope only within their procedure or block.</span></span>

<span data-ttu-id="70103-166">Aşağıdaki erişim değiştiricileri, değişkenleri bir yordam dışında bildirmek için kullanılır: `Public` , `Protected` ,, `Friend` `Protected Friend` ve `Private` .</span><span class="sxs-lookup"><span data-stu-id="70103-166">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="70103-167">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="70103-167">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="70103-168">`Dim`Anahtar sözcüğü isteğe bağlıdır ve aşağıdaki değiştiricilerin herhangi birini belirtirseniz genellikle atlanır: `Public` ,,, `Protected` `Friend` `Protected Friend` , `Private` , `Shared` , `Shadows` , `Static` , `ReadOnly` veya `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="70103-168">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

<span data-ttu-id="70103-169">`Option Explicit`Açık ise (varsayılan), derleyici kullandığınız her değişken için bir bildirim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="70103-169">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="70103-170">Daha fazla bilgi için bkz. [Option Explicit deyimdir](option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="70103-170">For more information, see [Option Explicit Statement](option-explicit-statement.md).</span></span>

## <a name="specifying-an-initial-value"></a><span data-ttu-id="70103-171">Bir başlangıç değeri belirtme</span><span class="sxs-lookup"><span data-stu-id="70103-171">Specifying an initial value</span></span>

<span data-ttu-id="70103-172">Bir değişkene, oluşturulduğunda bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-172">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="70103-173">Değer türü için, değişkene atanacak bir ifade sağlamak üzere bir *Başlatıcı* kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="70103-173">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="70103-174">İfade, derleme zamanında hesaplanabilecek bir sabit olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="70103-174">The expression must evaluate to a constant that can be calculated at compile time.</span></span>

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

<span data-ttu-id="70103-175">Bir başlatıcı belirtilmişse ve bir yan tümcesinde veri türü belirtilmemişse `As` , veri türünü başlatıcıdan çıkarsmak için *tür çıkarımı* kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70103-175">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="70103-176">Aşağıdaki örnekte, her ikisi de `num1` `num2` kesin olarak tam sayı olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="70103-176">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="70103-177">İkinci bildirimde, tür çıkarımı tür 3 ' ten yazın.</span><span class="sxs-lookup"><span data-stu-id="70103-177">In the second declaration, type inference infers the type from the value 3.</span></span>

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

<span data-ttu-id="70103-178">Tür çıkarımı yordam düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="70103-178">Type inference applies at the procedure level.</span></span> <span data-ttu-id="70103-179">Bir sınıf, yapı, modül veya arabirimdeki bir yordamın dışında uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="70103-179">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="70103-180">Tür çıkarımı hakkında daha fazla bilgi için bkz. [Option Infer deyimleri](option-infer-statement.md) ve [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="70103-180">For more information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="70103-181">Veri türü veya Başlatıcı belirtilmediğinde ne olacağı hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alarak [varsayılan veri türleri ve değerleri](dim-statement.md#default) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="70103-181">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](dim-statement.md#default) later in this topic.</span></span>

<span data-ttu-id="70103-182">Adlandırılmış ve anonim türlerin örneklerini bildirmek için bir *nesne Başlatıcısı* kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-182">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="70103-183">Aşağıdaki kod, sınıfının bir örneğini oluşturur `Student` ve özellikleri başlatmak için bir nesne Başlatıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="70103-183">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

<span data-ttu-id="70103-184">Nesne başlatıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: nesne Başlatıcısı](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [nesne başlatıcıları: adlandırılmış ve anonim türler](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)ve [anonim türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)kullanarak nesne bildirme.</span><span class="sxs-lookup"><span data-stu-id="70103-184">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="declaring-multiple-variables"></a><span data-ttu-id="70103-185">Birden çok değişken bildirme</span><span class="sxs-lookup"><span data-stu-id="70103-185">Declaring multiple variables</span></span>

<span data-ttu-id="70103-186">Tek bir bildirim ifadesinde, her biri için değişken adını belirterek ve her dizi adını parantez ile izleyerek birkaç değişken bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-186">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="70103-187">Birden çok değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="70103-187">Multiple variables are separated by commas.</span></span>

```vb
Dim lastTime, nextTime, allTimes() As Date
```

<span data-ttu-id="70103-188">Tek bir yan tümcesiyle birden fazla değişken bildirirseniz `As` , bu değişken grubu için bir başlatıcı sağlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="70103-188">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>

<span data-ttu-id="70103-189">Farklı değişkenler için, `As` bildirdiğiniz her değişken için ayrı bir yan tümce kullanarak farklı veri türleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-189">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="70103-190">Her değişken, `As` bölümünün sonunda karşılaşılan ilk yan tümcesinde belirtilen veri türünü alır `variablename` .</span><span class="sxs-lookup"><span data-stu-id="70103-190">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a><span data-ttu-id="70103-191">Diziler</span><span class="sxs-lookup"><span data-stu-id="70103-191">Arrays</span></span>

<span data-ttu-id="70103-192">Birden çok değer içerebilen bir *diziyi* tutacak bir değişken bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-192">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="70103-193">Bir değişkenin bir diziyi bulundurduğunu belirtmek için, `variablename` parantez ile hemen izleyin.</span><span class="sxs-lookup"><span data-stu-id="70103-193">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="70103-194">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="70103-194">For more information about arrays, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="70103-195">Bir dizinin her boyutunun alt ve üst sınırını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-195">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="70103-196">Bunu yapmak için `boundslist` ayraçları içine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="70103-196">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="70103-197">Her boyut için, `boundslist` üst sınırı ve isteğe bağlı olarak alt sınırı belirtir.</span><span class="sxs-lookup"><span data-stu-id="70103-197">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="70103-198">Alt sınır, sizin belirtmeksizin her zaman sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="70103-198">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="70103-199">Her dizin, üst sınır değeri ile sıfırdan farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="70103-199">Each index can vary from zero through its upper bound value.</span></span>

<span data-ttu-id="70103-200">Aşağıdaki iki deyim eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="70103-200">The following two statements are equivalent.</span></span> <span data-ttu-id="70103-201">Her ifade bir 21 öğe dizisi bildirir `Integer` .</span><span class="sxs-lookup"><span data-stu-id="70103-201">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="70103-202">Diziye eriştiğinizde, dizin 0 ile 20 arasında farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="70103-202">When you access the array, the index can vary from 0 through 20.</span></span>

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

<span data-ttu-id="70103-203">Aşağıdaki ifade, türünde iki boyutlu bir dizi bildirir `Double` .</span><span class="sxs-lookup"><span data-stu-id="70103-203">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="70103-204">Dizide 4 satır (3 + 1) 6 sütun (5 + 1) bulunur.</span><span class="sxs-lookup"><span data-stu-id="70103-204">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="70103-205">Üst sınır, boyutun uzunluğunu değil, dizin için mümkün olan en yüksek değeri temsil ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="70103-205">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="70103-206">Boyutun uzunluğu üst sınır artı bir değer.</span><span class="sxs-lookup"><span data-stu-id="70103-206">The length of the dimension is the upper bound plus one.</span></span>

```vb
Dim matrix2(3, 5) As Double
```

<span data-ttu-id="70103-207">Bir dizi 1 ile 32 arasında boyutlara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="70103-207">An array can have from 1 to 32 dimensions.</span></span>

<span data-ttu-id="70103-208">Bir dizi bildiriminde tüm sınırların boş kalmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-208">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="70103-209">Bunu yaparsanız dizi, belirttiğiniz boyut sayısına sahiptir ancak başlatılmamış olur.</span><span class="sxs-lookup"><span data-stu-id="70103-209">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="70103-210">`Nothing`Öğelerinin en az bir kısmını başlatana kadar bir değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="70103-210">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="70103-211">`Dim`Deyimin tüm boyutlar veya boyut yok için sınır belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="70103-211">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

<span data-ttu-id="70103-212">Dizide birden fazla boyut varsa, boyut sayısını göstermek için parantez arasına virgül eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="70103-212">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

<span data-ttu-id="70103-213">Dizinin boyutlarından birini-1 olarak bildirerek *sıfır uzunluklu bir dizi* bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-213">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="70103-214">Sıfır uzunluklu bir diziyi tutan bir değişken değeri yok `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="70103-214">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="70103-215">Belirli ortak dil çalışma zamanı işlevleri için sıfır uzunluklu diziler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="70103-215">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="70103-216">Böyle bir diziye erişmeyi denerseniz, bir çalışma zamanı özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="70103-216">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="70103-217">Daha fazla bilgi için bkz. [diziler](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="70103-217">For more information, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="70103-218">Bir dizinin değerlerini bir dizi değişmez değeri kullanarak başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-218">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="70103-219">Bunu yapmak için başlatma değerlerini küme ayraçları () ile çevreleyin `{}` .</span><span class="sxs-lookup"><span data-stu-id="70103-219">To do this, surround the initialization values with braces (`{}`).</span></span>

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

<span data-ttu-id="70103-220">Çok boyutlu diziler için, her ayrı boyut için başlatma, dış boyuttaki küme ayraçları içine alınır.</span><span class="sxs-lookup"><span data-stu-id="70103-220">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="70103-221">Öğeler satır birincil sırada belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="70103-221">The elements are specified in row-major order.</span></span>

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

<span data-ttu-id="70103-222">Dizi değişmez değerleri hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="70103-222">For more information about array literals, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

## <a name="default-data-types-and-values"></a><a name="default"></a> <span data-ttu-id="70103-223">Varsayılan veri türleri ve değerleri</span><span class="sxs-lookup"><span data-stu-id="70103-223">Default data types and values</span></span>

<span data-ttu-id="70103-224">Aşağıdaki tabloda, bir deyimindeki veri türünü ve başlatıcıyı belirtmenin çeşitli birleşimlerinin sonuçları açıklanmaktadır `Dim` .</span><span class="sxs-lookup"><span data-stu-id="70103-224">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="70103-225">Veri türü belirtildi mi?</span><span class="sxs-lookup"><span data-stu-id="70103-225">Data type specified?</span></span>|<span data-ttu-id="70103-226">Başlatıcı belirtildi mi?</span><span class="sxs-lookup"><span data-stu-id="70103-226">Initializer specified?</span></span>|<span data-ttu-id="70103-227">Örnek</span><span class="sxs-lookup"><span data-stu-id="70103-227">Example</span></span>|<span data-ttu-id="70103-228">Sonuç</span><span class="sxs-lookup"><span data-stu-id="70103-228">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="70103-229">Hayır</span><span class="sxs-lookup"><span data-stu-id="70103-229">No</span></span>|<span data-ttu-id="70103-230">Hayır</span><span class="sxs-lookup"><span data-stu-id="70103-230">No</span></span>|`Dim qty`|<span data-ttu-id="70103-231">[Option Strict](option-strict-statement.md) kapalıysa (varsayılan), değişkeni olarak ayarlanır `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="70103-231">If [Option Strict](option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="70103-232">`Option Strict`Açık ise, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="70103-232">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="70103-233">Hayır</span><span class="sxs-lookup"><span data-stu-id="70103-233">No</span></span>|<span data-ttu-id="70103-234">Yes</span><span class="sxs-lookup"><span data-stu-id="70103-234">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="70103-235">[Seçenek çıkarımı](option-infer-statement.md) açık ise (varsayılan), değişkeni başlatıcının veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="70103-235">If [Option Infer](option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="70103-236">Bkz. [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="70103-236">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="70103-237">`Option Infer`Kapalıysa ve `Option Strict` kapalıysa, değişken veri türünü alır `Object` .</span><span class="sxs-lookup"><span data-stu-id="70103-237">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="70103-238">`Option Infer`Kapalıysa ve açık ise `Option Strict` , bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="70103-238">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="70103-239">Yes</span><span class="sxs-lookup"><span data-stu-id="70103-239">Yes</span></span>|<span data-ttu-id="70103-240">Hayır</span><span class="sxs-lookup"><span data-stu-id="70103-240">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="70103-241">Değişken, veri türü için varsayılan değer olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="70103-241">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="70103-242">Bu bölümün ilerleyen kısımlarında tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="70103-242">See the table later in this section.</span></span>|
|<span data-ttu-id="70103-243">Yes</span><span class="sxs-lookup"><span data-stu-id="70103-243">Yes</span></span>|<span data-ttu-id="70103-244">Yes</span><span class="sxs-lookup"><span data-stu-id="70103-244">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="70103-245">Başlatıcının veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="70103-245">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

<span data-ttu-id="70103-246">Bir veri türü belirtirseniz ancak Başlatıcı belirtmezseniz, Visual Basic değişkeni, veri türü için varsayılan değer olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="70103-246">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="70103-247">Aşağıdaki tabloda varsayılan başlatma değerleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="70103-247">The following table shows the default initialization values.</span></span>

|<span data-ttu-id="70103-248">Veri türü</span><span class="sxs-lookup"><span data-stu-id="70103-248">Data type</span></span>|<span data-ttu-id="70103-249">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="70103-249">Default value</span></span>|
|---|---|
|<span data-ttu-id="70103-250">Tüm sayısal türler ( `Byte` ve dahil `SByte` )</span><span class="sxs-lookup"><span data-stu-id="70103-250">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="70103-251">0</span><span class="sxs-lookup"><span data-stu-id="70103-251">0</span></span>|
|`Char`|<span data-ttu-id="70103-252">İkili 0</span><span class="sxs-lookup"><span data-stu-id="70103-252">Binary 0</span></span>|
|<span data-ttu-id="70103-253">Tüm başvuru türleri ( `Object` , `String` ve tüm diziler dahil)</span><span class="sxs-lookup"><span data-stu-id="70103-253">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|
|`Boolean`|`False`|
|`Date`|<span data-ttu-id="70103-254">1 yılın 1 Ocak 12:00 (01/01/0001 12:00:00)</span><span class="sxs-lookup"><span data-stu-id="70103-254">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|

<span data-ttu-id="70103-255">Bir yapının her öğesi ayrı bir değişken gibi başlatılır.</span><span class="sxs-lookup"><span data-stu-id="70103-255">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="70103-256">Bir dizinin uzunluğunu bildirir ancak öğelerini başlatmayın, her öğe ayrı bir değişken gibi başlatılır.</span><span class="sxs-lookup"><span data-stu-id="70103-256">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>

## <a name="static-local-variable-lifetime"></a><span data-ttu-id="70103-257">Statik yerel değişken ömrü</span><span class="sxs-lookup"><span data-stu-id="70103-257">Static local variable lifetime</span></span>

<span data-ttu-id="70103-258">`Static`Yerel bir değişken, bildirildiği yordamın süresinden daha uzun bir yaşam süresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="70103-258">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="70103-259">Değişkenin yaşam süresinin sınırları yordamın bildirildiği yere ve olup olmadığına bağlıdır `Shared` .</span><span class="sxs-lookup"><span data-stu-id="70103-259">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>

|<span data-ttu-id="70103-260">Yordam bildirimi</span><span class="sxs-lookup"><span data-stu-id="70103-260">Procedure declaration</span></span>|<span data-ttu-id="70103-261">Değişken başlatıldı</span><span class="sxs-lookup"><span data-stu-id="70103-261">Variable initialized</span></span>|<span data-ttu-id="70103-262">Değişken var olanı durduruyor</span><span class="sxs-lookup"><span data-stu-id="70103-262">Variable stops existing</span></span>|
|---|---|---|
|<span data-ttu-id="70103-263">Bir modülde</span><span class="sxs-lookup"><span data-stu-id="70103-263">In a module</span></span>|<span data-ttu-id="70103-264">Yordamın ilk çağrılışında</span><span class="sxs-lookup"><span data-stu-id="70103-264">The first time the procedure is called</span></span>|<span data-ttu-id="70103-265">Programınız yürütmeyi durduruyor</span><span class="sxs-lookup"><span data-stu-id="70103-265">When your program stops execution</span></span>|
|<span data-ttu-id="70103-266">Bir sınıf veya yapıda, yordam `Shared`</span><span class="sxs-lookup"><span data-stu-id="70103-266">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="70103-267">Yordamın, belirli bir örnek veya sınıf ya da yapının kendisindeki ilk kez çağrılması</span><span class="sxs-lookup"><span data-stu-id="70103-267">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="70103-268">Programınız yürütmeyi durduruyor</span><span class="sxs-lookup"><span data-stu-id="70103-268">When your program stops execution</span></span>|
|<span data-ttu-id="70103-269">Bir sınıf veya yapıda, yordam `Shared`</span><span class="sxs-lookup"><span data-stu-id="70103-269">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="70103-270">Yordamın belirli bir örnek üzerinde ilk çağrılışında</span><span class="sxs-lookup"><span data-stu-id="70103-270">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="70103-271">Örnek, atık toplama (GC) için bırakıldığında</span><span class="sxs-lookup"><span data-stu-id="70103-271">When the instance is released for garbage collection (GC)</span></span>|

## <a name="attributes-and-modifiers"></a><span data-ttu-id="70103-272">Öznitelikler ve değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="70103-272">Attributes and modifiers</span></span>

<span data-ttu-id="70103-273">Öznitelikleri, yerel değişkenlere değil yalnızca üye değişkenlerine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-273">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="70103-274">Bir öznitelik, bilgileri derlemenin meta verilerine katkıda bulunur ve bu, yerel değişkenler gibi geçici depolama için anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="70103-274">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>

<span data-ttu-id="70103-275">Modül düzeyinde, `Static` üye değişkenlerini bildirmek için değiştiricisini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="70103-275">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="70103-276">Yordam düzeyinde,,,, `Shared` `Shadows` `ReadOnly` `WithEvents` veya herhangi bir erişim değiştiricilerini yerel değişkenleri bildirmek için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="70103-276">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>

<span data-ttu-id="70103-277">Bir değişkene hangi kodun erişebileceğini belirtebilirsiniz `accessmodifier` .</span><span class="sxs-lookup"><span data-stu-id="70103-277">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="70103-278">Sınıf ve modül üye değişkenleri (herhangi bir yordam dışında), varsayılan olarak özel erişim ve yapı üye değişkenlerini genel erişime varsayılan olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="70103-278">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="70103-279">Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-279">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="70103-280">Yerel değişkenlerde erişim değiştiricilerini kullanamazsınız (bir yordam içinde).</span><span class="sxs-lookup"><span data-stu-id="70103-280">You cannot use access modifiers on local variables (inside a procedure).</span></span>

<span data-ttu-id="70103-281">`WithEvents`Bir yordamın içindeki yerel değişkenlerde değil, yalnızca üye değişkenlerinde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-281">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="70103-282">Belirtirseniz `WithEvents` , değişkenin veri türü, değil, belirli bir sınıf türü olmalıdır `Object` .</span><span class="sxs-lookup"><span data-stu-id="70103-282">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="70103-283">İle bir dizi bildiremezsiniz `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="70103-283">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="70103-284">Olaylar hakkında daha fazla bilgi için bkz. [Olaylar](../../programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="70103-284">For more information about events, see [Events](../../programming-guide/language-features/events/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="70103-285">Bir sınıf, yapı veya modülün dışındaki kodun, bir üye değişkeninin adını bu sınıf, yapı veya modülün adı ile nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="70103-285">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="70103-286">Bir yordamın veya bloğun dışındaki kod, bu yordam veya blok içindeki herhangi bir yerel değişkene başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="70103-286">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>

## <a name="releasing-managed-resources"></a><span data-ttu-id="70103-287">Yönetilen kaynakları serbest bırakma</span><span class="sxs-lookup"><span data-stu-id="70103-287">Releasing managed resources</span></span>

<span data-ttu-id="70103-288">.NET Framework atık toplayıcı, sizin bölüminizdeki ek kodlama yapmadan yönetilen kaynakları ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="70103-288">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="70103-289">Ancak, atık toplayıcıyı beklemek yerine, yönetilen bir kaynağın elden çıkarılmasını zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-289">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

<span data-ttu-id="70103-290">Bir sınıf özellikle değerli ve nadir kaynağına (veritabanı bağlantısı veya dosya tanıtıcısı gibi) sahip olursa, artık kullanımda olmayan bir sınıf örneğini temizleyebilmek için sonraki atık toplamaya kadar beklemek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70103-290">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="70103-291">Bir sınıf, bir <xref:System.IDisposable> atık toplama işleminden önce kaynakları serbest bırakmak için arabirimi uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="70103-291">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="70103-292">Bu arabirimi uygulayan bir sınıf, `Dispose` değerli kaynakların hemen yayınlanmasını zorlamak için çağrılabilecek bir yöntemi ortaya koyar.</span><span class="sxs-lookup"><span data-stu-id="70103-292">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>

<span data-ttu-id="70103-293">`Using`Deyimi bir kaynağı alma, bir deyim kümesi yürütme ve sonra kaynağı atma sürecini otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="70103-293">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="70103-294">Ancak, kaynağın arabirimini uygulaması gerekir <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="70103-294">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="70103-295">Daha fazla bilgi için bkz. [using deyimleri](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="70103-295">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="70103-296">Örnek</span><span class="sxs-lookup"><span data-stu-id="70103-296">Example</span></span>

<span data-ttu-id="70103-297">Aşağıdaki örnek, `Dim` çeşitli seçeneklerle deyimleri kullanarak değişkenleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="70103-297">The following example declares variables by using the `Dim` statement with various options.</span></span>

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a><span data-ttu-id="70103-298">Örnek</span><span class="sxs-lookup"><span data-stu-id="70103-298">Example</span></span>

<span data-ttu-id="70103-299">Aşağıdaki örnekte 1 ile 30 arasında asal sayılar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="70103-299">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="70103-300">Yerel değişkenlerin kapsamı kod açıklamalarında açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="70103-300">The scope of local variables is described in code comments.</span></span>

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a><span data-ttu-id="70103-301">Örnek</span><span class="sxs-lookup"><span data-stu-id="70103-301">Example</span></span>

<span data-ttu-id="70103-302">Aşağıdaki örnekte, `speedValue` değişkeni sınıf düzeyinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="70103-302">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="70103-303">`Private`Anahtar sözcüğü değişkeni bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70103-303">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="70103-304">Değişkenine, sınıftaki herhangi bir yordam tarafından erişilebilir `Car` .</span><span class="sxs-lookup"><span data-stu-id="70103-304">The variable can be accessed by any procedure in the `Car` class.</span></span>

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a><span data-ttu-id="70103-305">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70103-305">See also</span></span>

- [<span data-ttu-id="70103-306">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="70103-306">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="70103-307">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="70103-307">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="70103-308">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="70103-308">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="70103-309">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="70103-309">Option Infer Statement</span></span>](option-infer-statement.md)
- [<span data-ttu-id="70103-310">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="70103-310">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="70103-311">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70103-311">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="70103-312">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="70103-312">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="70103-313">Diziler</span><span class="sxs-lookup"><span data-stu-id="70103-313">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="70103-314">Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="70103-314">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="70103-315">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="70103-315">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="70103-316">Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="70103-316">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="70103-317">Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesne Bildirme</span><span class="sxs-lookup"><span data-stu-id="70103-317">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="70103-318">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70103-318">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
