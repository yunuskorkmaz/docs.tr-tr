---
title: uint (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
ms.openlocfilehash: fa0169ad92819cee36832d6c928202eb0dd6733e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288911"
---
# <a name="uint-c-reference"></a>uint (C# Başvurusu)

`uint` Anahtar sözcüğü değerleri aşağıdaki tabloda gösterilen aralığı ve boyutu göre depolayan bir tam sayı türü belirtir.  
  
|Tür|Aralık|Boyut|.NET Framework türü|  
|----------|-----------|----------|-------------------------|  
|`uint`|0 için 4.294.967.295|İmzasız 32 bit tamsayı|<xref:System.UInt32?displayProperty=nameWithType>|  
  
 **Not** `uint` türü CLS uyumlu değil. Kullanım `int` mümkün olduğunda.  
  
## <a name="literals"></a>Sabit değerler  

Bildirme ve başlatma bir `uint` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# ile 7.0 için değişmez değer bir ikili başlayarak). Değişmez değer tamsayı aralığı dışında ise `uint` (diğer bir deyişle, bu ise değerinden <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 3,000,000,000 tamsayılar eşit ve ikili değişmez değerler atanır `uint` değerleri.  
  
[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için. Ondalık değişmez değerler, önek vardır. 

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.
 - C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak. Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 Tamsayı değişmez değerleri türü gösterir bir sonek de içerir. Sonek `U` veya 'u' gösterir ya da bir `uint` veya `ulong`değişmez değeri sayısal değerini bağlı olarak. Aşağıdaki örnek kullanır `u` işaretsiz tamsayıya her iki türdeki belirtmek için soneki. İlk sabit olduğuna dikkat edin bir `uint` değeri olduğu için değerinden <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, ikinci bir `ulong` değerini daha büyük olduğu için <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.

[!code-csharp[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
Değişmez değer bir tamsayı sonek türünü ilk değerini gösterilebilir aşağıdaki türlerde ise: 

1. [int](int.md)
2. `uint`
3. [long](../../../csharp/language-reference/keywords/long.md)
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a>Dönüşümler  
 Önceden tanımlanmış bir örtük dönüştürme `uint` için [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ ondalık](../../../csharp/language-reference/keywords/decimal.md). Örneğin:  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 Önceden tanımlanmış bir örtük dönüştürme [bayt](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `uint`. Aksi halde, bir cast kullanmanız gerekir. Örneğin, aşağıdaki atama deyimi bir cast derleme hatasız üretir:  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 Ayrıca kayan nokta türleri için örtük dönüştürme yok fark `uint`. Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
 Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.UInt32>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
