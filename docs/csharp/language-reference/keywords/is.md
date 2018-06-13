---
title: is (C# Başvurusu)
ms.date: 02/17/2017
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: c01152d016a852c15ffa1d1c82c16d6795965f31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289223"
---
# <a name="is-c-reference"></a>is (C# Başvurusu) #

Bir nesneyi belirtilen bir türle uyumlu değil veya (C# 7. 0'dan başlayarak) belirli bir desene göre bir ifade testleri olup olmadığını denetler.

## <a name="testing-for-type-compatibility"></a>Tür uyumluluk için test etme ##

`is` Anahtar sözcüğü çalışma zamanında tür uyumluluğu değerlendirilir. Bir ifadenin sonucu belirtilen türe dönüştürülebilir veya bir nesne örneği olup olmadığını belirler. Sözdizimine sahip

```csharp
   expr is type
```

Burada *expr* bazı türünün bir örneği için değerlendirilen ifade olan ve *türü* türün adı sonucu *expr* dönüştürülecek. `is` İfadesi `true` varsa *expr* null olmayan ve ifade değerlendirmede sonuçlarına dönüştürülebilir nesne *türü*; Aksi takdirde döndürdüğü `false`.

Örneğin, aşağıdaki kodu belirler. `obj` örneğine cast `Person` türü:

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

`is` Deyimi doğruysa varsa:

- *Expr* aynı türde örneği *türü*.

- *Expr* türeyen bir tür örneği *türü*. Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.

- *Expr* bir taban sınıf, derleme zamanı türüne sahip *türü*, ve *expr* olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*. *Derleme zamanı tür* bir değişken değişkenin bildiriminde tanımlandığı gibi türüdür. *Çalışma zamanı tür* bir değişken bu değişkenine atanan örnek türüdür.

- *Expr* uygulayan bir tür örneği *türü* arabirimi.

Aşağıdaki örnekte gösterilir `is` ifadeyi hesaplar için `true` her dönüştürmeler.

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

`is` Anahtar sözcüğü her zaman ya da olacak şekilde ifade biliniyorsa bir derleme zamanı uyarı oluşturur `true` veya `false`. Yalnızca başvuru dönüşümleri, kutulama dönüşümler ve kutudan çıkarma dönüşümleri dikkate alır; Kullanıcı tanımlı dönüşümler veya bir tür tarafından tanımlanan dönüşümleri düşünmez [örtük](implicit.md) ve [açık](explicit.md) işleçler. Dönüştürme işleminin sonucu derleme zamanında bilindiğinden aşağıdaki örnekte uyarılar oluşturur. Unutmayın `is` dönüştürmeleri için ifade `int` için `long` ve `double` return dönüştürmeler tarafından işlenen beri false, [örtük](implicit.md) işleci.

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

`expr` anonim yöntemler dışında bir değer döndüren ifadeye ve lambda ifadeleri olabilir. Aşağıdaki örnek kullanır `is` bir yöntem çağrısının dönüş değerini değerlendirmek için.   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

C# 7. 0'dan başlayarak, deseni ile eşleşen kullanabilirsiniz [türü düzeni](#type) kullanan daha kısa kod yazmaya `is` deyimi.

## <a name="pattern-matching-with-is"></a>Desen ile eşleştirme `is` ##

C# 7.0 ile başlayan `is` ve [geçiş](../../../csharp/language-reference/keywords/switch.md) deyimleri destek desen eşleştirme. `is` Anahtar sözcüğünü aşağıdaki desenleri destekler:

- [Tür deseni](#type), bir ifade belirtilen türe dönüştürülüp dönüştürülemeyeceğini test eder ve, olabiliyorsa, bu tür bir değişkene çevirir.

- [Sabit düzeni](#constant), belirtilen bir sabit değer için bir ifadeyi değerlendirir olup olmadığını sınar.

- [var deseni](#var), her zaman başarılı olur ve bir ifadenin değerini yeni yerel bir değişkene bağlayan bir eşleşme. 

### <a name="type" /> Tür deseni </a>

Tür deseni desen eşleştirme gerçekleştirmek için kullanılırken `is` bir ifade belirtilen türe dönüştürülüp dönüştürülemeyeceğini test eder ve olabiliyorsa, bu tür bir değişkene çevirir. Basit bir uzantısıdır `is` kısa türü değerlendirme ve dönüştürme sağlayan deyimi. Genel biçiminde `is` türü deseni:

```csharp
   expr is type varname 
```

Burada *expr* bazı türünün bir örneği için değerlendirilen ifade *türü* türün adı sonucu *expr* dönüştürülmekte olan ve *varname* hangi nesne sonucu *expr* dönüştürülür `is` test `true`. 

`is` İfade `true` aşağıdakilerden biri doğruysa:

- *Expr* aynı türde örneği *türü*.

- *Expr* türeyen bir tür örneği *türü*. Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.

- *Expr* bir taban sınıf, derleme zamanı türüne sahip *türü*, ve *expr* olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*. *Derleme zamanı tür* bir değişken değişkenin bildiriminde tanımlandığı gibi türüdür. *Çalışma zamanı tür* bir değişken bu değişkenine atanan örnek türüdür.

- *Expr* uygulayan bir tür örneği *türü* arabirimi.

Varsa *exp* olan `true` ve `is` ile kullanılan bir `if` deyimi, *varname* atanır ve yerel kapsamda sahip `if` deyimi yalnızca.

Aşağıdaki örnek kullanır `is` bir türün uygulamasını sağlamak için türü desen <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> yöntemi.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Desen eşleştirme olmadan, bu kod şu şekilde yazılmış olabilir. Bir dönüştürme sonucu olup olmadığını sınamak için gereksinimini ortadan kaldırarak daha küçük, okunabilir kod türü desen eşleştirme kullanımını üreten bir `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` Türü desen türündeki bir değer belirlerken daha küçük kod da oluşturur. Aşağıdaki örnek kullanır `is` bir nesne olup olmadığını belirlemek için türü desen bir `Person` veya `Dog` uygun bir özelliğin değerini göstermeden önce örneği. 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Desen eşleştirme olmadan eşdeğer kodu içeren bir açık atama ayrı bir atama gerektirir.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><a name="constant" /> Sabit düzeni ###

Sabit desenle eşleşen kalıbı gerçekleştirirken `is` belirtilen bir sabit bir ifade eşit olup olmadığını sınar. C# 6 ve önceki sürümlerinde, sabit düzeni tarafından desteklenen [geçiş](switch.md) deyimi. C# 7. 0'dan başlayarak, onu tarafından desteklenen `is` de deyimi. Sözdizimi aşağıdaki gibidir:

```csharp
   expr is constant
```

Burada *expr* değerlendirmek için ifade ve *sabit* sınamak için bir değerdir. *Sabit* aşağıdaki sabit ifadelerden herhangi biri olabilir: 

- Değişmez değer.

- Bir bildirilen adını `const` değişkeni.

- Bir numaralandırma sabiti.

Sabit ifade aşağıdaki gibi değerlendirilir:

- Varsa *expr* ve *sabit* tam sayı türleri, C# eşitlik işleci ifade döndürüp döndürmediğini belirler `true` (diğer bir deyişle, olup olmadığını `expr == constant`).

- Aksi takdirde, ifadenin değerini statik bir çağrı tarafından belirlenir [Object.Equals (ifade, sabit)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi.  

Aşağıdaki örnekte bir nesne olup olmadığını sınamak için türü ve sabiti desenleri birleştiren bir `Dice` örneği ve, varsa, belirlemek için bölmek toplama değeri olup 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <a name="var" /> var deseni </a>

Desen eşleştirme var deseni ile her zaman başarılı olur. Sözdizimi aşağıdaki gibidir:

```csharp 
   expr is var varname
```

Burada değerini *expr* her zaman adlı yerel bir değişkene atanır *varname*. *varName* statik bir değişken aynı türde *expr*. Aşağıdaki örnek, bir ifade adlı bir değişkene atamak var deseni kullanır. `obj`. Ardından değerini ve türünü görüntüler `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

Unutmayın *expr* olan `null`, `is` ifade hala geçerlidir ve atar `null` için *varname*. 

# <a name="c-language-specification"></a>C# Dil Belirtimi
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [typeof](../../../csharp/language-reference/keywords/typeof.md)  
 [as](../../../csharp/language-reference/keywords/as.md)  
 [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)
