---
title: long (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
ms.openlocfilehash: f2bdc34400215ad24d5dcec2e1e9f314a01430d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288460"
---
# <a name="long-c-reference"></a>long (C# Başvurusu)

`long` Aşağıdaki tabloda gösterilen aralığı ve boyutu göre değerleri depolayan tamsayı türü gösterir.  
  
|Tür|Aralık|Boyut|.NET Framework türü|  
|----------|-----------|----------|-------------------------|  
|`long`|-9,223,372,036,854,775,808 için 9,223,372,036,854,775,807|işaretli 64 bit tam sayı|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler 

Bildirme ve başlatma bir `long` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# ile 7.0 için değişmez değer bir ikili başlayarak). 

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 4,294,967,296 tamsayılar eşit ve ikili değişmez değerler atanır `long` değerleri.  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için. Ondalık değişmez değerler, önek vardır. 

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.
 - C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak. Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 Tamsayı değişmez değerleri türü gösterir bir sonek de içerir. Sonek `L` gösterir bir `long`. Aşağıdaki örnek kullanır `L` uzun tamsayı belirtmek için soneki:
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  Bu gibi durumlarda, küçük harf "m" de sonek olarak kullanabilirsiniz. Ancak, bu derleyici uyarısı oluşturur harf "l" kolay "1." rakamla karıştırılır çünkü "M" daha anlaşılır olması için kullanın.  
  
 Sonek kullandığınızda `L`, sabit değeri Tamsayı türünde ya da olduğu belirlenir `long` veya [ulong](../../../csharp/language-reference/keywords/ulong.md)boyutuna bağlı olarak. Bu durumda olan `long` olduğundan, aralığı'den [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Bir ortak soneki aşırı yüklenmiş yöntemleri çağırmak için kullanılır. Örneğin, aşağıdaki aşırı yüklenmiş yöntemler türü parametrelerine sahip `long` ve [int](../../../csharp/language-reference/keywords/int.md):  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 `L` Soneki garanti doğru aşırı adı verilir:  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
Değişmez değer bir tamsayı sonek türünü ilk değerini gösterilebilir aşağıdaki türlerde ise: 

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 

Önceki örneklerde değişmez değer 4294967296 türünde `long`, aralığı aştığından [uint](../../../csharp/language-reference/keywords/uint.md) (bkz [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md) depolama boyutları tam sayı türleri için).  
  
 Kullanırsanız `long` ifadesi aynı ifadedeki diğer tam sayı türleri türüyle olarak değerlendirildiği `long` (veya [bool](../../../csharp/language-reference/keywords/bool.md) ilişkisel ya da Boole ifadeleri söz konusu olduğunda). Örneğin, olarak aşağıdaki ifadeyi hesaplar `long`:  
  
```csharp  
898L + 88  
```  
  
 Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="conversions"></a>Dönüşümler  
 Önceden tanımlanmış bir örtük dönüştürme `long` için [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md). Aksi halde bir cast kullanılmalıdır. Örneğin, aşağıdaki deyim derleme hatası açık atama olmadan üretir:  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 Önceden tanımlanmış bir örtük dönüştürme [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bayt](../../../csharp/language-reference/keywords/byte.md), [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `long`.  
  
 Ayrıca kayan nokta türleri için örtük dönüştürme yok fark `long`. Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Int64>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
