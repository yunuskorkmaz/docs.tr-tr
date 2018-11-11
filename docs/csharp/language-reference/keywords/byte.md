---
title: byte (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: d952f56df62aa3a53e3889baa65c491e1a0fc81e
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "43505101"
---
# <a name="byte-c-reference"></a>byte (C# Başvurusu)

`byte` Aşağıdaki tabloda gösterildiği gibi değerleri depolayan bir tamsayı türü gösterir.  
  
|Tür|Aralık|Boyut|.NET türü|  
|----------|-----------|----------|-------------------------|  
|`byte`|0 ile 255 arasında|İmzalanmamış 8 bit tam sayı|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  

 Bildirmek ve başlatmak bir `byte` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak). Tamsayı sabit değeri aralığının dışında ise `byte` (diğer bir deyişle, bu ise kısa <xref:System.Byte.MinValue?displayProperty=nameWithType> veya ondan <xref:System.Byte.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 201 eşit ve ikili sabit dizeler öğesinden örtük olarak dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `byte` değerleri.    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.
 - C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak. Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a>Dönüşümler  
 Önceden tanımlanmış bir örtük dönüştürme vardır `byte` için [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun ](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).  
  
 Daha büyük depolama boyutu için sabit olmayan değer sayısal türleri örtülü olarak dönüştürülemiyor `byte`. Tam sayı türleri depolama alanı boyutları hakkında daha fazla bilgi için bkz. [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md). Örneğin, aşağıdaki iki göz önünde bulundurun `byte` değişkenleri `x` ve `y`:  
  
```csharp  
byte x = 10, y = 20;  
```  
  
 Atama işlecinin sağ tarafında aritmetik ifadenin değerlendirdiği çünkü aşağıdaki atama deyimi bir derleme hatası üretecektir `int` varsayılan olarak.  
  
```csharp  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Bu sorunu gidermek için bir tür dönüştürme kullanın:  
  
```csharp  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 Ancak, hedef değişkeni aynı depolama boyutuna veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak mümkündür:  
  
```csharp  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Ayrıca, kayan nokta türlerinden örtük dönüştürme vardır `byte`. Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:  
  
```csharp  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Aşırı yüklenmiş yöntemleri çağrılırken bir yayın kullanılmalıdır. Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `byte` ve [int](../../../csharp/language-reference/keywords/int.md) parametreleri:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 Kullanarak `byte` atama doğru tür, örneğin çağrıldığını güvence altına alır:  
  
```csharp  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Karma kayan nokta türleri ve tamsayı türleri aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
 Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca Bkz.  

- <xref:System.Byte>  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
