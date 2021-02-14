---
description: 'Daha fazla bilgi edinin: nesne odaklı programlama (Visual Basic)'
title: Nesne odaklı programlama
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: af2fbac16bfefc90876bf22bb8c67de162ee6459
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486803"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="a253c-103">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a253c-103">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="a253c-104">Visual Basic, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne odaklı programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a253c-104">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="a253c-105">*Kapsülleme* , ilişkili özellikler, Yöntemler ve diğer üyelerin bir grubunun tek bir birim veya nesne olarak kabul edildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a253c-105">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="a253c-106">*Devralma* , mevcut bir sınıfı temel alan yeni sınıflar oluşturma özelliğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a253c-106">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="a253c-107">Çok *biçimlilik* , her bir sınıf farklı yollarla aynı özellikleri veya yöntemleri uyguladığından bile, birbirinin yerine kullanılabilecek birden fazla sınıfa sahip olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a253c-107">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="a253c-108">Bu bölümde aşağıdaki kavramlar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="a253c-108">This section describes the following concepts:</span></span>

- [<span data-ttu-id="a253c-109">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="a253c-109">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="a253c-110">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="a253c-110">Class members</span></span>](#class-members)
    - [<span data-ttu-id="a253c-111">Özellikler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="a253c-111">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="a253c-112">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a253c-112">Methods</span></span>](#methods)
    - [<span data-ttu-id="a253c-113">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a253c-113">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="a253c-114">Yıkıcılar</span><span class="sxs-lookup"><span data-stu-id="a253c-114">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="a253c-115">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="a253c-115">Events</span></span>](#events)
    - [<span data-ttu-id="a253c-116">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="a253c-116">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="a253c-117">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a253c-117">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="a253c-118">Sınıfları örnekleme</span><span class="sxs-lookup"><span data-stu-id="a253c-118">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="a253c-119">Paylaşılan sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="a253c-119">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="a253c-120">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="a253c-120">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="a253c-121">Devralma</span><span class="sxs-lookup"><span data-stu-id="a253c-121">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="a253c-122">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a253c-122">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="a253c-123">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a253c-123">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="a253c-124">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="a253c-124">Generics</span></span>](#generics)
- [<span data-ttu-id="a253c-125">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a253c-125">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="a253c-126">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="a253c-126">Classes and objects</span></span>

<span data-ttu-id="a253c-127">Terimler *sınıfı* ve *nesne* bazen birbirinin yerine kullanılır, ancak aslında nesneler sınıfların kullanılabilir *örnekleri* olduğunda sınıflar nesne *türünü* betimler.</span><span class="sxs-lookup"><span data-stu-id="a253c-127">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="a253c-128">Bu nedenle, bir nesne oluşturma konusuna *örnek* oluşturma denir.</span><span class="sxs-lookup"><span data-stu-id="a253c-128">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="a253c-129">Şema benzerleme vurguladı kullanarak bir sınıf şeması bir şema, bir nesne ise bu şema tarafından oluşturulan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="a253c-129">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="a253c-130">Bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-130">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="a253c-131">Visual Basic Ayrıca, büyük bir nesne dizisi oluşturmanız gerektiğinde ve bunun için çok fazla bellek kullanmak istemediğinizde yararlı olan *yapılar* adlı sınıfların hafif bir sürümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="a253c-131">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="a253c-132">Bir yapı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-132">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="a253c-133">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a253c-133">For more information, see:</span></span>

- [<span data-ttu-id="a253c-134">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="a253c-134">Class Statement</span></span>](../../language-reference/statements/class-statement.md)
- [<span data-ttu-id="a253c-135">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="a253c-135">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="a253c-136">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="a253c-136">Class members</span></span>

<span data-ttu-id="a253c-137">Her sınıf, sınıf verilerini tanımlayan özellikleri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasında iletişim sağlayan olayları içeren farklı *sınıf üyelerine* sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-137">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="a253c-138">Özellikler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="a253c-138">Properties and fields</span></span>

<span data-ttu-id="a253c-139">Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a253c-139">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="a253c-140">Alanlar, okunabilir veya doğrudan ayarlanabileceğinden, değişkenlere benzer.</span><span class="sxs-lookup"><span data-stu-id="a253c-140">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="a253c-141">Bir alan tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-141">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="a253c-142">Özellikler, değerlerin nasıl ayarlandığı veya döndürüldüğü hakkında daha fazla denetim sağlayan alma ve ayarlama yordamlarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a253c-142">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="a253c-143">Visual Basic, özellik değerini depolamak için özel bir alan oluşturmanıza veya bu alanı arka planda otomatik olarak oluşturan ve özellik yordamları için temel mantığı sağlayan, otomatik olarak uygulanan özelliklerin kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a253c-143">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="a253c-144">Otomatik uygulanan bir özellik tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-144">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="a253c-145">Özellik değerini okumak ve yazmak için bazı ek işlemler gerçekleştirmeniz gerekiyorsa, özellik değerini depolamak için bir alan tanımlayın ve bunu depolamak ve almak için temel mantığı sağlayın:</span><span class="sxs-lookup"><span data-stu-id="a253c-145">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="a253c-146">Çoğu özelliğin, özellik değerini ayarlamak ve almak için yöntemleri ya da yordamları vardır.</span><span class="sxs-lookup"><span data-stu-id="a253c-146">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="a253c-147">Ancak, bunları değiştirilmesini veya okumayı kısıtlamak için salt okunurdur veya salt yazılır özellikler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a253c-147">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="a253c-148">Visual Basic, `ReadOnly` ve `WriteOnly` anahtar sözcüklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a253c-148">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="a253c-149">Ancak otomatik olarak uygulanan özellikler salt okunurdur veya salt yazılır olamaz.</span><span class="sxs-lookup"><span data-stu-id="a253c-149">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="a253c-150">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a253c-150">For more information, see:</span></span>

- [<span data-ttu-id="a253c-151">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="a253c-151">Property Statement</span></span>](../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="a253c-152">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="a253c-152">Get Statement</span></span>](../../language-reference/statements/get-statement.md)
- [<span data-ttu-id="a253c-153">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="a253c-153">Set Statement</span></span>](../../language-reference/statements/set-statement.md)
- [<span data-ttu-id="a253c-154">Özelliğinin</span><span class="sxs-lookup"><span data-stu-id="a253c-154">ReadOnly</span></span>](../../language-reference/modifiers/readonly.md)
- [<span data-ttu-id="a253c-155">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="a253c-155">WriteOnly</span></span>](../../language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="a253c-156">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a253c-156">Methods</span></span>

 <span data-ttu-id="a253c-157">Bir *Yöntem* , bir nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="a253c-157">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="a253c-158">Visual Basic, bir yöntem oluşturmanın iki yolu vardır: `Sub` Yöntem bir değer döndürmezse ifade kullanılır; `Function` bir yöntem bir değer döndürürse, ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a253c-158">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="a253c-159">Bir sınıfın yöntemini tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-159">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="a253c-160">Bir sınıf, parametrelerin veya parametre türlerinin sayısında farklı olan aynı yöntemin çeşitli uygulamalarına veya *aşırı* yüküne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-160">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="a253c-161">Bir yöntemi aşırı yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="a253c-161">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="a253c-162">Çoğu durumda, bir sınıf tanımı içinde bir yöntemi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a253c-162">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="a253c-163">Ancak Visual Basic Ayrıca, sınıfının gerçek tanımının dışında mevcut bir sınıfa Yöntemler eklemenize olanak tanıyan *genişletme yöntemlerini* destekler.</span><span class="sxs-lookup"><span data-stu-id="a253c-163">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="a253c-164">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a253c-164">For more information, see:</span></span>

- [<span data-ttu-id="a253c-165">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="a253c-165">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="a253c-166">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="a253c-166">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="a253c-167">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="a253c-167">Overloads</span></span>](../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="a253c-168">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="a253c-168">Extension Methods</span></span>](../language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="a253c-169">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a253c-169">Constructors</span></span>

<span data-ttu-id="a253c-170">Oluşturucular, belirli bir türden bir nesne oluşturulduğunda otomatik olarak yürütülen sınıf yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="a253c-170">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="a253c-171">Oluşturucular genellikle yeni nesnenin veri üyelerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="a253c-171">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="a253c-172">Bir Oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-172">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="a253c-173">Ayrıca, kurucudaki kod her zaman bir sınıftaki diğer koddan önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="a253c-173">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="a253c-174">Ancak, başka bir yöntemle aynı şekilde birden çok Oluşturucu aşırı yüklemesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a253c-174">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="a253c-175">Bir sınıf için bir Oluşturucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-175">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="a253c-176">Daha fazla bilgi için bkz. [nesne ömrü: nesneleri oluşturma ve yok etme](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="a253c-176">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="a253c-177">Yıkıcılar</span><span class="sxs-lookup"><span data-stu-id="a253c-177">Destructors</span></span>

<span data-ttu-id="a253c-178">Yok ediciler sınıfların örneklerini deketmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a253c-178">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="a253c-179">.NET Framework, çöp toplayıcı uygulamanızdaki yönetilen nesneler için bellek ayırmayı ve serbest bırakma işlemini otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="a253c-179">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="a253c-180">Ancak, uygulamanızın oluşturduğu yönetilmeyen kaynakları temizlemek için yine de yıkıcı gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-180">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="a253c-181">Bir sınıf için yalnızca bir yıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-181">There can be only one destructor for a class.</span></span>

<span data-ttu-id="a253c-182">.NET Framework Yıkıcılar ve çöp toplama hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="a253c-182">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="a253c-183">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="a253c-183">Events</span></span>

<span data-ttu-id="a253c-184">Olaylar, bir sınıf ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a253c-184">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="a253c-185">Olayı gönderen (veya Başlatan) sınıf *Yayımcı* olarak adlandırılır ve olayı alan (veya işleyen) sınıflar *aboneler* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a253c-185">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="a253c-186">Olaylar, nasıl oluşturulur ve işlenir hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="a253c-186">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="a253c-187">Olayları bildirmek için [Event ifadesini](../../language-reference/statements/event-statement.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="a253c-187">To declare events, use the [Event Statement](../../language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="a253c-188">Olay yükseltmek için [RaiseEvent ifadesini](../../language-reference/statements/raiseevent-statement.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="a253c-188">To raise events, use the [RaiseEvent Statement](../../language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="a253c-189">Bildirim temelli bir yöntem kullanarak olay işleyicileri belirtmek için [WithEvents](../../language-reference/modifiers/withevents.md) deyimi ve [Handles](../../language-reference/statements/handles-clause.md) yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a253c-189">To specify event handlers using a declarative way, use the [WithEvents](../../language-reference/modifiers/withevents.md) statement and the [Handles](../../language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="a253c-190">Bir olayla ilişkili olay işleyicisini dinamik olarak eklemek, kaldırmak ve değiştirmek için, [AddressOf işleci](../../language-reference/operators/addressof-operator.md)Ile birlikte [AddHandler](../../language-reference/statements/addhandler-statement.md) ifadesini ve [RemoveHandler ifadesini](../../language-reference/statements/removehandler-statement.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a253c-190">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="a253c-191">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="a253c-191">Nested classes</span></span>

<span data-ttu-id="a253c-192">Başka bir sınıf içinde tanımlı bir sınıf *iç içe* çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a253c-192">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="a253c-193">Varsayılan olarak, iç içe yerleştirilmiş sınıf özeldir.</span><span class="sxs-lookup"><span data-stu-id="a253c-193">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="a253c-194">İç içe yerleştirilmiş sınıfın bir örneğini oluşturmak için, container sınıfının adını ve ardından nokta ve ardından iç içe geçmiş sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="a253c-194">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="a253c-195">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a253c-195">Access modifiers and access levels</span></span>

<span data-ttu-id="a253c-196">Tüm sınıflar ve sınıf üyeleri, *erişim değiştiricilerini* kullanarak diğer sınıflara hangi erişim düzeyini sundukları belirler.</span><span class="sxs-lookup"><span data-stu-id="a253c-196">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="a253c-197">Aşağıdaki erişim değiştiriciler kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a253c-197">The following access modifiers are available:</span></span>

|<span data-ttu-id="a253c-198">Visual Basic değiştirici</span><span class="sxs-lookup"><span data-stu-id="a253c-198">Visual Basic Modifier</span></span>|<span data-ttu-id="a253c-199">Tanım</span><span class="sxs-lookup"><span data-stu-id="a253c-199">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="a253c-200">Genel</span><span class="sxs-lookup"><span data-stu-id="a253c-200">Public</span></span>](../../language-reference/modifiers/public.md)|<span data-ttu-id="a253c-201">Türe veya üyeye aynı derlemedeki veya buna başvuran başka bir derlemede bir veya daha fazla kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-201">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="a253c-202">Özel</span><span class="sxs-lookup"><span data-stu-id="a253c-202">Private</span></span>](../../language-reference/modifiers/private.md)|<span data-ttu-id="a253c-203">Türe veya üyeye yalnızca aynı sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-203">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="a253c-204">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="a253c-204">Protected</span></span>](../../language-reference/modifiers/protected.md)|<span data-ttu-id="a253c-205">Türe veya üyeye yalnızca aynı sınıftaki veya türetilmiş bir sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-205">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="a253c-206">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="a253c-206">Friend</span></span>](../../language-reference/modifiers/friend.md)|<span data-ttu-id="a253c-207">Türe veya üyeye aynı derlemedeki kod tarafından erişilebilir, ancak başka bir derlemeden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-207">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="a253c-208">Türe veya üyeye aynı derlemedeki herhangi bir kod ya da başka bir derlemedeki türetilmiş bir sınıf tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-208">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="a253c-209">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a253c-209">For more information, see [Access levels in Visual Basic](../language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="a253c-210">Sınıfları örnekleme</span><span class="sxs-lookup"><span data-stu-id="a253c-210">Instantiating classes</span></span>

<span data-ttu-id="a253c-211">Bir nesne oluşturmak için bir sınıf örneği oluşturmanız veya bir sınıf örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a253c-211">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="a253c-212">Bir sınıfı örnekledikten sonra, örneğin özelliklerine ve alanlarına değerler atayabilir ve sınıf yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a253c-212">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="a253c-213">Sınıf örnek oluşturma işlemi sırasında özelliklere değer atamak için, nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="a253c-213">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="a253c-214">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a253c-214">For more information, see:</span></span>

- [<span data-ttu-id="a253c-215">New Işleci</span><span class="sxs-lookup"><span data-stu-id="a253c-215">New Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="a253c-216">Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="a253c-216">Object Initializers: Named and Anonymous Types</span></span>](../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="a253c-217">Paylaşılan sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="a253c-217">Shared classes and members</span></span>

 <span data-ttu-id="a253c-218">Sınıfın paylaşılan bir üyesi bir sınıfın tüm örnekleri tarafından paylaşılan bir özellik, yordam veya alandır.</span><span class="sxs-lookup"><span data-stu-id="a253c-218">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="a253c-219">Paylaşılan bir üye tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-219">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="a253c-220">Paylaşılan üyeye erişmek için sınıfın adını bu sınıfın bir nesnesi oluşturmadan kullanın:</span><span class="sxs-lookup"><span data-stu-id="a253c-220">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="a253c-221">Visual Basic paylaşılan modüller yalnızca paylaşılan üyelere sahiptir ve örneklenemez.</span><span class="sxs-lookup"><span data-stu-id="a253c-221">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="a253c-222">Paylaşılan Üyeler ayrıca paylaşılmayan özelliklere, alanlara veya yöntemlere erişemez</span><span class="sxs-lookup"><span data-stu-id="a253c-222">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="a253c-223">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a253c-223">For more information, see:</span></span>

- [<span data-ttu-id="a253c-224">Paylaşılan</span><span class="sxs-lookup"><span data-stu-id="a253c-224">Shared</span></span>](../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="a253c-225">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="a253c-225">Module Statement</span></span>](../../language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="a253c-226">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="a253c-226">Anonymous types</span></span>

<span data-ttu-id="a253c-227">Anonim türler, veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a253c-227">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="a253c-228">Bunun yerine, derleyici sizin için bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a253c-228">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="a253c-229">Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a253c-229">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="a253c-230">Anonim türün bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-230">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="a253c-231">Daha fazla bilgi için bkz: [anonim türler](../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a253c-231">For more information, see: [Anonymous Types](../language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="a253c-232">Devralma</span><span class="sxs-lookup"><span data-stu-id="a253c-232">Inheritance</span></span>

<span data-ttu-id="a253c-233">Devralma, başka bir sınıfta tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni bir sınıf oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a253c-233">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="a253c-234">Üyeleri devralınmış olan sınıfa *temel sınıf* denir ve bu üyeleri devralan sınıfa *türetilmiş sınıf* denir.</span><span class="sxs-lookup"><span data-stu-id="a253c-234">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="a253c-235">Ancak Visual Basic içindeki tüm sınıflar, <xref:System.Object> .NET sınıf hiyerarşisini destekleyen sınıftan dolaylı olarak devralınır ve tüm sınıflara alt düzey hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a253c-235">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="a253c-236">Visual Basic birden çok devralmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a253c-236">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="a253c-237">Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a253c-237">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="a253c-238">Temel sınıftan devralması için:</span><span class="sxs-lookup"><span data-stu-id="a253c-238">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="a253c-239">Varsayılan olarak, tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-239">By default all classes can be inherited.</span></span> <span data-ttu-id="a253c-240">Ancak, bir sınıfın temel sınıf olarak kullanılması gerekip gerekmediğini belirtebilir veya yalnızca temel sınıf olarak kullanılabilecek bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a253c-240">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="a253c-241">Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="a253c-241">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="a253c-242">Bir sınıfın yalnızca temel sınıf olarak kullanılabileceğini ve örneklenemez olduğunu belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="a253c-242">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="a253c-243">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a253c-243">For more information, see:</span></span>

- [<span data-ttu-id="a253c-244">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="a253c-244">Inherits Statement</span></span>](../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="a253c-245">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="a253c-245">NotInheritable</span></span>](../../language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="a253c-246">MustInherit</span><span class="sxs-lookup"><span data-stu-id="a253c-246">MustInherit</span></span>](../../language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="a253c-247">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a253c-247">Overriding members</span></span>

<span data-ttu-id="a253c-248">Varsayılan olarak, türetilmiş bir sınıf kendi temel sınıfından tüm üyeleri devralır.</span><span class="sxs-lookup"><span data-stu-id="a253c-248">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="a253c-249">Devralınan üyenin davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a253c-249">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="a253c-250">Diğer bir deyişle, türetilmiş sınıfta yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a253c-250">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="a253c-251">Özelliklerin ve yöntemlerin nasıl geçersiz kılınabileceğini denetlemek için aşağıdaki değiştiriciler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="a253c-251">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="a253c-252">Visual Basic değiştirici</span><span class="sxs-lookup"><span data-stu-id="a253c-252">Visual Basic Modifier</span></span>|<span data-ttu-id="a253c-253">Tanım</span><span class="sxs-lookup"><span data-stu-id="a253c-253">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="a253c-254">Overridable</span><span class="sxs-lookup"><span data-stu-id="a253c-254">Overridable</span></span>](../../language-reference/modifiers/overridable.md)|<span data-ttu-id="a253c-255">Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a253c-255">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="a253c-256">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="a253c-256">Overrides</span></span>](../../language-reference/modifiers/overrides.md)|<span data-ttu-id="a253c-257">Temel sınıfta tanımlanan bir sanal (geçersiz kılınabilir) üyeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a253c-257">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="a253c-258">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="a253c-258">NotOverridable</span></span>](../../language-reference/modifiers/notoverridable.md)|<span data-ttu-id="a253c-259">Devralan bir sınıfta üyenin geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="a253c-259">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="a253c-260">MustOverride</span><span class="sxs-lookup"><span data-stu-id="a253c-260">MustOverride</span></span>](../../language-reference/modifiers/mustoverride.md)|<span data-ttu-id="a253c-261">Türetilmiş sınıfta bir sınıf üyesinin geçersiz kılınmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a253c-261">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="a253c-262">Shadows</span><span class="sxs-lookup"><span data-stu-id="a253c-262">Shadows</span></span>](../../language-reference/modifiers/shadows.md)|<span data-ttu-id="a253c-263">Temel sınıftan devralınan bir üyeyi gizler</span><span class="sxs-lookup"><span data-stu-id="a253c-263">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="a253c-264">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a253c-264">Interfaces</span></span>

<span data-ttu-id="a253c-265">Sınıflar gibi arabirimler, özellikler, Yöntemler ve olaylar kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a253c-265">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="a253c-266">Ancak sınıfların aksine arabirimler uygulama sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="a253c-266">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="a253c-267">Sınıflar tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a253c-267">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="a253c-268">Arabirim, bir arabirimi uygulayan bir sınıfın, bu arabirimin her yönünü tam olarak tanımlandığı gibi uygulaması gerektiğini belirten bir sözleşmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a253c-268">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="a253c-269">Bir arabirim tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-269">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="a253c-270">Bir sınıfa bir arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-270">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="a253c-271">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a253c-271">For more information, see:</span></span>

- [<span data-ttu-id="a253c-272">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a253c-272">Interfaces</span></span>](../language-features/interfaces/index.md)
- [<span data-ttu-id="a253c-273">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="a253c-273">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="a253c-274">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="a253c-274">Implements Statement</span></span>](../../language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="a253c-275">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="a253c-275">Generics</span></span>

<span data-ttu-id="a253c-276">.NET 'teki sınıflar, yapılar, arabirimler ve Yöntemler, depolayabilecekleri veya kullanabileceği nesne türlerini tanımlayan *tür parametreleri* içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-276">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="a253c-277">En yaygın genel türler örneği, bir koleksiyonda depolanacak nesne türlerini belirtebileceğiniz bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="a253c-277">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="a253c-278">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-278">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="a253c-279">Genel sınıfın bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-279">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="a253c-280">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a253c-280">For more information, see:</span></span>

- [<span data-ttu-id="a253c-281">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="a253c-281">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="a253c-282">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="a253c-282">Generic Types in Visual Basic</span></span>](../language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="a253c-283">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a253c-283">Delegates</span></span>

 <span data-ttu-id="a253c-284">*Temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu imzaya sahip herhangi bir yönteme başvuru sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a253c-284">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="a253c-285">Yöntemi temsilci aracılığıyla çağırabilir (veya çağırabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="a253c-285">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="a253c-286">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a253c-286">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="a253c-287">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="a253c-287">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="a253c-288">Olay İşlemede temsilciler kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="a253c-288">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="a253c-289">Bir temsilci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-289">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="a253c-290">Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a253c-290">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="a253c-291">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a253c-291">For more information, see:</span></span>

- [<span data-ttu-id="a253c-292">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a253c-292">Delegates</span></span>](../language-features/delegates/index.md)
- [<span data-ttu-id="a253c-293">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="a253c-293">Delegate Statement</span></span>](../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="a253c-294">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="a253c-294">AddressOf Operator</span></span>](../../language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="a253c-295">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a253c-295">See also</span></span>

- [<span data-ttu-id="a253c-296">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a253c-296">Visual Basic Programming Guide</span></span>](../index.md)
