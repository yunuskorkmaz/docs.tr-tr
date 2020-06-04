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
ms.openlocfilehash: 5561812a53e2fe45c3ad4d12d0e18a8a1e948559
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411772"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="911b6-102">Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="911b6-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="911b6-103">Nesne başlatıcıları, tek bir ifade kullanarak karmaşık bir nesne için özellikler belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="911b6-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="911b6-104">Bunlar, adlandırılmış türlerin örnekleri ve anonim türler oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="911b6-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="911b6-105">Bildirimler</span><span class="sxs-lookup"><span data-stu-id="911b6-105">Declarations</span></span>  
 <span data-ttu-id="911b6-106">Adlandırılmış ve anonim türdeki örneklerin bildirimleri neredeyse özdeş olabilir, ancak etkileri aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="911b6-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="911b6-107">Her kategori kendi yeteneklerini ve kısıtlamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="911b6-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="911b6-108">Aşağıdaki örnek, `Customer` bir nesne Başlatıcısı listesi kullanarak, adlandırılmış bir sınıfın bir örneğini bildirmek ve başlatmak için kullanışlı bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="911b6-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="911b6-109">Sınıfın adının anahtar sözcüğünden sonra belirtildiğine dikkat edin `New` .</span><span class="sxs-lookup"><span data-stu-id="911b6-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 <span data-ttu-id="911b6-110">Anonim bir türün kullanılabilir adı yok.</span><span class="sxs-lookup"><span data-stu-id="911b6-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="911b6-111">Bu nedenle, anonim bir türün örneklemesi bir sınıf adı içeremez.</span><span class="sxs-lookup"><span data-stu-id="911b6-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 <span data-ttu-id="911b6-112">İki bildirime ait gereksinimler ve sonuçlar aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="911b6-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="911b6-113">İçin `namedCust` , özelliği olan bir `Customer` sınıf `Name` zaten var olmalıdır ve bildirim bu sınıfın bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="911b6-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="911b6-114">İçin `anonymousCust` , derleyici bir özelliğine sahip olan ve bir dize adlı yeni bir sınıf tanımlar `Name` ve bu sınıfın yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="911b6-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="911b6-115">Adlandırılmış türler</span><span class="sxs-lookup"><span data-stu-id="911b6-115">Named Types</span></span>  
 <span data-ttu-id="911b6-116">Nesne başlatıcıları, bir türün yapıcısını çağırmak için basit bir yol sağlar ve sonra bazı veya tüm özelliklerin değerlerini tek bir deyime göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="911b6-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="911b6-117">Derleyici, bir veya daha fazla bağımsız değişken gönderildiyse parametresiz Oluşturucu veya bir veya daha fazla bağımsız değişken gönderilirse parametreli Oluşturucu olarak ifade için uygun oluşturucuyu çağırır.</span><span class="sxs-lookup"><span data-stu-id="911b6-117">The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="911b6-118">Bundan sonra, belirtilen özellikler Başlatıcı listesinde sunuldukları sırada başlatılır.</span><span class="sxs-lookup"><span data-stu-id="911b6-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="911b6-119">Başlatıcı listesindeki her başlatma, sınıfın bir üyesine ilk değer atamasından oluşur.</span><span class="sxs-lookup"><span data-stu-id="911b6-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="911b6-120">Üyelerin adları ve veri türleri, sınıf tanımlandığında belirlenir.</span><span class="sxs-lookup"><span data-stu-id="911b6-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="911b6-121">Aşağıdaki örneklerde, `Customer` sınıfı bulunmalı ve `Name` `City` dize değerlerini kabul edebilecek ve adlı üyelere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="911b6-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 <span data-ttu-id="911b6-122">Alternatif olarak, aşağıdaki kodu kullanarak aynı sonucu elde edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="911b6-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 <span data-ttu-id="911b6-123">Bu bildirimlerin her biri, parametresiz oluşturucuyu kullanarak bir nesne oluşturan aşağıdaki örneğe eşdeğerdir `Customer` ve sonra `Name` `City` bir ifade kullanarak ve özellikleri için başlangıç değerlerini belirtir `With` .</span><span class="sxs-lookup"><span data-stu-id="911b6-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 <span data-ttu-id="911b6-124">`Customer`Sınıfı için bir değer içinde göndermenizi sağlayan parametreli bir Oluşturucu içeriyorsa, `Name` Örneğin, aşağıdaki yollarla bir nesneyi de bildirip başlatabilirsiniz `Customer` :</span><span class="sxs-lookup"><span data-stu-id="911b6-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 <span data-ttu-id="911b6-125">Aşağıdaki kodda gösterildiği gibi tüm özellikleri başlatmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="911b6-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 <span data-ttu-id="911b6-126">Ancak, başlatma listesi boş olamaz.</span><span class="sxs-lookup"><span data-stu-id="911b6-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="911b6-127">Başlatılmamış özellikler varsayılan değerlerini korurlar.</span><span class="sxs-lookup"><span data-stu-id="911b6-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="911b6-128">Adlandırılmış türlerle tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="911b6-128">Type Inference with Named Types</span></span>  
 <span data-ttu-id="911b6-129">`cust1`Nesne başlatıcılarının ve yerel tür çıkarımını birleştirerek bildirimi için kodu kısaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="911b6-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="911b6-130">Bu, `As` değişken bildiriminde yan tümceyi atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="911b6-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="911b6-131">Değişkenin veri türü, atama tarafından oluşturulan nesnenin türünden algılanır.</span><span class="sxs-lookup"><span data-stu-id="911b6-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="911b6-132">Aşağıdaki örnekte, türü ' `cust6` dir `Customer` .</span><span class="sxs-lookup"><span data-stu-id="911b6-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="911b6-133">Adlandırılmış türler hakkında açıklamalar</span><span class="sxs-lookup"><span data-stu-id="911b6-133">Remarks About Named Types</span></span>  
  
