---
title: 'Nasıl yapılır: Otomatik uygulanan özelliklerle hafif bir sınıf uygulama- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 4cbed8145487325d8b06882bbab843321a49d0d3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596910"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a>Nasıl yapılır: Otomatik uygulanan özelliklerle hafif bir sınıf uygulama (C# Programlama Kılavuzu)

Bu örnek, yalnızca bir otomatik uygulanan özellikler kümesini kapsüllemek için hizmet veren sabit bir basit sınıfın nasıl oluşturulacağını gösterir. Başvuru türü semantiğini kullanmanız gerektiğinde, yapı yerine bu tür yapıyı kullanın.

Değişmez bir özelliği iki şekilde yapabilirsiniz:
- [Set](../../language-reference/keywords/set.md) erişimcisinin [Private](../../language-reference/keywords/private.md)olarak bildirilmesini sağlayabilirsiniz.  Özelliği yalnızca tür içinde ayarlanabilir, ancak tüketicilere sabittir.

  Özel `set` bir erişimci bildirdiğinizde, özelliği başlatmak için bir nesne Başlatıcısı kullanamazsınız. Bir Oluşturucu veya Factory yöntemi kullanmanız gerekir.
- Yalnızca [Get](../../language-reference/keywords/get.md) erişimcisini bildirebilirsiniz. Bu, özelliği türün Oluşturucusu dışında her yerde sabit hale getirir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, otomatik uygulanan özellikleri olan sabit bir sınıfı uygulamak için iki yol göstermektedir. Her bir şekilde, bir özel `set` ve özelliklerden `get` biri olan özelliklerden birini bildirir.  İlk sınıf yalnızca özellikleri başlatmak için bir Oluşturucu kullanır ve ikinci sınıf Oluşturucu çağıran bir statik fabrika yöntemi kullanır.

```csharp
// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// constructor to initialize its properties.
class Contact
{
    // Read-only properties.
    public string Name { get; }
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
    // Read-only properties.
    public string Name { get; private set; }
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

Derleyici, otomatik uygulanan her özellik için yedekleme alanları oluşturur. Alanlara doğrudan kaynak kodundan erişilebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikler](./properties.md)
- [struct](../../language-reference/keywords/struct.md)
- [Nesne ve Koleksiyon Başlatıcıları](./object-and-collection-initializers.md)
