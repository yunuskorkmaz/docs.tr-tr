---
title: Özellikler
description: Bilgi C# hakkında değerleri, geç değerlendirme doğrulama için özellikler, Özellikler hesaplanır ve özelliği bildirimleri değiştirildi.
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.openlocfilehash: 05e51d527dc3c05301fc85d7717c751dc46bf9fa
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="properties"></a><span data-ttu-id="257b6-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="257b6-104">Properties</span></span>

<span data-ttu-id="257b6-105">C# birinci sınıf kullanıcılarının özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="257b6-105">Properties are first class citizens in C#.</span></span> <span data-ttu-id="257b6-106">Dil kendi tasarım hedefi doğru şekilde ifade kod yazmaya geliştiricilerinin sözdizimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="257b6-106">The language defines syntax that enables developers to write code that accurately expresses their design intent.</span></span>

<span data-ttu-id="257b6-107">Bunlar erişildiğinde özellikleri alanlar gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="257b6-107">Properties behave like fields when they are accessed.</span></span>
<span data-ttu-id="257b6-108">Ancak, alanları, bir özellik erişilen veya atandığında, yürütülen deyimleri tanımlayan erişimciler ile özellikleri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="257b6-108">However, unlike fields, properties are implemented with accessors that define the statements executed when a property is accessed or assigned.</span></span>

## <a name="property-syntax"></a><span data-ttu-id="257b6-109">Özellik sözdizimi</span><span class="sxs-lookup"><span data-stu-id="257b6-109">Property Syntax</span></span>

<span data-ttu-id="257b6-110">Özellikleri için sözdizimi, alanlar için doğal bir uzantıdır.</span><span class="sxs-lookup"><span data-stu-id="257b6-110">The syntax for properties is a natural extension to fields.</span></span> <span data-ttu-id="257b6-111">Bir alan bir depolama konumu tanımlar:</span><span class="sxs-lookup"><span data-stu-id="257b6-111">A field defines a storage location:</span></span>

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="257b6-112">Bildirimler için bir özellik tanımını içeren bir `get` ve `set` alır ve bu özelliğin değeri atayan erişimcisi:</span><span class="sxs-lookup"><span data-stu-id="257b6-112">A property definition contains declarations for a `get` and `set` accessor that retrieves and assigns the value of that property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="257b6-113">Yukarıda gösterilen sözdizimi *otomatik özelliği* sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="257b6-113">The syntax shown above is the *auto property* syntax.</span></span> <span data-ttu-id="257b6-114">Derleyici özelliği yedekler alanı için depolama konumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="257b6-114">The compiler generates the storage location for the field that backs up the property.</span></span> <span data-ttu-id="257b6-115">Derleyici de gövdesini uygulayan `get` ve `set` erişimciler.</span><span class="sxs-lookup"><span data-stu-id="257b6-115">The compiler also implements the body of the `get` and `set` accessors.</span></span>

<span data-ttu-id="257b6-116">Bazı durumlarda, bir özellik türü için varsayılan farklı bir değere başlatmak için gerekir.</span><span class="sxs-lookup"><span data-stu-id="257b6-116">Sometimes, you need to initialize a property to a value other than the default for its type.</span></span>  <span data-ttu-id="257b6-117">C#, sonra kapanış ayracı özelliği için bir değer ayarlanarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="257b6-117">C# enables that by setting a value after the closing brace for the property.</span></span> <span data-ttu-id="257b6-118">İlk değeri tercih edebilirsiniz `FirstName` boş dize özelliğini yerine `null`.</span><span class="sxs-lookup"><span data-stu-id="257b6-118">You may prefer the initial value for the `FirstName` property to be the empty string rather than `null`.</span></span> <span data-ttu-id="257b6-119">Aşağıda gösterildiği gibi belirtmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="257b6-119">You would specify that as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

<span data-ttu-id="257b6-120">Bu konunun ilerleyen bölümlerinde anlatıldığı gibi bu salt okunur özellikler için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="257b6-120">This is most useful for read-only properties, as you'll see later in this topic.</span></span>

