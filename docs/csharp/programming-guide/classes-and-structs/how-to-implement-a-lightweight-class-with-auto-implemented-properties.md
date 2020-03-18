---
title: Otomatik olarak uygulanan özelliklere sahip hafif bir sınıf nasıl uygulanır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 6d121f6be768d41d22ea01d871662913b2daae2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170279"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a>Otomatik olarak uygulanan özelliklere sahip hafif bir sınıf nasıl uygulanır (C# Programlama Kılavuzu)

Bu örnek, yalnızca otomatik olarak uygulanan özellikler kümesini kapsüllemek için hizmet veren değişmez bir hafif sınıfın nasıl oluşturulacağını gösterir. Başvuru türü semantik kullanmanız gerekirken yapı yerine bu tür yapıyı kullanın.

Değişmez bir özelliği iki şekilde yapabilirsiniz:

- [Ayarlanan](../../language-reference/keywords/set.md) erişimciyi [özel](../../language-reference/keywords/private.md)olarak bildirebilirsiniz.  Özellik yalnızca türü içinde ayarlanabilir, ancak tüketiciler için değişmez.

  Özel `set` bir erişimci beyan ettiğinizde, özelliği başlatmak için bir nesne baş harflerini kullanamazsınız. Bir oluşturucu veya fabrika yöntemi kullanmanız gerekir.
- Yalnızca [get](../../language-reference/keywords/get.md) accessörünü bildirebilirsiniz, bu da özelliği türün oluşturucusu dışında her yerde değişmez hale getirir.

Aşağıdaki örnek, yalnızca erişim sahibi olan bir özelliğin get ve private set'li olandan nasıl farklı olduğunu gösterir.

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

## <a name="example"></a>Örnek

Aşağıdaki örnek, otomatik olarak uygulanan özelliklere sahip değişmez bir sınıf uygulamanın iki yolunu gösterir. Her şekilde bir özel `set` ve bir `get` tek özellikleri ile özellikleri biri bildirir.  Birinci sınıf yalnızca özellikleri başlatmak için bir oluşturucu kullanır ve ikinci sınıf bir oluşturucu çağıran statik bir fabrika yöntemi kullanır.

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

Derleyici, otomatik olarak uygulanan her özellik için destek alanları oluşturur. Alanlara doğrudan kaynak kodundan erişilemez.

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikler](./properties.md)
- [Yapı](../../language-reference/builtin-types/struct.md)
- [Nesne ve Koleksiyon Başlatıcıları](./object-and-collection-initializers.md)
