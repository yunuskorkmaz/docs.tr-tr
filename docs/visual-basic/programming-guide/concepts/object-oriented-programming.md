---
title: Nesne odaklı programlama (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 058d8b932e50f784d4a5cefa9fadfb31953687f0
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297094"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="a9e82-102">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9e82-102">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="a9e82-103">Visual Basic kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne yönelimli programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9e82-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="a9e82-104">*Kapsülleme* ilgili özellikleri, yöntemleri ve diğer üyeleri bir grup işlem tek bir birim veya nesne anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="a9e82-105">*Devralma* mevcut bir sınıfı temel alan yeni sınıflar oluşturma becerisidir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="a9e82-106">*Çok biçimlilik* her sınıf aynı özellikleri veya yöntemleri farklı şekilde uygular olsa da birbirinin yerine kullanılabilen birden fazla sınıfınız olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="a9e82-107">Bu bölüm aşağıdaki kavramları açıklar:</span><span class="sxs-lookup"><span data-stu-id="a9e82-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="a9e82-108">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="a9e82-108">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="a9e82-109">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="a9e82-109">Class members</span></span>](#class-members)
    - [<span data-ttu-id="a9e82-110">Özellikler ve alanları</span><span class="sxs-lookup"><span data-stu-id="a9e82-110">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="a9e82-111">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a9e82-111">Methods</span></span>](#methods)
    - [<span data-ttu-id="a9e82-112">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a9e82-112">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="a9e82-113">Yıkıcılar</span><span class="sxs-lookup"><span data-stu-id="a9e82-113">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="a9e82-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="a9e82-114">Events</span></span>](#events)
    - [<span data-ttu-id="a9e82-115">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="a9e82-115">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="a9e82-116">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a9e82-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="a9e82-117">Sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="a9e82-117">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="a9e82-118">Paylaşılan sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="a9e82-118">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="a9e82-119">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="a9e82-119">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="a9e82-120">Devralma</span><span class="sxs-lookup"><span data-stu-id="a9e82-120">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="a9e82-121">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a9e82-121">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="a9e82-122">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a9e82-122">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="a9e82-123">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="a9e82-123">Generics</span></span>](#generics)
- [<span data-ttu-id="a9e82-124">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a9e82-124">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="a9e82-125">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="a9e82-125">Classes and objects</span></span>

<span data-ttu-id="a9e82-126">Koşulları *sınıfı* ve *nesne* bazen birbirlerinin yerine, ancak aslında sınıfları açıklar kullanılan *türü* nesnelerin nesneleri iken  *örnekleri* sınıf.</span><span class="sxs-lookup"><span data-stu-id="a9e82-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="a9e82-127">Bu nedenle, bir nesne oluşturma işlemi olarak da adlandırılır *oluşturmada*.</span><span class="sxs-lookup"><span data-stu-id="a9e82-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="a9e82-128">Blueprint benzerliği kullanarak bir sınıf plandır ve nesne bu yapılan bir binadır.</span><span class="sxs-lookup"><span data-stu-id="a9e82-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="a9e82-129">Bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-129">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="a9e82-130">Visual Basic, hafif bir sınıflar adlandırılan sürümünü de sağlar *yapıları* yapın ve büyük nesneler dizisi oluşturmanız gerektiğinde yararlı olan çok fazla bellek için kullanmak istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="a9e82-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="a9e82-131">Yapı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-131">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="a9e82-132">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a9e82-132">For more information, see:</span></span>

- [<span data-ttu-id="a9e82-133">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="a9e82-134">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="a9e82-135">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="a9e82-135">Class members</span></span>

<span data-ttu-id="a9e82-136">Her sınıf farklı olabilir *sınıf üyeleri* sınıf verilerini, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasındaki iletişimi sağlayan olayları tanımlayan özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="a9e82-137">Özellikler ve alanları</span><span class="sxs-lookup"><span data-stu-id="a9e82-137">Properties and fields</span></span>

<span data-ttu-id="a9e82-138">Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a9e82-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="a9e82-139">Bunlar okunabilir ve doğrudan ayarlamak için alanları gibi değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="a9e82-140">Bir alanı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="a9e82-141">Özellik get ve set yordamları, değerlerin nasıl ayarlanacağı veya döndürüleceği hakkında daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9e82-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="a9e82-142">Visual Basic ya da özellik değerini depolamak için özel bir alan oluşturabilir veya bu alanı arka planda otomatik olarak oluşturmak ve özellik yordamları için temel mantığı sağlayan sözde ve otomatik olarak uygulanan özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9e82-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="a9e82-143">Otomatik uygulanan bir özellik tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="a9e82-144">Okuma için bazı ek işlemler gerçekleştirebilir ve yazma özellik değeri özellik değerini depolamak için bir alan tanımlayın ve depolanması ve alınması için temel mantığı sağlayan gerekiyorsa:</span><span class="sxs-lookup"><span data-stu-id="a9e82-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

<span data-ttu-id="a9e82-145">Çoğu özellikleri, yöntemleri ya da yordamlar hem ayarlamak ve özellik değerini almak için vardır.</span><span class="sxs-lookup"><span data-stu-id="a9e82-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="a9e82-146">Ancak, değiştiren veya okunmalarını kısıtlamak için salt okunur veya salt yazılır özellikler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9e82-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="a9e82-147">Visual Basic'te kullanabileceğiniz `ReadOnly` ve `WriteOnly` anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="a9e82-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="a9e82-148">Ancak, otomatik uygulanan özellikler salt okunur veya salt yazılır olamaz.</span><span class="sxs-lookup"><span data-stu-id="a9e82-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="a9e82-149">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a9e82-149">For more information, see:</span></span>

- [<span data-ttu-id="a9e82-150">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="a9e82-151">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="a9e82-152">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="a9e82-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="a9e82-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="a9e82-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="a9e82-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="a9e82-155">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a9e82-155">Methods</span></span>

 <span data-ttu-id="a9e82-156">A *yöntemi* , nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-156">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="a9e82-157">Visual Basic'te, bir yöntem oluşturmanın iki yolu vardır: `Sub` deyimi kullanılır; değer döndürmezse `Function` bir yöntem bir değer döndürüyorsa deyimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9e82-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="a9e82-158">Bir sınıfın yöntemini tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="a9e82-159">Bir sınıfta çeşitli uygulamalar olabilir veya *aşırı*, parametre sayıları veya parametre türleri içinde farklı aynı yöntemin.</span><span class="sxs-lookup"><span data-stu-id="a9e82-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="a9e82-160">Bir yöntemi aşırı yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="a9e82-161">Çoğu durumda, sınıf tanımında bir yöntem bildirin.</span><span class="sxs-lookup"><span data-stu-id="a9e82-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="a9e82-162">Ancak, Visual Basic de destekler *genişletme yöntemleri* mevcut sınıfa sınıfın gerçek tanımı dışında yöntemler eklemenize olanak tanıyan.</span><span class="sxs-lookup"><span data-stu-id="a9e82-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="a9e82-163">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a9e82-163">For more information, see:</span></span>

- [<span data-ttu-id="a9e82-164">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="a9e82-165">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="a9e82-166">Overloads</span><span class="sxs-lookup"><span data-stu-id="a9e82-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="a9e82-167">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a9e82-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="a9e82-168">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a9e82-168">Constructors</span></span>

<span data-ttu-id="a9e82-169">Oluşturucular, belirli bir türde bir nesne oluşturulduğunda, otomatik olarak yürütülen sınıf yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="a9e82-170">Kurucular genellikle yeni nesnenin veri üyeleri başlatın.</span><span class="sxs-lookup"><span data-stu-id="a9e82-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="a9e82-171">Sonra yalnızca bir sınıf oluşturulduğunda Oluşturucu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9e82-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="a9e82-172">Ayrıca, Oluşturucudaki kod her zaman bir sınıftaki herhangi bir kod önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="a9e82-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="a9e82-173">Ancak, başka bir yöntem olduğu gibi birden çok oluşturucu aşırı yüklemeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9e82-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="a9e82-174">Bir sınıf için bir kurucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="a9e82-175">Daha fazla bilgi için bkz: [nesne ömrü: nesneleri oluşturma ve Destroyed şeklini](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="a9e82-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="a9e82-176">Yıkıcılar</span><span class="sxs-lookup"><span data-stu-id="a9e82-176">Destructors</span></span>

<span data-ttu-id="a9e82-177">Yıkıcılar, sınıfların örneklerini yok etmek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9e82-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="a9e82-178">.NET Framework, atık toplayıcı sağlanmasını ve ayrılmasını uygulamanızda yönetilen nesneler için bellek otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="a9e82-179">Ancak, Yıkıcılar uygulamanızın oluşturduğu herhangi yönetilmeyen kaynakları temizlemek için yine de gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="a9e82-180">Bir sınıf için yalnızca bir yıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="a9e82-181">Yok ediciler ve çöp toplama .NET Framework'teki hakkında daha fazla bilgi için bkz: [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="a9e82-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="a9e82-182">Olaylar</span><span class="sxs-lookup"><span data-stu-id="a9e82-182">Events</span></span>

<span data-ttu-id="a9e82-183">Bir sınıf olayları etkinleştirin veya nesneyi diğer sınıfları veya nesneleri ilgilendiğiniz bir şeyler olduğunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="a9e82-184">Olay gönderir (veya harekete geçiren) sınıf adlı *yayımcı* ve olay alma (veya tanıtıcı) sınıflar adlandırılan *aboneleri*.</span><span class="sxs-lookup"><span data-stu-id="a9e82-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="a9e82-185">Olaylar hakkında daha fazla bilgi için nasıl oluştukları ve işlendikleri bkz [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="a9e82-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="a9e82-186">Olayları bildirmek için kullanın [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a9e82-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="a9e82-187">Olayları yükseltmek için kullanmak [RaiseEvent deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a9e82-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="a9e82-188">Bildirim temelli bir yöntemini kullanarak olay işleyicileri belirtmek için kullanın [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) deyimi ve [işleme](../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a9e82-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="a9e82-189">Dinamik olarak ekleme, kaldırma ve bir olay ile ilişkili olay işleyicisini değiştirme yapabilmek için kullanmak [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md) ve [RemoveHandler deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md) ile birlikte [AddressOf İşleç](../../../visual-basic/language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="a9e82-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="a9e82-190">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="a9e82-190">Nested classes</span></span>

<span data-ttu-id="a9e82-191">Başka bir sınıfın içinde tanımlanan bir sınıfa *iç içe geçmiş*.</span><span class="sxs-lookup"><span data-stu-id="a9e82-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="a9e82-192">Varsayılan olarak, iç içe geçmiş özel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="a9e82-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="a9e82-193">İç içe geçmiş sınıfının bir örneğini oluşturmak için kapsayıcı sınıfının arkasına bir nokta koyun ve sonra ardından iç içe geçmiş sınıf adı adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="a9e82-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="a9e82-194">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a9e82-194">Access modifiers and access levels</span></span>

<span data-ttu-id="a9e82-195">Tüm sınıflar ve sınıf üyeleri sağlamaları için diğer sınıflar kullanılarak hangi erişim düzeyini belirtebilirsiniz *erişim değiştiricilerine*.</span><span class="sxs-lookup"><span data-stu-id="a9e82-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="a9e82-196">Aşağıdaki erişim değiştiriciler kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a9e82-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="a9e82-197">Visual Basic değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="a9e82-197">Visual Basic Modifier</span></span>|<span data-ttu-id="a9e82-198">Tanım</span><span class="sxs-lookup"><span data-stu-id="a9e82-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="a9e82-199">Public</span><span class="sxs-lookup"><span data-stu-id="a9e82-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="a9e82-200">Türe veya üyeye aynı derlemenin veya ona başvuran başka bir derleme içindeki diğer kodlardan tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="a9e82-201">Private</span><span class="sxs-lookup"><span data-stu-id="a9e82-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="a9e82-202">Türe veya üyeye aynı sınıftaki kod tarafından yalnızca erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="a9e82-203">Protected</span><span class="sxs-lookup"><span data-stu-id="a9e82-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="a9e82-204">Türe veya üyeye aynı sınıftaki veya türetilmiş bir sınıf içinde kod tarafından yalnızca erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="a9e82-205">Friend</span><span class="sxs-lookup"><span data-stu-id="a9e82-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="a9e82-206">Türe veya üyeye aynı derlemedeki ancak farklı derlemeyle herhangi bir kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="a9e82-207">Türe veya üyeye aynı derlemedeki kod ile veya başka bir derlemedeki türetilmiş sınıfla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="a9e82-208">Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a9e82-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="a9e82-209">Sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="a9e82-209">Instantiating classes</span></span>

<span data-ttu-id="a9e82-210">Bir nesne oluşturmak için bir sınıf örneği başlatmanız veya sınıf örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="a9e82-211">Bir sınıf başlatıldıktan sonra Örneğin özelliklerine ve alanlarına değerler atayın ve sınıf yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9e82-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="a9e82-212">Sınıf örnekleme işlemi sırasında özellikleri değerleri atamak için nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="a9e82-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="a9e82-213">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a9e82-213">For more information, see:</span></span>

- [<span data-ttu-id="a9e82-214">New İşleci</span><span class="sxs-lookup"><span data-stu-id="a9e82-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="a9e82-215">Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="a9e82-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="a9e82-216">Paylaşılan sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="a9e82-216">Shared classes and members</span></span>

 <span data-ttu-id="a9e82-217">Paylaşılan bir sınıfın üyesi bir özellik, yordam veya bir sınıfın tüm örnekleri tarafından paylaşıldığını alan var.</span><span class="sxs-lookup"><span data-stu-id="a9e82-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="a9e82-218">Paylaşılan bir üye tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-218">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="a9e82-219">Paylaşılan üyeye erişmek için sınıfın adını, bu sınıfın bir nesnesi oluşturmadan kullanın:</span><span class="sxs-lookup"><span data-stu-id="a9e82-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="a9e82-220">Visual Basic'te paylaşılan modülleri, üyeleri yalnızca paylaşılan ve örnekleri oluşturulamaz.</span><span class="sxs-lookup"><span data-stu-id="a9e82-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="a9e82-221">Paylaşılan üyeleri ayrıca paylaşılmayan özellikleri, alanlara veya yöntemlere erişemez</span><span class="sxs-lookup"><span data-stu-id="a9e82-221">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="a9e82-222">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a9e82-222">For more information, see:</span></span>

- [<span data-ttu-id="a9e82-223">Shared</span><span class="sxs-lookup"><span data-stu-id="a9e82-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="a9e82-224">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="a9e82-225">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="a9e82-225">Anonymous types</span></span>

<span data-ttu-id="a9e82-226">Anonim türler nesne veri türü için bir sınıf tanımı yazmaya gerek kalmadan oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9e82-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="a9e82-227">Bunun yerine, derleyici bir sınıf sizin için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a9e82-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="a9e82-228">Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="a9e82-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="a9e82-229">Anonim bir türün bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="a9e82-230">Daha fazla bilgi için bkz: [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a9e82-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="a9e82-231">Devralma</span><span class="sxs-lookup"><span data-stu-id="a9e82-231">Inheritance</span></span>

<span data-ttu-id="a9e82-232">Devralma, başka bir sınıfta tanımlanan davranışı değiştirir kullanır ve genişleten yeni bir sınıf oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9e82-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="a9e82-233">Üyeleri devralınan sınıf *temel sınıfı*, ve bu üyeleri devralan sınıf *türetilmiş sınıf*.</span><span class="sxs-lookup"><span data-stu-id="a9e82-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="a9e82-234">Ancak, Visual Basic'te tüm sınıflar örtük olarak devralınacak <xref:System.Object> .NET sınıf hiyerarşisini destekleyen ve tüm sınıflara alt düzey hizmetler sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="a9e82-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="a9e82-235">Visual Basic, birden çok devralmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a9e82-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="a9e82-236">Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9e82-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="a9e82-237">Temel sınıfından devralmak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="a9e82-238">Varsayılan olarak, tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-238">By default all classes can be inherited.</span></span> <span data-ttu-id="a9e82-239">Ancak, bir sınıfın temel sınıf olarak kullanılmamalıdır veya yalnızca temel sınıf olarak kullanılan bir sınıf oluşturmak olup olmadığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9e82-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="a9e82-240">Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="a9e82-241">Bir sınıf yalnızca temel sınıf olarak kullanılabilecek ve başlatılamayacak belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="a9e82-242">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a9e82-242">For more information, see:</span></span>

- [<span data-ttu-id="a9e82-243">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="a9e82-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="a9e82-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="a9e82-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="a9e82-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="a9e82-246">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a9e82-246">Overriding members</span></span>

<span data-ttu-id="a9e82-247">Varsayılan olarak, türetilmiş bir sınıf tüm üyelerini kendi temel sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="a9e82-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="a9e82-248">Devralınan üye davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="a9e82-249">Diğer bir deyişle, türetilmiş bir sınıf içindeki yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9e82-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="a9e82-250">Özellikleri ve yöntemleri nasıl geçersiz kılınacağını denetlemek için aşağıdaki değiştiriciler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="a9e82-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="a9e82-251">Visual Basic değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="a9e82-251">Visual Basic Modifier</span></span>|<span data-ttu-id="a9e82-252">Tanım</span><span class="sxs-lookup"><span data-stu-id="a9e82-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="a9e82-253">Overridable</span><span class="sxs-lookup"><span data-stu-id="a9e82-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="a9e82-254">Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="a9e82-255">Overrides</span><span class="sxs-lookup"><span data-stu-id="a9e82-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="a9e82-256">Temel sınıfta tanımlanan sanal bir (geçersiz kılınabilir) üyeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a9e82-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="a9e82-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="a9e82-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="a9e82-258">Üye devralınan bir sınıfta kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="a9e82-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="a9e82-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="a9e82-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="a9e82-260">Gerektiren bir sınıf üyesinin derlenen sınıfta geçersiz kılınacak.</span><span class="sxs-lookup"><span data-stu-id="a9e82-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="a9e82-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="a9e82-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="a9e82-262">Bir temel sınıftan devralınan üyeyi gizler</span><span class="sxs-lookup"><span data-stu-id="a9e82-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="a9e82-263">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a9e82-263">Interfaces</span></span>

<span data-ttu-id="a9e82-264">Sınıflar gibi arabirimler, özellikleri, yöntemleri ve olayları kümesi tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="a9e82-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="a9e82-265">Ancak, sınıflardan farklı olarak, arabirimler uygulama sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="a9e82-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="a9e82-266">Bunlar sınıfları tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a9e82-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="a9e82-267">Tam olarak tanımlandığı şekilde bir arabirimi uygulayan bir sınıf, o arabirimi her yönüyle uygulamalıdır bir arabirim bir sözleşmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a9e82-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="a9e82-268">Arabirim tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="a9e82-269">Bir sınıf içinde arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="a9e82-270">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a9e82-270">For more information, see:</span></span>

- [<span data-ttu-id="a9e82-271">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a9e82-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [<span data-ttu-id="a9e82-272">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="a9e82-273">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="a9e82-274">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="a9e82-274">Generics</span></span>

<span data-ttu-id="a9e82-275">Sınıflar, yapılar, arabirimler ve yöntemler .NET içerebilir *tür parametrelerindeki* bunlar depolayabildikleri veya kullanabildikleri nesnelerin türlerini tanımlayan.</span><span class="sxs-lookup"><span data-stu-id="a9e82-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="a9e82-276">Genel türlerin yararları en yaygın örnek, bir koleksiyonda depolanacak nesnelerin türünü belirleyebileceğiniz koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="a9e82-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="a9e82-277">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="a9e82-278">Bir genel sınıfın bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="a9e82-279">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a9e82-279">For more information, see:</span></span>

- [<span data-ttu-id="a9e82-280">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="a9e82-280">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="a9e82-281">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="a9e82-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="a9e82-282">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a9e82-282">Delegates</span></span>

 <span data-ttu-id="a9e82-283">A *temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu bir imza ile herhangi bir yönteme başvuru sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="a9e82-284">Çağırma (çağrı yöntemi temsilci aracılığıyla veya).</span><span class="sxs-lookup"><span data-stu-id="a9e82-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="a9e82-285">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9e82-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="a9e82-286">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="a9e82-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="a9e82-287">Temsilcileri olay işlemede kullanma hakkında daha fazla bilgi için bkz. [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="a9e82-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="a9e82-288">Temsilci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="a9e82-289">Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a9e82-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

<span data-ttu-id="a9e82-290">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a9e82-290">For more information, see:</span></span>

- [<span data-ttu-id="a9e82-291">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a9e82-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="a9e82-292">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9e82-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="a9e82-293">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="a9e82-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="a9e82-294">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9e82-294">See also</span></span>

- [<span data-ttu-id="a9e82-295">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a9e82-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
