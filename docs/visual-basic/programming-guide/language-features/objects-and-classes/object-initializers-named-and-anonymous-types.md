---
title: 'Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: e6ffc649d7eb841c2d009b0ec1237975f46e2d2d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636815"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="f7097-102">Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7097-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="f7097-103">Nesne başlatıcıları, tek bir ifade kullanarak karmaşık bir nesne için özellikler belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f7097-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="f7097-104">Bunlar, adlandırılmış türlerin örnekleri ve anonim türler oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7097-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="f7097-105">Bildirimler</span><span class="sxs-lookup"><span data-stu-id="f7097-105">Declarations</span></span>  
 <span data-ttu-id="f7097-106">Adlandırılmış ve anonim türdeki örneklerin bildirimleri neredeyse özdeş olabilir, ancak etkileri aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="f7097-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="f7097-107">Her kategori kendi yeteneklerini ve kısıtlamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f7097-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="f7097-108">Aşağıdaki örnek, bir nesne Başlatıcısı listesi kullanarak `Customer`adlandırılmış bir sınıfın örneğini bildirmek ve başlatmak için kullanışlı bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7097-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="f7097-109">Sınıf adının `New`anahtar sözcüğünden sonra belirtildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f7097-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 <span data-ttu-id="f7097-110">Anonim bir türün kullanılabilir adı yok.</span><span class="sxs-lookup"><span data-stu-id="f7097-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="f7097-111">Bu nedenle, anonim bir türün örneklemesi bir sınıf adı içeremez.</span><span class="sxs-lookup"><span data-stu-id="f7097-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 <span data-ttu-id="f7097-112">İki bildirime ait gereksinimler ve sonuçlar aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="f7097-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="f7097-113">`namedCust`için, bir `Name` özelliğine sahip bir `Customer` sınıfı zaten var olmalıdır ve bildirim bu sınıfın bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7097-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="f7097-114">`anonymousCust`, derleyici bir özelliği olan yeni bir sınıf tanımlar, `Name`adlı bir dize ve bu sınıfın yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7097-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="f7097-115">Adlandırılmış türler</span><span class="sxs-lookup"><span data-stu-id="f7097-115">Named Types</span></span>  
 <span data-ttu-id="f7097-116">Nesne başlatıcıları, bir türün yapıcısını çağırmak için basit bir yol sağlar ve sonra bazı veya tüm özelliklerin değerlerini tek bir deyime göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f7097-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="f7097-117">Derleyici, bir veya daha fazla bağımsız değişken gönderildiyse parametresiz Oluşturucu veya bir veya daha fazla bağımsız değişken gönderilirse parametreli Oluşturucu olarak ifade için uygun oluşturucuyu çağırır.</span><span class="sxs-lookup"><span data-stu-id="f7097-117">The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="f7097-118">Bundan sonra, belirtilen özellikler Başlatıcı listesinde sunuldukları sırada başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f7097-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="f7097-119">Başlatıcı listesindeki her başlatma, sınıfın bir üyesine ilk değer atamasından oluşur.</span><span class="sxs-lookup"><span data-stu-id="f7097-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="f7097-120">Üyelerin adları ve veri türleri, sınıf tanımlandığında belirlenir.</span><span class="sxs-lookup"><span data-stu-id="f7097-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="f7097-121">Aşağıdaki örneklerde `Customer` sınıfı var olmalıdır ve dize değerlerini kabul edebilecek `Name` ve `City` adlı üyelere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7097-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 <span data-ttu-id="f7097-122">Alternatif olarak, aşağıdaki kodu kullanarak aynı sonucu elde edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f7097-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 <span data-ttu-id="f7097-123">Bu bildirimlerin her biri, parametresiz oluşturucuyu kullanarak bir `Customer` nesnesi oluşturan aşağıdaki örneğe eşdeğerdir ve sonra `Name` ve `City` özellikler için ilk değerleri `With` bir ifade kullanarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7097-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 <span data-ttu-id="f7097-124">`Customer` sınıfı, `Name`için bir değer göndermenizi sağlayan parametreli bir Oluşturucu içeriyorsa, örneğin, aşağıdaki yollarla bir `Customer` nesnesi bildirip de başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f7097-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 <span data-ttu-id="f7097-125">Aşağıdaki kodda gösterildiği gibi tüm özellikleri başlatmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7097-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 <span data-ttu-id="f7097-126">Ancak, başlatma listesi boş olamaz.</span><span class="sxs-lookup"><span data-stu-id="f7097-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="f7097-127">Başlatılmamış özellikler varsayılan değerlerini korurlar.</span><span class="sxs-lookup"><span data-stu-id="f7097-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="f7097-128">Adlandırılmış türlerle tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="f7097-128">Type Inference with Named Types</span></span>  
 <span data-ttu-id="f7097-129">Nesne başlatıcıları ve yerel tür çıkarımı birleştirerek `cust1` bildirimi için kodu kısaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7097-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="f7097-130">Bu, değişken bildiriminde `As` yan tümcesini atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7097-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="f7097-131">Değişkenin veri türü, atama tarafından oluşturulan nesnenin türünden algılanır.</span><span class="sxs-lookup"><span data-stu-id="f7097-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="f7097-132">Aşağıdaki örnekte `cust6` türü `Customer`.</span><span class="sxs-lookup"><span data-stu-id="f7097-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="f7097-133">Adlandırılmış türler hakkında açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7097-133">Remarks About Named Types</span></span>  
  
