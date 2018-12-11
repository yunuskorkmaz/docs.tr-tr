---
title: uzun - C# başvurusu
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
ms.openlocfilehash: 7693de1502898a6ba8d35c0011d31756848fb461
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241515"
---
# <a name="long-c-reference"></a>long (C# Başvurusu)

`long` boyutu ve aşağıdaki tabloda gösterilen aralığı göre değerler depolayan bir tamsayı türü gösterir.  
  
|Tür|Aralık|Boyut|.NET türü|  
|----------|-----------|----------|-------------------------|  
|`long`|-9,223,372,036,854,775,808 için 9.223.372.036.854.775.807|İşaretli 64 bit tam sayı|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler 

Bildirmek ve başlatmak bir `long` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak). 

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 4,294,967,296 eşit ve ikili sabit değerler atanır `long` değerleri.  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır. 

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.
 - C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak. Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 Tamsayı sabit değerleri türü gösteren bir son eki de içerebilir. Sonek `L` gösterir bir `long`. Aşağıdaki örnekte `L` sonek uzun tamsayı belirtmek için:
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  Bu gibi durumlarda, küçük harf "l" de sonek olarak kullanabilirsiniz. Ancak, bu bir derleyici uyarısı oluşturur çünkü "m" harfinin basamağı "1" ile kolaylıkla karıştırılır "M" daha anlaşılır olması için kullanın.  
  
 Sonek kullandığınızda `L`, sabit tamsayı türü ya da belirlenir `long` veya [ulong](../../../csharp/language-reference/keywords/ulong.md)boyutuna bağlı olarak. Bu durumda `long` çünkü bu aralığı değerinden [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Bir ortak soneki aşırı yüklü yöntemleri çağırmak için kullanılır. Örneğin, aşağıdaki aşırı yüklenmiş yöntemler türünde parametreye sahip `long` ve [int](../../../csharp/language-reference/keywords/int.md):  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 `L` Soneki garanti aşırı yük çağrılır:  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
Değişmez değer bir tamsayı sonek varsa, ilk değerini gösterilebilir aşağıdaki türlerde türünü verilmiştir: 

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 

Önceki örneklerde değişmez değer 4294967296 türünde `long`, aralığı aştığından [uint](../../../csharp/language-reference/keywords/uint.md) (bkz [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md) depolama boyutları tam sayı türleri için).  
  
 Kullanırsanız `long` diğer tamsayı türlerinin aynı ifadede, ifade türü olarak değerlendirildiği `long` (veya [bool](../../../csharp/language-reference/keywords/bool.md) ilişkisel veya Boolean ifadeler söz konusu olduğunda). Örneğin, aşağıdaki ifade, olarak değerlendirir `long`:  
  
```csharp  
898L + 88  
```  
  
 Karma kayan nokta türleri ve tamsayı türleri aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="conversions"></a>Dönüşümler  
 Önceden tanımlanmış bir örtük dönüştürme vardır `long` için [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md). Aksi takdirde bir yayın kullanılmalıdır. Örneğin, aşağıdaki deyim, açık atama olmadan bir derleme hatasına neden olur:  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int y = (int)8L;   // OK: explicit conversion to int  
```  
  
 Önceden tanımlanmış bir örtük dönüştürme vardır [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bayt](../../../csharp/language-reference/keywords/byte.md), [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `long`.  
  
 Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `long`. Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Int64>  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
