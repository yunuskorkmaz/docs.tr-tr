---
title: C# 6 - C# Kılavuzu yenilikler nelerdir?
description: C# sürüm 6'deki yeni özelliklerin öğrenin
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: 00aeb3ed940acfca748a1a9eb876fd0133baf6c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c-6"></a>C# 6 yenilikler nelerdir?

C# 6.0 yayın geliştiriciler için verimliliğini artıran birçok özellik içeriyor. Bu sürümdeki özellikleri şunlardır:

* [Salt okunur otomatik özellikleri](#read-only-auto-properties):
    - Salt okunur otomatik yalnızca kurucularda ayarlanabilecek özelliklerini oluşturabilirsiniz.
* [Otomatik özelliği başlatıcıları](#auto-property-initializers):
    - Bir otomatik özelliğinin ilk değeri ayarlamak için başlatma ifadeler yazabilirsiniz.
* [İşlev ifadesi bodied üyeleri](#expression-bodied-function-members):
    - Lambda ifadeleri kullanma tek satır yöntemleri yazabilirsiniz.
* [statik kullanarak](#using-static):
    - Tek bir sınıfın tüm yöntemleri geçerli ad alanı aktarabilirsiniz.
* [Null - Koşullu işleçler](#null-conditional-operators):
    - Null ile null koşullu işleç için hala denetlenirken bir nesnenin üyelerine yönelik olarak kısaca ve güvenli bir şekilde erişebilir.
* [Dize ilişkilendirme](#string-interpolation):
    - Satır içi ifadeler yerine konumsal bağımsız değişkenler kullanarak ifadeleri biçimlendirme dizesi yazabilirsiniz.
* [Özel durum filtreleri](#exception-filters):
    - Özel durum veya diğer program durumunu bir özelliğe göre ifadeler yakalayabilir. 
* [nameof ifadeleri](#nameof-expressions):
    - Simgeler dize temsilini oluşturmak derleyici izin verebilirsiniz.
* [catch await ve son olarak engeller](#await-in-catch-and-finally-blocks):
    - Kullanabileceğiniz `await` daha önce bunları izin verilmeyen konumları ifadelerinde.
* [Dizin başlatıcıları](#index-initializers):
    - Başlatma ifadeleri sıralı kapsayıcıları yanı sıra ilişkilendirilebilir kapsayıcıları için yazabilirsiniz.
* [Koleksiyon başlatıcıları için genişletme yöntemleri](#extension-add-methods-in-collection-initializers):
    - Koleksiyon başlatıcıları üye yöntemleri yanı sıra erişilebilir uzantı yöntemleri güvenebilirsiniz.
* [Geliştirilmiş aşırı yükleme çözünürlüğü](#improved-overload-resolution):
    - Belirsiz yöntem çağrılarını şimdi daha önce oluşturulan bazı yapıları doğru şekilde çözümleyin.

Genel bu özelliklerin de daha okunabilir daha kısa kod yazma etkisidir. Birçok ortak uygulamalar için daha az seremoni sözdizimi içeriyor. Daha az seremoni ile tasarım hedefi görmek daha kolay olur. Bu özellikler de öğrenin ve daha üretken, daha okunabilir kod yazın ve daha dil yapıları, çekirdek özellikleri yoğunlaşabilirsiniz.

Bu konunun geri kalanında bu özelliklerin her biri hakkında ayrıntılar sağlar.

## <a name="auto-property-enhancements"></a>Otomatik özellik geliştirmeleri 

Otomatik uygulanan özellikler (genellikle 'otomatik-Özellikler' adlandırılır) sözdizimi yaptığı basit get vardı özellikleri oluşturmak çok kolay ve erişimciler ayarlayın:

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

Ancak, bu basit sözdizimi otomatik özelliklerini kullanarak destekleyebilir tasarımları türlerini sınırlı. Daha fazla senaryolarda kullanabilmeleri C# 6 otomatik özellikleri yeteneklerini artırır. Geri dönüş bildirme ve kadar sık yedekleme alanını el ile düzenleme hakkında daha ayrıntılı sözdizimi gerekmez.

Yeni sözdizimini senaryoları salt okunur özellikler ve değişken depolama otomatik özelliği arkasında başlatma yer almaktadır.

### <a name="read-only-auto-properties"></a>Salt okunur otomatik özellikleri

*Salt okunur otomatik özelliklerini* değişmez türleri oluşturmak için daha kısa bir sözdizimi sağlar. Özel ayarlayıcılar bildirmek için en yakın önceki sürümlerinde, C# değişmez türlerine alabilir oluştu:

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
Bu sözdizimini kullanarak, derleyici türü gerçekten değişmez garanti etmez. Onu yalnızca, zorlar `FirstName` ve `LastName` sınıfı dışında herhangi bir koddan özellikleri değiştirilmez.

Salt okunur otomatik özellikler doğru salt okunur davranışını etkinleştirir. Otomatik özelliği yalnızca bir get erişimcisine bildirin:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

`FirstName` Ve `LastName` özellikleri yalnızca bir oluşturucu gövdesinde ayarlanabilir:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Ayarlanmaya çalışılırken `LastName` içinde başka bir yöntem oluşturur bir `CS0200` derleme hatası:

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

Bu özellik sabit türleri daha kısa ve uygun otomatik özelliği sözdizimini kullanarak doğru dil için destek sağlar.

### <a name="auto-property-initializers"></a>Otomatik özelliği başlatıcıları

*Otomatik özelliği başlatıcıları* özellik bildirimi bir parçası olarak bir otomatik özelliğinin ilk değeri bildirme sağlar.  Önceki sürümlerde, bu özellikleri ayarlayıcılar olması gerekir ve yedekleme alanı tarafından kullanılan veri depolama alanı başlatmak için bu ayarlayıcı kullanmanız gerekir. Bu sınıf adı ve öğrencinin dereceleri listesini içeren bir öğrenci için göz önünde bulundurun:

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
Bu sınıf büyüdükçe, diğer oluşturucular içerebilir. Bu alan başlatmak her Oluşturucusu gerekiyor veya hatalara neden.

C# 6 otomatik özelliği otomatik özellik bildirimi tarafından kullanılan depolama alanı için bir başlangıç değeri atamanızı sağlar:

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` Üyesi olduğu bildirilmiş başlatılır. Tam olarak bir kez başlatma işlemini kolaylaştırır. Başlatma için ortak arabirimi ile depolama ayırma eşitlemek daha kolay özellik bildirimi parçası olan `Student` nesneleri.

Özellik başlatıcıları gösterildiği gibi salt okunur özellikler yanı sıra okuma/yazma özellikleri ile kullanılabilir.

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a>İşlev ifadesi bodied üyeleri

Biz yazma üyeleri çok gövdesi bir ifade olarak temsil edilebilir yalnızca bir deyim oluşur. Bunun yerine bir ifade bodied üye yazarak o sözdizimi azaltabilir. Bu yöntemleri ve salt okunur özellikler için çalışır. Örneğin, bir geçersiz kılma `ToString()` genellikle mükemmel bir adaydır:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

İfade bodied üyeleri de salt okunur özellikler de kullanabilirsiniz:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a>statik kullanma

*Statik kullanarak* geliştirme, tek bir sınıfın statik yöntemleri içeri aktarmanıza olanak sağlar. Daha önce `using` beyanının içeri aktarılıp bir ad alanındaki tüm türleri. 

Genellikle bir sınıfın statik yöntemleri kodumuza kullanırız. Art arda sınıf adını yazarak kodunuzu anlamını soyutlamaması. Birçok sayısal hesaplamalar sınıfları yazdığınızda, ortak bir örnektir.
Kodunuz ile littered <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> ve diğer çağrılar farklı yöntemlere <xref:System.Math> sınıfı. Yeni `using static` sözdizimi yapabilir bu sınıfların çok temizleyici okunamıyor. Kullanmakta olduğunuz sınıfı belirtin:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

Ve şimdi, tüm statik yönteminde kullanabilirsiniz <xref:System.Math> niteleme olmadan sınıfı <xref:System.Math> sınıfı. <xref:System.Math> Sınıfı herhangi bir örnek yöntem içermediğinden bu özellik için harika kullanımı söz konusu değildir. Aynı zamanda `using static` statik olan bir sınıfı için bir sınıfın statik yöntemleri alıp yöntemleri örneği. En yararlı örnekler biri <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Tam sınıf adını kullanmalısınız `System.String` statik olarak using deyimi. Kullanamazsınız `string` anahtar sözcüğü yerine. 

Tanımlanan statik yöntemler çağırabilirsiniz <xref:System.String> bu yöntemleri o sınıfın bir üyesi olarak niteleme olmadan sınıfı:

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

`static using` Özelliği ve uzantı yöntemleri ilginç şekillerde etkileşim ve özellikle bu etkileşimler adres bazı kurallar dil tasarım dahil. Varolan önemli değişiklikler herhangi olasılığını en aza indirmek için sizin de dahil olmak üzere olarak kullanılabilecek kod temeli hedeftir.

Bir statik yöntem olarak değil çağrıldığında uzantı yöntemi çağırma sözdizimini kullanarak çağrıldığında kapsamında uzantı yöntemleri şunlardır.
Bu LINQ sorguları genellikle görürsünüz. İçeri aktararak LINQ düzeni aktarabilirsiniz <xref:System.Linq.Enumerable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Bu tüm yöntemleri alır <xref:System.Linq.Enumerable> sınıfı.
Ancak, genişletme yöntemleri genişletme yöntemleri olarak çağrıldığında kapsamında değildir. Statik yöntem sözdizimi kullanılarak çağrılır varsa bunlar kapsamında değildir:

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

Genişletme yöntemleri, genellikle uzantı yöntemi çağırma ifadeler kullanarak denir çünkü bu bir karardır. Bunlar statik yöntemini kullanarak burada adlandırılır nadir durumda karışıklığı çözmek için olan sözdizimi çağırın.
Sınıf adı çağırma bir parçası olarak gerektiren akıllıca gibi görünüyor.

Bir son özelliğini yok `static using`. `static using` Yönergesi de tüm iç içe geçmiş türler alır. Bu tüm iç içe geçmiş türler niteliğe olmadan başvuru sağlar.

## <a name="null-conditional-operators"></a>Null-conditional işleçleri

Null değerler kod zorlaştırabilir. Her erişim değişkenlerinin değil başvurusunun kaldırılmasının emin olmak için kontrol etmeniz `null`. *Null koşullu işleç* bu denetimlerini çok daha kolay ve akıcı hale getirir.

Üye erişimi yalnızca Değiştir `.` ile `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

Önceki örnekte, değişken `first` atanan `null` kişi nesne ise `null`. Değeri, aksi takdirde, atanan `FirstName` özelliği. En önemlisi, `?.` Bu kod satırı oluşturmayacak anlamına gelir bir `NullReferenceException` zaman `person` değişken `null`. Bunun yerine, short-circuits ve üreten `null`.

Ayrıca, bu deyim döndürür Not bir `string`değerinin ne olursa olsun `person`.
Kestirmeler, söz konusu olduğunda `null` tam ifadeyle eşleşecek döndürülen değeri belirtilmiş.

Bu yapı ile genellikle kullanabilirsiniz *null birleştirmesi* özelliklerinden biri olduğunda, varsayılan değerleri atamak için işleci `null`:

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Sağ taraftaki yan işleneni `?.` işleci özellikler veya alanlar için sınırlı değildir.
Koşullu yöntemleri çağırmak için de kullanabilirsiniz. Üye işlevleri null koşullu işleç ile en yaygın kullanımı güvenle temsilciler (veya olay işleyicileri) çağırmaktır olabilecek `null`.  Siz temsilcinin çağırarak gerçekleştirirsiniz `Invoke` yöntemini kullanarak `?.` üye erişimi işleci. Bir örneğe bakın  
[desenler temsilci](../delegates-patterns.md#handling-null-delegates) konu.

Kurallarına `?.` işleci olun işlecinin sol taraftaki yalnızca bir kez değerlendirilir. Bu önemlidir ve olay işleyicilerini kullanarak örnek dahil olmak üzere birçok deyimleri sağlar. Olay işleyici kullanımıyla başlayalım. Önceki sürümlerinde C#, aşağıdakine benzer bir kod yazmak için önerilir:

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

Bu, daha basit bir söz dizimi tercih edilen:

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> Önceki örnekte bir yarış durumu sunar. `SomethingHappened` Olay karşı işaretlendiğinde aboneleri olabilir `null`, ve olay tetiklenir önce bu aboneleri kaldırılmış olabilir. Neden bir <xref:System.NullReferenceException> oluşturulmasına.

Bu ikinci sürümünde `SomethingHappened` olay işleyicisi sınandığında null olmayan olabilir, ancak başka bir kod bir işleyici kaldırırsa, olay işleyicisi çağrıldığında hala null olabilir.

Derleyici için kod oluşturur `?.` sol tarafındaki sağlar işleci (`this.SomethingHappened`), `?.` ifade kez değerlendirilir ve sonucu önbelleğe alınır:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Sol tarafta yalnızca bir kez değerlendirilir sağlama da sol tarafındaki yöntem çağrıları dahil olmak üzere herhangi bir ifade kullanabilmenizi sağlar `?.` bu yan etkileri sahip olsa bile yan etkileri yalnızca bir kez gerçekleşebilir, yani bir kez değerlendirilme. Bizim içerik örnek görebilirsiniz [olayları](../events-overview.md#language-support-for-events).

## <a name="string-interpolation"></a>Dize ilişkilendirme

C# 6 bir biçim dizesi ve diğer dize değerlerini üretmek için değerlendirilen bir ifade dizelerden oluşturmak için yeni sözdizimi içeriyor.

Konumsal parametreler gibi bir yöntem kullanmak için gereken geleneksel olarak, `string.Format`:

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

C# 6, yeni [dize ilişkilendirme](../language-reference/tokens/interpolated.md) özelliği Biçim dizesinde ifade katıştırma olanak sağlar. Yalnızca dizesiyle yazdığınızdan `$`:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Bu ilk örnek özellik ifadeleri değiştirilen ifadeleri için kullanır. Herhangi bir ifade kullanmak için bu sözdizimini genişletebilirsiniz. Örneğin, öğrencinin Not noktası ortalaması ilişkilendirme bir parçası olarak işlem:

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

Önceki örnekte çalışan, size, çıktı için bulur `Grades.Average()` istediğiniz olandan daha fazla ondalık hane olabilir. Dize ilişkilendirme sözdizimi tüm biçim dizeleri kullanılabilir önceki biçimlendirme yöntemlerine kullanılmasını destekler. Biçim dizeleri kaşlı ayraçlar içinde ekleyin. Ekleme bir `:` ifade biçimlendirmek için aşağıdaki:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Önceki kod satırı ile değeri biçimlendirir `Grades.Average()` iki ondalık basamak içeren bir kayan noktalı sayı olarak.

`:` Her zaman biçimlendirilen ifadesi ve biçim dizesi arasındaki ayırıcı olarak yorumlanır. İfadeniz kullandığında, bu sorunları ortaya çıkarabilir bir `:` koşullu bir işleç gibi başka bir şekilde:

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

Önceki örnekte `:` koşullu işleç parçası olmayan biçim dizesi başlayan olarak ayrıştırılır. Burada bu gerçekleşir tüm durumlarda ifade düşündüğünüz olarak ifade yorumlamaya derleyici zorlamak için parantez ile çevreleyen:

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

Kaşlı ayraç yerleştirebilirsiniz ifadeleri sınırlamalar değil. Karmaşık bir LINQ Sorgu sonucu görüntülemek ve hesaplamalar gerçekleştirmek için Ara değerli bir dize içinde çalıştırabilirsiniz:

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

Bir dize ilişkilendirme ifadesi başka bir dize ilişkilendirme deyimi içinde bile geçirebilmenize bu örnekten görebilirsiniz. Bu örnek daha daha karmaşık üretim kodunda istersiniz olasılığı yüksektir.
Bunun yerine, yalnızca tanım özellik derecesini. Ara değerli bir dize süslü ayraçlar arasında herhangi bir C# ifade yerleştirilebilir.

### <a name="string-interpolation-and-specific-cultures"></a>Dize ilişkilendirme ve belirli kültürler

Önceki bölümde gösterilen tüm örnekler burada kodu yürütür makinede dil ve geçerli kültürü kullanarak dizeleri biçimlendirin. Genellikle bir kültürü kullanarak üretilen dize biçiminde gerekebilir.
Bunu yapmak için dize ilişkilendirme tarafından üretilen nesnesi örtük olarak dönüştürülebilir olgu kullanın <xref:System.FormattableString>.

<xref:System.FormattableString> Örnek biçim dizesi ve dizeleri dönüştürme önce ifadeleri değerlendirme sonuçlarını içerir. Ortak yöntemlerini kullanabilirsiniz <xref:System.FormattableString> bir dize biçimlendirme sırasında kültür belirtmek için. Örneğin, aşağıdaki örnekte, Almanca kültürü kullanarak bir dize oluşturur. (İçin ondalık ayırıcı, ',' karakterini kullanır ve '.' karakteri olarak binlik ayırıcı.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Daha fazla bilgi için bkz: [dize ilişkilendirme](../language-reference/tokens/interpolated.md) konu.

## <a name="exception-filters"></a>Özel durum filtreleri

C# 6 başka bir yeni özelliği *özel durum filtreleri*. Özel durum filtreleri verilen catch yan tümcesinin ne zaman uygulanacağını belirleme tümceler var.
Bir özel durum filtresi için kullanılan ifade değerlendiren varsa `true`, catch yan tümcesi, özel durum normal işleme gerçekleştirir. İfade değerlendirilirse `false`, sonra `catch` yan tümcesi atlandı.

Bir kullanım olduğunu belirlemek için bir özel durum bilgilerini incelemek için bir `catch` yan tümcesi, özel durumu işleyebilir:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

Özel durum filtreleri tarafından oluşturulan kodu oluşturulur ve işlenmemiş bir özel durum hakkında daha iyi bilgi sağlar. Özel durum filtreleri diline eklenmeden önce aşağıdaki gibi bir kod oluşturmanız gerekir:

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

Özel değişiklikler bu iki örnek arasında olduğu durum noktası.
Önceki kodda, burada bir `throw` yan tümcesi kullanıldığında, özel durumu, herhangi bir yığın izleme çözümlemesi veya kilitlenme bilgi dökümleri incelenmesi gösterecektir `throw` catch yan tümcesi deyiminde. Gerçek özel durum nesnesi özgün çağrı yığını içerir, ancak bu throw noktası ve özgün throw noktasının konumunu arasında çağrı yığınında tüm değişkenleri hakkında diğer tüm bilgiler kaybolmuş olabilir. 

Bir özel durum filtresi kullanarak kodu nasıl işleneceğini ile karşılaştırın: özel durum filtre ifadesi değerlendiren `false`. Bu nedenle, yürütme hiçbir zaman girer `catch` yan tümcesi. Çünkü `catch` yan tümcesi yürütülmez, hiçbir yığın geriye doğru izleme gerçekleşir. Anlamına gelir özgün konum throw daha sonra gerçekleşmesi hata ayıklama etkinlikler için korunur.

Alanları veya yalnızca özel durum türü üzerinde kalmak yerine bir özel durum özelliklerini değerlendirmek gerektiğinde daha fazla hata ayıklama bilgilerini korumak için bir özel durum filtresi kullanın.

Özel durum filtreleri önerilen başka bir desenle günlük yordamları için bunları kullanmaktır. Bu kullanım da, özel durum throw noktası korunur bir özel durum filtresi olarak değerlendirildiğinde şekilde yararlanır `false`.

Günlüğe kayıt yöntemi, bağımsız değişkeni olan koşulsuz olarak döndüren özel bir yöntem olacaktır `false`:

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

Bir özel durum günlüğe kaydetmek istediğiniz her bir catch yan tümcesi ekleyin ve bu yöntemi özel durum filtre olarak kullanın:

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

Özel durumlar hiçbir zaman, çünkü yakalanan `LogException` yöntem her zaman döndürür `false`. Bu her zaman yanlış özel durum filtresi anlamına gelir, bu günlüğü işleyicisi herhangi bir özel durum işleyicileri önce yerleştirebilirsiniz:

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

Önceki örnekte bir özel durum filtreleri güvenliğin çok önemli vurgular.
Özel durum filtreleri daha genel bir özel durum catch yan tümcesi önce daha belirli bir yere görünebilir senaryoları etkinleştirin. Birden çok catch tümcelerinde yer aynı özel durum türü olması mümkündür:

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

Başka bir önerilen deseni, bir hata ayıklayıcısı ekli özel durumları işleme catch yan tümceleri önlemeye yardımcı olur. Bu teknik hata ayıklayıcısı ile bir uygulamayı çalıştırın ve bir özel durum yakalandığında yürütme durdurmanızı sağlar.

Böylece yalnızca bir hata ayıklayıcısı değil iliştirildiğinde herhangi bir kurtarma kodu yürütür, kodunuzda bir özel durum filtresi ekleyin:

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

Bu kodda ekledikten sonra tüm işlenmeyen özel durumlarını ayırmak için hata ayıklayıcı ayarlayın. Hata ayıklayıcı altında programını çalıştırın ve hata ayıklayıcısı sonları her `PerformFailingOperation()` oluşturur bir `RecoverableException`.
Catch yan tümcesi nedeniyle false döndüren özel durum filtresi yürütülen olmaz çünkü hata ayıklayıcı programınızın keser.

## <a name="nameof-expressions"></a>`nameof` İfadeler

`nameof` Bir simge adı için ifadeyi hesaplar. Bir değişken, bir özellik veya bir üye alanı adını ihtiyaç duyduğunuzda çalışma araçları almak için harika bir yoludur.

En yaygın birini kullanan için `nameof` bir özel duruma neden bir sembol adını sağlar:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Başka bir uygulama temel XAML uygulamaları ile kullanılır `INotifyPropertyChanged` arabirimi:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

Kullanmanın avantajı `nameof` bir sabit dize üzerinden işlecidir araçları simgenin anlayabilirsiniz. Simgenin yeniden adlandırmak için yeniden düzenleme araçları kullanırsanız, içindeki adlandıracak `nameof` ifade. Sabit Dizeler Bu avantajı yok. Sık kullanılan düzenleyicinizde kendiniz deneyin: bir değişken ve herhangi bir yeniden adlandırma `nameof` ifadeler de güncelleştirir.

`nameof` İfade bağımsız değişkeni nitelenmemiş adı üretir (`LastName` önceki örneklerde) dahi bağımsız değişkeni için tam ad kullanın:

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

Bu `nameof` ifade üretir `FirstName`değil `UXComponents.ViewModel.FirstName`.

## <a name="await-in-catch-and-finally-blocks"></a>Catch await ve son olarak engeller

C# 5 vardı nereye geçici bazı sınırlamaları `await` ifadeler.
Bunlardan birini C# 6'kaldırılmıştır. Artık kullanabilirsiniz `await` içinde `catch` veya `finally` ifadeler. 

Eklenmesi await catch ifadelerinde ve finally blokları olanlar nasıl işlendiği karmaşık hale gibi görünebilir. Bu görünme tartışmak için örnek ekleyelim. Herhangi bir zaman uyumsuz yöntem bekleme deyimde kullanabileceğiniz bir finally yan tümcesinin.

C# 6 catch ifadelerinde beklemek. Bu günlük kaydı senaryoları ile en sık kullanılır:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Eklemek için uygulama ayrıntılarını `await` içinde destek `catch` ve `finally` yan tümceleri davranışı zaman uyumlu bir kod davranışını ile tutarlı olmasını sağlar. Ne zaman yürütülen kod içinde bir `catch` veya `finally` yan tümcesi oluşturur, yürütme için uygun bir arar `catch` yan tümcesinde sonraki çevresindeki bloğu. Geçerli bir özel durum varsa, bu özel durum kaybolur. Beklemenin ifadelerinde ile aynı olur `catch` ve `finally` yan tümceleri: uygun bir `catch` , aranır ve varsa, geçerli özel durumun kaybolur.  

> [!NOTE]
> Bu davranış önerilen yazmak için nedeni `catch` ve `finally` yan tümceleri dikkatle, yeni özel durumları önlemek için.

## <a name="index-initializers"></a>Dizin başlatıcıları

*Dizin başlatıcıları* koleksiyon başlatıcıları daha tutarlı hale iki özelliklerinden biridir. Önceki sürümlerinde, C#, kullanabileceğinizi *koleksiyon başlatıcıları* dizisi stili koleksiyonlarıyla yalnızca:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

Şimdi, ayrıca bunları ile kullanabileceğiniz <xref:System.Collections.Generic.Dictionary%602> koleksiyonları ve benzer türleri:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Bu özellik ilişkilendirilebilir kapsayıcıları ne birkaç sürümleri için dizisi kapsayıcıları için yerinde bırakıldı için benzer bir sözdizimi kullanılarak başlatılabilir anlamına gelir.

### <a name="extension-add-methods-in-collection-initializers"></a>Uzantı `Add` koleksiyon başlatıcıları yöntemleri

Kullanma yeteneğini koleksiyonu başlatma kolaylaştırır başka bir özellik olan bir *genişletme yöntemi* için `Add` yöntemi. Bu özellik, Visual Basic ile eşlik için eklenmiştir. 

Bir yöntem anlamsal olarak yeni öğeler eklemek için farklı bir ada sahip olan bir özel koleksiyon sınıfı olduğunda en kullanışlı bir özelliktir.

Örneğin, şöyle Öğrenciler koleksiyonu göz önünde bulundurun:

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

`Enroll` Yöntemi öğrencinin ekler. Ancak bunu IU `Add` düzeni.
Önceki sürümlerde, C# ile koleksiyon başlatıcıları kullanılamadı bir `Enrollment` nesnesi:

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

Artık, ancak yalnızca eşleyen bir genişletme yöntemi oluşturursanız `Add` için `Enroll`:

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

Bu özellik ile yapmakta olduğunuz hangi yöntemi adlı bir yöntem bir koleksiyona öğe ekler eşlemektir `Add` bir genişletme yöntemi oluşturarak: 

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]
[!code-csharp[ExtensionAddSample](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAddSample)]

## <a name="improved-overload-resolution"></a>Geliştirilmiş aşırı yükleme çözümü

Son bu özellik, büyük olasılıkla farkına biridir. C# Derleyici'nın önceki sürümünü lambda ifadeleri belirsiz içeren bazı yöntem çağrılarını bulunduğu yapıları vardı. Bu yöntem göz önünde bulundurun:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

Önceki sürümlerde, C#, yöntemi Grup sözdizimini kullanarak bu yöntem çağırma başarısız olur:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
Önceki derleyici doğru arasında ayrım yapmamak `Task.Run(Action)` ve `Task.Run(Func<Task>())`. Önceki sürümlerde, bağımsız değişken olarak bir lambda ifadesi kullanmanız gerekir:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

C# 6 derleyici doğru belirleyen `Task.Run(Func<Task>())` daha iyi bir seçimdir.
