---
title: "Nesne odaklı programlama (C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a7f30293bb2d50981353badfb7e373b60dcfeec
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2017
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="a7c1c-102">Nesne odaklı programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="a7c1c-102">Object-Oriented Programming (C#)</span></span>
<span data-ttu-id="a7c1c-103">C# kapsülleme, devralma ve çok biçimlilik dahil nesne odaklı programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="a7c1c-104">*Kapsülleme* ilgili özellikleri, yöntemleri ve diğer üyeleri bir grup kabul edilir olduğunu tek bir birim veya nesne olarak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="a7c1c-105">*Devralma* var olan bir sınıfına dayalı yeni sınıflar oluşturma olanağı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="a7c1c-106">*Çok biçimlilik* farklı yollarla aynı özelliklerinin veya yöntemlerin her sınıf uygulayan olsa bile, birbirinin yerine, kullanılabilir birden çok sınıf olabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="a7c1c-107">Bu bölümde aşağıdaki kavramlar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="a7c1c-108">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="a7c1c-109">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="a7c1c-110">Özellikleri ve alanları</span><span class="sxs-lookup"><span data-stu-id="a7c1c-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="a7c1c-111">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="a7c1c-112">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a7c1c-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="a7c1c-113">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="a7c1c-113">Finalizers</span></span>](#Finalizers)  
  
         [<span data-ttu-id="a7c1c-114">Olayları</span><span class="sxs-lookup"><span data-stu-id="a7c1c-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="a7c1c-115">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="a7c1c-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="a7c1c-116">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="a7c1c-117">Örnek oluşturma sınıfları</span><span class="sxs-lookup"><span data-stu-id="a7c1c-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="a7c1c-118">Statik sınıflar ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-118">Static Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="a7c1c-119">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="a7c1c-120">Devralma</span><span class="sxs-lookup"><span data-stu-id="a7c1c-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="a7c1c-121">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a7c1c-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="a7c1c-122">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="a7c1c-123">Genel türler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="a7c1c-124">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-124">Delegates</span></span>](#Delegates)  
  
##  <a name="Classes"></a><span data-ttu-id="a7c1c-125">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-125">Classes and Objects</span></span>  
 <span data-ttu-id="a7c1c-126">Koşulları *sınıfı* ve *nesne* bazen birbirinin yerine, ancak aslında, sınıfları açıklar kullanılan *türü* nesnelerin nesneleri kullanılabilir durumdayken  *örnekleri* sınıfların.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="a7c1c-127">Bu nedenle, bir nesne oluşturma işlemi adlı *örneklemesi*.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="a7c1c-128">Şeması benzerleme kullanarak şeması sınıftır ve o şeması yapılan bir yapı bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="a7c1c-129">Bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-129">To define a class:</span></span>  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 <span data-ttu-id="a7c1c-130">C# ayrıca sağlar adlı sınıflar açık bir sürümünü *yapıları* büyük nesneler dizisi oluşturmak ve gerektiğinde faydalı olan çok fazla bellek için kullanmak istediğiniz değil.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="a7c1c-131">Bir yapı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-131">To define a structure:</span></span>  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 <span data-ttu-id="a7c1c-132">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="a7c1c-133">sınıfı</span><span class="sxs-lookup"><span data-stu-id="a7c1c-133">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="a7c1c-134">yapısı</span><span class="sxs-lookup"><span data-stu-id="a7c1c-134">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a><span data-ttu-id="a7c1c-135">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-135">Class Members</span></span>  
 <span data-ttu-id="a7c1c-136">Her sınıf farklı olabilir *sınıfı üyeleri* sınıfı verileri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasındaki iletişimi sağlamak olayları tanımlayan özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
####  <a name="Properties"></a><span data-ttu-id="a7c1c-137">Özellikleri ve alanları</span><span class="sxs-lookup"><span data-stu-id="a7c1c-137">Properties and Fields</span></span>  
 <span data-ttu-id="a7c1c-138">Alanları ve özellikleri bir nesne içeren bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="a7c1c-139">Bunlar okunabilir veya doğrudan ayarlamak için alanları gibi değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="a7c1c-140">Bir alan tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-140">To define a field:</span></span>  
  
```csharp  
Class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 <span data-ttu-id="a7c1c-141">Özelliklerin get ve değerleri nasıl ayarlayın veya döndürülen üzerinde daha fazla denetim sağlamak yordamları ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="a7c1c-142">C#, özellik değeri depolamak için özel bir alan oluşturun veya bu alan otomatik olarak arka planda oluşturun ve özellik yordamlar için temel mantığın sözde ve otomatik uygulanan özellikler kullanmak üzere sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="a7c1c-143">Otomatik uygulanan bir özellik tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-143">To define an auto-implemented property:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 <span data-ttu-id="a7c1c-144">Özellik değeri depolamak için bir alan tanımlayın ve depolamak ve bunu alma için temel mantığı sağlar özellik değeri yazılırken okuma için bazı ek işlemler gerçekleştirmek ve gerekirse:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
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
  
 <span data-ttu-id="a7c1c-145">Çoğu özellikleri yöntemleri ya da hem ayarlamak ve özellik değerini almak için yordamlar vardır.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="a7c1c-146">Ancak, okuma veya değiştirilmesini kısıtlamak için salt okunur veya salt yazılır özellikler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="a7c1c-147">C# ' ta, atlayabilirsiniz `get` veya `set` özelliği yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="a7c1c-148">Ancak, otomatik uygulanan özellikler salt okunur veya sadece yazılabilir olamaz.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="a7c1c-149">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="a7c1c-150">Al</span><span class="sxs-lookup"><span data-stu-id="a7c1c-150">get</span></span>](../../../csharp/language-reference/keywords/get.md)  
  
-   [<span data-ttu-id="a7c1c-151">ayarlama</span><span class="sxs-lookup"><span data-stu-id="a7c1c-151">set</span></span>](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a><span data-ttu-id="a7c1c-152">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-152">Methods</span></span>  
 <span data-ttu-id="a7c1c-153">A *yöntemi* bir nesne gerçekleştirebileceğiniz bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-153">A *method* is an action that an object can perform.</span></span>  
  
 <span data-ttu-id="a7c1c-154">Bir sınıfın bir yöntemi tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-154">To define a method of a class:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 <span data-ttu-id="a7c1c-155">Bir sınıf çeşitli uygulamalarını olabilir veya *aşırı*, aynı yönteminin parametreleri veya parametre türleri sayısında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="a7c1c-156">Bir yöntem aşırı yükleme için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-156">To overload a method:</span></span>  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 <span data-ttu-id="a7c1c-157">Çoğu durumda bir sınıf tanımı içinde bir yöntem bildirin.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="a7c1c-158">Ancak, ayrıca C# destekler *genişletme yöntemleri* sınıfının gerçek tanımının dışında varolan bir sınıfı yöntemleri eklemek izin verir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="a7c1c-159">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-159">For more information, see:</span></span>  
  
-   [<span data-ttu-id="a7c1c-160">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-160">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="a7c1c-161">Genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-161">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a><span data-ttu-id="a7c1c-162">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a7c1c-162">Constructors</span></span>  
 <span data-ttu-id="a7c1c-163">Oluşturucular belirli bir türde bir nesne oluşturulduğunda, otomatik olarak yürütülen sınıfı yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="a7c1c-164">Oluşturucular genellikle yeni nesnenin veri üyeleri başlatır.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="a7c1c-165">Yalnızca bir sınıf oluşturulduğunda sonra bir oluşturucu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="a7c1c-166">Ayrıca, Oluşturucusu kodda, başka bir kod sınıfında önce her zaman çalışır.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="a7c1c-167">Ancak, başka bir yöntem için olduğu gibi aynı şekilde, birden çok Oluşturucusu aşırı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="a7c1c-168">Bir sınıf için bir oluşturucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-168">To define a constructor for a class:</span></span>  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 <span data-ttu-id="a7c1c-169">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-169">For more information, see:</span></span>  
  
 <span data-ttu-id="a7c1c-170">[Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="a7c1c-170">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>  
  
####  <a name="Finalizers"></a><span data-ttu-id="a7c1c-171">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="a7c1c-171">Finalizers</span></span>  
 <span data-ttu-id="a7c1c-172">Sonlandırıcılar sınıfların örneklerini destruct için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="a7c1c-173">.NET Framework Atık toplayıcısının ayırma ve uygulamanızda yönetilen nesneler için bellek sürümü otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="a7c1c-174">Ancak, uygulamanızın oluşturduğu herhangi yönetilmeyen kaynakları temizlemek için sonlandırıcılar hala gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="a7c1c-175">Yalnızca bir olabilir sonlandırıcılar bir sınıf için.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-175">There can be only one finalizers for a class.</span></span>  
  
 <span data-ttu-id="a7c1c-176">Sonlandırıcılar ve .NET Framework atık toplama hakkında daha fazla bilgi için bkz: [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="a7c1c-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
####  <a name="Events"></a><span data-ttu-id="a7c1c-177">Olayları</span><span class="sxs-lookup"><span data-stu-id="a7c1c-177">Events</span></span>  
 <span data-ttu-id="a7c1c-178">Bir sınıf olayları etkinleştirin veya diğer sınıflar bildirmek için nesne veya nesnelerin çeken bir şey olduğunda oluşur.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="a7c1c-179">Olay gönderir (veya oluşturur) sınıf adlı *yayımcı* ve olay alın (veya ele) sınıfları adlı *aboneleri*.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="a7c1c-180">Olaylar hakkında daha fazla bilgi için nasıl oluşturulur ve işlenmiş, bkz: [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="a7c1c-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>  
  
-   <span data-ttu-id="a7c1c-181">Bir sınıftaki bir olay bildirmek için kullanın [olay](../../../csharp/language-reference/keywords/event.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-181">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>  
  
-   <span data-ttu-id="a7c1c-182">Bir olay yükseltmek için olay temsilcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-182">To raise an event, invoke the event delegate.</span></span>  
  
-   <span data-ttu-id="a7c1c-183">Bir olaya abone olmak için kullanmak `+=` bir olayından aboneliği kullanmak için işleci; `-=` işleci.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>  
  
####  <a name="NestedClasses"></a><span data-ttu-id="a7c1c-184">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="a7c1c-184">Nested Classes</span></span>  
 <span data-ttu-id="a7c1c-185">Başka bir sınıfın içinde tanımlanmış bir sınıf olarak adlandırılan *iç içe geçmiş*.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="a7c1c-186">Varsayılan olarak, iç içe geçmiş sınıf özeldir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-186">By default, the nested class is private.</span></span>  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 <span data-ttu-id="a7c1c-187">İç içe geçmiş sınıf örneği oluşturmak için nokta tarafından takip ve iç içe geçmiş sınıf adına göre ve ardından kapsayıcı sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a><span data-ttu-id="a7c1c-188">Erişim değiştiricileri ve erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-188">Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="a7c1c-189">Tüm sınıflar ve sınıf üyeleri sağladıkları diğer sınıflara kullanarak hangi erişim düzeyi belirtebilirsiniz *erişim değiştiricileri*.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="a7c1c-190">Aşağıdaki erişim değiştiricileri kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-190">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="a7c1c-191">C# değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="a7c1c-191">C# Modifier</span></span>|<span data-ttu-id="a7c1c-192">Tanım</span><span class="sxs-lookup"><span data-stu-id="a7c1c-192">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="a7c1c-193">Ortak</span><span class="sxs-lookup"><span data-stu-id="a7c1c-193">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="a7c1c-194">Tür veya üye, başka bir kod aynı bütünleştirilmiş kodda ya da başvurduğu başka bir derleme tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="a7c1c-195">Özel</span><span class="sxs-lookup"><span data-stu-id="a7c1c-195">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="a7c1c-196">Tür veya üye yalnızca aynı sınıfta kodu tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-196">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="a7c1c-197">korumalı</span><span class="sxs-lookup"><span data-stu-id="a7c1c-197">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="a7c1c-198">Tür veya üye yalnızca kodu aynı sınıfın veya türetilmiş bir sınıf tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="a7c1c-199">İç</span><span class="sxs-lookup"><span data-stu-id="a7c1c-199">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="a7c1c-200">Tür veya üye, herhangi bir kod aynı bütünleştirilmiş kodda değiştirebilir, ancak başka bir derleme tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|[<span data-ttu-id="a7c1c-201">İç korumalı</span><span class="sxs-lookup"><span data-stu-id="a7c1c-201">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="a7c1c-202">Tür veya üye aynı bütünleştirilmiş kod veya başka bir derlemede herhangi bir türetilmiş sınıf tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
|[<span data-ttu-id="a7c1c-203">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="a7c1c-203">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="a7c1c-204">Tür veya üye kodu aynı sınıfın veya temel sınıf derlemedeki türetilmiş bir sınıf tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|  
  
 <span data-ttu-id="a7c1c-205">Daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="a7c1c-205">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
###  <a name="InstantiatingClasses"></a><span data-ttu-id="a7c1c-206">Örnek oluşturma sınıfları</span><span class="sxs-lookup"><span data-stu-id="a7c1c-206">Instantiating Classes</span></span>  
 <span data-ttu-id="a7c1c-207">Nesne oluşturmak için bir sınıf örneği veya bir sınıf örneği oluşturmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 <span data-ttu-id="a7c1c-208">Bir sınıf örneği sonra değerleri örneğin özellikleri ve alanları atayın ve sınıf yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 <span data-ttu-id="a7c1c-209">Sınıf örnek oluşturma işlemi sırasında özellikleri değerleri atamak için nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="a7c1c-210">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-210">For more information, see:</span></span>  
  
-   [<span data-ttu-id="a7c1c-211">New işleci</span><span class="sxs-lookup"><span data-stu-id="a7c1c-211">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [<span data-ttu-id="a7c1c-212">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="a7c1c-212">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a><span data-ttu-id="a7c1c-213">Statik sınıflar ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-213">Static Classes and Members</span></span>  
 <span data-ttu-id="a7c1c-214">Bir statik sınıf özelliği, yordam veya bir sınıfın tüm örnekleri tarafından paylaşılan alan üyesidir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="a7c1c-215">Statik bir üyenin tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-215">To define a static member:</span></span>  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 <span data-ttu-id="a7c1c-216">Statik üye erişmek için bu sınıfın bir nesnesi oluşturmadan sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-216">To access the static member, use the name of the class without creating an object of this class:</span></span>  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 <span data-ttu-id="a7c1c-217">C# statik sınıflar yalnızca statik üyeleri sahip ve örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="a7c1c-218">Statik üyeler statik olmayan özellikler, alanlar veya yöntemler de erişemiyor</span><span class="sxs-lookup"><span data-stu-id="a7c1c-218">Static members also cannot access non-static  properties, fields or methods</span></span>  
  
 <span data-ttu-id="a7c1c-219">Daha fazla bilgi için bkz: [statik](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="a7c1c-219">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
###  <a name="AnonymousTypes"></a><span data-ttu-id="a7c1c-220">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-220">Anonymous Types</span></span>  
 <span data-ttu-id="a7c1c-221">Anonim türler veri türü için bir sınıf tanımı yazmadan nesneleri oluşturmak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="a7c1c-222">Bunun yerine, derleyici bir sınıf sizin için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="a7c1c-223">Sınıf kullanılabilir adı yok ve nesne bildirme belirttiğiniz özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="a7c1c-224">Anonim bir türün bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-224">To create an instance of an anonymous type:</span></span>  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="a7c1c-225">Daha fazla bilgi için bkz: [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a7c1c-225">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
##  <a name="Inheritance"></a><span data-ttu-id="a7c1c-226">Devralma</span><span class="sxs-lookup"><span data-stu-id="a7c1c-226">Inheritance</span></span>  
 <span data-ttu-id="a7c1c-227">Devralma yeniden kullanır, genişletir ve başka bir sınıf içinde tanımlanan davranışını değiştiren yeni bir sınıf oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="a7c1c-228">Üyeleri devralındığı sınıfı adlı *temel sınıfı*, bu üyeler devralan sınıf adı verilen ve *türetilmiş sınıf*.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="a7c1c-229">Ancak, C# tüm sınıflar örtük olarak devralınmalıdır <xref:System.Object> .NET sınıf hiyerarşisi destekleyen ve tüm sınıfları için alt düzey hizmetleri sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7c1c-230">C# birden çok devralma desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="a7c1c-231">Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-231">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="a7c1c-232">Bir taban sınıftan devralın için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-232">To inherit from a base class:</span></span>  
  
```csharp  
class DerivedClass:BaseClass{}  
```  
  
 <span data-ttu-id="a7c1c-233">Varsayılan olarak tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-233">By default all classes can be inherited.</span></span> <span data-ttu-id="a7c1c-234">Ancak, bir sınıfın temel sınıf olarak kullanılmamalıdır veya yalnızca bir temel sınıf olarak kullanılan bir sınıf oluşturun olup olmadığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="a7c1c-235">Bir sınıfın temel sınıf olarak kullanılan belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-235">To specify that a class cannot be used as a base class:</span></span>  
  
```csharp  
public sealed class A { }  
```  
  
 <span data-ttu-id="a7c1c-236">Sınıfı yalnızca bir temel sınıf olarak kullanılabilir ve başlatılamaz belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```csharp  
public abstract class B { }  
```  
  
 <span data-ttu-id="a7c1c-237">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-237">For more information, see:</span></span>  
  
-   [<span data-ttu-id="a7c1c-238">korumalı</span><span class="sxs-lookup"><span data-stu-id="a7c1c-238">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [<span data-ttu-id="a7c1c-239">Özet</span><span class="sxs-lookup"><span data-stu-id="a7c1c-239">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a><span data-ttu-id="a7c1c-240">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a7c1c-240">Overriding Members</span></span>  
 <span data-ttu-id="a7c1c-241">Varsayılan olarak, türetilmiş bir sınıf tüm üyelerin kendi taban sınıfından devralıyor.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="a7c1c-242">Devralınan üye davranışını değiştirmek istiyorsanız, bunu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="a7c1c-243">Diğer bir deyişle, yeni bir uygulama yöntemi, özelliği veya olay türetilen sınıfta tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="a7c1c-244">Aşağıdaki değiştiricileri özellikleri ve yöntemleri nasıl geçersiz kılınır denetlemek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-244">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="a7c1c-245">C# değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="a7c1c-245">C# Modifier</span></span>|<span data-ttu-id="a7c1c-246">Tanım</span><span class="sxs-lookup"><span data-stu-id="a7c1c-246">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="a7c1c-247">sanal</span><span class="sxs-lookup"><span data-stu-id="a7c1c-247">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="a7c1c-248">Türetilen bir sınıfta geçersiz kılınmak üzere sınıf üyesine sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-248">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="a7c1c-249">geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a7c1c-249">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="a7c1c-250">Taban sınıf içinde tanımlı sanal (geçersiz kılınabilir) üyesi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="a7c1c-251">Özet</span><span class="sxs-lookup"><span data-stu-id="a7c1c-251">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="a7c1c-252">Gerektiren türetilen bir sınıfta geçersiz kılınmak üzere bir sınıf üyesi.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-252">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="a7c1c-253">New değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="a7c1c-253">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="a7c1c-254">Bir taban sınıftan devralınan üye gizler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-254">Hides a member inherited from a base class</span></span>|  
  
##  <a name="Interfaces"></a><span data-ttu-id="a7c1c-255">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-255">Interfaces</span></span>  
 <span data-ttu-id="a7c1c-256">Sınıfları gibi arabirimler özellikleri, yöntemleri ve olayları kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="a7c1c-257">Ancak sınıflarından farklı olarak, uygulama arabirimleri sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="a7c1c-258">Bunlar sınıfları tarafından uygulanan ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="a7c1c-259">Tam olarak tanımlandığı şekilde bir arabirimini uygulayan bir sınıf her açıdan bu arabirimi uygulamalıdır içeren bir sözleşme bir arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="a7c1c-260">Bir arabirim tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-260">To define an interface:</span></span>  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 <span data-ttu-id="a7c1c-261">Bir sınıfta bir arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-261">To implement an interface in a class:</span></span>  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 <span data-ttu-id="a7c1c-262">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-262">For more information, see:</span></span>  
  
 [<span data-ttu-id="a7c1c-263">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a7c1c-263">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
 [<span data-ttu-id="a7c1c-264">arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7c1c-264">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a><span data-ttu-id="a7c1c-265">Genel türler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-265">Generics</span></span>  
 <span data-ttu-id="a7c1c-266">Sınıflar, yapılar, arabirimler ve .NET Framework yöntemlerini içerebilir *tür parametrelerindeki* kullanan depolamak veya nesne türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="a7c1c-267">Genel türler en yaygın örneği, bir koleksiyonda depolanan nesnelerin türü belirtebileceğiniz koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="a7c1c-268">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-268">To define a generic class:</span></span>  
  
```csharp  
Public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 <span data-ttu-id="a7c1c-269">Genel bir sınıf örneği oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-269">To create an instance of a generic class:</span></span>  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 <span data-ttu-id="a7c1c-270">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-270">For more information, see:</span></span>  
  
-   [<span data-ttu-id="a7c1c-271">Genel türler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-271">Generics</span></span>](~/docs/standard/generics/index.md)  
  
-   [<span data-ttu-id="a7c1c-272">Genel türler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-272">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a><span data-ttu-id="a7c1c-273">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-273">Delegates</span></span>  
 <span data-ttu-id="a7c1c-274">A *temsilci* yöntem imzası tanımlar türüdür ve herhangi bir yöntem başvuru ile uyumlu bir imzası sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="a7c1c-275">Çağırma (çağrı yöntemi temsilci aracılığıyla veya).</span><span class="sxs-lookup"><span data-stu-id="a7c1c-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="a7c1c-276">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-276">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7c1c-277">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="a7c1c-278">Olay işlemede kullanma hakkında daha fazla bilgi için bkz: [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="a7c1c-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="a7c1c-279">Bir temsilciyi oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-279">To create a delegate:</span></span>  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 <span data-ttu-id="a7c1c-280">Temsilci tarafından belirtilen imza eşleşen bir yöntem başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
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
  
 <span data-ttu-id="a7c1c-281">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a7c1c-281">For more information, see:</span></span>  
  
-   [<span data-ttu-id="a7c1c-282">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a7c1c-282">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
-   [<span data-ttu-id="a7c1c-283">temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="a7c1c-283">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a><span data-ttu-id="a7c1c-284">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a7c1c-284">See Also</span></span>  
 [<span data-ttu-id="a7c1c-285">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a7c1c-285">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
