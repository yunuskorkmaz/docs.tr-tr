---
title: Nesne odaklı programlama
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: f7e222cde8ce80d4c52cc8b4b111c576eb4041b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413199"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="f16ff-102">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f16ff-102">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="f16ff-103">Visual Basic, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne odaklı programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f16ff-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="f16ff-104">*Kapsülleme* , ilişkili özellikler, Yöntemler ve diğer üyelerin bir grubunun tek bir birim veya nesne olarak kabul edildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="f16ff-105">*Devralma* , mevcut bir sınıfı temel alan yeni sınıflar oluşturma özelliğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f16ff-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="f16ff-106">Çok *biçimlilik* , her bir sınıf farklı yollarla aynı özellikleri veya yöntemleri uyguladığından bile, birbirinin yerine kullanılabilecek birden fazla sınıfa sahip olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="f16ff-107">Bu bölümde aşağıdaki kavramlar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f16ff-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="f16ff-108">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="f16ff-108">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="f16ff-109">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="f16ff-109">Class members</span></span>](#class-members)
    - [<span data-ttu-id="f16ff-110">Özellikler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="f16ff-110">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="f16ff-111">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f16ff-111">Methods</span></span>](#methods)
    - [<span data-ttu-id="f16ff-112">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="f16ff-112">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="f16ff-113">Yıkıcılar</span><span class="sxs-lookup"><span data-stu-id="f16ff-113">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="f16ff-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="f16ff-114">Events</span></span>](#events)
    - [<span data-ttu-id="f16ff-115">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="f16ff-115">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="f16ff-116">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="f16ff-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="f16ff-117">Sınıfları örnekleme</span><span class="sxs-lookup"><span data-stu-id="f16ff-117">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="f16ff-118">Paylaşılan sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="f16ff-118">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="f16ff-119">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="f16ff-119">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="f16ff-120">Devralma</span><span class="sxs-lookup"><span data-stu-id="f16ff-120">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="f16ff-121">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="f16ff-121">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="f16ff-122">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="f16ff-122">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="f16ff-123">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="f16ff-123">Generics</span></span>](#generics)
- [<span data-ttu-id="f16ff-124">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f16ff-124">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="f16ff-125">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="f16ff-125">Classes and objects</span></span>

<span data-ttu-id="f16ff-126">Terimler *sınıfı* ve *nesne* bazen birbirinin yerine kullanılır, ancak aslında nesneler sınıfların kullanılabilir *örnekleri* olduğunda sınıflar nesne *türünü* betimler.</span><span class="sxs-lookup"><span data-stu-id="f16ff-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="f16ff-127">Bu nedenle, bir nesne oluşturma konusuna *örnek*oluşturma denir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="f16ff-128">Şema benzerleme vurguladı kullanarak bir sınıf şeması bir şema, bir nesne ise bu şema tarafından oluşturulan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="f16ff-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="f16ff-129">Bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-129">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="f16ff-130">Visual Basic Ayrıca, büyük bir nesne dizisi oluşturmanız gerektiğinde ve bunun için çok fazla bellek kullanmak istemediğinizde yararlı olan *yapılar* adlı sınıfların hafif bir sürümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="f16ff-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="f16ff-131">Bir yapı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-131">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="f16ff-132">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-132">For more information, see:</span></span>

- [<span data-ttu-id="f16ff-133">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="f16ff-133">Class Statement</span></span>](../../language-reference/statements/class-statement.md)
- [<span data-ttu-id="f16ff-134">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="f16ff-134">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="f16ff-135">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="f16ff-135">Class members</span></span>

<span data-ttu-id="f16ff-136">Her sınıf, sınıf verilerini tanımlayan özellikleri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasında iletişim sağlayan olayları içeren farklı *sınıf üyelerine* sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="f16ff-137">Özellikler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="f16ff-137">Properties and fields</span></span>

<span data-ttu-id="f16ff-138">Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f16ff-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="f16ff-139">Alanlar, okunabilir veya doğrudan ayarlanabileceğinden, değişkenlere benzer.</span><span class="sxs-lookup"><span data-stu-id="f16ff-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="f16ff-140">Bir alan tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="f16ff-141">Özellikler, değerlerin nasıl ayarlandığı veya döndürüldüğü hakkında daha fazla denetim sağlayan alma ve ayarlama yordamlarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="f16ff-142">Visual Basic, özellik değerini depolamak için özel bir alan oluşturmanıza veya bu alanı arka planda otomatik olarak oluşturan ve özellik yordamları için temel mantığı sağlayan, otomatik olarak uygulanan özelliklerin kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="f16ff-143">Otomatik uygulanan bir özellik tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="f16ff-144">Özellik değerini okumak ve yazmak için bazı ek işlemler gerçekleştirmeniz gerekiyorsa, özellik değerini depolamak için bir alan tanımlayın ve bunu depolamak ve almak için temel mantığı sağlayın:</span><span class="sxs-lookup"><span data-stu-id="f16ff-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="f16ff-145">Çoğu özelliğin, özellik değerini ayarlamak ve almak için yöntemleri ya da yordamları vardır.</span><span class="sxs-lookup"><span data-stu-id="f16ff-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="f16ff-146">Ancak, bunları değiştirilmesini veya okumayı kısıtlamak için salt okunurdur veya salt yazılır özellikler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="f16ff-147">Visual Basic, `ReadOnly` ve `WriteOnly` anahtar sözcüklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="f16ff-148">Ancak otomatik olarak uygulanan özellikler salt okunurdur veya salt yazılır olamaz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="f16ff-149">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-149">For more information, see:</span></span>

- [<span data-ttu-id="f16ff-150">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="f16ff-150">Property Statement</span></span>](../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="f16ff-151">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="f16ff-151">Get Statement</span></span>](../../language-reference/statements/get-statement.md)
- [<span data-ttu-id="f16ff-152">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="f16ff-152">Set Statement</span></span>](../../language-reference/statements/set-statement.md)
- [<span data-ttu-id="f16ff-153">Özelliğinin</span><span class="sxs-lookup"><span data-stu-id="f16ff-153">ReadOnly</span></span>](../../language-reference/modifiers/readonly.md)
- [<span data-ttu-id="f16ff-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="f16ff-154">WriteOnly</span></span>](../../language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="f16ff-155">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f16ff-155">Methods</span></span>

 <span data-ttu-id="f16ff-156">Bir *Yöntem* , bir nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-156">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="f16ff-157">Visual Basic, bir yöntem oluşturmanın iki yolu vardır: `Sub` Yöntem bir değer döndürmezse ifade kullanılır; `Function` bir yöntem bir değer döndürürse, ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f16ff-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="f16ff-158">Bir sınıfın yöntemini tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="f16ff-159">Bir sınıf, parametrelerin veya parametre türlerinin sayısında farklı olan aynı yöntemin çeşitli uygulamalarına veya *aşırı*yüküne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="f16ff-160">Bir yöntemi aşırı yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="f16ff-161">Çoğu durumda, bir sınıf tanımı içinde bir yöntemi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="f16ff-162">Ancak Visual Basic Ayrıca, sınıfının gerçek tanımının dışında mevcut bir sınıfa Yöntemler eklemenize olanak tanıyan *genişletme yöntemlerini* destekler.</span><span class="sxs-lookup"><span data-stu-id="f16ff-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="f16ff-163">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-163">For more information, see:</span></span>

- [<span data-ttu-id="f16ff-164">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="f16ff-164">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="f16ff-165">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="f16ff-165">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="f16ff-166">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="f16ff-166">Overloads</span></span>](../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="f16ff-167">Uzantı yöntemleri</span><span class="sxs-lookup"><span data-stu-id="f16ff-167">Extension Methods</span></span>](../language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="f16ff-168">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="f16ff-168">Constructors</span></span>

<span data-ttu-id="f16ff-169">Oluşturucular, belirli bir türden bir nesne oluşturulduğunda otomatik olarak yürütülen sınıf yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="f16ff-170">Oluşturucular genellikle yeni nesnenin veri üyelerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="f16ff-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="f16ff-171">Bir Oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="f16ff-172">Ayrıca, kurucudaki kod her zaman bir sınıftaki diğer koddan önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="f16ff-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="f16ff-173">Ancak, başka bir yöntemle aynı şekilde birden çok Oluşturucu aşırı yüklemesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="f16ff-174">Bir sınıf için bir Oluşturucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="f16ff-175">Daha fazla bilgi için bkz. [nesne ömrü: nesneleri oluşturma ve yok etme](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="f16ff-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="f16ff-176">Yıkıcılar</span><span class="sxs-lookup"><span data-stu-id="f16ff-176">Destructors</span></span>

<span data-ttu-id="f16ff-177">Yok ediciler sınıfların örneklerini deketmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f16ff-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="f16ff-178">.NET Framework, çöp toplayıcı uygulamanızdaki yönetilen nesneler için bellek ayırmayı ve serbest bırakma işlemini otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="f16ff-179">Ancak, uygulamanızın oluşturduğu yönetilmeyen kaynakları temizlemek için yine de yıkıcı gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="f16ff-180">Bir sınıf için yalnızca bir yıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="f16ff-181">.NET Framework Yıkıcılar ve çöp toplama hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="f16ff-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="f16ff-182">Olaylar</span><span class="sxs-lookup"><span data-stu-id="f16ff-182">Events</span></span>

<span data-ttu-id="f16ff-183">Olaylar, bir sınıf ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f16ff-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="f16ff-184">Olayı gönderen (veya Başlatan) sınıf *Yayımcı* olarak adlandırılır ve olayı alan (veya işleyen) sınıflar *aboneler*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f16ff-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="f16ff-185">Olaylar, nasıl oluşturulur ve işlenir hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="f16ff-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="f16ff-186">Olayları bildirmek için [Event ifadesini](../../language-reference/statements/event-statement.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="f16ff-186">To declare events, use the [Event Statement](../../language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="f16ff-187">Olay yükseltmek için [RaiseEvent ifadesini](../../language-reference/statements/raiseevent-statement.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="f16ff-187">To raise events, use the [RaiseEvent Statement](../../language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="f16ff-188">Bildirim temelli bir yöntem kullanarak olay işleyicileri belirtmek için [WithEvents](../../language-reference/modifiers/withevents.md) deyimi ve [Handles](../../language-reference/statements/handles-clause.md) yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f16ff-188">To specify event handlers using a declarative way, use the [WithEvents](../../language-reference/modifiers/withevents.md) statement and the [Handles](../../language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="f16ff-189">Bir olayla ilişkili olay işleyicisini dinamik olarak eklemek, kaldırmak ve değiştirmek için, [AddressOf işleci](../../language-reference/operators/addressof-operator.md)Ile birlikte [AddHandler](../../language-reference/statements/addhandler-statement.md) ifadesini ve [RemoveHandler ifadesini](../../language-reference/statements/removehandler-statement.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f16ff-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="f16ff-190">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="f16ff-190">Nested classes</span></span>

<span data-ttu-id="f16ff-191">Başka bir sınıf içinde tanımlı bir sınıf *iç içe*çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f16ff-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="f16ff-192">Varsayılan olarak, iç içe yerleştirilmiş sınıf özeldir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="f16ff-193">İç içe yerleştirilmiş sınıfın bir örneğini oluşturmak için, container sınıfının adını ve ardından nokta ve ardından iç içe geçmiş sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="f16ff-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="f16ff-194">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="f16ff-194">Access modifiers and access levels</span></span>

<span data-ttu-id="f16ff-195">Tüm sınıflar ve sınıf üyeleri, *erişim değiştiricilerini*kullanarak diğer sınıflara hangi erişim düzeyini sundukları belirler.</span><span class="sxs-lookup"><span data-stu-id="f16ff-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="f16ff-196">Aşağıdaki erişim değiştiriciler kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f16ff-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="f16ff-197">Visual Basic değiştirici</span><span class="sxs-lookup"><span data-stu-id="f16ff-197">Visual Basic Modifier</span></span>|<span data-ttu-id="f16ff-198">Tanım</span><span class="sxs-lookup"><span data-stu-id="f16ff-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="f16ff-199">Geneldir</span><span class="sxs-lookup"><span data-stu-id="f16ff-199">Public</span></span>](../../language-reference/modifiers/public.md)|<span data-ttu-id="f16ff-200">Türe veya üyeye aynı derlemedeki veya buna başvuran başka bir derlemede bir veya daha fazla kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="f16ff-201">Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f16ff-201">Private</span></span>](../../language-reference/modifiers/private.md)|<span data-ttu-id="f16ff-202">Türe veya üyeye yalnızca aynı sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="f16ff-203">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="f16ff-203">Protected</span></span>](../../language-reference/modifiers/protected.md)|<span data-ttu-id="f16ff-204">Türe veya üyeye yalnızca aynı sınıftaki veya türetilmiş bir sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="f16ff-205">Dost</span><span class="sxs-lookup"><span data-stu-id="f16ff-205">Friend</span></span>](../../language-reference/modifiers/friend.md)|<span data-ttu-id="f16ff-206">Türe veya üyeye aynı derlemedeki kod tarafından erişilebilir, ancak başka bir derlemeden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="f16ff-207">Türe veya üyeye aynı derlemedeki herhangi bir kod ya da başka bir derlemedeki türetilmiş bir sınıf tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="f16ff-208">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f16ff-208">For more information, see [Access levels in Visual Basic](../language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="f16ff-209">Sınıfları örnekleme</span><span class="sxs-lookup"><span data-stu-id="f16ff-209">Instantiating classes</span></span>

<span data-ttu-id="f16ff-210">Bir nesne oluşturmak için bir sınıf örneği oluşturmanız veya bir sınıf örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="f16ff-211">Bir sınıfı örnekledikten sonra, örneğin özelliklerine ve alanlarına değerler atayabilir ve sınıf yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="f16ff-212">Sınıf örnek oluşturma işlemi sırasında özelliklere değer atamak için, nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="f16ff-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="f16ff-213">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-213">For more information, see:</span></span>

- [<span data-ttu-id="f16ff-214">New Işleci</span><span class="sxs-lookup"><span data-stu-id="f16ff-214">New Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="f16ff-215">Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="f16ff-215">Object Initializers: Named and Anonymous Types</span></span>](../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="f16ff-216">Paylaşılan sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="f16ff-216">Shared classes and members</span></span>

 <span data-ttu-id="f16ff-217">Sınıfın paylaşılan bir üyesi bir sınıfın tüm örnekleri tarafından paylaşılan bir özellik, yordam veya alandır.</span><span class="sxs-lookup"><span data-stu-id="f16ff-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="f16ff-218">Paylaşılan bir üye tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-218">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="f16ff-219">Paylaşılan üyeye erişmek için sınıfın adını bu sınıfın bir nesnesi oluşturmadan kullanın:</span><span class="sxs-lookup"><span data-stu-id="f16ff-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="f16ff-220">Visual Basic paylaşılan modüller yalnızca paylaşılan üyelere sahiptir ve örneklenemez.</span><span class="sxs-lookup"><span data-stu-id="f16ff-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="f16ff-221">Paylaşılan Üyeler ayrıca paylaşılmayan özelliklere, alanlara veya yöntemlere erişemez</span><span class="sxs-lookup"><span data-stu-id="f16ff-221">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="f16ff-222">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-222">For more information, see:</span></span>

- [<span data-ttu-id="f16ff-223">Shared</span><span class="sxs-lookup"><span data-stu-id="f16ff-223">Shared</span></span>](../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="f16ff-224">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="f16ff-224">Module Statement</span></span>](../../language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="f16ff-225">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="f16ff-225">Anonymous types</span></span>

<span data-ttu-id="f16ff-226">Anonim türler, veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f16ff-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="f16ff-227">Bunun yerine, derleyici sizin için bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f16ff-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="f16ff-228">Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="f16ff-229">Anonim türün bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="f16ff-230">Daha fazla bilgi için bkz: [anonim türler](../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f16ff-230">For more information, see: [Anonymous Types](../language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="f16ff-231">Devralma</span><span class="sxs-lookup"><span data-stu-id="f16ff-231">Inheritance</span></span>

<span data-ttu-id="f16ff-232">Devralma, başka bir sınıfta tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni bir sınıf oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f16ff-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="f16ff-233">Üyeleri devralınmış olan sınıfa *temel sınıf*denir ve bu üyeleri devralan sınıfa *türetilmiş sınıf*denir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="f16ff-234">Ancak Visual Basic içindeki tüm sınıflar, <xref:System.Object> .NET sınıf hiyerarşisini destekleyen sınıftan dolaylı olarak devralınır ve tüm sınıflara alt düzey hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f16ff-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="f16ff-235">Visual Basic birden çok devralmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f16ff-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="f16ff-236">Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="f16ff-237">Temel sınıftan devralması için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="f16ff-238">Varsayılan olarak, tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-238">By default all classes can be inherited.</span></span> <span data-ttu-id="f16ff-239">Ancak, bir sınıfın temel sınıf olarak kullanılması gerekip gerekmediğini belirtebilir veya yalnızca temel sınıf olarak kullanılabilecek bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="f16ff-240">Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="f16ff-241">Bir sınıfın yalnızca temel sınıf olarak kullanılabileceğini ve örneklenemez olduğunu belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="f16ff-242">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-242">For more information, see:</span></span>

- [<span data-ttu-id="f16ff-243">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="f16ff-243">Inherits Statement</span></span>](../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="f16ff-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="f16ff-244">NotInheritable</span></span>](../../language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="f16ff-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="f16ff-245">MustInherit</span></span>](../../language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="f16ff-246">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="f16ff-246">Overriding members</span></span>

<span data-ttu-id="f16ff-247">Varsayılan olarak, türetilmiş bir sınıf kendi temel sınıfından tüm üyeleri devralır.</span><span class="sxs-lookup"><span data-stu-id="f16ff-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="f16ff-248">Devralınan üyenin davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="f16ff-249">Diğer bir deyişle, türetilmiş sınıfta yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="f16ff-250">Özelliklerin ve yöntemlerin nasıl geçersiz kılınabileceğini denetlemek için aşağıdaki değiştiriciler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="f16ff-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="f16ff-251">Visual Basic değiştirici</span><span class="sxs-lookup"><span data-stu-id="f16ff-251">Visual Basic Modifier</span></span>|<span data-ttu-id="f16ff-252">Tanım</span><span class="sxs-lookup"><span data-stu-id="f16ff-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="f16ff-253">Overridable</span><span class="sxs-lookup"><span data-stu-id="f16ff-253">Overridable</span></span>](../../language-reference/modifiers/overridable.md)|<span data-ttu-id="f16ff-254">Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="f16ff-255">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="f16ff-255">Overrides</span></span>](../../language-reference/modifiers/overrides.md)|<span data-ttu-id="f16ff-256">Temel sınıfta tanımlanan bir sanal (geçersiz kılınabilir) üyeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f16ff-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="f16ff-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="f16ff-257">NotOverridable</span></span>](../../language-reference/modifiers/notoverridable.md)|<span data-ttu-id="f16ff-258">Devralan bir sınıfta üyenin geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="f16ff-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="f16ff-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="f16ff-259">MustOverride</span></span>](../../language-reference/modifiers/mustoverride.md)|<span data-ttu-id="f16ff-260">Türetilmiş sınıfta bir sınıf üyesinin geçersiz kılınmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="f16ff-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="f16ff-261">Shadows</span></span>](../../language-reference/modifiers/shadows.md)|<span data-ttu-id="f16ff-262">Temel sınıftan devralınan bir üyeyi gizler</span><span class="sxs-lookup"><span data-stu-id="f16ff-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="f16ff-263">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="f16ff-263">Interfaces</span></span>

<span data-ttu-id="f16ff-264">Sınıflar gibi arabirimler, özellikler, Yöntemler ve olaylar kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f16ff-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="f16ff-265">Ancak sınıfların aksine arabirimler uygulama sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="f16ff-266">Sınıflar tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f16ff-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="f16ff-267">Arabirim, bir arabirimi uygulayan bir sınıfın, bu arabirimin her yönünü tam olarak tanımlandığı gibi uygulaması gerektiğini belirten bir sözleşmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f16ff-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="f16ff-268">Bir arabirim tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="f16ff-269">Bir sınıfa bir arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="f16ff-270">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-270">For more information, see:</span></span>

- [<span data-ttu-id="f16ff-271">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="f16ff-271">Interfaces</span></span>](../language-features/interfaces/index.md)
- [<span data-ttu-id="f16ff-272">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="f16ff-272">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="f16ff-273">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="f16ff-273">Implements Statement</span></span>](../../language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="f16ff-274">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="f16ff-274">Generics</span></span>

<span data-ttu-id="f16ff-275">.NET 'teki sınıflar, yapılar, arabirimler ve Yöntemler, depolayabilecekleri veya kullanabileceği nesne türlerini tanımlayan *tür parametreleri* içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="f16ff-276">En yaygın genel türler örneği, bir koleksiyonda depolanacak nesne türlerini belirtebileceğiniz bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="f16ff-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="f16ff-277">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="f16ff-278">Genel sınıfın bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="f16ff-279">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-279">For more information, see:</span></span>

- [<span data-ttu-id="f16ff-280">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="f16ff-280">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="f16ff-281">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="f16ff-281">Generic Types in Visual Basic</span></span>](../language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="f16ff-282">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f16ff-282">Delegates</span></span>

 <span data-ttu-id="f16ff-283">*Temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu imzaya sahip herhangi bir yönteme başvuru sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="f16ff-284">Yöntemi temsilci aracılığıyla çağırabilir (veya çağırabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="f16ff-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="f16ff-285">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f16ff-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="f16ff-286">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="f16ff-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="f16ff-287">Olay İşlemede temsilciler kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="f16ff-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="f16ff-288">Bir temsilci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="f16ff-289">Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="f16ff-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="f16ff-290">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-290">For more information, see:</span></span>

- [<span data-ttu-id="f16ff-291">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f16ff-291">Delegates</span></span>](../language-features/delegates/index.md)
- [<span data-ttu-id="f16ff-292">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="f16ff-292">Delegate Statement</span></span>](../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="f16ff-293">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="f16ff-293">AddressOf Operator</span></span>](../../language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="f16ff-294">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f16ff-294">See also</span></span>

- [<span data-ttu-id="f16ff-295">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f16ff-295">Visual Basic Programming Guide</span></span>](../index.md)
