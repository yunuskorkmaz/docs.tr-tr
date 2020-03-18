---
title: C# 6'da Yenilikler - C# Rehberi
description: C# Sürüm 6'daki yeni özellikleri öğrenin
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399394"
---
# <a name="whats-new-in-c-6"></a>C# 6'daki Yenilikler

C#'ın 6.0 sürümü, geliştiriciler için üretkenliği artıran birçok özellik içeriyordu. Bu özelliklerin genel etkisi, aynı zamanda daha okunabilir daha kısa kod yazmak olduğunu. Sözdizimi birçok yaygın uygulamalar için daha az tören içerir. Daha az törenle tasarım niyetini görmek daha kolaydır. Bu özellikleri iyi öğrenin ve daha üretken olun ve daha okunabilir kodlar yazın. Dilin yapısından çok özelliklerinize odaklanabilirsiniz.

Bu makalenin geri kalanı, her özelliği keşfetmek için bir bağlantı ile, bu özelliklerin her biri genel bir bakış sağlar. Ayrıca, [c# 6'daki etkileşimli](../tutorials/exploration/csharp-6.yml) bir keşifte, öğreticiler bölümündeki özellikleri de keşfedebilirsiniz.

## <a name="read-only-auto-properties"></a>Salt okunur otomatik özellikler

*Yalnızca okunur otomatik özellikler,* değişmez türler oluşturmak için daha kısa bir sözdizimi sağlar. Otomatik özelliği yalnızca bir erişime sahip olarak bildirirsiniz:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

Ve `FirstName` `LastName` özellikleri yalnızca aynı sınıfın oluşturucusu gövdesinde ayarlanabilir:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Başka bir `LastName` yöntemde ayarlanmayı denemek bir `CS0200` derleme hatası oluşturur:

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

Bu özellik, değişmez türleri oluşturmak için gerçek dil desteği sağlar ve daha kısa ve kullanışlı otomatik özellik sözdizimini kullanır.

Bu sözdizimini eklemek erişilebilir bir yöntemi kaldırmazsa, ikili uyumlu bir [değişikliktir.](version-update-considerations.md#binary-compatible-changes)

## <a name="auto-property-initializers"></a>Otomatik özellik başlangıç layıcıları

*Otomatik özellik baş harfleri,* bir otomatik mülkün başlangıç değerini özellik bildiriminin bir parçası olarak beyan etmenize izin verebiliyor.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` Üye, beyan edildiği yerde paraya yatırılır. Bu, başlatmayı tam olarak bir kez gerçekleştirmeyi kolaylaştırır. Başlatma özelliği bildiriminin bir parçasıdır, bu da depolama ayırmasını nesneler için `Student` ortak arabirimle eşitlemesini kolaylaştırır.

## <a name="expression-bodied-function-members"></a>İfade gövdeli işlev üyeleri

Yazdığınız birçok üye, tek ifadeler olabilecek tek ifadelerdir. Bunun yerine ifade gövdeli bir üye yazın. Yöntemler ve salt okunur özellikler için çalışır. Örneğin, geçersiz kılma `ToString()` genellikle büyük bir adaydır:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Salt okunur özellikler için bu sözdizimini de kullanabilirsiniz:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Varolan bir üyeyi ifade gövdeli bir üyeye değiştirmek ikili uyumlu bir [değişikliktir.](version-update-considerations.md#binary-compatible-changes)

## <a name="using-static"></a>statik kullanarak

*Statik geliştirmeyi kullanma,* tek bir sınıfın statik yöntemlerini içe aktarmanızı sağlar. Kullandığınız sınıfı belirtin:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

Herhangi <xref:System.Math> bir örnek yöntemi içermez. Hem statik `using static` hem de örnek yöntemleri olan bir sınıf için sınıfın statik yöntemlerini almak için de kullanabilirsiniz. En yararlı örneklerden <xref:System.String>biri:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Tam nitelikli sınıf adını statik `System.String` bir şekilde kullanmanız gerekir.  Bunun yerine `string` anahtar sözcüğü kullanamazsınız.

Bir `static using` deyimden aktarıldığında, uzantı yöntemi sözdizimi kullanılarak çağrıldığında uzantı yöntemleri yalnızca kapsamdadır. Statik bir yöntem olarak çağrıldığında kapsam içinde değildirler. Bunu sık sık LINQ sorgularında görürsünüz. Linq deseni içe aktararak <xref:System.Linq.Enumerable>veya <xref:System.Linq.Queryable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Uzantı yöntemi çağırma ifadelerini kullanarak genellikle uzantı yöntemlerini çağırırsınız. Statik yöntem kullanarak onları aramak nadir durumda sınıf adı ekleme sözdizimi çağrı belirsizliği giderir.

Yönerge `static using` ayrıca iç içe herhangi bir türü de içeri iter. Nitelik olmadan iç içe herhangi bir tür başvuru yapabilirsiniz.

## <a name="null-conditional-operators"></a>Null koşullu işleçler

*Null koşullu işleç* null kontrolleri çok daha kolay ve akışkan hale getirir. Üye erişimini `.` aşağıdakilerle değiştirin: `?.`

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

Önceki örnekte, `first` `null` kişi nesnesi `null`. Aksi takdirde, `FirstName` özelliğin değeri atanır. En önemlisi, `?.` bu kod satırı `person` değişkeni ise `null` `NullReferenceException` bir oluşturmaz anlamına gelir. Bunun yerine, kısa devreler `null`ve döner. Dizi veya dizinleyici erişimi için null koşullu işleci de kullanabilirsiniz. Dizin `?[]` ifadesinde değiştirin. `[]`

Aşağıdaki ifade, `string`değerine bakılmaksızın bir `person`döndürür. Bu yapıyı genellikle *null coalescing* işleci ile birlikte kullanırsınız, `null`özelliklerden biri . İfade kısa devreyaptığında, döndürülen `null` değer tam ifadeyle eşleşecek şekilde yazılır.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Yöntemleri koşullu `?.` olarak çağırmak için de kullanabilirsiniz. Null koşullu işleç ile üye işlevlerin en yaygın kullanımı güvenli bir şekilde temsilcileri çağırmak `null`için (veya olay işleyicileri) olabilir .  Üyeye erişmek için `Invoke` `?.` işleci kullanarak temsilcinin yöntemini ararsınız. [Temsilci desenleri](../delegates-patterns.md#handling-null-delegates) makalesinde bir örnek görebilirsiniz.

İşleticinin `?.` kuralları, işlecinin sol tarafının yalnızca bir kez değerlendirilmesini sağlar. Olay işleyicileri kullanarak aşağıdaki örnek de dahil olmak üzere birçok deyimsağlar:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Sol tarafın sadece bir kez değerlendirilmesini sağlamak, yöntem aramaları da dahil olmak üzere, sol taraftaki herhangi bir ifadeyi`?.`

## <a name="string-interpolation"></a>Dize ilişkilendirme

C# 6 ile yeni [dize enterpolasyon](../language-reference/tokens/interpolated.md) özelliği ifadeleri bir dize ye gömmenizi sağlar. Yalnızca dize ile `$`önsöz ve `{` `}` yerine ordinals arasında ifadeler kullanın:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Bu örnek, değiştirilen ifadeler için özellikler kullanır. Herhangi bir ifade kullanabilirsiniz. Örneğin, bir öğrencinin not ortalamasını enterpolasyonun bir parçası olarak hesaplayabilirsiniz:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Önceki kod satırı, iki ondalık basamakla kayan nokta sayısı `Grades.Average()` olarak değeri biçimlendirin.

Genellikle, belirli bir kültür kullanılarak üretilen dize biçimlendirmeniz gerekebilir. Bir dize enterpolasyonu tarafından üretilen nesnenin örtülü olarak <xref:System.FormattableString?displayProperty=nameWithType>.'e dönüştürülebileceği gerçeğini kullanırsınız. Örnek, <xref:System.FormattableString> bileşik biçim dizesi ve dizeleri dönüştürmeden önce ifadeleri değerlendirme sonuçlarını içerir. Bir <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> dize biçimlendirirken kültürü belirtmek için yöntemi kullanın. Aşağıdaki örnek, Almanca (de-DE) kültürünü kullanarak bir dize üretir. (Varsayılan olarak, Alman kültürü ondalık ayırıcı için ',' karakterini ve binlerce ayırıcı olarak '.' karakterini kullanır.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

String enterpolasyonuile başlamak için C# etkileşimli [öğreticideki String enterpolasyonunu,](../tutorials/exploration/interpolated-strings.yml) [String enterpolasyon](../language-reference/tokens/interpolated.md) makalesini ve [C# öğreticisinde String enterpolasyonunu](../tutorials/string-interpolation.md) görün.

## <a name="exception-filters"></a>Özel durum filtreleri

*Özel Durum Filtreleri,* belirli bir yakalama yan tümcesi uygulanacağı zaman belirleyen yan tümcelerdir. Bir özel durum filtresi için kullanılan `true`ifade değerlendirirse, catch yan tümcesi bir özel durum üzerinde normal işlemini gerçekleştirir. İfade için `false`değerlendirilirse, `catch` yan tümce atlanır. Bir kullanım, bir `catch` yan tümcenin özel durumu işleyip işlemeyebileceğini belirlemek için bir özel durum la ilgili bilgileri incelemektir:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>İfade `nameof`

İfade [adı](../language-reference/operators/nameof.md) bir sembolün adını değerlendirir. Bir değişkenin, bir özelliğin veya üye alanın adına ihtiyaç duyduğunuzda araçların çalışmasını sağlamak için harika bir yoldur. Bunun en yaygın kullanımlarından `nameof` biri, özel bir özel durum oluşturan bir simgenin adını sağlamaktır:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Başka bir kullanım `INotifyPropertyChanged` arabirimi uygulayan XAML tabanlı uygulamalar ile:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Catch ve Finally bloklarda bekleyin

C# 5'in ifadelerin ilerleyebileceği `await` birkaç sınırlaması vardı. C# 6 ile artık `await` ifadeleri `catch` `finally` veya ifadeleri kullanabilirsiniz. Bu en sık günlük senaryoları ile kullanılır:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

İçeride `await` `catch` destek eklemek için `finally` uygulama ayrıntıları ve yan tümceler, davranışın eşzamanlı kod davranışıyla tutarlı olmasını sağlar. Bir `catch` veya `finally` yan tümce de yürütüldüğünde, `catch` yürütme sonraki çevre bloğunda uygun bir yan tümce arar. Geçerli bir özel durum varsa, bu özel durum kaybolur. Aynı durum beklenen ifadeler `catch` ve `finally` yan tümceler `catch` ile de olur: uygun bir arama yapılır ve varsa geçerli özel durum kaybolur.  

> [!NOTE]
> Bu davranış, yeni özel durumlar `catch` getirilmesini önlemek için dikkatle yazmak ve `finally` yantümler önerilir nedenidir.

## <a name="initialize-associative-collections-using-indexers"></a>Dizinleyicileri kullanarak bağdaştırıcı koleksiyonları başlatma

*Dizin Initializers,* koleksiyon başlatılmasını dizin kullanımıyla daha tutarlı hale getiren iki özellikten biridir. C#'ın önceki sürümlerinde, anahtar ve değer çiftleri etrafında <xref:System.Collections.Generic.Dictionary%602>ayraçlar ekleyerek sıra stili koleksiyonları içeren *koleksiyon başlatmalayıcılarını* kullanabilirsiniz:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Bunları, erişilebilir `Add` <xref:System.Collections.Generic.Dictionary%602> yöntemin birden fazla bağımsız değişkeni kabul ettiği koleksiyonlar ve diğer türlerde kullanabilirsiniz. Yeni sözdizimi, koleksiyona bir dizin kullanarak atamayı destekler:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Bu özellik, bağşılı kapsayıcıların, çeşitli sürümler için sıra kapsayıcıları için yerinde olana benzer sözdizimi kullanılarak başharflerle başlatAbileceği anlamına gelir.

## <a name="extension-add-methods-in-collection-initializers"></a>Toplama `Add` başlatma da uzatma yöntemleri

Toplama başlatmayı kolaylaştıran bir diğer özellik de `Add` yöntem için bir *uzantı yöntemi* kullanabilme özelliğidir. Bu özellik Visual Basic ile eşlik için eklendi. Bu özellik, semantik olarak yeni öğeler eklemek için farklı bir ada sahip bir yönteme sahip özel bir koleksiyon sınıfına sahipolduğunuzda en kullanışlı özelliktir.

## <a name="improved-overload-resolution"></a>Geliştirilmiş aşırı yük çözünürlüğü

Bu son özellik muhtemelen fark olmaz biridir. C# derleyicisinin önceki sürümünün lambda ifadelerini içeren bazı yöntem çağrılarının belirsiz bulduğu yapılar vardı. Bu yöntemi göz önünde bulundurun:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

C#'ın önceki sürümlerinde, yöntem grubu sözdizimini kullanarak bu yöntemi çağırmak başarısız olur:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

Önceki derleyici ile `Task.Run(Action)` `Task.Run(Func<Task>())`' yi doğru ayırt edemedi. Önceki sürümlerde, bir argüman olarak bir lambda ifadesi kullanmanız gerekir:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

C# 6 derleyicisi bunun `Task.Run(Func<Task>())` daha iyi bir seçim olduğunu doğru bir şekilde belirler.

### <a name="deterministic-compiler-output"></a>Deterministik derleyici çıktısı

Seçenek, `-deterministic` derleyiciye aynı kaynak dosyalarının ardışık derlemeleri için bayt için bir aynı çıktı derlemesi oluşturmasını bildirir.

Varsayılan olarak, her derleme her derlemede benzersiz çıktı üretir. Derleyici bir zaman damgası ve rasgele sayılardan oluşturulan bir GUID ekler. Yapılar arasında tutarlılık sağlamak için bayt için bayt çıktısını karşılaştırmak istiyorsanız bu seçeneği kullanırsınız.

Daha fazla bilgi için [-deterministic derleyici seçeneği](../language-reference/compiler-options/deterministic-compiler-option.md) makalesine bakın.