<span data-ttu-id="257b6-121">Aşağıda gösterildiği gibi depolama kendiniz de tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="257b6-121">You can also define the storage yourself, as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="257b6-122">Bir özellik uygulama tek bir ifade olduğunda kullanabileceğiniz *ifade bodied üyeleri* alıcı veya ayarlayıcı için:</span><span class="sxs-lookup"><span data-stu-id="257b6-122">When a property implementation is a single expression, you can use *expression-bodied members* for the getter or setter:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="257b6-123">Bu Basitleştirilmiş söz dizimi, bu konuda boyunca uygunsa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="257b6-123">This simplified syntax will be used where applicable throughout this topic.</span></span>

<span data-ttu-id="257b6-124">Yukarıda gösterilen özellik tanımı bir okuma-yazma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="257b6-124">The property definition shown above is a read-write property.</span></span> <span data-ttu-id="257b6-125">Anahtar sözcüğü fark `value` set erişimcisi içinde.</span><span class="sxs-lookup"><span data-stu-id="257b6-125">Notice the keyword `value` in the set accessor.</span></span> <span data-ttu-id="257b6-126">`set` Erişimcisine sahip her zaman adlı tek bir parametre `value`.</span><span class="sxs-lookup"><span data-stu-id="257b6-126">The `set` accessor always has a single parameter named `value`.</span></span> <span data-ttu-id="257b6-127">`get` Erişimci özelliği türüne dönüştürülebilir olan bir değer döndürmesi gerekir (`string` Bu örnekte).</span><span class="sxs-lookup"><span data-stu-id="257b6-127">The `get` accessor must return a value that is convertible to the type of the property (`string` in this example).</span></span>
 
<span data-ttu-id="257b6-128">Sözdizimi temelleri olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="257b6-128">That's the basics of the syntax.</span></span> <span data-ttu-id="257b6-129">Farklı tasarım deyimleri çeşitli destek pek çok farklı Çeşitleme vardır.</span><span class="sxs-lookup"><span data-stu-id="257b6-129">There are many different variations that support a variety of different design idioms.</span></span> <span data-ttu-id="257b6-130">Şimdi bu keşfedin ve her sözdizimi seçenekleri öğrenin.</span><span class="sxs-lookup"><span data-stu-id="257b6-130">Let's explore those, and learn the syntax options for each.</span></span>

## <a name="scenarios"></a><span data-ttu-id="257b6-131">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="257b6-131">Scenarios</span></span>

<span data-ttu-id="257b6-132">Yukarıdaki örneklerde gösterilen özellik tanımı, basit bir durumda birini: hiçbir doğrulama okuma-yazma özelliğiyle.</span><span class="sxs-lookup"><span data-stu-id="257b6-132">The examples above showed one of the simplest cases of property definition: a read-write property with no validation.</span></span> <span data-ttu-id="257b6-133">Kod yazarak istediğiniz `get` ve `set` erişimciler, birçok farklı senaryolar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="257b6-133">By writing the code you want in the `get` and `set` accessors, you can create many different scenarios.</span></span>

### <a name="validation"></a><span data-ttu-id="257b6-134">Doğrulama</span><span class="sxs-lookup"><span data-stu-id="257b6-134">Validation</span></span>

<span data-ttu-id="257b6-135">Kod yazabilirsiniz `set` erişimci özelliği tarafından temsil edilen değerler her zaman geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="257b6-135">You can write code in the `set` accessor to ensure that the values represented by a property are always valid.</span></span> <span data-ttu-id="257b6-136">Örneğin, bir kural için varsayalım `Person` sınıftır adı boş veya boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="257b6-136">For example, suppose one rule for the `Person` class is that the name cannot be blank or white space.</span></span> <span data-ttu-id="257b6-137">Aşağıdaki gibi yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="257b6-137">You would write that as follows:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="257b6-138">Yukarıdaki örnekte kuralı adı boş olmamalı veya boşluk zorlar.</span><span class="sxs-lookup"><span data-stu-id="257b6-138">The example above enforces the rule that the first name must not be blank or white space.</span></span> <span data-ttu-id="257b6-139">Bir geliştirici yazıyorsa</span><span class="sxs-lookup"><span data-stu-id="257b6-139">If a developer writes</span></span>

