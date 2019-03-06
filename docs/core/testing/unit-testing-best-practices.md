---
title: Birim testleri yazmak için en iyi uygulamalar
description: Bu sürücü kod kalite ve esneklik için .NET Core ve .NET Standard projelerine birim testleri yazmak için en iyi uygulamaları öğrenin.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.custom: seodec18
ms.openlocfilehash: b543ab2e200e8169a251db8ddfb1493c5583ed69
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360257"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a>Birim testi .NET Core ve .NET Standard ile en iyi uygulamalar

Birim testleri yazma için çok sayıda avantaj vardır; belgeler, regresyonla sağlar ve iyi bir tasarım kolaylaştırmak yardımcı olurlar. Ancak, okuma ve kırılgan sabit bir birim testlerini kod tabanınız üzerinde düzensizliğe benzer zararlar verecektir. Bu makalede, .NET Core ve .NET Standard projeleri için birim test tasarımı ile ilgili bazı en iyi uygulamaları açıklar.

Bu kılavuzda, esnek ve kolay anlaşılır testlerinizi tutmak için birim testleri yazılırken bazı en iyi uygulamaları öğreneceksiniz.

Tarafından [John Reese](https://reese.dev) performanstan özel ile [Roy Osherove](http://osherove.com/)

## <a name="why-unit-test"></a>Neden birim testi?

### <a name="less-time-performing-functional-tests"></a>Daha az zaman işlevsel testleri gerçekleştirme
İşlevsel testleri pahalıdır. Bunlar genellikle uygulamayı açmaktan ve bir dizi (veya bir başkasının), Beklenen davranış doğrulayabilmek izlemelidir adımları gerçekleştirerek de içerir. Bu adımları her zaman daha bilgili birine alanı test gerçekleştirmek için ulaşmak olacağı anlamına gelir test edici için bilinmeyebilir. Kendi test Önemsiz değişiklikleri saniye veya daha büyük değişikliklerin dakika sürebilir. Son olarak, bu işlem her değişiklik için sistemde yaptığınız yinelenmesi gerekir.

Birim testleri, diğer el, milisaniye almak, bir düğmeye basarak çalıştırılabilir ve büyük sistemin herhangi bir Bilgi Bankası gerektirmeyebilecek. Testin geçtiğini veya başarısız olup olmadığını test Çalıştırıcısı kadar kişi var.

### <a name="protection-against-regression"></a>Regresyon karşı koruma
Regresyon hataları uygulamada bir değişiklik yapıldığında, sunulan hatalar var. Yalnızca test ediciler, yeni bir özellik test ancak beklendiği gibi özellikleri daha önce uygulanan doğrulamak için önceden varolan özellikleri işlevi ayrıca hala yaygındır.

Birim testi ile her derlemeden sonra veya bir kod satırı değiştirdikten sonra bile, tüm testleri paketi yeniden çalıştırmak mümkündür. Size yeni kodunuz var olan işlevselliği kesmez güvenilirlik sağlar.

### <a name="executable-documentation"></a>Yürütülebilir belgeleri
Bu her zaman belirli bir yöntem yapar veya belirli bir giriş nasıl davrandığını belirgin olmayabilir. Kendiniz isteyebilir: Boş bir dize başarılı olursa bu yöntem nasıl çalışır? Null?

İyi adlandırılmış birim testleri paketi varsa, her test açıkça belirtilen bir giriş için beklenen çıktıyı açıklamak gerekir. Ayrıca, aslında çalışıp çalışmadığını doğrulayabilirsiniz olmalıdır.

### <a name="less-coupled-code"></a>Daha az bağlı kod
Kod sıkı şekilde bağlı olduğunda, birim testi zor olabilir. Yazmakta olduğunuz koda yönelik birim testleri oluşturmadan bağlantısından daha az görünür olabilir.

Aksi takdirde test daha zor olduğundan kodunuz için testleri yazmak kodunuzu, doğal olarak ayırmak.

## <a name="characteristics-of-a-good-unit-test"></a>İyi birim testi özellikleri
- **Hızlı**. Seyrek olgun projeleri için birim testleri binlerce sahip değil. Birim testleri çalıştırmak için çok az zamanınız olması gerekir. Milisaniye cinsinden.
- **Yalıtılmış**. Birim testleri tek başına olan, yalıtılmış olarak çalıştırabilir ve herhangi bir dosya sistemi veya veritabanı gibi faktörlere dışında hiçbir bağımlılıkları vardır.
- **Tekrarlanabilir**. Birim testi sonuçlarını ile tutarlı olmalıdır, çalıştırmaları arasında herhangi bir şey değiştirmezseniz diğer bir deyişle, her zaman aynı sonucu döndürür.
- **Kendi kendine denetimi**. Test, Geçti veya insan etkileşimi başarısız olursa otomatik olarak algılayabilir olmalıdır.
- **Zamanında**. Birim testi test edilen kodu karşılaştırılan yazma orantısız uzun sürmesi gerekir. Çok miktarda kod yazmaya kıyasla saat sürüyor kodu test etmek bulursanız, daha fazla test edilebilir bir tasarım kullanmayı düşünün.

## <a name="lets-speak-the-same-language"></a>Aynı dili şimdi konuşun
Terim *sahte* testi hakkında konuşurken ne yazık ki çok yanlış kullanılmış olan. En yaygın türleri, aşağıdaki tanımlar *fakes* birim testleri yazılırken:

*Sahte* -sahte bir saplama veya sahte bir nesne tanımlamak için kullanılan genel bir terimdir. Bir saplama veya sahte bir olup olmadığını, kullanıldığı bağlam üzerinde bağlıdır. Bu nedenle başka bir deyişle, sahte bir saplama veya bir sahte olabilir.

*Sahte* -sahte bir nesne bir sahte bir birim testi geçti veya başarısız olup olmadığını karar sistemde nesnesidir. Karşı onaylanan kadar bir Sahne sahte başlar.

*Saplama* -bir saplama sistemde mevcut bağımlılık (veya ortak çalışanı) denetlenebilir bir ardılı olan. Bir saplama kullanarak kodunuzu doğrudan bağımlılık uğraşmanızı olmadan test edebilirsiniz. Varsayılan olarak, sahte bir saplama başlar.

Aşağıdaki kod parçacığı göz önünde bulundurun:

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Bu, kalıntı bir Sahne başvurulan bir örneği olabilir. Bu durumda, bir saptama olur. Yalnızca örneklemek için bir yol sırada geçirme `Purchase` (test altındaki sistem). Adı `MockOrder` yeniden sırasını sahte bir de çok yanıltıcı olmamasıdır.

Daha iyi bir yaklaşım olacaktır

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Sınıfı yeniden adlandırarak `FakeOrder`sınıfı çok daha genel yaptığınız, sınıfı bir sahte veya bir saplama kullanılabilir. Hangisi, test çalışması için iyidir. Yukarıdaki örnekte, `FakeOrder` yer tutucusu olarak kullanılır. Kullanmadığınız `FakeOrder` assert sırasında herhangi bir şekil veya biçimde. `FakeOrder` yalnızca içine geçirilen `Purchase` Oluşturucu gereksinimlerini karşılamak için sınıf.

Bir Sahne kullanmak için aşağıdakine benzer yapabilirsiniz

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

Bu durumda, (karşı sunduğundan), sahte bu nedenle Yukarıdaki kod parçacığında, bir özellik denetimi `mockOrder` bir sahte olduğu.

> [!IMPORTANT]
> Bu terimler doğru almak önemlidir. "Mocks", saptamalar çağırırsanız, diğer geliştiriciler, amacı hakkında varsayımlar false oluşturacaksınız.

Bir saplama karşı assert değil ise mocks yer tutucular yerine ilgili hatırlamak ana mocks yalnızca saptamalar gibi olan, ancak sahte bir nesneye karşı assert şeydir.

## <a name="best-practices"></a>Önerilen uygulamalar

### <a name="naming-your-tests"></a>Testlerinizi adlandırma
Test adı üç bölümden oluşmalıdır:
- Test edilen yöntemin adı.
- Altında sınanır senaryo.
- Senaryo çağrıldığında Beklenen davranış.

#### <a name="why"></a>Neden?
- Adlandırma standartlarına, bunlar test amacı açıkça express için önemlidir.

Testler daha fazlasını bulunduğunuzdan emin kodunuzun çalıştığı da sağladıkları belgeleri. Yalnızca birim testleri suite'e bakarak bile koda göz bakmadan kodunuzu davranışını belirleyebilir olmalıdır. Ayrıca, test başarısız olduğunda, tam olarak hangi senaryoların beklentilerinizi karşılamayan görebilirsiniz.

#### <a name="bad"></a>Hatalı:
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a>Daha iyi:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a>Testlerinizi Düzenleme
**Düzenleme, hareket, onaylama işlemi** yaygın olduğu zaman desen birim testi. Adından da anlaşılacağı gibi üç ana eylemden oluşur:
- *Düzenleme* nesnelerinizi, oluşturma ve bunları gerektiği şekilde ayarlama.
- *ACT* bir nesne üzerinde.
- *Assert* , beklendiği gibi bir şeydir.

#### <a name="why"></a>Neden?
- Açıkça ne gelen edildiğini ayıran *düzenleme* ve *assert* adımları.
- "Eylem" kodlu bir onayları intermix olasılığı daha az.

Okunabilirlik en önemli yönlerinden test yazarken biridir. Test içinde bu eylemlerin her birine ayırarak açıkça kodunuzu, kodunuzu nasıl çağrılan ve onay çalıştığınız çağırmak için gereken bağımlılıklar vurgulayın. Bazı adımlar birleştirin ve testinizi boyutunu küçültmek mümkün olabilir, ancak birincil amacı, test olarak okunabilir olmasını sağlamaktır.

#### <a name="bad"></a>Hatalı:
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a>Daha iyi:
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a>En düşük düzeyde geçirme testleri yazma
Şu anda test ettiğiniz davranışına doğrulamak için bir birim testinde kullanılacak giriş basit mümkün olması gerekir.

#### <a name="why"></a>Neden?
- Testler kod tabanındaki gelecekteki değişikliklere daha dayanıklı hale gelir.
- Uygulama davranışı test yakın.

Test geçirmek için gerekenden daha fazla bilgi içeren testler hataları teste giriş, daha yüksek şansına sahip olabilirsiniz ve amacı, az NET test yapabilirsiniz. Testleri yazılırken davranışı odaklanmak istiyorsunuz. Modeller üzerinde ek özellikleri ayarlamak veya gerekli olduğunda sıfır olmayan değerler kullanarak, yalnızca ne kanıtlamak çalışıyorsunuz gelen detracts.

#### <a name="bad"></a>Hatalı:
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a>Daha iyi:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a>Sihirli dize kaçının
Değişkenleri adlandırma birim testleri gibi önemli değil daha da önemlisi, üretim kodunda adlandırma değişkenleri daha. Birim testleri Sihirli dize içermemelidir.

#### <a name="why"></a>Neden?
- Değer özel kılan anlamak için üretim kodu incelemek için gereken test okuyucu engeller.
- Açmaya çalıştığınız açıkça gösterir *kanıtlamak* çalışılırken yerine *gerçekleştirmek*.

Sihirli dize testlerinizin Okuyucu için karışıklığa neden olabilir. Bir dize normal dışı görünüyorsa, bunlar belirli bir değer için bir parametre neden seçildiğini merak ediyor veya dönüş değeri. Bu test yakından odak yerine uygulama ayrıntılarını almak için bunları neden olabilir.

> [!TIP] 
> Testleri yazılırken, mümkün olduğunca fazla hedefi ifade etmek için indirmeyi amaçlamanız gerekir. Sihirli dize söz konusu olduğunda, bu değerleri sabitleri atama iyi bir yaklaşımdır.

#### <a name="bad"></a>Hatalı:
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a>Daha iyi:
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a>Testleri mantığı kaçının
Birim testleri önlemek el ile dize birleştirme ve mantıksal gibi koşullar yazılırken `if`, `while`, `for`, `switch`vb.

#### <a name="why"></a>Neden?
- Testlerinizi içinde bir hata tanıtmak için fırsat daha az.
- Sonuç, yerine uygulama ayrıntılarını odaklanın.

Mantıksal test paketiniz aldığımızda, içine bir hata ile tanışın olasılığını önemli ölçüde artırır. Bir hatayı bulmak için istediğiniz son içinde test çalışmalarıyla yerdir. Testlerinizi iş güvenle yüksek düzeyde olmalıdır, aksi takdirde, bunları güvenir değil. Güvenmediğiniz, testler herhangi bir değer sağlamaz. Bir test başarısız olduğunda, bir şeyin aslında kodunuzla yanlış olduğunu ve bunu göz ardı edilemez olduğunu bir fikir edindiniz istiyorsunuz.

> [!TIP]
> Testinizde mantıksal kaçınılmaz görünüyorsa, iki veya daha fazla farklı testlere test bölmeyi göz önünde bulundurun.

#### <a name="bad"></a>Hatalı:
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a>Daha iyi:
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a>Kurulumu ve kaldırma için yardımcı yöntemler tercih et
Testleriniz için benzer bir nesne ya da durum gerekiyorsa, bir yardımcı yöntemi varsa, kurulumu ve kaldırma öznitelikleri yararlanarak daha tercih eder.

#### <a name="why"></a>Neden?
- Daha az karışıklık, testlerin tüm kodu beri okunurken her test içinde görülebilir.
- Çok fazla veya çok küçük bir verilen test için kurma olasılığı daha az.
- Bunlar arasında istenmeyen bağımlılıklar oluşturan testleri arasında durum paylaşma şansı daha az.

Birim test çerçeveleri, `Setup` içinde test çalışmalarıyla her birim testi önce çağrılır. Bazı faydalı bir araç olarak görebilir, ancak bu genellikle için bloated ve testleri okunmasını sonlanan sona erer. Her test genellikle test çalıştırmaya almak için farklı gereksinimleri vardır. Ne yazık ki `Setup` , her test için aynı gereksinimlerinin tamamı kullanmaya zorlayabilir.

> [!NOTE] 
> xUnit sürümden itibaren kaldırdı hem kurulumu ve kaldırma 2.x

#### <a name="bad"></a>Hatalı:
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a>Daha iyi:
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a>Birden çok önlemek onaylar
Testlerinizi yazarken, yalnızca test başına bir onay içerecek şekilde deneyin. Yalnızca birini kullanarak genel yaklaşımları onaylama Ekle:
- Her onay için ayrı bir test oluşturun.
- Parametreli testleri kullanır.

#### <a name="why"></a>Neden?
- Bir onay başarısız olursa, sonraki Asserts değerlendirilmez.
- Birden çok durum testlerinizde sunduğundan değil sağlar.
- Testlerinizi neden başarısız dair tüm resim sunar. 

Birden çok giriş için bir test çalışmasına onaylar, bu, tüm garanti edilmez, onaylar yürütülebilir. Onaylama başarısız bir birim test, sonra çoğu birim testi çerçevelerini içinde devam etmeden testleri otomatik olarak başarısız olduğunu kabul edilir. Gerçekten çalışmaktadır, işlevselliği gösterilecek şekilde başarısız olarak bu kafa karıştırıcı olabilir.

> [!NOTE]
> Bir nesneye karşı sunduğundan bu kural için ortak bir özel durumdur. Bu durumda olması genellikle kabul edilebilirdir nesne, olmasını beklediğiniz durumunda olduğundan emin olmak için her bir özellik karşı birden çok onaylar.

#### <a name="bad"></a>Hatalı:
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a>Daha iyi:
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a>Özel birim testi genel yöntemleri yöntemle doğrula
Çoğu durumda olmamalıdır test bir özel yöntemi gerekir. Bir uygulama ayrıntısı özel yöntemlerdir. Bunu bu şekilde düşünebilirsiniz: özel yöntemler yalıtım modunda hiçbir zaman yok. Belirli bir noktada oluşacak uygulanması bir parçası olarak özel yöntemi çağıran bir genel kullanıma yönelik yöntemi. Önem verdiğiniz metodun özel bir çağıran son sonucudur. 

Aşağıdaki örneği inceleyin

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = trimInput(input);
    return sanitizedInput;
}

