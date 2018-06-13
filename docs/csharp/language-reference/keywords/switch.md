---
title: switch anahtar sözcüğü (C# Başvurusu)
ms.date: 03/07/2017
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: 4e21700b36437bf9bd60bb4f33e2833819333f1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288898"
---
# <a name="switch-c-reference"></a>switch (C# Başvurusu)
`switch` tek bir seçtiği seçimi açıklamadır *geçiş bölüm* bir desen eşleştirme ile temel adaylar listesinden yürütmek için *ifade ile eşleşen*. 
  
 [!code-csharp[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]  

`switch` Deyimi alternatif olarak kullanılan genellikle bir [if-else](if-else.md) tek bir ifade üç veya daha fazla koşul karşı test varsa oluşturun. Örneğin, aşağıdaki `switch` ifadesi bir değişken türü olup olmadığını belirler `Color` üç değerden birini içeriyor: 

[!code-csharp[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)] 

Kullanan aşağıdaki örneğe eşdeğer olan bir `if` - `else` oluşturun. 

[!code-csharp[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)] 

## <a name="the-match-expression"></a>Eşleşme ifadesi

Eşleşme ifadesi düzenleri eşleştirilecek değer sağlar `case` etiketler. Sözdizimi aşağıdaki gibidir:

```csharp
   switch (expr)
```

C# 6'da, aşağıdaki türlerde bir değer döndüren bir ifadeye eşleşme ifadesi olması gerekir:

- bir [char](char.md).
- bir [dize](string.md).
- bir [bool](bool.md). 
- gibi bir integral değeri bir [int](int.md) veya [uzun](long.md).
- bir [enum](enum.md) değeri.

C# 7. 0'dan başlayarak, eşleşme ifadesi herhangi bir null olmayan ifade olabilir.
 
## <a name="the-switch-section"></a>Anahtar bölümü
 
 A `switch` deyimi bir veya daha fazla anahtar bölümleri içerir. Bir veya daha fazla her anahtar bölüm içerir *durumda etiketler* bir veya daha fazla deyimleri tarafından izlenen. Aşağıdaki örnekte basit bir `switch` üç anahtar bölümleri olan deyimi. Her anahtar bölümü gibi bir durum etiketi, sahip `case 1:`ve iki ifade.
 
  A `switch` deyimi herhangi bir sayıda anahtar bölümü içerebilir ve her bölüm aşağıdaki örnekte gösterildiği gibi durum etiketi, bir veya daha fazla olabilir. Ancak, hiçbir iki durum etiketi aynı ifadesi içeriyor olabilir.  

 [!code-csharp[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]  

 Switch deyimi yalnızca bir anahtar bölümünde yürütür. C# bir anahtar bölümünden sonraki devam etmek için yürütmeye izin vermez. Bu nedenle, aşağıdaki kod bir Derleyici Hatası CS0163 oluşturur: "Denetim olamaz atlayabilir bir case etiketinden (<case label>) diğerine."  

```csharp  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
Bu gereksinim, genellikle açıkça kullanarak anahtar bölüm çıkılarak karşılanır bir [sonu](break.md), [goto](goto.md), veya [dönmek](return.md) deyimi. Program denetim için geçemez sağlar ancak, aşağıdaki kodu aynı zamanda, geçersiz çünkü `default` bölümüne geçin.
  
 [!code-csharp[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]    
  
 Eşleşme ifadeyle eşleşen bir servis talebi etiket anahtarı bölümle deyimi listesinde yürütülmesi ilk deyimi ile başlar ve genellikle bir atlama deyimi kadar deyimi eşlemeleri gibi devam eder bir `break`, `goto case`, `goto label`, `return`, veya `throw`, ulaşıldı. Bu noktada, denetimi dışında aktarılır `switch` deyimi veya başka bir durum etiketi. A `goto` deyimi, kullanılırsa, gerekir aktarım denetimi için sabit bir etiket. Bir sabit olmayan etiket denetimi aktarmaya çalışırken istenmeyen yan etkiler, bu tür denetim kodu istenmeyen bir konumda aktarılıyor veya sonsuz bir döngüde oluşturma olabileceği için bu kısıtlama gereklidir.

## <a name="case-labels"></a>Durum etiketi

 Servis talebi her etiket eşleşme ifadesi karşılaştırmak için bir desen belirtir ( `caseSwitch` önceki örneklerde değişken). Eşleşirlerse, denetimi içeren anahtar bölümü aktarılır **ilk** eşleşen durum etiketi. Durum etiketi desen eşleştirme ifadesi eşleşirse, Denetim bölümle aktarılır `default` varsa durum etiketi. Varsa hiçbir `default` durumu, herhangi bir anahtar bölümü hiçbir deyimlerinde yürütülür ve denetim dışında aktarılır `switch` deyimi.

 Hakkında bilgi için `switch` deyimi ve desen eşleştirme, bkz: [ile desen eşleştirme `switch` deyimi](#pattern) bölümü.

 C# 6 yalnızca sabit düzeni destekler ve sabit değerleri yinelenmesinin izin verme olduğundan, birbirini dışlayan değerleri büyük küçük harf etiketleri tanımlamak ve yalnızca bir desen eşleştirme ifadesi eşleştirebilirsiniz. Sonuç olarak, hangi sırayla `case` deyimleri görünür olan önemli.

 C# 7.0, ancak diğer desenleri desteklenmediğinden durum etiketi birbirini dışlayan değerleri tanımlayın olmayan ve birden çok desen eşleştirme ifadesi eşleştirebilirsiniz. Yalnızca ilk eşleştirme deseni içeren anahtar bölüm deyimlerinde çalıştırıldığı için hangi sırayla `case` deyimleri görünür önemlidir şimdi. C#, case deyimi deyimleri eşit olan veya önceki deyimleri kümeleridir anahtar bölüm algılarsa, "anahtar durumu önceki bir örneği tarafından zaten işlendi." bir derleyici hatası, CS8120, oluşturur 

 Aşağıdaki örnek gösterilmektedir bir `switch` olmayan-birbirini dışlayan desenleri çeşitli kullanan deyimi. Taşırsanız `case 0:` böylece artık ilk bölümde değil bölüm geçiş `switch` deyimi, C# Derleyici Hatası değeri sıfır olmayan bir tamsayı tanımlanan örnekle olan bir alt tüm tamsayıların olduğundan oluşturur tarafından `case int val` deyimi.

 [!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]    

Bu sorunu düzeltin ve iki yoldan biriyle derleyici uyarısı kaldırın:

- Anahtar bölümlerin sırasını değiştirerek. 
 
- Kullanarak bir < /a adı "zaman" = > zaman yan tümcesi</a> içinde `case` etiketi.
 
## <a name="the-default-case"></a>`default` Durumu

`default` Durumda eşleşme ifadesi diğer eşleşmiyorsa yürütmek için anahtar bölüm belirtir `case` etiketi. Varsa bir `default` durumda mevcut değil ve eşleşme ifadesi diğer eşleşmiyor `case` program akışı etiketi, geçer `switch` deyimi.

`default` Durumda herhangi bir sırada görünebilir `switch` deyimi. Kaynak kodu, sırasıyla bağımsız olarak, her zaman son olarak, tüm değerlendirilir `case` etiketleri değerlendirilir.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" /> Deseni ile eşleşen `switch` deyimi
  
Her `case` deyimi eşleşme ifadesi eşleşirse, yürütülecek içeren kendi anahtar bölüm neden olan bir desen tanımlar. C# ' in tüm sürümleri sabit düzenini destekler. Kalan desenleri, C# 7. 0'den başlayarak desteklenir. 
  
### <a name="constant-pattern"></a>Sabit düzeni 

Sabit desen eşleşmesi ifadesi belirtilen bir sabit eşit olup olmadığını sınar. Sözdizimi aşağıdaki gibidir:

```csharp
   case constant:
```

Burada *sabit* sınamak için bir değerdir. *Sabit* aşağıdaki sabit ifadelerden herhangi biri olabilir: 

- A [bool](bool.md) değişmez değer, ya da `true` veya `false`.
- Tüm integral gibi sabit bir [int](int.md), [uzun](long.md), veya bir [bayt](byte.md). 
- Bir bildirilen adını `const` değişkeni.
- Bir numaralandırma sabiti.
- A [char](char.md) değişmez.
- A [dize](string.md) değişmez.

Sabit ifade aşağıdaki gibi değerlendirilir:

- Varsa *expr* ve *sabit* tam sayı türleri, C# eşitlik işleci ifade döndürüp döndürmediğini belirler `true` (diğer bir deyişle, olup olmadığını `expr == constant`).

- Aksi takdirde, ifadenin değerini statik bir çağrı tarafından belirlenir [Object.Equals (ifade, sabit)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi.  

Aşağıdaki örnek, belirli bir tarihin hafta sonu, haftanın, başında veya ortasında haftanın son gününü iş haftanın ilk günü olup olmadığını belirlemek için sabit desen kullanır. Bu hesaplar <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> özelliği üyeleri için geçerli günün <xref:System.DayOfWeek> numaralandırması. 

[!code-csharp[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Aşağıdaki örnek, bir otomatik kahve makine taklit eden bir konsol uygulamasında kullanıcı girişini işlemek için sabit desen kullanır.
  
 [!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]  

### <a name="type-pattern"></a>Tür deseni

Tür deseni kısa türü değerlendirme ve dönüştürme sağlar. İle kullanıldığında `switch` desen eşleştirme gerçekleştirmek için deyimi, bir ifade belirtilen türe dönüştürülüp dönüştürülemeyeceğini test eder ve olabiliyorsa, bu tür bir değişkene çevirir. Sözdizimi aşağıdaki gibidir:

```csharp
   case type varname 
```
Burada *türü* türün adı sonucu *expr* dönüştürülmekte olan ve *varname* hangi nesne sonucu *ifade*eşlemesi başarılı olursa dönüştürülür. 

`case` İfade `true` aşağıdakilerden biri doğruysa:

- *Expr* aynı türde örneği *türü*.

- *Expr* türeyen bir tür örneği *türü*. Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.

- *Expr* bir taban sınıf, derleme zamanı türüne sahip *türü*, ve *expr* olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*. *Derleme zamanı tür* bir değişken değişkenin türü bildiriminde tanımlandığı gibi türüdür. *Çalışma zamanı tür* bir değişken bu değişkenine atanan örnek türüdür.

- *Expr* uygulayan bir tür örneği *türü* arabirimi.

Servis talebi ifade doğruysa *varname* kesinlikle atanır ve yalnızca anahtarı bölüm içinde yerel kapsama sahip.

Unutmayın `null` bir türle eşleşmiyor. Eşleştirilecek bir `null`, aşağıdaki `case` etiketi:

```csharp
case null:
```
 
Aşağıdaki örnek türü desen çeşitli koleksiyon türleri hakkında bilgi sağlamak için kullanır.

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Desen eşleştirme olmadan, bu kod şu şekilde yazılmış olabilir. Bir dönüştürme sonucu olup olmadığını sınamak için gereksinimini ortadan kaldırarak daha küçük, okunabilir kod türü desen eşleştirme kullanımını üreten bir `null` veya yinelenen atamaları gerçekleştirmek için.  

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a>`case` Deyimi ve `when` yan tümcesi

Case deyimleri birbirini dışlayan olması gerekmez çünkü C# 7.0 ile başlayarak, kullanabilirsiniz eklemek bir `when` ek bir koşul belirtmek için yan tümcesi memnun, doğru olarak değerlendirilecek case deyimi için. `when` Yan tümcesi bir Boole değeri döndürür herhangi bir ifade olabilir. Daha yaygın kullanımları birini `when` yan tümcesi anahtar bölüm bir eşleşme ifadesi değeri olduğunda yürütülmesini engellemek için kullanılan `null`. 

 Aşağıdaki örnek, bir taban tanımlar `Shape` sınıfı, bir `Rectangle` öğesinden türetilen sınıf `Shape`ve bir `Square` öğesinden türetilen sınıf `Rectangle`. Kullandığı `when` emin olmak için yan tümcesi `ShowShapeInfo` değerlendirir bir `Rectangle` eşit uzunlukta ve genişliklerini olarak atanan nesne bir `Square` bile değiştirilmediğinden olarak örneği bir `Square` nesnesi. Yöntem bilgileri görüntülemek denemez herhangi bir nesne hakkında `null` veya bir şekil, alan sıfırsa. 

[!code-csharp[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]
  
Unutmayın `when` test girişiminde örnek yan tümcesinde olup bir `Shape` nesne `null` değil çalıştırma. İçin test etmek için doğru türde desen bir `null` olan `case null:`.

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](../../../../includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  

 [C# başvurusu](../index.md)  
 [C# Programlama Kılavuzu](../../programming-guide/index.md)  
 [C# Anahtar Sözcükleri](index.md)  
 [if-else](if-else.md)  
 [Desen Eşleştirme](../../pattern-matching.md)  
 

 
