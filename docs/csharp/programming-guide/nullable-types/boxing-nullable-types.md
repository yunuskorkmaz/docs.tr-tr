---
title: Boş Değer Atanabilir Türleri Kutulama (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
ms.openlocfilehash: e2c7602bf45f1861d3a32a73824e9fedf0a4d29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334762"
---
# <a name="boxing-nullable-types-c-programming-guide"></a>Boş Değer Atanabilir Türleri Kutulama (C# Programlama Kılavuzu)
Null olmayan nesne ise, boş değer atanabilir türlerine göre nesneleri yalnızca Kutulu. Varsa <xref:System.Nullable%601.HasValue%2A> olan `false`, nesne başvurusu atandığı `null` kutulama yerine. Örneğin:  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 Nesne null olmayan--ise, <xref:System.Nullable%601.HasValue%2A> olan `true` --sonra kutulama oluşur, ancak null atanabilir nesne dayanan temel alınan tür Kutulu. Bir null olmayan boş değer atanabilir değer türü kutulama kutular değer türü kendisi değil <xref:System.Nullable%601?displayProperty=nameWithType> değer türü sarmalar. Örneğin:  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 İki Kutulu nesneleri kutulama null türleri tarafından oluşturulanlar için aynıdır. Ve yalnızca null Kutulu türleri gibi aşağıdaki örnekte olduğu gibi boş değer atanabilir türler içine sarmalanmamış olabilir:  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Kutulu zaman boş değer atanabilir türler davranışını iki avantajları sağlar:  
  
1.  Boş değer atanabilir nesneler ve onların paketlenmiş karşılık gelen null test edilebilir:  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  Paketlenmiş boş değer atanabilir türler, temel alınan tür işlevselliğini tam olarak destekler:  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Boş Değer Atanabilir Tipler](../../../csharp/programming-guide/nullable-types/index.md)  
 [Nasıl yapılır: Boş Değer Atanabilir Tipi Tanımlama](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
