---
title: sbyte (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
ms.openlocfilehash: c64aae58317c54499b3d16c5643e4a473544c6a6
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50744515"
---
# <a name="sbyte-c-reference"></a>sbyte (C# Başvurusu)

`sbyte` boyutu ve aşağıdaki tabloda gösterilen aralığı göre değerler depolayan bir tamsayı türü gösterir.  
  
|Tür|Aralık|Boyut|.NET türü|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|-128 ila 127 arasında|İşaretli 8 bit tam sayı|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  

Bildirmek ve başlatmak bir `sbyte` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak). 

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen-102 eşit ve ikili sabit dizeler gelen dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `sbyte` değerleri.    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.
 - C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak. Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.

 Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

Tamsayı sabit değeri aralığının dışında ise `sbyte` (diğer bir deyişle, bu ise kısa <xref:System.SByte.MinValue?displayProperty=nameWithType> veya ondan <xref:System.SByte.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur. Değişmez değer bir tamsayı sonek varsa, kendi içinde değerini gösterilebileceği bu tür ilk türüdür: [int](int.md), [uint](uint.md), [uzun](long.md), [ulong](ulong.md). Bu örnekte, sayısal değişmez değerleri, yani, `0x9A` ve `0b10011010` aşıyor 156, değerini 32-bit imzalı tamsayı olarak yorumlanır <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Bu nedenle, yayım işleciyle gereklidir ve atama oluşması gereken bir [denetlenmeyen](unchecked.md) bağlamı. 

## <a name="compiler-overload-resolution"></a>Derleyici aşırı yükleme çözümlemesi

 Çağırma yöntemleri aşırı yüklendiğinde bir yayın kullanılmalıdır. Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `sbyte` ve [int](../../../csharp/language-reference/keywords/int.md) parametreleri:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 Kullanarak `sbyte` atama doğru tür, örneğin çağrıldığını güvence altına alır:  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a>Dönüşümler  
 Önceden tanımlanmış bir örtük dönüştürme vardır `sbyte` için [kısa](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [uzun](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [çift ](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).  
  
 Daha büyük depolama boyutu için sabit değerli olmayan sayısal türleri örtülü olarak dönüştürülemiyor `sbyte` (bkz [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md) depolama boyutları tam sayı türleri için). Örneğin, aşağıdaki iki göz önünde bulundurun `sbyte` değişkenleri `x` ve `y`:  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 Atama işlecinin sağ tarafında aritmetik ifadenin değerlendirdiği çünkü aşağıdaki atama deyimi bir derleme hatası üretecektir [int](../../../csharp/language-reference/keywords/int.md) varsayılan olarak.  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 Bu sorunu gidermek için aşağıdaki örnekte olduğu gibi ifade dönüştürün:  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 Ancak hedef değişkeni aynı depolama boyutuna veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak mümkündür:  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `sbyte`. Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 Karma kayan nokta türleri ve tamsayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
 Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.SByte>  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
