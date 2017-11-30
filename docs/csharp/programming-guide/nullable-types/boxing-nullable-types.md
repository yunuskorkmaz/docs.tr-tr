---
title: "Boş Değer Atanabilir Türleri Kutulama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 29fccba56f6758fdfd407fa1879baa9260b69187
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md)  
 [Nasıl yapılır: boş değer atanabilir bir tür belirleme](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
