---
title: C# 6 C# kılavuzundaki yenilikler
description: Sürüm 6 ' daki C# yeni özellikleri öğrenin
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971380"
---
# <a name="whats-new-in-c-6"></a>6 ' daki C# yenilikler

Uygulamasının C# 6,0 sürümü, geliştiricilerin üretkenliğini artıran birçok özellik içeriyordu. Bu özelliklerin genel etkisi, daha okunaklı olan daha kısa kodlar yazmanızı de ister. Söz dizimi birçok yaygın uygulama için daha az sertifika içerir. Tasarım amacını daha az seremle görmek daha kolaydır. Bu özellikleri iyi öğrenin ve daha üretken olacak daha fazla kod yazmanız ve daha fazla okunabilir kod yazmanız gerekir. Özelliklerden daha fazlasını, dilin yapılarından daha fazla odaklanabilirsiniz.

Bu makalenin geri kalanında, her bir özelliği keşfetmeye yönelik bir bağlantı ile bu özelliklerin her biri için bir genel bakış sunulmaktadır. Ayrıca öğreticiler bölümünde [6 ' da etkileşimli bir araştırmayla ilgili C# ](../tutorials/exploration/csharp-6.yml) özellikleri inceleyebilirsiniz.

## <a name="read-only-auto-properties"></a>Salt okunurdur otomatik Özellikler

*Salt okuma otomatik özellikleri* , sabit türler oluşturmak için daha kısa bir sözdizimi sağlar. Auto özelliğini yalnızca bir get erişimcisi ile bildirirsiniz:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

`FirstName` Ve`LastName` özellikleri yalnızca aynı sınıfın oluşturucusunun gövdesinde ayarlanabilir:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Başka bir yöntemde `LastName` ayarlamaya çalışmak, `CS0200` derleme hatası oluşturur:

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

Bu özellik, sabit türler oluşturmak için gerçek dil desteğini sunar ve daha kısa ve uygun otomatik özellik sözdizimini kullanır.

Bu söz dizimini eklemek erişilebilir bir yöntemi kaldırmazsa, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)olur.

## <a name="auto-property-initializers"></a>Otomatik-özellik başlatıcıları

*Otomatik Özellik başlatıcıları* , otomatik özellik için ilk değeri özellik bildiriminin bir parçası olarak bildirmenize olanak tanır.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

Üye `Grades` , bildirildiği yerde başlatılır. Bu, başlatmayı tam olarak bir kez gerçekleştirmeyi kolaylaştırır. Başlatma, özellik bildiriminin bir parçasıdır ve bu, depolama ayırmasının nesneler için `Student` ortak arabirimle daha kolay olmasını sağlar.

## <a name="expression-bodied-function-members"></a>İfade-Bodied işlev üyeleri

Yazdığınız birçok üye tek deyimler olabilecek tek ifadelerdir. Bunun yerine Expression-Bodied üyesi yazın. Yöntemler ve salt okunurdur özellikleri için geçerlidir. Örneğin, bir geçersiz kılma `ToString()` genellikle harika bir adaydır:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Bu sözdizimini salt okuma özellikleri için de kullanabilirsiniz:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Varolan bir üyenin bir ifade ile değiştirilmesi, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)olur.

## <a name="using-static"></a>statik kullanma

*Statik geliştirme kullanımı* , tek bir sınıfın statik yöntemlerini içeri aktarmanızı sağlar. Kullanmakta olduğunuz sınıfı belirtirsiniz:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<xref:System.Math> Herhangi bir örnek yöntemi içermez. Statik ve örnek yöntemlerine `using static` sahip bir sınıf için sınıf ' statik yöntemleri içeri aktarmak için de kullanabilirsiniz. En yararlı örneklerden <xref:System.String>biri şunlardır:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Statik bir using ifadesinde tam sınıf adını `System.String` kullanmanız gerekir.  Bunun yerine `string` anahtar sözcüğünü kullanamazsınız.

Bir `static using` deyimden içeri aktarıldığında, genişletme yöntemleri yalnızca uzantı yöntemi çağırma sözdizimi kullanılarak çağrıldığında kapsamdadır. Statik bir yöntem olarak çağrıldığında kapsamda değildir. Bunu genellikle LINQ sorgularında görürsünüz. <xref:System.Linq.Enumerable> Ya<xref:System.Linq.Queryable>da içeri aktararak LINQ deseninin içeri aktarabilirsiniz.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Uzantı yöntemlerini, genellikle uzantı yöntemi çağırma ifadelerini kullanarak çağırabilirsiniz. Statik yöntem çağrısı sözdizimini kullanarak çağırdığınız nadir bir durumda sınıf adı ekleme belirsizlik çözümleniyor.

Yönerge `static using` , iç içe geçmiş türleri de içeri aktarır. Herhangi bir iç içe geçmiş türe, nitelik olmadan başvurabilirsiniz.