- <span data-ttu-id="f7097-134">Bir sınıf üyesi, nesne başlatıcısı listesinde birden çok kez başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="f7097-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="f7097-135">`cust7` bildirimi hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="f7097-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- <span data-ttu-id="f7097-136">Bir üye, kendisini veya başka bir alanı başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7097-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="f7097-137">Bir üyeye başlatıldıktan sonra, `cust8`için aşağıdaki bildirimde olduğu gibi, varsayılan değer kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="f7097-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="f7097-138">Bir nesne Başlatıcısı kullanan bir bildirim işlendiğinde, gerçekleşen ilk şey uygun oluşturucunun çağrılmakta olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f7097-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="f7097-139">Bundan sonra, Başlatıcı listesindeki ayrı alanlar başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f7097-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="f7097-140">Aşağıdaki örneklerde `Name` için varsayılan değer `cust8`atanır ve başlatılmış bir değer `cust9`atanır.</span><span class="sxs-lookup"><span data-stu-id="f7097-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     <span data-ttu-id="f7097-141">Aşağıdaki örnek, `cust10` ve `cust11`bildirmek ve başlatmak için `cust3` ve `cust4` parametreli oluşturucuyu kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7097-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- <span data-ttu-id="f7097-142">Nesne başlatıcıları iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7097-142">Object initializers can be nested.</span></span> <span data-ttu-id="f7097-143">Aşağıdaki örnekte `AddressClass`, `City` ve `State`iki özelliği olan bir sınıftır ve `Customer` sınıfı `Address` örneği olan bir `AddressClass`özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f7097-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- <span data-ttu-id="f7097-144">Başlatma listesi boş olamaz.</span><span class="sxs-lookup"><span data-stu-id="f7097-144">The initialization list cannot be empty.</span></span>  
  
- <span data-ttu-id="f7097-145">Başlatılan örnek Object türünde olamaz.</span><span class="sxs-lookup"><span data-stu-id="f7097-145">The instance being initialized cannot be of type Object.</span></span>  
  
