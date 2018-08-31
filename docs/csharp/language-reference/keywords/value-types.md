---
title: Değer Türleri (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 3bbaea9247d975c27ed6f49dedb749312f675296
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331856"
---
# <a name="value-types-c-reference"></a>Değer Türleri (C# Başvurusu)
Değer türleri iki ana kategoride oluşur:  
  
-   [Yapılar](../../../csharp/language-reference/keywords/struct.md)  
  
-   [Sabit Listeleri](../../../csharp/language-reference/keywords/enum.md)  
  
 Yapılar, bu kategoriye ayrılır:  
  
-   Sayısal türler  
  
    -   [Tam sayı türleri](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [Kayan nokta türleri](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   Kullanıcı tanımlı yapılar.  
  
## <a name="main-features-of-value-types"></a>Değer türleri'larının temel özellikleri  
 Değer türlerine doğrudan bağlı değişkenleri değerleri içerir. Bir değer türü değişken içindeki değeri için başka bir kopya atama. Bu nesne, ancak nesnenin kendisi için bir başvuru kopyalayan atama başvuru türü değişkenlerin farklıdır.  
  
 Tüm değer türleri örtülü olarak türetilmiş <xref:System.ValueType?displayProperty=nameWithType>.  
  
 Farklı başvuru türleri ile yeni bir tür bir değer türünden türetilemez. Ancak, başvuru türleri, ister yapılar, arabirimler uygulayabilirsiniz.  
  
 Başvuru türlerinin aksine, bir değer türü içeremez `null` değeri. Ancak, [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md) özelliğinin izin atanacak değer türleri için `null`.  
  
 Her değer türü varsayılan değer türü başlatan örtülü varsayılan bir oluşturucuya sahiptir. Değer türleri varsayılan değerler hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="main-features-of-simple-types"></a>Basit türler'larının temel özellikleri  
 --C# dilinin bu sayıya--basit türlerinin tümü, .NET Framework sistem türleri adlardır. Örneğin, [int](../../../csharp/language-reference/keywords/int.md) bir diğer adıdır <xref:System.Int32?displayProperty=nameWithType>. Diğer adlar tam bir listesi için bkz. [yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md).  
  
 Sabit ifadeler, işlenenleri tüm basit tür sabit değerlerdir, derleme zamanında değerlendirilir.  
  
 Basit türler, değişmez değerleri kullanılarak başlatılabilir. Örneğin, '' bir sabit değer türü açık `char` ve 2001 bir sabit değer türü `int`.  
  
## <a name="initializing-value-types"></a>Değer türleri başlatma  
 C# dilinde yerel değişkenler, kullanılmadan önce başlatılmalıdır. Örneğin, aşağıdaki örnekte olduğu gibi başlatma olmadan yerel bir değişken bildirmeniz:  
  
```csharp  
int myInt;  
```  
  
 Bunu başlatılmadan önce kullanamazsınız. Aşağıdaki deyimi kullanarak başlatabilirsiniz:  
  
```csharp  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 Bu ifade, aşağıdaki deyime eşdeğerdir:  
  
```csharp  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 Elbette, bildirim ve başlatma aşağıdaki örneklerde gösterildiği gibi aynı deyimde olabilir:  
  
```csharp  
int myInt = new int();  
```  
  
 – veya –  
  
```csharp  
int myInt = 0;  
```  
  
 Kullanarak [yeni](../../../csharp/language-reference/keywords/new.md) işleci belirli türdeki varsayılan oluşturucuyu çağırır ve varsayılan değer değişkenine atar. Önceki örnekte, varsayılan oluşturucu değer atanmış `0` için `myInt`. Varsayılan Oluşturucu çağırarak atanan değerler hakkında daha fazla bilgi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Kullanıcı tanımlı türler ile kullanın [yeni](../../../csharp/language-reference/keywords/new.md) varsayılan oluşturucuyu çağırmak için. Örneğin, aşağıdaki deyim olan varsayılan oluşturucusunu çağırır `Point` yapısı:  
  
```csharp  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 Bu çağrıdan sonra kesinlikle atanacak yapı olarak kabul edilir; diğer bir deyişle, tüm üyeleri varsayılan değerlerine başlatılır.  
  
 New işleci hakkında daha fazla bilgi için bkz: [yeni](../../../csharp/language-reference/keywords/new.md).  
  
 Sayısal türlerin çıktı biçimlendirme hakkında daha fazla bilgi için bkz: [sayısal sonuçlar tablosunu biçimlendirme](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Türler](../../../csharp/language-reference/keywords/types.md)  
- [Türler için Başvuru Tabloları](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
- [Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)  
- [Boş değer atanabilir türler](../../programming-guide/nullable-types/index.md)  
