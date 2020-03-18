---
title: Nesne Yönelimli Programlama (C#)
ms.date: 02/08/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 01d6f55bf0752f902f351675c4596abbb8ac85c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627896"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="d1bfc-102">Nesne Yönelimli programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="d1bfc-102">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="d1bfc-103">C#, kapsülleme, kalıtım ve çok biçimlilik gibi nesne yönelimli programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="d1bfc-104">*Kapsülleme,* ilgili özellikler, yöntemler ve diğer üyelerden oluşan bir grubun tek bir birim veya nesne olarak kabul edilsi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="d1bfc-105">*Devralma,* varolan bir sınıfa dayalı yeni sınıflar oluşturma yeteneğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="d1bfc-106">*Çok biçimlilik,* her sınıf aynı özellikleri veya yöntemleri farklı şekillerde uygulasa bile, birbirinin yerine kullanılabilecek birden çok sınıfa sahip olabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="d1bfc-107">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="d1bfc-107">Classes and objects</span></span>

<span data-ttu-id="d1bfc-108">Terim *sınıf* ve *nesne,* sırasıyla nesnelerin *türünü* ve sınıf *örneklerini* açıklar.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-108">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="d1bfc-109">Yani, bir nesne oluşturma eylemine *anlık hareket*denir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-109">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="d1bfc-110">Plan benzetmesini kullanarak, sınıf bir plandır ve bir nesne de bu plandan yapılmış bir binadır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-110">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="d1bfc-111">Bir sınıfı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-111">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="d1bfc-112">C# ayrıca kalıtım veya çok biçimlilik için desteğe ihtiyacınız olmadığında yararlı olan *yapılar* olarak adlandırılan türleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-112">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span>

<span data-ttu-id="d1bfc-113">Bir yapıtanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-113">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="d1bfc-114">Daha fazla bilgi için [sınıf](../../language-reference/keywords/class.md) ve [yapı](../../language-reference/builtin-types/struct.md) anahtar kelimeleri hakkındaki makalelere bakın.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-114">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="d1bfc-115">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="d1bfc-115">Class members</span></span>

<span data-ttu-id="d1bfc-116">Her *sınıfın,* sınıf verilerini açıklayan özellikleri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasında iletişim sağlayan olayları içeren farklı sınıf üyeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-116">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="d1bfc-117">Özellikler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="d1bfc-117">Properties and fields</span></span>

<span data-ttu-id="d1bfc-118">Alanlar ve özellikler, nesnenin içerdiği bilgileri temsil ediyor.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-118">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="d1bfc-119">Alanlar, uygulanabilir erişim değiştiricilere tabi olarak doğrudan okunabildikleri veya ayarlanabildikleri için değişkenler gibidir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-119">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="d1bfc-120">Sınıfın örnekleri içinden erişilebilen bir alanı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-120">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="d1bfc-121">Özelliklerin `get` `set` ve erişime sahip olan ve değerlerin nasıl ayarlandığı veya döndürüldek hakkında daha fazla denetim sağlayan.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-121">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="d1bfc-122">C# özellik değerini depolamak için özel bir alan oluşturmanıza veya bu alanı otomatik olarak arka planda oluşturan otomatik olarak uygulanan özellikleri kullanmanıza ve özellik yordamları için temel mantığı sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-122">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="d1bfc-123">Otomatik olarak uygulanan bir özelliği tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-123">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="d1bfc-124">Özellik değerini okumak ve yazmak için bazı ek işlemler gerçekleştirmeniz gerekiyorsa, özellik değerini depolamak için bir alan tanımlayın ve depolamak ve almak için temel mantığı sağlayın:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-124">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="d1bfc-125">Çoğu özelliğin hem ayarlayıp hem de özellik değerini almak için yöntemleri veya yordamları vardır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-125">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="d1bfc-126">Ancak, değiştirilmelerini veya okunmasını kısıtlamak için salt okunur veya yalnızca yazma özellikleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-126">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="d1bfc-127">C#'da, özelliği veya `get` `set` özelliği yöntemini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-127">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="d1bfc-128">Ancak, otomatik olarak uygulanan özellikler yalnızca yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-128">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="d1bfc-129">Yalnızca okunan otomatik uygulanan özellikler, içeren sınıfın oluşturucularında ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-129">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="d1bfc-130">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-130">For more information, see:</span></span>

- [<span data-ttu-id="d1bfc-131">get</span><span class="sxs-lookup"><span data-stu-id="d1bfc-131">get</span></span>](../../language-reference/keywords/get.md)

- [<span data-ttu-id="d1bfc-132">Ayarlamak</span><span class="sxs-lookup"><span data-stu-id="d1bfc-132">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="d1bfc-133">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d1bfc-133">Methods</span></span>

<span data-ttu-id="d1bfc-134">*Yöntem,* bir nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-134">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="d1bfc-135">Bir sınıfın yöntemini tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-135">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="d1bfc-136">Bir sınıfın, parametre veya parametre türlerinin sayısında farklılık gösteren aynı yöntemin birkaç uygulaması veya *aşırı yüklemesi*olabilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-136">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="d1bfc-137">Bir yöntemi aşırı yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-137">To overload a method:</span></span>

```csharp
public int sampleMethod(string sampleParam) {}
public int sampleMethod(int sampleParam) {}
```

<span data-ttu-id="d1bfc-138">Çoğu durumda bir sınıf tanımı içinde bir yöntem bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-138">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="d1bfc-139">Ancak C# ayrıca, sınıfın gerçek tanımı dışında varolan bir sınıfa yöntem eklemenize olanak tanıyan *uzantı yöntemlerini* de destekler.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-139">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="d1bfc-140">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-140">For more information, see:</span></span>

- [<span data-ttu-id="d1bfc-141">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d1bfc-141">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="d1bfc-142">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="d1bfc-142">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="d1bfc-143">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="d1bfc-143">Constructors</span></span>

<span data-ttu-id="d1bfc-144">Oluşturucular, belirli bir türdeki bir nesne oluşturulduğunda otomatik olarak yürütülen sınıf yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-144">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="d1bfc-145">Oluşturucular genellikle yeni nesnenin veri üyelerini başlangıç olarak karşılarlar.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-145">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="d1bfc-146">Bir oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-146">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="d1bfc-147">Ayrıca, oluşturucudaki kod her zaman bir sınıftaki başka bir koddan önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-147">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="d1bfc-148">Ancak, birden çok oluşturucu başka bir yöntemle aynı şekilde aşırı yüklemeler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-148">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="d1bfc-149">Bir sınıf için bir oluşturucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-149">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="d1bfc-150">Daha fazla bilgi için [Constructors'a](../classes-and-structs/constructors.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-150">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="d1bfc-151">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="d1bfc-151">Finalizers</span></span>

<span data-ttu-id="d1bfc-152">Sonlandırıcılar sınıfların örneklerini yok etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-152">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="d1bfc-153">.NET Framework'de, çöp toplayıcı, uygulamanızdaki yönetilen nesneler için bellek tahsisini ve serbest bırakılmasını otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-153">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="d1bfc-154">Ancak, uygulamanızın oluşturduğu yönetilmeyen kaynakları temizlemek için yine de sonlandırıcılara ihtiyacınız olabilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-154">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="d1bfc-155">Bir ders için sadece bir finalizatör olabilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-155">There can be only one finalizers for a class.</span></span>

<span data-ttu-id="d1bfc-156">.NET Framework'de sonlandırıcılar ve çöp toplama hakkında daha fazla bilgi için [Bkz.](../../../standard/garbage-collection/index.md)</span><span class="sxs-lookup"><span data-stu-id="d1bfc-156">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="d1bfc-157">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d1bfc-157">Events</span></span>

<span data-ttu-id="d1bfc-158">Olaylar, ilgi çekici bir şey oluştuğunda bir sınıfın veya nesnenin diğer sınıfları veya nesneleri bildirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-158">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="d1bfc-159">Olayı gönderen (veya yükselten) sınıfa *yayımcı,* olayı alan (veya işleyen) sınıflara *abone*denir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-159">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="d1bfc-160">Olaylar hakkında daha fazla bilgi için, bunların nasıl yükseltildiği ve işlendiği [hakkında](../../../standard/events/index.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-160">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="d1bfc-161">Bir sınıfta olay bildirmek için [olay](../../language-reference/keywords/event.md) anahtar sözcük'ünden yararlanın.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-161">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>

- <span data-ttu-id="d1bfc-162">Bir olayı yükseltmek için olay temsilcisini çağırın.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-162">To raise an event, invoke the event delegate.</span></span>

- <span data-ttu-id="d1bfc-163">Bir etkinliğe abone olmak `+=` için operatörü kullanın; bir etkinlikten aboneliğinizi iptal `-=` etmek için işleci kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-163">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="d1bfc-164">İç içe sınıflar</span><span class="sxs-lookup"><span data-stu-id="d1bfc-164">Nested classes</span></span>

<span data-ttu-id="d1bfc-165">Başka bir sınıf içinde tanımlanan bir sınıf *iç içe*denir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-165">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="d1bfc-166">Varsayılan olarak, iç içe sınıf özeldir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-166">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="d1bfc-167">İç içe sınıf bir örnek oluşturmak için, nokta ardından kapsayıcı sınıfın adını ve ardından iç içe sınıf adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-167">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="d1bfc-168">Değiştiricilere ve erişim düzeylerine erişin</span><span class="sxs-lookup"><span data-stu-id="d1bfc-168">Access modifiers and access levels</span></span>

<span data-ttu-id="d1bfc-169">Tüm sınıflar ve sınıf *üyeleri, erişim değiştiriciler*kullanarak diğer sınıflara hangi erişim düzeyini sağladıklarını belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-169">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="d1bfc-170">Aşağıdaki erişim değiştiriciler kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-170">The following access modifiers are available:</span></span>

|<span data-ttu-id="d1bfc-171">C# Değiştirici</span><span class="sxs-lookup"><span data-stu-id="d1bfc-171">C# Modifier</span></span>|<span data-ttu-id="d1bfc-172">Tanım</span><span class="sxs-lookup"><span data-stu-id="d1bfc-172">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="d1bfc-173">Kamu</span><span class="sxs-lookup"><span data-stu-id="d1bfc-173">public</span></span>](../../language-reference/keywords/public.md)|<span data-ttu-id="d1bfc-174">Türe veya üyeye, aynı derlemedeki veya ona başvuran başka bir derlemedeki başka bir kod erişebilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-174">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="d1bfc-175">Özel</span><span class="sxs-lookup"><span data-stu-id="d1bfc-175">private</span></span>](../../language-reference/keywords/private.md)|<span data-ttu-id="d1bfc-176">Türe veya üyeye yalnızca aynı sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-176">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="d1bfc-177">protected</span><span class="sxs-lookup"><span data-stu-id="d1bfc-177">protected</span></span>](../../language-reference/keywords/protected.md)|<span data-ttu-id="d1bfc-178">Türe veya üyeye yalnızca aynı sınıftaveya türemiş bir sınıfta kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-178">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="d1bfc-179">Iç</span><span class="sxs-lookup"><span data-stu-id="d1bfc-179">internal</span></span>](../../language-reference/keywords/internal.md)|<span data-ttu-id="d1bfc-180">Türe veya üyeye aynı derlemedeki herhangi bir kod erişebilir, ancak başka bir derlemeden erişilemez.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-180">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|[<span data-ttu-id="d1bfc-181">protected internal</span><span class="sxs-lookup"><span data-stu-id="d1bfc-181">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)|<span data-ttu-id="d1bfc-182">Türe veya üyeye aynı derlemedeki herhangi bir kod veya başka bir derlemedeki herhangi bir türemiş sınıf erişebilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-182">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|
|[<span data-ttu-id="d1bfc-183">özel korumalı</span><span class="sxs-lookup"><span data-stu-id="d1bfc-183">private protected</span></span>](../../language-reference/keywords/private-protected.md)|<span data-ttu-id="d1bfc-184">Türe veya üyeye aynı sınıftaki kodla veya taban sınıf derlemesi içinde türetilmiş bir sınıfta erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-184">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|

<span data-ttu-id="d1bfc-185">Daha fazla bilgi için [Erişim Değiştiriciler'e](../classes-and-structs/access-modifiers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-185">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="d1bfc-186">Anında sınıflar</span><span class="sxs-lookup"><span data-stu-id="d1bfc-186">Instantiating classes</span></span>

<span data-ttu-id="d1bfc-187">Bir nesne oluşturmak için, bir sınıfı anında oluşturmanız veya bir sınıf örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-187">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="d1bfc-188">Bir sınıfı anında yaptıktan sonra, örnek özelliklerine ve alanlarına değerler atayabilir ve sınıf yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-188">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

<span data-ttu-id="d1bfc-189">Sınıf anlık işlem sırasında özelliklerine değer atamak için nesne baş harflerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-189">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="d1bfc-190">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-190">For more information, see:</span></span>

- [<span data-ttu-id="d1bfc-191">new İşleci</span><span class="sxs-lookup"><span data-stu-id="d1bfc-191">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="d1bfc-192">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="d1bfc-192">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="d1bfc-193">Statik Sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="d1bfc-193">Static Classes and Members</span></span>

<span data-ttu-id="d1bfc-194">Sınıfın statik bir üyesi, sınıfın tüm örnekleri tarafından paylaşılan bir özellik, yordam veya alandır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-194">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="d1bfc-195">Statik bir üye tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-195">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="d1bfc-196">Statik üyeye erişmek için, bu sınıfın bir nesnesini oluşturmadan sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-196">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="d1bfc-197">C#'daki statik sınıflar yalnızca statik üyelere sahiptir ve anında alınamaz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-197">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="d1bfc-198">Statik üyeler de statik olmayan özelliklere, alanlara veya yöntemlere erişemez</span><span class="sxs-lookup"><span data-stu-id="d1bfc-198">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="d1bfc-199">Daha fazla bilgi için bkz: [statik](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="d1bfc-199">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="d1bfc-200">Anonim türleri</span><span class="sxs-lookup"><span data-stu-id="d1bfc-200">Anonymous types</span></span>

<span data-ttu-id="d1bfc-201">Anonim türler, veri türü için sınıf tanımı yazmadan nesneler oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-201">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="d1bfc-202">Bunun yerine, derleyici sizin için bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-202">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="d1bfc-203">Sınıfın kullanılabilir bir adı yoktur ve nesneyi bildirirken belirttiğiniz özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-203">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="d1bfc-204">Anonim bir tür örneği oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-204">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="d1bfc-205">Daha fazla bilgi için bkz: [Anonim Türleri](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="d1bfc-205">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="d1bfc-206">Devralma</span><span class="sxs-lookup"><span data-stu-id="d1bfc-206">Inheritance</span></span>

<span data-ttu-id="d1bfc-207">Devralma, başka bir sınıfta tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni bir sınıf oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-207">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="d1bfc-208">Üyeleri devralınan *sınıfa taban sınıf,* bu üyeleri devralan sınıfa *ise türemiş sınıf*denir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-208">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="d1bfc-209">Ancak, C#'daki tüm sınıflar <xref:System.Object> ,.NET sınıf hiyerarşisini destekleyen ve tüm sınıflara düşük düzeyli hizmetler sağlayan sınıftan örtülü olarak devralır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-209">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="d1bfc-210">C# birden fazla mirası desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-210">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="d1bfc-211">Diğer bir tanesi, türemiş bir sınıf için yalnızca bir taban sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-211">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="d1bfc-212">Taban sınıftan devralmak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-212">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass {}
```

<span data-ttu-id="d1bfc-213">Varsayılan olarak tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-213">By default all classes can be inherited.</span></span> <span data-ttu-id="d1bfc-214">Ancak, bir sınıfın taban sınıf olarak kullanılmaması mı yoksa yalnızca taban sınıf olarak kullanılabilecek bir sınıf oluşturup oluşturmayacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-214">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="d1bfc-215">Bir sınıfın taban sınıf olarak kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-215">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="d1bfc-216">Bir sınıfın yalnızca taban sınıf olarak kullanılabileceğini ve anında kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-216">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="d1bfc-217">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-217">For more information, see:</span></span>

- [<span data-ttu-id="d1bfc-218">sealed</span><span class="sxs-lookup"><span data-stu-id="d1bfc-218">sealed</span></span>](../../language-reference/keywords/sealed.md)

- [<span data-ttu-id="d1bfc-219">Soyut</span><span class="sxs-lookup"><span data-stu-id="d1bfc-219">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="d1bfc-220">Üyeleri Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="d1bfc-220">Overriding Members</span></span>

<span data-ttu-id="d1bfc-221">Varsayılan olarak, türetilmiş bir sınıf tüm üyeleri taban sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-221">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="d1bfc-222">Devralınan üyenin davranışını değiştirmek istiyorsanız, bunu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-222">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="d1bfc-223">Diğer bir deyişle, türemiş sınıfta yöntem, özellik veya olay yeni bir uygulama tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-223">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="d1bfc-224">Aşağıdaki değiştiriciler özelliklerin ve yöntemlerin nasıl geçersiz kılındığını denetlemek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-224">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="d1bfc-225">C# Değiştirici</span><span class="sxs-lookup"><span data-stu-id="d1bfc-225">C# Modifier</span></span>|<span data-ttu-id="d1bfc-226">Tanım</span><span class="sxs-lookup"><span data-stu-id="d1bfc-226">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="d1bfc-227">virtual</span><span class="sxs-lookup"><span data-stu-id="d1bfc-227">virtual</span></span>](../../language-reference/keywords/virtual.md)|<span data-ttu-id="d1bfc-228">Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-228">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="d1bfc-229">Geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="d1bfc-229">override</span></span>](../../language-reference/keywords/override.md)|<span data-ttu-id="d1bfc-230">Taban sınıfta tanımlanan sanal (geçersiz kılınabilir) bir üyeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-230">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="d1bfc-231">Soyut</span><span class="sxs-lookup"><span data-stu-id="d1bfc-231">abstract</span></span>](../../language-reference/keywords/abstract.md)|<span data-ttu-id="d1bfc-232">Bir sınıf üyesinin türemiş sınıfta geçersiz kılınmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-232">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="d1bfc-233">new Değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="d1bfc-233">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md)|<span data-ttu-id="d1bfc-234">Taban sınıftan devralınan bir üyeyi gizler</span><span class="sxs-lookup"><span data-stu-id="d1bfc-234">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="d1bfc-235">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d1bfc-235">Interfaces</span></span>

<span data-ttu-id="d1bfc-236">Arabirimler, sınıflar gibi, özellikler, yöntemler ve olaylar kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-236">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="d1bfc-237">Ancak sınıfların aksine, arabirimler uygulama sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-237">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="d1bfc-238">Sınıflar tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-238">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="d1bfc-239">Arabirim, arabirimi uygulayan bir sınıfın bu arabirimin her yönünü tam olarak tanımlandığı şekilde uygulaması gerektiğinden, bir sözleşmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-239">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="d1bfc-240">Arabirimi tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-240">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

<span data-ttu-id="d1bfc-241">Bir sınıfta arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-241">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="d1bfc-242">Daha fazla bilgi [için, Arabirimler](../interfaces/index.md) ve [arayüz](../../language-reference/keywords/interface.md) anahtar kelimesi ndeki dil başvuru makalesi hakkındaki programlama kılavuzu makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-242">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="d1bfc-243">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d1bfc-243">Generics</span></span>

<span data-ttu-id="d1bfc-244">.NET Framework'deki sınıflar, yapılar, arabirimler ve yöntemler, depolayabildikleri veya kullanabilecekleri nesne türlerini tanımlayan *tür parametreleri* içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-244">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="d1bfc-245">Jeneriklerin en yaygın örneği, koleksiyonda depolanacak nesnelerin türünü belirtebileceğiniz bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-245">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="d1bfc-246">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-246">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="d1bfc-247">Genel bir sınıfın örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-247">To create an instance of a generic class:</span></span>

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="d1bfc-248">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-248">For more information, see:</span></span>

- [<span data-ttu-id="d1bfc-249">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d1bfc-249">Generics</span></span>](../../../standard/generics/index.md)

- [<span data-ttu-id="d1bfc-250">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d1bfc-250">Generics</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="d1bfc-251">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="d1bfc-251">Delegates</span></span>

<span data-ttu-id="d1bfc-252">*Temsilci,* yöntem imzasını tanımlayan ve uyumlu imzası olan herhangi bir yönteme başvuru sağlayan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-252">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="d1bfc-253">Temsilci aracılığıyla yöntemi çağırabilir (veya çağırabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="d1bfc-253">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="d1bfc-254">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-254">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="d1bfc-255">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-255">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="d1bfc-256">Etkinlik işlemede temsilci kullanma hakkında daha fazla bilgi için [Etkinlikler'e](../../../standard/events/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-256">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="d1bfc-257">Bir temsilci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-257">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="d1bfc-258">Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="d1bfc-258">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="d1bfc-259">Daha fazla bilgi [için, Temsilciler](../delegates/index.md) hakkındaki programlama kılavuzu makalesine ve [temsilci](../../language-reference/builtin-types/reference-types.md) anahtar kelimesindeki dil başvuru makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-259">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1bfc-260">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1bfc-260">See also</span></span>

- [<span data-ttu-id="d1bfc-261">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d1bfc-261">C# Programming Guide</span></span>](../index.md)
