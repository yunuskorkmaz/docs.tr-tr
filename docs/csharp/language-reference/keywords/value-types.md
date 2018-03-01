---
title: "Değer Türleri (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 281b811f2a8a1f2c364405b563f9f103899b492c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="value-types-c-reference"></a>Değer Türleri (C# Başvurusu)
Değer türleri iki ana kategoriye oluşur:  
  
-   [Yapılar](../../../csharp/language-reference/keywords/struct.md)  
  
-   [Numaralandırmalar](../../../csharp/language-reference/keywords/enum.md)  
  
 Yapılar kategorileri şunlardır:  
  
-   Sayısal türler  
  
    -   [Tam sayı türleri](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [Kayan nokta türleri](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [ondalık](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   Kullanıcı tanımlı yapılar.  
  
## <a name="main-features-of-value-types"></a>Değer türleri başlıca özellikleri  
 Değer türleri üzerinde doğrudan bağlı değişkenlerin değerlerini içerir. Bir değer türü değişkeni kapsanan değeri için başka bir kopya atama. Bu nesne, ancak nesnenin kendisini değil bir başvuru kopyaladığı atama başvuru türü değişkenlerin farklıdır.  
  
 Tüm değer türlerini örtük olarak türetilmiş <xref:System.ValueType?displayProperty=nameWithType>.  
  
 Farklı olarak başvuru türleri ile yeni bir tür değeri türünden türetilemez. Ancak, başvuru türleri, ister yapılar arabirimleri uygulayabilirsiniz.  
  
 Başvuru türlerinin aksine, bir değer türü içeremez `null` değeri. Ancak, [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md) özelliğinin izin atanacak değer türleri için `null`.  
  
 Her değer türünün varsayılan değer bu tür başlatır bir örtük varsayılan oluşturucusu vardır. Değer türleri varsayılan değerleri hakkında daha fazla bilgi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="main-features-of-simple-types"></a>Basit türler başlıca özellikleri  
 Tüm basit türleri--C# dili bu sayıya--, .NET Framework sistem türlerinin adlardır. Örneğin, [int](../../../csharp/language-reference/keywords/int.md) bir diğer adı <xref:System.Int32?displayProperty=nameWithType>. Diğer adlar tam bir listesi için bkz: [yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md).  
  
 Sabit ifadeler, işlenenleri tüm basit tür sabittir, derleme zamanında değerlendirilir.  
  
 Değişmez değerler kullanarak basit türler başlatılabilir. Örneğin, 'A' türündeki bir hazır değer olan `char` ve 2001 değişmez değer türü `int`.  
  
## <a name="initializing-value-types"></a>Değer türleri başlatma  
 C# yerel değişkenler kullanıldıkları önce başlatılması gerekir. Örneğin, aşağıdaki örnekte olduğu gibi başlatma olmadan yerel bir değişken bildirin:  
  
```  
int myInt;  
```  
  
 Bunu başlatılmadan önce kullanamazsınız. Şu deyimi kullanarak başlatabilirsiniz:  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 Bu deyim şu deyimi eşdeğerdir:  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 Doğal olarak, bildirim ve başlatma aşağıdaki örneklerde olduğu gibi aynı deyimde elinizde olabilir:  
  
```  
int myInt = new int();  
```  
  
 – veya –  
  
```  
int myInt = 0;  
```  
  
 Kullanarak [yeni](../../../csharp/language-reference/keywords/new.md) işleci belirli türdeki varsayılan oluşturucuyu çağırır ve varsayılan değer değişkenine atar. Önceki örnekte, varsayılan oluşturucu değer atanmışsa `0` için `myInt`. Varsayılan Oluşturucu çağırarak atanan değerler hakkında daha fazla bilgi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Kullanıcı tanımlı türler ile kullanmak [yeni](../../../csharp/language-reference/keywords/new.md) varsayılan oluşturucu çağrılamıyor. Örneğin, aşağıdaki deyim, varsayılan oluşturucu çağırır `Point` yapısı:  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 Bu çağrısından sonra kesinlikle atanacak yapı olarak kabul edilir; diğer bir deyişle, tüm üyeleri varsayılan değerlerine başlatılır.  
  
 New işleci hakkında daha fazla bilgi için bkz: [yeni](../../../csharp/language-reference/keywords/new.md).  
  
 Sayısal türler çıktısını biçimlendirme hakkında daha fazla bilgi için bkz: [sayısal sonuçlar tablosunu biçimlendirme](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [Türler için başvuru tabloları](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [Başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md)
