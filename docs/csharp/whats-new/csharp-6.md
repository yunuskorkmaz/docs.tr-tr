---
title: C# 6 ' daki yenilikler-C# Kılavuzu
description: C# sürüm 6 ' daki yeni özellikleri öğrenin
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224234"
---
# <a name="whats-new-in-c-6"></a>C# 6 ' daki yenilikler

C# 6,0 sürümü, geliştiriciler için üretkenliği geliştiren birçok özellik Içeriyordu. Bu özelliklerin genel etkisi, daha okunaklı olan daha kısa kodlar yazmanızı de ister. Söz dizimi birçok yaygın uygulama için daha az sertifika içerir. Tasarım amacını daha az seremle görmek daha kolaydır. Bu özellikleri iyi öğrenin ve daha üretken olacak daha fazla kod yazmanız ve daha fazla okunabilir kod yazmanız gerekir. Özelliklerden daha fazlasını, dilin yapılarından daha fazla odaklanabilirsiniz.

Bu makalenin geri kalanında, her bir özelliği keşfetmeye yönelik bir bağlantı ile bu özelliklerin her biri için bir genel bakış sunulmaktadır. Ayrıca öğreticiler bölümünde [C# 6 ' da etkileşimli bir araştırmayla ilgili](../tutorials/exploration/csharp-6.yml) özellikleri inceleyebilirsiniz.

## <a name="read-only-auto-properties"></a>Salt okunurdur otomatik Özellikler

*Salt okuma otomatik özellikleri* , sabit türler oluşturmak için daha kısa bir sözdizimi sağlar. Auto özelliğini yalnızca bir get erişimcisi ile bildirirsiniz:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

`FirstName`Ve `LastName` özellikleri yalnızca aynı sınıfın oluşturucusunun gövdesinde ayarlanabilir:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Başka bir yöntemde ayarlamaya çalışmak `LastName` , `CS0200` derleme hatası oluşturur:

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

## <a name="auto-property-initializers"></a>Otomatik Özellik başlatıcıları

*Otomatik Özellik başlatıcıları* , otomatik özellik için ilk değeri özellik bildiriminin bir parçası olarak bildirmenize olanak tanır.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades`Üye, bildirildiği yerde başlatılır. Bu, başlatmayı tam olarak bir kez gerçekleştirmeyi kolaylaştırır. Başlatma, özellik bildiriminin bir parçasıdır ve bu, depolama ayırmasının nesneler için ortak arabirimle daha kolay olmasını sağlar `Student` .

## <a name="expression-bodied-function-members"></a>İfade-Bodied işlev üyeleri

Yazdığınız birçok üye tek deyimler olabilecek tek ifadelerdir. Bunun yerine Expression-Bodied üyesi yazın. Yöntemler ve salt okunurdur özellikleri için geçerlidir. Örneğin, bir geçersiz kılma `ToString()` genellikle harika bir adaydır:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Bu sözdizimini salt okuma özellikleri için de kullanabilirsiniz:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Varolan bir üyenin bir ifade ile değiştirilmesi, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)olur.

## <a name="using-static"></a>statik kullanma

*Statik geliştirme kullanımı* , tek bir sınıfın statik yöntemlerini içeri aktarmanızı sağlar. Kullanmakta olduğunuz sınıfı belirtirsiniz:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<xref:System.Math>Herhangi bir örnek yöntemi içermez. `using static`Statik ve örnek yöntemlerine sahip bir sınıf için sınıf ' statik yöntemleri içeri aktarmak için de kullanabilirsiniz. En yararlı örneklerden biri şunlardır <xref:System.String> :

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Statik bir using ifadesinde tam sınıf adını kullanmanız gerekir `System.String`  .  `string`Bunun yerine anahtar sözcüğünü kullanamazsınız.

Bir `static using` deyimden içeri aktarıldığında, genişletme yöntemleri yalnızca uzantı yöntemi çağırma sözdizimi kullanılarak çağrıldığında kapsamdadır. Statik bir yöntem olarak çağrıldığında kapsamda değildir. Bunu genellikle LINQ sorgularında görürsünüz. Ya da içeri aktararak LINQ deseninin içeri aktarabilirsiniz <xref:System.Linq.Enumerable> <xref:System.Linq.Queryable> .

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Uzantı yöntemlerini, genellikle uzantı yöntemi çağırma ifadelerini kullanarak çağırabilirsiniz. Statik yöntem çağrısı sözdizimini kullanarak çağırdığınız nadir bir durumda sınıf adı ekleme belirsizlik çözümleniyor.

`static using`Yönerge, iç içe geçmiş türleri de içeri aktarır. Herhangi bir iç içe geçmiş türe, nitelik olmadan başvurabilirsiniz.

## <a name="null-conditional-operators"></a>Null-koşullu işleçler

*Null koşullu işleç* , null denetimleri çok daha kolay ve akıcı hale getirir. Üye erişimini bununla değiştirin `.` `?.` :

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

Önceki örnekte, değişken, `first` kişi nesnesi ise atanır `null` `null` . Aksi takdirde, özelliğin değeri atanır `FirstName` . En önemlisi, `?.` Bu kod satırının, değişkeni ise, bir olarak yaramayacağı anlamına gelir `NullReferenceException` `person` `null` . Bunun yerine, kısa devreler ve döndürür `null` . Dizi veya Dizin Oluşturucu erişimi için null koşullu bir işleç de kullanabilirsiniz. `[]` `?[]` Dizin ifadesinde ile değiştirin.

Aşağıdaki ifade, değerinden bağımsız olarak bir döndürür `string` `person` . Bu yapıyı genellikle, özelliklerden biri olduğunda varsayılan değerleri atamak için *null birleşim* işleciyle kullanırsınız `null` . Kısa devre ifadesi olduğunda `null` döndürülen değer tam ifadeyle eşleşecek şekilde yazılır.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

`?.`Yöntemleri koşullu olarak çağırmak için de kullanabilirsiniz. Null koşullu işleçle üye işlevlerinin en yaygın kullanımı, güvenli temsilcileri (veya olay işleyicilerini) güvenle çağırmadır `null` .  `Invoke`Üyeye erişmek için işlecini kullanarak temsilcinin yöntemini çağıracaksınız `?.` . [Temsilci desenleri](../delegates-patterns.md#handling-null-delegates) makalesinde bir örnek görebilirsiniz.

İşlecinin kuralları, `?.` işlecin sol tarafının yalnızca bir kez değerlendirildiğinden emin olur. Olay işleyicilerini kullanarak aşağıdaki örnek dahil olmak üzere birçok deyim sunar:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Sol tarafının yalnızca bir kez değerlendirilmesinin yanı sıra, yöntemin sol tarafındaki Yöntem çağrıları dahil herhangi bir ifadeyi kullanmanıza de olanak sağlar. `?.`

## <a name="string-interpolation"></a>Dize ilişkilendirme

C# 6 ile, yeni [dize ilişkilendirme](../language-reference/tokens/interpolated.md) özelliği bir dizeye ifade eklemenizi sağlar. Dizeyi yalnızca ile önyüz ve `$` `{` sıra sayıları yerine ve arasında ifadeleri kullanın `}` :

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Bu örnek, değiştirilen ifadeler için özellikleri kullanır. Herhangi bir ifadeyi kullanabilirsiniz. Örneğin, ilişkilendirme 'nin bir parçası olarak bir öğrencinin sınıf noktası ortalamasını hesaplamanız gerekir:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Yukarıdaki kod satırı, değeri `Grades.Average()` iki ondalık basamakla kayan noktalı sayı olarak biçimlendirir.

Genellikle, belirli bir kültür kullanılarak üretilen dizeyi biçimlendirmeniz gerekebilir. Dize ilişkilendirme tarafından üretilen nesnenin örtük olarak öğesine dönüştürülebileceği olguyu kullanırsınız <xref:System.FormattableString?displayProperty=nameWithType> . <xref:System.FormattableString>Örnek, bileşik biçim dizesini ve ifadeleri dizelere dönüştürmeden önce değerlendirme sonuçlarını içerir. <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType>Bir dizeyi biçimlendirirken kültürü belirtmek için yöntemini kullanın. Aşağıdaki örnek, Almanya (de-DE) kültürünü kullanarak bir dize üretir. (Varsayılan olarak, Almanya kültürü ondalık ayırıcı için ', ' karakterini ve binlik ayırıcı olarak '. ' karakterini kullanır.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Dize ilişkilendirmeyi kullanmaya başlamak için bkz. c# etkileşimli öğreticisinde [dize ilişkilendirme](../tutorials/exploration/interpolated-strings.yml) , [dize ilişkilendirme](../language-reference/tokens/interpolated.md) makalesi ve c# öğreticisinde [dize ilişkilendirme](../tutorials/string-interpolation.md) .

## <a name="exception-filters"></a>Özel durum filtreleri

*Özel durum filtreleri* , belirli bir catch yan tümcesinin ne zaman uygulanacağını tespit eden yan tümcelerdir. Özel durum filtresi için kullanılan ifade olarak değerlendirilirse `true` , catch yan tümcesi bir özel durum üzerinde normal işlemesini gerçekleştirir. İfade olarak değerlendirilirse `false` , `catch` yan tümce atlanır. Bir kullanım, bir `catch` yan tümcenin özel durumu işleyebilmesine izin vermek için bir özel durumla ilgili bilgileri incelemektir:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>`nameof`İfade

[NameOf](../language-reference/operators/nameof.md) ifadesinin bir sembolün adı olarak değerlendirilir. Bir değişken, özellik veya üye alanı için her ihtiyaç duyduğunuzda, araçların çalışmasını sağlamak için harika bir yoldur. İçin en yaygın `nameof` kullanımlardır bir özel duruma neden olan bir simgenin adını sağlamaktır:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Başka bir kullanım, arabirimini uygulayan XAML tabanlı uygulamalardır `INotifyPropertyChanged` :

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Catch ve finally bloklarında await

C# 5 ' te ifadeler yerleştirebileceğiniz yerde çeşitli sınırlamalar vardı `await` . C# 6 ile artık `await` `catch` veya ifadeleri içinde kullanabilirsiniz `finally` . Bu, genellikle günlük senaryolarıyla kullanılır:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

İçinde destek eklemek için uygulama ayrıntıları `await` `catch` ve `finally` yan tümceleri, davranışın zaman uyumlu kod davranışıyla tutarlı olmasını sağlamaktır. `catch`Or `finally` yan tümcesinde yürütülen kod oluşturduğunda, yürütme `catch` sonraki çevresindeki blokta uygun bir yan tümce arar. Geçerli bir özel durum varsa, bu özel durum kaybedilir. Aynı durum, `catch` ve `finally` yan tümcelerinde beklenen ifadelerle aynıdır: için uygun bir `catch` aranır ve varsa geçerli özel durum kaybolur.  

> [!NOTE]
> Bu davranış, `catch` `finally` Yeni özel durumlar oluşturmamaya özen gösterin.

## <a name="initialize-associative-collections-using-indexers"></a>Dizin oluşturucular kullanarak ilişkilendirilebilir koleksiyonları başlatma

*Dizin başlatıcıları* , koleksiyon başlatıcılarının Dizin kullanımıyla daha tutarlı olmasını sağlayan iki özellikten biridir. C# ' nin önceki sürümlerinde, *collection initializers* <xref:System.Collections.Generic.Dictionary%602> anahtar ve değer çiftleri etrafında küme ayraçları ekleyerek sıra stili koleksiyonlarıyla koleksiyon başlatıcıları kullanabilirsiniz:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Bunları, <xref:System.Collections.Generic.Dictionary%602> erişilebilir `Add` yöntemin birden fazla bağımsız değişken kabul ettiği koleksiyonlar ve diğer türlerle birlikte kullanabilirsiniz. Yeni sözdizimi, koleksiyona bir dizin kullanılarak atamayı destekler:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Bu özellik, çeşitli sürümlere yönelik dizi kapsayıcılarına benzer bir sözdizimi kullanılarak ilişkilendirilebilir kapsayıcıların başlatılabileceği anlamına gelir.

## <a name="extension-add-methods-in-collection-initializers"></a>`Add`Koleksiyon başlatıcılarında uzantı yöntemleri

Koleksiyon başlatmayı daha kolay hale getiren başka bir özellik, yöntemi için bir *genişletme yöntemi* kullanma olanağıdır `Add` . Bu özellik Visual Basic eşlik için eklendi. Özelliği, en çok, anlamsal olarak yeni öğeler eklemek için farklı bir ada sahip bir yöntemi olan bir özel koleksiyon sınıfınız olduğunda yararlıdır.

## <a name="improved-overload-resolution"></a>Geliştirilmiş aşırı yükleme çözümlemesi

Bu son özellik, büyük olasılıkla fark edilmeyecek bir özelliktir. Önceki C# derleyicisi sürümünde lambda ifadeleri içeren bazı yöntem çağrılarının bulduğu yapılar vardı. Şu yöntemi göz önünde bulundurun:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

C# ' nin önceki sürümlerinde, Yöntem grubu sözdizimini kullanarak bu yöntemi çağırmak başarısız olur:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

Önceki derleyici ve arasında doğru şekilde ayırt `Task.Run(Action)` edilemedi `Task.Run(Func<Task>())` . Önceki sürümlerde bağımsız değişken olarak bir lambda ifadesi kullanmanız gerekir:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

C# 6 derleyicisi, `Task.Run(Func<Task>())` daha iyi bir seçim olduğunu doğru şekilde belirler.

### <a name="deterministic-compiler-output"></a>Belirleyici derleyici çıkışı

`-deterministic`Seçeneği derleyiciye aynı kaynak dosyaların birbirini izleyen derlemeler için bayt için aynı çıkış derlemesi oluşturmasını söyler.

Varsayılan olarak, her derleme her derlemede benzersiz çıktı üretir. Derleyici, bir zaman damgası ve rastgele sayıdan oluşturulan bir GUID ekler. Bu seçeneği, derlemeler genelinde tutarlılığı sağlamak üzere bayt için bayt çıkışı karşılaştırmak istiyorsanız kullanın.

Daha fazla bilgi için, bkz. [belirleyici derleyici seçeneği](../language-reference/compiler-options/deterministic-compiler-option.md) makalesi.