- <span data-ttu-id="f7097-146">Başlatılan sınıf üyeleri, paylaşılan Üyeler, salt okuma üyeleri, sabitler veya yöntem çağrıları olamaz.</span><span class="sxs-lookup"><span data-stu-id="f7097-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
- <span data-ttu-id="f7097-147">Başlatılan sınıf üyeleri dizinlenemez veya nitelenmiyor.</span><span class="sxs-lookup"><span data-stu-id="f7097-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="f7097-148">Aşağıdaki örnekler derleyici hatalarını yükseltir:</span><span class="sxs-lookup"><span data-stu-id="f7097-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="f7097-149">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="f7097-149">Anonymous Types</span></span>  
 <span data-ttu-id="f7097-150">Anonim türler, açıkça tanımlamadığınız ve isimsiz olmayan yeni türlerin örneklerini oluşturmak için nesne başlatıcıları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7097-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="f7097-151">Bunun yerine, derleyici, nesne başlatıcısı listesinde belirleyeceğiniz özelliklere göre bir tür üretir.</span><span class="sxs-lookup"><span data-stu-id="f7097-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="f7097-152">Türün adı belirtilmediğinden, *anonim bir tür*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f7097-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="f7097-153">Örneğin, aşağıdaki bildirimi `cust6`için önceki bir ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="f7097-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 <span data-ttu-id="f7097-154">Tek fark sözdizimi, veri türü için `New` sonrasında hiçbir adın belirtilme türüdür.</span><span class="sxs-lookup"><span data-stu-id="f7097-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="f7097-155">Ancak, ne olur oldukça farklıdır.</span><span class="sxs-lookup"><span data-stu-id="f7097-155">However, what happens is quite different.</span></span> <span data-ttu-id="f7097-156">Derleyici, `Name` ve `City`iki özelliği olan yeni bir anonim tür tanımlar ve belirtilen değerlerle bunun bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7097-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="f7097-157">Tür çıkarımı, dizeler gibi örnekteki `Name` ve `City` türlerini belirler.</span><span class="sxs-lookup"><span data-stu-id="f7097-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f7097-158">Anonim türün adı derleyici tarafından oluşturulur ve derlemeden derlemeye değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f7097-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="f7097-159">Kodunuz, anonim bir türün adını kullanmamalıdır veya bu adı kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7097-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="f7097-160">Türün adı kullanılamadığından, `cust13`bildirmek için bir `As` yan tümcesi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f7097-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="f7097-161">Türü çıkarsanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7097-161">Its type must be inferred.</span></span> <span data-ttu-id="f7097-162">Bu, geç bağlama kullanılmadan, anonim türlerin kullanımını yerel değişkenlere kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="f7097-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="f7097-163">Anonim türler, LINQ sorguları için kritik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7097-163">Anonymous types provide critical support for LINQ queries.</span></span> <span data-ttu-id="f7097-164">Sorgularda anonim türlerin kullanımı hakkında daha fazla bilgi için, bkz. Visual Basic [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) ve [lınq 'ye giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span><span class="sxs-lookup"><span data-stu-id="f7097-164">For more information about the use of anonymous types in queries, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="f7097-165">Anonim türler hakkında açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7097-165">Remarks About Anonymous Types</span></span>  
  
- <span data-ttu-id="f7097-166">Genellikle, anonim bir tür bildirimindeki özelliklerin tümü veya çoğu, özellik adının önüne `Key` anahtar sözcüğü yazılarak belirtilen temel özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="f7097-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     <span data-ttu-id="f7097-167">Anahtar özellikleri hakkında daha fazla bilgi için bkz. [anahtar](../../../../visual-basic/language-reference/modifiers/key.md).</span><span class="sxs-lookup"><span data-stu-id="f7097-167">For more information about key properties, see [Key](../../../../visual-basic/language-reference/modifiers/key.md).</span></span>  
  
- <span data-ttu-id="f7097-168">Adlandırılmış türler gibi, anonim tür tanımlarının başlatıcı listeleri en az bir özellik bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="f7097-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- <span data-ttu-id="f7097-169">Anonim türün bir örneği bildirildiğinde, derleyici eşleşen bir anonim tür tanımı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7097-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="f7097-170">Özelliklerin adları ve veri türleri örnek bildiriminden alınır ve tanımda derleyici tarafından dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="f7097-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="f7097-171">Adlandırılmış bir tür için olduklarından özellikler önceden adlandırılmaz ve önceden tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="f7097-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="f7097-172">Türleri algılanır.</span><span class="sxs-lookup"><span data-stu-id="f7097-172">Their types are inferred.</span></span> <span data-ttu-id="f7097-173">`As` yan tümcesini kullanarak özelliklerin veri türlerini belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7097-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
- <span data-ttu-id="f7097-174">Anonim türler, özelliklerinin adlarını ve değerlerini birkaç farklı yolla de kurabilir.</span><span class="sxs-lookup"><span data-stu-id="f7097-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="f7097-175">Örneğin, anonim bir tür özelliği bir değişkenin adını ve değerini ya da başka bir nesnenin özelliğinin adını ve değerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="f7097-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     <span data-ttu-id="f7097-176">Anonim türlerde özellikleri tanımlamaya yönelik seçenekler hakkında daha fazla bilgi için bkz. [nasıl yapılır: özellik adlarını ve türleri anonim tür bildirimlerinde çıkarım](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="f7097-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7097-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7097-177">See also</span></span>

- [<span data-ttu-id="f7097-178">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="f7097-178">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="f7097-179">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="f7097-179">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="f7097-180">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="f7097-180">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f7097-181">Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma</span><span class="sxs-lookup"><span data-stu-id="f7097-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="f7097-182">Key</span><span class="sxs-lookup"><span data-stu-id="f7097-182">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
- [<span data-ttu-id="f7097-183">Nasıl yapılır: Nesne Başlatıcısı Kullanarak Nesne Bildirme</span><span class="sxs-lookup"><span data-stu-id="f7097-183">How to: Declare an Object by Using an Object Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
