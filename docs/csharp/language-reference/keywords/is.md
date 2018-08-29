---
title: is (C# Başvurusu)
ms.date: 02/17/2017
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 974e0c3ab29da582e7b22c909650a61d179ec3f7
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931172"
---
# <a name="is-c-reference"></a>is (C# Başvurusu) #

Bir nesne belirli bir tür ile uyumlu olan veya bir ifade belirli bir desene göre testleri (C# 7. 0'dan itibaren) denetler.

## <a name="testing-for-type-compatibility"></a>Tür uyumluluğu için test etme ##

`is` Anahtar sözcüğü, çalışma zamanında tür uyumluluğu değerlendirilir. Bir ifadenin sonucu bir belirtilen türe dönüştürülebilir ya da bir nesne örneği olup olmadığını belirler. Söz dizimine sahiptir

```csharp
   expr is type
```

Burada *expr* bazı türünde bir örnek için değerlendirilen bir ifade olan ve *türü* türün adı sonucunu *expr* dönüştürülecek. `is` Deyimi `true` varsa *expr* null olmayan ve ifade değerlendirme sonuçları dönüştürülebilir nesne *türü*; Aksi halde döndürür `false`.

Örneğin, aşağıdaki kod, belirler `obj` örneğine atanabilecek `Person` türü:

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

`is` Deyimi değeri true ise:

- *Expr* örneği aynı türde olan *türü*.

- *Expr* türetilen türün bir örneği *türü*. Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.

- *Expr* temel bir sınıfı olan bir derleme zamanı türü sahip *türü*, ve *expr* sahip olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*. *Derleme zamanı tür* değişkeninin Değişken bildiriminde tanımlanan türüdür. *Çalışma zamanı türü* bir değişken, bu değişkene atanan örnek türüdür.

- *Expr* uygulayan bir tür örneğidir *türü* arabirimi.

Aşağıdaki örnek, gösterir `is` ifadeyi hesaplar için `true` her biri bu dönüştürmeleri için.

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

`is` Anahtar sözcüğü ifade her zaman ya da olarak bilinen bir derleme zamanı uyarısı oluşturur `true` veya `false`. Yalnızca başvuru dönüşümleri, dönüştürmeleri kutulama ve kutudan çıkarma dönüştürme dikkate alır; Kullanıcı tanımlı dönüşümler veya bir türün tarafından tanımlanan dönüştürmeler düşünmez [örtük](implicit.md) ve [açık](explicit.md) işleçleri. Aşağıdaki örnek, uyarılar oluşturur, bu dönüştürme sonucu olarak, derleme zamanında bilinen çünkü. Unutmayın `is` dönüştürmelerinde ifade `int` için `long` ve `double` dönüştürmeler tarafından işlendiğinden dolayı false dönüş [örtük](implicit.md) işleci.

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

`expr` herhangi bir lambda ifadeleri ve anonim yöntemler dışında bir değer döndüren bir ifade olabilir. Aşağıdaki örnekte `is` bir yöntem çağrısının dönüş değerini değerlendirilecek.   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

C# 7.0 ile başlayarak, deseni ile eşleşen kullanabilirsiniz [türü deseni](#type) kullanan daha kısa kodu yazmak için `is` deyimi.

## <a name="pattern-matching-with-is"></a>İle desen eşleştirme `is` ##

C# 7.0 ile başlayan `is` ve [geçiş](../../../csharp/language-reference/keywords/switch.md) ifadeleri desen eşleştirme desteği. `is` Anahtar sözcüğü aşağıdaki düzenini destekler:

- [Tür deseni](#type), bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülemeyeceğini test eder ve, olabilir, bu türden bir değişkene çevirir.

- [Sabit desen](#constant), belirtilen bir sabit değer için bir ifadeyi değerlendirir olup olmadığını sınar.

- [değişken desen](#var), her zaman yeni bir yerel değişken bir ifadenin değerine bağlar ve başarılı bir eşleşme. 

### <a name="type" /> Tür deseni </a>

Desen eşleştirme, gerçekleştirmek için tür deseni kullanılırken `is` bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülemeyeceğini test eder ve bu olabilir, bu türden bir değişkene çevirir. Basit bir uzantısıdır `is` kısa türü değerlendirme ve dönüştürme sağlayan deyimi. Genel formu `is` türü modelidir:

```csharp
   expr is type varname 
```

Burada *expr* bazı türünde bir örnek için değerlendirilen bir ifade olan *türü* türün adı sonucunu *expr* Boolean'a dönüştürülecek ve *varname* hangi nesne sonucu *expr* aralığındaysa dönüştürülür `is` test `true`. 

`is` İfade `true` varsa *expr* değil `null`, ve aşağıdakilerden birini doğrudur:

- *Expr* örneği aynı türde olan *türü*.

- *Expr* türetilen türün bir örneği *türü*. Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.

- *Expr* temel bir sınıfı olan bir derleme zamanı türü sahip *türü*, ve *expr* sahip olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*. *Derleme zamanı tür* değişkeninin Değişken bildiriminde tanımlanan türüdür. *Çalışma zamanı türü* bir değişken, bu değişkene atanan örnek türüdür.

- *Expr* uygulayan bir tür örneğidir *türü* arabirimi.

Varsa *expr* olduğu `true` ve `is` ile kullanılan bir `if` deyimi *varname* atanır ve yerel kapsamda olan `if` deyimi yalnızca.

Aşağıdaki örnekte `is` türün uygulamasını sağlamak üzere tür deseni <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> yöntemi.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Desen eşleştirme olmadan, bu kod şu şekilde yazılmış olabilir. Kullanım türü desen eşleştirme bir dönüştürmenin sonucu olup olmadığını sınamak için gereksinimini ortadan kaldırarak daha kompakt ve okunabilir bir kod oluşturur bir `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` Türü desen türü bir değer türü tespit edilirken daha küçük kod ayrıca oluşturur. Aşağıdaki örnekte `is` türü desen, bir nesne olup olmadığını belirlemek için bir `Person` veya `Dog` uygun bir özelliğin değerini göstermeden önce örneği. 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Desen eşleştirme olmadan eşdeğer kod, bir açık tür dönüştürme içeren ayrı bir atama gerektirir.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><a name="constant" /> Sabit desen ###

Sabit desen ile eşleşen deseni gerçekleştirirken `is` belirtilen sabit bir ifade eşit olup olmadığını test eder. C# 6 ve önceki sürümleri, sabit desen tarafından desteklenen [geçiş](switch.md) deyimi. C# 7.0 ile başlayarak, tarafından desteklenir mi `is` deyimi de. Kendi sözdizimi aşağıdaki gibidir:

```csharp
   expr is constant
```

Burada *expr* değerlendirmek için ifade ve *sabit* sınamak için değer. *Sabit* aşağıdaki sabit ifadeler biri olabilir: 

- Değişmez değer.

- Bildirilen bir adı `const` değişkeni.

- Bir numaralandırma sabiti.

Sabit ifade gibi değerlendirilir:

- Varsa *expr* ve *sabit* integral türleri, C# eşitlik işlecini ifade döndürüp döndürmediğini belirler `true` (olup, diğer bir deyişle, `expr == constant`).

- Aksi takdirde, ifadenin değerini statik bir çağrı tarafından belirlenir [Object.Equals (ifade, sabit)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi.  

Aşağıdaki örnek bir nesne olup olmadığını sınamak için tür ve sabit desenler birleştiren bir `Dice` örneği ve ise, belirlemek için bir zar değerini olup 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <a name="var" /> değişken deseni </a>

Bir desen eşleşmesi var deseni ile her zaman başarılı olur. Sözdizimi aşağıdaki gibidir:

```csharp 
   expr is var varname
```

Burada değerini *expr* adlı yerel bir değişkene her zaman atanmış *varname*. *varName* aynı türde bir statik değişken *expr*. Aşağıdaki örnek, bir ifade adlı bir değişkene atayın için değişken deseni kullanır. `obj`. Ardından değerine ve türüne görüntüler `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

Unutmayın *expr* olduğu `null`, `is` ifade hala geçerlidir ve atar `null` için *varname*. 

# <a name="c-language-specification"></a>C# Dil Belirtimi
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [typeof](../../../csharp/language-reference/keywords/typeof.md)  
- [as](../../../csharp/language-reference/keywords/as.md)  
- [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)