```csharp
hero.FirstName = "";
```

<span data-ttu-id="257b6-140">Bu atama oluşturur bir `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="257b6-140">That assignment throws an `ArgumentException`.</span></span> <span data-ttu-id="257b6-141">Dönüş türü void özellik bir set erişimcisine sahip olması gerektiğinden, bir özel durum atma tarafından set erişimcisine hataları rapor.</span><span class="sxs-lookup"><span data-stu-id="257b6-141">Because a property set accessor must have a void return type, you report errors in the set accessor by throwing an exception.</span></span>

<span data-ttu-id="257b6-142">Bu, doğrulama basit bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="257b6-142">That is a simple case of validation.</span></span> <span data-ttu-id="257b6-143">Bu aynı sözdizimini senaryonuzda gereken herhangi bir şeye genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="257b6-143">You can extend this same syntax to anything needed in your scenario.</span></span> <span data-ttu-id="257b6-144">Farklı özellikler arasındaki ilişkileri denetleyin veya karşı dış koşulları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="257b6-144">You can check the relationships between different properties, or validate against any external conditions.</span></span> <span data-ttu-id="257b6-145">Geçerli bir C# ifadelerinin içinde bir özellik erişimcisini geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="257b6-145">Any valid C# statements are valid in a property accessor.</span></span>

### <a name="read-only"></a><span data-ttu-id="257b6-146">Salt okunur</span><span class="sxs-lookup"><span data-stu-id="257b6-146">Read-only</span></span>

<span data-ttu-id="257b6-147">Bu noktaya kadar açtığınız tüm özellik tanımları ortak erişimciler ile okuma/yazma özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="257b6-147">Up to this point, all the property definitions you have seen are read/write properties with public accessors.</span></span> <span data-ttu-id="257b6-148">Bu özellikler için geçerli tek erişilebilirlik değil.</span><span class="sxs-lookup"><span data-stu-id="257b6-148">That's not the only valid accessibility for properties.</span></span>
<span data-ttu-id="257b6-149">Salt okunur özellikler oluşturun veya farklı erişilebilirlik kümesine verin ve erişimciler alın.</span><span class="sxs-lookup"><span data-stu-id="257b6-149">You can create read-only properties, or give different accessibility to the set and get accessors.</span></span> <span data-ttu-id="257b6-150">Varsayın, `Person` sınıfı, değerinin değiştirilmesi yalnızca etkinleştirmelisiniz `FirstName` o sınıfın diğer yöntemlerle özelliğinden.</span><span class="sxs-lookup"><span data-stu-id="257b6-150">Suppose that your `Person` class should only enable changing the value of the `FirstName` property from other methods in that class.</span></span> <span data-ttu-id="257b6-151">Set erişimcisine sunabilir `private` yerine erişilebilirlik `public`:</span><span class="sxs-lookup"><span data-stu-id="257b6-151">You could give the set accessor `private` accessibility instead of `public`:</span></span>

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="257b6-152">Şimdi, `FirstName` özelliği herhangi bir kodda erişilebilir, ancak diğer koddan yalnızca atanabilir `Person` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="257b6-152">Now, the `FirstName` property can be accessed from any code, but it can only be assigned from other code in the `Person` class.</span></span>

<span data-ttu-id="257b6-153">Herhangi bir kısıtlayıcı erişim değiştiricisi ya da kümesi ekleyin veya erişimciler alın.</span><span class="sxs-lookup"><span data-stu-id="257b6-153">You can add any restrictive access modifier to either the set or get accessors.</span></span> <span data-ttu-id="257b6-154">Tek tek erişimcisine yerleştirin herhangi bir erişim değiştiricisi özellik tanımı üzerinde erişim değiştiricisi daha kısıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="257b6-154">Any access modifier you place on the individual accessor must be more limited than the access modifier on the property definition.</span></span> <span data-ttu-id="257b6-155">Yukarıdaki yasal olduğundan `FirstName` özelliği `public`, ancak set erişimcisine `private`.</span><span class="sxs-lookup"><span data-stu-id="257b6-155">The above is legal because the `FirstName` property is `public`, but the set accessor is `private`.</span></span> <span data-ttu-id="257b6-156">Değil bildirebilirsiniz bir `private` özelliği ile bir `public` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="257b6-156">You could not declare a `private` property with a `public` accessor.</span></span> <span data-ttu-id="257b6-157">Özellik bildirimleri de bildirilebilir `protected`, `internal`, `protected internal`, `private protected` ve hatta `private`.</span><span class="sxs-lookup"><span data-stu-id="257b6-157">Property declarations can also be declared `protected`, `internal`, `protected internal`, `private protected` or even `private`.</span></span>   

<span data-ttu-id="257b6-158">Daha kısıtlayıcı değiştiricisi yerleştirmek için uygundur `get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="257b6-158">It is also legal to place the more restrictive modifier on the `get` accessor.</span></span> <span data-ttu-id="257b6-159">Örneğin, olabilir bir `public` özelliği, ancak kısıtlamak `get` erişimcisi için `private`.</span><span class="sxs-lookup"><span data-stu-id="257b6-159">For example, you could have a `public` property, but restrict the `get` accessor to `private`.</span></span> <span data-ttu-id="257b6-160">Bu senaryo, uygulamada nadiren yapılır.</span><span class="sxs-lookup"><span data-stu-id="257b6-160">That scenario is rarely done in practice.</span></span>

