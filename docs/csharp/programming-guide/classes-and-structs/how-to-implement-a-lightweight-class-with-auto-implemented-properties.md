---
title: Otomatik uygulanan özelliklerle hafif bir sınıf uygulama-C# Programlama Kılavuzu
description: C# ' de otomatik uygulanan özellikleri kapsülleyen sabit hafif bir sınıf oluşturmayı öğrenin. İki uygulama yaklaşımı vardır.
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 1d80cb2391a94c21360117c8217ecc4514fd666e
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190274"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="a0503-104">Otomatik uygulanan özelliklerle hafif bir sınıf uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a0503-104">How to implement a lightweight class with auto-implemented properties (C# Programming Guide)</span></span>

<span data-ttu-id="a0503-105">Bu örnek, yalnızca bir otomatik uygulanan özellikler kümesini kapsüllemek için hizmet veren sabit bir basit sınıfın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0503-105">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="a0503-106">Başvuru türü semantiğini kullanmanız gerektiğinde, yapı yerine bu tür yapıyı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0503-106">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>

<span data-ttu-id="a0503-107">Değişmez bir özelliği aşağıdaki yöntemlerle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a0503-107">You can make an immutable property in the following ways:</span></span>

- <span data-ttu-id="a0503-108">Özelliği türün Oluşturucusu haricinde her yerde sabit hale getiren [Get](../../language-reference/keywords/get.md) erişimcisini bildirin.</span><span class="sxs-lookup"><span data-stu-id="a0503-108">Declare only the [get](../../language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type's constructor.</span></span>

- <span data-ttu-id="a0503-109">[](../../language-reference/keywords/init.md) `set` Özelliği yalnızca oluşturucuda veya bir [nesne Başlatıcısı](object-and-collection-initializers.md)kullanarak ayarlanabilir hale getiren bir erişimci yerine bir init erişimcisi bildirin.</span><span class="sxs-lookup"><span data-stu-id="a0503-109">Declare an [init](../../language-reference/keywords/init.md) accessor instead of a `set` accessor, which makes the property settable only in the constructor or by using an [object initializer](object-and-collection-initializers.md).</span></span>

- <span data-ttu-id="a0503-110">[Küme](../../language-reference/keywords/set.md) erişimcisini [özel](../../language-reference/keywords/private.md)olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="a0503-110">Declare the [set](../../language-reference/keywords/set.md) accessor to be [private](../../language-reference/keywords/private.md).</span></span>  <span data-ttu-id="a0503-111">Özelliği tür içinde ayarlanabilir, ancak tüketicilere sabittir.</span><span class="sxs-lookup"><span data-stu-id="a0503-111">The property is settable within the type, but it is immutable to consumers.</span></span>

  <span data-ttu-id="a0503-112">Özel bir `set` erişimci bildirdiğinizde, özelliği başlatmak için bir nesne Başlatıcısı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a0503-112">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="a0503-113">Bir Oluşturucu veya Factory yöntemi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0503-113">You must use a constructor or a factory method.</span></span>

<span data-ttu-id="a0503-114">Aşağıdaki örnek, Get ve Private kümesi ile tek bir get erişimcisine sahip bir özelliğin nasıl farklı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0503-114">The following example shows how a property with only get accessor differs than one with get and private set.</span></span>

```csharp
class Contact
{
    public string Name { get; }
    public string Address { get; private set; }

    public Contact(string contactName, string contactAddress)
    {
        // Both properties are accessible in the constructor.
        Name = contactName;
        Address = contactAddress;
    }

    // Name isn't assignable here. This will generate a compile error.
    //public void ChangeName(string newName) => Name = newName;

    // Address is assignable here.
    public void ChangeAddress(string newAddress) => Address = newAddress
}
```

## <a name="example"></a><span data-ttu-id="a0503-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0503-115">Example</span></span>

<span data-ttu-id="a0503-116">Aşağıdaki örnek, otomatik uygulanan özellikleri olan sabit bir sınıfı uygulamak için iki yol göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a0503-116">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="a0503-117">Her bir şekilde, bir özel ve özelliklerden biri olan özelliklerden birini bildirir `set` `get` .</span><span class="sxs-lookup"><span data-stu-id="a0503-117">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="a0503-118">İlk sınıf yalnızca özellikleri başlatmak için bir Oluşturucu kullanır ve ikinci sınıf Oluşturucu çağıran bir statik fabrika yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0503-118">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>

```csharp
// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// constructor to initialize its properties.
class Contact
{
    // Read-only property.
    public string Name { get; }

    // Read-write property with a private set accessor.
    public string Address { get; private set; }

    // Public constructor.
    public Contact(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }
}

// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// static method and private constructor to initialize its properties.
public class Contact2
{
    // Read-write property with a private set accessor.
    public string Name { get; private set; }

    // Read-only property.
    public string Address { get; }

    // Private constructor.
    private Contact2(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }

    // Public factory method.
    public static Contact2 CreateContact(string name, string address)
    {
        return new Contact2(name, address);
    }
}

public class Program
{
    static void Main()
    {
        // Some simple data sources.
        string[] names = {"Terry Adams","Fadi Fakhouri", "Hanying Feng",
                            "Cesar Garcia", "Debra Garcia"};
        string[] addresses = {"123 Main St.", "345 Cypress Ave.", "678 1st Ave",
                                "12 108th St.", "89 E. 42nd St."};

        // Simple query to demonstrate object creation in select clause.
        // Create Contact objects by using a constructor.
        var query1 = from i in Enumerable.Range(0, 5)
                    select new Contact(names[i], addresses[i]);

        // List elements cannot be modified by client code.
        var list = query1.ToList();
        foreach (var contact in list)
        {
            Console.WriteLine("{0}, {1}", contact.Name, contact.Address);
        }

        // Create Contact2 objects by using a static factory method.
        var query2 = from i in Enumerable.Range(0, 5)
                        select Contact2.CreateContact(names[i], addresses[i]);

        // Console output is identical to query1.
        var list2 = query2.ToList();

        // List elements cannot be modified by client code.
        // CS0272:
        // list2[0].Name = "Eugene Zabokritski";

        // Keep the console open in debug mode.
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}

/* Output:
    Terry Adams, 123 Main St.
    Fadi Fakhouri, 345 Cypress Ave.
    Hanying Feng, 678 1st Ave
    Cesar Garcia, 12 108th St.
    Debra Garcia, 89 E. 42nd St.
*/
```

<span data-ttu-id="a0503-119">Derleyici, otomatik uygulanan her özellik için yedekleme alanları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0503-119">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="a0503-120">Alanlara doğrudan kaynak kodundan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a0503-120">The fields are not accessible directly from source code.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0503-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0503-121">See also</span></span>

- [<span data-ttu-id="a0503-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a0503-122">Properties</span></span>](./properties.md)
- [<span data-ttu-id="a0503-123">sýný</span><span class="sxs-lookup"><span data-stu-id="a0503-123">struct</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="a0503-124">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="a0503-124">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
