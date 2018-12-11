---
title: Visual Basic'te diziler
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: c0198cde88b66f5e115c82b5454bd8a32db7ef96
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143720"
---
# <a name="tuples-visual-basic"></a>Diziler (Visual Basic)

Visual Basic 2017'den itibaren Visual Basic dili yapan diziler için yerleşik destek sunan tanımlama grupları oluşturma ve tanımlama grubu daha kolay öğelere erişme. Bir demet belirli sayıda ve sıralamadaki değerleri olan bir basit veri yapısıdır. Tanımlama grubu başlattığınızda, sayı ve her değeri (veya öğenin) veri türünü tanımlayın. Örneğin, iki öğe 2 bölütlü (veya çift) vardır. İlk olabilir bir `Boolean` ikinci olmakla birlikte, değeri bir `String`. Tanımlama grubu birden çok değeri tek bir nesnede depolamak kolaylaştırmak için bunlar genellikle bir yöntemden birden çok değer döndürmek için basit bir yolu olarak kullanılır.

> [!IMPORTANT]
> Tanımlama grubu desteği gerektiren <xref:System.ValueTuple> türü. .NET Framework 4.7 yüklü değilse, NuGet paketini eklemeniz gerekir `System.ValueTuple`, kullanılabildiği NuGet galerisinde. Bu paket olmadan bir derleme hatası benzer şekilde, "'ValueTuple(Of,,,)' tanımlı veya içeri aktarılmamış önceden tanımlanmış türü." alabilirsiniz

## <a name="instantiating-and-using-a-tuple"></a>Örnekleme ve bir tanımlama grubu kullanımı

