---
title: Demetler
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: b169a1c13b3f20d7b5e2a1386cfb28a9cc093dcd
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559095"
---
# <a name="tuples-visual-basic"></a>Tanımlama grupları (Visual Basic)

Visual Basic 2017 ' den itibaren Visual Basic dili, tanımlama gruplarını oluşturmayı ve tanımlama gruplarının öğelerine erişimi kolaylaştıran tanımlama grupları için yerleşik destek sunar. Kayıt düzeni, belirli bir sayı ve değer dizisi olan basit bir veri yapısıdır. Kayıt kümesini örneklediğinizde, her bir değerin (veya öğesinin) numarasını ve veri türünü tanımlarsınız. Örneğin, 2 demet (veya çift) iki öğeye sahiptir. İlki `Boolean` bir değer, ikincisi ise bir değer olabilir `String` . Tanımlama grupları birden çok değeri tek bir nesnede depolamayı kolaylaştırdığından, genellikle bir yöntemden birden çok değer döndürmenin hafif bir yolu olarak kullanılırlar.

> [!IMPORTANT]
> Tanımlama grubu desteği <xref:System.ValueTuple> türü gerektirir. .NET Framework 4,7 yüklü değilse, NuGet galerisinde bulunan NuGet paketini eklemeniz gerekir `System.ValueTuple` . Bu paket olmadan şuna benzer bir derleme hatası alabilirsiniz, "önceden tanımlanmış tür ' ValueTuple (Of,,,) ' tanımlanmamış veya içeri aktarılmaz."

## <a name="instantiating-and-using-a-tuple"></a>Tanımlama grubu örneği oluşturma ve kullanma

Virgülle ayrılmış değerleri parantez içine alarak bir tanımlama grubu örnekleyebilirsiniz. Bu değerlerin her biri, kayıt düzeni alanı haline gelir. Örneğin, aşağıdaki kod, `Date` birinci değeri,, `String` ikincisinin ve üçüncü olarak bir ile bir üçlü (veya 3-kayıt) tanımlar `Boolean` .

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Varsayılan olarak, bir tanımlama grubu içindeki her alanın adı, dizenin `Item` kayıt düzeninde tek tabanlı konumuyla birlikte dizeden oluşur. Bu 3 tanımlama grubu için alan, alanı `Date` `Item1` `String` `Item2` ve `Boolean` alanıdır `Item3` . Aşağıdaki örnek, önceki kod satırında oluşturulan kayıt kümesi alanlarının değerlerini görüntüler

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Visual Basic bir tanımlama grubu alanları okuma-yazma; bir tanımlama grubu örnekledikten sonra, değerlerini değiştirebilirsiniz. Aşağıdaki örnek, önceki örnekte oluşturulan kayıt düzeninin üç alanının ikisini değiştirir ve sonucu görüntüler.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Adlandırılmış bir tanımlama grubu örneği oluşturma ve kullanma

Bir tanımlama grubu alanları için varsayılan adları kullanmak yerine, kendi adlarınızı kayıt düzeni öğelerine atayarak *adlandırılmış bir tanımlama grubu* örneğini oluşturabilirsiniz. Kayıt düzeni alanlarına, kendilerine atanan adlarıyla *veya* varsayılan adlarıyla erişilebilir. Aşağıdaki örnek, ilk alanı `EventDate` , ikincisini ve üçüncü kez açıkça isimlendiren şekilde, daha önceden aynı 3 kayıt hattı oluşturur `Name` `IsHoliday` . Ardından alan değerlerini görüntüler, değiştirir ve alan değerlerini yeniden görüntüler.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Gösterilen demet öğesi adları

Visual Basic 15,3 ' den başlayarak, Visual Basic demet öğelerinin adlarını çıkarabilir; Bunları açıkça atamanız gerekmez. Çıkarsanan tanımlama grubu adları, bir dizi değişkenden bir tanımlama grubu başlattığınızda ve demet öğesi adının değişken adıyla aynı olmasını istediğinizde faydalıdır.

Aşağıdaki örnek, `stateInfo` açıkça adlandırılmış üç öğe,, `state` , ve içeren bir tanımlama grubu oluşturur `stateName` `capital` . Öğeleri adlandırırken, demet başlatma bildiriminin adlandırılmış öğeleri, aynı adlı değişkenlerin değerlerini atadığını unutmayın.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]

Öğeler ve değişkenler aynı ada sahip olduğundan, aşağıdaki örnekte gösterildiği gibi Visual Basic derleyici alanların adlarını çıkarsalabilir.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Gösterilen demet öğesi adlarını etkinleştirmek için, Visual Basic projesi ( \* . vbproj) dosyanızda kullanmak üzere Visual Basic derleyicisinin sürümünü tanımlamanız gerekir:

```xml
<PropertyGroup>
  <LangVersion>15.3</LangVersion>
</PropertyGroup>
```