- <span data-ttu-id="911b6-134">Bir sınıf üyesi, nesne başlatıcısı listesinde birden çok kez başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="911b6-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="911b6-135">Bildirimi `cust7` bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="911b6-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- <span data-ttu-id="911b6-136">Bir üye, kendisini veya başka bir alanı başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="911b6-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="911b6-137">Bir üyeye, için aşağıdaki bildirimde olduğu gibi, başlatılmadan önce erişiliyorsa `cust8` , varsayılan değer kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="911b6-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="911b6-138">Bir nesne Başlatıcısı kullanan bir bildirim işlendiğinde, gerçekleşen ilk şey uygun oluşturucunun çağrılmakta olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="911b6-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="911b6-139">Bundan sonra, Başlatıcı listesindeki ayrı alanlar başlatılır.</span><span class="sxs-lookup"><span data-stu-id="911b6-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="911b6-140">Aşağıdaki örneklerde için varsayılan değeri `Name` için atanır `cust8` ve başlatılmış bir değer içinde atanır `cust9` .</span><span class="sxs-lookup"><span data-stu-id="911b6-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     <span data-ttu-id="911b6-141">Aşağıdaki örnek, ve ' den ' i `cust3` `cust4` bildirmek ve başlatmak için parametreli oluşturucuyu kullanır `cust10` `cust11` .</span><span class="sxs-lookup"><span data-stu-id="911b6-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- <span data-ttu-id="911b6-142">Nesne başlatıcıları iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="911b6-142">Object initializers can be nested.</span></span> <span data-ttu-id="911b6-143">Aşağıdaki örnekte, `AddressClass` iki özelliği olan `City` ve sınıfının bir örneği olan bir `State` `Customer` özelliğine sahip olan `Address` bir sınıftır `AddressClass` .</span><span class="sxs-lookup"><span data-stu-id="911b6-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- <span data-ttu-id="911b6-144">Başlatma listesi boş olamaz.</span><span class="sxs-lookup"><span data-stu-id="911b6-144">The initialization list cannot be empty.</span></span>  
  
- <span data-ttu-id="911b6-145">Başlatılan örnek Object türünde olamaz.</span><span class="sxs-lookup"><span data-stu-id="911b6-145">The instance being initialized cannot be of type Object.</span></span>  
  
