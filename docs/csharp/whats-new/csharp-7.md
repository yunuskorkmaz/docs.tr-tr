---
title: "C# 7 - C# Kılavuzu yenilikler nelerdir?"
description: "C# dili gelecek sürümünde 7 gelen yeni özelliklere genel bakış alın."
keywords: "Yenilikler C#, .NET, .NET Core, en son özellikleri"
author: BillWagner
ms.author: wiwagn
ms.date: 12/21/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 3f3598fce5abeb67b772f51ed6f93e6ada4c92d0
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2017
---
# <a name="whats-new-in-c-7"></a>C# 7'deki yenilikler

C# 7 C# dili için birtakım yeni özellikleri ekler:
* [`out`değişkenleri](#out-variables)
    - Bildirebilirsiniz `out` bunlar burada kullanılır yöntemi bağımsız değişken olarak satır içi değerleri.
* [Diziler](#tuples)
    - Birden çok genel alanlar içeren basit, adlandırılmamış türleri oluşturabilirsiniz. Bu tür semantiği derleyicileri ve IDE araçları anlayın.
* [Atar](#discards)
    - İptali atanan değer hakkında önemli değil atamalarını kullanılan geçici, yalnızca yazma değişkenlerdir. Tanımlama grupları ve kullanıcı tanımlı türler deconstructing zaman yanı sıra yöntemleri çağrılırken özellikle yararlı oldukları `out` parametreleri.
* [Desen eşleştirme](#pattern-matching)
    - Rastgele türler ve bu türlerde üyelerinin değerlerine dayalı dallandırma mantığını oluşturabilirsiniz.
* [`ref`Yerel öğeler ve döndürür](#ref-locals-and-returns)
    - Yöntem bağımsız değişkenleri ve yerel değişkenler diğer depolama başvurular olabilir.
* [Yerel İşlevler](#local-functions)
    - Kendi kapsam ve görünürlük sınırlamak için diğer işlevleri iç işlevleri iç içe.
* [Daha fazla ifade bodied üyeleri](#more-expression-bodied-members)
    - İfadeler kullanarak yazılabilir üyelerin listesi haline geldi.
* [`throw`İfadeler](#throw-expressions)
    - Özel durumlar, daha önce olduğundan verilmez kod yapılardan throw `throw` bir ifadesi. 
* [Genelleştirilmiş zaman uyumsuz dönüş türleri](#generalized-async-return-types)
    - Yöntemleri bildirilen ile `async` değiştiricisi ek olarak diğer türleri dönebilirsiniz `Task` ve `Task<T>`.
* [Değişmez sayısal sözdizimi geliştirmeleri](#numeric-literal-syntax-improvements)
    - Yeni belirteçleri Sayısal sabitler için okunabilirliğini artırmak.

Bu konunun geri kalanında özelliklerin her biri açıklanmaktadır. Her bir özellik için bunun arkasındaki mantığı öğreneceksiniz. Sözdizimi öğreneceksiniz. Burada yeni özelliği kullanarak, bir uygulama geliştiricisi olarak daha verimli hale getirir bazı örnek senaryolar görürsünüz. 

## <a name="out-variables"></a>`out`değişkenleri

Destekleyen mevcut sözdizimi `out` parametreleri bu sürümde geliştirilmiştir.  

Daha önce out değişkeni ve onun başlatma iki farklı deyimleri içine bildirimi ayrı gerekir:

[!code-csharp[OutVariableOldStyle](../../../samples/snippets/csharp/new-in-7/program.cs#03_OutVariableOldStyle "classic out variable declaration")]

Şimdi bildirebilir `out` ayrı bildirimi deyimi yazma yerine bir yöntem çağrısı bağımsız değişken listesinde değişkenleri:

[!code-csharp[OutVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#01_OutVariableDeclarations "Out variable declarations")]

Türünü belirtmek isteyebilirsiniz `out` anlaşılması için değişken yukarıda gösterildiği gibi. Ancak, dil türü örtük olarak belirlenmiş yerel değişken kullanarak destekler:

[!code-csharp[OutVarVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#02_OutVarVariableDeclarations "Implicitly typed Out variable")]

* Kod okumak daha kolay olur. 
    - Olmayan başka bir satıra yukarıdaki kullandığınız out değişken bildirin.
* Bir başlangıç değeri atamak gerek yoktur.
    - Bildirme tarafından `out` kendisine atanmış önce bir yöntem çağrısı kullanıldığı değişken, yanlışlıkla kullanamazsınız.

Bu özellik için en yaygın kullanımı olacaktır `Try` düzeni. Bu modelinde bir yöntem bir `bool` başarı veya başarısızlık belirten ve bir `out` yöntem başarılı olursa, sonuç sağlayan değişkeni.

Kullanırken `out` değişken bildirimi bildirilen değişkeni "sızdırıyor" IF dış kapsamı içine deyimi. Bu değişkeni sonradan kullanmanıza olanak sağlar:

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
> NuGet paketini eklemeniz gerekir [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) türleri dahil etmeyin platformlarda kullanmak için.
>
> Bu framework teslim türlerine dayanan diğer dil özellikleri benzer. Örnek dahil `async` ve `await` güvenmek `INotifyCompletion` arabirimi ve güvenmek LINQ `IEnumerable<T>`. Ancak, daha fazla platform bağımsız .NET olma gibi teslim mekanizması değiştiriyor. .NET Framework her zaman aynı tempoyla dil derleyici olarak yükleyeceğiniz değil. Yeni dil özellikleri yeni türlerinde kullanır, dil özellikleri sevk ettiğinizde bu türlerde NuGet paketleri olarak kullanılabilir. Bu yeni tür .NET standart API'sine eklenir ve framework'ün bir parçası olarak teslim olarak NuGet paketi gereksinimi kaldırılacak.

C# sınıflar ve tasarım hedefi açıklamak için kullanılan yapılar için zengin bir sözdizimi sağlar. Ancak bazen bu zengin sözdizimi en az avantajı ile ek iş gerektirir. Birden fazla veri öğesi içeren basit bir yapıya gereksinim yöntemleri genellikle yazabilir. Bu senaryoları desteklemek için *diziler* C# eklendi. Diziler veri üyeleri göstermek için birden çok alan içeren basit veri yapılarını ' dir.
Alanları doğrulanmazsa ve kendi yöntemleri tanımlanamıyor

> [!NOTE]
> Diziler C# 7 önce kullanılabilir, ancak verimsiz ve hiçbir dil desteği vardı.
> Bu başlığın öğeleri yalnızca olarak başvurulan geliyordu `Item1`, `Item2` ve benzeri. C# 7 yeni, daha verimli tanımlama grubu türlerini kullanarak bir tanımlama grubu alanlarının anlamsal adlarını etkinleştirir diziler için dil desteği sunar.

Her üye bir değere atayarak bir tanımlama grubu oluşturabilirsiniz:

[!code-csharp[UnnamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#04_UnnamedTuple "Unnamed tuple")]

Atama üyeleri olan bir tanımlama grubu oluşturur `Item1` ve `Item2`, aynı şekilde kullanabileceğiniz <xref:System.Tuple> her bir tanımlama grubu üyeleri anlamsal adları sağlayan bir tanımlama grubu oluşturmak için söz dizimi değiştirebilirsiniz:

[!code-csharp[NamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#05_NamedTuple "Named tuple")]

`namedLetters` Tanımlama grubu olarak adlandırılan alanları içeren `Alpha` ve `Beta`. Bu adları yalnızca derleme zamanında mevcut ve örneğin, çalışma zamanında yansıma kullanarak tanımlama grubu incelerken korunmaz.

Bir tanımlama grubu ataması alanların adlarını atama sağ tarafta belirtebilirsiniz:

[!code-csharp[ImplicitNamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#06_ImplicitNamedTuple "Implicitly named tuple")]

Ad alanları için iki sol ve sağ tarafında atama belirtebilirsiniz:

[!code-csharp[NamedTupleConflict](../../../samples/snippets/csharp/new-in-7/program.cs#07_NamedTupleConflict "Named tuple conflict")]

Yukarıdaki satır bir uyarı oluşturur `CS8123`, bunu söyleyen adları atama sağ tarafındaki `Alpha` ve `Beta` sol taraftaki adlarıyla çakıştığından göz ardı edilir `First` ve `Second`.

Yukarıdaki örnekler diziler bildirmek için temel söz dizimini gösterir. Diziler için dönüş türü olarak en yararlı `private` ve `internal` yöntemleri. Tanımlama grupları birden çok ayrık değer döndürmek bu yöntemleri için basit bir sözdizimi sağlar: yazma çalışmalarınızı kaydedin bir `class` veya `struct` döndürülen türü tanımlar. Yeni bir tür oluşturmak için gerek yoktur.

Bir tanımlama grubu oluşturmak daha etkili ve daha verimli olur.
Birden fazla değer taşıyan bir veri yapısı tanımlamak için daha basit ve basit bir sözdizimi şeklindedir. Aşağıdaki örnek yöntemi tamsayılar dizisinde bulunan minimum ve maksimum değerleri döndürür:

[!code-csharp[TupleReturningMethod](../../../samples/snippets/csharp/new-in-7/program.cs#08_TupleReturningMethod "Tuple returning method")]

Bu şekilde tanımlama gruplarını kullanma birkaç avantaj sunar:

* Yazma işlemlerini kaydettiğiniz bir `class` veya `struct` döndürülen türü tanımlar. 
* Yeni türü oluşturmak gerekmez.
* Dil geliştirmeleri kaldırır çağırmak için gereken < xref:System.Tuple.Create``1(``0) > yöntemleri.

Yöntem bildirimi döndürülen tanımlama grubu alanlarının adları sağlar. Yöntemini çağırdığınızda, dönüş değeri olan alanlar bir tanımlama grubu olan `Max` ve `Min`:

[!code-csharp[CallingTupleMethod](../../../samples/snippets/csharp/new-in-7/program.cs#09_CallingTupleMethod "Calling a tuple returning method")]

Bir yönteminden döndürülen bir tanımlama grubu üyeleri gitmeniz istediğinizde zamanlar olabilir.  Tanımlama grubundaki değerlerin her biri için ayrı değişkenlerini bildirerek yapabilirsiniz. Bu adlı *deconstructing* tanımlama:

[!code-csharp[CallingWithDeconstructor](../../../samples/snippets/csharp/new-in-7/program.cs#10_CallingWithDeconstructor "Deconstructing a tuple")]

<!-- Add wildcards here, if they are in C# 7
-->

.NET içinde herhangi bir türü için benzer bir deconstruction sağlar. Bu yazarak yapılır bir `Deconstruct` sınıf üyesi olarak yöntemi. Olduğunu `Deconstruct` yöntemi sağlayan bir dizi `out` özelliklerin her biri için ayıklamak istediğiniz bağımsız değişkenleri. Şunları göz önünde bulundurun `Point` ayıklar deconstructor yöntemi sağlayan sınıf `X` ve `Y` koordinatları:

[!code-csharp[PointWithDeconstruction](../../../samples/snippets/csharp/new-in-7/point.cs#11_PointWithDeconstruction "Point with deconstruction method")]
 
Bir tanımlama grubu atayarak tek tek alanların ayıklayabilirsiniz bir `Point`:

[!code-csharp[DeconstructPoint](../../../samples/snippets/csharp/new-in-7/program.cs#12_DeconstructPoint "Deconstruct a point")]

Tanımlanmış adlarıyla bağlı olmayan `Deconstruct` yöntemi. Extract değişkenleri atama bir parçası olarak yeniden adlandırabilirsiniz:  

[!code-csharp[DeconstructNames](../../../samples/snippets/csharp/new-in-7/program.cs#13_DeconstructNames "Deconstruct with new names")]

Diziler hakkında daha fazla giriş derinliği öğrenebilirsiniz [diziler konu](../tuples.md).

## <a name="discards"></a>Atar

Olduğunda, genellikle bir tanımlama grubu deconstructing veya sahip bir yöntemi çağırma `out` parametreleri hakkında önemli değil ve kullanmayı düşünmüyorsanız değeri bir değişkeni tanımlamak zorunda. C# için destek ekler *atar* bu senaryo işlemek için. Bir atma adı olan bir salt yazılır değişkendir `_` (alt çizgi karakteri); tüm tek değişkene atmak istiyorsanız değerleri atayabilirsiniz. Bir atma gibi atanmamış bir değişkenidir; atama deyimi dışında atma kod içinde kullanılamaz.

İptali aşağıdaki senaryolarda desteklenir:

* Tanımlama grupları ve kullanıcı tanımlı türler deconstructing olduğunda.

* Yöntemleri çağrılırken [çıkışı](../language-reference/keywords/out.md) parametreleri.

* İşlemi ile eşleşen bir düzende [olan](../language-reference/keywords/is.md) ve [geçiş](../language-reference/keywords/switch.md) deyimleri.

* Açıkça istediğinizde, bir tek başına tanımlayıcı olarak bir atma olarak atama değerini belirleyin.

Aşağıdaki örnek tanımlayan bir `QueryCityDataForYears` 6-bir şehir için bir veri iki farklı yıl içeren tanımlama grubu döndürür yöntemi. Örnekte yöntem çağrısı yalnızca yöntemi tarafından döndürülen iki doldurma değerleri ile ilgilidir ve böylece kalan değerler tanımlama grubu tanımlama grubu deconstructs zaman atar gibi davranır.

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Daha fazla bilgi için bkz: [atar](../discards.md).
 
## <a name="pattern-matching"></a>Desen eşleştirme

*Desen eşleştirme* yöntemi gönderme özellikleri bir nesne türünü dışında uygulamak olanak sağlayan bir özelliktir. Büyük olasılıkla zaten aşina olan bir nesne türüne göre yöntemi gönderme. Nesne yönelimli, sanal programlama ve geçersiz kılma yöntemleri yöntemi nesnenin türüne göre göndermeyi uygulamak için dili sözdizimi sağlar. Temel ve türetilmiş sınıflarının farklı uygulamaları sağlar. Böylece bir devralma hiyerarşisi aracılığıyla ilgili olmayan türleri ve veri öğeleri için benzer gönderme desenleri kolayca uygulayabilirsiniz desen eşleştirme ifadeleri bu kavramı genişletir. 

Desen eşleştirme destekler `is` ifadeleri ve `switch` ifadeler. Her bir nesne ve söz konusu nesne Aranan düzeni karşılayan varsa belirlemek üzere özelliklerini inceleme sağlar. Kullandığınız `when` düzeni için ek kurallarını belirtmek için anahtar sözcüğü.

### <a name="is-expression"></a>`is`ifade

`is` Düzeni ifade genişletir bilinen `is` bir nesne türünü ötesinde sorgu işleci.

Basit bir senaryoyla başlayalım. Desen eşleştirme ifadeleri kolay iş ile ilgisiz türleri algoritmaları nasıl oluşturduğunu gösteren bu senaryo için özellikleri ekleyeceğiz. Dökme dökümünü sayısı toplamını hesaplar bir yöntem ile başlayacağız:

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

Bazı dökümünü ile birden çok bölmek yapılan burada dökme dökümünü toplamını bulmanız gereken hızlı bir şekilde bulabilirsiniz (dökme çoğul bölmek'dir). Giriş dizisinin bir parçası, tek bir sayı yerine birden çok sonuç olabilir:

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

`is` Deseni ifadesi bu senaryoda oldukça iyi çalışır. Tür denetleme bir parçası olarak bir değişken başlatma yazma. Doğrulanmış çalışma zamanı türü yeni bir değişken oluşturur.

Bu senaryolar genişletme tutmak gibi daha fazla yapı bulabilirsiniz `if` ve `else if` deyimleri. Yönetilmeleri olduktan sonra büyük olasılıkla geçiş yapmak istediğiniz `switch` ifadeleri desen.

### <a name="switch-statement-updates"></a>`switch`deyim

*İfade ile eşleşen* sahip dayalı bir bilinen sözdizimini `switch` deyimi C# dili zaten parçası. Şimdi yeni durumları eklemeden önce bir eşleşme ifadesi kullanmak için var olan kodu çevir: 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

Eşleşme ifadeleri değerinden biraz farklı bir sözdizimi sahip `is` ifadeleri, burada bildirdiğiniz türü ve değişken başındaki `case` ifade.

Eşleşme ifadeleri sabitleri de destekler. Basit durumlar Finansman tarafından bu zamandan tasarruf edebilirsiniz:

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

Yukarıdaki kod durumlarda ekler `0` bir özel durum olarak `int`, ve `null` herhangi bir giriş olduğunda bir özel durum olarak. Bu anahtar düzeni ifadelerde yeni bir önemli özellik gösterir: sırasını `case` ifadeleri şimdi önemlidir. `0` Durumda önce genel görünür `int` durumda. Aksi durumda, eşleştirmek için ilk desen olacak `int` durumda değer olsa bile, `0`. Bir sonraki servis talebi zaten işlenmiş şekilde eşleşme ifadeleri yanlışlıkla sipariş, derleyici, bayrak ve bir hata oluşturur.

Bu aynı davranışı boş bir giriş sırası için özel durum sağlar.
Görebilirsiniz bu durum bir `IEnumerable` öğeleri içeren öğe genel önce görünmelidir `IEnumerable` durumda.

Bu sürüm ayrıca eklenmiş bir `default` durumda. `default` Durumu her zaman değerlendirildiği son, sipariş bağımsız olarak kaynak olarak görünür. Bu nedenle, yerleştirilecek kuraldır `default` servis talebi son.

Son olarak, bir son ekleyelim `case` dökme yeni stili için. Bazı oyunlar yüzdebirlik bölmek numaraları büyük aralıklarına göstermek için kullanın. 

> [!NOTE]
> İki 10 taraflı yüzdebirlik bölmek 0 ile 99 arasındaki tüm sayıları temsil edebilir. Bir özel etiketli kenara sahip `00`, `10`, `20`,... `90`. Diğer özel etiketli kenarlara sahip `0`, `1`, `2`,... `9`. İki dökme değerlerin birlikte ekleyin ve her sayı 0 ile 99 arasında alabilirsiniz.

Bu tür bir dökme koleksiyonunuza eklemek için öncelikle yüzdelik bölmek temsil etmek için bir tür tanımlayın. `TensDigit` Özellik değerleri depolar `0`, `10`, `20`, en fazla `90`:

[!code-csharp[18_PercentileDice](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDice "Percentile Die type")]

Ardından, ekleyin bir `case` yeni türü için ifade ile eşleşen:

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

Desen eşleştirme ifadeleri yeni sözdizimi, nesnenin türü veya kısa ve öz sözdizimini kullanarak diğer özellikleri göre gönderme algoritmaları oluşturmak kolaylaştırır. Desen eşleştirme ifadeleri tarafından devralma ilişkisiz veri türleri üzerinde bu yapıları etkinleştirin.

Desen ayrılmış konudaki eşleştirme hakkında daha fazla bilgiyi [desen eşleştirme C# dilinde](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Ref Yereller ve döndürür

Bu özelliği kullanmak ve başka bir yerde tanımlanan değişkenler başvurular algoritmaları sağlar. Örneğin, büyük matrisleri ile çalışma ve belirli özelliklere sahip tek bir konum bulma. Bir yöntem tek bir konum için iki dizinlerini matrisinde döndürür:

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

Bu kod birçok sorunları vardır. İlk olarak bir tanımlama grubu döndüren bir ortak yöntem olur. Bu dil destekler, ancak kullanıcı tanımlı türler (sınıfları veya yapılar) için ortak API'ler tercih edilir.

İkinci olarak, bu yöntem dizinlerini Matristeki öğesine döndürüyor.
Bu matris dereference ve tek bir öğe değiştirmek için bu dizinlerini kullanan kod yazmaya arayanlar yol açar:

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

Bunun yerine döndüren bir yöntem yazmak istediğiniz bir *başvuru* değiştirmek istediğiniz matrisi öğesine. Yalnızca güvenli olmayan kod kullanarak ve bir işaretçi döndüren bunu bir `int` önceki sürümlerinde.

Şimdi değişikliklerin ref yerel özellik göstermek ve dahili depolama başvuru döndüren bir yöntem oluşturma göstermek için bir dizi yol.
Yol boyunca ref dönüş ve onu kötüye yanlışlıkla korur ref yerel özellik kurallarına öğreneceksiniz.

Başlangıç değiştirerek `Find` onun döndürecek şekilde yöntem bildirimi bir `ref int` yerine bir tanımlama grubu. Ardından, iki dizinlerini yerine Matristeki depolanan değeri döndürecek şekilde return deyimi değiştirin:

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

Ne zaman bildirdiğiniz yöntemi döndürür bir `ref` değişken, ayrıca eklemelisiniz `ref` anahtar sözcüğü her return deyimi için. Return başvuruya göre gösterir ve yöntem başvuruya göre döndürür kodu daha sonra okuma yardımcı geliştiriciler unutmayın:

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

Yöntem matrisinde tamsayı değeri bir başvuru döndürür, burada adlı değiştirmeniz gerekir.  `var` Bildirimi anlamına `valItem` artık bir `int` bir tanımlama grubu yerine:

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

İkinci `WriteLine` deyimi yukarıdaki örnekte yazdırır değerini `42`değil `24`. Değişkeni `valItem` olan bir `int`değil bir `ref int`. `var` Anahtar sözcüğü türünü belirtmek derleyici sağlar, ancak örtük olarak eklemeyecek `ref` değiştiricisi. Bunun yerine, değer tarafından başvurulan `ref return` olan *kopyalanan* değişkenine atama sol taraftaki. Değişken değil bir `ref` yerel.

İstediğiniz sonucu alabilmek için eklemeniz gerekir `ref` değiştiricisi dönüş değeri bir başvuru değişkeni bir başvuru yapmak için yerel değişken bildirimi için:

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

Şimdi, ikinci `WriteLine` deyimi yukarıdaki örnekte değerini yazdıracak `24`, Matristeki depolama değiştirildiğini belirten. Yerel değişken ile bildirilen `ref` değiştirici ve alacak bir `ref` döndürür. Başlatması gerekir bir `ref` değişkeni bildirildiğinde, bildirim ve başlatma bölünemez.

C# dili kötüye kullanmasının korumak diğer üç kurallarına sahiptir `ref` Yereller ve döndürür:

* Bir standart yönteminin dönüş değeri atayamazsınız bir `ref` yerel değişken.
    - Aşağıdaki gibi ifadeler izin vermez`ref int i = sequence.Count();`
* Geri dönemezsiniz bir `ref` bir değişkene, yaşam süresi yönteminin yürütülmesi genişletmek değil.
    - Yerel bir değişken ya da benzer bir kapsama sahip bir değişken başvuru döndüremez anlamına gelir.
* `ref`Yerel öğeler ve döndürür zaman uyumsuz yöntemleri ile kullanılamaz.
    - Derleyici, zaman uyumsuz yöntem döndüğünde başvurulan değişken son değerine ayarlanmış olmadığını bilemezsiniz.

Ref Yereller ve ref değerleri kopyalama veya birden çok kez bilgileri başvuru kaldırma işlemlerini gerçekleştirme kaçınarak daha verimlidir etkinleştir algoritmaları döndürür. 

## <a name="local-functions"></a>Yerel İşlevler

Çoğu tasarımları sınıfları için yalnızca tek bir konumdan adlı yöntemleri içerir. Bu ek özel yöntemleri, küçük ve odaklanmış her yöntem tutun. Ancak, bunlar, ilk kez okurken bir sınıf anlaşılması zor yapabilirsiniz. Bu yöntemler tek arama konumu bağlamı dışında anlaşılması gerekir.

Bu tasarımları için *yerel işlevler* yöntemlerin başka bir yöntem bağlamı içinde bildirme olanak sağlar. Bu bağlamda olmasından bildirilen yerel yöntemi yalnızca çağrılır olduğunu görmek için sınıf okuyucular için kolaylaştırır.

İki çok ortak kullanım durumları için yerel işlevler vardır: ortak Yineleyici ve ortak zaman uyumsuz yöntemleri. Her iki tür yöntemi hataları programcıları bekleyebilirsiniz daha sonra rapor kodu oluşturur. Yineleyici metotları söz konusu olduğunda, yalnızca özel durumlar gözlenen döndürülen dizi numaralandırır kod çağrılırken. Zaman uyumsuz yöntemleri söz konusu olduğunda, tüm özel durumlar yalnızca zaman gözlemlenen döndürülen `Task` beklemenin.

İterator yöntemi ile başlayalım:

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

İterator yöntemi yanlış çağıran aşağıdaki kodu inceleyin:

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

Ne zaman özel durum `resultSet` , ne zaman yinelendiğinde değil `resultSet` oluşturulur.
Çoğu geliştirici, içerilen bu örnekte, hızlı bir şekilde bu sorunu tanılamak. Ancak, daha büyük olarak kullanılabilecek kod temeli, sonuç numaralandırır kodu gibi yakın genellikle yineleyici oluşturan kodu değil. Böylece tüm bağımsız değişkenler genel yöntem doğrular ve özel bir yöntem numaralandırma oluşturur kodu yeniden düzenleme:

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

Bu işlenmiş sürüm özel durum atar hemen genel yöntem bir yineleyici yöntemi; olmadığından yalnızca bir özel yöntem `yield return` sözdizimi. Ancak, bu yeniden düzenleme olası sorunları vardır. Aksi takdirde tüm bağımsız değişkeni doğrulama atlandığından ortak arabirim yöntemi, yalnızca özel yöntemi çağrılmalıdır.
Sınıfın okuyucuları gerekir Bul olgunun tüm sınıf okuma ve başka bir başvuru için arama yaparak `alphabetSubsetImplementation` yöntemi.

Bu tasarım hedefi daha temizleyin bildirerek yapabileceğiniz `alphabetSubsetImplementation` ortak API yöntemi içinde yerel bir işlev olarak:

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

Yukarıdaki sürüm temizleyin yerel yöntemi başvurulan yalnızca dış yöntem bağlamında kolaylaştırır. Yerel işlevler için kuralları ayrıca Geliştirici olamaz yanlışlıkla sınıfında başka bir konumdan yerel işlevini çağırın ve bağımsız değişkeni Doğrulamayı atla emin olun.

İle aynı tekniği işe `async` yöntemleri zaman uyumsuz iş başlamadan önce bağımsız değişkeni doğrulama dışında doğan özel durumlar emin olun:

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> Yerel işlevler tarafından desteklenen tasarımları bazıları da kullanarak bunu sağlayabilirsiniz *lambda ifadeleri*. Bu ilgi yapabilirsiniz [farklar hakkında daha fazlasını okuyun](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>Daha fazla ifade bodied üyeleri

C# 6 sunulan [ifade bodied üyeleri](csharp-6.md#expression-bodied-function-members) üye işlevleri ve salt okunur özellikler. C# 7 ifadeleri olarak uygulanabilir izin verilen üyeleri genişletir. C# 7'de, uygulayabileceğiniz *oluşturucular*, *sonlandırıcılar*, ve `get` ve `set` erişimciler üzerinde *özellikleri* ve *dizin oluşturucular* . Aşağıdaki kod örnekleri her gösterir:

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Bu örnek bir sonlandırıcı gerekmez, ancak sözdizimini göstermek için gösterilir. Yönetilmeyen kaynakları serbest bırakmak gerekli olmadıkça bir sonlandırıcı sınıfınızda uygulamalıdır değil. Kullanmayı düşünmelisiniz <xref:System.Runtime.InteropServices.SafeHandle> yönetilmeyen kaynakları doğrudan yönetmek yerine sınıfı.

Bu yeni konumlar ifade bodied üyeleri için C# dili için önemli bir kilometre taşını temsil eder: Bu özellikler üzerinde açık kaynak çalışma topluluk üyeleri tarafından uygulanan [Roslyn](https://github.com/dotnet/Roslyn) projesi.

## <a name="throw-expressions"></a>Throw deyimleri

C# ' ta, `throw` her zaman bir deyim olmuştur. Çünkü `throw` bir, olmayan bir ifade, var olan C# yapılarını burada kullandığınızda, bir ifadedir. Bunlar, koşullu ifadeleri, null birleştirmesi ifadeleri ve bazı lambda ifadeleri dahil. Daha fazla konumları ifade bodied üyelerinin eklenmesini ekler nerede `throw` ifadeleri yararlı olacaktır. Bu yapıları hiçbirini yazma böylece C# 7 tanıtır *ifadeleri throw*.

Her zaman için kullandığınız sözdizimi aynıdır `throw` deyimleri. Tek fark, bunları yeni konumlarda gibi bir koşullu ifade yerleştirebilirsiniz şimdi Bunun anlamı:

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

Throw deyimleri başlatma ifadelerinde kullanarak etkinleştirir özellikleri:

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

Daha önce bu başlatmaları Oluşturucusu gövdesinde throw deyimleri ile bir oluşturucuda olması gerekir:


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> Önceki yapıları her ikisinin bir nesne oluşturma sırasında durum için özel durumlar neden olur. Bu genellikle kurtarılır zordur.
> Bu nedenle, oluşturma sırasında özel durumlar oluşturma tasarımları önerilmez.

## <a name="generalized-async-return-types"></a>Genelleştirilmiş zaman uyumsuz dönüş türleri

Döndüren bir `Task` zaman uyumsuz yöntemleri bir nesneden performans sorunları belirli yollarda tanıtır. `Task`bir başvuru türü olduğundan, kullanmadan bir nesne ayırma anlamına gelir. Burada bir yöntem bildirilen ile durumlarda `async` değiştiricisi önbelleğe alınmış bir sonuç döndürür veya zaman uyumlu olarak tamamlar, fazladan ayırmaları önemli zaman Maliyet performans kritik kod bölümlerini hale gelebilir. Bu ayırmaları sıkı Döngülerde oluşursa çok yüksek maliyetli hale gelebilir.

Yeni dil zaman uyumsuz yöntemleri ek olarak diğer türleri döndürebilir özelliğin `Task`, `Task<T>` ve `void`. Döndürülen türü zaman uyumsuz desen karşılaması gerekir yani bir `GetAwaiter` yöntemi erişilebilir olmalıdır. Somut bir örnek olarak `ValueTask` türü yapmak için .NET framework eklendi bu yeni dil özelliğini kullanın: 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> NuGet paketini eklemeniz [ `System.Threading.Tasks.Extensions` ](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) kullanmak için <xref:System.Threading.Tasks.ValueTask%601> türü.

Basit bir iyileştirme kullanmak olabilir `ValueTask` yerlerde nerede `Task` önce kullanılacaktır. Ancak, ek iyileştirmeler el ile gerçekleştirmek istiyorsanız, zaman uyumsuz iş sonuçlarından önbelleğe ve sonraki çağrılar sonuç yeniden kullanabilirsiniz. `ValueTask` Yapısı bir oluşturucu sahip bir `Task` parametresi, oluşturabileceğiniz böylece bir `ValueTask` varolan herhangi bir zaman uyumsuz yöntemi dönüş değerinin:

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]
 
Tüm performans önerileri, her iki sürümünü de büyük yapmadan önce Kıyaslama şekilde ölçek kodunuzu değiştirir.

## <a name="numeric-literal-syntax-improvements"></a>Değişmez sayısal sözdizimi geliştirmeleri

Sayısal sabitleri misreading ilk kez okunurken kod anlaşılması zor yapabilirsiniz. Bu sayı bit maskesi veya diğer sembolik olarak kullanıldığında, bu genellikle oluşur. sayısal değerler yerine. C# 7 kullanım için en okunabilir şekilde numaraları yazmayı kolaylaştırmak için iki yeni özellikler içerir: *ikili değişmez değerleri*, ve *basamak ayırıcıları*.

Bu kez için bu sayıyı ikili yazma en okunabilir kod bit maskesi oluştururken veya bir sayı ikili gösterimidir her yapar:

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

`0b` Sayı ikili bir sayı olarak yazılır sabiti başında gösterir.

Genellikle sunarak bit desenleri görmek daha kolay olacak şekilde ikili sayılar çok uzun alabilirsiniz `_` basamak ayırıcı olarak:

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

Basamak ayırıcı sabitinde herhangi bir yerde görünebilir. Temel 10 numaraları için binlerce kullanmak için ortak olacaktır ayırıcı:

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

Basamak ayırıcı kullanılabilir `decimal`, `float` ve `double` de türleri:

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

Birlikte ele alındığında sayısal sabit ile çok daha fazla okunabilirliği bildirebilirsiniz.
