---
title: Nesne odaklı programlama (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: a7a3ce1b33d040b337087dfede90b58906c95cbd
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481177"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="e6160-102">Nesne odaklı programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="e6160-102">Object-Oriented Programming (C#)</span></span>

<span data-ttu-id="e6160-103">C#, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne yönelimli programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6160-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

<span data-ttu-id="e6160-104">*Kapsülleme* ilgili özellikleri, yöntemleri ve diğer üyeleri bir grup işlem tek bir birim veya nesne anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e6160-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

<span data-ttu-id="e6160-105">*Devralma* mevcut bir sınıfı temel alan yeni sınıflar oluşturma becerisidir.</span><span class="sxs-lookup"><span data-stu-id="e6160-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

<span data-ttu-id="e6160-106">*Çok biçimlilik* her sınıf aynı özellikleri veya yöntemleri farklı şekilde uygular olsa da birbirinin yerine kullanılabilen birden fazla sınıfınız olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e6160-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

<span data-ttu-id="e6160-107">Bu bölüm aşağıdaki kavramları açıklar:</span><span class="sxs-lookup"><span data-stu-id="e6160-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="e6160-108">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="e6160-108">Classes and Objects</span></span>](#Classes)

  - [<span data-ttu-id="e6160-109">Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="e6160-109">Class Members</span></span>](#Members)

        [Properties and Fields](#Properties)

        [Methods](#Methods)

        [Constructors](#Constructors)

        [Finalizers](#Finalizers)

        [Events](#Events)

        [Nested Classes](#NestedClasses)

  - [<span data-ttu-id="e6160-110">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="e6160-110">Access Modifiers and Access Levels</span></span>](#AccessModifiers)

  - [<span data-ttu-id="e6160-111">Sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="e6160-111">Instantiating Classes</span></span>](#InstantiatingClasses)

  - [<span data-ttu-id="e6160-112">Statik sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="e6160-112">Static Classes and Members</span></span>](#Static)

  - [<span data-ttu-id="e6160-113">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="e6160-113">Anonymous Types</span></span>](#AnonymousTypes)

- [<span data-ttu-id="e6160-114">Devralma</span><span class="sxs-lookup"><span data-stu-id="e6160-114">Inheritance</span></span>](#Inheritance)

  - [<span data-ttu-id="e6160-115">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="e6160-115">Overriding Members</span></span>](#Overriding)

- [<span data-ttu-id="e6160-116">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e6160-116">Interfaces</span></span>](#Interfaces)

- [<span data-ttu-id="e6160-117">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="e6160-117">Generics</span></span>](#Generics)

- [<span data-ttu-id="e6160-118">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e6160-118">Delegates</span></span>](#Delegates)

## <a name="Classes"></a> <span data-ttu-id="e6160-119">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="e6160-119">Classes and Objects</span></span>

<span data-ttu-id="e6160-120">Koşulları *sınıfı* ve *nesne* bazen birbirlerinin yerine, ancak aslında sınıfları açıklar kullanılan *türü* nesnelerin nesneleri iken  *örnekleri* sınıf.</span><span class="sxs-lookup"><span data-stu-id="e6160-120">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="e6160-121">Bu nedenle, bir nesne oluşturma işlemi olarak da adlandırılır *oluşturmada*.</span><span class="sxs-lookup"><span data-stu-id="e6160-121">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="e6160-122">Blueprint benzerliği kullanarak bir sınıf plandır ve nesne bu yapılan bir binadır.</span><span class="sxs-lookup"><span data-stu-id="e6160-122">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="e6160-123">Bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-123">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="e6160-124">C# ayrıca sağlayan hafif bir sınıflar adlandırılan sürümünü *yapıları* yapın ve büyük nesneler dizisi oluşturmanız gerektiğinde yararlı olan çok fazla bellek için kullanmak istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="e6160-124">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="e6160-125">Yapı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-125">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="e6160-126">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="e6160-126">For more information, see:</span></span>

- [<span data-ttu-id="e6160-127">sınıf</span><span class="sxs-lookup"><span data-stu-id="e6160-127">class</span></span>](../../../csharp/language-reference/keywords/class.md)

- [<span data-ttu-id="e6160-128">struct </span><span class="sxs-lookup"><span data-stu-id="e6160-128">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)

### <a name="Members"></a> <span data-ttu-id="e6160-129">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="e6160-129">Class Members</span></span>

<span data-ttu-id="e6160-130">Her sınıf farklı olabilir *sınıf üyeleri* sınıf verilerini, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasındaki iletişimi sağlayan olayları tanımlayan özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="e6160-130">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="Properties"></a> <span data-ttu-id="e6160-131">Özellikler ve alanları</span><span class="sxs-lookup"><span data-stu-id="e6160-131">Properties and Fields</span></span>

<span data-ttu-id="e6160-132">Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e6160-132">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="e6160-133">Bunlar okunabilir ve doğrudan ayarlamak için alanları gibi değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="e6160-133">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="e6160-134">Bir alanı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-134">To define a field:</span></span>

```csharp
class SampleClass
{
    public string sampleField;
}
```

<span data-ttu-id="e6160-135">Özellik get ve set yordamları, değerlerin nasıl ayarlanacağı veya döndürüleceği hakkında daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6160-135">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="e6160-136">C# ya da özellik değerini depolamak için özel bir alan oluşturabilir veya bu alanı arka planda otomatik olarak oluşturmak ve özellik yordamları için temel mantığı sağlayan sözde ve otomatik olarak uygulanan özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6160-136">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="e6160-137">Otomatik uygulanan bir özellik tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-137">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="e6160-138">Okuma için bazı ek işlemler gerçekleştirebilir ve yazma özellik değeri özellik değerini depolamak için bir alan tanımlayın ve depolanması ve alınması için temel mantığı sağlayan gerekiyorsa:</span><span class="sxs-lookup"><span data-stu-id="e6160-138">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get { return _sample; }
        // Store the value in the field.
        set { _sample = value; }
    }
}
```

<span data-ttu-id="e6160-139">Çoğu özellikleri, yöntemleri ya da yordamlar hem ayarlamak ve özellik değerini almak için vardır.</span><span class="sxs-lookup"><span data-stu-id="e6160-139">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="e6160-140">Ancak, değiştiren veya okunmalarını kısıtlamak için salt okunur veya salt yazılır özellikler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6160-140">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="e6160-141">C# ' ta atlayabilirsiniz `get` veya `set` özellik yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e6160-141">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="e6160-142">Ancak, otomatik uygulanan özellikler salt okunur veya salt yazılır olamaz.</span><span class="sxs-lookup"><span data-stu-id="e6160-142">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="e6160-143">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="e6160-143">For more information, see:</span></span>

- [<span data-ttu-id="e6160-144">get</span><span class="sxs-lookup"><span data-stu-id="e6160-144">get</span></span>](../../../csharp/language-reference/keywords/get.md)

- [<span data-ttu-id="e6160-145">set</span><span class="sxs-lookup"><span data-stu-id="e6160-145">set</span></span>](../../../csharp/language-reference/keywords/set.md)

#### <a name="Methods"></a> <span data-ttu-id="e6160-146">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e6160-146">Methods</span></span>

<span data-ttu-id="e6160-147">A *yöntemi* , nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="e6160-147">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="e6160-148">Bir sınıfın yöntemini tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-148">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="e6160-149">Bir sınıfta çeşitli uygulamalar olabilir veya *aşırı*, parametre sayıları veya parametre türleri içinde farklı aynı yöntemin.</span><span class="sxs-lookup"><span data-stu-id="e6160-149">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="e6160-150">Bir yöntemi aşırı yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="e6160-150">To overload a method:</span></span>

```csharp
public int sampleMethod(string sampleParam) {};
public int sampleMethod(int sampleParam) {}
```

<span data-ttu-id="e6160-151">Çoğu durumda, sınıf tanımında bir yöntem bildirin.</span><span class="sxs-lookup"><span data-stu-id="e6160-151">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="e6160-152">Ancak, ayrıca C# destekler *genişletme yöntemleri* mevcut sınıfa sınıfın gerçek tanımı dışında yöntemler eklemenize olanak tanıyan.</span><span class="sxs-lookup"><span data-stu-id="e6160-152">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="e6160-153">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="e6160-153">For more information, see:</span></span>

- [<span data-ttu-id="e6160-154">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e6160-154">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="e6160-155">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e6160-155">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a> <span data-ttu-id="e6160-156">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e6160-156">Constructors</span></span>

<span data-ttu-id="e6160-157">Oluşturucular, belirli bir türde bir nesne oluşturulduğunda, otomatik olarak yürütülen sınıf yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="e6160-157">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="e6160-158">Kurucular genellikle yeni nesnenin veri üyeleri başlatın.</span><span class="sxs-lookup"><span data-stu-id="e6160-158">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="e6160-159">Sonra yalnızca bir sınıf oluşturulduğunda Oluşturucu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6160-159">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="e6160-160">Ayrıca, Oluşturucudaki kod her zaman bir sınıftaki herhangi bir kod önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="e6160-160">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="e6160-161">Ancak, başka bir yöntem olduğu gibi birden çok oluşturucu aşırı yüklemeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6160-161">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="e6160-162">Bir sınıf için bir kurucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-162">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="e6160-163">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="e6160-163">For more information, see:</span></span>

<span data-ttu-id="e6160-164">[Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="e6160-164">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>

#### <a name="Finalizers"></a> <span data-ttu-id="e6160-165">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="e6160-165">Finalizers</span></span>

<span data-ttu-id="e6160-166">Sonlandırıcılar, sınıfların örneklerini yok etmek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e6160-166">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="e6160-167">.NET Framework, atık toplayıcı sağlanmasını ve ayrılmasını uygulamanızda yönetilen nesneler için bellek otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="e6160-167">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="e6160-168">Ancak, yine de sonlandırıcılar uygulamanızın oluşturduğu herhangi yönetilmeyen kaynakları temizlemek için gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e6160-168">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="e6160-169">Yalnızca bir olabilir bir sınıf için bir sonlandırıcı.</span><span class="sxs-lookup"><span data-stu-id="e6160-169">There can be only one finalizers for a class.</span></span>

<span data-ttu-id="e6160-170">Sonlandırıcılar ve .NET Framework atık toplama hakkında daha fazla bilgi için bkz: [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="e6160-170">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="Events"></a> <span data-ttu-id="e6160-171">Olayları</span><span class="sxs-lookup"><span data-stu-id="e6160-171">Events</span></span>

<span data-ttu-id="e6160-172">Bir sınıf olayları etkinleştirin veya nesneyi diğer sınıfları veya nesneleri ilgilendiğiniz bir şeyler olduğunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="e6160-172">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="e6160-173">Olay gönderir (veya harekete geçiren) sınıf adlı *yayımcı* ve olay alma (veya tanıtıcı) sınıflar adlandırılan *aboneleri*.</span><span class="sxs-lookup"><span data-stu-id="e6160-173">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="e6160-174">Olaylar hakkında daha fazla bilgi için nasıl oluştukları ve işlendikleri bkz [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="e6160-174">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="e6160-175">Bir sınıf içinde bir olay bildirmek için kullanın [olay](../../../csharp/language-reference/keywords/event.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e6160-175">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>

- <span data-ttu-id="e6160-176">Bir olayı için olay temsilcisini çağırın.</span><span class="sxs-lookup"><span data-stu-id="e6160-176">To raise an event, invoke the event delegate.</span></span>

- <span data-ttu-id="e6160-177">Bir olaya abone olmak için kullanmak `+=` işleci, bir olayın aboneliğini kaldırmak için kullanın; `-=` işleci.</span><span class="sxs-lookup"><span data-stu-id="e6160-177">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="NestedClasses"></a> <span data-ttu-id="e6160-178">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="e6160-178">Nested Classes</span></span>

<span data-ttu-id="e6160-179">Başka bir sınıfın içinde tanımlanan bir sınıfa *iç içe geçmiş*.</span><span class="sxs-lookup"><span data-stu-id="e6160-179">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="e6160-180">Varsayılan olarak, iç içe geçmiş özel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="e6160-180">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="e6160-181">İç içe geçmiş sınıfının bir örneğini oluşturmak için kapsayıcı sınıfının arkasına bir nokta koyun ve sonra ardından iç içe geçmiş sınıf adı adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="e6160-181">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="AccessModifiers"></a> <span data-ttu-id="e6160-182">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="e6160-182">Access Modifiers and Access Levels</span></span>

<span data-ttu-id="e6160-183">Tüm sınıflar ve sınıf üyeleri sağlamaları için diğer sınıflar kullanılarak hangi erişim düzeyini belirtebilirsiniz *erişim değiştiricilerine*.</span><span class="sxs-lookup"><span data-stu-id="e6160-183">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="e6160-184">Aşağıdaki erişim değiştiriciler kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e6160-184">The following access modifiers are available:</span></span>

|<span data-ttu-id="e6160-185">C# Modifier</span><span class="sxs-lookup"><span data-stu-id="e6160-185">C# Modifier</span></span>|<span data-ttu-id="e6160-186">Tanım</span><span class="sxs-lookup"><span data-stu-id="e6160-186">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="e6160-187">public</span><span class="sxs-lookup"><span data-stu-id="e6160-187">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="e6160-188">Türe veya üyeye aynı derlemenin veya ona başvuran başka bir derleme içindeki diğer kodlardan tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e6160-188">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="e6160-189">private</span><span class="sxs-lookup"><span data-stu-id="e6160-189">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="e6160-190">Türe veya üyeye aynı sınıftaki kod tarafından yalnızca erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e6160-190">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="e6160-191">protected</span><span class="sxs-lookup"><span data-stu-id="e6160-191">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="e6160-192">Türe veya üyeye aynı sınıftaki veya türetilmiş bir sınıf içinde kod tarafından yalnızca erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e6160-192">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="e6160-193">internal</span><span class="sxs-lookup"><span data-stu-id="e6160-193">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="e6160-194">Türe veya üyeye aynı derlemedeki ancak farklı derlemeyle herhangi bir kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e6160-194">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|[<span data-ttu-id="e6160-195">protected internal</span><span class="sxs-lookup"><span data-stu-id="e6160-195">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="e6160-196">Türe veya üyeye aynı derlemedeki kod ile veya başka bir derlemedeki türetilmiş sınıfla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e6160-196">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|
|[<span data-ttu-id="e6160-197">private protected</span><span class="sxs-lookup"><span data-stu-id="e6160-197">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="e6160-198">Türe veya üyeye aynı sınıftaki veya türetilmiş bir sınıfın temel sınıf derleme içinde kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e6160-198">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|

<span data-ttu-id="e6160-199">Daha fazla bilgi için [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="e6160-199">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>

### <a name="InstantiatingClasses"></a> <span data-ttu-id="e6160-200">Sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="e6160-200">Instantiating Classes</span></span>

<span data-ttu-id="e6160-201">Bir nesne oluşturmak için bir sınıf örneği başlatmanız veya sınıf örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6160-201">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="e6160-202">Bir sınıf başlatıldıktan sonra Örneğin özelliklerine ve alanlarına değerler atayın ve sınıf yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6160-202">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

<span data-ttu-id="e6160-203">Sınıf örnekleme işlemi sırasında özellikleri değerleri atamak için nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="e6160-203">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="e6160-204">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="e6160-204">For more information, see:</span></span>

- [<span data-ttu-id="e6160-205">new İşleci</span><span class="sxs-lookup"><span data-stu-id="e6160-205">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)

- [<span data-ttu-id="e6160-206">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="e6160-206">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a> <span data-ttu-id="e6160-207">Statik sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="e6160-207">Static Classes and Members</span></span>

<span data-ttu-id="e6160-208">Statik sınıf üyesi bir özellik, yordam veya bir sınıfın tüm örnekleri tarafından paylaşıldığını alan var.</span><span class="sxs-lookup"><span data-stu-id="e6160-208">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="e6160-209">Statik bir üye tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-209">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="e6160-210">Statik bir üyeye erişmek için sınıfın adını, bu sınıfın bir nesnesi oluşturmadan kullanın:</span><span class="sxs-lookup"><span data-stu-id="e6160-210">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="e6160-211">C# ' de statik sınıflar yalnızca statik üyeleri sahiptir ve örnekleri oluşturulamaz.</span><span class="sxs-lookup"><span data-stu-id="e6160-211">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="e6160-212">Statik üyeleri de statik olmayan özellikler, alanlara veya yöntemlere erişemez</span><span class="sxs-lookup"><span data-stu-id="e6160-212">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="e6160-213">Daha fazla bilgi için bkz: [statik](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="e6160-213">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>

### <a name="AnonymousTypes"></a> <span data-ttu-id="e6160-214">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="e6160-214">Anonymous Types</span></span>

<span data-ttu-id="e6160-215">Anonim türler nesne veri türü için bir sınıf tanımı yazmaya gerek kalmadan oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6160-215">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="e6160-216">Bunun yerine, derleyici bir sınıf sizin için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e6160-216">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="e6160-217">Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e6160-217">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="e6160-218">Anonim bir türün bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-218">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="e6160-219">Daha fazla bilgi için bkz.: [Anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="e6160-219">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>

## <a name="Inheritance"></a> <span data-ttu-id="e6160-220">Devralma</span><span class="sxs-lookup"><span data-stu-id="e6160-220">Inheritance</span></span>

<span data-ttu-id="e6160-221">Devralma, başka bir sınıfta tanımlanan davranışı değiştirir kullanır ve genişleten yeni bir sınıf oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6160-221">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="e6160-222">Üyeleri devralınan sınıf *temel sınıfı*, ve bu üyeleri devralan sınıf *türetilmiş sınıf*.</span><span class="sxs-lookup"><span data-stu-id="e6160-222">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="e6160-223">Ancak, C# içindeki tüm sınıflar örtük olarak devralınacak <xref:System.Object> .NET sınıf hiyerarşisini destekleyen ve tüm sınıflara alt düzey hizmetler sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="e6160-223">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="e6160-224">C# birden çok devralmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e6160-224">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="e6160-225">Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6160-225">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="e6160-226">Temel sınıfından devralmak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-226">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass {}
```

<span data-ttu-id="e6160-227">Varsayılan olarak, tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="e6160-227">By default all classes can be inherited.</span></span> <span data-ttu-id="e6160-228">Ancak, bir sınıfın temel sınıf olarak kullanılmamalıdır veya yalnızca temel sınıf olarak kullanılan bir sınıf oluşturmak olup olmadığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6160-228">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="e6160-229">Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="e6160-229">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="e6160-230">Bir sınıf yalnızca temel sınıf olarak kullanılabilecek ve başlatılamayacak belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="e6160-230">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="e6160-231">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="e6160-231">For more information, see:</span></span>

- [<span data-ttu-id="e6160-232">korumalı</span><span class="sxs-lookup"><span data-stu-id="e6160-232">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)

- [<span data-ttu-id="e6160-233">abstract</span><span class="sxs-lookup"><span data-stu-id="e6160-233">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)

### <a name="Overriding"></a> <span data-ttu-id="e6160-234">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="e6160-234">Overriding Members</span></span>

<span data-ttu-id="e6160-235">Varsayılan olarak, türetilmiş bir sınıf tüm üyelerini kendi temel sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="e6160-235">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="e6160-236">Devralınan üye davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6160-236">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="e6160-237">Diğer bir deyişle, türetilmiş bir sınıf içindeki yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6160-237">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="e6160-238">Özellikleri ve yöntemleri nasıl geçersiz kılınacağını denetlemek için aşağıdaki değiştiriciler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e6160-238">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="e6160-239">C# Modifier</span><span class="sxs-lookup"><span data-stu-id="e6160-239">C# Modifier</span></span>|<span data-ttu-id="e6160-240">Tanım</span><span class="sxs-lookup"><span data-stu-id="e6160-240">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="e6160-241">virtual</span><span class="sxs-lookup"><span data-stu-id="e6160-241">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="e6160-242">Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="e6160-242">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="e6160-243">override</span><span class="sxs-lookup"><span data-stu-id="e6160-243">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="e6160-244">Temel sınıfta tanımlanan sanal bir (geçersiz kılınabilir) üyeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e6160-244">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="e6160-245">abstract</span><span class="sxs-lookup"><span data-stu-id="e6160-245">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="e6160-246">Gerektiren bir sınıf üyesinin derlenen sınıfta geçersiz kılınacak.</span><span class="sxs-lookup"><span data-stu-id="e6160-246">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="e6160-247">new Değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="e6160-247">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="e6160-248">Bir temel sınıftan devralınan üyeyi gizler</span><span class="sxs-lookup"><span data-stu-id="e6160-248">Hides a member inherited from a base class</span></span>|

## <a name="Interfaces"></a> <span data-ttu-id="e6160-249">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e6160-249">Interfaces</span></span>

<span data-ttu-id="e6160-250">Sınıflar gibi arabirimler, özellikleri, yöntemleri ve olayları kümesi tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="e6160-250">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="e6160-251">Ancak, sınıflardan farklı olarak, arabirimler uygulama sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="e6160-251">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="e6160-252">Bunlar sınıfları tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e6160-252">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="e6160-253">Tam olarak tanımlandığı şekilde bir arabirimi uygulayan bir sınıf, o arabirimi her yönüyle uygulamalıdır bir arabirim bir sözleşmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e6160-253">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="e6160-254">Arabirim tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-254">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

<span data-ttu-id="e6160-255">Bir sınıf içinde arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-255">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="e6160-256">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="e6160-256">For more information, see:</span></span>

[<span data-ttu-id="e6160-257">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e6160-257">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

[<span data-ttu-id="e6160-258">arabirim</span><span class="sxs-lookup"><span data-stu-id="e6160-258">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)

## <a name="Generics"></a> <span data-ttu-id="e6160-259">Genel türler</span><span class="sxs-lookup"><span data-stu-id="e6160-259">Generics</span></span>

<span data-ttu-id="e6160-260">Sınıflar, yapılar, arabirimler ve yöntemler .NET Framework'teki içerebilir *tür parametrelerindeki* bunlar depolayabildikleri veya kullanabildikleri nesnelerin türlerini tanımlayan.</span><span class="sxs-lookup"><span data-stu-id="e6160-260">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="e6160-261">Genel türlerin yararları en yaygın örnek, bir koleksiyonda depolanacak nesnelerin türünü belirleyebileceğiniz koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="e6160-261">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="e6160-262">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-262">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="e6160-263">Bir genel sınıfın bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-263">To create an instance of a generic class:</span></span>

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="e6160-264">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="e6160-264">For more information, see:</span></span>

- [<span data-ttu-id="e6160-265">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="e6160-265">Generics</span></span>](~/docs/standard/generics/index.md)

- [<span data-ttu-id="e6160-266">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="e6160-266">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)

## <a name="Delegates"></a> <span data-ttu-id="e6160-267">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e6160-267">Delegates</span></span>

<span data-ttu-id="e6160-268">A *temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu bir imza ile herhangi bir yönteme başvuru sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e6160-268">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="e6160-269">Çağırma (çağrı yöntemi temsilci aracılığıyla veya).</span><span class="sxs-lookup"><span data-stu-id="e6160-269">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="e6160-270">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e6160-270">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="e6160-271">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="e6160-271">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="e6160-272">Temsilcileri olay işlemede kullanma hakkında daha fazla bilgi için bkz. [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="e6160-272">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="e6160-273">Temsilci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-273">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="e6160-274">Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="e6160-274">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void sampleMethod(string message)
    {
        // Add code here.
    }
    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

<span data-ttu-id="e6160-275">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="e6160-275">For more information, see:</span></span>

- [<span data-ttu-id="e6160-276">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e6160-276">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

- [<span data-ttu-id="e6160-277">temsilci</span><span class="sxs-lookup"><span data-stu-id="e6160-277">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)

## <a name="see-also"></a><span data-ttu-id="e6160-278">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6160-278">See also</span></span>

- [<span data-ttu-id="e6160-279">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e6160-279">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
