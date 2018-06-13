---
title: Nesne odaklı programlama (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: e8936eb9031ef68ea333835d8433e1ba1a45990f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655973"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="ee383-102">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee383-102">Object-Oriented Programming (Visual Basic)</span></span>
<span data-ttu-id="ee383-103">Visual Basic kapsülleme, devralma ve çok biçimlilik dahil nesne odaklı programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee383-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="ee383-104">*Kapsülleme* ilgili özellikleri, yöntemleri ve diğer üyeleri bir grup kabul edilir olduğunu tek bir birim veya nesne olarak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ee383-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="ee383-105">*Devralma* var olan bir sınıfına dayalı yeni sınıflar oluşturma olanağı açıklar.</span><span class="sxs-lookup"><span data-stu-id="ee383-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="ee383-106">*Çok biçimlilik* farklı yollarla aynı özelliklerinin veya yöntemlerin her sınıf uygulayan olsa bile, birbirinin yerine, kullanılabilir birden çok sınıf olabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ee383-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="ee383-107">Bu bölümde aşağıdaki kavramlar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="ee383-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="ee383-108">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="ee383-108">Classes and objects</span></span>](#classes-and-objects)  
  
    -   [<span data-ttu-id="ee383-109">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="ee383-109">Class members</span></span>](#members)  
  
         [<span data-ttu-id="ee383-110">Özellikleri ve alanları</span><span class="sxs-lookup"><span data-stu-id="ee383-110">Properties and fields</span></span>](#properties-and-fields)  
  
         [<span data-ttu-id="ee383-111">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ee383-111">Methods</span></span>](#methods)  
  
         [<span data-ttu-id="ee383-112">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ee383-112">Constructors</span></span>](#constructors)  
  
         [<span data-ttu-id="ee383-113">Yıkıcılar</span><span class="sxs-lookup"><span data-stu-id="ee383-113">Destructors</span></span>](#destructors)  
  
         [<span data-ttu-id="ee383-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ee383-114">Events</span></span>](#events)  
  
         [<span data-ttu-id="ee383-115">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="ee383-115">Nested classes</span></span>](#nested-classes)  
  
    -   [<span data-ttu-id="ee383-116">Erişim değiştiricileri ve erişim düzeylerini</span><span class="sxs-lookup"><span data-stu-id="ee383-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)  
  
    -   [<span data-ttu-id="ee383-117">Örnek oluşturma sınıfları</span><span class="sxs-lookup"><span data-stu-id="ee383-117">Instantiating classes</span></span>](#instantiating-classes)  
  
    -   [<span data-ttu-id="ee383-118">Paylaşılan sınıflar ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="ee383-118">Shared classes and members</span></span>](#shared-classes-and-members)  
  
    -   [<span data-ttu-id="ee383-119">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="ee383-119">Anonymous types</span></span>](#anonymous-types)  
  
-   [<span data-ttu-id="ee383-120">Devralma</span><span class="sxs-lookup"><span data-stu-id="ee383-120">Inheritance</span></span>](#inheritance)  
  
    -   [<span data-ttu-id="ee383-121">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="ee383-121">Overriding members</span></span>](#overriding-members)  
  
-   [<span data-ttu-id="ee383-122">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ee383-122">Interfaces</span></span>](#interfaces)  
  
-   [<span data-ttu-id="ee383-123">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="ee383-123">Generics</span></span>](#generics)  
  
-   [<span data-ttu-id="ee383-124">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="ee383-124">Delegates</span></span>](#delegates)  
  
## <a name="classes-and-objects"></a><span data-ttu-id="ee383-125">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="ee383-125">Classes and objects</span></span>  
<span data-ttu-id="ee383-126">Koşulları *sınıfı* ve *nesne* bazen birbirinin yerine, ancak aslında, sınıfları açıklar kullanılan *türü* nesnelerin nesneleri kullanılabilir durumdayken  *örnekleri* sınıfların.</span><span class="sxs-lookup"><span data-stu-id="ee383-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="ee383-127">Bu nedenle, bir nesne oluşturma işlemi adlı *örneklemesi*.</span><span class="sxs-lookup"><span data-stu-id="ee383-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="ee383-128">Şeması benzerleme kullanarak şeması sınıftır ve o şeması yapılan bir yapı bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="ee383-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="ee383-129">Bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-129">To define a class:</span></span>

```vb  
Class SampleClass
End Class
```

<span data-ttu-id="ee383-130">Visual Basic adlı sınıflar açık bir sürümünü de sağlar *yapıları* büyük nesneler dizisi oluşturmak ve gerektiğinde faydalı olan çok fazla bellek için kullanmak istediğiniz değil.</span><span class="sxs-lookup"><span data-stu-id="ee383-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="ee383-131">Bir yapı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-131">To define a structure:</span></span>  

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="ee383-132">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="ee383-132">For more information, see:</span></span>

- [<span data-ttu-id="ee383-133">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="ee383-134">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="ee383-135">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="ee383-135">Class members</span></span>
<span data-ttu-id="ee383-136">Her sınıf farklı olabilir *sınıfı üyeleri* sınıfı verileri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasındaki iletişimi sağlamak olayları tanımlayan özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="ee383-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="ee383-137">Özellikleri ve alanları</span><span class="sxs-lookup"><span data-stu-id="ee383-137">Properties and fields</span></span>
<span data-ttu-id="ee383-138">Alanları ve özellikleri bir nesne içeren bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee383-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="ee383-139">Bunlar okunabilir veya doğrudan ayarlamak için alanları gibi değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="ee383-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="ee383-140">Bir alan tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="ee383-141">Özelliklerin get ve değerleri nasıl ayarlayın veya döndürülen üzerinde daha fazla denetim sağlamak yordamları ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ee383-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="ee383-142">Visual Basic, özellik değeri depolamak için özel bir alan oluşturun veya bu alan otomatik olarak arka planda oluşturun ve özellik yordamlar için temel mantığın sözde ve otomatik uygulanan özellikler kullanmak üzere sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee383-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="ee383-143">Otomatik uygulanan bir özellik tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="ee383-144">Özellik değeri depolamak için bir alan tanımlayın ve depolamak ve bunu alma için temel mantığı sağlar özellik değeri yazılırken okuma için bazı ek işlemler gerçekleştirmek ve gerekirse:</span><span class="sxs-lookup"><span data-stu-id="ee383-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="ee383-145">Çoğu özellikleri yöntemleri ya da hem ayarlamak ve özellik değerini almak için yordamlar vardır.</span><span class="sxs-lookup"><span data-stu-id="ee383-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="ee383-146">Ancak, okuma veya değiştirilmesini kısıtlamak için salt okunur veya salt yazılır özellikler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee383-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="ee383-147">Visual Basic'te kullandığınız `ReadOnly` ve `WriteOnly` anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="ee383-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="ee383-148">Ancak, otomatik uygulanan özellikler salt okunur veya sadece yazılabilir olamaz.</span><span class="sxs-lookup"><span data-stu-id="ee383-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="ee383-149">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="ee383-149">For more information, see:</span></span>
  
-   [<span data-ttu-id="ee383-150">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="ee383-151">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [<span data-ttu-id="ee383-152">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [<span data-ttu-id="ee383-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="ee383-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [<span data-ttu-id="ee383-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="ee383-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
#### <a name="methods"></a><span data-ttu-id="ee383-155">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ee383-155">Methods</span></span>  
 <span data-ttu-id="ee383-156">A *yöntemi* bir nesne gerçekleştirebileceğiniz bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="ee383-156">A *method* is an action that an object can perform.</span></span>  

> [!NOTE]
>  <span data-ttu-id="ee383-157">Visual Basic'te bir yöntem oluşturmanın iki yolu vardır: `Sub` yöntemi bir değer; döndürmezse deyimi kullanılan `Function` deyimi bir yöntemi bir değer döndürürse kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee383-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="ee383-158">Bir sınıfın bir yöntemi tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="ee383-159">Bir sınıf çeşitli uygulamalarını olabilir veya *aşırı*, aynı yönteminin parametreleri veya parametre türleri sayısında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee383-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="ee383-160">Bir yöntem aşırı yükleme için:</span><span class="sxs-lookup"><span data-stu-id="ee383-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="ee383-161">Çoğu durumda bir sınıf tanımı içinde bir yöntem bildirin.</span><span class="sxs-lookup"><span data-stu-id="ee383-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="ee383-162">Ancak, Visual Basic de destekler *genişletme yöntemleri* sınıfının gerçek tanımının dışında varolan bir sınıfı yöntemleri eklemek izin verir.</span><span class="sxs-lookup"><span data-stu-id="ee383-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="ee383-163">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="ee383-163">For more information, see:</span></span>

- [<span data-ttu-id="ee383-164">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  

- [<span data-ttu-id="ee383-165">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  

- [<span data-ttu-id="ee383-166">Overloads</span><span class="sxs-lookup"><span data-stu-id="ee383-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  

- [<span data-ttu-id="ee383-167">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ee383-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  

#### <a name="constructors"></a><span data-ttu-id="ee383-168">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ee383-168">Constructors</span></span>  
<span data-ttu-id="ee383-169">Oluşturucular belirli bir türde bir nesne oluşturulduğunda, otomatik olarak yürütülen sınıfı yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="ee383-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="ee383-170">Oluşturucular genellikle yeni nesnenin veri üyeleri başlatır.</span><span class="sxs-lookup"><span data-stu-id="ee383-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="ee383-171">Yalnızca bir sınıf oluşturulduğunda sonra bir oluşturucu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee383-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="ee383-172">Ayrıca, Oluşturucusu kodda, başka bir kod sınıfında önce her zaman çalışır.</span><span class="sxs-lookup"><span data-stu-id="ee383-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="ee383-173">Ancak, başka bir yöntem için olduğu gibi aynı şekilde, birden çok Oluşturucusu aşırı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee383-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="ee383-174">Bir sınıf için bir oluşturucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class 
```

<span data-ttu-id="ee383-175">Daha fazla bilgi için bkz: [nesne ömrü: nesneleri oluşturma ve Destroyed şeklini](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="ee383-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="ee383-176">Yıkıcılar</span><span class="sxs-lookup"><span data-stu-id="ee383-176">Destructors</span></span>
<span data-ttu-id="ee383-177">Yıkıcılar sınıfların örneklerini destruct için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee383-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="ee383-178">.NET Framework Atık toplayıcısının ayırma ve uygulamanızda yönetilen nesneler için bellek sürümü otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="ee383-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="ee383-179">Ancak, uygulamanızın oluşturduğu herhangi yönetilmeyen kaynakları temizlemek için Yıkıcılar hala gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ee383-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="ee383-180">Bir sınıf için yalnızca bir yıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee383-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="ee383-181">Yok ediciler ve .NET Framework atık toplama hakkında daha fazla bilgi için bkz: [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="ee383-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="ee383-182">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ee383-182">Events</span></span>
<span data-ttu-id="ee383-183">Bir sınıf olayları etkinleştirin veya diğer sınıflar bildirmek için nesne veya nesnelerin çeken bir şey olduğunda oluşur.</span><span class="sxs-lookup"><span data-stu-id="ee383-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="ee383-184">Olay gönderir (veya oluşturur) sınıf adlı *yayımcı* ve olay alın (veya ele) sınıfları adlı *aboneleri*.</span><span class="sxs-lookup"><span data-stu-id="ee383-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="ee383-185">Olaylar hakkında daha fazla bilgi için nasıl oluşturulur ve işlenmiş, bkz: [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="ee383-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="ee383-186">Olayları bildirme için kullanmak [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ee383-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="ee383-187">Olayları yükseltmek için kullanmak [RaiseEvent deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ee383-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="ee383-188">Olay işleyicileri bildirim temelli bir yolunu kullanarak belirtmek için kullanın [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) deyimi ve [işler](../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ee383-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="ee383-189">Dinamik olarak eklemek, kaldırmak ve olayla ilişkili olay işleyicisini değiştirin yapabiliyor olmanız için kullanmak [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md) ve [RemoveHandler deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md) ile birlikte [AddressOf İşleç](../../../visual-basic/language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ee383-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="ee383-190">İç içe geçmiş sınıflar</span><span class="sxs-lookup"><span data-stu-id="ee383-190">Nested classes</span></span>  
<span data-ttu-id="ee383-191">Başka bir sınıfın içinde tanımlanmış bir sınıf olarak adlandırılan *iç içe geçmiş*.</span><span class="sxs-lookup"><span data-stu-id="ee383-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="ee383-192">Varsayılan olarak, iç içe geçmiş sınıf özeldir.</span><span class="sxs-lookup"><span data-stu-id="ee383-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="ee383-193">İç içe geçmiş sınıf örneği oluşturmak için nokta tarafından takip ve iç içe geçmiş sınıf adına göre ve ardından kapsayıcı sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="ee383-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="ee383-194">Erişim değiştiricileri ve erişim düzeylerini</span><span class="sxs-lookup"><span data-stu-id="ee383-194">Access modifiers and access levels</span></span>  
<span data-ttu-id="ee383-195">Tüm sınıflar ve sınıf üyeleri sağladıkları diğer sınıflara kullanarak hangi erişim düzeyi belirtebilirsiniz *erişim değiştiricileri*.</span><span class="sxs-lookup"><span data-stu-id="ee383-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="ee383-196">Aşağıdaki erişim değiştiricileri kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ee383-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="ee383-197">Visual Basic değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="ee383-197">Visual Basic Modifier</span></span>|<span data-ttu-id="ee383-198">Tanım</span><span class="sxs-lookup"><span data-stu-id="ee383-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="ee383-199">Public</span><span class="sxs-lookup"><span data-stu-id="ee383-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="ee383-200">Tür veya üye, başka bir kod aynı bütünleştirilmiş kodda ya da başvurduğu başka bir derleme tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee383-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="ee383-201">Private</span><span class="sxs-lookup"><span data-stu-id="ee383-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="ee383-202">Tür veya üye yalnızca aynı sınıfta kodu tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee383-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="ee383-203">Protected</span><span class="sxs-lookup"><span data-stu-id="ee383-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="ee383-204">Tür veya üye yalnızca kodu aynı sınıfın veya türetilmiş bir sınıf tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee383-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="ee383-205">Friend</span><span class="sxs-lookup"><span data-stu-id="ee383-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="ee383-206">Tür veya üye, herhangi bir kod aynı bütünleştirilmiş kodda değiştirebilir, ancak başka bir derleme tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee383-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="ee383-207">Tür veya üye aynı bütünleştirilmiş kod veya başka bir derlemede herhangi bir türetilmiş sınıf tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee383-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="ee383-208">Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ee383-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="ee383-209">Örnek oluşturma sınıfları</span><span class="sxs-lookup"><span data-stu-id="ee383-209">Instantiating classes</span></span>  
<span data-ttu-id="ee383-210">Nesne oluşturmak için bir sınıf örneği veya bir sınıf örneği oluşturmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee383-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="ee383-211">Bir sınıf örneği sonra değerleri örneğin özellikleri ve alanları atayın ve sınıf yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ee383-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="ee383-212">Sınıf örnek oluşturma işlemi sırasında özellikleri değerleri atamak için nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="ee383-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="ee383-213">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="ee383-213">For more information, see:</span></span>

- [<span data-ttu-id="ee383-214">New İşleci</span><span class="sxs-lookup"><span data-stu-id="ee383-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)

- [<span data-ttu-id="ee383-215">Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="ee383-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

###  <a name="Static"></a> <span data-ttu-id="ee383-216">Paylaşılan sınıflar ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="ee383-216">Shared Classes and Members</span></span>  
 <span data-ttu-id="ee383-217">Bir paylaşılan sınıfı bir özellik, yordam veya bir sınıfın tüm örnekleri tarafından paylaşılan alan üyesidir.</span><span class="sxs-lookup"><span data-stu-id="ee383-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="ee383-218">Paylaşılan bir üyeye tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-218">To define a shared member:</span></span>  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 <span data-ttu-id="ee383-219">Paylaşılan üyeye erişmek için bu sınıfın bir nesnesi oluşturmadan sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="ee383-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 <span data-ttu-id="ee383-220">Visual Basic'te paylaşılan modülleri üyeleri yalnızca paylaşılan ve örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="ee383-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="ee383-221">Paylaşılan üyeler da paylaşılmayan özellikleri, alan veya yöntem erişemiyor</span><span class="sxs-lookup"><span data-stu-id="ee383-221">Shared members also cannot access non-shared properties, fields or methods</span></span>  
  
 <span data-ttu-id="ee383-222">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="ee383-222">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ee383-223">Shared</span><span class="sxs-lookup"><span data-stu-id="ee383-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [<span data-ttu-id="ee383-224">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
### <a name="anonymous-types"></a><span data-ttu-id="ee383-225">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="ee383-225">Anonymous types</span></span>  
<span data-ttu-id="ee383-226">Anonim türler veri türü için bir sınıf tanımı yazmadan nesneleri oluşturmak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="ee383-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="ee383-227">Bunun yerine, derleyici bir sınıf sizin için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ee383-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="ee383-228">Sınıf kullanılabilir adı yok ve nesne bildirme belirttiğiniz özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="ee383-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="ee383-229">Anonim bir türün bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="ee383-230">Daha fazla bilgi için bkz: [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="ee383-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="ee383-231">Devralma</span><span class="sxs-lookup"><span data-stu-id="ee383-231">Inheritance</span></span>
<span data-ttu-id="ee383-232">Devralma yeniden kullanır, genişletir ve başka bir sınıf içinde tanımlanan davranışını değiştiren yeni bir sınıf oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee383-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="ee383-233">Üyeleri devralındığı sınıfı adlı *temel sınıfı*, bu üyeler devralan sınıf adı verilen ve *türetilmiş sınıf*.</span><span class="sxs-lookup"><span data-stu-id="ee383-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="ee383-234">Ancak, Visual Basic'te tüm sınıflar örtük olarak devralınmalıdır <xref:System.Object> .NET sınıf hiyerarşisi destekleyen ve tüm sınıfları için alt düzey hizmetleri sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="ee383-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
>  <span data-ttu-id="ee383-235">Visual Basic birden çok devralma desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="ee383-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="ee383-236">Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee383-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="ee383-237">Bir taban sınıftan devralın için:</span><span class="sxs-lookup"><span data-stu-id="ee383-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="ee383-238">Varsayılan olarak tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="ee383-238">By default all classes can be inherited.</span></span> <span data-ttu-id="ee383-239">Ancak, bir sınıfın temel sınıf olarak kullanılmamalıdır veya yalnızca bir temel sınıf olarak kullanılan bir sınıf oluşturun olup olmadığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee383-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="ee383-240">Bir sınıfın temel sınıf olarak kullanılan belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="ee383-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="ee383-241">Sınıfı yalnızca bir temel sınıf olarak kullanılabilir ve başlatılamaz belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="ee383-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="ee383-242">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="ee383-242">For more information, see:</span></span>

- [<span data-ttu-id="ee383-243">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)

- [<span data-ttu-id="ee383-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="ee383-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)

- [<span data-ttu-id="ee383-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="ee383-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="ee383-246">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="ee383-246">Overriding members</span></span>
<span data-ttu-id="ee383-247">Varsayılan olarak, türetilmiş bir sınıf tüm üyelerin kendi taban sınıfından devralıyor.</span><span class="sxs-lookup"><span data-stu-id="ee383-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="ee383-248">Devralınan üye davranışını değiştirmek istiyorsanız, bunu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee383-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="ee383-249">Diğer bir deyişle, yeni bir uygulama yöntemi, özelliği veya olay türetilen sınıfta tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee383-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="ee383-250">Aşağıdaki değiştiricileri özellikleri ve yöntemleri nasıl geçersiz kılınır denetlemek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="ee383-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="ee383-251">Visual Basic değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="ee383-251">Visual Basic Modifier</span></span>|<span data-ttu-id="ee383-252">Tanım</span><span class="sxs-lookup"><span data-stu-id="ee383-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="ee383-253">Overridable</span><span class="sxs-lookup"><span data-stu-id="ee383-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="ee383-254">Türetilen bir sınıfta geçersiz kılınmak üzere sınıf üyesine sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee383-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="ee383-255">Overrides</span><span class="sxs-lookup"><span data-stu-id="ee383-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="ee383-256">Taban sınıf içinde tanımlı sanal (geçersiz kılınabilir) üyesi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ee383-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="ee383-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="ee383-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="ee383-258">Türetilen bir sınıfta geçersiz üye engeller.</span><span class="sxs-lookup"><span data-stu-id="ee383-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="ee383-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="ee383-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="ee383-260">Gerektiren türetilen bir sınıfta geçersiz kılınmak üzere bir sınıf üyesi.</span><span class="sxs-lookup"><span data-stu-id="ee383-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="ee383-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="ee383-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="ee383-262">Bir taban sınıftan devralınan üye gizler</span><span class="sxs-lookup"><span data-stu-id="ee383-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="ee383-263">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ee383-263">Interfaces</span></span>
<span data-ttu-id="ee383-264">Sınıfları gibi arabirimler özellikleri, yöntemleri ve olayları kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ee383-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="ee383-265">Ancak sınıflarından farklı olarak, uygulama arabirimleri sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="ee383-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="ee383-266">Bunlar sınıfları tarafından uygulanan ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ee383-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="ee383-267">Tam olarak tanımlandığı şekilde bir arabirimini uygulayan bir sınıf her açıdan bu arabirimi uygulamalıdır içeren bir sözleşme bir arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee383-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="ee383-268">Bir arabirim tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="ee383-269">Bir sınıfta bir arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="ee383-270">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="ee383-270">For more information, see:</span></span>

- [<span data-ttu-id="ee383-271">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ee383-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  

- [<span data-ttu-id="ee383-272">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  

- [<span data-ttu-id="ee383-273">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  

## <a name="generics"></a><span data-ttu-id="ee383-274">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="ee383-274">Generics</span></span>
<span data-ttu-id="ee383-275">Sınıflar, yapılar, arabirimler ve .NET yöntemleri dahil edebileceğiniz *tür parametrelerindeki* kullanan depolamak veya nesne türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ee383-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="ee383-276">Genel türler en yaygın örneği, bir koleksiyonda depolanan nesnelerin türü belirtebileceğiniz koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="ee383-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  

<span data-ttu-id="ee383-277">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="ee383-278">Genel bir sınıf örneği oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="ee383-279">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="ee383-279">For more information, see:</span></span>

- [<span data-ttu-id="ee383-280">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="ee383-280">Generics</span></span>](~/docs/standard/generics/index.md)

- [<span data-ttu-id="ee383-281">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="ee383-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="ee383-282">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="ee383-282">Delegates</span></span>
 <span data-ttu-id="ee383-283">A *temsilci* yöntem imzası tanımlar türüdür ve herhangi bir yöntem başvuru ile uyumlu bir imzası sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ee383-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="ee383-284">Çağırma (çağrı yöntemi temsilci aracılığıyla veya).</span><span class="sxs-lookup"><span data-stu-id="ee383-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="ee383-285">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee383-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
>  <span data-ttu-id="ee383-286">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="ee383-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="ee383-287">Olay işlemede kullanma hakkında daha fazla bilgi için bkz: [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="ee383-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="ee383-288">Bir temsilciyi oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="ee383-289">Temsilci tarafından belirtilen imza eşleşen bir yöntem başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="ee383-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="ee383-290">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="ee383-290">For more information, see:</span></span>

- [<span data-ttu-id="ee383-291">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="ee383-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)

- [<span data-ttu-id="ee383-292">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee383-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="ee383-293">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="ee383-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="ee383-294">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee383-294">See also</span></span>
 [<span data-ttu-id="ee383-295">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ee383-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
