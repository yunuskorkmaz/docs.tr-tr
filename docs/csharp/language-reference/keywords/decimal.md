---
title: "decimal (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0da001851c681fe4d698b920d9668b2f6b731e3a
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2018
---
# <a name="decimal-c-reference"></a>decimal (C# Başvurusu)
`decimal` Anahtar sözcüğü 128-bit veri türünü gösterir. Diğer kayan nokta türleri için karşılaştırıldığında `decimal` daha yüksek duyarlılık ve finansal ve para hesaplamaları için uygun hale getirir daha küçük bir aralık türü içeriyor. İçin duyarlık ve yaklaşık aralığı `decimal` türü aşağıdaki tabloda gösterilmiştir.  
  
|Tür|Yaklaşık Aralık|Duyarlık|.NET Framework türü|  
|----------|-----------------------|---------------|-------------------------|  
|`decimal`|(-7.9 x 10<sup>28</sup> 7,9 x 10<sup>28</sup>) / (10<sup>0</sup> 10<sup>28</sup>)|28-29 önemli basamaklar|<xref:System.Decimal?displayProperty=nameWithType>|  

Varsayılan değer olan bir `decimal` 0 m.
  
## <a name="literals"></a>Sabit değerler  
 Göreceğini sayısal gerçek değişmez değeri isteyip istemediğinizi `decimal`, sonek m veya M, örneğin kullanın:  
  
```csharp
decimal myMoney = 300.5m;  
```  
  
 M soneki sayı olarak işlem görür bir [çift](../../../csharp/language-reference/keywords/double.md) ve derleyici hatası oluşturur.  
  
## <a name="conversions"></a>Dönüşümler  
 Tam sayı türleri örtük olarak dönüştürülür `decimal` ve sonucu veren `decimal`. Bu nedenle, bir tamsayı hazır değerini kullanarak, son ek olmadan, bir ondalık değişken başlatabilirsiniz:  
  
```csharp
decimal myMoney = 300;  
```  
  
 Kayan nokta diğer türleri arasında örtük bir dönüştürme yok ve `decimal` yazın; bu nedenle, bir cast bu iki türleri arasında dönüştürme için kullanılması gerekir. Örneğin:  
  
```csharp
decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 Ayrıca karıştırabilirsiniz `decimal` ve aynı ifadedeki sayısal tam sayı türleri. Ancak, karıştırma `decimal` ve diğer kayan nokta türleri bir cast olmadan bir derleme hatası neden olur.  
  
 Örtük sayısal dönüşümler hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Açık sayısal dönüşümler hakkında daha fazla bilgi için bkz: [açık sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="formatting-decimal-output"></a>Ondalık Çıktı Biçimlendirme  
 Kullanarak sonuçları biçimlendirebilirsiniz `String.Format` yöntemi, aracılığıyla veya <xref:System.Console.Write%2A?displayProperty=nameWithType> çağırır yöntemi `String.Format()`. Para birimi, bu makalenin ilerisinde ikinci örnekte gösterildiği gibi, standart para birimi biçimi dizisi "C" veya "c" kullanılarak belirtilir. Hakkında daha fazla bilgi için `String.Format` yöntemi, bkz: <xref:System.String.Format%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek eklemek deneyerek derleyici hatası neden olan [çift](../../../csharp/language-reference/keywords/double.md) ve `decimal` değişkenleri.  
  
```csharp  
decimal dec = 0m;
double dub = 9;  
// The following line causes an error that reads "Operator '+' cannot be applied to   
// operands of type 'double' and 'decimal'"  
Console.WriteLine(dec + dub);   
  
// You can fix the error by using explicit casting of either operand.  
Console.WriteLine(dec + (decimal)dub);  
Console.WriteLine((double)dec + dub);  
```  
  
 Sonuç olarak aşağıdaki hata oluşur:  
  
 `Operator '+' cannot be applied to operands of type 'double' and 'decimal'`  
  
 Bu örnekte, bir `decimal` ve bir [int](../../../csharp/language-reference/keywords/int.md) aynı ifadesinde karıştırılır. Sonucu veren `decimal` türü.  
  
 [!code-csharp[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte, çıktı, para birimi biçim dizesi kullanılarak biçimlendirilir. Dikkat `x` ondalık 0,99 aştığından yuvarlanır. Değişkeni `y`, en büyük tam sayı temsil eden tam olarak doğru biçimde görüntülenir.  
  
 [!code-csharp[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Decimal>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Standart Sayısal Biçim Dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
