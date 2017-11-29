---
title: "Nasıl yapılır: Otomatik Uygulanan Özelliklerle Hafif bir Sınıf Uygulama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f43dfaffe6ff696387573729dc25cabe33c1fede
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="7148d-102">Nasıl yapılır: Otomatik Uygulanan Özelliklerle Hafif bir Sınıf Uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7148d-102">How to: Implement a Lightweight Class with Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="7148d-103">Bu örnek yalnızca otomatik uygulanan özellikler kümesi kapsülleyen hizmet veren değişmez hafif bir sınıf oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7148d-103">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="7148d-104">Başvuru türü anlamları kullandığınızda, bu tür bir yapı yapı yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="7148d-104">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>  
  
 <span data-ttu-id="7148d-105">Bir sabit özelliği iki şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7148d-105">You can make an immutable property in two ways.</span></span>  <span data-ttu-id="7148d-106">Bildirebilirsiniz [ayarlamak](../../../csharp/language-reference/keywords/set.md) accessor.to olması [özel](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="7148d-106">You can declare the [set](../../../csharp/language-reference/keywords/set.md) accessor.to be [private](../../../csharp/language-reference/keywords/private.md).</span></span>  <span data-ttu-id="7148d-107">Özellik yalnızca türü içinde ayarlanabilir, ancak tüketicilere sabittir.</span><span class="sxs-lookup"><span data-stu-id="7148d-107">The property is only settable within the type, but it is immutable to consumers.</span></span>  <span data-ttu-id="7148d-108">Bunun yerine yalnızca bildirebilir [almak](../../../csharp/language-reference/keywords/get.md) özelliği tür oluşturucusundaki her yerde dışında değişmez yapar erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="7148d-108">You can instead declare only the [get](../../../csharp/language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type’s constructor.</span></span>  
  
 <span data-ttu-id="7148d-109">Bildirme ne zaman özel `set` erişimci özelliği başlatmak için nesne Başlatıcı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7148d-109">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="7148d-110">Bir oluşturucu ya da bir fabrika yöntemini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7148d-110">You must use a constructor or a factory method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7148d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7148d-111">Example</span></span>  
 <span data-ttu-id="7148d-112">Aşağıdaki örnek, otomatik uygulanan özellikler sahip değişmez bir sınıf uygulama için iki yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="7148d-112">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="7148d-113">Özel özelliklerle birini her bildirir `set` ve özelliklere sahip bir `get` yalnızca.</span><span class="sxs-lookup"><span data-stu-id="7148d-113">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="7148d-114">Birinci sınıf kullandığı özellikler ve ikinci sınıfı yalnızca başlatmak için bir oluşturucu bir oluşturucu çağıran bir statik fabrika yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7148d-114">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>  
  
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
  
 <span data-ttu-id="7148d-115">Derleyici her otomatik uygulanan bir özellik için yedekleme alanları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7148d-115">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="7148d-116">Alanlar doğrudan kaynak kodundan erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="7148d-116">The fields are not accessible directly from source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7148d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7148d-117">See Also</span></span>  
 [<span data-ttu-id="7148d-118">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="7148d-118">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="7148d-119">yapısı</span><span class="sxs-lookup"><span data-stu-id="7148d-119">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
 [<span data-ttu-id="7148d-120">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="7148d-120">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
