---
title: C# 7.0 - C# Kılavuzu yenilikler nelerdir?
description: Yeni özelliklere genel bakış sürümünü 7.0 almak C# dili.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 81d06d2e2079e04948ad5e93eefadb1bc11d855a
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654191"
---
# <a name="whats-new-in-c-70"></a>C# 7.0 yenilikleri

C# 7.0 C# dili için yeni özellikler ekler:
* [`out` Değişkenleri](#out-variables)
    - Bildirebilirsiniz `out` kullanıldıkları yöntemi için bağımsız değişkeni olarak satır içi değerleri.
* [Demetler](#tuples)
    - Birden çok ortak alanları içeren basit, adsız türleri oluşturabilirsiniz. Bu tür semantikleri, derleyiciler ve Araçlar IDE anlayın.
* [Atılanlar](#discards)
    - İptali atanan değer hakkında umursamaz atamalarını kullanılan geçici, salt yazılır değişkenlerdir. Diziler ve kullanıcı tanımlı türler Ayrıştırma sırasında yanı sıra ile yöntemleri çağrılırken en yararlı oldukları `out` parametreleri.
* [Desen Eşleştirme](#pattern-matching)
    - Rastgele türler ve bu türlerin üyelerinin değerlerini göre dallanma mantığı oluşturabilirsiniz.
* [`ref` yerel değerleri ve dönüşleri](#ref-locals-and-returns)
    - Diğer depolama başvuruları yöntemi yerel değişkenleri ve dönüş değerleri olabilir.
* [Yerel İşlevler](#local-functions)
    - İşlevler, kapsam ve görünürlük sınırlamak için diğer işlevler içinde iç içe yerleştirebilirsiniz.
* [Daha fazla ifade gövdeli üyeler](#more-expression-bodied-members)
    - İfadeleri kullanarak yazılabilir üye listesini geldi.
* [`throw` İfadeleri](#throw-expressions)
    - Daha önce olduğundan izin vermediği kod yapıları özel durumlar oluşturabilecek `throw` bir ifadesi. 
* [Genelleştirilmiş bir zaman uyumsuz dönüş türleri](#generalized-async-return-types)
    - Yöntemleri ile bildirilmiş `async` değiştiricisi, ek olarak diğer türleri döndürebilir `Task` ve `Task<T>`.
* [Sayısal sabit değer sözdizimi geliştirmeleri](#numeric-literal-syntax-improvements)
    - Yeni belirteç sayısal sabitlere okunabilirliği geliştirir.

Bu makalenin geri kalanında her özelliğine genel bakış sağlar. Her bir özellik için ardındaki mantık öğreneceksiniz. Söz dizimi öğreneceksiniz. Bu özelliklerin keşfedebilirsiniz bizim [etkileşimli incelenmesi](../tutorials/exploration/csharp-7.yml) bu özellikleri.

## <a name="out-variables"></a>`out` Değişkenleri

Destekleyen varolan sözdizimi `out` parametreleri bu sürümde geliştirildi. Artık bildirebilirsiniz `out` ayrı bildirim deyimindeki yazmak yerine bir yöntem çağrısının bağımsız değişken listesinde değişkenleri:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Türünü belirtmek isteyebilirsiniz `out` , anlaşılması için değişken yukarıda da gösterildiği gibi. Ancak bir türü örtük olarak belirlenmiş yerel değişken kullanarak dili destekler:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

* Kodu daha kolay. 
    - Out değişkeni da değil başka bir satırda yukarıdaki kullandığınız bildirdiğiniz.
* Bir başlangıç değeri atamanız gerekmez.
    - Bildirmek `out` bunu atanmadan önce değişken bir yöntem çağrısında kullanıldığı yanlışlıkla kullanamazsınız.

## <a name="tuples"></a>Demetler

C# sınıfları ve, tasarım amacı açıklamak için kullanılan yapıları için zengin bir söz dizimi sağlar. Ancak bazen zengin Bu sözdizimi en az avantajı ile ek iş gerektirir. Birden fazla veri öğesini içeren basit bir yapıya gereken yöntemler genellikle yazabilir. Bu senaryoları desteklemek için *diziler* C# için eklendi. Diziler veri üyelerini temsil etmek için birden fazla alan içeren basit veri yapılarıdır.
Alanlarını doğrulandı değildir ve kendi yöntem tanımlanamaz

> [!NOTE]
> Diziler C# 7.0 önce kullanılabilir, ancak verimsiz ve dil desteği yok vardı.
> Bu dizi öğeleri yalnızca olarak başvurulan geliyordu `Item1`, `Item2` ve benzeri. C# 7.0 alanlarını yeni ve daha verimli bir tanımlama grubu türleri kullanarak bir demet için anlamsal adları sağlayan diziler için dil desteği sunar.

Her üye için bir değer atamak, ve isteğe bağlı olarak her bir tanımlama grubu üyelerinin anlam adları sağlayarak bir tanımlama grubu oluşturabilirsiniz:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

`namedLetters` Tanımlama grubu olarak adlandırılan alanları içeren `Alpha` ve `Beta`. Bu adları, yalnızca derleme zamanında mevcut ve çalışma zamanında yansıma kullanarak demet incelerken örneğin korunmaz.

Bir tanımlama grubu atamasını alanların adlarını atamada sağ tarafta da belirtebilirsiniz:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Yöntemden döndürülen bir tanımlama grubu üyelerinin açmak istediğinizde zamanlar olabilir.  Dizideki değerlerin her biri için ayrı değişkenleri bildirerek bunu yapabilirsiniz. Bu paketi adlı *ayrıştırma* tanımlama grubu:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

. NET'te herhangi bir tür için benzer bir ayrıştırma de sağlayabilirsiniz. Yazdığınız bir `Deconstruct` yöntemi sınıfının bir üyesi olarak. Olduğunu `Deconstruct` yöntem kümesi sağlar `out` ayıklamak istediğiniz bağımsız değişkenleri özelliklerin her biri için. Bunu göz önünde bulundurun `Point` ayıklayan deconstructor yöntemi sağlar sınıfını `X` ve `Y` koordinatları:

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]
 
Tek tek alanları atayarak ayıklayabileceğiniz bir `Point` bir demet için:

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Diziler hakkında daha da ayrıntılı bilgi edinebilirsiniz [diziler makale](../tuples.md).

## <a name="discards"></a>Atar

Olduğunda, genellikle bir demet ayrıştırma veya bir yöntemi çağırmak `out` parametreleri hakkında umursamaz ve kullanmayı düşünmüyorsanız değeri bir değişken tanımlayın zorunda. C# için destek ekler *atar* bu senaryonun işlenmesi için. Bir atma adı olan bir salt yazılır değişkendir `_` (alt çizgi karakteri); tüm tek bir değişkene atmak düşündüğünüz değerleri atayabilirsiniz. Bir atma gibi atanmamış bir değişkenidir; atama ifadesi dışında atma kodda kullanılamaz.

Atar, aşağıdaki senaryolarda desteklenir:

* Tanımlama grubu veya kullanıcı tanımlı türler ayrıştırma olduğunda.
* Yöntemleri çağrılırken [kullanıma](../language-reference/keywords/out-parameter-modifier.md) parametreleri.
* İşlemle eşleşen desende [olduğu](../language-reference/keywords/is.md) ve [geçiş](../language-reference/keywords/switch.md) deyimleri.
* Açıkça istediğinizde bir tek başına tanımlayıcı olarak bir atma atamadan değerini belirleyin.

Aşağıdaki örnekte tanımlayan bir `QueryCityDataForYears` farklı iki yıllık bir şehir için bir veri içeren bir 6 bölütlü döndüren yöntem. Örnek yöntem çağrısında yöntem tarafından döndürülen iki popülasyon değerleri ile ilgilidir ve bu nedenle kalan değerler demet tanımlama grubu deconstructs olduğunda atar gibi davranır.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Daha fazla bilgi için [atar](../discards.md).

## <a name="pattern-matching"></a>Desen eşleştirme

*Desen eşleştirme* yöntem gönderimine dışındaki bir nesne türü özellikleri uygulamak izin veren bir özelliktir. Zaten bir nesne türüne göre yöntemi gönderme hakkında bilgi sahibi. Yöntemi, bir nesnenin türüne göre gönderme uygulamak için dili sözdizimi, nesne yönelimli programlama, sanal ve geçersiz kılma yöntemleri sağlar. Temel ve türetilmiş sınıfları farklı uygulamalar sağlayabilir. Desen eşleştirme ifadeleri bu kavramı genişletmeniz türleri ve devralma hiyerarşisi ilişkili olmayan veri öğeleri için benzer gönderme desenleri kolayca uygulayabilirsiniz. 

Desen eşleştirme destekler `is` ifadeleri ve `switch` ifadeler. Her bir nesne ve o nesnenin Aranan deseni karşılayıp karşılamadığını belirlemek için özelliklerini inceleme sağlar. Kullandığınız `when` düzeninin ek kuralları belirtmek için anahtar sözcüğü.

`is` Desen ifadesi genişletir bilinen [ `is` işleci](../language-reference/keywords/is.md#pattern-matching-with-is) bir nesne türü hakkında sorgulayabilir ve sonucu bir yönerge olarak atayın. Aşağıdaki kod bir değişkenin olup olmadığını denetler. bir `int`ve bu durumda, geçerli toplama ekler:

```csharp
if (input is int count)
    sum += count;
```

Önceki küçük örnek geliştirmeler gösterir `is` ifade. Başvuru türleri yanı sıra değer türleri karşı sınayabilirsiniz ve başarılı sonuç doğru türde yeni bir değişkene atayabilirsiniz.

Geçiş eşleşme ifadesi göre tanıdık bir söz dizimi olan `switch` deyimi zaten parçası C# dili. Güncelleştirilmiş switch deyimi birkaç yeni yapılar vardır:

- Değerlendirip türünü bir `switch` ifadesi tam sayı türleri için kısıtlı artık `Enum` türleri `string`, ya da bu türlerden birine karşılık gelen null yapılabilir bir tür. Her türlü kullanılabilir.
- Türünü test edebilirsiniz `switch` her ifade `case` etiketi. Olduğu gibi `is` ifade atadığınız yeni bir değişken için bu türü.
- Eklediğiniz bir `when` daha fazla değişken koşulu test etmek yan tümcesi.
- Sırasını `case` etiketleri önemli sunuldu. Eşleştirilecek ilk dalı yürütülür. Başkalarının atlanır.

Aşağıdaki kod, bu yeni özellikler gösterir:

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0: 
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0: 
                sum += n; 
                break;
            null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- `case 0:` tanıdık sabit modelidir. 
- `case IEnumerable<int> childSequence:` bir tür desendir.
- `case int n when n > 0:` bir türü ile ek bir desendir `when` koşul.
- `case null:` null modelidir.
- `default:` tanıdık varsayılan durumdur.

İçinde desen eşleştirme hakkında daha fazla bilgi [desen eşleştirme C# ](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Ref yerel değerleri ve dönüşleri

Bu özelliği kullanın ve başka bir yerde tanımlanan değişkenleri başvuruları dönüş algoritmalar sağlar. Örneğin, büyük matrisleri ile çalışma ve belirli özelliklere sahip tek bir konum bulma. Aşağıdaki yöntemi döndürür bir **başvuru** Matristeki depolama için:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Dönüş değeri olarak bildirdiğiniz bir `ref` ve matris değeri aşağıdaki kodda gösterildiği gibi değiştirin:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/program.cs#AssignRefReturn "Assign ref return")]

C# Dil kötüye kullanmasının korunmasına çeşitli kurallara sahip `ref` yerel değerleri ve Dönüşleri:

* Eklemelisiniz `ref` yöntem imzası ve tüm anahtar sözcüğü `return` yöntemine deyimler.
    - Bu sayede Temizle yöntemi genelinde başvuruya göre yöntemi döndürür.
* A `ref return` değeri bir değişkene atanabilir veya bir `ref` değişkeni.
    - Çağıran, dönüş değeri veya kopyalanıp kopyalanmadığını denetler. Atlama `ref` dönüş değeri atarken değiştiricisi çağıran bir başvuru değil depolama değerinin bir kopyasıdır istediğini gösterir.
* Standart bir yöntem dönüş değerine atanamaz bir `ref` yerel değişken.
    - Aşağıdaki gibi ifadeler izin vermiyor `ref int i = sequence.Count();`
* Döndüremezsiniz bir `ref` ömürlerinin yönteminin yürütülmesi genişletmek olmayan bir değişkene.
    - Yerel bir değişken veya benzer bir kapsama sahip bir değişken başvuru döndüremez anlamına gelir.
* `ref` yerel değerleri ve dönüşleri zaman uyumsuz yöntemlerle kullanılamaz.
    - Derleyici, zaman uyumsuz yöntem döndürüldüğünde başvurulan değişken son değerine ayarlandı olmadığını bilemezsiniz.

Ref yerel ayarlar ve ref değerleri kopyalama ya da birden çok kez başvurusunu kaldırma işlemlerini gerçekleştirme önleyerek daha verimlidir etkinleştirir algoritmaları döndürür.

Ekleme `ref` için dönüş değeri bir [kaynağı uyumlu değişiklik](version-update-considerations.md#source-compatible-changes). Var olan kod derlenir, ancak başvuru dönüş değeri atandığında kopyalanır. Çağıranlar, depolama alanı için dönüş değeri için güncelleştirilmesi gerekir bir `ref` dönüş başvuru olarak saklamak için yerel değişken.

Daha fazla bilgi için [ref anahtar sözcüğü](../language-reference/keywords/ref.md) makalesi.

## <a name="local-functions"></a>Yerel İşlevler

Sınıflar için birçok tasarım tek bir konumdan Aranan yöntemleri kapsar. Bu ek özel yöntemleri her yöntem, küçük ve odaklı tutun. *Yerel işlevler* , başka bir yöntem bağlamı içinde yöntemleri bildirmek etkinleştirin. Yerel işlevler çalıştığı bağlamı olduğu bildirilen yerel yöntemi yalnızca çağrılır, görmek için sınıf okuyucular için kolaylaştırır.

Yerel işlevler için iki yaygın kullanım örnekleri vardır: Genel yineleyici yöntemleri ve genel zaman uyumsuz yöntemler. Her iki yöntem tür hataları programcılar beklenebilir daha sonra rapor kod oluşturur. Yineleyici yöntemleri, yalnızca özel durumların gözlemlenen döndürülen dizi numaralandırır kod çağırırken. Zaman uyumsuz yöntemlerde özel durumların yalnızca zaman uyulması gereken döndürülen `Task` beklenir. Aşağıdaki örnek, yerel bir işlevi kullanarak yineleyici yöntemin ayıran parametre doğrulaması gösterir:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Aynı yöntem ile işe `async` zaman uyumsuz işler başlamadan önce bağımsız değişken doğrulama doğan özel durumlar emin olmak için yöntemleri:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Yerel işlevleri tarafından desteklenen tasarımları bazılarını da kullanarak sağlayabilirsiniz *lambda ifadeleri*. Bu ilgi olabilir [farklar hakkında daha fazla bilgi](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>Daha fazla ifade gövdeli üyeler

C# 6 sunulan [ifade gövdeli üyeler](csharp-6.md#expression-bodied-function-members) üye işlevleri ve salt okunur özellikler için. C# 7.0 ifadeleri olarak uygulanabilir izin verilen üyeleri genişletir. C# 7. 0 ', uygulayabileceğiniz *oluşturucular*, *sonlandırıcılar*, ve `get` ve `set` bulunan erişimciler *özellikleri* ve *dizin oluşturucular* . Aşağıdaki kod her örneklerini gösterir:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Bu örnek bir sonlandırıcıya gerek yoktur, ancak sözdizimini göstermek için gösterilir. Yönetilmeyen kaynakları serbest bırakmak gerekli olmadıkça, sınıfta bir sonlandırıcı uygulamamalıdır. Kullanmayı da düşünmelisiniz <xref:System.Runtime.InteropServices.SafeHandle> yönetilmeyen kaynakları doğrudan yönetmek yerine sınıfı.

İfade gövdeli üyeler için bu yeni konumlar için önemli bir kilometre temsil C# dil: Bu özellikler, açık kaynaklı çalışma topluluk üyeleri tarafından uygulanan [Roslyn](https://github.com/dotnet/Roslyn) proje.

Bir ifade bodied üyesine bir yöntemi değiştirme bir [ikili uyumlu değişiklik](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Throw ifadeleri

C# ' ta, `throw` her zaman bir deyim olmuştur. Çünkü `throw` deyimi, bir ifade vardı C# uygulanamadı kullandığınız, yapıları. Bunlar, koşullu ifadeleri ve null birleşim ifadelerini bazı lambda ifadeleri dahil. İfade gövdeli üyeler eklenmesi için daha fazla konum ekler burada `throw` ifadeleri yararlı olacaktır. Bu yapıları hiçbirini yazabilmesi amacıyla da, C# 7.0 tanıtır *throw ifadelerini*. 

Bu ayrıca daha fazla ifade tabanlı kod yazmayı kolaylaştırır. Hata denetimi için ek deyimleri gerekmez.

## <a name="generalized-async-return-types"></a>Genelleştirilmiş bir zaman uyumsuz dönüş türleri

Döndüren bir `Task` zaman uyumsuz yöntemler bir nesneden performans sorunlarını Belirli yollardaki tanıtmak. `Task` bir başvuru türü olduğundan, onu kullanarak bir nesne ayırma anlamına gelir. Burada bir yöntem ile bildirilmiş durumlarda `async` değiştiricisi önbelleğe alınmış bir sonuç döndürür ya da zaman uyumlu olarak tamamlanan, kodun önemli bölümleri performans ciddi zaman maliyetine ek ayırmaları hale gelebilir. Bu ayırmalar sıkı döngüleri oluşursa pahalı hale gelebilir.

Bu zaman uyumsuz yöntem dönüş türleri sınırlı olmayan yeni dil özelliğin `Task`, `Task<T>`, ve `void`. Döndürülen tür yine de zaman uyumsuz desen karşılaması gerekir yani bir `GetAwaiter` yöntemi erişilebilir olmalıdır. Somut bir örnek olarak `ValueTask` yapmak için .NET framework türü eklendi bu yeni dil özelliğini kullanın: 

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> NuGet paketini eklemeniz [ `System.Threading.Tasks.Extensions` ](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) kullanmak için <xref:System.Threading.Tasks.ValueTask%601> türü.

Bu geliştirme ayırmaktan kaçınmak kitaplık yazarlar için en kullanışlı bir `Task` kritik kod performansı.

## <a name="numeric-literal-syntax-improvements"></a>Sayısal sabit değer sözdizimi geliştirmeleri

Sayısal sabitlere misreading kodu ilk kez okurken anlaşılması zor yapabilirsiniz. Bit maskeleri ya da diğer simgesel değerleri için yanlış anlama fazladır. C#7.0 en okunabilir bir biçimde için kullanım sayıları yazmak için iki yeni özellikler içerir: *ikili sabit dizeler*, ve *rakam ayırıcıları*.

İçin bu kez, bit maskeleri oluştururken ya da birkaç ikili gösterimini her ikili dosyada bu sayıyı yazma en okunabilir bir kod yapar:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

`0b` Sayı ikili sayı olarak yazılır sabiti başında gösterir. Genellikle bit düzenleri sunarak daha kolay olacak şekilde ikili sayılar uzun alabilirsiniz `_` ikili sabiti yukarıda gösterildiği gibi bir basamak ayırıcı olarak. Basamak ayırıcı sabiti her yerde görünebilir. Taban 10 numaraları için bir binler basamağı kullanmak yaygın ayırıcı:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Basamak ayırıcı ile birlikte kullanılabilir `decimal`, `float`, ve `double` türleri de:

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Birlikte ele alındığında Sayısal sabitler ile çok daha fazla okunabilirliği bildirebilirsiniz.