private string trimInput(string input)
{
    return input.Trim();
}
```

Bir test için yazmaya başlamak için ilk tepkinizi olabilir `trimInput` yöntemi beklendiği gibi çalıştığından emin olmak istememiz. Ancak, bu tamamen mümkündür, `ParseLogLine` yöneten `sanitizedInput` gibi bir sınaması işleme beklediğiniz olmayan bir şekilde `trimInput` gereksiz. 

Gerçek bir testin genel kullanıma yönelik yöntemi karşı yapılmalıdır `ParseLogLine` ne sonuçta verdiğiniz, çünkü. 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

Bu bakış açısı ile özel bir yöntem görürseniz, genel yöntemini bulun ve karşı bu yöntemi testlerinizi yazın. Özel bir yöntem yalnızca beklenen sonuç döndürdüğünden, sonunda özel yöntemi çağıran sistem sonucu doğru kullandığı anlamına gelmez.

### <a name="stub-static-references"></a>Saplama statik başvuruları
İlkeleri bir birim testinin, test altındaki sistem tam denetimi olmalıdır biridir. Üretim kodu statik başvuruları çağrıları içerdiğinde bu sorunlu olabilir (örneğin `DateTime.Now`). Aşağıdaki kodu düşünün

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

Nasıl Bu kod, birim test büyük olasılıkla olabilir? Bir yaklaşım gibi çalışabilir

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

Ne yazık ki, testlerinizi birkaç sorunlar olduğunu hızla fark edeceksiniz. 

- Test paketi Salı günü çalıştırırsanız, ikinci test geçer, ancak ilk test başarısız olur.
- Test paketi başka bir günü çalıştırırsanız, ilk test geçer, ancak ikinci test başarısız olur.

Bu sorunları çözmek için tanıtmak gerekecektir bir *bağlantı yeri* üretim kodunuzla. Bir arabirim, denetlemek ve bu arabirimdeki bağımlı üretim kodu için gereken kodu kaydırmak bir yaklaşımdır.

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if(dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

Test paketiniz artık hale gelir

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

Test paketi üzerinde tam denetime sahiptir. Şimdi `DateTime.Now` ve herhangi bir değer yöntemi çağırırken saplama.