Sürüm numarası, 15,3 ile başlayan Visual Basic derleyicisinin herhangi bir sürümü olabilir. Belirli bir derleyici sürümünü sabit kodlamak yerine, `LangVersion` sisteminizde yüklü Visual Basic derleyicisinin en son sürümüyle derlemek için "en son" değerini de belirtebilirsiniz.

Daha fazla bilgi için, [Visual Basic dil sürümünü ayarlama](../../../language-reference/configure-language-version.md)bölümüne bakın.

Bazı durumlarda Visual Basic derleyici, aday adından demet öğesi adını çıkarsamaz ve demet alanına yalnızca varsayılan adı kullanılarak başvurulabilir, örneğin, `Item1` `Item2` vb. Bunlar şunları içerir:

- Aday adı,, veya gibi bir demet üyesinin adı ile aynıdır `Item3` `Rest` `ToString` .

- Aday adı kayıt düzeninde yinelenir.

Alan adının çıkarımı başarısız olduğunda, Visual Basic bir derleyici hatası oluşturmaz veya çalışma zamanında oluşturulan bir özel durumdur. Bunun yerine, demet alanlarına, ve gibi önceden tanımlanmış adlarıyla başvurulmalıdır `Item1` `Item2` .

## <a name="tuples-versus-structures"></a>Tanımlama grupları ve yapılar

Visual Basic tanımlama grubu, **System. ValueTuple** genel türlerinden birinin bir örneği olan bir değer türüdür. Örneğin, `holiday` Önceki örnekte tanımlanan kayıt düzeni yapının bir örneğidir <xref:System.ValueTuple%603> . Veriler için hafif bir kapsayıcı olacak şekilde tasarlanmıştır. Kayıt düzeni, birden fazla veri öğesiyle bir nesne oluşturmayı kolaylaştıran bir özel yapının sahip olabileceği bazı özelliklerden oluşur. Bu modüller şunlardır:

- Özel Üyeler. Tanımlama grubu için kendi özelliklerinizi, yöntemlerinizi veya olaylarını tanımlayamazsınız.

- Doğrulamasına. Alanlara atanan verileri doğrulayamazsınız.

- Değiştirilemezlik. Visual Basic tanımlama grupları değişebilir. Buna karşılık, özel bir yapı, bir örneğin değişebilir mi yoksa sabit mi olduğunu denetlemenize olanak tanır.

Özel Üyeler, özellik ve alan doğrulama veya imlik kullanılabilirliği önemliyse, bir özel değer türü tanımlamak için Visual Basic [yapısı](../../../language-reference/statements/structure-statement.md) ifadesini kullanmanız gerekir.

Visual Basic bir tanımlama grubu, değer **Etuple** türünün üyelerini devralınır. Alanlarına ek olarak, bunlar aşağıdaki yöntemleri içerir:

| Yöntem | Açıklama |
| ---|---|
| CompareTo | Geçerli tanımlama grubunu aynı sayıda öğeye sahip başka bir tanımlama grubu ile karşılaştırır. |
| Eşittir | Geçerli tanımlama grubunun başka bir demet veya nesneye eşit olup olmadığını belirler. |
| GetHashCode | Geçerli örnek için karma kodu hesaplar. |
| ToString | Bu tanımlama grubunun dize gösterimini döndürür. Bu, formunu alır `(Item1, Item2...)` `Item1` ve `Item2` kayıt düzeni alanlarının değerlerini temsil eder. |

Ayrıca, **Valuetuple** türleri <xref:System.Collections.IStructuralComparable> <xref:System.Collections.IStructuralEquatable> , ve arabirimlerini özel Karşılaştırıcılar tanımlamanızı sağlayacak şekilde uygular.

## <a name="assignment-and-tuples"></a>Atama ve tanımlama grupları

Visual Basic, aynı sayıda alana sahip demet türleri arasında atamayı destekler. Aşağıdakilerden biri doğruysa alan türleri dönüştürülebilir:

- Kaynak ve hedef alanı aynı türde.

- Kaynak türü için bir genişletme (veya örtük) hedef türüne dönüştürme tanımlanır.

- `Option Strict``On`, ve kaynak türün hedef türüne bir daraltma (veya açık) dönüştürmesi tanımlanmıştır. Bu dönüştürme, kaynak değer hedef türü aralığının dışındaysa bir özel durum oluşturabilir.

Diğer dönüşümler atamalar için değerlendirilmez. Demet türleri arasında izin verilen atama türlerine bakalım.

Aşağıdaki örneklerde kullanılan değişkenleri göz önünde bulundurun:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

İlk iki değişken `unnamed` ve `anonymous` , alanlar için belirtilen semantik adlara sahip değildir. Alan adları varsayılan `Item1` ve ' dir `Item2` . Son iki değişken `named` ve `differentName` anlamsal alan adlarına sahip. Bu iki tanımlama alanının alanlar için farklı adlara sahip olduğunu unutmayın.