<span data-ttu-id="257b6-161">Böylece bir oluşturucu veya özellik başlatıcı yalnızca ayarlanabilir bir özellik değişiklikler de kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="257b6-161">You can also restrict modifications to a property so that it can only be set in a constructor or a property initializer.</span></span> <span data-ttu-id="257b6-162">Değiştirebileceğiniz `Person` bunu aşağıdaki gibi sınıfı:</span><span class="sxs-lookup"><span data-stu-id="257b6-162">You can modify the `Person` class so as follows:</span></span>

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="257b6-163">Bu özellik salt okunur özellikler olarak sunulan koleksiyonları başlatmak için en yaygın olarak kullanılır:</span><span class="sxs-lookup"><span data-stu-id="257b6-163">This feature is most commonly used for initializing collections that are exposed as read-only properties:</span></span>

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a><span data-ttu-id="257b6-164">Hesaplanan özellikleri</span><span class="sxs-lookup"><span data-stu-id="257b6-164">Computed Properties</span></span>

<span data-ttu-id="257b6-165">Bir özelliği yalnızca bir üye alanın değerini döndürmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="257b6-165">A property does not need to simply return the value of a member field.</span></span> <span data-ttu-id="257b6-166">Hesaplanan değeri döndüren özellikleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="257b6-166">You can create properties that return a computed value.</span></span> <span data-ttu-id="257b6-167">Şimdi genişletin `Person` nesne adları ve soyadları birleştirerek hesaplanan tam adını döndürmek için:</span><span class="sxs-lookup"><span data-stu-id="257b6-167">Let's expand the `Person` object to return the full name, computed by concatenating the first and last names:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

<span data-ttu-id="257b6-168">Kullandığı Yukarıdaki örnek [dize ilişkilendirme](../csharp/language-reference/tokens/interpolated.md) biçimlendirilmiş dize tam adı oluşturmak için özellik.</span><span class="sxs-lookup"><span data-stu-id="257b6-168">The example above uses the [string interpolation](../csharp/language-reference/tokens/interpolated.md) feature to create the formatted string for the full name.</span></span>

<span data-ttu-id="257b6-169">De kullanabilirsiniz *ifade bodied üyeleri*, hesaplanan oluşturmak için daha kısa bir yol sağlayan `FullName` özelliği:</span><span class="sxs-lookup"><span data-stu-id="257b6-169">You can also use *expression-bodied members*, which provides a more succinct way to create the computed `FullName` property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
<span data-ttu-id="257b6-170">*İfade bodied üyeleri* kullanmak *lambda ifadesi* tek bir ifade içeren bir yöntemi tanımlamak için sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="257b6-170">*Expression-bodied members* use the *lambda expression* syntax to define a method that contain a single expression.</span></span> <span data-ttu-id="257b6-171">Burada, bu ifade kişi nesnesi tam adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="257b6-171">Here, that expression returns the full name for the person object.</span></span>

