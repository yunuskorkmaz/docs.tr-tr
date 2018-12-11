---
title: C# 6 - C# Kılavuzu yenilikler nelerdir?
description: C# sürüm 6'daki yeni özelliklerin öğrenin
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: 6aa070d54bb1b571d4fa51538b0521a554073cbc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146751"
---
# <a name="whats-new-in-c-6"></a>C# 6 yenilikleri

C# 6.0 sürüm, geliştiriciler için üretkenliği artıran birçok özellik içeriyor. Bu sürümde aşağıdaki özelliklere sahiptir:

* [Salt okunur otomatik özelliklerde](#read-only-auto-properties):
    - Salt okunur otomatik yalnızca oluşturucularda ayarlanabilen özelliklerde oluşturabilirsiniz.
* [Otomatik-özellik başlatıcıları](#auto-property-initializers):
    - Otomatik özellik başlangıç değeri ayarlamak için başlatma ifadeleri yazabilirsiniz.
* [İfade gövdeli işlev üyeleri](#expression-bodied-function-members):
    - Lambda ifadeleri kullanarak bir satır içi yöntemler yazabilirsiniz.
* [' using static](#using-static):
    - Tek bir sınıfın tüm yöntemler geçerli bir ad alanına içeri aktarabilirsiniz.
* [Null koşullu işleçleri](#null-conditional-operators):
    - Null null koşullu işleci ile hala denetleme sırasında bir nesnenin üyelerine kısaca ve güvenli bir şekilde erişebilir.
* [Dize ilişkilendirme](#string-interpolation):
    - Satır içi ifadeler yerine konumsal bağımsız değişkenlerle ifadeleri biçimlendirme dizesi yazabilirsiniz.
* [Özel durum filtreleri](#exception-filters):
    - İfadeleri özelliklerine göre özel durum veya diğer program durumunu yakalayabilir. 
* [`nameof` İfade](#the-nameof-expression):
    - Semboller dize temsillerini oluşturmak derleyici izin verebilirsiniz.
* [await catch ve finally bloklarında](#await-in-catch-and-finally-blocks):
    - Kullanabileceğiniz `await` ifadeleri önceden izin verilmeyen bir konumda.
* [Dizin başlatıcılar](#index-initializers):
    - Sıra kapsayıcılar yanı sıra, ilişkili kapsayıcılar için başlatma ifadeleri yazabilirsiniz.
* [Koleksiyon başlatıcıları için genişletme yöntemleri](#extension-add-methods-in-collection-initializers):
    - Koleksiyon başlatıcıları, üye yöntemleri yanı sıra erişilebilir genişletme yöntemleri üzerinde güvenebilirsiniz.
* [Geliştirilmiş aşırı yükleme çözünürlüğü](#improved-overload-resolution):
    - Belirsiz yöntem çağrıları artık daha önce oluşturulan bazı yapıları doğru bir şekilde çözün.
* [`deterministic` derleyici seçeneği](#deterministic-compiler-output):
    - Sonraki derlemeleri aynı kaynak aynı ikili çıkışı Oluştur belirleyici derleyici seçeneği sağlar.

Bu özellikler genel etkisini de daha okunabilir daha kısa kod yazma ' dir. Birçok ortak uygulamalar için daha az seremoni söz dizimi içeriyor. Tasarım hedefi ile daha az seremoni görmek daha kolaydır. Bu özellikler de öğrenin ve daha üretken olmanıza, daha okunabilir bir kod yazma ve daha çekirdek özellikleri dil yapıları üzerinde yoğunlaşabilirsiniz.

Bu konunun geri kalanı bu özelliklerin her biri hakkında ayrıntılar sağlar.

## <a name="auto-property-enhancements"></a>Otomatik-özellik geliştirmeleri

Otomatik olarak uygulanan özellikler (genellikle 'otomatik-Özellikler' adlandırılır) sözdizimi kolay, çok basit get olan özellikler oluşturma ve ayarlama erişimci:

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

Ancak, bu basit söz dizimi otomatik özelliklerde kullanarak destekleyebilir tasarımları tür sınırlı. Daha fazla senaryoda kullanmak C# 6 otomatik özelliklerde özellikleri geliştirir. Bildirme ve Destek alanı çoğunlukla el ile düzenleme hakkında daha ayrıntılı sözdizimi dönmesi gerekmez.

Yeni sözdizimi senaryoları için salt okunur özellikler ve değişken depolama otomatik-özellik arkasında başlatma için yer almaktadır.

### <a name="read-only-auto-properties"></a>Salt okunur otomatik özellikleri

*Salt okunur otomatik özelliklerde* değişmez türleri oluşturmak için daha kısa bir söz dizimi sağlar. Özel ayarlayıcılar bildirmek için C# ' ın önceki sürümlerinde sabit türlerine alabilir en yakın şöyleydi:

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
Bu söz dizimini kullanarak derleyicinin türü gerçekten sabit olduğunu garanti etmez. Bu yalnızca, zorlar `FirstName` ve `LastName` sınıf dışındaki herhangi bir kod öğesinden özellikleri değiştirilmez.

Salt okunur otomatik özelliklerde true salt okunur davranışı etkinleştirin. Otomatik özelliği yalnızca bir alma erişimcisi ile bildirdiğiniz:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

`FirstName` Ve `LastName` özellikleri yalnızca Oluşturucu gövdesinde ayarlanabilir:

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

Bu özellik sabit türleri oluşturma ve daha net ve uygun otomatik-özellik söz dizimini kullanarak true dil desteği sağlar.

Bu söz dizimi ekleme erişilebilir bir yöntemi kaldırmazsa olduğu bir [ikili uyumlu değişiklik](version-update-considerations.md#binary-compatible-changes).

### <a name="auto-property-initializers"></a>Otomatik-özellik başlatıcıları

*Otomatik-özellik başlatıcıları* başlangıç değeri otomatik özellik için özellik bildiriminde bir parçası olarak bildirmenize.  Önceki sürümlerde, bu özellikleri ayarlayıcılar olması gerekir ve yedekleme alanı tarafından kullanılan veri depolama alanı başlatmak için ayarlayıcı'ı kullanmanız gerekir. Bu sınıf adı ve öğrencinin derece listesini içeren bir öğrenci için göz önünde bulundurun:

[!code-csharp[Student](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Student)]
 
Bu sınıf büyüdükçe, diğer oluşturucular içerebilir. Her Oluşturucu eğitim verdiğiniz özelliği başlatması gerekiyor veya hatalara neden.

C# 6 otomatik-özellik bildiriminde otomatik-özellik tarafından kullanılan depolama alanı için bir başlangıç değeri atamanızı sağlar:

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` Üyesi olduğu bildirilir başlatılır. Bu, tam bir kez başlatma gerçekleştirmek kolaylaştırır. Başlatma ile ortak arabirim için depolama ayırmayı excel'dir kolaylaştırarak özellik bildiriminde bir parçasıdır `Student` nesneleri.

Özellik başlatıcıları gösterildiği yukarıda ve okuma/yazma özellikleri de, aşağıda gösterildiği gibi salt okunur özellikler ile kullanılabilir.

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a>İfade gövdeli işlev üyeleri

Bir ifade olarak temsil edilebilir yalnızca bir deyim gövdesi çok sayıda biz yazma üyeleri oluşur. Bunun yerine bir ifade gövdeli üye yazarak bu söz dizimini azaltabilir. Bu yöntemler ve salt okunur özellikler için çalışır. Örneğin, bir geçersiz kılma `ToString()` genellikle iyi bir adaydır:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

İfade gövdeli üyeler de salt okunur özellikler de kullanabilirsiniz:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Varolan bir üye ifadesi bodied üyesine değiştirme bir [ikili uyumlu değişiklik](version-update-considerations.md#binary-compatible-changes).


## <a name="using-static"></a>' Using static

*'Using static* geliştirme, tek bir sınıfın statik yöntemleri içeri aktarmanıza olanak sağlar. Daha önce `using` beyanının içeri aktarılıp, bir ad alanındaki tüm türleri. 

Genellikle bir sınıfın statik yöntemleri kodumuz kullanırız. Art arda sınıf adını yazarak kodunuzu anlamını gizlememeniz. Birçok sayısal hesaplamalar sınıfları yazdığınızda yaygın bir örnektir.
Kodunuz ile littered <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> ve diğer çağrılar farklı yöntemlere <xref:System.Math> sınıfı. Yeni `using static` söz dizimi yapabilir bu sınıfların okumak için çok daha net. Kullanmakta olduğunuz sınıfı belirtin:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

Artık, herhangi bir statik yöntemdeki kullanabileceğiniz <xref:System.Math> niteleme olmadan sınıfı <xref:System.Math> sınıfı. <xref:System.Math> Sınıfı, herhangi bir örnek yöntem içermediğinden bu özellik için harika kullanım durumu değildir. Ayrıca `using static` bir sınıfın statik yöntemleri statik bir sınıf için içeri aktarma ve örnek yöntemler. En kullanışlı örneklerden biridir <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Tam nitelikli sınıf adınız kullanmalısınız `System.String` statik olarak using deyimi. Kullanamazsınız `string` anahtar sözcüğü yerine. 

Tanımlanan statik yöntemlerini çağırabilirsiniz <xref:System.String> bu yöntemleri söz konusu sınıfın bir üye olarak niteleme olmadan sınıfı:

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

`static using` Özellik ve uzantı yöntemleri ilginç şekillerde etkileşim ve dil tasarımını, özellikle bu etkileşimlerin bazı kuralları dahil. Varolan önemli değişiklikler herhangi olasılığını en aza indirmek için sizinki de dahil olmak üzere kod tabanlarında hedeftir.

Uzantı yöntemleri yalnızca statik bir yöntem olarak değil çağrıldığında yöntem çağırma söz dizimi uzantısı kullanarak çağrıldığında kapsamına dahildir.
Bu, LINQ sorgularında sık sık görürsünüz. İçeri aktararak LINQ desen aktarabilirsiniz <xref:System.Linq.Enumerable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Bu tüm yöntemleri aktarır <xref:System.Linq.Enumerable> sınıfı.
Ancak, genişletme yöntemleri genişletme yöntemleri çağrıldığında kapsamına dahildir. Statik yöntem sözdizimini kullanarak çağrılır, bunlar kapsamda değildir:

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

Çünkü bu kararı genişletme yöntemleri, genellikle uzantı metodu çağırma ifadeleri kullanılarak çağrılır. Burada statik yöntemi kullanılarak çağrılır nadir durumlarda, söz dizimi belirsizliği olduğu çağırın.
Sınıf adı çağrısının bir parçası olarak gerek akıllıca gibi görünüyor.

Bir son özelliği yoktur `static using`. `static using` Yönergesi, tüm iç içe geçmiş türler de alır. Tüm iç içe geçmiş türler nitelik olmadan başvuru sağlar.

## <a name="null-conditional-operators"></a>Null koşullu işleçleri

Null değerler kod zorlaştırabilir. Değişken değil başvuruluyor emin olmak için her bir erişim denetimi için ihtiyacınız `null`. *Null koşullu işleci* bu denetimleri çok daha kolay ve akıcı hale getirir.

Üye erişimi yalnızca değiştirmek `.` ile `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

Yukarıdaki örnekte, değişken `first` atanan `null` kişi nesnesi varsa `null`. Aksi takdirde, değeri atandığını `FirstName` özelliği. En önemlisi de `?.` Bu kod satırı oluşturmaz anlamına gelir bir `NullReferenceException` olduğunda `person` değişkendir `null`. Bunun yerine, short-circuits ve üretir `null`.

Ayrıca, bu ifade döndürür Not bir `string`değerini bakılmaksızın `person`.
Kestirmeler, söz konusu olduğunda `null` tam ifadeyle eşleşecek döndürülen değerin türü.

Genellikle bu yapı ile kullanabileceğiniz *null birleşim* özelliklerinden olduğunda varsayılan değer atamak için işleç `null`:

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Sağ taraf işleneni `?.` işleci, özellikler veya alanlar için sınırlı değildir.
Koşullu olarak yöntemlerini çağırmak için de kullanabilirsiniz. Temsilciler (veya olay işleyicileri) güvenli bir şekilde çağrılacak üye işlevleri null koşullu işleci ile en yaygın kullanımı olan olabilecek `null`.  Bu temsilcinin çağırarak yaparsınız `Invoke` yöntemi kullanarak `?.` üye erişim işleci. Bir örnek görebilirsiniz.  
[desenler temsilci](../delegates-patterns.md#handling-null-delegates) konu.

Kurallarına `?.` işleci olun işlecinin sol tarafı yalnızca bir kez değerlendirilir. Bu önemlidir ve olay işleyicilerini kullanarak örnek dahil olmak üzere birçok deyimleri sağlar. Olay işleyicisi kullanım ile başlayalım. Önceki sürümlerinde C#, aşağıdakine benzer bir kod yazmak için önerilir:

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
> Yukarıdaki örnekte, bir yarış durumu ortaya çıkarır. `SomethingHappened` Olay karşı işaretlendiğinde aboneleri olabilir `null`, ve olay gerçekleşmeden önce bu aboneleri kaldırılmış olabilir. Bu neden bir <xref:System.NullReferenceException> oluşturulması için.

Bu ikinci sürüm `SomethingHappened` olay işleyicisi, test edildiğinde null olmayan olabilir, ancak diğer kod bir işleyici kaldırırsa, olay işleyicisi çağrıldığında hala null olabilir.

Derleyici için kod oluşturur `?.` sol tarafındaki sağlar işleci (`this.SomethingHappened`), `?.` ifade bir kez değerlendirilir ve sonuç önbelleğe alınır:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Sol tarafta yalnızca bir kez değerlendirilir sağlamak da sol tarafındaki yöntem çağrıları dahil olmak üzere herhangi bir ifade kullanmanıza olanak sağlar `?.` bu yan etkilere sahip olsanız bile, yan etkileri yalnızca bir kez meydana şekilde bunlar bir kez değerlendirilir. Sunduğumuz içeriğin bir örnekte gördüğünüz [olayları](../events-overview.md#language-support-for-events).

## <a name="string-interpolation"></a>Dize ilişkilendirme

C# 6 dizeler dize ve diğer string değerleri oluşturmak için değerlendirilen katıştırılmış ifadeler oluşturmak için yeni sözdizimi içeriyor.

Geleneksel olarak, konumsal parametreler gibi bir yöntem kullanmak için gereken <xref:System.String.Format%2A?displayProperty=nameWithType>:

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

C# 6, yeni [dize ilişkilendirme](../language-reference/tokens/interpolated.md) özellik ifadeleri bir dizeye katıştırmak olanak sağlar. Yalnızca dize ile yazdığınızdan `$`:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Bu örnek özellik ifadeleri için yedek ifadeler kullanır. Herhangi bir ifade kullanmak için bu sözdizimini genişletebilirsiniz. Örneğin, bir öğrencinin sınıf noktası ortalama ilişkilendirme bir parçası olarak işlem:

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

Önceki örnekte çalışan, size, çıktısı bulur `Grades.Average()` istediğiniz çok daha fazla ondalık basamak olabilir. Dize ilişkilendirme sözdizimi tüm biçim dizeleri kullanılabilir daha önce biçimlendirme yöntemleri kullanmayı destekler. Küme ayraçları içinde biçim dizesi belirtin. Ekleme bir `:` biçimlendirmek için ifadeyi aşağıdaki:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Önceki kod satırının değeri biçimlendirir `Grades.Average()` iki ondalık kayan noktalı bir sayı olarak.

`:` Her zaman biçimlendirilen ifade ve biçim dizesi arasındaki ayırıcı olarak yorumlanır. İfadeniz kullandığında bu sorunları ortaya çıkarabilir bir `:` başka bir yolla gibi bir [koşullu işleç](../language-reference/operators/conditional-operator.md):

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

Önceki örnekte `:` koşullu işleç parçası olmayan biçim dizesinin başlangıcı olarak ayrıştırılır. Burada böyle her durumda, parantezli ifade düşündüğünüz olarak yorumlamak üzere zorlamanız ifadeyi çevreler:

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

Küme ayraçları arasında yerleştirebilirsiniz ifadeleri herhangi bir sınırlama yok. Hesaplamaları gerçekleştirmek ve sonucu görüntülemek için bir aradeğerlendirme dizesinde içinde karmaşık bir LINQ Sorgu yürütebilirsiniz:

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

Bu örnekten başka bir dize ilişkilendirme ifadesi bir dize ilişkilendirme ifadesinde bile yuvalayabilirsiniz görebilirsiniz. Bu örnek daha daha karmaşık üretim kodunda istersiniz olasılıktır.
Bunun yerine, bu özelliğin kapsamını yalnızca tanım olur. Herhangi bir C# deyimi, bir aradeğerlendirme dizesinde arasında ve küme ayraçlarının yerleştirilebilir.

Dize ilişkilendirme ile çalışmaya başlamak için denetleme [dize ilişkilendirme, C# ](../tutorials/intro-to-csharp/interpolated-strings.yml) etkileşimli öğretici.

### <a name="string-interpolation-and-specific-cultures"></a>Dize ilişkilendirme ve özel kültürler

Tüm örnekleri burada kodu yürütür makine üzerinde geçerli kültürü kullanarak dizeleri önceki bölümde biçiminde gösterilir. Genellikle belirli bir kültür kullanılarak üretilen dize biçimlendirmeniz gerekebilir.
Yapmak için bir dize ilişkilendirme tarafından üretilen nesne için örtük olarak dönüştürülebilir olgu kullanan <xref:System.FormattableString?displayProperty=nameWithType>.

<xref:System.FormattableString> Örneği bileşik biçimlendirme dizesi ve dizeleri için dönüştürme önce ifadeleri değerlendirme sonuçlarını içerir. Kullanım <xref:System.FormattableString.ToString(System.IFormatProvider)> kültür biçimlendirme dizesi bir zaman belirtmek için yöntemi. Örneğin, aşağıdaki örnekte, Alman kültürü kullanarak bir dize oluşturur. (',' Karakteri ondalık ayırıcısı için kullanır ve '.' karakteri olarak binlik ayırıcı.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Daha fazla bilgi için [dize ilişkilendirme](../language-reference/tokens/interpolated.md) makale ve [dize ilişkilendirme C#](../tutorials/string-interpolation.md) öğretici.

## <a name="exception-filters"></a>Özel durum filtreleri

Başka bir yeni özelliktir C# 6 *özel durum filtreleri*. Özel durum, belirli bir catch yan tümcesinin ne zaman uygulanacağını belirleme yan tümceleri filtrelerdir.
Bir özel durum filtresi için kullanılan ifade olmaması halinde `true`, catch yan tümcesi, bir özel normal işleme gerçekleştirir. İfade değerlendirme sonucu `false`, ardından `catch` yan tümcesi atlandı.

Bir kullanım olup olmadığını belirlemek için bir özel durum hakkında bilgileri incelemek için bir `catch` yan tümcesi, özel durumu işleyebilir:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

Özel durum filtreleri tarafından oluşturulan kodu oluşturulur ve işlenmemiş bir özel durum hakkında bilgi sağlar. Dile özel durum filtreleri eklenmeden önce aşağıdaki gibi bir kod oluşturmak için ihtiyacınız:

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

Burada bu iki örnek arasındaki değişiklikleri özel durum noktası.
Önceki kodda, burada bir `throw` yan tümcesi kullanıldığında, herhangi bir yığın izleme analiz veya kilitlenme bilgi dökümleri incelenmesi öğesinden özel durumun oluştuğu gösterecektir `throw` deyiminde, catch yan tümcesi. Gerçek özel durum nesnesi orijinal çağrı yığını içerir, ancak bu throw noktası özgün throw noktasının konumunu arasındaki çağrı yığınındaki tüm değişkenler hakkında diğer tüm bilgi kaybı olmadı. 

Özel durum filtresi kullanarak kodu nasıl işleneceği ile karşılaştırın: özel durum filtresi ifadesi olarak değerlendirilen `false`. Bu nedenle, hiçbir zaman yürütme aşamasına girer `catch` yan tümcesi. Çünkü `catch` yan tümcesi yürütülmez, hiçbir yığın geriye doğru izleme gerçekleşir. Yol özgün konum throw daha sonra gerçekleşmesi hata ayıklama etkinlikler için korunur.

Alanlar ve özellikler, yalnızca özel durum türü üzerinde kalmak yerine bir özel durumun değerlendirmek gerektiğinde daha fazla hata ayıklama bilgileri korumak için bir özel durum filtresi kullanın.

Özel durum filtreleri ile başka bir önerilen düzen, bunları için günlük rutinleri kullanmaktır. Bu kullanım, özel durum throw noktası korunur bir özel durum filtresi sonucunu verdiğinde bir şekilde de yararlanır `false`.

Günlüğe kayıt yöntemi, bağımsız değişken olan koşulsuz olarak döndüren özel bir yöntem olacaktır `false`:

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

Bir özel durum günlüğe kaydetmek istediğiniz her bir catch yan tümcesi ekleyin ve özel durum filtre olarak bu yöntemi kullanın:

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

Özel durumları hiçbir zaman, çünkü yakalanan `LogException` yöntemi her zaman döndürür `false`. Bu her zaman false özel durum filtresi anlamına gelir, bu günlüğü işleyicisi önce herhangi bir özel durum işleyiciler koyabilirsiniz:

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

Yukarıdaki örnekte, bir özel durum filtreleri güvenliğin çok önemli vurgular.
Özel durum filtreleri daha genel bir özel durum catch yan tümcesi önce daha belirli bir yeri görünebilir senaryolara olanak tanır. Birden çok catch yan tümcelerinde yer aynı özel durum türü olması mümkündür:

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

Başka bir önerilen Düzen catch yan tümceleri bir hata ayıklayıcı eklendiğinde özel durumları işleme engeller. Bu teknik, hata ayıklayıcısı ile bir uygulamayı çalıştırmak ve bir özel durum oluştuğunda yürütmeyi durdurmak sağlar.

Yalnızca bir hata ayıklayıcısı iliştirilmemiş olduğunda herhangi bir kurtarma kodu yürütür, böylece kodunuza, bir özel durum filtresi ekleyin:

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

Bu kodu ekledikten sonra tüm işlenmemiş özel durumlarda kesin, hata ayıklayıcının ayarlayın. Hata ayıklayıcısı altında programı çalıştırın ve hata ayıklayıcı keser her `PerformFailingOperation()` oluşturur bir `RecoverableException`.
Catch yan tümcesi false döndüren özel durum filtresi nedeniyle yürütülen gerekmez çünkü hata ayıklayıcı, programınızın keser.

## <a name="the-nameof-expression"></a>`nameof` İfadesi

`nameof` Bir sembol adı için ifadeyi hesaplar. Her bir değişken, bir özellik veya üye alan adını ihtiyaç duyduğunuzda çalışma araçları almak için harika bir yoludur.

En yaygın birini kullanan için `nameof` bir özel durum nedeniyle bir sembol adını sağlar:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Başka bir uygulama XAML tabanlı uygulamalar ile kullanılır `INotifyPropertyChanged` arabirimi:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

Kullanmanın avantajı `nameof` işleci bir sabit dize üzerinden, araçları sembol anlayabilirsiniz. Sembolü yeniden adlandır için yeniden düzenleme araçları kullanırsanız, içindeki adlandıracak `nameof` ifade. Sabit dizelerini, bu avantajı yoktur. Sık kullandığınız düzenleyicinizde kendiniz deneyin: bir değişkeni veya herhangi bir yeniden adlandırma `nameof` ifadeleri de güncelleştirir.

`nameof` İfade bağımsız değişkenini nitelenmemiş adı üretir (`LastName` önceki örneklerde) tam adı bağımsız değişkeni için kullanıyor olsanız bile:

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

Bu `nameof` ifade üretir `FirstName`değil `UXComponents.ViewModel.FirstName`.

## <a name="await-in-catch-and-finally-blocks"></a>Await catch ve Finally bloklarında

C# 5 vardı yerleştirdiğiniz etrafında bazı sınırlamaları `await` ifadeler.
Bunlardan biri, C# 6'da kaldırılmıştır. Artık `await` içinde `catch` veya `finally` ifadeler. 

Ek await ifadeleri catch ve blokları son olarak bunları nasıl işlendiği karmaşık görünebilir. Bunun nasıl göründüğünü tartışmak için örnek ekleyelim. Herhangi bir zaman uyumsuz yöntemdeki bir await ifadesine kullanabileceğiniz bir finally yan tümcesi.

C# 6 ile catch ifadelerinde await. Bu, genellikle günlük kaydı senaryoları ile kullanılır:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Uygulama ayrıntılarını ekleme `await` içinde destek `catch` ve `finally` yan tümceleri davranışı eş zamanlı kod davranışı ile tutarlı olmasını sağlar. Ne zaman yürütülen kod içinde bir `catch` veya `finally` yan tümcesi oluşturmaz, yürütme için uygun görünüyor `catch` yan tümcesinde sonraki çevreleyen bloğu. Geçerli bir özel durum varsa, bu özel durum kaybolur. Beklenen ifadelerinde ile aynı olur `catch` ve `finally` yan tümceleri: uygun bir `catch` , aranır ve varsa, geçerli özel durumun kaybolur.  

> [!NOTE]
> Bu, davranıştır yazmak için önerilir nedeni `catch` ve `finally` yan tümceleri dikkatli bir şekilde, yeni özel durumlar önlemek için.

## <a name="index-initializers"></a>Dizin başlatıcılar

*Dizin başlatıcılar* koleksiyon başlatıcıları dizin kullanımı ile daha tutarlı hale getirmek iki özelliklerinden biridir. Önceki sürümlerinde, C#, kullanabileceğinizi *koleksiyon başlatıcıları* koleksiyonlarıyla da dahil olmak üzere yalnızca dizisi stili, <xref:System.Collections.Generic.Dictionary%602> anahtar ve değer çiftlerini etrafında ayraç ekleyerek:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

Şimdi ile kullanabilmek için <xref:System.Collections.Generic.Dictionary%602> koleksiyonları ve benzer türleri. Yeni söz dizimini kullanarak koleksiyona bir dizin atama destekler:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Bu özellik, ilişkili kapsayıcılar dizisi kapsayıcıları çeşitli sürümleri için yerinde çürütülen için benzer bir sözdizimi kullanılarak başlatılabilir anlamına gelir.

## <a name="extension-add-methods-in-collection-initializers"></a>Uzantı `Add` koleksiyon başlatıcıları yöntemleri

Toplama başlatma kolaylaştırır başka bir özellik kullanma yeteneğini olduğu bir *genişletme yöntemi* için `Add` yöntemi. Bu özellik, Visual Basic ile eşlik için eklendi. 

Anlamsal olarak yeni öğeler eklemek için farklı bir ada sahip bir yöntemi olan bir özel koleksiyon sınıfı varsa, en yararlı bir özelliktir.

Örneğin, bu gibi öğrencilere koleksiyonunu göz önünde bulundurun:

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

`Enroll` Yöntemi bir öğrenci ekler. Ancak izleyin değil `Add` deseni.
Önceki sürümlerinde C#, koleksiyon başlatıcıları kullanılamadı bir `Enrollment` nesnesi:

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

Artık, ancak yalnızca eşleyen bir genişletme yöntemi oluşturursanız `Add` için `Enroll`:

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

Bu özellik ile neler yaptığına yöntem öğeleri bir koleksiyona adlı bir yöntem ekler eşlemektir `Add` bir genişletme yöntemi yaratarak.

## <a name="improved-overload-resolution"></a>Geliştirilmiş aşırı yükleme çözünürlüğü

Son bu özellik, büyük olasılıkla fark olmaz biridir. C# derleyicisinin önceki sürümünü içeren lambda ifadeleri belirsiz bazı yöntem çağrıları bulunduğu yapıları vardı. Bu yöntem göz önünde bulundurun:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

Önceki sürümlerde, C#, yöntem grubu söz dizimini kullanarak bu yöntemini çağırmak başarısız olur:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
Önceki derleyici doğru arasında ayrım değil `Task.Run(Action)` ve `Task.Run(Func<Task>())`. Önceki sürümlerinde, bir lambda ifadesi bağımsız değişken olarak kullanması gerekir:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

C# 6 derleyici doğru belirleyen `Task.Run(Func<Task>())` daha iyi bir seçimdir.

### <a name="deterministic-compiler-output"></a>Belirleyici derleyici çıkışı

`-deterministic` Bayt için aynı çıkış derlemesi için aynı kaynak dosyaları art arda gelen derlemesi üretmek için derleyici seçeneği bildirir.

Varsayılan olarak, her derleme her derleme üzerinde benzersiz bir çıktı üretir. Derleyici bir zaman damgası ekler ve rastgele sayı bir GUID oluşturulur. İçin-derlemeler arasında tutarlılık sağlamak için çıkış bayt karşılaştırmak istiyorsanız bu seçeneği kullanın.

Daha fazla bilgi için [-belirleyici derleyici seçeneği](../language-reference/compiler-options/deterministic-compiler-option.md) makalesi.