Bu başlıkların dördü, aynı sayıda alana sahiptir (' parametre sayısı ' olarak adlandırılır) ve bu alanların türleri aynıdır. Bu nedenle, bu atamaların hepsi çalışır:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Başlıkların adlarının atanmadığından emin olun. Alanların değerleri, kayıt grubundaki alanların sırasını izleyerek atanır.

Son olarak, `named` `conversion` ilk alanı `named` bir, `Integer` ve ' nin ilk alanı bir olan olan ' a sahip olsa da, kayıt kümesini tanımlama grubu `conversion` atayabiliriz `Long` . Bu atama başarılı oldu çünkü bir `Integer` öğesine dönüştürme `Long` , genişleyen bir dönüştürme.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Farklı sayıda alan içeren diziler atanamaz:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Yöntem dönüş değerleri olarak tanımlama grubu

Bir yöntem yalnızca tek bir değer döndürebilir. Genellikle, bir yöntem çağrısını birden çok değer döndürecek şekilde istersiniz. Bu kısıtlamayı geçici olarak çözmek için birkaç yol vardır:

- Özellikleri veya alanları yöntemi tarafından döndürülen değerleri temsil eden özel bir sınıf veya yapı oluşturabilirsiniz. Bu nedenle ağır bir çözümdür; yalnızca amacı bir yöntem çağrısından değerleri almak olan özel bir tür tanımlamanızı gerektirir.

- Yönteminden tek bir değer döndürebilir ve diğer değerleri yöntemine başvuruya göre geçirerek döndürebilirsiniz. Bu, başvuruya göre geçirdiğiniz değişkenin değerinin yanlışlıkla üzerine yazılması için bir değişken ve riskleri örnekleyerek oluşan ek yükünü içerir.

- Birden çok dönüş değerini almak için basit bir çözüm sağlayan bir tanımlama grubu kullanabilirsiniz.

Örneğin, .NET 'teki **Tryparo** yöntemleri `Boolean` ayrıştırma işleminin başarılı olup olmadığını gösteren bir değer döndürür. Ayrıştırma işleminin sonucu, metoduna verilen başvuruya göre geçirilen bir değişkende döndürülür. Normalde, gibi bir ayrıştırma yöntemine yapılan bir çağrı aşağıdaki gibi <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> görünür:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

Yöntemini kendi yöntemdeki yöntemine sarımızda ayrıştırma işleminden bir tanımlama grubu döndürüyoruz <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> . Aşağıdaki örnekte, `NumericLibrary.ParseInteger` <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemini çağırır ve iki öğesi olan adlandırılmış bir tanımlama grubu döndürür.

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Daha sonra aşağıdaki gibi kodla yöntemi çağırabilirsiniz:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>.NET Framework Visual Basic tanımlama grupları ve tanımlama grupları

Visual Basic tanımlama grubu, .NET Framework 4,7 ' de tanıtılan **System. ValueTuple** genel türlerinden birinin bir örneğidir. .NET Framework Ayrıca bir dizi genel **System. Tuple** sınıfı içerir. Ancak, bu sınıflar, Visual Basic tanımlama tiplerinden ve **System. ValueTuple** genel türlerinden farklı çeşitli yollarla farklılık gösterir:

- **Demet** sınıflarının öğeleri, vb. adlı özelliklerdir `Item1` `Item2` . Visual Basic tanımlama tiplerinde ve **Valuetuple** türlerinde, demet öğeleri alanlardır.

- Bir **demet** örneğinin veya bir **Valuetuple** örneğinin öğelerine anlamlı adlar atayamazsınız. Visual Basic alanların anlamını karşılayan adlar atamanıza izin verir.

- Bir **tanımlama grubu** örneğinin özellikleri salt okunurdur; tanımlama grupları sabittir. Visual Basic tanımlama tiplerinde ve **Valuetuple** türlerinde, demet alanları okuma-yazma ' dır; tanımlama grupları değişebilir.

- Genel **demet** türleri başvuru türleridir. Bu **demet** türlerinin kullanılması, nesneleri ayırmayı gösterir. Etkin yollarda bu, uygulamanızın performansı üzerinde ölçülebilir bir etkiye sahip olabilir. Visual Basic tanımlama grupları ve **Valuetuple** türleri değer türlerdir.

Sınıfındaki genişletme yöntemleri <xref:System.TupleExtensions> Visual Basic tanımlama grupları ve .net **demet** nesneleri arasında dönüştürme yapmayı kolaylaştırır. **ToTuple** yöntemi bir Visual Basic tanımlama grubunu bir .net **demet** nesnesine dönüştürür ve **tovaluetuple** yöntemi bir .net **demet** nesnesini bir Visual Basic tanımlama grubu öğesine dönüştürür.

Aşağıdaki örnek bir tanımlama grubu oluşturur, bunu bir .NET **demet** nesnesine dönüştürür ve Visual Basic bir tanımlama grubu geri dönüştürür. Daha sonra örnek, eşit olduklarından emin olmak için bu tanımlama grubunu orijinal bir ile karşılaştırır.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic dil başvurusu](index.md)
