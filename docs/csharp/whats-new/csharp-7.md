---
title: C# 7.0 - C# Kılavuzu yenilikler nelerdir?
description: C# dilinin gelecek sürümünde 7 gelecek yeni özelliklere genel bakış edinin.
ms.date: 12/21/2016
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 08e9b9d1a991c6dd18477214dec60fba95afc6c9
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415734"
---
# <a name="whats-new-in-c-70"></a>C# 7.0 yenilikleri

C# 7.0 C# dili için yeni özellikler ekler:
* [`out` Değişkenleri](#out-variables)
    - Bildirebilirsiniz `out` kullanıldıkları yöntemi için bağımsız değişkeni olarak satır içi değerleri.
* [Demetler](#tuples)
    - Birden çok ortak alanları içeren basit, adsız türleri oluşturabilirsiniz. Bu tür semantikleri, derleyiciler ve Araçlar IDE anlayın.
* [Atılanlar](#discards)
    - İptali atanan değer hakkında umursamaz atamalarını kullanılan geçici, salt yazılır değişkenlerdir. Diziler ve kullanıcı tanımlı türler Ayrıştırma sırasında yanı sıra ile yöntemleri çağrılırken özellikle yararlı oldukları `out` parametreleri.
* [Desen Eşleştirme](#pattern-matching)
    - Rastgele türler ve bu türlerin üyelerinin değerlerini göre dallanma mantığı oluşturabilirsiniz.
* [`ref` yerel değerleri ve dönüşleri](#ref-locals-and-returns)
    - Diğer depolama başvuruları yöntemi yerel değişkenleri ve dönüş değerleri olabilir.
* [Yerel İşlevler](#local-functions)
    - İşlevler, kapsam ve görünürlük sınırlamak için diğer işlevler içinde iç içe yerleştirebilirsiniz.
* [Daha fazla ifade gövdeli üyeler](#more-expression-bodied-members)
    - İfadeleri kullanarak yazılabilir üye listesini geldi.
* [`throw` İfadeleri](#throw-expressions)
    - Daha önce olduğundan kullanılamaz kod yapıları özel durumlar oluşturabilecek `throw` bir ifadesi. 
* [Genelleştirilmiş bir zaman uyumsuz dönüş türleri](#generalized-async-return-types)
    - Yöntemleri ile bildirilmiş `async` değiştiricisi, ek olarak diğer türleri döndürebilir `Task` ve `Task<T>`.
* [Sayısal sabit değer sözdizimi geliştirmeleri](#numeric-literal-syntax-improvements)
    - Yeni belirteç sayısal sabitlere okunabilirliği geliştirir.

Bu konunun geri kalanı özelliklerin her biri açıklanmaktadır. Her bir özellik için ardındaki mantık öğreneceksiniz. Söz dizimi öğreneceksiniz. Burada yeni özelliği kullanarak daha üretken bir geliştirici olarak yapacağınız bazı örnek senaryolar görürsünüz. 

## <a name="out-variables"></a>`out` Değişkenleri

Destekleyen varolan sözdizimi `out` parametreleri bu sürümde geliştirildi.  

Daha önce out değişkeni bildirimi başlatılmasını iki farklı deyimleri içinde ayırmak gerekir:

[!code-csharp[OutVariableOldStyle](../../../samples/snippets/csharp/new-in-7/program.cs#03_OutVariableOldStyle "classic out variable declaration")]

Artık bildirebilirsiniz `out` ayrı bildirim deyimindeki yazmak yerine bir yöntem çağrısının bağımsız değişken listesinde değişkenleri:

[!code-csharp[OutVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#01_OutVariableDeclarations "Out variable declarations")]

Türünü belirtmek isteyebilirsiniz `out` , anlaşılması için değişken yukarıda da gösterildiği gibi. Ancak bir türü örtük olarak belirlenmiş yerel değişken kullanarak dili destekler:

[!code-csharp[OutVarVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#02_OutVarVariableDeclarations "Implicitly typed Out variable")]

* Kodu daha kolay. 
    - Out değişkeni da değil başka bir satırda yukarıdaki kullandığınız bildirdiğiniz.
* Bir başlangıç değeri atamanız gerekmez.
    - Bildirmek `out` bunu atanmadan önce değişken bir yöntem çağrısında kullanıldığı yanlışlıkla kullanamazsınız.

Bu özelliğin en yaygın kullanımı olacaktır `Try` deseni. Bu düzende, bir yöntemi döndürür bir `bool` başarısı veya başarısızlığı gösteren ve bir `out` sonucunu yöntem başarılı olursa sağlayan değişken.

Kullanırken `out` değişken bildirimi bildirilmiş bir değişken "sızıntıları" if dış kapsamına deyimi. Bu değişkeni sonradan kullanmanıza olanak tanır:

```csharp
if (!int.TryParse(input, out int result))
{    
    return null;
}

return result;
```

## <a name="tuples"></a>Demetler

> [!NOTE]
> Yeni diziler işlevleri <xref:System.ValueTuple> türleri.
> NuGet paketini eklemeniz gerekir [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) türlerini içermez platformlarda kullanmak için.
>
> Bu çerçevede teslim türleri kullanan diğer dil özellikleri benzer. Örnek dahil `async` ve `await` güvenmek `INotifyCompletion` arabirimi ve bağlı LINQ `IEnumerable<T>`. Ancak, .NET, daha fazla platform bağımsız olma gibi teslim mekanizması değişiyor. .NET Framework her zaman aynı temposu dil derleyicisi olarak yükleyeceğiniz değil. Yeni dil özellikleri üzerinde yeni türler kullanan, dil başlayamıyorsunuz türlerine NuGet paketleri olarak kullanılabilir. Bu yeni türleri ve .NET standart API için eklenen framework'ün bir parçası olarak sunulan NuGet paketini gereksinim kaldırılacak.

C# sınıfları ve, tasarım amacı açıklamak için kullanılan yapıları için zengin bir söz dizimi sağlar. Ancak bazen zengin Bu sözdizimi en az avantajı ile ek iş gerektirir. Birden fazla veri öğesini içeren basit bir yapıya gereken yöntemler genellikle yazabilir. Bu senaryoları desteklemek için *diziler* C# için eklendi. Diziler veri üyelerini temsil etmek için birden fazla alan içeren basit veri yapılarıdır.
Alanlar yok doğrulandı ve kendi yöntem tanımlanamaz

> [!NOTE]
> Diziler C# 7.0 önce kullanılabilir, ancak verimsiz ve dil desteği yok vardı.
> Bu dizi öğeleri yalnızca olarak başvurulan geliyordu `Item1`, `Item2` ve benzeri. C# 7.0 alanlarını yeni ve daha verimli bir tanımlama grubu türleri kullanarak bir demet için anlamsal adları sağlayan diziler için dil desteği sunar.

Bir değer her üyesine atayarak bir tanımlama grubu oluşturabilirsiniz:

[!code-csharp[UnnamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#04_UnnamedTuple "Unnamed tuple")]

Atama üyeleri olan bir dizi oluşturur `Item1` ve `Item2`, aynı şekilde kullanabileceğiniz <xref:System.Tuple> anlam adları her tanımlama grubu üyelerinin sağlayan bir kayıt düzeni oluşturmak için sözdizimi değiştirebilirsiniz:

[!code-csharp[NamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#05_NamedTuple "Named tuple")]

`namedLetters` Tanımlama grubu olarak adlandırılan alanları içeren `Alpha` ve `Beta`. Bu adları, yalnızca derleme zamanında mevcut ve örnek için çalışma zamanında yansıma kullanarak demet incelerken korunmaz.

Bir tanımlama grubu atamasını alanların adlarını atamada sağ tarafta da belirtebilirsiniz:

[!code-csharp[ImplicitNamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#06_ImplicitNamedTuple "Implicitly named tuple")]

Her iki sol ve sağ tarafında atama alanların adlarını belirtebilirsiniz:

[!code-csharp[NamedTupleConflict](../../../samples/snippets/csharp/new-in-7/program.cs#07_NamedTupleConflict "Named tuple conflict")]

Yukarıdaki satırı bir uyarı üretir `CS8123`, şeklinde ataması sağ tarafında adları `Alpha` ve `Beta` sol tarafındaki adlarıyla çakıştığından göz ardı edilir `First` ve `Second`.

Yukarıdaki örnekler diziler bildirmek için temel söz dizimini gösterir. Diziler için dönüş türleri olarak faydalı `private` ve `internal` yöntemleri. Diziler, birden çok ayrı değer döndürmek bu yöntemleri için basit bir söz dizimi sağlar: Yazma iş kaydettiğiniz bir `class` veya `struct` döndürülen tür tanımlar. Yeni tür oluşturma için gerek yoktur.

Daha verimli ve daha üretken bir tanımlama grubu oluşturuluyor.
Bu, birden fazla değer taşıyan bir veri yapısını tanımlamak için daha basit ve basit bir söz dizimi olur. Aşağıdaki örnek yöntemi, bir tamsayı dizisinde bulunan minimum ve maksimum değerleri döndürür:

[!code-csharp[TupleReturningMethod](../../../samples/snippets/csharp/new-in-7/program.cs#08_TupleReturningMethod "Tuple returning method")]

Bu şekilde demetlerin kullanılmasını sağlayan çeşitli avantajlar sunar:

* Yazma iş kaydettiğiniz bir `class` veya `struct` döndürülen tür tanımlar. 
* Yeni tür oluşturma gerekmez.
* Dil geliştirmelerini çağırma gereksinimini kaldırır <xref:System.Tuple.Create``1(``0)> yöntemleri.

Yöntem bildiriminin döndürülen kayıt düzeninin alanların adlarını sağlar. Yöntemini çağırdığınızda, bir tanımlama grubu olan alanlar dönüş değeridir `Max` ve `Min`:

[!code-csharp[CallingTupleMethod](../../../samples/snippets/csharp/new-in-7/program.cs#09_CallingTupleMethod "Calling a tuple returning method")]

Yöntemden döndürülen bir tanımlama grubu üyelerinin açmak istediğinizde zamanlar olabilir.  Dizideki değerlerin her biri için ayrı değişkenleri bildirerek bunu yapabilirsiniz. Bu adlandırılır *ayrıştırma* tanımlama grubu:

[!code-csharp[CallingWithDeconstructor](../../../samples/snippets/csharp/new-in-7/program.cs#10_CallingWithDeconstructor "Deconstructing a tuple")]

. NET'te herhangi bir tür için benzer bir ayrıştırma de sağlayabilirsiniz. Yazarak yapıldığını bir `Deconstruct` yöntemi sınıfının bir üyesi olarak. Olduğunu `Deconstruct` yöntem kümesi sağlar `out` ayıklamak istediğiniz bağımsız değişkenleri özelliklerin her biri için. Bunu göz önünde bulundurun `Point` ayıklayan deconstructor yöntemi sağlar sınıfını `X` ve `Y` koordinatları:

[!code-csharp[PointWithDeconstruction](../../../samples/snippets/csharp/new-in-7/point.cs#11_PointWithDeconstruction "Point with deconstruction method")]
 
Tek tek alanları atayarak ayıklayabileceğiniz bir `Point` bir demet için:

[!code-csharp[DeconstructPoint](../../../samples/snippets/csharp/new-in-7/program.cs#12_DeconstructPoint "Deconstruct a point")]

Tanımlanan adlarına göre bağlı değildir `Deconstruct` yöntemi. Extract değişkenleri atama bir parçası olarak yeniden adlandırabilirsiniz:  

[!code-csharp[DeconstructNames](../../../samples/snippets/csharp/new-in-7/program.cs#13_DeconstructNames "Deconstruct with new names")]

Diziler hakkında daha da ayrıntılı bilgi edinebilirsiniz [diziler konu](../tuples.md).

## <a name="discards"></a>Atar

Olduğunda, genellikle bir demet ayrıştırma veya bir yöntemi çağırmak `out` parametreleri hakkında umursamaz ve kullanmayı düşünmüyorsanız değeri bir değişken tanımlayın zorunda. C# için destek ekler *atar* bu senaryonun işlenmesi için. Bir atma adı olan bir salt yazılır değişkendir `_` (alt çizgi karakteri); tüm tek bir değişkene atmak düşündüğünüz değerleri atayabilirsiniz. Bir atma gibi atanmamış bir değişkenidir; atama ifadesi dışında atma kodda kullanılamaz.

Atar, aşağıdaki senaryolarda desteklenir:

* Tanımlama grubu veya kullanıcı tanımlı türler ayrıştırma olduğunda.

* Yöntemleri çağrılırken [kullanıma](../language-reference/keywords/out-parameter-modifier.md) parametreleri.

* İşlemle eşleşen desende [olduğu](../language-reference/keywords/is.md) ve [geçiş](../language-reference/keywords/switch.md) deyimleri.

* Açıkça istediğinizde bir tek başına tanımlayıcı olarak bir atma atamadan değerini belirleyin.

Aşağıdaki örnekte tanımlayan bir `QueryCityDataForYears` farklı iki yıllık bir şehir için bir veri içeren bir 6 bölütlü döndüren yöntem. Örnek yöntem çağrısında yöntem tarafından döndürülen iki popülasyon değerleri ile ilgilidir ve bu nedenle kalan değerler demet tanımlama grubu deconstructs olduğunda atar gibi davranır.

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Daha fazla bilgi için [atar](../discards.md).

## <a name="pattern-matching"></a>Desen eşleştirme

*Desen eşleştirme* yöntem gönderimine dışındaki bir nesne türü özellikleri uygulamak izin veren bir özelliktir. Zaten bir nesne türüne göre yöntemi gönderme hakkında bilgi sahibi. Yöntemi, bir nesnenin türüne göre gönderme uygulamak için dili sözdizimi, nesne yönelimli, sanal programlama ve geçersiz kılma yöntemleri sağlar. Temel ve türetilmiş sınıfları farklı uygulamalar sağlayabilir. Desen eşleştirme ifadeleri bu kavramı genişletmeniz Devralma Hiyerarşisi ilgili olmayan türler ve veri öğeleri için benzer gönderme desenleri kolayca uygulayabilirsiniz. 

Desen eşleştirme destekler `is` ifadeleri ve `switch` ifadeler. Her bir nesne ve o nesnenin Aranan deseni karşılayıp karşılamadığını belirlemek için özelliklerini inceleme sağlar. Kullandığınız `when` düzeninin ek kuralları belirtmek için anahtar sözcüğü.

### <a name="is-expression"></a>`is` İfade

`is` Desen ifadesi genişletir bilinen [ `is` işleci](../language-reference/keywords/is.md#pattern-matching-with-is) bir nesne türünü ötesinde sorgulamak için.

Basit bir senaryoyla başlayalım. Desen eşleştirme ifadeleri iş ile ilgisiz türleri kolay algoritmalar nasıl oluşturduğunu gösteren bu senaryo özellikleri ekleyeceğiz. Zar pay sayısı toplamını hesaplar bir yöntem ile başlayacağız:

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

Bazı pay ile birden çok dice yapılan burada zar pay toplamını bulmak gerektiğini hızla fark edebilirsiniz (zar, plural dice'dir). Giriş dizisinin bir parçası birden çok sonuç yerine tek bir sayı olabilir:

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

`is` Desen ifadesi bu senaryoda oldukça iyi çalışır. Tür denetleme bir parçası olarak bir değişken başlatma yazın. Bu, doğrulanmış çalışma zamanı türü yeni bir değişken oluşturur.

Bu senaryolar genişletme tutmak gibi daha fazla yapı bulabilirsiniz `if` ve `else if` deyimleri. Zahmetli hale geldikten sonra büyük olasılıkla geçmek istersiniz `switch` ifadeleri desen.

### <a name="switch-statement-updates"></a>`switch` deyim

*Eşleşen ifade* sahip temel tanıdık bir söz dizimi `switch` ifadesi C# dilinin zaten parçası. Şimdi yeni çalışmaları eklemeden önce bir eşleme ifadesi kullanmak için mevcut kodu çevir: 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

Eşleşme ifadeleri değerinden biraz farklı bir sözdizimi sahip `is` ifadeleri, burada bildirdiğiniz tür ve değişken başındaki `case` ifade.

Eşleşme ifadeleri sabitleri de destekler. Bu basit durumlar hesaba katacak şekilde tarafından zamandan tasarruf edebilirsiniz:

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

Yukarıdaki kod çalışmaları için ekler `0` bir özel durum olarak `int`, ve `null` müdahalesi olduğunda özel bir durum olarak. Bu önemli bir yeni özellik anahtarı düzeni ifadelerde gösterir: sırasını `case` ifadeleri şimdi önemlidir. `0` Çalışması genel önce görünmelidir `int` çalışması. Aksi durumda, ilk eşleşme gerçekleştirilecek desenin olacak `int` değer olsa bile çalışması `0`. Bir sonraki çalışması zaten işlenmiş şekilde eşleşme ifadeleri yanlışlıkla sipariş, derleyici, bayrak ve bir hata oluşturur.

Boş bir giriş sırası için özel durum bu aynı davranışı sağlar.
Gördüğünüz gibi bu durum bir `IEnumerable` öğelere sahip öğesi genel önce görünmelidir `IEnumerable` çalışması.

Bu sürüm ayrıca eklemiştir bir `default` çalışması. `default` Çalışması her zaman değerlendirilir son, kaynak sırasını bağımsız olarak görünür. Bu nedenle, kuralı eklemektir `default` büyük/küçük harf son.

Son olarak, bir son ekleyelim `case` zar yeni stili için. Bazı oyunlar yüzdebirlik dice daha büyük sayılar aralıklarını temsil etmek için kullanın. 

> [!NOTE]
> 0 ile 99 arasında iki 10 taraflı yüzdebirlik dice tüm sayıları temsil edebilir. Bir özel etiketli yüz sahip `00`, `10`, `20`,... `90`. Diğer özel etiketli kenarlara sahip `0`, `1`, `2`,... `9`. İki zar değerlerini birleştirmek ve her sayı 0 ile 99 arasında alabilirsiniz.

Bu tür bir zar koleksiyonunuza eklemek için önce yüzdebirlik dice temsil edecek bir tür tanımlar. `TensDigit` Özellik değerlerini depolar `0`, `10`, `20`, en fazla `90`:

[!code-csharp[18_PercentileDice](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDice "Percentile Die type")]

Ardından, ekleme bir `case` eşleşen yeni türü ifadesi:

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

Desen eşleştirme ifadelerinde yeni sözdizimi, bir nesnenin türü ya da kısa ve anlaşılır bir söz dizimi kullanılarak diğer özellikleri de dayalı dağıtma algoritmaları oluşturmak kolaylaştırır. Desen eşleştirme ifadeleri, bu yapıları tarafından devralma ilişkisiz veri türlerinde etkinleştirin.

Adanmış konusunda desen hakkında daha fazla bilgi [desen eşleştirme C# dilinde](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Ref yerel değerleri ve dönüşleri

Bu özelliği kullanın ve başka bir yerde tanımlanan değişkenleri başvuruları dönüş algoritmalar sağlar. Örneğin, büyük matrisleri ile çalışma ve belirli özelliklere sahip tek bir konum bulma. Bir yöntem tek bir konum için iki indeks matriste döndürür:

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

Bu kod ile birçok sorun vardır. İlk olarak bir dizi döndüren bir ortak yöntemidir. Bu dili destekler, ancak kullanıcı tanımlı türler (sınıflar veya yapılar) yönelik ortak API'ler tercih edilir.

İkinci olarak, bu yöntem, dizinleri matris öğeye döndürmektir.
Bu başvuru matrisi ve bir öğeyi değiştirmek için bu dizinleri kullanan kod yazmak için çağıranlar doğurur:

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

Döndüren bir yöntem yerine yazmak istediğiniz bir *başvuru* değiştirmek istediğiniz matris öğesine. Bunu yalnızca güvenli olmayan kod kullanarak ve bir işaretçi döndüren gerçekleştirirsiniz bir `int` önceki sürümlerinde.

Şimdi bir dizi değişikliği ref yerel özelliği göstermek ve dahili depolama başvuru döndüren bir yöntem oluşturma işlemini göstermek için yol.
Bu doğrultuda, ref dönüş ve bunu kötüye yanlışlıkla koruyan bir ref yerel özelliği kurallarını öğreneceksiniz.

Başlangıç değiştirerek `Find` BT'nin döndürecek şekilde yöntem bildiriminde bir `ref int` yerine bir tanımlama grubu. Ardından, iki indeks yerine Matristeki depolanan değer döndürecek şekilde return deyimi değiştirin:

```csharp
// Note that this won't compile. 
// Method declaration indicates ref return,
// but return statement specifies a value return.
public static ref int Find2(int[,] matrix, Func<int, bool> predicate)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
        for (int j = 0; j < matrix.GetLength(1); j++)
            if (predicate(matrix[i, j]))
                return matrix[i, j];
    throw new InvalidOperationException("Not found");
}
```

Bir yöntemi döndürür bildirdiğinizde bir `ref` değişkeni de eklemeniz gerekir `ref` her iade bildirimde anahtar sözcüğü. Başvuru ile dönüş gösterir ve daha sonra kodu okuyan yardımcı geliştiriciler yöntemi başvuru ile döndürülen unutmayın:

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

Yöntem matriste tamsayı değerine bir başvuru döndürür, burada çağrılır değiştirmeniz gerekir.  `var` Bildirimi anlamına `valItem` artık bir `int` yerine bir demet:

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

İkinci `WriteLine` yukarıdaki örnekte deyimi yazdırır değerini `42`değil `24`. Değişken `valItem` olduğu bir `int`değil bir `ref int`. `var` Anahtar sözcüğü türü belirtmek derleyiciyi etkinleştirir, ancak değil örtük olarak ekleyecek `ref` değiştiricisi. Bunun yerine, değeri adlandırılan tarafından `ref return` olduğu *kopyalanan* atamanın sol tarafı değişkenine. Değişken değil bir `ref` yerel.

Eklemenize gerek istediğiniz sonucu elde etmek için `ref` değiştirici dönüş değeri bir başvuru değişkeni başvuru yapmak için yerel değişken bildirimi için:

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

Şimdi, ikinci `WriteLine` yukarıdaki örnekte deyimi şeyler değerini yazdırır `24`, Matristeki depolama değiştirilmiş olduğunu gösteren. Yerel değişken ile bildirilen `ref` değiştiricisi ve alacağınız bir `ref` döndürür. Başlatması gerekir bir `ref` değişkeni bildirildiğinde, bildirim ve başlatma bölünemiyor.

C# dili kötüye kullanmasının korumak üç kuralları sahip `ref` yerel değerleri ve Dönüşleri:

* Standart bir yöntem dönüş değerine atanamaz bir `ref` yerel değişken.
    - Aşağıdaki gibi ifadeler izin vermiyor `ref int i = sequence.Count();`
* Döndüremezsiniz bir `ref` ömürlerinin yönteminin yürütülmesi genişletmiyoruz bir değişkene.
    - Yerel bir değişken veya benzer bir kapsama sahip bir değişken başvuru döndüremez anlamına gelir.
* `ref` yerel değerleri ve dönüşleri zaman uyumsuz yöntemlerle kullanılamaz.
    - Derleyici, zaman uyumsuz yöntem döndürüldüğünde başvurulan değişken son değerine ayarlandı olmadığını bilemezsiniz.

Ref yerel ayarlar ve ref değerleri kopyalama ya da birden çok kez başvurusunu kaldırma işlemlerini gerçekleştirme önleyerek daha verimlidir etkinleştir algoritmaları döndürür.

Ekleme `ref` için dönüş değeri bir [kaynağı uyumlu değişiklik](version-update-considerations.md#source-compatible-changes). Var olan kod derlenir, ancak başvuru dönüş değeri atandığında kopyalanır. Çağıranlar, depolama alanı için dönüş değeri için güncelleştirilmesi gerekir bir `ref` dönüş başvuru olarak saklamak için yerel değişken.

Daha fazla bilgi için [ref anahtar sözcüğü](../language-reference/keywords/ref.md) makalesi.

## <a name="local-functions"></a>Yerel İşlevler

Sınıflar için birçok tasarım tek bir konumdan Aranan yöntemleri kapsar. Bu ek özel yöntemleri her yöntem, küçük ve odaklı tutun. Ancak, bunlar, bir sınıf ilk kez okurken anlamak zorlaştırabilir. Tek arama konumu bağlamı dışında bu yöntemlerin anlaşılması gerekir.

Bu tasarım için *yerel işlevler* , başka bir yöntem bağlamı içinde yöntemleri bildirmek etkinleştirin. Bu bağlamda olduğu bildirilen yerel yöntemi yalnızca çağrılır, görmek için sınıf okuyucular için kolaylaştırır.

Yerel işlevler için iki yaygın kullanım örnekleri vardır: Genel yineleyici yöntemleri ve genel zaman uyumsuz yöntemler. Her iki yöntem tür hataları programcılar beklenebilir daha sonra rapor kod oluşturur. Yineleyici metotları olması durumunda, yalnızca özel durumların gözlemlenen döndürülen dizi numaralandırır kod çağırırken. Söz konusu olduğunda zaman uyumsuz yöntemler, özel durumların yalnızca zaman uyulması gereken döndürülen `Task` beklenir.

Bir yineleyici yöntem ile başlayalım:

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

Yineleyici yöntem yanlış çağıran kodu aşağıdaki inceleyin:

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

Özel durum oluşan `resultSet` , ne zaman yinelendiğinde değil `resultSet` oluşturulur.
Çoğu geliştirici, kapsanan bu örnekte, hızlı bir şekilde bu sorunu tanılamak. Ancak, büyük kod tabanlarında, sonuç listesini numaralandıran kod olarak yakın bir yineleyici genellikle oluşturan kodu değil. Tüm bağımsız değişkenler genel yöntem doğrular ve özel bir yöntem sabit listesi oluşturur. böylece kodu yeniden düzenleyebilirsiniz:

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

İşlenmiş bu sürümü, özel durumları oluşturmaz hemen genel yöntem yineleyici yöntemini; olmadığı için yalnızca özel yöntemi kullanan `yield return` söz dizimi. Ancak, bu yeniden düzenleme ile olası sorunları vardır. Aksi takdirde tüm bağımsız değişken doğrulama atlandığından ortak arabirim yöntemi yalnızca özel yöntemi çağrılmalıdır.
Okuyucular sınıfının gerekir Bul bu olgu sınıfın tamamı okuyarak ve diğer tüm başvurular aranıyor `alphabetSubsetImplementation` yöntemi.

Bildirerek bu tasarım hedefi daha temiz yapabilirsiniz `alphabetSubsetImplementation` Genel API yöntemi içinde yerel bir işlev olarak:

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

Yukarıdaki sürüm Temizle yerel yöntemi başvurulan yalnızca dış yöntem bağlamında kolaylaştırır. Yerel işlevleri için kurallar ayrıca bir geliştirici yanlışlıkla sınıfında başka bir konumdan yerel işlev çağrısı veya bağımsız değişken doğrulama atlama emin emin olun.

Aynı yöntem ile işe `async` zaman uyumsuz işler başlamadan önce bağımsız değişken doğrulama doğan özel durumlar emin olmak için yöntemleri:

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> Yerel işlevleri tarafından desteklenen tasarımları bazılarını da kullanarak sağlayabilirsiniz *lambda ifadeleri*. Bu ilgi olabilir [farklar hakkında daha fazla bilgi](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>Daha fazla ifade gövdeli üyeler

C# 6 sunulan [ifade gövdeli üyeler](csharp-6.md#expression-bodied-function-members) üye işlevleri ve salt okunur özellikler için. C# 7.0 ifadeleri olarak uygulanabilir izin verilen üyeleri genişletir. C# 7. 0 ', uygulayabileceğiniz *oluşturucular*, *sonlandırıcılar*, ve `get` ve `set` bulunan erişimciler *özellikleri* ve *dizin oluşturucular* . Aşağıdaki kod her örneklerini gösterir:

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Bu örnek bir sonlandırıcıya gerek yoktur, ancak sözdizimini göstermek için gösterilir. Yönetilmeyen kaynakları serbest bırakmak gerekli olmadıkça, sınıfta bir sonlandırıcı uygulamamalıdır. Kullanmayı da düşünmelisiniz <xref:System.Runtime.InteropServices.SafeHandle> yönetilmeyen kaynakları doğrudan yönetmek yerine sınıfı.

İfade gövdeli üyeler için bu yeni konumlar için önemli bir kilometre temsil C# dil: Bu özellikler, açık kaynaklı çalışma topluluk üyeleri tarafından uygulanan [Roslyn](https://github.com/dotnet/Roslyn) proje.

Bir ifade bodied üyesine bir yöntemi değiştirme bir [ikili uyumlu değişiklik](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Throw ifadeleri

C# ' ta, `throw` her zaman bir deyim olmuştur. Çünkü `throw` olan C# yapılarını değil kullanabileceğiniz, bir ifade değil bir ifade, var olan. Bunlar, koşullu ifadeleri ve null birleşim ifadelerini bazı lambda ifadeleri dahil. İfade gövdeli üyeler eklenmesi için daha fazla konum ekler burada `throw` ifadeleri yararlı olacaktır. Bu yapıları hiçbirini yazabilmesi amacıyla da, C# 7.0 tanıtır *throw ifadelerini*.

Her zaman için kullandığınız sözdizimi aynıdır `throw` deyimleri. Bunları yeni konumlara gibi koşullu ifadede yerleştirebilirsiniz artık tek fark,.:

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

Bu, throw ifadelerini başlatma ifadeleri kullanarak etkinleştirir özellikleri:

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

Daha önce bu başlatmalar Oluşturucu gövdesinde throw deyimleri ile bir oluşturucu içinde olması gerekir:


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> Önceki yapıları her ikisi de, özel bir nesnenin yapımı sırasında durum oluşturulmasına neden olur. Bu genellikle kurtarma yapmak zordur.
> Bu nedenle, yapım sırasında özel durumlar oluşturan tasarımları önerilmez.

## <a name="generalized-async-return-types"></a>Genelleştirilmiş bir zaman uyumsuz dönüş türleri

Döndüren bir `Task` zaman uyumsuz yöntemler bir nesneden performans sorunlarını Belirli yollardaki tanıtmak. `Task` bir başvuru türü olduğundan, onu kullanarak bir nesne ayırma anlamına gelir. Burada bir yöntem ile bildirilmiş durumlarda `async` değiştiricisi önbelleğe alınmış bir sonuç döndürür ya da zaman uyumlu olarak tamamlanan, kodun önemli bölümleri performans ciddi zaman maliyetine ek ayırmaları hale gelebilir. Bu ayırmalar sıkı döngüleri oluşursa çok pahalı hale gelebilir.

Yeni dil özelliği zaman uyumsuz yöntemler diğer tür ek olarak döndürebilir anlamına gelir. `Task`, `Task<T>` ve `void`. Döndürülen tür yine de zaman uyumsuz desen karşılaması gerekir yani bir `GetAwaiter` yöntemi erişilebilir olmalıdır. Somut bir örnek olarak `ValueTask` yapmak için .NET framework türü eklendi bu yeni dil özelliğini kullanın: 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> NuGet paketini eklemeniz [ `System.Threading.Tasks.Extensions` ](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) kullanmak için <xref:System.Threading.Tasks.ValueTask%601> türü.

Basit bir iyileştirme kullanmak olabilir `ValueTask` yerde nerede `Task` önce kullanılması. Ancak, ek iyileştirmeler el ile gerçekleştirmek istiyorsanız, zaman uyumsuz iş sonuçlarını önbelleğe alma ve sonraki çağrılar sonuç yeniden. `ValueTask` Yapı sahip bir oluşturucuyla bir `Task` parametresi, oluşturabilirsiniz böylece bir `ValueTask` herhangi bir mevcut zaman uyumsuz yöntem dönüş değerinin:

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]

Tüm performans önerileri ile iki sürüm de büyük yapmadan önce Kıyaslama şekilde ölçek kodunuza değiştirir.

Dönüş değeri hedefinin olduğunda bir `await` API'den değiştirme deyimi, bir <xref:System.Threading.Tasks.Task%601> için bir <xref:System.Threading.Tasks.ValueTask%601> olduğu bir [kaynağı uyumlu değişiklik](version-update-considerations.md#source-compatible-changes). Genel olarak, değiştirerek `ValueTask` değil.

## <a name="numeric-literal-syntax-improvements"></a>Sayısal sabit değer sözdizimi geliştirmeleri

Sayısal sabitlere misreading kodu ilk kez okurken anlaşılması zor yapabilirsiniz. Bu sayı, bit maskeleri veya diğer sembolik olarak kullanıldığında, bu genellikle oluşur. sayısal değerler yerine. C# 7.0 en okunabilir bir biçimde için kullanım sayıları yazma daha kolay hale getirmek için iki yeni özellikler içerir: *ikili sabit dizeler*, ve *rakam ayırıcıları*.

İçin bu kez, bit maskeleri oluştururken ya da birkaç ikili gösterimini her ikili dosyada bu sayıyı yazma en okunabilir bir kod sağlar:

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

`0b` Sayı ikili sayı olarak yazılır sabiti başında gösterir.

Genellikle bit düzenleri sunarak daha kolay olacak şekilde ikili sayı çok uzun alabilirsiniz `_` basamak ayırıcı olarak:

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

Basamak ayırıcı sabiti her yerde görünebilir. Taban 10 numaraları için bir binler basamağı kullanmak yaygın olacaktır ayırıcı:

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

Basamak ayırıcı ile birlikte kullanılabilir `decimal`, `float` ve `double` türleri de:

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

Birlikte ele alındığında Sayısal sabitler ile çok daha fazla okunabilirliği bildirebilirsiniz.