- <span data-ttu-id="911b6-146">Başlatılan sınıf üyeleri, paylaşılan Üyeler, salt okuma üyeleri, sabitler veya yöntem çağrıları olamaz.</span><span class="sxs-lookup"><span data-stu-id="911b6-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
- <span data-ttu-id="911b6-147">Başlatılan sınıf üyeleri dizinlenemez veya nitelenmiyor.</span><span class="sxs-lookup"><span data-stu-id="911b6-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="911b6-148">Aşağıdaki örnekler derleyici hatalarını yükseltir:</span><span class="sxs-lookup"><span data-stu-id="911b6-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="911b6-149">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="911b6-149">Anonymous Types</span></span>  
 <span data-ttu-id="911b6-150">Anonim türler, açıkça tanımlamadığınız ve isimsiz olmayan yeni türlerin örneklerini oluşturmak için nesne başlatıcıları kullanır.</span><span class="sxs-lookup"><span data-stu-id="911b6-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="911b6-151">Bunun yerine, derleyici, nesne başlatıcısı listesinde belirleyeceğiniz özelliklere göre bir tür üretir.</span><span class="sxs-lookup"><span data-stu-id="911b6-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="911b6-152">Türün adı belirtilmediğinden, *anonim bir tür*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="911b6-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="911b6-153">Örneğin, aşağıdaki bildirimi ile için daha önceki bir ile karşılaştırın `cust6` .</span><span class="sxs-lookup"><span data-stu-id="911b6-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 <span data-ttu-id="911b6-154">Tek fark sözdizimi, veri türü için sonrasında hiçbir adın belirtilme türüdür `New` .</span><span class="sxs-lookup"><span data-stu-id="911b6-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="911b6-155">Ancak, ne olur oldukça farklıdır.</span><span class="sxs-lookup"><span data-stu-id="911b6-155">However, what happens is quite different.</span></span> <span data-ttu-id="911b6-156">Derleyici, ve ' ı iki özelliği olan yeni bir anonim türü `Name` tanımlar `City` ve belirtilen değerlerle bir örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="911b6-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="911b6-157">Tür çıkarımı, `Name` `City` dizeler gibi örnekte ve türlerini belirler.</span><span class="sxs-lookup"><span data-stu-id="911b6-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="911b6-158">Anonim türün adı derleyici tarafından oluşturulur ve derlemeden derlemeye değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="911b6-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="911b6-159">Kodunuz, anonim bir türün adını kullanmamalıdır veya bu adı kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="911b6-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="911b6-160">Türün adı kullanılamadığından, öğesini `As` bildirmek için bir yan tümce kullanamazsınız `cust13` .</span><span class="sxs-lookup"><span data-stu-id="911b6-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="911b6-161">Türü çıkarsanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="911b6-161">Its type must be inferred.</span></span> <span data-ttu-id="911b6-162">Bu, geç bağlama kullanılmadan, anonim türlerin kullanımını yerel değişkenlere kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="911b6-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="911b6-163">Anonim türler, LINQ sorguları için kritik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="911b6-163">Anonymous types provide critical support for LINQ queries.</span></span> <span data-ttu-id="911b6-164">Sorgularda anonim türlerin kullanımı hakkında daha fazla bilgi için, bkz. Visual Basic [anonim türler](anonymous-types.md) ve [lınq 'ye giriş](../linq/introduction-to-linq.md).</span><span class="sxs-lookup"><span data-stu-id="911b6-164">For more information about the use of anonymous types in queries, see [Anonymous Types](anonymous-types.md) and [Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="911b6-165">Anonim türler hakkında açıklamalar</span><span class="sxs-lookup"><span data-stu-id="911b6-165">Remarks About Anonymous Types</span></span>  
  
- <span data-ttu-id="911b6-166">Genellikle, anonim bir tür bildirimindeki özelliklerin tümü veya çoğu, özellik adının önüne anahtar sözcüğü yazılarak belirtilen temel özelliklerdir `Key` .</span><span class="sxs-lookup"><span data-stu-id="911b6-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     <span data-ttu-id="911b6-167">Anahtar özellikleri hakkında daha fazla bilgi için bkz. [anahtar](../../../language-reference/modifiers/key.md).</span><span class="sxs-lookup"><span data-stu-id="911b6-167">For more information about key properties, see [Key](../../../language-reference/modifiers/key.md).</span></span>  
  
- <span data-ttu-id="911b6-168">Adlandırılmış türler gibi, anonim tür tanımlarının başlatıcı listeleri en az bir özellik bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="911b6-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- <span data-ttu-id="911b6-169">Anonim türün bir örneği bildirildiğinde, derleyici eşleşen bir anonim tür tanımı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="911b6-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="911b6-170">Özelliklerin adları ve veri türleri örnek bildiriminden alınır ve tanımda derleyici tarafından dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="911b6-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="911b6-171">Adlandırılmış bir tür için olduklarından özellikler önceden adlandırılmaz ve önceden tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="911b6-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="911b6-172">Türleri algılanır.</span><span class="sxs-lookup"><span data-stu-id="911b6-172">Their types are inferred.</span></span> <span data-ttu-id="911b6-173">Bir yan tümce kullanarak özelliklerin veri türlerini belirtemezsiniz `As` .</span><span class="sxs-lookup"><span data-stu-id="911b6-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
- <span data-ttu-id="911b6-174">Anonim türler, özelliklerinin adlarını ve değerlerini birkaç farklı yolla de kurabilir.</span><span class="sxs-lookup"><span data-stu-id="911b6-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="911b6-175">Örneğin, anonim bir tür özelliği bir değişkenin adını ve değerini ya da başka bir nesnenin özelliğinin adını ve değerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="911b6-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     <span data-ttu-id="911b6-176">Anonim türlerde özellikleri tanımlamaya yönelik seçenekler hakkında daha fazla bilgi için bkz. [nasıl yapılır: özellik adlarını ve türleri anonim tür bildirimlerinde çıkarım](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="911b6-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911b6-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="911b6-177">See also</span></span>

- [<span data-ttu-id="911b6-178">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="911b6-178">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="911b6-179">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="911b6-179">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="911b6-180">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="911b6-180">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="911b6-181">Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma</span><span class="sxs-lookup"><span data-stu-id="911b6-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="911b6-182">Anahtar</span><span class="sxs-lookup"><span data-stu-id="911b6-182">Key</span></span>](../../../language-reference/modifiers/key.md)
- [<span data-ttu-id="911b6-183">Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesne Bildirme</span><span class="sxs-lookup"><span data-stu-id="911b6-183">How to: Declare an Object by Using an Object Initializer</span></span>](how-to-declare-an-object-by-using-an-object-initializer.md)
