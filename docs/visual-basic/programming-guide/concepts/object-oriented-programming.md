---
title: Nesne yönelimli programlama
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 3739919273f4cdd285d519c414c542f1a82a16d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400689"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="ca477-102">Nesne yönelimli programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca477-102">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="ca477-103">Visual Basic kapsülleme, kalıtım ve çok biçimlilik gibi nesne yönelimli programlama için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca477-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="ca477-104">*Kapsülleme,* ilgili özellikler, yöntemler ve diğer üyelerden oluşan bir grubun tek bir birim veya nesne olarak kabul edilsi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ca477-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="ca477-105">*Devralma,* varolan bir sınıfa dayalı yeni sınıflar oluşturma yeteneğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca477-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="ca477-106">*Çok biçimlilik,* her sınıf aynı özellikleri veya yöntemleri farklı şekillerde uygulasa bile, birbirinin yerine kullanılabilecek birden çok sınıfa sahip olabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ca477-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="ca477-107">Bu bölümde aşağıdaki kavramlar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="ca477-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="ca477-108">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="ca477-108">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="ca477-109">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="ca477-109">Class members</span></span>](#class-members)
    - [<span data-ttu-id="ca477-110">Özellikler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="ca477-110">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="ca477-111">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ca477-111">Methods</span></span>](#methods)
    - [<span data-ttu-id="ca477-112">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ca477-112">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="ca477-113">Yıkıcılar</span><span class="sxs-lookup"><span data-stu-id="ca477-113">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="ca477-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ca477-114">Events</span></span>](#events)
    - [<span data-ttu-id="ca477-115">İç içe sınıflar</span><span class="sxs-lookup"><span data-stu-id="ca477-115">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="ca477-116">Değiştiricilere ve erişim düzeylerine erişin</span><span class="sxs-lookup"><span data-stu-id="ca477-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="ca477-117">Anında sınıflar</span><span class="sxs-lookup"><span data-stu-id="ca477-117">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="ca477-118">Paylaşılan sınıflar ve üyeler</span><span class="sxs-lookup"><span data-stu-id="ca477-118">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="ca477-119">Anonim türleri</span><span class="sxs-lookup"><span data-stu-id="ca477-119">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="ca477-120">Devralma</span><span class="sxs-lookup"><span data-stu-id="ca477-120">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="ca477-121">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="ca477-121">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="ca477-122">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ca477-122">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="ca477-123">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="ca477-123">Generics</span></span>](#generics)
- [<span data-ttu-id="ca477-124">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="ca477-124">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="ca477-125">Sınıflar ve nesneler</span><span class="sxs-lookup"><span data-stu-id="ca477-125">Classes and objects</span></span>

<span data-ttu-id="ca477-126">*Sınıf* ve *nesne* terimleri bazen birbirinin yerine kullanılır, ancak aslında sınıflar nesnelerin *türünü* açıklarken, nesneler kullanılabilir sınıf *örnekleridir.*</span><span class="sxs-lookup"><span data-stu-id="ca477-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="ca477-127">Yani, bir nesne oluşturma eylemine *anlık hareket*denir.</span><span class="sxs-lookup"><span data-stu-id="ca477-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="ca477-128">Plan benzetmesini kullanarak, sınıf bir plandır ve bir nesne de bu plandan yapılmış bir binadır.</span><span class="sxs-lookup"><span data-stu-id="ca477-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="ca477-129">Bir sınıfı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-129">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="ca477-130">Visual Basic ayrıca, büyük bir nesne dizisi oluşturmanız gerektiğinde yararlı olan ve bunun için çok fazla bellek tüketmek istemediğinde yararlı olan *yapılar* adı verilen sınıfların hafif bir sürümünü de sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca477-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="ca477-131">Bir yapıtanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-131">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="ca477-132">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="ca477-132">For more information, see:</span></span>

- [<span data-ttu-id="ca477-133">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca477-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="ca477-134">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca477-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="ca477-135">Sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="ca477-135">Class members</span></span>

<span data-ttu-id="ca477-136">Her *sınıfın,* sınıf verilerini açıklayan özellikleri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasında iletişim sağlayan olayları içeren farklı sınıf üyeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="ca477-137">Özellikler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="ca477-137">Properties and fields</span></span>

<span data-ttu-id="ca477-138">Alanlar ve özellikler, nesnenin içerdiği bilgileri temsil ediyor.</span><span class="sxs-lookup"><span data-stu-id="ca477-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="ca477-139">Alanlar, doğrudan okunabildikleri veya ayarlanabildikleri için değişkenler gibidir.</span><span class="sxs-lookup"><span data-stu-id="ca477-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="ca477-140">Bir alanı tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="ca477-141">Özellikler, değerlerin nasıl ayarlandığı veya döndürüldüğü konusunda daha fazla denetim sağlayan yordamları alırıp ayarla</span><span class="sxs-lookup"><span data-stu-id="ca477-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="ca477-142">Visual Basic, özellik değerini depolamak için özel bir alan oluşturmanıza veya bu alanı otomatik olarak arka planda oluşturan ve özellik yordamları için temel mantığı sağlayan otomatik olarak uygulanan özellikleri kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ca477-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="ca477-143">Otomatik olarak uygulanan bir özelliği tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="ca477-144">Özellik değerini okumak ve yazmak için bazı ek işlemler gerçekleştirmeniz gerekiyorsa, özellik değerini depolamak için bir alan tanımlayın ve depolamak ve almak için temel mantığı sağlayın:</span><span class="sxs-lookup"><span data-stu-id="ca477-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="ca477-145">Çoğu özelliğin hem ayarlayıp hem de özellik değerini almak için yöntemleri veya yordamları vardır.</span><span class="sxs-lookup"><span data-stu-id="ca477-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="ca477-146">Ancak, değiştirilmelerini veya okunmasını kısıtlamak için salt okunur veya yalnızca yazma özellikleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca477-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="ca477-147">Visual Basic'te `ReadOnly` anahtar `WriteOnly` kelimeleri ve anahtar kelimeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca477-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="ca477-148">Ancak, otomatik olarak uygulanan özellikler salt okunur veya yalnızca yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="ca477-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="ca477-149">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="ca477-149">For more information, see:</span></span>

- [<span data-ttu-id="ca477-150">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca477-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="ca477-151">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca477-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="ca477-152">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca477-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="ca477-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="ca477-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="ca477-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="ca477-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="ca477-155">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ca477-155">Methods</span></span>

 <span data-ttu-id="ca477-156">*Yöntem,* bir nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="ca477-156">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="ca477-157">Visual Basic'te bir yöntem oluşturmanın iki `Sub` yolu vardır: yöntem bir değer döndürmüyorsa deyim kullanılır; `Function` bir yöntem bir değer döndürürse deyim kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ca477-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="ca477-158">Bir sınıfın yöntemini tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="ca477-159">Bir sınıfın, parametre veya parametre türlerinin sayısında farklılık gösteren aynı yöntemin birkaç uygulaması veya *aşırı yüklemesi*olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="ca477-160">Bir yöntemi aşırı yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="ca477-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="ca477-161">Çoğu durumda bir sınıf tanımı içinde bir yöntem bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca477-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="ca477-162">Ancak, Visual Basic, sınıfın gerçek tanımı dışında varolan bir sınıfa yöntem eklemenize olanak tanıyan *uzantı yöntemlerini* de destekler.</span><span class="sxs-lookup"><span data-stu-id="ca477-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="ca477-163">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="ca477-163">For more information, see:</span></span>

- [<span data-ttu-id="ca477-164">Fonksiyon Bildirimi</span><span class="sxs-lookup"><span data-stu-id="ca477-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="ca477-165">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca477-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ca477-166">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="ca477-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="ca477-167">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ca477-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="ca477-168">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ca477-168">Constructors</span></span>

<span data-ttu-id="ca477-169">Oluşturucular, belirli bir türdeki bir nesne oluşturulduğunda otomatik olarak yürütülen sınıf yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="ca477-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="ca477-170">Oluşturucular genellikle yeni nesnenin veri üyelerini başlangıç olarak karşılarlar.</span><span class="sxs-lookup"><span data-stu-id="ca477-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="ca477-171">Bir oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="ca477-172">Ayrıca, oluşturucudaki kod her zaman bir sınıftaki başka bir koddan önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="ca477-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="ca477-173">Ancak, birden çok oluşturucu başka bir yöntemle aynı şekilde aşırı yüklemeler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca477-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="ca477-174">Bir sınıf için bir oluşturucu tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="ca477-175">Daha fazla bilgi için bkz: [Nesne Yaşam Süresi: Nesneler Nasıl Oluşturulur ve Yok Edilir.](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="ca477-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="ca477-176">Yıkıcılar</span><span class="sxs-lookup"><span data-stu-id="ca477-176">Destructors</span></span>

<span data-ttu-id="ca477-177">Yıkıcılar sınıfların örneklerini yok etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ca477-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="ca477-178">.NET Framework'de, çöp toplayıcı, uygulamanızdaki yönetilen nesneler için bellek tahsisini ve serbest bırakılmasını otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="ca477-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="ca477-179">Ancak, uygulamanızın oluşturduğu yönetilmeyen kaynakları temizlemek için yine de yıkıcılara ihtiyacınız olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="ca477-180">Bir sınıf için sadece bir yıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="ca477-181">.NET Framework'de yıkıcılar ve çöp toplama hakkında daha fazla bilgi için [Bkz.](../../../standard/garbage-collection/index.md)</span><span class="sxs-lookup"><span data-stu-id="ca477-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="ca477-182">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ca477-182">Events</span></span>

<span data-ttu-id="ca477-183">Olaylar, ilgi çekici bir şey oluştuğunda bir sınıfın veya nesnenin diğer sınıfları veya nesneleri bildirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca477-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="ca477-184">Olayı gönderen (veya yükselten) sınıfa *yayımcı,* olayı alan (veya işleyen) sınıflara *abone*denir.</span><span class="sxs-lookup"><span data-stu-id="ca477-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="ca477-185">Olaylar hakkında daha fazla bilgi için, bunların nasıl yükseltildiği ve işlendiği [hakkında](../../../standard/events/index.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="ca477-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="ca477-186">Olayları bildirmek için [Olay Bildirimi'ni](../../../visual-basic/language-reference/statements/event-statement.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca477-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="ca477-187">Olayları yükseltmek için [RaiseEvent Bildirimi'ni](../../../visual-basic/language-reference/statements/raiseevent-statement.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca477-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="ca477-188">Olay işleyicilerini bildirimsel bir yol kullanarak belirtmek [için, WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) deyimini ve [İşleştiler](../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca477-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="ca477-189">Bir olayla ilişkili olay işleyicisini dinamik olarak ekleyebilmek, kaldırabilmek ve değiştirebilmek için, [İşleç'in Adresi](../../../visual-basic/language-reference/operators/addressof-operator.md)ile birlikte AddHandler Bildirimi ni ve [RemoveHandler Bildirimini](../../../visual-basic/language-reference/statements/addhandler-statement.md) kullanın. [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md)</span><span class="sxs-lookup"><span data-stu-id="ca477-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="ca477-190">İç içe sınıflar</span><span class="sxs-lookup"><span data-stu-id="ca477-190">Nested classes</span></span>

<span data-ttu-id="ca477-191">Başka bir sınıf içinde tanımlanan bir sınıf *iç içe*denir.</span><span class="sxs-lookup"><span data-stu-id="ca477-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="ca477-192">Varsayılan olarak, iç içe sınıf özeldir.</span><span class="sxs-lookup"><span data-stu-id="ca477-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="ca477-193">İç içe sınıf bir örnek oluşturmak için, nokta ardından kapsayıcı sınıfın adını ve ardından iç içe sınıf adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="ca477-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="ca477-194">Değiştiricilere ve erişim düzeylerine erişin</span><span class="sxs-lookup"><span data-stu-id="ca477-194">Access modifiers and access levels</span></span>

<span data-ttu-id="ca477-195">Tüm sınıflar ve sınıf *üyeleri, erişim değiştiriciler*kullanarak diğer sınıflara hangi erişim düzeyini sağladıklarını belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="ca477-196">Aşağıdaki erişim değiştiriciler kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ca477-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="ca477-197">Görsel Temel Değiştirici</span><span class="sxs-lookup"><span data-stu-id="ca477-197">Visual Basic Modifier</span></span>|<span data-ttu-id="ca477-198">Tanım</span><span class="sxs-lookup"><span data-stu-id="ca477-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="ca477-199">Genel</span><span class="sxs-lookup"><span data-stu-id="ca477-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="ca477-200">Türe veya üyeye, aynı derlemedeki veya ona başvuran başka bir derlemedeki başka bir kod erişebilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="ca477-201">Özel</span><span class="sxs-lookup"><span data-stu-id="ca477-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="ca477-202">Türe veya üyeye yalnızca aynı sınıftaki kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="ca477-203">Korumalı</span><span class="sxs-lookup"><span data-stu-id="ca477-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="ca477-204">Türe veya üyeye yalnızca aynı sınıftaveya türemiş bir sınıfta kodla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="ca477-205">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="ca477-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="ca477-206">Türe veya üyeye aynı derlemedeki herhangi bir kod erişebilir, ancak başka bir derlemeden erişilemez.</span><span class="sxs-lookup"><span data-stu-id="ca477-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="ca477-207">Türe veya üyeye aynı derlemedeki herhangi bir kod veya başka bir derlemedeki herhangi bir türemiş sınıf erişebilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="ca477-208">Daha fazla bilgi için [Visual Basic'teki Access düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ca477-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="ca477-209">Anında sınıflar</span><span class="sxs-lookup"><span data-stu-id="ca477-209">Instantiating classes</span></span>

<span data-ttu-id="ca477-210">Bir nesne oluşturmak için, bir sınıfı anında oluşturmanız veya bir sınıf örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca477-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="ca477-211">Bir sınıfı anında yaptıktan sonra, örnek özelliklerine ve alanlarına değerler atayabilir ve sınıf yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca477-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="ca477-212">Sınıf anlık işlem sırasında özelliklerine değer atamak için nesne baş harflerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="ca477-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="ca477-213">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="ca477-213">For more information, see:</span></span>

- [<span data-ttu-id="ca477-214">Yeni Operatör</span><span class="sxs-lookup"><span data-stu-id="ca477-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="ca477-215">Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="ca477-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="ca477-216">Paylaşılan sınıflar ve üyeler</span><span class="sxs-lookup"><span data-stu-id="ca477-216">Shared classes and members</span></span>

 <span data-ttu-id="ca477-217">Sınıfın paylaşılan bir üyesi, sınıfın tüm örnekleri tarafından paylaşılan bir özellik, yordam veya alandır.</span><span class="sxs-lookup"><span data-stu-id="ca477-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="ca477-218">Paylaşılan bir üyeyi tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-218">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="ca477-219">Paylaşılan üyeye erişmek için, bu sınıfın bir nesnesini oluşturmadan sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="ca477-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="ca477-220">Visual Basic'teki paylaşılan modüller yalnızca üyeleri paylaştı ve anlık olarak paylaşılamaz.</span><span class="sxs-lookup"><span data-stu-id="ca477-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="ca477-221">Paylaşılan üyeler ayrıca paylaşılmayan özelliklere, alanlara veya yöntemlere erişemez</span><span class="sxs-lookup"><span data-stu-id="ca477-221">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="ca477-222">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="ca477-222">For more information, see:</span></span>

- [<span data-ttu-id="ca477-223">Paylaşımlı</span><span class="sxs-lookup"><span data-stu-id="ca477-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="ca477-224">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca477-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="ca477-225">Anonim türleri</span><span class="sxs-lookup"><span data-stu-id="ca477-225">Anonymous types</span></span>

<span data-ttu-id="ca477-226">Anonim türler, veri türü için sınıf tanımı yazmadan nesneler oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ca477-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="ca477-227">Bunun yerine, derleyici sizin için bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ca477-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="ca477-228">Sınıfın kullanılabilir bir adı yoktur ve nesneyi bildirirken belirttiğiniz özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ca477-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="ca477-229">Anonim bir tür örneği oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="ca477-230">Daha fazla bilgi için bkz: [Anonim Türleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="ca477-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="ca477-231">Devralma</span><span class="sxs-lookup"><span data-stu-id="ca477-231">Inheritance</span></span>

<span data-ttu-id="ca477-232">Devralma, başka bir sınıfta tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni bir sınıf oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ca477-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="ca477-233">Üyeleri devralınan *sınıfa taban sınıf,* bu üyeleri devralan sınıfa *ise türemiş sınıf*denir.</span><span class="sxs-lookup"><span data-stu-id="ca477-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="ca477-234">Ancak, Visual Basic'teki tüm sınıflar <xref:System.Object> ,.NET sınıf hiyerarşisini destekleyen ve tüm sınıflara düşük düzeyli hizmetler sağlayan sınıftan örtülü olarak devralır.</span><span class="sxs-lookup"><span data-stu-id="ca477-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="ca477-235">Visual Basic birden çok devralmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ca477-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="ca477-236">Diğer bir tanesi, türemiş bir sınıf için yalnızca bir taban sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca477-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="ca477-237">Taban sınıftan devralmak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="ca477-238">Varsayılan olarak tüm sınıflar devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-238">By default all classes can be inherited.</span></span> <span data-ttu-id="ca477-239">Ancak, bir sınıfın taban sınıf olarak kullanılmaması mı yoksa yalnızca taban sınıf olarak kullanılabilecek bir sınıf oluşturup oluşturmayacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca477-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="ca477-240">Bir sınıfın taban sınıf olarak kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="ca477-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="ca477-241">Bir sınıfın yalnızca taban sınıf olarak kullanılabileceğini ve anında kullanılamayacağını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="ca477-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="ca477-242">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="ca477-242">For more information, see:</span></span>

- [<span data-ttu-id="ca477-243">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca477-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="ca477-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="ca477-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="ca477-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="ca477-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="ca477-246">Üyeleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="ca477-246">Overriding members</span></span>

<span data-ttu-id="ca477-247">Varsayılan olarak, türetilmiş bir sınıf tüm üyeleri taban sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="ca477-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="ca477-248">Devralınan üyenin davranışını değiştirmek istiyorsanız, bunu geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca477-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="ca477-249">Diğer bir deyişle, türemiş sınıfta yöntem, özellik veya olay yeni bir uygulama tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca477-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="ca477-250">Aşağıdaki değiştiriciler özelliklerin ve yöntemlerin nasıl geçersiz kılındığını denetlemek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="ca477-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="ca477-251">Görsel Temel Değiştirici</span><span class="sxs-lookup"><span data-stu-id="ca477-251">Visual Basic Modifier</span></span>|<span data-ttu-id="ca477-252">Tanım</span><span class="sxs-lookup"><span data-stu-id="ca477-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="ca477-253">Geçersiz Kılınabilir</span><span class="sxs-lookup"><span data-stu-id="ca477-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="ca477-254">Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="ca477-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="ca477-255">Overrides</span><span class="sxs-lookup"><span data-stu-id="ca477-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="ca477-256">Taban sınıfta tanımlanan sanal (geçersiz kılınabilir) bir üyeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ca477-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="ca477-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="ca477-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="ca477-258">Bir üyenin devralan bir sınıfta geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="ca477-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="ca477-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="ca477-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="ca477-260">Bir sınıf üyesinin türemiş sınıfta geçersiz kılınmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ca477-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="ca477-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="ca477-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="ca477-262">Taban sınıftan devralınan bir üyeyi gizler</span><span class="sxs-lookup"><span data-stu-id="ca477-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="ca477-263">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ca477-263">Interfaces</span></span>

<span data-ttu-id="ca477-264">Arabirimler, sınıflar gibi, özellikler, yöntemler ve olaylar kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ca477-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="ca477-265">Ancak sınıfların aksine, arabirimler uygulama sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="ca477-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="ca477-266">Sınıflar tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ca477-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="ca477-267">Arabirim, arabirimi uygulayan bir sınıfın bu arabirimin her yönünü tam olarak tanımlandığı şekilde uygulaması gerektiğinden, bir sözleşmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ca477-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="ca477-268">Arabirimi tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="ca477-269">Bir sınıfta arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="ca477-270">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="ca477-270">For more information, see:</span></span>

- [<span data-ttu-id="ca477-271">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ca477-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [<span data-ttu-id="ca477-272">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca477-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="ca477-273">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca477-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="ca477-274">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="ca477-274">Generics</span></span>

<span data-ttu-id="ca477-275">.NET'teki sınıflar, yapılar, arabirimler ve yöntemler, depolayabildikleri veya kullanabilecekleri nesne türlerini tanımlayan *tür parametreleri* içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ca477-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="ca477-276">Jeneriklerin en yaygın örneği, koleksiyonda depolanacak nesnelerin türünü belirtebileceğiniz bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="ca477-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="ca477-277">Genel bir sınıf tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="ca477-278">Genel bir sınıfın örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="ca477-279">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="ca477-279">For more information, see:</span></span>

- [<span data-ttu-id="ca477-280">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="ca477-280">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="ca477-281">Visual Basic'te Genel Türler</span><span class="sxs-lookup"><span data-stu-id="ca477-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="ca477-282">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="ca477-282">Delegates</span></span>

 <span data-ttu-id="ca477-283">*Temsilci,* yöntem imzasını tanımlayan ve uyumlu imzası olan herhangi bir yönteme başvuru sağlayan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="ca477-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="ca477-284">Temsilci aracılığıyla yöntemi çağırabilir (veya çağırabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="ca477-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="ca477-285">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ca477-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="ca477-286">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="ca477-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="ca477-287">Etkinlik işlemede temsilci kullanma hakkında daha fazla bilgi için [Etkinlikler'e](../../../standard/events/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ca477-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="ca477-288">Bir temsilci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="ca477-289">Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="ca477-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="ca477-290">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="ca477-290">For more information, see:</span></span>

- [<span data-ttu-id="ca477-291">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="ca477-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="ca477-292">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca477-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="ca477-293">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="ca477-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="ca477-294">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca477-294">See also</span></span>

- [<span data-ttu-id="ca477-295">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ca477-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
