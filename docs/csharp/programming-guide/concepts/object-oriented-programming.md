---
title: Nesne odaklı programlama (C#)
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 541d1a2581a3241f35fc8478040c007b6581e3b2
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396683"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="868e1-102">Nesne odaklı programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="868e1-102">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="868e1-103">C#, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne odaklı programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="868e1-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="868e1-104">*Kapsülleme* , ilişkili özellikler, Yöntemler ve diğer üyelerin bir grubunun tek bir birim veya nesne olarak kabul edildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="868e1-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="868e1-105">*Devralma* , mevcut bir sınıfı temel alan yeni sınıflar oluşturma özelliğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="868e1-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="868e1-106">Çok *biçimlilik* , her bir sınıf farklı yollarla aynı özellikleri veya yöntemleri uyguladığından bile, birbirinin yerine kullanılabilecek birden fazla sınıfa sahip olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="868e1-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="868e1-107">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="868e1-107">Classes and objects</span></span>

<span data-ttu-id="868e1-108">Terimleri, sırasıyla nesnelerin *türünü* ve sınıfların *örneklerini* betimleyen *sınıf* ve *nesne* .</span><span class="sxs-lookup"><span data-stu-id="868e1-108">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="868e1-109">Bu nedenle, bir nesne oluşturma konusuna *örnek*oluşturma denir.</span><span class="sxs-lookup"><span data-stu-id="868e1-109">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="868e1-110">Şema benzerleme vurguladı kullanarak bir sınıf şeması bir şema, bir nesne ise bu şema tarafından oluşturulan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="868e1-110">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="868e1-111">Bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-111">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="868e1-112">C# Ayrıca, devralma veya çok biçimlilik için desteğe ihtiyacınız olmadığında yararlı olan *yapılar* olarak adlandırılan türler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="868e1-112">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span>

<span data-ttu-id="868e1-113">Bir yapı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-113">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="868e1-114">Daha fazla bilgi için [sınıf](../../language-reference/keywords/class.md) ve [Yapı](../../language-reference/builtin-types/struct.md) anahtar kelimeleri makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="868e1-114">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="868e1-115">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="868e1-115">Class members</span></span>

<span data-ttu-id="868e1-116">Her sınıf, sınıf verilerini tanımlayan özellikleri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasında iletişim sağlayan olayları içeren farklı *sınıf üyelerine* sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-116">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="868e1-117">Özellikler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="868e1-117">Properties and fields</span></span>

<span data-ttu-id="868e1-118">Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="868e1-118">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="868e1-119">Alanlar, uygun erişim değiştiricilerine bağlı olarak doğrudan okunabildikleri veya ayarlanabileceğinden değişkenlere benzer.</span><span class="sxs-lookup"><span data-stu-id="868e1-119">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="868e1-120">Sınıfın örnekleri içinden erişilebilen bir alan tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-120">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="868e1-121">Özellikler `get` ve `set` erişimcileri, değerlerin nasıl ayarlandığı veya döndürüldüğü üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="868e1-121">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="868e1-122">C#, özellik değerini depolamak için özel bir alan oluşturmanıza ya da bu alanı arka planda otomatik olarak oluşturan otomatik uygulanan özellikleri ve özellik yordamları için temel mantığı kullanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="868e1-122">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="868e1-123">Otomatik uygulanan bir özellik tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-123">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="868e1-124">Özellik değerini okumak ve yazmak için bazı ek işlemler gerçekleştirmeniz gerekiyorsa, özellik değerini depolamak için bir alan tanımlayın ve bunu depolamak ve almak için temel mantığı sağlayın:</span><span class="sxs-lookup"><span data-stu-id="868e1-124">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

<span data-ttu-id="868e1-125">Çoğu özelliğin, özellik değerini ayarlamak ve almak için yöntemleri ya da yordamları vardır.</span><span class="sxs-lookup"><span data-stu-id="868e1-125">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="868e1-126">Ancak, bunları değiştirilmesini veya okumayı kısıtlamak için salt okunurdur veya salt yazılır özellikler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="868e1-126">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="868e1-127">C# ' de, `get` veya `set` özellik yöntemini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="868e1-127">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="868e1-128">Ancak otomatik uygulanan özellikler salt yazılır olamaz.</span><span class="sxs-lookup"><span data-stu-id="868e1-128">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="868e1-129">Salt okuma otomatik uygulanmış özellikler, kapsayan sınıfın oluşturucuları içinde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-129">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="868e1-130">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="868e1-130">For more information, see:</span></span>

- [<span data-ttu-id="868e1-131">Al</span><span class="sxs-lookup"><span data-stu-id="868e1-131">get</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="868e1-132">set</span><span class="sxs-lookup"><span data-stu-id="868e1-132">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="868e1-133">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="868e1-133">Methods</span></span>

<span data-ttu-id="868e1-134">Bir *Yöntem* , bir nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="868e1-134">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="868e1-135">Bir sınıfın yöntemini tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-135">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="868e1-136">Bir sınıf, parametrelerin veya parametre türlerinin sayısında farklı olan aynı yöntemin çeşitli uygulamalarına veya *aşırı*yüküne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-136">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="868e1-137">Bir yöntemi aşırı yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="868e1-137">To overload a method:</span></span>

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

<span data-ttu-id="868e1-138">Çoğu durumda, bir sınıf tanımı içinde bir yöntemi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="868e1-138">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="868e1-139">Ancak C#, sınıfın gerçek tanımının dışında mevcut bir sınıfa Yöntemler eklemenize olanak tanıyan *genişletme yöntemlerini* de destekler.</span><span class="sxs-lookup"><span data-stu-id="868e1-139">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="868e1-140">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="868e1-140">For more information, see:</span></span>

- [<span data-ttu-id="868e1-141">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="868e1-141">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="868e1-142">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="868e1-142">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="868e1-143">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="868e1-143">Constructors</span></span>

<span data-ttu-id="868e1-144">Oluşturucular, belirli bir türden bir nesne oluşturulduğunda otomatik olarak yürütülen sınıf yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="868e1-144">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="868e1-145">Oluşturucular genellikle yeni nesnenin veri üyelerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="868e1-145">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="868e1-146">Bir Oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-146">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="868e1-147">Ayrıca, kurucudaki kod her zaman bir sınıftaki diğer koddan önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="868e1-147">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="868e1-148">Ancak, başka bir yöntemle aynı şekilde birden çok Oluşturucu aşırı yüklemesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="868e1-148">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="868e1-149">Bir sınıf için bir Oluşturucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-149">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="868e1-150">Daha fazla bilgi için bkz. [oluşturucular](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="868e1-150">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="868e1-151">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="868e1-151">Finalizers</span></span>

<span data-ttu-id="868e1-152">Sonlandırıcı, sınıf örneklerinin çıkarılması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="868e1-152">A finalizer is used to destruct instances of classes.</span></span> <span data-ttu-id="868e1-153">.NET Framework, çöp toplayıcı uygulamanızdaki yönetilen nesneler için bellek ayırmayı ve serbest bırakma işlemini otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="868e1-153">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="868e1-154">Ancak, uygulamanızın oluşturduğu yönetilmeyen kaynakları temizlemek için sonlandırıcılardan yine de ihtiyacınız olabilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-154">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="868e1-155">Bir sınıf için yalnızca bir Sonlandırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-155">There can be only one finalizer for a class.</span></span>

<span data-ttu-id="868e1-156">.NET Framework sonlandırıcılar ve çöp toplama hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="868e1-156">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="868e1-157">Olaylar</span><span class="sxs-lookup"><span data-stu-id="868e1-157">Events</span></span>

<span data-ttu-id="868e1-158">Olaylar, bir sınıf ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="868e1-158">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="868e1-159">Olayı gönderen (veya Başlatan) sınıf *Yayımcı* olarak adlandırılır ve olayı alan (veya işleyen) sınıflar *aboneler*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="868e1-159">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="868e1-160">Olaylar, nasıl oluşturulur ve işlenir hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="868e1-160">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="868e1-161">Bir sınıfında bir olay bildirmek için [Event](../../language-reference/keywords/event.md) anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="868e1-161">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>
- <span data-ttu-id="868e1-162">Bir olayı yükseltmek için olay temsilcisini çağırın.</span><span class="sxs-lookup"><span data-stu-id="868e1-162">To raise an event, invoke the event delegate.</span></span>
- <span data-ttu-id="868e1-163">Bir olaya abone olmak için `+=` işlecini kullanın; bir olayın aboneliğini kaldırmak için `-=` işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="868e1-163">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="868e1-164">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="868e1-164">Nested classes</span></span>

<span data-ttu-id="868e1-165">Başka bir sınıf içinde tanımlı bir sınıf *iç içe*çağırılır.</span><span class="sxs-lookup"><span data-stu-id="868e1-165">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="868e1-166">Varsayılan olarak, iç içe yerleştirilmiş sınıf özeldir.</span><span class="sxs-lookup"><span data-stu-id="868e1-166">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="868e1-167">İç içe yerleştirilmiş sınıfın bir örneğini oluşturmak için, container sınıfının adını ve ardından nokta ve ardından iç içe geçmiş sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="868e1-167">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="868e1-168">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="868e1-168">Access modifiers and access levels</span></span>

<span data-ttu-id="868e1-169">Tüm sınıflar ve sınıf üyeleri, *erişim değiştiricilerini*kullanarak diğer sınıflara hangi erişim düzeyini sundukları belirler.</span><span class="sxs-lookup"><span data-stu-id="868e1-169">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="868e1-170">Aşağıdaki erişim değiştiriciler kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="868e1-170">The following access modifiers are available:</span></span>

| <span data-ttu-id="868e1-171">C# değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="868e1-171">C# Modifier</span></span> | <span data-ttu-id="868e1-172">Tanım</span><span class="sxs-lookup"><span data-stu-id="868e1-172">Definition</span></span> |
|--|--|
| [<span data-ttu-id="868e1-173">public</span><span class="sxs-lookup"><span data-stu-id="868e1-173">public</span></span>](../../language-reference/keywords/public.md) | <span data-ttu-id="868e1-174">Türe veya üyeye aynı derlemedeki veya buna başvuran başka bir derlemede bir veya daha fazla kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-174">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> |
| [<span data-ttu-id="868e1-175">private</span><span class="sxs-lookup"><span data-stu-id="868e1-175">private</span></span>](../../language-reference/keywords/private.md) | <span data-ttu-id="868e1-176">Türe veya üyeye yalnızca aynı sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-176">The type or member can only be accessed by code in the same class.</span></span> |
| [<span data-ttu-id="868e1-177">protected</span><span class="sxs-lookup"><span data-stu-id="868e1-177">protected</span></span>](../../language-reference/keywords/protected.md) | <span data-ttu-id="868e1-178">Türe veya üyeye yalnızca aynı sınıftaki veya türetilmiş bir sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-178">The type or member can only be accessed by code in the same class or in a derived class.</span></span> |
| [<span data-ttu-id="868e1-179">internal</span><span class="sxs-lookup"><span data-stu-id="868e1-179">internal</span></span>](../../language-reference/keywords/internal.md) | <span data-ttu-id="868e1-180">Türe veya üyeye aynı derlemedeki kod tarafından erişilebilir, ancak başka bir derlemeden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-180">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span> |
| [<span data-ttu-id="868e1-181">protected internal</span><span class="sxs-lookup"><span data-stu-id="868e1-181">protected internal</span></span>](../../language-reference/keywords/protected-internal.md) | <span data-ttu-id="868e1-182">Türe veya üyeye aynı derlemedeki herhangi bir kod ya da başka bir derlemedeki türetilmiş bir sınıf tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-182">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span> |
| [<span data-ttu-id="868e1-183">private protected</span><span class="sxs-lookup"><span data-stu-id="868e1-183">private protected</span></span>](../../language-reference/keywords/private-protected.md) | <span data-ttu-id="868e1-184">Türe veya üyeye aynı sınıftaki veya temel sınıf derlemesi içindeki türetilmiş bir sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-184">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span> |

<span data-ttu-id="868e1-185">Daha fazla bilgi için bkz. [erişim değiştiricileri](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="868e1-185">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="868e1-186">Sınıfları örnekleme</span><span class="sxs-lookup"><span data-stu-id="868e1-186">Instantiating classes</span></span>

<span data-ttu-id="868e1-187">Bir nesne oluşturmak için bir sınıf örneği oluşturmanız veya bir sınıf örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="868e1-187">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="868e1-188">Bir sınıfı örnekledikten sonra, örneğin özelliklerine ve alanlarına değerler atayabilir ve sınıf yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="868e1-188">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

<span data-ttu-id="868e1-189">Sınıf örnek oluşturma işlemi sırasında özelliklere değer atamak için, nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="868e1-189">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="868e1-190">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="868e1-190">For more information, see:</span></span>

- [<span data-ttu-id="868e1-191">New Işleci</span><span class="sxs-lookup"><span data-stu-id="868e1-191">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="868e1-192">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="868e1-192">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="868e1-193">Statik sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="868e1-193">Static Classes and Members</span></span>

<span data-ttu-id="868e1-194">Sınıfının statik üyesi, bir sınıfın tüm örnekleri tarafından paylaşılan bir özellik, yordam veya alandır.</span><span class="sxs-lookup"><span data-stu-id="868e1-194">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="868e1-195">Statik üye tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-195">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="868e1-196">Statik üyeye erişmek için, sınıfın adını bu sınıfın bir nesnesi oluşturmadan kullanın:</span><span class="sxs-lookup"><span data-stu-id="868e1-196">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="868e1-197">C# içindeki statik sınıflar yalnızca statik üyelere sahiptir ve örneklenemez.</span><span class="sxs-lookup"><span data-stu-id="868e1-197">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="868e1-198">Statik Üyeler ayrıca statik olmayan özelliklere, alanlara veya yöntemlere erişemez</span><span class="sxs-lookup"><span data-stu-id="868e1-198">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="868e1-199">Daha fazla bilgi için bkz: [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="868e1-199">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="868e1-200">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="868e1-200">Anonymous types</span></span>

<span data-ttu-id="868e1-201">Anonim türler, veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="868e1-201">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="868e1-202">Bunun yerine, derleyici sizin için bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="868e1-202">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="868e1-203">Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="868e1-203">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="868e1-204">Anonim türün bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-204">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="868e1-205">Daha fazla bilgi için bkz: [anonim türler](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="868e1-205">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="868e1-206">Devralma</span><span class="sxs-lookup"><span data-stu-id="868e1-206">Inheritance</span></span>

<span data-ttu-id="868e1-207">Devralma, başka bir sınıfta tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni bir sınıf oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="868e1-207">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="868e1-208">Üyeleri devralınmış olan sınıfa *temel sınıf*denir ve bu üyeleri devralan sınıfa *türetilmiş sınıf*denir.</span><span class="sxs-lookup"><span data-stu-id="868e1-208">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="868e1-209">Ancak, C# ' deki tüm sınıflar dolaylı olarak <xref:System.Object> .NET sınıf hiyerarşisini destekleyen sınıftan devralınır ve tüm sınıflara alt düzey hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="868e1-209">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="868e1-210">C# birden fazla devralmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="868e1-210">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="868e1-211">Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="868e1-211">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="868e1-212">Temel sınıftan devralması için:</span><span class="sxs-lookup"><span data-stu-id="868e1-212">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass { }
```

<span data-ttu-id="868e1-213">Varsayılan olarak, tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-213">By default all classes can be inherited.</span></span> <span data-ttu-id="868e1-214">Ancak, bir sınıfın temel sınıf olarak kullanılması gerekip gerekmediğini belirtebilir veya yalnızca temel sınıf olarak kullanılabilecek bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="868e1-214">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="868e1-215">Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="868e1-215">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="868e1-216">Bir sınıfın yalnızca temel sınıf olarak kullanılabileceğini ve örneklenemez olduğunu belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="868e1-216">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="868e1-217">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="868e1-217">For more information, see:</span></span>

- [<span data-ttu-id="868e1-218">sealed</span><span class="sxs-lookup"><span data-stu-id="868e1-218">sealed</span></span>](../../language-reference/keywords/sealed.md)
- [<span data-ttu-id="868e1-219">abstract</span><span class="sxs-lookup"><span data-stu-id="868e1-219">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="868e1-220">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="868e1-220">Overriding Members</span></span>

<span data-ttu-id="868e1-221">Varsayılan olarak, türetilmiş bir sınıf kendi temel sınıfından tüm üyeleri devralır.</span><span class="sxs-lookup"><span data-stu-id="868e1-221">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="868e1-222">Devralınan üyenin davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="868e1-222">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="868e1-223">Diğer bir deyişle, türetilmiş sınıfta yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="868e1-223">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="868e1-224">Özelliklerin ve yöntemlerin nasıl geçersiz kılınabileceğini denetlemek için aşağıdaki değiştiriciler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="868e1-224">The following modifiers are used to control how properties and methods are overridden:</span></span>

| <span data-ttu-id="868e1-225">C# değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="868e1-225">C# Modifier</span></span> | <span data-ttu-id="868e1-226">Tanım</span><span class="sxs-lookup"><span data-stu-id="868e1-226">Definition</span></span> |
|--|--|
| [<span data-ttu-id="868e1-227">virtual</span><span class="sxs-lookup"><span data-stu-id="868e1-227">virtual</span></span>](../../language-reference/keywords/virtual.md) | <span data-ttu-id="868e1-228">Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="868e1-228">Allows a class member to be overridden in a derived class.</span></span> |
| [<span data-ttu-id="868e1-229">override</span><span class="sxs-lookup"><span data-stu-id="868e1-229">override</span></span>](../../language-reference/keywords/override.md) | <span data-ttu-id="868e1-230">Temel sınıfta tanımlanan bir sanal (geçersiz kılınabilir) üyeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="868e1-230">Overrides a virtual (overridable) member defined in the base class.</span></span> |
| [<span data-ttu-id="868e1-231">abstract</span><span class="sxs-lookup"><span data-stu-id="868e1-231">abstract</span></span>](../../language-reference/keywords/abstract.md) | <span data-ttu-id="868e1-232">Türetilmiş sınıfta bir sınıf üyesinin geçersiz kılınmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="868e1-232">Requires that a class member to be overridden in the derived class.</span></span> |
| [<span data-ttu-id="868e1-233">new Değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="868e1-233">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md) | <span data-ttu-id="868e1-234">Temel sınıftan devralınan bir üyeyi gizler</span><span class="sxs-lookup"><span data-stu-id="868e1-234">Hides a member inherited from a base class</span></span> |

## <a name="interfaces"></a><span data-ttu-id="868e1-235">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="868e1-235">Interfaces</span></span>

<span data-ttu-id="868e1-236">Sınıflar gibi arabirimler, özellikler, Yöntemler ve olaylar kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="868e1-236">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="868e1-237">Ancak sınıfların aksine arabirimler uygulama sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="868e1-237">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="868e1-238">Sınıflar tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="868e1-238">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="868e1-239">Arabirim, bir arabirimi uygulayan bir sınıfın, bu arabirimin her yönünü tam olarak tanımlandığı gibi uygulaması gerektiğini belirten bir sözleşmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="868e1-239">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="868e1-240">Bir arabirim tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-240">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

<span data-ttu-id="868e1-241">Bir sınıfa bir arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-241">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="868e1-242">Daha fazla bilgi için [arabirim](../../language-reference/keywords/interface.md) anahtar sözcüğünün [arabirimler](../interfaces/index.md) ve dil başvurusu makalesindeki Programlama Kılavuzu makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="868e1-242">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="868e1-243">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="868e1-243">Generics</span></span>

<span data-ttu-id="868e1-244">.NET Framework sınıflar, yapılar, arabirimler ve Yöntemler, depolayabilecekleri veya kullanabileceği nesne türlerini tanımlayan *tür parametreleri* içerebilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-244">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="868e1-245">En yaygın genel türler örneği, bir koleksiyonda depolanacak nesne türlerini belirtebileceğiniz bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="868e1-245">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="868e1-246">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-246">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="868e1-247">Genel sınıfın bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-247">To create an instance of a generic class:</span></span>

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="868e1-248">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="868e1-248">For more information, see:</span></span>

- [<span data-ttu-id="868e1-249">.NET içindeki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="868e1-249">Generics in .NET</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="868e1-250">Genel türler-C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="868e1-250">Generics - C# Programming Guide</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="868e1-251">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="868e1-251">Delegates</span></span>

<span data-ttu-id="868e1-252">*Temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu imzaya sahip herhangi bir yönteme başvuru sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="868e1-252">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="868e1-253">Yöntemi temsilci aracılığıyla çağırabilir (veya çağırabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="868e1-253">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="868e1-254">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="868e1-254">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="868e1-255">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="868e1-255">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="868e1-256">Olay İşlemede temsilciler kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="868e1-256">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="868e1-257">Bir temsilci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-257">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="868e1-258">Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="868e1-258">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void SampleMethod(string message)
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

<span data-ttu-id="868e1-259">Daha fazla bilgi için [temsilci](../../language-reference/builtin-types/reference-types.md) anahtar kelimesiyle ilgili [Temsilciler](../delegates/index.md) ve dil başvurusu makalesindeki Programlama Kılavuzu makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="868e1-259">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="868e1-260">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="868e1-260">See also</span></span>

- [<span data-ttu-id="868e1-261">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="868e1-261">C# Programming Guide</span></span>](../index.md)