Bir kayıt düzeni, virgülle ayrılmış değerler IM parantezleri kapsayan tarafından örneği oluşturur. Bu değerlerin her birinin ardından düzeninin bir alan haline gelir. Örneğin, aşağıdaki kod bir Üçlü (veya 3'lü demet) ile tanımlar bir `Date` ilk değer olarak bir `String` olarak kendi ikinci ve `Boolean` kendi üçüncü olarak.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Varsayılan olarak, her bir alan tanımlama grubu adı dizesi oluşur `Item` alanın bir tabanlı konumu dizideki yanı sıra. Bu 3'lü demet için `Date` alandır `Item1`, `String` alandır `Item2`ve `Boolean` alandır `Item3`. Aşağıdaki örnek kod önceki satırda örneği düzeninin alanların değerlerini görüntüler.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Visual Basic tanımlama grubu salt okunur alanları; bir demet kullanmanızın sonra değerlerini değiştirebilirsiniz. Aşağıdaki örnek önceki örnekte oluşturulan demet üç alanı iki değiştirir ve sonucu görüntüler.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Örnekleme ve adlandırılmış bir tanımlama grubu kullanımı

Bir Demetin alanlar için varsayılan adlar kullanmak yerine örneği oluşturabilir bir *demet adlı* düzeninin öğelerine kendi adlarınızı atayarak. Kayıt düzeninin alanları sonra atanan adlarıyla erişilebilir *veya* varsayılan adlarına göre. Açıkça ilk alan adları dışında aynı 3 demet olarak daha önce aşağıdaki örnekte başlatır `EventDate`, ikinci `Name`ve üçüncü `IsHoliday`. Ardından alan değerlerini görüntüler, bunları değiştirir ve yeniden alan değerlerini görüntüler.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Çıkarsanan demet öğesi adları

Visual Basic, Visual Basic 15.3 ile başlayarak, tanımlama grubu öğelerinin adlarını çıkarımını; açıkça atamanız gerekmez. Çıkarsanan demet adları, değişkenlerin bir kümeden bir tanımlama grubu başlatmak ve demet öğesi adı değişken adı ile aynı olmasını istediğinizde yararlıdır. 

Aşağıdaki örnek, oluşturur bir `stateInfo` açıkça içeren üç dizi öğeleri, adlı `state`, `stateName`, ve `capital`. Öğeleri adlandırmada unutmayın, dizi başlatma ifadesi, yalnızca adlandırılmış öğeleri aynı adlı değişkenlerin değerleri atar.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
Öğeleri ve değişkenler aynı ada sahip olduğundan, Visual Basic derleyicisi aşağıdaki örnekte gösterildiği gibi alanların adlarını çıkarabilir.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Çıkarsanan demet öğesi adları etkinleştirmek için Visual Basic projesinde kullanmak için Visual Basic derleyici tanımlayın (\*.vbproj) dosya: 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 
```

Herhangi bir sürümü 15.3 ile başlayarak Visual Basic derleyicinin sürüm numarası olabilir. Belirli bir derleyici sürümü kodlamak yerine, "Son" değeri olarak belirtebilirsiniz `LangVersion` sisteminizde yüklü Visual Basic derleyici en son sürümünü derlemek için.

Daha fazla bilgi için [Visual Basic dil sürümü ayarını](../../../language-reference/configure-language-version.md).

Bazı durumlarda, Visual Basic Derleyicisi demet öğesi adı aday adından çıkarsanamıyor ve demet alanı yalnızca kendi varsayılan adı gibi kullanarak başvurulabilir `Item1`, `Item2`vb. Bu güncelleştirmeler şunlardır:

- Aday adı bir tanımlama grubu üyesinin adıyla aynı olduğu gibi `Item3`, `Rest`, veya `ToString`.

- Tanımlama grubunda bulunan aday adı yineleniyor.
 
Alan adı anlam çıkarma başarısız olduğunda, Visual Basic derleyici hatası oluşturmaz veya çalışma zamanında bir durum değil. Bunun yerine, tanımlama grubu alanları önceden tanımlanmış adlarıyla gibi başvurulmalıdır `Item1` ve `Item2`. 
  
## <a name="tuples-versus-structures"></a>Diziler ve yapılar

Visual Basic tanımlama grubu örneği biri olan bir değer türü olan bir **System.ValueTuple** genel türler. Örneğin, `holiday` önceki örnekte tanımlanan dizi öğesinin bir örneğiyse <xref:System.ValueTuple%603> yapısı. Veriler için basit bir kapsayıcı olacak şekilde tasarlanmıştır. Birden çok veri öğeleri ile bir nesne oluşturmak kolay hale getirmek için demet amaçlar olduğundan, özel bir yapı olabilecek özelliklerden bazıları eksik olabilir. Bu güncelleştirmeler şunlardır:

- Özel üyeler. Kendi özellikleri, yöntemleri ve olayları bir demet için tanımlayamazsınız.

- Doğrulama. Alanlara atanan veri doğrulanamıyor.

- Değiştirilemezlik. Visual Basic diziler değişebilir. Bir örneği değişebilir veya sabit olup olmadığını buna karşılık, özel bir yapı denetlemenize izin verir.

Özel üyeler, özellik ve alan doğrulama veya değiştirilemezlik önemliyse, Visual Basic kullanması gereken [yapısı](../../../language-reference/statements/structure-statement.md) deyimi bir özel değer türü tanımlamak için.

Visual Basic tanımlama grubu üyelerini devralır, **ValueTuple** türü. Alanlara ek olarak, bunlar aşağıdaki yöntemleri içerir:

| Üye | Açıklama |
| ---|---|
| compareTo | Geçerli tanımlama grubu için başka bir tanımlama grubu aynı sayıda öğe ile karşılaştırır. |
| Eşittir | Geçerli tanımlama grubu başka bir tanımlama grubu veya nesneye eşit olup olmadığını belirler. |
| GetHashCode | Geçerli örneğin karma kodunu hesaplar. |
| ToString | Bu dizi biçimi alır dize gösterimini döndürür `(Item1, Item2...)`burada `Item1` ve `Item2` düzeninin alanların değerlerini temsil eder. |

Ayrıca, **ValueTuple** türleri uygulayan <xref:System.Collections.IStructuralComparable> ve <xref:System.Collections.IStructuralEquatable> form veya arabirimlerini müşteri karşılaştırıcılarla tanımlamanızı sağlar.

## <a name="assignment-and-tuples"></a>Atama ve diziler

Visual Basic, aynı sayıda alan tanımlama grubu türleri arasında atama destekler. Aşağıdakilerden biri true ise alan türleri dönüştürülebilir:

- Kaynak ve hedef alan aynı türde olan.

- Kaynak türü hedef türü için bir genişletme (ya da örtük) dönüştürme tanımlanır. 

- `Option Strict` olan `On`, ve bir kaynak türü daraltma (veya açık) dönüştürme için hedef türü tanımlanır. Bu dönüştürme, kaynak değeri hedef türün aralığı dışında ise bir özel durum.

Diğer dönüştürme atamalarını kabul edilmez. Tanımlama grubu türleri arasında izin atamaları türlerini bakalım.

Aşağıdaki örneklerde kullanılan bu değişkenleri göz önünde bulundurun:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

İlk iki değişken `unnamed` ve `anonymous`, alanlar için sağlanan anlam adları yok. Varsayılan alan adları olan `Item1` ve `Item2`. Son iki değişken `named` ve `differentName` anlam alan adlarına sahip. Bu iki diziler alanları için farklı adlar olduğunu unutmayın.

Dört bu tanımlama grubu ('kutup' adlandırılır) alanları aynı sayıda sahiptir ve bu alan türlerini aynıdır. Bu nedenle, tüm bu atamaları çalışır:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Tanımlama grubu adlarını atanmamış dikkat edin. Kayıt düzeni, alanların sırasını aşağıdaki alanların değerlerini atanır.

Son olarak, biz atayabilirsiniz dikkat edin `named` kullanılacak kayıt düzeni `conversion` başlığın olsa bile ilk alanı, `named` olduğu bir `Integer`ve ilk alanı, `conversion` olduğu bir `Long`. Dönüştürme çünkü bu atama başarılı bir `Integer` için bir `Long` genişleyen bir dönüştürmedir.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Diziler farklı sayıda alanlar atanabilir değil:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Yöntemin dönüş değeri olarak diziler

Bir yöntem, yalnızca tek bir değer döndürebilir. Sık, ancak birden çok değer döndürmek için bir yöntem çağrısının istediğiniz. Bu sınırlara yakın çalışmak için birkaç yol vardır:

- Özel bir sınıf veya yapı özelliklerini oluşturabilir veya alanları yöntem tarafından döndürülen değerleri temsil eder. Bu nedenle ağır bir çözümdür; tek amacı, bir yöntem çağrısından değerleri almak için olan özel bir tür tanımlamak gerektiriyor.

- Yönteminden tek bir değer döndürmesi ve yönteme başvuru tarafından geçirerek kalan değerler döndürür. Bu, bir değişken ve başvuruya göre geçiren değişkenin değerini yanlışlıkla üzerine riskleri örnekleme ek yükünü içerir.

- Birden çok değer almak için basit bir çözüm sağlayan bir tanımlama grubu kullanabilirsiniz.

Örneğin, **TryParse** .NET dönüş yöntemleri bir `Boolean` ayrıştırma işleminin başarılı olup olmadığını gösteren değer. Ayrıştırma işleminin sonucu bir değişkene bir yönteme başvuru tarafından geçirilen döndürülür. Normalde, bir çağrı gibi bir ayrıştırma yönteminin <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> aşağıdaki gibi görünür:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

Biz çağrısını sarmalamak, biz bir demet ayrıştırma işlemi döndürebilir <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> kendi yöntemi yöntemi. Aşağıdaki örnekte, `NumericLibrary.ParseInteger` çağrıları <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemi ve iki öğe ile adlandırılmış bir tanımlama grubu döndürür. 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Ardından, aşağıdaki gibi kod ile yöntemi çağırabilirsiniz:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Visual Basic diziler ve .NET Framework içindeki diziler

Visual Basic tanımlama grubu birinin örneğidir **System.ValueTuple** içinde .NET Framework 4.7 tanıtılan genel türler. .NET Framework ayrıca genel bir kümesini içerir **System.Tuple** sınıfları. Bu sınıfların ancak Visual Basic dizilerini ' farklı ve **System.ValueTuple** çeşitli yollarla genel türleri:

- Öğeleri **demet** sınıflardır adlı özellikleri `Item1`, `Item2`ve benzeri. Visual Basic demetlerde ve **ValueTuple** türleri, tanımlama grubu öğelerinin alanlardır.

- Öğeleri için anlamlı adlar atanamaz bir **demet** örneği veya bir **ValueTuple** örneği. Visual Basic, anlamı alanları, iletişim kuran adları atamanıza olanak tanır.

- Özellikleri bir **demet** örnek salt okunur; diziler sabittir. Visual Basic demetlerde ve **ValueTuple** türleri, dizi alanları salt okunur; diziler değişebilir.

- Genel **demet** türleri başvuru türleridir. Bunları kullanarak **demet** türleri nesneleri ayırma anlamına gelir. Etkin yolları üzerinde bu, uygulamanızın performans üzerinde ölçülebilir bir etkisi olabilir. Visual Basic diziler ve **ValueTuple** türler değer türleridir.

Uzantı yöntemleri <xref:System.TupleExtensions> sınıfı kolaylaştırır .NET ve Visual Basic diziler arasında dönüştürme **demet** nesneleri. **ToTuple** yöntemi, bir Visual Basic tanımlama grubu için bir .NET dönüştürür **demet** nesnesi ve **ToValueTuple** yöntemi, bir .NET dönüştürür **demet** Visual Basic tanımlama grubu için nesne.

Aşağıdaki örnek bir tanımlama grubu oluşturur, bir .NET ile dönüştürür **demet** nesnesi ve bir Visual Basic demet için geri dönüştürür. Örnek daha sonra bu demet eşit olmasını sağlamak için özgün bir karşılaştırır.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

[Visual Basic Dili Başvurusu](index.md)  
