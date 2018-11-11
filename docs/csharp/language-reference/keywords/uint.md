---
title: uint (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
ms.openlocfilehash: c8610d13a97e672773fdf80d013a159a58e7cfbf
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50744344"
---
# <a name="uint-c-reference"></a>uint (C# Başvurusu)

`uint` Anahtar sözcüğü, boyutu ve aşağıdaki tabloda gösterilen aralığı göre değerler depolayan bir tamsayı türü belirtir.  
  
|Tür|Aralık|Boyut|.NET türü|  
|----------|-----------|----------|-------------------------|  
|`uint`|0 için 4.294.967.295'e|32-bit işaretsiz tamsayı|<xref:System.UInt32?displayProperty=nameWithType>|  
  
 **Not** `uint` türü CLS uyumlu değil. Kullanım `int` mümkün olduğunda.  
  
## <a name="literals"></a>Sabit değerler  

Bildirmek ve başlatmak bir `uint` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak). Tamsayı sabit değeri aralığının dışında ise `uint` (diğer bir deyişle, bu ise kısa <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 3,000,000,000 eşit ve ikili sabit değerler atanır `uint` değerleri.  
  
[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır. 

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.
 - C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak. Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 Tamsayı sabit değerleri türü gösteren bir son eki de içerebilir. Sonek `U` veya 'u' gösterir ya da bir `uint` veya `ulong`sayısal değerine bağlı olarak. Aşağıdaki örnekte `u` sonek işaretsiz bir tamsayı her iki türdeki belirtmek için. İlk değişmez değer olduğunu unutmayın bir `uint` değeri olduğundan küçüktür <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, ikinci olmakla birlikte bir `ulong` değeri büyük olduğundan <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.

[!code-csharp[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
Değişmez değer bir tamsayı sonek varsa, ilk değerini gösterilebilir aşağıdaki türlerde türünü verilmiştir: 

1. [int](int.md)
2. `uint`
3. [long](../../../csharp/language-reference/keywords/long.md)
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a>Dönüşümler  
 Önceden tanımlanmış bir örtük dönüştürme vardır `uint` için [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ ondalık](../../../csharp/language-reference/keywords/decimal.md). Örneğin:  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 Önceden tanımlanmış bir örtük dönüştürme vardır [bayt](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `uint`. Aksi takdirde, bir dönüştürme kullanmanız gerekir. Örneğin, aşağıdaki atama deyimi, bir yayın olmadan bir derleme hatasına neden olur:  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `uint`. Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 Karma kayan nokta türleri ve tamsayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
 Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.UInt32>  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
