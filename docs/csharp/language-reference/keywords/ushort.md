---
title: ushort (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: fa7f80f8f0fd6efa92242949ef16963213d0a28e
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50744489"
---
# <a name="ushort-c-reference"></a>ushort (C# Başvurusu)

`ushort` Anahtar değerlere göre boyutunu ve aşağıdaki tabloda gösterilen aralığı depolayan bir tam sayı veri türü belirtir.  
  
|Tür|Aralık|Boyut|.NET türü|  
|----------|-----------|----------|-------------------------|  
|`ushort`|0 ile 65.535 arasındaki|16 bit işaretsiz tamsayı|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  

Bildirmek ve başlatmak bir `ushort` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak). Tamsayı sabit değeri aralığının dışında ise `ushort` (diğer bir deyişle, bu ise kısa <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 65,034 eşit ve ikili sabit dizeler öğesinden örtük olarak dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `ushort` değerleri.    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.
 - C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak. Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a>Derleyici aşırı yükleme çözümlemesi
  
 Aşırı yüklenmiş yöntemler çağırdığınızda, bir yayın kullanılmalıdır. Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `ushort` ve [int](../../../csharp/language-reference/keywords/int.md) parametreleri:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 Kullanarak `ushort` atama doğru tür, örneğin çağrıldığını güvence altına alır:  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a>Dönüşümler  
 Önceden tanımlanmış bir örtük dönüştürme vardır `ushort` için [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float ](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).  
  
 Önceden tanımlanmış bir örtük dönüştürme vardır [bayt](../../../csharp/language-reference/keywords/byte.md) veya [char](../../../csharp/language-reference/keywords/char.md) için `ushort`. Aksi halde bir tür dönüştürme açık bir dönüştürme gerçekleştirmek için kullanılması gerekir. Örneğin, aşağıdaki iki göz önünde bulundurun `ushort` değişkenleri `x` ve `y`:  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 Atama işlecinin sağ tarafında aritmetik ifadenin değerlendirdiği çünkü aşağıdaki atama deyimi bir derleme hatası üretecektir `int` varsayılan olarak.  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 Bu sorunu gidermek için bir tür dönüştürme kullanın:  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 Ancak hedef değişkeni aynı depolama boyutuna veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak mümkündür:  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `ushort`. Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 Karma kayan nokta türleri ve tamsayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
 Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.UInt16>  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