### <a name="lazy-evaluated-properties"></a><span data-ttu-id="257b6-172">Yavaş değerlendirilen Özellikler</span><span class="sxs-lookup"><span data-stu-id="257b6-172">Lazy Evaluated Properties</span></span>

<span data-ttu-id="257b6-173">Hesaplanan bir özellik kavramı depolama ile karıştırmak ve oluşturma bir *yavaş hesaplanan özelliği*.</span><span class="sxs-lookup"><span data-stu-id="257b6-173">You can mix the concept of a computed property with storage and create a *lazy evaluated property*.</span></span>  <span data-ttu-id="257b6-174">Örneğin, güncelleştirebilir `FullName` özelliği böylece biçimlendirme dizesi yalnızca erişilen ilk kez oluştu:</span><span class="sxs-lookup"><span data-stu-id="257b6-174">For example, you could update the `FullName` property so that the string formatting only happened the first time it was accessed:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="257b6-175">Yukarıdaki kod, ancak bir hata içeriyor.</span><span class="sxs-lookup"><span data-stu-id="257b6-175">The above code contains a bug though.</span></span> <span data-ttu-id="257b6-176">Kod ya da değeri güncelleştirmeleri olursa `FirstName` veya `LastName` özelliği, daha önce değerlendirilen `fullName` alanı geçersiz.</span><span class="sxs-lookup"><span data-stu-id="257b6-176">If code updates the value of either the `FirstName` or `LastName` property, the previously evaluated `fullName` field is invalid.</span></span> <span data-ttu-id="257b6-177">Güncelleştirmek gereken `set` erişimci `FirstName` ve `LastName` özelliği böylece `fullName` alan yeniden hesaplanır:</span><span class="sxs-lookup"><span data-stu-id="257b6-177">You need to update the `set` accessors of the `FirstName` and `LastName` property so that the `fullName` field is calculated again:</span></span>

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="257b6-178">Bu son sürümü değerlendirir `FullName` yalnızca gerekli olduğunda özelliği.</span><span class="sxs-lookup"><span data-stu-id="257b6-178">This final version evaluates the `FullName` property only when needed.</span></span>
<span data-ttu-id="257b6-179">Önceden hesaplanmış sürümü geçerli ise kullanılır.</span><span class="sxs-lookup"><span data-stu-id="257b6-179">If the previously calculated version is valid, it's used.</span></span> <span data-ttu-id="257b6-180">Başka bir durum değişikliği önceden hesaplanmış sürümü geçersiz kılar, hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="257b6-180">If another state change invalidates the previously calculated version, it will be recalculated.</span></span> <span data-ttu-id="257b6-181">Bu sınıf kullanan geliştiriciler uygulama ayrıntılarını bilmeniz gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="257b6-181">Developers that use this class do not need to know the details of the implementation.</span></span> <span data-ttu-id="257b6-182">İç değişikliklerin hiçbiri kişi nesnesinin kullanımını etkiler.</span><span class="sxs-lookup"><span data-stu-id="257b6-182">None of these internal changes affect the use of the Person object.</span></span> <span data-ttu-id="257b6-183">Veri üyeleri bir nesnenin kullanıma sunmak için özelliklerini kullanarak anahtar nedenini olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="257b6-183">That's the key reason for using Properties to expose data members of an object.</span></span>
 
### <a name="inotifypropertychanged"></a><span data-ttu-id="257b6-184">INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="257b6-184">INotifyPropertyChanged</span></span>

