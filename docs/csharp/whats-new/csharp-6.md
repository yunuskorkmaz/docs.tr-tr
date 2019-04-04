---
title: C# 6 - C# Kılavuzu yenilikler nelerdir?
description: C# sürüm 6'daki yeni özelliklerin öğrenin
ms.date: 12/12/2018
ms.openlocfilehash: 478fd512f6b6facfce6d7f70f9691ce15e418d6e
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920681"
---
# <a name="whats-new-in-c-6"></a>C# 6 yenilikleri

C# 6.0 sürüm, geliştiriciler için üretkenliği artıran birçok özellik içeriyor. Bu özellikler genel etkisini de daha okunabilir daha kısa kod yazma ' dir. Birçok ortak uygulamalar için daha az seremoni söz dizimi içeriyor. Tasarım hedefi ile daha az seremoni görmek daha kolaydır. Bu özellikler de öğrenin ve daha üretken ve daha okunabilir bir kod yazma. Daha özellikleri dil yapıları üzerinde odaklanabilirsiniz.

Bu makalenin geri kalanında her bir özellik keşfetmek için bir bağlantı ile bu özelliklerin her biri bir bakış sağlar. Özellikleri da keşfedebilirsiniz bir [üzerinde etkileşimli incelenmesi C# 6](../tutorials/exploration/csharp-6.yml) öğreticiler bölümünde.

## <a name="read-only-auto-properties"></a>Salt okunur otomatik özellikleri

*Salt okunur otomatik özelliklerde* değişmez türleri oluşturmak için daha kısa bir söz dizimi sağlar. Otomatik özelliği yalnızca bir alma erişimcisi ile bildirdiğiniz:

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

Bu özellik sabit türleri oluşturmak için true dil desteği sağlar ve daha net ve uygun otomatik-özellik söz dizimini kullanır.

Bu sözdizimi, erişilebilir bir yöntemi kaldırmaz ekleme, eğer ise bir [ikili uyumlu değişiklik](version-update-considerations.md#binary-compatible-changes).

## <a name="auto-property-initializers"></a>Otomatik-özellik başlatıcıları

*Otomatik-özellik başlatıcıları* başlangıç değeri otomatik özellik için özellik bildiriminde bir parçası olarak bildirmenize.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` Üyesi olduğu bildirilir başlatılır. Bu, tam bir kez başlatma gerçekleştirmek kolaylaştırır. Başlatma ile ortak arabirim için depolama ayırmayı excel'dir kolaylaştırarak özellik bildiriminde bir parçasıdır `Student` nesneleri.

## <a name="expression-bodied-function-members"></a>İfade gövdeli işlev üyeleri

Yazdığınız birçok tek ifadeleri olabilecek tek deyimler üyeleridir. Bunun yerine bir ifade gövdeli üye yazın. Bu yöntemler ve salt okunur özellikler için çalışır. Örneğin, bir geçersiz kılma `ToString()` genellikle iyi bir adaydır:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Salt okunur özellikler için de bu söz dizimini kullanabilirsiniz:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Varolan bir üye ifadesi bodied üyesine değiştirme bir [ikili uyumlu değişiklik](version-update-considerations.md#binary-compatible-changes).

## <a name="using-static"></a>' Using static

*'Using static* geliştirme, tek bir sınıfın statik yöntemleri içeri aktarmanıza olanak sağlar. Kullanmakta olduğunuz sınıfı belirtin:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<xref:System.Math> Herhangi bir örnek yöntem içermiyor. Ayrıca `using static` bir sınıfın statik yöntemleri statik bir sınıf için içeri aktarma ve örnek yöntemler. En kullanışlı örneklerden biridir <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Tam nitelikli sınıf adınız kullanmalısınız `System.String` statik olarak using deyimi.  Kullanamazsınız `string` anahtar sözcüğü yerine.

İçeri aktarılan olduğunda bir `static using` deyimi, genişletme yöntemleri olan uzantı metodu çağırma söz dizimi kullanılarak çağrıldığında yalnızca kapsam. Bir statik yöntem olarak çağrıldığında kapsamında değildir. Bu, LINQ sorgularında sık sık görürsünüz. İçeri aktararak LINQ desen aktarabilirsiniz <xref:System.Linq.Enumerable>, veya <xref:System.Linq.Queryable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Genellikle uzantı metodu çağırma ifadeleri kullanarak genişletme yöntemlerini çağırırsınız. Sınıf adı çağırdığınız bunları nadir durumlarda ekleme söz dizimi çözümler belirsizlik statik yöntem çağrısı.

`static using` Yönergesi, tüm iç içe geçmiş türler de alır. Nitelik olmadan tüm iç içe geçmiş türler başvurabilirsiniz.

## <a name="null-conditional-operators"></a>Null koşullu işleçleri

*Null koşullu işleci* null denetimleri çok daha kolay ve akıcı hale getirir. Üye erişimi yerine `.` ile `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

Yukarıdaki örnekte, değişken `first` atanan `null` kişi nesnesi varsa `null`. Aksi takdirde, değeri atanır `FirstName` özelliği. En önemlisi de `?.` Bu kod satırı oluşturmadığını anlamına gelir bir `NullReferenceException` varsa `person` değişkendir `null`. Bunun yerine, short-circuits ve döndürür `null`. Null koşullu bir işleç dizi ya da dizin oluşturucu erişimi için de kullanabilirsiniz. Değiştirin `[]` ile `?[]` Dizin ifadesi içinde.

Aşağıdaki ifade döndürür bir `string`değerini bakılmaksızın `person`. Bu yapı ile kullandığınız *null birleşim* varsayılan atamak için işleç değerleri özelliklerinden olduğunda `null`. Ne zaman ifade short-circuits, `null` tam ifadeyle eşleşecek döndürülen değerin türü.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Ayrıca `?.` koşullu olarak yöntemlerini çağırmak için. Temsilciler (veya olay işleyicileri) güvenli bir şekilde çağrılacak üye işlevleri null koşullu işleci ile en yaygın kullanımı olan olabilecek `null`.  Temsilcinin ararız `Invoke` yöntemi kullanarak `?.` üye erişim işleci. Bir örnekte gördüğünüz [temsilci desenleri](../delegates-patterns.md#handling-null-delegates) makalesi.

Kurallarına `?.` işleci olun işlecinin sol tarafı yalnızca bir kez değerlendirilir. Bu olay işleyicilerini kullanarak aşağıdaki örnekte de dahil olmak üzere birçok deyimleri sağlar:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Sol tarafta yalnızca bir kez değerlendirilir sağlamak da sol tarafındaki yöntem çağrıları dahil olmak üzere herhangi bir ifade kullanmanıza olanak sağlar `?.`

## <a name="string-interpolation"></a>Dize ilişkilendirme

İle C# 6, yeni [dize ilişkilendirme](../language-reference/tokens/interpolated.md) özellik ifadeleri bir dizeye katıştırmak olanak sağlar. Yalnızca dize ile yazdığınızdan `$`ve ifadeler arasında `{` ve `}` sıra sayıları yerine:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Bu örnek için yedek ifadeleri özelliklerini kullanır. Herhangi bir ifade kullanabilirsiniz. Örneğin, bir öğrencinin sınıf noktası ortalama ilişkilendirme bir parçası olarak işlem:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Önceki kod satırının değeri biçimlendirir `Grades.Average()` iki ondalık kayan noktalı bir sayı olarak.

Genellikle, belirli bir kültür kullanılarak üretilen dize biçimlendirmeniz gerekebilir. Bir dize ilişkilendirme tarafından üretilen nesne için örtük olarak dönüştürülebilir olgu kullandığınız <xref:System.FormattableString?displayProperty=nameWithType>. <xref:System.FormattableString> Örneği bileşik biçimlendirme dizesi ve dizeleri için dönüştürme önce ifadeleri değerlendirme sonuçlarını içerir. Kullanım <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> kültür biçimlendirme dizesi bir zaman belirtmek için yöntemi. Aşağıdaki örnek, Almanca (de-DE) kültürü kullanarak bir dize oluşturur. (Varsayılan olarak, Alman kullanılan kültür ',' karakteri ondalık ayırıcısı için kullanır ve '.' karakteri olarak binlik ayırıcı.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Dize ilişkilendirme ile çalışmaya başlamak için bkz. [dize ilişkilendirme, C# ](../tutorials/exploration/interpolated-strings.yml) etkileşimli öğreticisini [dize ilişkilendirme](../language-reference/tokens/interpolated.md) makalenin ve [dize ilişkilendirme C# ](../tutorials/string-interpolation.md) öğretici.

## <a name="exception-filters"></a>Özel durum filtreleri

*Özel durum filtreleri* belirli bir catch yan tümcesinin ne zaman uygulanacağını belirleme yan tümceleri olan. Bir özel durum filtresi için kullanılan ifade olmaması halinde `true`, catch yan tümcesi, bir özel normal işleme gerçekleştirir. İfade değerlendirme sonucu `false`, ardından `catch` yan tümcesi atlandı. Bir kullanım olup olmadığını belirlemek için bir özel durum hakkında bilgileri incelemek için bir `catch` yan tümcesi, özel durumu işleyebilir:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>`nameof` İfadesi

`nameof` Bir sembol adı için ifadeyi hesaplar. Her bir değişken, bir özellik veya üye alan adını ihtiyaç duyduğunuzda çalışma araçları almak için harika bir yoludur. En yaygın birini kullanan için `nameof` bir özel durum nedeniyle bir sembol adını sağlar:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Başka bir uygulama XAML tabanlı uygulamalar ile kullanılır `INotifyPropertyChanged` arabirimi:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Await catch ve Finally bloklarında

C# 5 vardı yerleştirdiğiniz etrafında bazı sınırlamaları `await` ifadeler. İle C# 6, hemen kullanabileceğiniz `await` içinde `catch` veya `finally` ifadeler. Bu, genellikle günlük kaydı senaryoları ile kullanılır:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Uygulama ayrıntılarını ekleme `await` içinde destek `catch` ve `finally` yan tümceleri, davranışı davranış eş zamanlı kod için tutarlı olduğundan emin olun. Ne zaman yürütülen kod içinde bir `catch` veya `finally` yan tümcesi oluşturmaz, yürütme için uygun görünüyor `catch` yan tümcesinde sonraki çevreleyen bloğu. Geçerli bir özel durum varsa, bu özel durum kaybolur. Beklenen ifadelerinde ile aynı olur `catch` ve `finally` yan tümceleri: uygun bir `catch` , aranır ve varsa, geçerli özel durumun kaybolur.  

> [!NOTE]
> Bu, davranıştır yazmak için önerilir nedeni `catch` ve `finally` yan tümceleri dikkatli bir şekilde, yeni özel durumlar önlemek için.

## <a name="initialize-associative-collections-using-indexers"></a>İlişkili koleksiyonlar dizin oluşturucuları kullanarak başlatma

*Dizin başlatıcılar* koleksiyon başlatıcıları dizin kullanımı ile daha tutarlı hale getirmek iki özelliklerinden biridir. Önceki sürümlerinde C#, kullanabileceğinizi *koleksiyon başlatıcıları* dizisi stili koleksiyonlarıyla da dahil olmak üzere, <xref:System.Collections.Generic.Dictionary%602>, ile küme ayraçları anahtarı geçici bir çözüm ekleme ve değer çiftlerini:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Bunları ile kullanabileceğiniz <xref:System.Collections.Generic.Dictionary%602> koleksiyonlar ve diğer türleri nerede erişilebilir `Add` yöntemi, birden fazla bağımsız değişken kabul eder. Yeni söz dizimini kullanarak koleksiyona bir dizin atama destekler:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Bu özellik, ilişkili kapsayıcılar dizisi kapsayıcıları çeşitli sürümleri için yerinde çürütülen için benzer bir sözdizimi kullanılarak başlatılabilir anlamına gelir.

## <a name="extension-add-methods-in-collection-initializers"></a>Uzantı `Add` koleksiyon başlatıcıları yöntemleri

Toplama başlatma kolaylaştırır başka bir özellik kullanma yeteneğini olduğu bir *genişletme yöntemi* için `Add` yöntemi. Bu özellik, Visual Basic ile eşlik için eklendi. Anlamsal olarak yeni öğeler eklemek için farklı bir ada sahip bir yöntemi olan bir özel koleksiyon sınıfı varsa, en yararlı bir özelliktir.

## <a name="improved-overload-resolution"></a>Geliştirilmiş aşırı yükleme çözünürlüğü

Son bu özellik, büyük olasılıkla fark olmaz biridir. C# derleyicisinin önceki sürümünü içeren lambda ifadeleri belirsiz bazı yöntem çağrıları bulunduğu yapıları vardı. Bu yöntem göz önünde bulundurun:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

Önceki sürümlerde, C#, yöntem grubu söz dizimini kullanarak bu yöntemini çağırmak başarısız olur:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

Önceki derleyici doğru arasında ayrım uygulanamadı `Task.Run(Action)` ve `Task.Run(Func<Task>())`. Önceki sürümlerinde, bir lambda ifadesi bağımsız değişken olarak kullanması gerekir:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

C# 6 derleyici doğru belirleyen `Task.Run(Func<Task>())` daha iyi bir seçimdir.

### <a name="deterministic-compiler-output"></a>Belirleyici derleyici çıkışı

`-deterministic` Bayt için aynı çıkış derlemesi için aynı kaynak dosyaları art arda gelen derlemesi üretmek için derleyici seçeneği bildirir.

Varsayılan olarak, her derleme her derleme üzerinde benzersiz bir çıktı üretir. Derleyici bir zaman damgası ekler ve rastgele sayı bir GUID oluşturulur. İçin-derlemeler arasında tutarlılık sağlamak için çıkış bayt karşılaştırmak istiyorsanız bu seçeneği kullanın.

Daha fazla bilgi için [-belirleyici derleyici seçeneği](../language-reference/compiler-options/deterministic-compiler-option.md) makalesi.
