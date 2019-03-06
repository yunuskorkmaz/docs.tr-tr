---
title: Nesne odaklı programlama (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 7822b9afa4b568563222d6096ea1b1ecc5d5ee0a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377930"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="f04eb-102">Nesne odaklı programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="f04eb-102">Object-Oriented Programming (C#)</span></span>
<span data-ttu-id="f04eb-103">C#, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne yönelimli programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f04eb-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="f04eb-104">*Kapsülleme* ilgili özellikleri, yöntemleri ve diğer üyeleri bir grup işlem tek bir birim veya nesne anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="f04eb-105">*Devralma* mevcut bir sınıfı temel alan yeni sınıflar oluşturma becerisidir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="f04eb-106">*Çok biçimlilik* her sınıf aynı özellikleri veya yöntemleri farklı şekilde uygular olsa da birbirinin yerine kullanılabilen birden fazla sınıfınız olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="f04eb-107">Bu bölüm aşağıdaki kavramları açıklar:</span><span class="sxs-lookup"><span data-stu-id="f04eb-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="f04eb-108">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="f04eb-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="f04eb-109">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="f04eb-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="f04eb-110">Özellikler ve alanları</span><span class="sxs-lookup"><span data-stu-id="f04eb-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="f04eb-111">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f04eb-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="f04eb-112">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="f04eb-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="f04eb-113">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="f04eb-113">Finalizers</span></span>](#Finalizers)  
  
         [<span data-ttu-id="f04eb-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="f04eb-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="f04eb-115">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="f04eb-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="f04eb-116">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="f04eb-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="f04eb-117">Sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="f04eb-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="f04eb-118">Statik sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="f04eb-118">Static Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="f04eb-119">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="f04eb-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="f04eb-120">Devralma</span><span class="sxs-lookup"><span data-stu-id="f04eb-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="f04eb-121">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="f04eb-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="f04eb-122">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="f04eb-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="f04eb-123">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="f04eb-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="f04eb-124">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f04eb-124">Delegates</span></span>](#Delegates)  
  
## <a name="Classes"></a> <span data-ttu-id="f04eb-125">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="f04eb-125">Classes and Objects</span></span>  
 <span data-ttu-id="f04eb-126">Koşulları *sınıfı* ve *nesne* bazen birbirlerinin yerine, ancak aslında sınıfları açıklar kullanılan *türü* nesnelerin nesneleri iken  *örnekleri* sınıf.</span><span class="sxs-lookup"><span data-stu-id="f04eb-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="f04eb-127">Bu nedenle, bir nesne oluşturma işlemi olarak da adlandırılır *oluşturmada*.</span><span class="sxs-lookup"><span data-stu-id="f04eb-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="f04eb-128">Blueprint benzerliği kullanarak bir sınıf plandır ve nesne bu yapılan bir binadır.</span><span class="sxs-lookup"><span data-stu-id="f04eb-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="f04eb-129">Bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-129">To define a class:</span></span>  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 <span data-ttu-id="f04eb-130">C# ayrıca sağlayan hafif bir sınıflar adlandırılan sürümünü *yapıları* yapın ve büyük nesneler dizisi oluşturmanız gerektiğinde yararlı olan çok fazla bellek için kullanmak istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="f04eb-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="f04eb-131">Yapı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-131">To define a structure:</span></span>  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 <span data-ttu-id="f04eb-132">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="f04eb-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f04eb-133">class</span><span class="sxs-lookup"><span data-stu-id="f04eb-133">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="f04eb-134">struct</span><span class="sxs-lookup"><span data-stu-id="f04eb-134">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
### <a name="Members"></a> <span data-ttu-id="f04eb-135">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="f04eb-135">Class Members</span></span>  
 <span data-ttu-id="f04eb-136">Her sınıf farklı olabilir *sınıf üyeleri* sınıf verilerini, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasındaki iletişimi sağlayan olayları tanımlayan özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
#### <a name="Properties"></a> <span data-ttu-id="f04eb-137">Özellikler ve alanları</span><span class="sxs-lookup"><span data-stu-id="f04eb-137">Properties and Fields</span></span>  
 <span data-ttu-id="f04eb-138">Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f04eb-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="f04eb-139">Bunlar okunabilir ve doğrudan ayarlamak için alanları gibi değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="f04eb-140">Bir alanı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-140">To define a field:</span></span>  
  
```csharp  
class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 <span data-ttu-id="f04eb-141">Özellik get ve set yordamları, değerlerin nasıl ayarlanacağı veya döndürüleceği hakkında daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f04eb-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="f04eb-142">C# ya da özellik değerini depolamak için özel bir alan oluşturabilir veya bu alanı arka planda otomatik olarak oluşturmak ve özellik yordamları için temel mantığı sağlayan sözde ve otomatik olarak uygulanan özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f04eb-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="f04eb-143">Otomatik uygulanan bir özellik tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-143">To define an auto-implemented property:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 <span data-ttu-id="f04eb-144">Okuma için bazı ek işlemler gerçekleştirebilir ve yazma özellik değeri özellik değerini depolamak için bir alan tanımlayın ve depolanması ve alınması için temel mantığı sağlayan gerekiyorsa:</span><span class="sxs-lookup"><span data-stu-id="f04eb-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
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
  
 <span data-ttu-id="f04eb-145">Çoğu özellikleri, yöntemleri ya da yordamlar hem ayarlamak ve özellik değerini almak için vardır.</span><span class="sxs-lookup"><span data-stu-id="f04eb-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="f04eb-146">Ancak, değiştiren veya okunmalarını kısıtlamak için salt okunur veya salt yazılır özellikler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f04eb-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="f04eb-147">C# ' ta atlayabilirsiniz `get` veya `set` özellik yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f04eb-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="f04eb-148">Ancak, otomatik uygulanan özellikler salt okunur veya salt yazılır olamaz.</span><span class="sxs-lookup"><span data-stu-id="f04eb-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="f04eb-149">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="f04eb-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f04eb-150">get</span><span class="sxs-lookup"><span data-stu-id="f04eb-150">get</span></span>](../../../csharp/language-reference/keywords/get.md)  
  
-   [<span data-ttu-id="f04eb-151">set</span><span class="sxs-lookup"><span data-stu-id="f04eb-151">set</span></span>](../../../csharp/language-reference/keywords/set.md)  
  
#### <a name="Methods"></a> <span data-ttu-id="f04eb-152">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="f04eb-152">Methods</span></span>  
 <span data-ttu-id="f04eb-153">A *yöntemi* , nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-153">A *method* is an action that an object can perform.</span></span>  
  
 <span data-ttu-id="f04eb-154">Bir sınıfın yöntemini tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-154">To define a method of a class:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 <span data-ttu-id="f04eb-155">Bir sınıfta çeşitli uygulamalar olabilir veya *aşırı*, parametre sayıları veya parametre türleri içinde farklı aynı yöntemin.</span><span class="sxs-lookup"><span data-stu-id="f04eb-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="f04eb-156">Bir yöntemi aşırı yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-156">To overload a method:</span></span>  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 <span data-ttu-id="f04eb-157">Çoğu durumda, sınıf tanımında bir yöntem bildirin.</span><span class="sxs-lookup"><span data-stu-id="f04eb-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="f04eb-158">Ancak, ayrıca C# destekler *genişletme yöntemleri* mevcut sınıfa sınıfın gerçek tanımı dışında yöntemler eklemenize olanak tanıyan.</span><span class="sxs-lookup"><span data-stu-id="f04eb-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="f04eb-159">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="f04eb-159">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f04eb-160">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f04eb-160">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="f04eb-161">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="f04eb-161">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
#### <a name="Constructors"></a> <span data-ttu-id="f04eb-162">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="f04eb-162">Constructors</span></span>  
 <span data-ttu-id="f04eb-163">Oluşturucular, belirli bir türde bir nesne oluşturulduğunda, otomatik olarak yürütülen sınıf yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="f04eb-164">Kurucular genellikle yeni nesnenin veri üyeleri başlatın.</span><span class="sxs-lookup"><span data-stu-id="f04eb-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="f04eb-165">Sonra yalnızca bir sınıf oluşturulduğunda Oluşturucu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f04eb-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="f04eb-166">Ayrıca, Oluşturucudaki kod her zaman bir sınıftaki herhangi bir kod önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="f04eb-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="f04eb-167">Ancak, başka bir yöntem olduğu gibi birden çok oluşturucu aşırı yüklemeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f04eb-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="f04eb-168">Bir sınıf için bir kurucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-168">To define a constructor for a class:</span></span>  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 <span data-ttu-id="f04eb-169">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="f04eb-169">For more information, see:</span></span>  
  
 <span data-ttu-id="f04eb-170">[Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="f04eb-170">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>  
  
#### <a name="Finalizers"></a> <span data-ttu-id="f04eb-171">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="f04eb-171">Finalizers</span></span>  
 <span data-ttu-id="f04eb-172">Sonlandırıcılar, sınıfların örneklerini yok etmek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f04eb-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="f04eb-173">.NET Framework, atık toplayıcı sağlanmasını ve ayrılmasını uygulamanızda yönetilen nesneler için bellek otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="f04eb-174">Ancak, yine de sonlandırıcılar uygulamanızın oluşturduğu herhangi yönetilmeyen kaynakları temizlemek için gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="f04eb-175">Yalnızca bir olabilir bir sınıf için bir sonlandırıcı.</span><span class="sxs-lookup"><span data-stu-id="f04eb-175">There can be only one finalizers for a class.</span></span>  
  
 <span data-ttu-id="f04eb-176">Sonlandırıcılar ve .NET Framework atık toplama hakkında daha fazla bilgi için bkz: [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="f04eb-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
#### <a name="Events"></a> <span data-ttu-id="f04eb-177">Olayları</span><span class="sxs-lookup"><span data-stu-id="f04eb-177">Events</span></span>  
 <span data-ttu-id="f04eb-178">Bir sınıf olayları etkinleştirin veya nesneyi diğer sınıfları veya nesneleri ilgilendiğiniz bir şeyler olduğunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="f04eb-179">Olay gönderir (veya harekete geçiren) sınıf adlı *yayımcı* ve olay alma (veya tanıtıcı) sınıflar adlandırılan *aboneleri*.</span><span class="sxs-lookup"><span data-stu-id="f04eb-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="f04eb-180">Olaylar hakkında daha fazla bilgi için nasıl oluştukları ve işlendikleri bkz [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="f04eb-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>  
  
-   <span data-ttu-id="f04eb-181">Bir sınıf içinde bir olay bildirmek için kullanın [olay](../../../csharp/language-reference/keywords/event.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f04eb-181">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>  
  
-   <span data-ttu-id="f04eb-182">Bir olayı için olay temsilcisini çağırın.</span><span class="sxs-lookup"><span data-stu-id="f04eb-182">To raise an event, invoke the event delegate.</span></span>  
  
-   <span data-ttu-id="f04eb-183">Bir olaya abone olmak için kullanmak `+=` işleci, bir olayın aboneliğini kaldırmak için kullanın; `-=` işleci.</span><span class="sxs-lookup"><span data-stu-id="f04eb-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>  
  
#### <a name="NestedClasses"></a> <span data-ttu-id="f04eb-184">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="f04eb-184">Nested Classes</span></span>  
 <span data-ttu-id="f04eb-185">Başka bir sınıfın içinde tanımlanan bir sınıfa *iç içe geçmiş*.</span><span class="sxs-lookup"><span data-stu-id="f04eb-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="f04eb-186">Varsayılan olarak, iç içe geçmiş özel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="f04eb-186">By default, the nested class is private.</span></span>  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 <span data-ttu-id="f04eb-187">İç içe geçmiş sınıfının bir örneğini oluşturmak için kapsayıcı sınıfının arkasına bir nokta koyun ve sonra ardından iç içe geçmiş sınıf adı adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="f04eb-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
### <a name="AccessModifiers"></a> <span data-ttu-id="f04eb-188">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="f04eb-188">Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="f04eb-189">Tüm sınıflar ve sınıf üyeleri sağlamaları için diğer sınıflar kullanılarak hangi erişim düzeyini belirtebilirsiniz *erişim değiştiricilerine*.</span><span class="sxs-lookup"><span data-stu-id="f04eb-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="f04eb-190">Aşağıdaki erişim değiştiriciler kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f04eb-190">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="f04eb-191">C# Modifier</span><span class="sxs-lookup"><span data-stu-id="f04eb-191">C# Modifier</span></span>|<span data-ttu-id="f04eb-192">Tanım</span><span class="sxs-lookup"><span data-stu-id="f04eb-192">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="f04eb-193">public</span><span class="sxs-lookup"><span data-stu-id="f04eb-193">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="f04eb-194">Türe veya üyeye aynı derlemenin veya ona başvuran başka bir derleme içindeki diğer kodlardan tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="f04eb-195">private</span><span class="sxs-lookup"><span data-stu-id="f04eb-195">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="f04eb-196">Türe veya üyeye aynı sınıftaki kod tarafından yalnızca erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-196">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="f04eb-197">protected</span><span class="sxs-lookup"><span data-stu-id="f04eb-197">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="f04eb-198">Türe veya üyeye aynı sınıftaki veya türetilmiş bir sınıf içinde kod tarafından yalnızca erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="f04eb-199">internal</span><span class="sxs-lookup"><span data-stu-id="f04eb-199">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="f04eb-200">Türe veya üyeye aynı derlemedeki ancak farklı derlemeyle herhangi bir kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|[<span data-ttu-id="f04eb-201">protected internal</span><span class="sxs-lookup"><span data-stu-id="f04eb-201">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="f04eb-202">Türe veya üyeye aynı derlemedeki kod ile veya başka bir derlemedeki türetilmiş sınıfla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
|[<span data-ttu-id="f04eb-203">private protected</span><span class="sxs-lookup"><span data-stu-id="f04eb-203">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="f04eb-204">Türe veya üyeye aynı sınıftaki veya türetilmiş bir sınıfın temel sınıf derleme içinde kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|  
  
 <span data-ttu-id="f04eb-205">Daha fazla bilgi için [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="f04eb-205">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
### <a name="InstantiatingClasses"></a> <span data-ttu-id="f04eb-206">Sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="f04eb-206">Instantiating Classes</span></span>  
 <span data-ttu-id="f04eb-207">Bir nesne oluşturmak için bir sınıf örneği başlatmanız veya sınıf örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 <span data-ttu-id="f04eb-208">Bir sınıf başlatıldıktan sonra Örneğin özelliklerine ve alanlarına değerler atayın ve sınıf yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f04eb-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 <span data-ttu-id="f04eb-209">Sınıf örnekleme işlemi sırasında özellikleri değerleri atamak için nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="f04eb-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="f04eb-210">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="f04eb-210">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f04eb-211">new İşleci</span><span class="sxs-lookup"><span data-stu-id="f04eb-211">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [<span data-ttu-id="f04eb-212">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="f04eb-212">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
### <a name="Static"></a> <span data-ttu-id="f04eb-213">Statik sınıflar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="f04eb-213">Static Classes and Members</span></span>  
 <span data-ttu-id="f04eb-214">Statik sınıf üyesi bir özellik, yordam veya bir sınıfın tüm örnekleri tarafından paylaşıldığını alan var.</span><span class="sxs-lookup"><span data-stu-id="f04eb-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="f04eb-215">Statik bir üye tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-215">To define a static member:</span></span>  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 <span data-ttu-id="f04eb-216">Statik bir üyeye erişmek için sınıfın adını, bu sınıfın bir nesnesi oluşturmadan kullanın:</span><span class="sxs-lookup"><span data-stu-id="f04eb-216">To access the static member, use the name of the class without creating an object of this class:</span></span>  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 <span data-ttu-id="f04eb-217">C# ' de statik sınıflar yalnızca statik üyeleri sahiptir ve örnekleri oluşturulamaz.</span><span class="sxs-lookup"><span data-stu-id="f04eb-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="f04eb-218">Statik üyeleri de statik olmayan özellikler, alanlara veya yöntemlere erişemez</span><span class="sxs-lookup"><span data-stu-id="f04eb-218">Static members also cannot access non-static  properties, fields or methods</span></span>  
  
 <span data-ttu-id="f04eb-219">Daha fazla bilgi için bkz: [statik](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="f04eb-219">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
### <a name="AnonymousTypes"></a> <span data-ttu-id="f04eb-220">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="f04eb-220">Anonymous Types</span></span>  
 <span data-ttu-id="f04eb-221">Anonim türler nesne veri türü için bir sınıf tanımı yazmaya gerek kalmadan oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f04eb-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="f04eb-222">Bunun yerine, derleyici bir sınıf sizin için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f04eb-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="f04eb-223">Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="f04eb-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="f04eb-224">Anonim bir türün bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-224">To create an instance of an anonymous type:</span></span>  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="f04eb-225">Daha fazla bilgi için bkz.: [Anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f04eb-225">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="Inheritance"></a> <span data-ttu-id="f04eb-226">Devralma</span><span class="sxs-lookup"><span data-stu-id="f04eb-226">Inheritance</span></span>  
 <span data-ttu-id="f04eb-227">Devralma, başka bir sınıfta tanımlanan davranışı değiştirir kullanır ve genişleten yeni bir sınıf oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f04eb-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="f04eb-228">Üyeleri devralınan sınıf *temel sınıfı*, ve bu üyeleri devralan sınıf *türetilmiş sınıf*.</span><span class="sxs-lookup"><span data-stu-id="f04eb-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="f04eb-229">Ancak, C# içindeki tüm sınıflar örtük olarak devralınacak <xref:System.Object> .NET sınıf hiyerarşisini destekleyen ve tüm sınıflara alt düzey hizmetler sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="f04eb-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f04eb-230">C# birden çok devralmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f04eb-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="f04eb-231">Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f04eb-231">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="f04eb-232">Temel sınıfından devralmak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-232">To inherit from a base class:</span></span>  
  
```csharp  
class DerivedClass:BaseClass {}  
```  
  
 <span data-ttu-id="f04eb-233">Varsayılan olarak, tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-233">By default all classes can be inherited.</span></span> <span data-ttu-id="f04eb-234">Ancak, bir sınıfın temel sınıf olarak kullanılmamalıdır veya yalnızca temel sınıf olarak kullanılan bir sınıf oluşturmak olup olmadığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f04eb-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="f04eb-235">Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-235">To specify that a class cannot be used as a base class:</span></span>  
  
```csharp  
public sealed class A { }  
```  
  
 <span data-ttu-id="f04eb-236">Bir sınıf yalnızca temel sınıf olarak kullanılabilecek ve başlatılamayacak belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```csharp  
public abstract class B { }  
```  
  
 <span data-ttu-id="f04eb-237">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="f04eb-237">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f04eb-238">sealed</span><span class="sxs-lookup"><span data-stu-id="f04eb-238">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [<span data-ttu-id="f04eb-239">abstract</span><span class="sxs-lookup"><span data-stu-id="f04eb-239">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
### <a name="Overriding"></a> <span data-ttu-id="f04eb-240">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="f04eb-240">Overriding Members</span></span>  
 <span data-ttu-id="f04eb-241">Varsayılan olarak, türetilmiş bir sınıf tüm üyelerini kendi temel sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="f04eb-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="f04eb-242">Devralınan üye davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="f04eb-243">Diğer bir deyişle, türetilmiş bir sınıf içindeki yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f04eb-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="f04eb-244">Özellikleri ve yöntemleri nasıl geçersiz kılınacağını denetlemek için aşağıdaki değiştiriciler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="f04eb-244">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="f04eb-245">C# Modifier</span><span class="sxs-lookup"><span data-stu-id="f04eb-245">C# Modifier</span></span>|<span data-ttu-id="f04eb-246">Tanım</span><span class="sxs-lookup"><span data-stu-id="f04eb-246">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="f04eb-247">virtual</span><span class="sxs-lookup"><span data-stu-id="f04eb-247">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="f04eb-248">Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-248">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="f04eb-249">override</span><span class="sxs-lookup"><span data-stu-id="f04eb-249">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="f04eb-250">Temel sınıfta tanımlanan sanal bir (geçersiz kılınabilir) üyeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f04eb-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="f04eb-251">abstract</span><span class="sxs-lookup"><span data-stu-id="f04eb-251">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="f04eb-252">Gerektiren bir sınıf üyesinin derlenen sınıfta geçersiz kılınacak.</span><span class="sxs-lookup"><span data-stu-id="f04eb-252">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="f04eb-253">new Değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="f04eb-253">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="f04eb-254">Bir temel sınıftan devralınan üyeyi gizler</span><span class="sxs-lookup"><span data-stu-id="f04eb-254">Hides a member inherited from a base class</span></span>|  
  
## <a name="Interfaces"></a> <span data-ttu-id="f04eb-255">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f04eb-255">Interfaces</span></span>  
 <span data-ttu-id="f04eb-256">Sınıflar gibi arabirimler, özellikleri, yöntemleri ve olayları kümesi tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="f04eb-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="f04eb-257">Ancak, sınıflardan farklı olarak, arabirimler uygulama sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f04eb-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="f04eb-258">Bunlar sınıfları tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f04eb-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="f04eb-259">Tam olarak tanımlandığı şekilde bir arabirimi uygulayan bir sınıf, o arabirimi her yönüyle uygulamalıdır bir arabirim bir sözleşmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f04eb-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="f04eb-260">Arabirim tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-260">To define an interface:</span></span>  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 <span data-ttu-id="f04eb-261">Bir sınıf içinde arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-261">To implement an interface in a class:</span></span>  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 <span data-ttu-id="f04eb-262">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="f04eb-262">For more information, see:</span></span>  
  
 [<span data-ttu-id="f04eb-263">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="f04eb-263">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
 [<span data-ttu-id="f04eb-264">interface</span><span class="sxs-lookup"><span data-stu-id="f04eb-264">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
## <a name="Generics"></a> <span data-ttu-id="f04eb-265">Genel türler</span><span class="sxs-lookup"><span data-stu-id="f04eb-265">Generics</span></span>  
 <span data-ttu-id="f04eb-266">Sınıflar, yapılar, arabirimler ve yöntemler .NET Framework'teki içerebilir *tür parametrelerindeki* bunlar depolayabildikleri veya kullanabildikleri nesnelerin türlerini tanımlayan.</span><span class="sxs-lookup"><span data-stu-id="f04eb-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="f04eb-267">Genel türlerin yararları en yaygın örnek, bir koleksiyonda depolanacak nesnelerin türünü belirleyebileceğiniz koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="f04eb-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="f04eb-268">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-268">To define a generic class:</span></span>  
  
```csharp  
public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 <span data-ttu-id="f04eb-269">Bir genel sınıfın bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-269">To create an instance of a generic class:</span></span>  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 <span data-ttu-id="f04eb-270">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="f04eb-270">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f04eb-271">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="f04eb-271">Generics</span></span>](~/docs/standard/generics/index.md)  
  
-   [<span data-ttu-id="f04eb-272">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="f04eb-272">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
  
## <a name="Delegates"></a> <span data-ttu-id="f04eb-273">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f04eb-273">Delegates</span></span>  
 <span data-ttu-id="f04eb-274">A *temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu bir imza ile herhangi bir yönteme başvuru sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="f04eb-275">Çağırma (çağrı yöntemi temsilci aracılığıyla veya).</span><span class="sxs-lookup"><span data-stu-id="f04eb-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="f04eb-276">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f04eb-276">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f04eb-277">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="f04eb-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="f04eb-278">Temsilcileri olay işlemede kullanma hakkında daha fazla bilgi için bkz. [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="f04eb-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="f04eb-279">Temsilci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-279">To create a delegate:</span></span>  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 <span data-ttu-id="f04eb-280">Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="f04eb-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
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
  
 <span data-ttu-id="f04eb-281">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="f04eb-281">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f04eb-282">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f04eb-282">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
-   [<span data-ttu-id="f04eb-283">delegate</span><span class="sxs-lookup"><span data-stu-id="f04eb-283">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a><span data-ttu-id="f04eb-284">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f04eb-284">See also</span></span>

- [<span data-ttu-id="f04eb-285">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f04eb-285">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