<span data-ttu-id="257b6-185">Bir özellik erişimcisini kod yazmanız gereken son bir senaryo desteklemektir `INotifyPropertyChanged` bir değer değiştikten veri bağlama istemcilerine bildirmek için kullanılan arabirim.</span><span class="sxs-lookup"><span data-stu-id="257b6-185">A final scenario where you need to write code in a property accessor is to support the `INotifyPropertyChanged` interface used to notify data binding clients that a value has changed.</span></span> <span data-ttu-id="257b6-186">Bir özellik değeri değiştiğinde, nesneyi başlatır `PropertyChanged` değişikliği göstermek için olay.</span><span class="sxs-lookup"><span data-stu-id="257b6-186">When the value of a property changes, the object raises the `PropertyChanged` event to indicate the change.</span></span> <span data-ttu-id="257b6-187">Veri kitaplıkları, bağlama sırayla, bu değişiklik temel görüntü öğeleri güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="257b6-187">The data binding libraries, in turn, update display elements based on that change.</span></span> <span data-ttu-id="257b6-188">Aşağıdaki kod, nasıl uygulayacağınıza gösterir `INotifyPropertyChanged` için `FirstName` bu kişinin sınıfının özelliği.</span><span class="sxs-lookup"><span data-stu-id="257b6-188">The code below shows how you would implement `INotifyPropertyChanged` for the `FirstName` property of this person class.</span></span>

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="257b6-189">`?.` İşleci çağrılır *null koşullu işleç*.</span><span class="sxs-lookup"><span data-stu-id="257b6-189">The `?.` operator is called the *null conditional operator*.</span></span> <span data-ttu-id="257b6-190">Bir null başvuru için işlecinin sağ tarafında değerlendirmeden önce denetler.</span><span class="sxs-lookup"><span data-stu-id="257b6-190">It checks for a null reference before evaluating the right side of the operator.</span></span> <span data-ttu-id="257b6-191">Hiçbir abonelere varsa olan sonuç `PropertyChanged` değil olay, olayı için kodu yürütün.</span><span class="sxs-lookup"><span data-stu-id="257b6-191">The end result is that if there are no subscribers to the `PropertyChanged` event, the code to raise the event doesn't execute.</span></span> <span data-ttu-id="257b6-192">Throw bir `NullReferenceException` bu durumda bu olmadan denetleyin.</span><span class="sxs-lookup"><span data-stu-id="257b6-192">It would throw a `NullReferenceException` without this check in that case.</span></span> <span data-ttu-id="257b6-193">Sayfasına bakın [ `events` ](delegates-events.md) daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="257b6-193">See the page on [`events`](delegates-events.md) for more details.</span></span> <span data-ttu-id="257b6-194">Bu örnek ayrıca yeni `nameof` kendi metin gösterimi olan özellik adı simgesini dönüştürmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="257b6-194">This example also uses the new `nameof` operator to convert from the property name symbol to its text representation.</span></span>
<span data-ttu-id="257b6-195">Kullanarak `nameof` Burada, yanlış yazmış özelliğinin adı hataları azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="257b6-195">Using `nameof` can reduce errors where you have mistyped the name of the property.</span></span>

<span data-ttu-id="257b6-196">Yeniden, bu nerede gereksinim duyduğunuz senaryoları desteklemek için erişimcileri kod yazabilirsiniz servis talebi örneğidir.</span><span class="sxs-lookup"><span data-stu-id="257b6-196">Again, this is an example of a case where you can write code in your accessors to support the scenarios you need.</span></span>

## <a name="summing-up"></a><span data-ttu-id="257b6-197">Özetle</span><span class="sxs-lookup"><span data-stu-id="257b6-197">Summing up</span></span>

<span data-ttu-id="257b6-198">Özellikler, bir sınıf veya nesne akıllı alanları biçimidir.</span><span class="sxs-lookup"><span data-stu-id="257b6-198">Properties are a form of smart fields in a class or object.</span></span> <span data-ttu-id="257b6-199">Gelen dışında nesne, nesne alanları gibi görünürler.</span><span class="sxs-lookup"><span data-stu-id="257b6-199">From outside the object, they appear like fields in the object.</span></span> <span data-ttu-id="257b6-200">Ancak, özellikler, C# işlevlerin tam paleti kullanarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="257b6-200">However, properties can be implemented using the full palette of C# functionality.</span></span>
<span data-ttu-id="257b6-201">Doğrulama, farklı erişilebilirlik, geç değerlendirme veya senaryolarınızı gereken herhangi bir gereksinimi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="257b6-201">You can provide validation, different accessibility, lazy evaluation, or any requirements your scenarios need.</span></span>
