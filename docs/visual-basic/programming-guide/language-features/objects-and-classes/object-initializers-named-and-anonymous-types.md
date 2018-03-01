---
title: "Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 349e4f7b4902eb18845fee7cb4d01b217849a4d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="87b16-102">Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87b16-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="87b16-103">Nesne başlatıcılar, tek bir ifade kullanarak karmaşık bir nesne özelliklerini belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="87b16-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="87b16-104">Adlandırılmış türler ve anonim türler örnekleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87b16-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="87b16-105">Bildirimler</span><span class="sxs-lookup"><span data-stu-id="87b16-105">Declarations</span></span>  
 <span data-ttu-id="87b16-106">Adlandırılmış ve anonim türler örneklerinin bildirimleri neredeyse aynı görünebilir, ancak etkilerini aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="87b16-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="87b16-107">Her kategori yeteneklerini ve kendi kısıtlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="87b16-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="87b16-108">Aşağıdaki örnek, bildirme ve bir adlandırılmış sınıfının bir örneği başlatmak için kolay bir yol gösterir `Customer`, bir nesne Başlatıcı listesini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="87b16-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="87b16-109">Sınıfın adını anahtar sözcüğü sonra belirttiğiniz fark `New`.</span><span class="sxs-lookup"><span data-stu-id="87b16-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 <span data-ttu-id="87b16-110">Anonim bir tür kullanılabilir adı yok.</span><span class="sxs-lookup"><span data-stu-id="87b16-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="87b16-111">Bu nedenle bir örnek oluşturma anonim bir türün bir sınıf adı içeremez.</span><span class="sxs-lookup"><span data-stu-id="87b16-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 <span data-ttu-id="87b16-112">Gereksinimler ve iki bildirimleri sonuçlarını aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="87b16-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="87b16-113">İçin `namedCust`, `Customer` olan sınıfı bir `Name` özellik zaten var olmalıdır ve bildirimi o sınıfın bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87b16-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="87b16-114">İçin `anonymousCust`, derleyici bir özelliği, bir dize olarak adlandırılan yeni bir sınıf tanımlar `Name`ve o sınıfın yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87b16-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="87b16-115">Adlandırılmış türler</span><span class="sxs-lookup"><span data-stu-id="87b16-115">Named Types</span></span>  
 <span data-ttu-id="87b16-116">Nesne başlatıcıları türü kurucusunu çağırmak ve ardından tek bir deyimde bazı veya tüm özelliklerinin değerlerini ayarlamak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="87b16-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="87b16-117">Deyim uygun Oluşturucusu derleyici çağırır: bağımsız değişken içermeyen görüntülenirse varsayılan oluşturucu veya bağımsız değişkenlerden biri veya daha fazla gönderilirse parametreli bir oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="87b16-117">The compiler invokes the appropriate constructor for the statement: the default constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="87b16-118">Başlatıcı listesinde verildikleri sırada bundan sonra belirtilen özellikleri başlatılır.</span><span class="sxs-lookup"><span data-stu-id="87b16-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="87b16-119">Sınıf üyesi için bir başlangıç değeri atamasının Başlatıcı listesindeki her başlatma oluşur.</span><span class="sxs-lookup"><span data-stu-id="87b16-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="87b16-120">Sınıf tanımladığınızda adları ve veri türleri üyeleri belirlenir.</span><span class="sxs-lookup"><span data-stu-id="87b16-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="87b16-121">Aşağıdaki örneklerde, `Customer` sınıfı bulunması gerektiğini ve üyeleri adlı sahip `Name` ve `City` dize değerlerini kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="87b16-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 <span data-ttu-id="87b16-122">Alternatif olarak, aşağıdaki kodu kullanarak aynı sonucu elde edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="87b16-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 <span data-ttu-id="87b16-123">Bu bildirimler her oluşturur aşağıdaki örneğe eşdeğerdir bir `Customer` nesnesi varsayılan oluşturucu kullanılarak ve sonra Başlangıç değerlerini belirtir `Name` ve `City` özelliklerini kullanarak bir `With` deyimi.</span><span class="sxs-lookup"><span data-stu-id="87b16-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the default constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 <span data-ttu-id="87b16-124">Varsa `Customer` sınıfı için bir değer göndermenize olanak sağlayan bir parametreli oluşturucu içeren `Name`, örneğin, aynı zamanda bildirme başlatmak ve bir `Customer` aşağıdaki yollarla nesnesi:</span><span class="sxs-lookup"><span data-stu-id="87b16-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 <span data-ttu-id="87b16-125">Aşağıdaki kod gösterildiği gibi tüm özellikleri başlatma gerekmez.</span><span class="sxs-lookup"><span data-stu-id="87b16-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 <span data-ttu-id="87b16-126">Ancak, başlatma listesi boş olamaz.</span><span class="sxs-lookup"><span data-stu-id="87b16-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="87b16-127">Başlatılmamış özellikler varsayılan değerleri korur.</span><span class="sxs-lookup"><span data-stu-id="87b16-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="87b16-128">Adlandırılmış türleriyle tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="87b16-128">Type Inference with Named Types</span></span>  
 <span data-ttu-id="87b16-129">Bildirimi için kod kısaltabilir `cust1` nesne başlatıcıları ve yerel türü çıkarımı birleştirerek.</span><span class="sxs-lookup"><span data-stu-id="87b16-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="87b16-130">Bu, atlamanızı sağlar `As` yan tümcesinde değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="87b16-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="87b16-131">Değişken veri türü atama tarafından oluşturulan nesnenin türünden algılanır.</span><span class="sxs-lookup"><span data-stu-id="87b16-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="87b16-132">Aşağıdaki örnekte, türü `cust6` olan `Customer`.</span><span class="sxs-lookup"><span data-stu-id="87b16-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="87b16-133">Adlandırılmış türler hakkında açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87b16-133">Remarks About Named Types</span></span>  
  
