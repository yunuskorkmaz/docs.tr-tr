---
title: Nesne odaklı programlama (C#)
description: C#; soyutlama, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne odaklı programlama için tam destek sağlar.
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 0c5495aefad73a2916ad6e2bd2bf3701d0868f24
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302821"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="de4b0-103">Nesne odaklı programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="de4b0-103">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="de4b0-104">C#; soyutlama, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne odaklı programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="de4b0-104">C# provides full support for object-oriented programming including abstraction, encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="de4b0-105">*Soyutlama* , tür tüketicilerden gereksiz ayrıntıların gizlenmesi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-105">*Abstraction* means hiding the unnecessary details from type consumers.</span></span>
- <span data-ttu-id="de4b0-106">*Kapsülleme* , ilişkili özellikler, Yöntemler ve diğer üyelerin bir grubunun tek bir birim veya nesne olarak kabul edildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-106">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="de4b0-107">*Devralma* , mevcut bir sınıfı temel alan yeni sınıflar oluşturma özelliğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="de4b0-107">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="de4b0-108">Çok *biçimlilik* , her bir sınıf farklı yollarla aynı özellikleri veya yöntemleri uyguladığından bile, birbirinin yerine kullanılabilecek birden fazla sınıfa sahip olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-108">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="de4b0-109">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="de4b0-109">Classes and objects</span></span>

<span data-ttu-id="de4b0-110">Terimleri, sırasıyla nesnelerin *türünü* ve sınıfların *örneklerini* betimleyen *sınıf* ve *nesne* .</span><span class="sxs-lookup"><span data-stu-id="de4b0-110">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="de4b0-111">Bu nedenle, bir nesne oluşturma konusuna *örnek*oluşturma denir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-111">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="de4b0-112">Şema benzerleme vurguladı kullanarak bir sınıf şeması bir şema, bir nesne ise bu şema tarafından oluşturulan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="de4b0-112">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="de4b0-113">Bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-113">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="de4b0-114">C# Ayrıca, devralma veya çok biçimlilik için desteğe ihtiyacınız olmadığında yararlı olan *yapılar* olarak adlandırılan türler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="de4b0-114">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span> <span data-ttu-id="de4b0-115">Daha fazla bilgi için bkz. [sınıf ve yapı arasında seçim yapma](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span><span class="sxs-lookup"><span data-stu-id="de4b0-115">For more information, see [Choosing between class and struct](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span></span>

<span data-ttu-id="de4b0-116">Bir yapı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-116">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="de4b0-117">Daha fazla bilgi için [sınıf](../../language-reference/keywords/class.md) ve [Yapı](../../language-reference/builtin-types/struct.md) anahtar kelimeleri makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="de4b0-117">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="de4b0-118">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="de4b0-118">Class members</span></span>

<span data-ttu-id="de4b0-119">Her sınıf, sınıf verilerini tanımlayan özellikleri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasında iletişim sağlayan olayları içeren farklı *sınıf üyelerine* sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-119">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="de4b0-120">Özellikler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="de4b0-120">Properties and fields</span></span>

<span data-ttu-id="de4b0-121">Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de4b0-121">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="de4b0-122">Alanlar, uygun erişim değiştiricilerine bağlı olarak doğrudan okunabildikleri veya ayarlanabileceğinden değişkenlere benzer.</span><span class="sxs-lookup"><span data-stu-id="de4b0-122">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="de4b0-123">Sınıfın örnekleri içinden erişilebilen bir alan tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-123">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="de4b0-124">Özellikler `get` ve `set` erişimcileri, değerlerin nasıl ayarlandığı veya döndürüldüğü üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="de4b0-124">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="de4b0-125">C#, özellik değerini depolamak için özel bir alan oluşturmanıza ya da bu alanı arka planda otomatik olarak oluşturan otomatik uygulanan özellikleri ve özellik yordamları için temel mantığı kullanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="de4b0-125">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="de4b0-126">Otomatik uygulanan bir özellik tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-126">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="de4b0-127">Özellik değerini okumak ve yazmak için bazı ek işlemler gerçekleştirmeniz gerekiyorsa, özellik değerini depolamak için bir alan tanımlayın ve bunu depolamak ve almak için temel mantığı sağlayın:</span><span class="sxs-lookup"><span data-stu-id="de4b0-127">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="de4b0-128">Çoğu özelliğin, özellik değerini ayarlamak ve almak için yöntemleri ya da yordamları vardır.</span><span class="sxs-lookup"><span data-stu-id="de4b0-128">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="de4b0-129">Ancak, bunları değiştirilmesini veya okumayı kısıtlamak için salt okunurdur veya salt yazılır özellikler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-129">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="de4b0-130">C# ' de, `get` veya `set` özellik yöntemini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-130">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="de4b0-131">Ancak otomatik uygulanan özellikler salt yazılır olamaz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-131">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="de4b0-132">Salt okuma otomatik uygulanmış özellikler, kapsayan sınıfın oluşturucuları içinde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-132">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="de4b0-133">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-133">For more information, see:</span></span>

- [<span data-ttu-id="de4b0-134">Al</span><span class="sxs-lookup"><span data-stu-id="de4b0-134">get</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="de4b0-135">kurmak</span><span class="sxs-lookup"><span data-stu-id="de4b0-135">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="de4b0-136">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="de4b0-136">Methods</span></span>

<span data-ttu-id="de4b0-137">Bir *Yöntem* , bir nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-137">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="de4b0-138">Bir sınıfın yöntemini tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-138">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="de4b0-139">Bir sınıf, parametrelerin veya parametre türlerinin sayısında farklı olan aynı yöntemin çeşitli uygulamalarına veya *aşırı*yüküne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-139">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="de4b0-140">Bir yöntemi aşırı yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-140">To overload a method:</span></span>

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

<span data-ttu-id="de4b0-141">Çoğu durumda, bir sınıf tanımı içinde bir yöntemi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-141">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="de4b0-142">Ancak C#, sınıfın gerçek tanımının dışında mevcut bir sınıfa Yöntemler eklemenize olanak tanıyan *genişletme yöntemlerini* de destekler.</span><span class="sxs-lookup"><span data-stu-id="de4b0-142">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="de4b0-143">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-143">For more information, see:</span></span>

- [<span data-ttu-id="de4b0-144">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="de4b0-144">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="de4b0-145">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="de4b0-145">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="de4b0-146">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="de4b0-146">Constructors</span></span>

<span data-ttu-id="de4b0-147">Oluşturucular, belirli bir türden bir nesne oluşturulduğunda otomatik olarak yürütülen sınıf yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-147">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="de4b0-148">Oluşturucular genellikle yeni nesnenin veri üyelerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="de4b0-148">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="de4b0-149">Bir Oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-149">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="de4b0-150">Ayrıca, kurucudaki kod her zaman bir sınıftaki diğer koddan önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="de4b0-150">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="de4b0-151">Ancak, başka bir yöntemle aynı şekilde birden çok Oluşturucu aşırı yüklemesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-151">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="de4b0-152">Bir sınıf için bir Oluşturucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-152">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="de4b0-153">Daha fazla bilgi için bkz. [oluşturucular](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="de4b0-153">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="de4b0-154">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="de4b0-154">Finalizers</span></span>

<span data-ttu-id="de4b0-155">Sonlandırıcı, sınıf örneklerinin çıkarılması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de4b0-155">A finalizer is used to destruct instances of classes.</span></span> <span data-ttu-id="de4b0-156">.NET sürümünde çöp toplayıcı, uygulamanızdaki yönetilen nesneler için bellek ayırmayı ve serbest bırakma işlemini otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-156">In .NET, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="de4b0-157">Ancak, uygulamanızın oluşturduğu yönetilmeyen kaynakları temizlemek için sonlandırıcılardan yine de ihtiyacınız olabilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-157">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="de4b0-158">Bir sınıf için yalnızca bir Sonlandırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-158">There can be only one finalizer for a class.</span></span>

<span data-ttu-id="de4b0-159">.NET 'teki sonlandırıcılar ve çöp toplama hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="de4b0-159">For more information about finalizers and garbage collection in .NET, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="de4b0-160">Olaylar</span><span class="sxs-lookup"><span data-stu-id="de4b0-160">Events</span></span>

<span data-ttu-id="de4b0-161">Olaylar, bir sınıf ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="de4b0-161">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="de4b0-162">Olayı gönderen (veya Başlatan) sınıf *Yayımcı* olarak adlandırılır ve olayı alan (veya işleyen) sınıflar *aboneler*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="de4b0-162">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="de4b0-163">Olaylar, nasıl oluşturulur ve işlenir hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="de4b0-163">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="de4b0-164">Bir sınıfında bir olay bildirmek için [Event](../../language-reference/keywords/event.md) anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="de4b0-164">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>
- <span data-ttu-id="de4b0-165">Bir olayı yükseltmek için olay temsilcisini çağırın.</span><span class="sxs-lookup"><span data-stu-id="de4b0-165">To raise an event, invoke the event delegate.</span></span>
- <span data-ttu-id="de4b0-166">Bir olaya abone olmak için `+=` işlecini kullanın; bir olayın aboneliğini kaldırmak için `-=` işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="de4b0-166">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="de4b0-167">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="de4b0-167">Nested classes</span></span>

<span data-ttu-id="de4b0-168">Başka bir sınıf içinde tanımlı bir sınıf *iç içe*çağırılır.</span><span class="sxs-lookup"><span data-stu-id="de4b0-168">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="de4b0-169">Varsayılan olarak, iç içe yerleştirilmiş sınıf özeldir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-169">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="de4b0-170">İç içe yerleştirilmiş sınıfın bir örneğini oluşturmak için, container sınıfının adını ve ardından nokta ve ardından iç içe geçmiş sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="de4b0-170">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="de4b0-171">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="de4b0-171">Access modifiers and access levels</span></span>

<span data-ttu-id="de4b0-172">Tüm sınıflar ve sınıf üyeleri, *erişim değiştiricilerini*kullanarak diğer sınıflara hangi erişim düzeyini sundukları belirler.</span><span class="sxs-lookup"><span data-stu-id="de4b0-172">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="de4b0-173">Aşağıdaki erişim değiştiriciler kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="de4b0-173">The following access modifiers are available:</span></span>

| <span data-ttu-id="de4b0-174">C# değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="de4b0-174">C# Modifier</span></span> | <span data-ttu-id="de4b0-175">Tanım</span><span class="sxs-lookup"><span data-stu-id="de4b0-175">Definition</span></span> |
|--|--|
| [<span data-ttu-id="de4b0-176">genel</span><span class="sxs-lookup"><span data-stu-id="de4b0-176">public</span></span>](../../language-reference/keywords/public.md) | <span data-ttu-id="de4b0-177">Türe veya üyeye aynı derlemedeki veya buna başvuran başka bir derlemede bir veya daha fazla kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-177">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> |
| [<span data-ttu-id="de4b0-178">özelleştirme</span><span class="sxs-lookup"><span data-stu-id="de4b0-178">private</span></span>](../../language-reference/keywords/private.md) | <span data-ttu-id="de4b0-179">Türe veya üyeye yalnızca aynı sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-179">The type or member can only be accessed by code in the same class.</span></span> |
| [<span data-ttu-id="de4b0-180">protected</span><span class="sxs-lookup"><span data-stu-id="de4b0-180">protected</span></span>](../../language-reference/keywords/protected.md) | <span data-ttu-id="de4b0-181">Türe veya üyeye yalnızca aynı sınıftaki veya türetilmiş bir sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-181">The type or member can only be accessed by code in the same class or in a derived class.</span></span> |
| [<span data-ttu-id="de4b0-182">internal</span><span class="sxs-lookup"><span data-stu-id="de4b0-182">internal</span></span>](../../language-reference/keywords/internal.md) | <span data-ttu-id="de4b0-183">Türe veya üyeye aynı derlemedeki kod tarafından erişilebilir, ancak başka bir derlemeden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-183">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span> |
| [<span data-ttu-id="de4b0-184">protected internal</span><span class="sxs-lookup"><span data-stu-id="de4b0-184">protected internal</span></span>](../../language-reference/keywords/protected-internal.md) | <span data-ttu-id="de4b0-185">Türe veya üyeye aynı derlemedeki herhangi bir kod ya da başka bir derlemedeki türetilmiş bir sınıf tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-185">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span> |
| [<span data-ttu-id="de4b0-186">private protected</span><span class="sxs-lookup"><span data-stu-id="de4b0-186">private protected</span></span>](../../language-reference/keywords/private-protected.md) | <span data-ttu-id="de4b0-187">Türe veya üyeye aynı sınıftaki veya temel sınıf derlemesi içindeki türetilmiş bir sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-187">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span> |

<span data-ttu-id="de4b0-188">Daha fazla bilgi için bkz. [erişim değiştiricileri](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="de4b0-188">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="de4b0-189">Sınıfları örnekleme</span><span class="sxs-lookup"><span data-stu-id="de4b0-189">Instantiating classes</span></span>

<span data-ttu-id="de4b0-190">Bir nesne oluşturmak için bir sınıf örneği oluşturmanız veya bir sınıf örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-190">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="de4b0-191">Bir sınıfı örnekledikten sonra, örneğin özelliklerine ve alanlarına değerler atayabilir ve sınıf yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-191">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

<span data-ttu-id="de4b0-192">Sınıf örnek oluşturma işlemi sırasında özelliklere değer atamak için, nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="de4b0-192">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="de4b0-193">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-193">For more information, see:</span></span>

- [<span data-ttu-id="de4b0-194">New Işleci</span><span class="sxs-lookup"><span data-stu-id="de4b0-194">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="de4b0-195">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="de4b0-195">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="de4b0-196">Statik sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="de4b0-196">Static Classes and Members</span></span>

<span data-ttu-id="de4b0-197">Sınıfının statik üyesi, bir sınıfın tüm örnekleri tarafından paylaşılan bir özellik, yordam veya alandır.</span><span class="sxs-lookup"><span data-stu-id="de4b0-197">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="de4b0-198">Statik üye tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-198">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="de4b0-199">Statik üyeye erişmek için, sınıfın adını bu sınıfın bir nesnesi oluşturmadan kullanın:</span><span class="sxs-lookup"><span data-stu-id="de4b0-199">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="de4b0-200">C# içindeki statik sınıflar yalnızca statik üyelere sahiptir ve örneklenemez.</span><span class="sxs-lookup"><span data-stu-id="de4b0-200">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="de4b0-201">Statik Üyeler ayrıca statik olmayan özelliklere, alanlara veya yöntemlere erişemez</span><span class="sxs-lookup"><span data-stu-id="de4b0-201">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="de4b0-202">Daha fazla bilgi için bkz: [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="de4b0-202">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="de4b0-203">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="de4b0-203">Anonymous types</span></span>

<span data-ttu-id="de4b0-204">Anonim türler, veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="de4b0-204">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="de4b0-205">Bunun yerine, derleyici sizin için bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de4b0-205">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="de4b0-206">Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-206">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="de4b0-207">Anonim türün bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-207">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="de4b0-208">Daha fazla bilgi için bkz: [anonim türler](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="de4b0-208">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="de4b0-209">Devralma</span><span class="sxs-lookup"><span data-stu-id="de4b0-209">Inheritance</span></span>

<span data-ttu-id="de4b0-210">Devralma, başka bir sınıfta tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni bir sınıf oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="de4b0-210">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="de4b0-211">Üyeleri devralınmış olan sınıfa *temel sınıf*denir ve bu üyeleri devralan sınıfa *türetilmiş sınıf*denir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-211">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="de4b0-212">Ancak, C# ' deki tüm sınıflar dolaylı olarak <xref:System.Object> .NET sınıf hiyerarşisini destekleyen sınıftan devralınır ve tüm sınıflara alt düzey hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="de4b0-212">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="de4b0-213">C# birden fazla devralmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="de4b0-213">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="de4b0-214">Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-214">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="de4b0-215">Temel sınıftan devralması için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-215">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass { }
```

<span data-ttu-id="de4b0-216">Varsayılan olarak, tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-216">By default all classes can be inherited.</span></span> <span data-ttu-id="de4b0-217">Ancak, bir sınıfın temel sınıf olarak kullanılması gerekip gerekmediğini belirtebilir veya yalnızca temel sınıf olarak kullanılabilecek bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-217">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="de4b0-218">Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-218">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="de4b0-219">Bir sınıfın yalnızca temel sınıf olarak kullanılabileceğini ve örneklenemez olduğunu belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-219">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="de4b0-220">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-220">For more information, see:</span></span>

- [<span data-ttu-id="de4b0-221">sealed</span><span class="sxs-lookup"><span data-stu-id="de4b0-221">sealed</span></span>](../../language-reference/keywords/sealed.md)
- [<span data-ttu-id="de4b0-222">Soyut</span><span class="sxs-lookup"><span data-stu-id="de4b0-222">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="de4b0-223">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="de4b0-223">Overriding Members</span></span>

<span data-ttu-id="de4b0-224">Varsayılan olarak, türetilmiş bir sınıf kendi temel sınıfından tüm üyeleri devralır.</span><span class="sxs-lookup"><span data-stu-id="de4b0-224">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="de4b0-225">Devralınan üyenin davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-225">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="de4b0-226">Diğer bir deyişle, türetilmiş sınıfta yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-226">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="de4b0-227">Özelliklerin ve yöntemlerin nasıl geçersiz kılınabileceğini denetlemek için aşağıdaki değiştiriciler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="de4b0-227">The following modifiers are used to control how properties and methods are overridden:</span></span>

| <span data-ttu-id="de4b0-228">C# değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="de4b0-228">C# Modifier</span></span> | <span data-ttu-id="de4b0-229">Tanım</span><span class="sxs-lookup"><span data-stu-id="de4b0-229">Definition</span></span> |
|--|--|
| [<span data-ttu-id="de4b0-230">sanal</span><span class="sxs-lookup"><span data-stu-id="de4b0-230">virtual</span></span>](../../language-reference/keywords/virtual.md) | <span data-ttu-id="de4b0-231">Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-231">Allows a class member to be overridden in a derived class.</span></span> |
| [<span data-ttu-id="de4b0-232">override</span><span class="sxs-lookup"><span data-stu-id="de4b0-232">override</span></span>](../../language-reference/keywords/override.md) | <span data-ttu-id="de4b0-233">Temel sınıfta tanımlanan bir sanal (geçersiz kılınabilir) üyeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="de4b0-233">Overrides a virtual (overridable) member defined in the base class.</span></span> |
| [<span data-ttu-id="de4b0-234">Soyut</span><span class="sxs-lookup"><span data-stu-id="de4b0-234">abstract</span></span>](../../language-reference/keywords/abstract.md) | <span data-ttu-id="de4b0-235">Türetilmiş sınıfta bir sınıf üyesinin geçersiz kılınmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-235">Requires that a class member to be overridden in the derived class.</span></span> |
| [<span data-ttu-id="de4b0-236">new Değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="de4b0-236">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md) | <span data-ttu-id="de4b0-237">Temel sınıftan devralınan bir üyeyi gizler</span><span class="sxs-lookup"><span data-stu-id="de4b0-237">Hides a member inherited from a base class</span></span> |

## <a name="interfaces"></a><span data-ttu-id="de4b0-238">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="de4b0-238">Interfaces</span></span>

<span data-ttu-id="de4b0-239">Sınıflar gibi arabirimler, özellikler, Yöntemler ve olaylar kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="de4b0-239">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="de4b0-240">Ancak sınıfların aksine arabirimler uygulama sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-240">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="de4b0-241">Sınıflar tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="de4b0-241">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="de4b0-242">Arabirim, bir arabirimi uygulayan bir sınıfın, bu arabirimin her yönünü tam olarak tanımlandığı gibi uygulaması gerektiğini belirten bir sözleşmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de4b0-242">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="de4b0-243">Bir arabirim tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-243">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

<span data-ttu-id="de4b0-244">Bir sınıfa bir arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-244">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="de4b0-245">Daha fazla bilgi için [arabirim](../../language-reference/keywords/interface.md) anahtar sözcüğünün [arabirimler](../interfaces/index.md) ve dil başvurusu makalesindeki Programlama Kılavuzu makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="de4b0-245">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="de4b0-246">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="de4b0-246">Generics</span></span>

<span data-ttu-id="de4b0-247">.NET 'teki sınıflar, yapılar, arabirimler ve Yöntemler, depolayabilecekleri veya kullanabileceği nesne türlerini tanımlayan *tür parametreleri* içerebilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-247">Classes, structures, interfaces, and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="de4b0-248">En yaygın genel türler örneği, bir koleksiyonda depolanacak nesne türlerini belirtebileceğiniz bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="de4b0-248">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="de4b0-249">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-249">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="de4b0-250">Genel sınıfın bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-250">To create an instance of a generic class:</span></span>

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="de4b0-251">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-251">For more information, see:</span></span>

- [<span data-ttu-id="de4b0-252">.NET içindeki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="de4b0-252">Generics in .NET</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="de4b0-253">Genel türler-C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="de4b0-253">Generics - C# Programming Guide</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="de4b0-254">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="de4b0-254">Delegates</span></span>

<span data-ttu-id="de4b0-255">*Temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu imzaya sahip herhangi bir yönteme başvuru sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-255">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="de4b0-256">Yöntemi temsilci aracılığıyla çağırabilir (veya çağırabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="de4b0-256">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="de4b0-257">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de4b0-257">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="de4b0-258">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="de4b0-258">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="de4b0-259">Olay İşlemede temsilciler kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="de4b0-259">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="de4b0-260">Bir temsilci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-260">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="de4b0-261">Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="de4b0-261">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="de4b0-262">Daha fazla bilgi için [temsilci](../../language-reference/builtin-types/reference-types.md) anahtar kelimesiyle ilgili [Temsilciler](../delegates/index.md) ve dil başvurusu makalesindeki Programlama Kılavuzu makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="de4b0-262">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="de4b0-263">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de4b0-263">See also</span></span>

- [<span data-ttu-id="de4b0-264">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="de4b0-264">C# Programming Guide</span></span>](../index.md)
