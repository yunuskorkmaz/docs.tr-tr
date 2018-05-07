---
title: byte (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: 71af48f1cbfa82bafdd4888f0985cd88d44976b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="byte-c-reference"></a>byte (C# Başvurusu)

`byte` değerleri aşağıdaki tabloda gösterildiği gibi depolayan bir tam sayı türünü gösterir.  
  
|Tür|Aralık|Boyut|.NET Framework türü|  
|----------|-----------|----------|-------------------------|  
|`byte`|0-255|İmzasız 8 bit tam sayı|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  

 Bildirme ve başlatma bir `byte` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# ile 7.0 için değişmez değer bir ikili başlayarak). Değişmez değer tamsayı aralığı dışında ise `byte` (diğer bir deyişle, bu ise değerinden <xref:System.Byte.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.Byte.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 201 tamsayılar eşit ve ikili değişmez değerleri gelen örtük olarak dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `byte` değerleri.    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için. Ondalık değişmez değerler, önek vardır.

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.
 - C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak. Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a>Dönüşümler  
 Önceden tanımlanmış bir örtük dönüştürme `byte` için [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun ](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).  
  
 Örtük olarak sabit olmayan sayısal türler için daha büyük depolama boyutunu dönüştürülemiyor `byte`. Tam sayı türleri depolama boyutları hakkında daha fazla bilgi için bkz: [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md). Örneğin, aşağıdaki iki göz önünde bulundurun `byte` değişkenleri `x` ve `y`:  
  
```  
byte x = 10, y = 20;  
```  
  
 Atama işlecinin sağ taraftaki aritmetik ifade değerlendiren çünkü aşağıdaki atama deyimi bir derleme hatası üretecektir `int` varsayılan olarak.  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Bu sorunu gidermek için bir atama kullanın:  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 Ancak, hedef değişkeni depolama boyutu ile aynı veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak için mümkündür:  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Ayrıca, kayan nokta türleri için örtük dönüştürme yok yok `byte`. Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Aşırı yüklenmiş yöntemleri çağrılırken bir cast kullanılması gerekir. Örneğin, aşağıdaki aşırı kullanan yöntemleri düşünün `byte` ve [int](../../../csharp/language-reference/keywords/int.md) Parametreler:  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 Kullanarak `byte` cast garanti doğru türde, örneğin çağrıldığından emin:  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
 Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Byte>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
