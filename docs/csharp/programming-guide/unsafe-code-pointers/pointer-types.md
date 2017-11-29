---
title: "İşaretçi türleri (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0699793e91199cc623c0d13e42937c8b919e992a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-types-c-programming-guide"></a>İşaretçi türleri (C# Programlama Kılavuzu)
Güvensiz bir bağlamda, bir işaretçi türü, bir değer türü veya bir başvuru türü bir tür olabilir. Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 Aşağıdaki türlerden herhangi birisi bir işaretçi türü olabilir:  
  
-   [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bayt](../../../csharp/language-reference/keywords/byte.md), [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [ uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), [ondalık](../../../csharp/language-reference/keywords/decimal.md), veya [bool](../../../csharp/language-reference/keywords/bool.md).  
  
-   Tüm [enum](../../../csharp/language-reference/keywords/enum.md) türü.  
  
-   Herhangi bir işaretçi türü.  
  
-   Yalnızca yönetilmeyen türlerde alanlar içeren, kullanıcı tarafından tanımlanmış herhangi bir yapı türü.  
  
 İşaretçi türleri devralmaz gelen [nesne](../../../csharp/language-reference/keywords/object.md) ve işaretçi türleri arasında hiçbir dönüşümleri var ve `object`. Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez. Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.  
  
 Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işareti (*) yalnızca altı çizili türle birlikte yazılır; her bir işaretçi adı için önek olarak kullanılmaz. Örneğin:  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 Bir işaretçi bir başvuru ya da çok işaret edemez bir [yapısı](../../../csharp/language-reference/keywords/struct.md) nesne başvurusu bir işaretçi işaret olsa bile toplanacak olabileceğinden başvuruları içeren. Çöp toplayıcı, bir nesneye herhangi bir işaretçi türü tarafından işaret edilip edilmediğini izlemez.  
  
 Tür işaretçi değişkeninin değerini `myType*` türünde bir değişken adresidir `myType`. Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:  
  
|Örnek|Açıklama|  
|-------------|-----------------|  
|`int* p`|`p`tamsayıya bir işaretçidir.|  
|`int** p`|`p`tamsayı gösteren bir işaretçi bir işaretçi var.|  
|`int*[] p`|`p`bir tek boyutlu tamsayı işaretçiler dizisidir.|  
|`char* p`|`p`bir karakter için bir işaretçidir.|  
|`void* p`|`p`Bilinmeyen bir tür için bir işaretçidir.|  
  
 İşaretçi yöneltme işleci *, işaretçi değişkeninin işaret ettiği yerdeki içeriğe erişebilir. Örneğin, aşağıdaki bildirimi ele alalım:  
  
```  
int* myVariable;  
```  
  
 İfade `*myVariable` gösterir `int` içinde yer alan adresinde bulunan değişkeni `myVariable`.  
  
 Bazı işaretçiler konulardaki örnekleri vardır [deyimi sabit](../../../csharp/language-reference/keywords/fixed-statement.md) ve [işaretçi dönüşümleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).  Aşağıdaki örnek, gereksinimini gösterir `unsafe` anahtar sözcüğü ve `fixed` deyimi ve iç işaretçi artırmak nasıl.  Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz. (Güvenli olmayan kod içinde etkinleştirmeyi unutmayın **Proje Tasarımcısı**; seçin **proje**, **özellikleri** menüsünde çubuğu ve ardından **güvenli olmayan kodizinver** içinde **yapı** sekmesi.)  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 İndirection işleci gösteren bir işaretçi türü uygulanamıyor `void*`. Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.  
  
 Bir işaretçi olabilir `null`. Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.  
  
 İşaretçilerin yöntemler arasında aktarılmasının tanımlanmamış davranışa neden olabileceğini unutmayın. Örnekler, bir Out veya Ref parametresi üzerinden veya işlev sonucu olarak bir işaretçiyi bir yerel değişkene döndürüyor. İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.  
  
 Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:  
  
|İşleç/Deyim|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-------------------------|---------|  
|*|İşaretçi yöneltmesi gerçekleştirir.|  
|->|Bir yapının bir üyesine bir işaretçi yoluyla erişir.|  
|[]|Bir işaretçiyi dizine ekler.|  
|`&`|Bir değişkenin adresini alır.|  
|++ ve --|İşaretçileri artırır ve azaltır.|  
|+ ve -|İşaretçi aritmetiği gerçekleştirir.|  
|==,! =, \<, >, \<= ve > =|İşaretçileri karşılaştırır.|  
|`stackalloc`|Yığında bellek ayırır.|  
|`fixed`deyimi|Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.|  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [İşaretçi dönüşümleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)  
 [İşaretçi ifadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [güvenli olmayan](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)  
 [Kutulama ve kutudan çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
