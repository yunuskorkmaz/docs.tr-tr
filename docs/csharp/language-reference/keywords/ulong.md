---
title: ulong (C# Başvurusu)
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 049d1cc4b30e16535f20cee8e0ad80e5c80b4a49
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="ulong-c-reference"></a>ulong (C# Başvurusu)

`ulong` Anahtar sözcüğü değerleri aşağıdaki tabloda gösterilen aralığı ve boyutu göre depolayan bir tam sayı türünü gösterir.  
  
|Tür|Aralık|Boyut|.NET Framework türü|  
|----------|-----------|----------|-------------------------|  
|`ulong`|0 için 18,446,744,073,709,551,615|İmzasız 64 bit tam sayı|<xref:System.UInt64?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  

Bildirme ve başlatma bir `ulong` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# ile 7.0 için değişmez değer bir ikili başlayarak).  Değişmez değer tamsayı aralığı dışında ise `ulong` (diğer bir deyişle, bu ise değerinden <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur. 

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 7,934,076,125 tamsayılar eşit ve ikili değişmez değerler atanır `ulong` değerleri.  
  
[!code-csharp[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]  

> [!NOTE] 
> Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için. Ondalık değişmez değerler, önek vardır. 

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.
 - C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak. Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 Tamsayı değişmez değerleri türü gösterir bir sonek de içerir. Sonek `UL` veya `ul` belirsizliğe sayısal sabit değer olarak tanımlayan bir `ulong` değeri. `L` Soneki gösterir bir `ulong` hazır değeri aşarsa <xref:System.Int64.MaxValue?displayProperty=nameWithType>. Ve `U` veya `u` soneki gösterir bir `ulong` hazır değeri aşarsa <xref:System.UInt32.MaxValue?displayProperty=nameWithType>. Aşağıdaki örnek kullanır `ul` uzun tamsayı belirtmek için soneki:
 
[!code-csharp[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

Değişmez değer bir tamsayı sonek türünü ilk değerini gösterilebilir aşağıdaki türlerde ise: 

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. [long](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a>Derleyici aşırı yükleme çözümü
  
 Bir ortak soneki aşırı yüklenmiş yöntemleri çağırma ile kullanılır. Örneğin, aşağıdaki aşırı kullanan yöntemleri düşünün `ulong` ve [int](../../../csharp/language-reference/keywords/int.md) Parametreler:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 Bir sonek ile kullanarak `ulong` parametresi doğru türde, örneğin çağrıldığından emin güvence altına alır:  
  
```csharp  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a>Dönüşümler  
 Önceden tanımlanmış bir örtük dönüştürme `ulong` için [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).  
  
 Örtük dönüştürme yok `ulong` herhangi bir tam sayı türüne. Örneğin, aşağıdaki deyim derleme hatası açık atama olmadan üretir:  
  
```csharp  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 Önceden tanımlanmış bir örtük dönüştürme [bayt](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `ulong`.  
  
 Ayrıca, kayan nokta türleri için örtük dönüştürme yok yok `ulong`. Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:  
  
```csharp  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
 Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
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