-   <span data-ttu-id="87b16-134">Sınıf üyesine nesne Başlatıcı listesinde birden fazla kez başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="87b16-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="87b16-135">Bildirimi `cust7` bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="87b16-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   <span data-ttu-id="87b16-136">Üye kendisiyle veya başka bir alanı başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87b16-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="87b16-137">Bunu, aşağıdaki gibi başlatılmadan önce üyesi erişiliyorsa `cust8`, varsayılan değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87b16-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="87b16-138">Nesne Başlatıcı kullanan bir bildirimi işlendiğinde olur ilk şey uygun Oluşturucusu çağrılır olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="87b16-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="87b16-139">Bundan sonra tek tek alanların Başlatıcı listesinde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="87b16-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="87b16-140">Aşağıdaki örneklerde, varsayılan değer için `Name` için atanan `cust8`, ve başlatılmış bir değeri atandığı `cust9`.</span><span class="sxs-lookup"><span data-stu-id="87b16-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     <span data-ttu-id="87b16-141">Aşağıdaki örnek, parametreli oluşturucudan kullanır `cust3` ve `cust4` bildirme ve başlatmak için `cust10` ve `cust11`.</span><span class="sxs-lookup"><span data-stu-id="87b16-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   <span data-ttu-id="87b16-142">Nesne başlatıcıları iç içe.</span><span class="sxs-lookup"><span data-stu-id="87b16-142">Object initializers can be nested.</span></span> <span data-ttu-id="87b16-143">Aşağıdaki örnekte, `AddressClass` iki özelliğe sahip bir sınıf `City` ve `State`ve `Customer` sınıfına sahip bir `Address` örneği özelliği `AddressClass`.</span><span class="sxs-lookup"><span data-stu-id="87b16-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   <span data-ttu-id="87b16-144">Başlatma listesi boş olamaz.</span><span class="sxs-lookup"><span data-stu-id="87b16-144">The initialization list cannot be empty.</span></span>  
  
-   <span data-ttu-id="87b16-145">Başlatılmakta örnek nesne türünde olamaz.</span><span class="sxs-lookup"><span data-stu-id="87b16-145">The instance being initialized cannot be of type Object.</span></span>  
  
