---
title: Nesne odaklı programlama (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 121d2e43f6896179756067e661be6d7960a1ee64
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418042"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="112da-102">Nesne odaklı programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="112da-102">Object-Oriented Programming (C#)</span></span>

<span data-ttu-id="112da-103">C#Kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne odaklı programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="112da-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

<span data-ttu-id="112da-104">*Kapsülleme* , ilişkili özellikler, Yöntemler ve diğer üyelerin bir grubunun tek bir birim veya nesne olarak kabul edildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="112da-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

<span data-ttu-id="112da-105">*Devralma* , mevcut bir sınıfı temel alan yeni sınıflar oluşturma özelliğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="112da-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

<span data-ttu-id="112da-106">Çok *biçimlilik* , her bir sınıf farklı yollarla aynı özellikleri veya yöntemleri uyguladığından bile, birbirinin yerine kullanılabilecek birden fazla sınıfa sahip olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="112da-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

<span data-ttu-id="112da-107">Bu bölümde aşağıdaki kavramlar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="112da-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="112da-108">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="112da-108">Classes and Objects</span></span>](#Classes)

  - [<span data-ttu-id="112da-109">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="112da-109">Class Members</span></span>](#Members)

    - [<span data-ttu-id="112da-110">Özellikler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="112da-110">Properties and Fields</span></span>](#Properties)

    - [<span data-ttu-id="112da-111">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="112da-111">Methods</span></span>](#Methods)

    - [<span data-ttu-id="112da-112">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="112da-112">Constructors</span></span>](#Constructors)

    - [<span data-ttu-id="112da-113">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="112da-113">Finalizers</span></span>](#Finalizers)

    - [<span data-ttu-id="112da-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="112da-114">Events</span></span>](#Events)

    - [<span data-ttu-id="112da-115">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="112da-115">Nested Classes</span></span>](#NestedClasses)

  - [<span data-ttu-id="112da-116">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="112da-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)

  - [<span data-ttu-id="112da-117">Sınıfları örnekleme</span><span class="sxs-lookup"><span data-stu-id="112da-117">Instantiating Classes</span></span>](#InstantiatingClasses)

  - [<span data-ttu-id="112da-118">Statik sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="112da-118">Static Classes and Members</span></span>](#Static)

  - [<span data-ttu-id="112da-119">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="112da-119">Anonymous Types</span></span>](#AnonymousTypes)

- [<span data-ttu-id="112da-120">Devralma</span><span class="sxs-lookup"><span data-stu-id="112da-120">Inheritance</span></span>](#Inheritance)

  - [<span data-ttu-id="112da-121">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="112da-121">Overriding Members</span></span>](#Overriding)

- [<span data-ttu-id="112da-122">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="112da-122">Interfaces</span></span>](#Interfaces)

- [<span data-ttu-id="112da-123">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="112da-123">Generics</span></span>](#Generics)

- [<span data-ttu-id="112da-124">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="112da-124">Delegates</span></span>](#Delegates)

## <a name="Classes"></a><span data-ttu-id="112da-125">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="112da-125">Classes and Objects</span></span>

<span data-ttu-id="112da-126">Terimler *sınıfı* ve *nesne* bazen birbirinin yerine kullanılır, ancak aslında nesneler sınıfların kullanılabilir *örnekleri* olduğunda sınıflar nesne *türünü* betimler.</span><span class="sxs-lookup"><span data-stu-id="112da-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="112da-127">Bu nedenle, bir nesne oluşturma konusuna *örnek*oluşturma denir.</span><span class="sxs-lookup"><span data-stu-id="112da-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="112da-128">Şema benzerleme vurguladı kullanarak bir sınıf şeması bir şema, bir nesne ise bu şema tarafından oluşturulan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="112da-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="112da-129">Bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="112da-129">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="112da-130">C#Ayrıca, büyük bir nesne dizisi oluşturmanız gerektiğinde ve bunun için çok fazla bellek kullanmak istemediğinizde yararlı olan *yapılar* adlı sınıfların hafif bir sürümünü de sağlar.</span><span class="sxs-lookup"><span data-stu-id="112da-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="112da-131">Bir yapı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="112da-131">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="112da-132">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="112da-132">For more information, see:</span></span>

- [<span data-ttu-id="112da-133">class</span><span class="sxs-lookup"><span data-stu-id="112da-133">class</span></span>](../../language-reference/keywords/class.md)

- [<span data-ttu-id="112da-134">struct</span><span class="sxs-lookup"><span data-stu-id="112da-134">struct</span></span>](../../language-reference/keywords/struct.md)

### <a name="Members"></a><span data-ttu-id="112da-135">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="112da-135">Class Members</span></span>

<span data-ttu-id="112da-136">Her sınıf, sınıf verilerini tanımlayan özellikleri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasında iletişim sağlayan olayları içeren farklı *sınıf üyelerine* sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="112da-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="Properties"></a><span data-ttu-id="112da-137">Özellikler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="112da-137">Properties and Fields</span></span>

<span data-ttu-id="112da-138">Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="112da-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="112da-139">Alanlar, okunabilir veya doğrudan ayarlanabileceğinden, değişkenlere benzer.</span><span class="sxs-lookup"><span data-stu-id="112da-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="112da-140">Bir alan tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="112da-140">To define a field:</span></span>

```csharp
class SampleClass
{
    public string sampleField;
}
```

<span data-ttu-id="112da-141">Özellikler, değerlerin nasıl ayarlandığı veya döndürüldüğü hakkında daha fazla denetim sağlayan alma ve ayarlama yordamlarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="112da-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="112da-142">C#Özellik değerini depolamak için özel bir alan oluşturmanıza veya bu alanı arka planda otomatik olarak oluşturan otomatik uygulanan özellikler olarak adlandırılan ve özellik yordamları için temel mantığı sağlayan bir özel alan oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="112da-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="112da-143">Otomatik uygulanan bir özellik tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="112da-143">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="112da-144">Özellik değerini okumak ve yazmak için bazı ek işlemler gerçekleştirmeniz gerekiyorsa, özellik değerini depolamak için bir alan tanımlayın ve bunu depolamak ve almak için temel mantığı sağlayın:</span><span class="sxs-lookup"><span data-stu-id="112da-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="112da-145">Çoğu özelliğin, özellik değerini ayarlamak ve almak için yöntemleri ya da yordamları vardır.</span><span class="sxs-lookup"><span data-stu-id="112da-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="112da-146">Ancak, bunları değiştirilmesini veya okumayı kısıtlamak için salt okunurdur veya salt yazılır özellikler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="112da-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="112da-147">İçinde C#, `get` veya `set` özellik yöntemini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="112da-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="112da-148">Ancak otomatik olarak uygulanan özellikler salt okunurdur veya salt yazılır olamaz.</span><span class="sxs-lookup"><span data-stu-id="112da-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="112da-149">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="112da-149">For more information, see:</span></span>

- [<span data-ttu-id="112da-150">get</span><span class="sxs-lookup"><span data-stu-id="112da-150">get</span></span>](../../language-reference/keywords/get.md)

- [<span data-ttu-id="112da-151">set</span><span class="sxs-lookup"><span data-stu-id="112da-151">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="Methods"></a><span data-ttu-id="112da-152">Yöntem</span><span class="sxs-lookup"><span data-stu-id="112da-152">Methods</span></span>

<span data-ttu-id="112da-153">Bir *Yöntem* , bir nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="112da-153">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="112da-154">Bir sınıfın yöntemini tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="112da-154">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="112da-155">Bir sınıf, parametrelerin veya parametre türlerinin sayısında farklı olan aynı yöntemin çeşitli uygulamalarına veya *aşırı*yüküne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="112da-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="112da-156">Bir yöntemi aşırı yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="112da-156">To overload a method:</span></span>

```csharp
public int sampleMethod(string sampleParam) {};
public int sampleMethod(int sampleParam) {}
```

<span data-ttu-id="112da-157">Çoğu durumda, bir sınıf tanımı içinde bir yöntemi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="112da-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="112da-158">Ancak, C# sınıfının gerçek tanımının dışında mevcut bir sınıfa Yöntemler eklemenize olanak tanıyan *genişletme yöntemlerini* de destekler.</span><span class="sxs-lookup"><span data-stu-id="112da-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="112da-159">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="112da-159">For more information, see:</span></span>

- [<span data-ttu-id="112da-160">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="112da-160">Methods</span></span>](../classes-and-structs/methods.md)

- [<span data-ttu-id="112da-161">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="112da-161">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a><span data-ttu-id="112da-162">Kurucu</span><span class="sxs-lookup"><span data-stu-id="112da-162">Constructors</span></span>

<span data-ttu-id="112da-163">Oluşturucular, belirli bir türden bir nesne oluşturulduğunda otomatik olarak yürütülen sınıf yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="112da-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="112da-164">Oluşturucular genellikle yeni nesnenin veri üyelerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="112da-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="112da-165">Bir Oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="112da-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="112da-166">Ayrıca, kurucudaki kod her zaman bir sınıftaki diğer koddan önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="112da-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="112da-167">Ancak, başka bir yöntemle aynı şekilde birden çok Oluşturucu aşırı yüklemesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="112da-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="112da-168">Bir sınıf için bir Oluşturucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="112da-168">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="112da-169">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="112da-169">For more information, see:</span></span>

<span data-ttu-id="112da-170">[Oluşturucular](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="112da-170">[Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="Finalizers"></a><span data-ttu-id="112da-171">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="112da-171">Finalizers</span></span>

<span data-ttu-id="112da-172">Sonlandırıcılar sınıfların örneklerini deketmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="112da-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="112da-173">.NET Framework, çöp toplayıcı uygulamanızdaki yönetilen nesneler için bellek ayırmayı ve serbest bırakma işlemini otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="112da-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="112da-174">Ancak, uygulamanızın oluşturduğu yönetilmeyen kaynakları temizlemek için sonlandırıcılardan yine de ihtiyacınız olabilir.</span><span class="sxs-lookup"><span data-stu-id="112da-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="112da-175">Bir sınıf için yalnızca bir sonlandırıcılar olabilir.</span><span class="sxs-lookup"><span data-stu-id="112da-175">There can be only one finalizers for a class.</span></span>

<span data-ttu-id="112da-176">.NET Framework sonlandırıcılar ve çöp toplama hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="112da-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="Events"></a><span data-ttu-id="112da-177">Olayları</span><span class="sxs-lookup"><span data-stu-id="112da-177">Events</span></span>

<span data-ttu-id="112da-178">Olaylar, bir sınıf ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="112da-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="112da-179">Olayı gönderen (veya Başlatan) sınıf *Yayımcı* olarak adlandırılır ve olayı alan (veya işleyen) sınıflar *aboneler*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="112da-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="112da-180">Olaylar, nasıl oluşturulur ve işlenir hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="112da-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="112da-181">Bir sınıfında bir olay bildirmek için [Event](../../language-reference/keywords/event.md) anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="112da-181">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>

- <span data-ttu-id="112da-182">Bir olayı yükseltmek için olay temsilcisini çağırın.</span><span class="sxs-lookup"><span data-stu-id="112da-182">To raise an event, invoke the event delegate.</span></span>

- <span data-ttu-id="112da-183">Bir olaya abone olmak için `+=` işlecini kullanın; bir olayın aboneliğini kaldırmak için `-=` işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="112da-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="NestedClasses"></a><span data-ttu-id="112da-184">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="112da-184">Nested Classes</span></span>

<span data-ttu-id="112da-185">Başka bir sınıf içinde tanımlı bir sınıf *iç içe*çağırılır.</span><span class="sxs-lookup"><span data-stu-id="112da-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="112da-186">Varsayılan olarak, iç içe yerleştirilmiş sınıf özeldir.</span><span class="sxs-lookup"><span data-stu-id="112da-186">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="112da-187">İç içe yerleştirilmiş sınıfın bir örneğini oluşturmak için, container sınıfının adını ve ardından nokta ve ardından iç içe geçmiş sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="112da-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="AccessModifiers"></a><span data-ttu-id="112da-188">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="112da-188">Access Modifiers and Access Levels</span></span>

<span data-ttu-id="112da-189">Tüm sınıflar ve sınıf üyeleri, *erişim değiştiricilerini*kullanarak diğer sınıflara hangi erişim düzeyini sundukları belirler.</span><span class="sxs-lookup"><span data-stu-id="112da-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="112da-190">Aşağıdaki erişim değiştiriciler kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="112da-190">The following access modifiers are available:</span></span>

|<span data-ttu-id="112da-191">C#İcisi</span><span class="sxs-lookup"><span data-stu-id="112da-191">C# Modifier</span></span>|<span data-ttu-id="112da-192">Tanım</span><span class="sxs-lookup"><span data-stu-id="112da-192">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="112da-193">public</span><span class="sxs-lookup"><span data-stu-id="112da-193">public</span></span>](../../language-reference/keywords/public.md)|<span data-ttu-id="112da-194">Türe veya üyeye aynı derlemedeki veya buna başvuran başka bir derlemede bir veya daha fazla kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="112da-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="112da-195">private</span><span class="sxs-lookup"><span data-stu-id="112da-195">private</span></span>](../../language-reference/keywords/private.md)|<span data-ttu-id="112da-196">Türe veya üyeye yalnızca aynı sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="112da-196">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="112da-197">protected</span><span class="sxs-lookup"><span data-stu-id="112da-197">protected</span></span>](../../language-reference/keywords/protected.md)|<span data-ttu-id="112da-198">Türe veya üyeye yalnızca aynı sınıftaki veya türetilmiş bir sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="112da-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="112da-199">internal</span><span class="sxs-lookup"><span data-stu-id="112da-199">internal</span></span>](../../language-reference/keywords/internal.md)|<span data-ttu-id="112da-200">Türe veya üyeye aynı derlemedeki kod tarafından erişilebilir, ancak başka bir derlemeden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="112da-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|[<span data-ttu-id="112da-201">protected internal</span><span class="sxs-lookup"><span data-stu-id="112da-201">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)|<span data-ttu-id="112da-202">Türe veya üyeye aynı derlemedeki herhangi bir kod ya da başka bir derlemedeki türetilmiş bir sınıf tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="112da-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|
|[<span data-ttu-id="112da-203">private protected</span><span class="sxs-lookup"><span data-stu-id="112da-203">private protected</span></span>](../../language-reference/keywords/private-protected.md)|<span data-ttu-id="112da-204">Türe veya üyeye aynı sınıftaki veya temel sınıf derlemesi içindeki türetilmiş bir sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="112da-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|

<span data-ttu-id="112da-205">Daha fazla bilgi için bkz. [erişim değiştiricileri](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="112da-205">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="InstantiatingClasses"></a><span data-ttu-id="112da-206">Sınıfları örnekleme</span><span class="sxs-lookup"><span data-stu-id="112da-206">Instantiating Classes</span></span>

<span data-ttu-id="112da-207">Bir nesne oluşturmak için bir sınıf örneği oluşturmanız veya bir sınıf örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="112da-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="112da-208">Bir sınıfı örnekledikten sonra, örneğin özelliklerine ve alanlarına değerler atayabilir ve sınıf yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="112da-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

<span data-ttu-id="112da-209">Sınıf örnek oluşturma işlemi sırasında özelliklere değer atamak için, nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="112da-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="112da-210">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="112da-210">For more information, see:</span></span>

- [<span data-ttu-id="112da-211">new İşleci</span><span class="sxs-lookup"><span data-stu-id="112da-211">new Operator</span></span>](../../language-reference/operators/new-operator.md)

- [<span data-ttu-id="112da-212">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="112da-212">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a><span data-ttu-id="112da-213">Statik sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="112da-213">Static Classes and Members</span></span>

<span data-ttu-id="112da-214">Sınıfının statik üyesi, bir sınıfın tüm örnekleri tarafından paylaşılan bir özellik, yordam veya alandır.</span><span class="sxs-lookup"><span data-stu-id="112da-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="112da-215">Statik üye tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="112da-215">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="112da-216">Statik üyeye erişmek için, sınıfın adını bu sınıfın bir nesnesi oluşturmadan kullanın:</span><span class="sxs-lookup"><span data-stu-id="112da-216">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="112da-217">İçindeki C# statik sınıfların yalnızca statik üyeleri vardır ve örneklenemez.</span><span class="sxs-lookup"><span data-stu-id="112da-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="112da-218">Statik Üyeler ayrıca statik olmayan özelliklere, alanlara veya yöntemlere erişemez</span><span class="sxs-lookup"><span data-stu-id="112da-218">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="112da-219">Daha fazla bilgi için bkz: [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="112da-219">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="AnonymousTypes"></a><span data-ttu-id="112da-220">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="112da-220">Anonymous Types</span></span>

<span data-ttu-id="112da-221">Anonim türler, veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="112da-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="112da-222">Bunun yerine, derleyici sizin için bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="112da-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="112da-223">Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="112da-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="112da-224">Anonim türün bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="112da-224">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="112da-225">Daha fazla bilgi için bkz: [anonim türler](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="112da-225">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="Inheritance"></a><span data-ttu-id="112da-226">Devralmayı</span><span class="sxs-lookup"><span data-stu-id="112da-226">Inheritance</span></span>

<span data-ttu-id="112da-227">Devralma, başka bir sınıfta tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni bir sınıf oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="112da-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="112da-228">Üyeleri devralınmış olan sınıfa *temel sınıf*denir ve bu üyeleri devralan sınıfa *türetilmiş sınıf*denir.</span><span class="sxs-lookup"><span data-stu-id="112da-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="112da-229">Ancak, içindeki C# tüm sınıflar, .NET sınıf hiyerarşisini destekleyen <xref:System.Object> sınıfından dolaylı olarak devralınır ve tüm sınıflara alt düzey hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="112da-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="112da-230">C#birden çok devralmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="112da-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="112da-231">Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="112da-231">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="112da-232">Temel sınıftan devralması için:</span><span class="sxs-lookup"><span data-stu-id="112da-232">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass {}
```

<span data-ttu-id="112da-233">Varsayılan olarak, tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="112da-233">By default all classes can be inherited.</span></span> <span data-ttu-id="112da-234">Ancak, bir sınıfın temel sınıf olarak kullanılması gerekip gerekmediğini belirtebilir veya yalnızca temel sınıf olarak kullanılabilecek bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="112da-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="112da-235">Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="112da-235">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="112da-236">Bir sınıfın yalnızca temel sınıf olarak kullanılabileceğini ve örneklenemez olduğunu belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="112da-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="112da-237">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="112da-237">For more information, see:</span></span>

- [<span data-ttu-id="112da-238">sealed</span><span class="sxs-lookup"><span data-stu-id="112da-238">sealed</span></span>](../../language-reference/keywords/sealed.md)

- [<span data-ttu-id="112da-239">abstract</span><span class="sxs-lookup"><span data-stu-id="112da-239">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="Overriding"></a><span data-ttu-id="112da-240">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="112da-240">Overriding Members</span></span>

<span data-ttu-id="112da-241">Varsayılan olarak, türetilmiş bir sınıf kendi temel sınıfından tüm üyeleri devralır.</span><span class="sxs-lookup"><span data-stu-id="112da-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="112da-242">Devralınan üyenin davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="112da-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="112da-243">Diğer bir deyişle, türetilmiş sınıfta yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="112da-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="112da-244">Özelliklerin ve yöntemlerin nasıl geçersiz kılınabileceğini denetlemek için aşağıdaki değiştiriciler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="112da-244">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="112da-245">C#İcisi</span><span class="sxs-lookup"><span data-stu-id="112da-245">C# Modifier</span></span>|<span data-ttu-id="112da-246">Tanım</span><span class="sxs-lookup"><span data-stu-id="112da-246">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="112da-247">virtual</span><span class="sxs-lookup"><span data-stu-id="112da-247">virtual</span></span>](../../language-reference/keywords/virtual.md)|<span data-ttu-id="112da-248">Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="112da-248">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="112da-249">override</span><span class="sxs-lookup"><span data-stu-id="112da-249">override</span></span>](../../language-reference/keywords/override.md)|<span data-ttu-id="112da-250">Temel sınıfta tanımlanan bir sanal (geçersiz kılınabilir) üyeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="112da-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="112da-251">abstract</span><span class="sxs-lookup"><span data-stu-id="112da-251">abstract</span></span>](../../language-reference/keywords/abstract.md)|<span data-ttu-id="112da-252">Türetilmiş sınıfta bir sınıf üyesinin geçersiz kılınmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="112da-252">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="112da-253">new Değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="112da-253">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md)|<span data-ttu-id="112da-254">Temel sınıftan devralınan bir üyeyi gizler</span><span class="sxs-lookup"><span data-stu-id="112da-254">Hides a member inherited from a base class</span></span>|

## <a name="Interfaces"></a><span data-ttu-id="112da-255">Arabirimlerdeki</span><span class="sxs-lookup"><span data-stu-id="112da-255">Interfaces</span></span>

<span data-ttu-id="112da-256">Sınıflar gibi arabirimler, özellikler, Yöntemler ve olaylar kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="112da-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="112da-257">Ancak sınıfların aksine arabirimler uygulama sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="112da-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="112da-258">Sınıflar tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="112da-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="112da-259">Arabirim, bir arabirimi uygulayan bir sınıfın, bu arabirimin her yönünü tam olarak tanımlandığı gibi uygulaması gerektiğini belirten bir sözleşmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="112da-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="112da-260">Bir arabirim tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="112da-260">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

<span data-ttu-id="112da-261">Bir sınıfa bir arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="112da-261">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="112da-262">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="112da-262">For more information, see:</span></span>

[<span data-ttu-id="112da-263">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="112da-263">Interfaces</span></span>](../interfaces/index.md)

[<span data-ttu-id="112da-264">interface</span><span class="sxs-lookup"><span data-stu-id="112da-264">interface</span></span>](../../language-reference/keywords/interface.md)

## <a name="Generics"></a><span data-ttu-id="112da-265">Tür</span><span class="sxs-lookup"><span data-stu-id="112da-265">Generics</span></span>

<span data-ttu-id="112da-266">.NET Framework sınıflar, yapılar, arabirimler ve Yöntemler, depolayabilecekleri veya kullanabileceği nesne türlerini tanımlayan *tür parametreleri* içerebilir.</span><span class="sxs-lookup"><span data-stu-id="112da-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="112da-267">En yaygın genel türler örneği, bir koleksiyonda depolanacak nesne türlerini belirtebileceğiniz bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="112da-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="112da-268">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="112da-268">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="112da-269">Genel sınıfın bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="112da-269">To create an instance of a generic class:</span></span>

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="112da-270">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="112da-270">For more information, see:</span></span>

- [<span data-ttu-id="112da-271">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="112da-271">Generics</span></span>](../../../standard/generics/index.md)

- [<span data-ttu-id="112da-272">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="112da-272">Generics</span></span>](../generics/index.md)

## <a name="Delegates"></a><span data-ttu-id="112da-273">İlerin</span><span class="sxs-lookup"><span data-stu-id="112da-273">Delegates</span></span>

<span data-ttu-id="112da-274">*Temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu imzaya sahip herhangi bir yönteme başvuru sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="112da-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="112da-275">Yöntemi temsilci aracılığıyla çağırabilir (veya çağırabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="112da-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="112da-276">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="112da-276">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="112da-277">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="112da-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="112da-278">Olay İşlemede temsilciler kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="112da-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="112da-279">Bir temsilci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="112da-279">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="112da-280">Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="112da-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="112da-281">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="112da-281">For more information, see:</span></span>

- [<span data-ttu-id="112da-282">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="112da-282">Delegates</span></span>](../delegates/index.md)

- [<span data-ttu-id="112da-283">delegate</span><span class="sxs-lookup"><span data-stu-id="112da-283">delegate</span></span>](../../language-reference/builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="112da-284">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="112da-284">See also</span></span>

- [<span data-ttu-id="112da-285">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="112da-285">C# Programming Guide</span></span>](../index.md)
