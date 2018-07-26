---
title: ulong (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: 96975bcfc270694a59a19e7c40183083dbc5bd98
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960227"
---
# <a name="ulong-c-reference"></a>ulong (C# Başvurusu)

`ulong` Anahtar değerlere göre boyutunu ve aşağıdaki tabloda gösterilen aralığı depolayan bir tamsayı türü gösterir.  
  
|Tür|Aralık|Boyut|.NET türü|  
|----------|-----------|----------|-------------------------|  
|`ulong`|0 için 18,446,744,073,709,551,615|64-bit işaretsiz tamsayı|<xref:System.UInt64?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  

Bildirmek ve başlatmak bir `ulong` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak).  Tamsayı sabit değeri aralığının dışında ise `ulong` (diğer bir deyişle, bu ise kısa <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur. 

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 7,934,076,125 eşit ve ikili sabit değerler atanır `ulong` değerleri.  
  
[!code-csharp[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]  

> [!NOTE] 
> Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır. 

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.
 - C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak. Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 Tamsayı sabit değerleri türü gösteren bir son eki de içerebilir. Sonek `UL` veya `ul` sayısal bir değişmez değer olarak kesin bir şekilde tanımlayan bir `ulong` değeri. `L` Soneki gösterir bir `ulong` değişmez değer aşarsa <xref:System.Int64.MaxValue?displayProperty=nameWithType>. Ve `U` veya `u` soneki gösterir bir `ulong` değişmez değer aşarsa <xref:System.UInt32.MaxValue?displayProperty=nameWithType>. Aşağıdaki örnekte `ul` sonek uzun tamsayı belirtmek için:
 
[!code-csharp[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

Değişmez değer bir tamsayı sonek varsa, ilk değerini gösterilebilir aşağıdaki türlerde türünü verilmiştir: 

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. [long](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a>Derleyici aşırı yükleme çözümlemesi
  
 Bir ortak soneki aşırı yüklenmiş yöntem çağırma işleviyle kullanılır. Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `ulong` ve [int](../../../csharp/language-reference/keywords/int.md) parametreleri:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 Bir sonek ile kullanarak `ulong` parametresi doğru türde, örneğin çağrıldığını güvence altına alır:  
  
```csharp  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a>Dönüşümler  
 Önceden tanımlanmış bir örtük dönüştürme vardır `ulong` için [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).  
  
 Örtülü dönüştürme olmaz yoktur `ulong` için herhangi bir tamsayı türü. Örneğin, aşağıdaki deyim, açık atama olmadan bir derleme hatasına neden olur:  
  
```csharp  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 Önceden tanımlanmış bir örtük dönüştürme vardır [bayt](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `ulong`.  
  
 Ayrıca, kayan nokta türlerinden örtük dönüştürme vardır `ulong`. Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:  
  
```csharp  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 Karma kayan nokta türleri ve tamsayı türleri aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
 Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.UInt64>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