-   <span data-ttu-id="87b16-146">Sınıf üyeleri başlatılmakta paylaşılan üyeler, salt okunur üyeler, sabitleri ve yöntem çağrılarını olamaz.</span><span class="sxs-lookup"><span data-stu-id="87b16-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
-   <span data-ttu-id="87b16-147">Sınıf üyeleri başlatılmakta dizine veya tam.</span><span class="sxs-lookup"><span data-stu-id="87b16-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="87b16-148">Aşağıdaki örnekler derleyici hataları Yükselt:</span><span class="sxs-lookup"><span data-stu-id="87b16-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="87b16-149">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="87b16-149">Anonymous Types</span></span>  
 <span data-ttu-id="87b16-150">Anonim türler nesne başlatıcıları değil açıkça tanımladığınız yeni türler ve ad örnekleri oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="87b16-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="87b16-151">Bunun yerine, derleyici nesne Başlatıcı listesinde belirttiğiniz özellikler göre bir türü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87b16-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="87b16-152">Türünün adı belirtilmediğinden, bu olarak adlandırılır bir *anonim tür*.</span><span class="sxs-lookup"><span data-stu-id="87b16-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="87b16-153">Örneğin, aşağıdaki bildirimi için önceki bir karşılaştırma `cust6`.</span><span class="sxs-lookup"><span data-stu-id="87b16-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 <span data-ttu-id="87b16-154">Yalnızca sözdizimsel olarak ad sonra belirttiğiniz farktır `New` veri türü için.</span><span class="sxs-lookup"><span data-stu-id="87b16-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="87b16-155">Ancak, oldukça farklı olur.</span><span class="sxs-lookup"><span data-stu-id="87b16-155">However, what happens is quite different.</span></span> <span data-ttu-id="87b16-156">İki özelliklere sahip yeni bir anonim tür derleyici tanımlar `Name` ve `City`ve belirtilen değerlerle bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87b16-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="87b16-157">Tür çıkarımı belirler türlerini `Name` ve `City` dizeleri olması için örnekte.</span><span class="sxs-lookup"><span data-stu-id="87b16-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="87b16-158">Anonim tür adını derleyici tarafından üretilen ve derleme derleme farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="87b16-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="87b16-159">Kodunuzu kullanın veya anonim bir tür adına bağlı gerekir.</span><span class="sxs-lookup"><span data-stu-id="87b16-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="87b16-160">Ad türü kullanılabilir olmadığından kullanamazsınız bir `As` bildirmek için yan tümcesi `cust13`.</span><span class="sxs-lookup"><span data-stu-id="87b16-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="87b16-161">Tür çıkarımı yapılan gerekir.</span><span class="sxs-lookup"><span data-stu-id="87b16-161">Its type must be inferred.</span></span> <span data-ttu-id="87b16-162">Geç bağlama kullanmadan bu anonim türleri yerel değişkenler için kullanımını kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="87b16-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="87b16-163">Anonim türler için kritik destek sağlar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="87b16-163">Anonymous types provide critical support for [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="87b16-164">Anonim türler sorgularda kullanımı hakkında daha fazla bilgi için bkz: [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) ve [Visual Basic'te LINQ giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span><span class="sxs-lookup"><span data-stu-id="87b16-164">For more information about the use of anonymous types in queries, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="87b16-165">Anonim türler hakkında açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87b16-165">Remarks About Anonymous Types</span></span>  
  
-   <span data-ttu-id="87b16-166">Genellikle, tüm veya anonim tür bildirimi özelliklerinin çoğu anahtar sözcüğü yazarak belirtilen anahtar özellikleri olur `Key` önünde özellik adı.</span><span class="sxs-lookup"><span data-stu-id="87b16-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     <span data-ttu-id="87b16-167">Anahtar özellikler hakkında daha fazla bilgi için bkz: [anahtar](../../../../visual-basic/language-reference/modifiers/key.md).</span><span class="sxs-lookup"><span data-stu-id="87b16-167">For more information about key properties, see [Key](../../../../visual-basic/language-reference/modifiers/key.md).</span></span>  
  
-   <span data-ttu-id="87b16-168">Anonim tür tanımları en az bir özellik bildirmelidir için türleri, başlatıcı listeleri gibi adlı.</span><span class="sxs-lookup"><span data-stu-id="87b16-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   <span data-ttu-id="87b16-169">Anonim bir türün bir örneği bildirilmişse derleyici eşleşen anonim tür tanımı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87b16-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="87b16-170">Adları ve özellikler veri türlerinde örneği bildiriminden alınır ve tanımında derleyici tarafından dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="87b16-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="87b16-171">Özellikler yok adlı ve adlandırılmış türü için olduğu gibi önceden tanımlı.</span><span class="sxs-lookup"><span data-stu-id="87b16-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="87b16-172">Bunların türlerine algılanır.</span><span class="sxs-lookup"><span data-stu-id="87b16-172">Their types are inferred.</span></span> <span data-ttu-id="87b16-173">Özellikler veri türlerini kullanarak belirtemezsiniz bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="87b16-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
-   <span data-ttu-id="87b16-174">Anonim türler ayrıca diğer çeşitli yollarla adlarını ve bunların özelliklerinin değerlerini kurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87b16-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="87b16-175">Örneğin, anonim tür özellik hem adı hem de değeri bir değişken veya ad ve başka bir nesnenin bir özelliğini değerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="87b16-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     <span data-ttu-id="87b16-176">Anonim türleri özelliklerini tanımlamak için seçenekleri hakkında daha fazla bilgi için bkz: [nasıl yapılır: Infer özellik adları ve türlerini anonim türde bildirimlerden](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="87b16-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87b16-177">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87b16-177">See Also</span></span>  
 [<span data-ttu-id="87b16-178">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="87b16-178">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="87b16-179">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="87b16-179">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="87b16-180">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="87b16-180">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="87b16-181">Nasıl yapılır: özellik adları ve türlerini anonim türde bildirimlerden çıkarma</span><span class="sxs-lookup"><span data-stu-id="87b16-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [<span data-ttu-id="87b16-182">Anahtarı</span><span class="sxs-lookup"><span data-stu-id="87b16-182">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)  
 [<span data-ttu-id="87b16-183">Nasıl yapılır: nesne Başlatıcı kullanarak nesne bildirme</span><span class="sxs-lookup"><span data-stu-id="87b16-183">How to: Declare an Object by Using an Object Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