## <a name="null-conditional-operators"></a>Null-koşullu işleçler

*Null koşullu işleç* , null denetimleri çok daha kolay ve akıcı hale getirir. Üye erişimini `.` bununla `?.`değiştirin:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

Önceki örnekte, değişken `first` , kişi nesnesi `null`ise atanır `null` . Aksi takdirde, `FirstName` özelliğin değeri atanır. En önemlisi, `?.` Bu kod satırının `person` , değişkeni ise, `null`bir `NullReferenceException` olarak yaramayacağı anlamına gelir. Bunun yerine, kısa devreler ve döndürür `null`. Dizi veya Dizin Oluşturucu erişimi için null koşullu bir işleç de kullanabilirsiniz. Dizin `[]` ifadesinde `?[]` ile değiştirin.

Aşağıdaki ifade, `person`değerinden bağımsız `string`olarak bir döndürür. Bu yapıyı genellikle, `null`özelliklerden biri olduğunda varsayılan değerleri atamak için *null birleşim* işleciyle kullanırsınız. Kısa devre `null` ifadesi olduğunda döndürülen değer tam ifadeyle eşleşecek şekilde yazılır.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Yöntemleri koşullu olarak çağırmak `?.` için de kullanabilirsiniz. Null koşullu işleçle üye işlevlerinin en yaygın kullanımı, güvenli temsilcileri (veya olay işleyicilerini) `null`güvenle çağırmadır.  Üyeye erişmek için `?.` işlecini kullanarak temsilcinin `Invoke` yöntemini çağıracaksınız. [Temsilci desenleri](../delegates-patterns.md#handling-null-delegates) makalesinde bir örnek görebilirsiniz.

`?.` İşlecinin kuralları, işlecin sol tarafının yalnızca bir kez değerlendirildiğinden emin olur. Olay işleyicilerini kullanarak aşağıdaki örnek dahil olmak üzere birçok deyim sunar:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Sol tarafının yalnızca bir kez değerlendirilmesinin yanı sıra, yöntemin sol tarafındaki Yöntem çağrıları dahil herhangi bir ifadeyi kullanmanıza de olanak sağlar.`?.`

## <a name="string-interpolation"></a>Dize ilişkilendirme

6 C# ile yeni [dize ilişkilendirme](../language-reference/tokens/interpolated.md) özelliği bir dizeye ifade eklemenizi sağlar. Dizeyi yalnızca ile `$`önyüz ve sıra sayıları yerine ve `{` `}` arasında ifadeleri kullanın:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Bu örnek, değiştirilen ifadeler için özellikleri kullanır. Herhangi bir ifadeyi kullanabilirsiniz. Örneğin, ilişkilendirme 'nin bir parçası olarak bir öğrencinin sınıf noktası ortalamasını hesaplamanız gerekir:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Yukarıdaki kod satırı, değeri `Grades.Average()` iki ondalık basamakla kayan noktalı sayı olarak biçimlendirir.

Genellikle, belirli bir kültür kullanılarak üretilen dizeyi biçimlendirmeniz gerekebilir. Dize ilişkilendirme tarafından üretilen nesnenin örtük olarak öğesine <xref:System.FormattableString?displayProperty=nameWithType>dönüştürülebileceği olguyu kullanırsınız. <xref:System.FormattableString> Örnek, bileşik biçim dizesini ve ifadeleri dizelere dönüştürmeden önce değerlendirme sonuçlarını içerir. Bir dizeyi biçimlendirirken kültürü belirtmek için yönteminikullanın.<xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> Aşağıdaki örnek, Almanya (de-DE) kültürünü kullanarak bir dize üretir. (Varsayılan olarak, Almanya kültürü ondalık ayırıcı için ', ' karakterini ve binlik ayırıcı olarak '. ' karakterini kullanır.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Dize ilişkilendirmeyi kullanmaya başlamak için etkileşimli öğreticide [dize ilişkilendirme C# ](../tutorials/exploration/interpolated-strings.yml) , [dize ilişkilendirme](../language-reference/tokens/interpolated.md) makalesi ve öğreticideki [dize ilişkilendirme C# ](../tutorials/string-interpolation.md) bölümüne bakın.

## <a name="exception-filters"></a>Özel durum filtreleri

*Özel durum filtreleri* , belirli bir catch yan tümcesinin ne zaman uygulanacağını tespit eden yan tümcelerdir. Özel durum filtresi için kullanılan ifade olarak `true`değerlendirilirse, catch yan tümcesi bir özel durum üzerinde normal işlemesini gerçekleştirir. İfade olarak `false`değerlendirilirse, `catch` yan tümce atlanır. Bir kullanım, bir `catch` yan tümcenin özel durumu işleyebilmesine izin vermek için bir özel durumla ilgili bilgileri incelemektir:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>`nameof` İfade

[NameOf](../language-reference/operators/nameof.md) ifadesinin bir sembolün adı olarak değerlendirilir. Bir değişken, özellik veya üye alanı için her ihtiyaç duyduğunuzda, araçların çalışmasını sağlamak için harika bir yoldur. İçin `nameof` en yaygın kullanımlardır bir özel duruma neden olan bir simgenin adını sağlamaktır:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Başka bir kullanım, `INotifyPropertyChanged` arabirimini uygulayan XAML tabanlı uygulamalardır:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Catch ve finally bloklarında await

C#5 ' te ifadeler yerleştirebileceğiniz `await` yerde çeşitli sınırlamalar vardı. 6 C# ile artık `await` `catch` veya ifadelerindekullanabilirsiniz.`finally` Bu, genellikle günlük senaryolarıyla kullanılır:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

`finally` İçinde `await` destekeklemek`catch` için uygulama ayrıntıları ve yan tümceleri, davranışın zaman uyumlu kod davranışıyla tutarlı olmasını sağlamaktır. `catch` `catch` Or yantümcesindeyürütülenkodoluşturduğunda,yürütmesonrakiçevresindekibloktauygunbiryantümcearar.`finally` Geçerli bir özel durum varsa, bu özel durum kaybedilir. Aynı durum, `catch` ve `finally` yan tümcelerinde beklenen ifadelerle aynıdır: için uygun `catch` bir aranır ve varsa geçerli özel durum kaybolur.  

> [!NOTE]
> Bu davranış `catch` `finally` , yeni özel durumlar oluşturmamaya özen gösterin.

## <a name="initialize-associative-collections-using-indexers"></a>Dizin oluşturucular kullanarak ilişkilendirilebilir koleksiyonları başlatma

*Dizin başlatıcıları* , koleksiyon başlatıcılarının Dizin kullanımıyla daha tutarlı olmasını sağlayan iki özellikten biridir. ' In C#önceki sürümlerinde, anahtar ve değer çiftleri etrafında küme ayraçları ekleyerek sıra stili <xref:System.Collections.Generic.Dictionary%602>koleksiyonlarıyla *koleksiyon başlatıcıları* kullanabilirsiniz:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Bunları, erişilebilir `Add` yöntemin birden <xref:System.Collections.Generic.Dictionary%602> fazla bağımsız değişken kabul ettiği koleksiyonlar ve diğer türlerle birlikte kullanabilirsiniz. Yeni sözdizimi, koleksiyona bir dizin kullanılarak atamayı destekler:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Bu özellik, çeşitli sürümlere yönelik dizi kapsayıcılarına benzer bir sözdizimi kullanılarak ilişkilendirilebilir kapsayıcıların başlatılabileceği anlamına gelir.

## <a name="extension-add-methods-in-collection-initializers"></a>Koleksiyon `Add` başlatıcılarında uzantı yöntemleri

Koleksiyon başlatmayı daha kolay hale getiren başka bir özellik, `Add` yöntemi için bir *genişletme yöntemi* kullanma olanağıdır. Bu özellik Visual Basic eşlik için eklendi. Özelliği, en çok, anlamsal olarak yeni öğeler eklemek için farklı bir ada sahip bir yöntemi olan bir özel koleksiyon sınıfınız olduğunda yararlıdır.

## <a name="improved-overload-resolution"></a>Geliştirilmiş aşırı yükleme çözümlemesi

Bu son özellik, büyük olasılıkla fark edilmeyecek bir özelliktir. C# Derleyicinin önceki sürümünde lambda ifadeleri içeren bazı Yöntem çağrıları bulunursa oluşturulan yapılar vardı. Şu yöntemi göz önünde bulundurun:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

Önceki sürümlerinde C#, Yöntem grubu sözdizimini kullanarak bu yöntemi çağırmak başarısız olur:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

Önceki derleyici ve `Task.Run(Action)` `Task.Run(Func<Task>())`arasında doğru şekilde ayırt edilemedi. Önceki sürümlerde bağımsız değişken olarak bir lambda ifadesi kullanmanız gerekir:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

6 C# derleyicisi, daha iyi bir `Task.Run(Func<Task>())` seçim olduğunu doğru şekilde belirler.

### <a name="deterministic-compiler-output"></a>Belirleyici derleyici çıkışı

`-deterministic` Seçeneği derleyiciye aynı kaynak dosyaların birbirini izleyen derlemeler için bayt için aynı çıkış derlemesi oluşturmasını söyler.

Varsayılan olarak, her derleme her derlemede benzersiz çıktı üretir. Derleyici, bir zaman damgası ve rastgele sayıdan oluşturulan bir GUID ekler. Bu seçeneği, derlemeler genelinde tutarlılığı sağlamak üzere bayt için bayt çıkışı karşılaştırmak istiyorsanız kullanın.

Daha fazla bilgi için, bkz. [belirleyici derleyici seçeneği](../language-reference/compiler-options/deterministic-compiler-option.md) makalesi.
