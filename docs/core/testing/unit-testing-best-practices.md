---
title: Birim testleri yazmak için en iyi uygulamalar
description: .NET Core ve .NET Standard projeleri için kod kalitesini ve esnekliğini artıran birim testleri yazmak için en iyi uygulamaları öğrenin.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 586373381bcb18384cbf29bb2ca2bd220a2b2d3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240967"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a>.NET Core ve .NET Standard ile en iyi uygulamaları test etme birimi

Birim testleri yazmanın sayısız faydası vardır; gerilemeye yardımcı olurlar, dokümantasyon sağlarlar ve iyi tasarımı kolaylaştırırlar. Ancak, okunması zor ve kırılgan birim testleri kod tabanınızda hasara yol açabilir. Bu makalede, .NET Core ve .NET Standard projeleriniz için birim test tasarımıyla ilgili en iyi bazı uygulamalar açıklanmaktadır.

Bu kılavuzda, testlerinizi esnek ve kolay anlaşılır tutmak için birim testleri yazarken bazı en iyi uygulamaları öğreneceksiniz.

John [Reese](https://reese.dev) tarafından [Roy Osherove](https://osherove.com/) için özel teşekkür

## <a name="why-unit-test"></a>Neden birim testi?

### <a name="less-time-performing-functional-tests"></a>İşlevsel testler gerçekleştirmede daha az zaman
Fonksiyonel testler pahalıdır. Bunlar genellikle uygulamayı açmayı ve beklenen davranışı doğrulamak için sizin (veya başka birinin) izlemesi gereken bir dizi adımı gerçekleştirmeyi içerir. Bu adımlar her zaman test eden tarafından bilinmeyebilir, bu da testi gerçekleştirmek için bölgede daha bilgili birine ulaşmaları gerektiği anlamına gelir. Test in kendisi önemsiz değişiklikler için saniyeler, daha büyük değişiklikler için dakikalar sürebilir. Son olarak, bu işlem sistemde yaptığınız her değişiklik için yinelenmelidir.

Birim testleri, diğer taraftan, milisaniye sürebilir, bir düğmeye basarak çalıştırılabilir ve mutlaka büyük sistem herhangi bir bilgi gerektirmez. Testin geçip geçmediği tek tek değil, test koşucusudur.

### <a name="protection-against-regression"></a>Regresyona karşı koruma
Regresyon kusurları, uygulamada değişiklik yapıldığında ortaya çıkan kusurlardır. Test edenlerin, daha önce uygulanan özelliklerin beklendiği gibi çalıştığını doğrulamak için yalnızca yeni özelliklerini değil, önceden var olan özellikleri de sınaması yaygındır.

Birim testi ile, her yapıdan sonra veya hatta bir kod satırını değiştirdikten sonra tüm test paketinizi yeniden çalıştırmak mümkündür. Yeni kodunuzu varolan işlevselliği bozmaz güven verir.

### <a name="executable-documentation"></a>Çalıştırılabilir belgeler
Belirli bir yöntemin ne yaptığı veya belirli bir girdi verildiğinde nasıl çalıştığı her zaman açık olmayabilir. Kendinize sorabilirsiniz: Boş bir dize geçersem bu yöntem nasıl olur? Null?

İyi adlandırılmış birim testleri paketiniz olduğunda, her test belirli bir giriş için beklenen çıktıyı açıkça açıklayabilmelidir. Buna ek olarak, gerçekten çalıştığını doğrulamak gerekir.

### <a name="less-coupled-code"></a>Daha az birleştirilmiş kod
Kod sıkıca birleştiğinde, testi birleştirmek zor olabilir. Yazdığınız kod için birim testleri oluşturmadan, bağlantı daha az belirgin olabilir.

Kodunuz için testler yazmak doğal olarak kodunuzu ayıracaktır, çünkü aksi takdirde test etmek daha zor olacaktır.

## <a name="characteristics-of-a-good-unit-test"></a>İyi bir birim testinin özellikleri

- **Hızlı.** Olgun projelerin binlerce birim testi olması nadir değildir. Birim testleri çalıştırmak için çok az zaman almalısınız. Milisaniye.
- **İzole edilmiş.** Birim testleri tek başınadır, yalıtımda çalıştırılabilir ve dosya sistemi veya veritabanı gibi dış etkenlere hiçbir bağımlılığı yoktur.
- **Tekrarlanabilir.** Bir birim testi çalıştırmak sonuçlarıyla tutarlı olmalıdır, yani, çalıştırmalar arasında hiçbir şeyi değiştirmezseniz her zaman aynı sonucu döndürür.
- **Kendi kendini kontrol etme.** Test, herhangi bir insan etkileşimi olmadan geçip geçemediğini veya başarısız olup olmadığını otomatik olarak algılayabilmelidir.
- **Zamanında.** Bir birim testi, test edilen kodla karşılaştırıldığında yazmak için orantısız olarak uzun bir zaman almamalıdır. Kodu yazmaya kıyasla büyük miktarda zaman alarak kodu sınamayı bulursanız, daha sınanabilir bir tasarım düşünün.

## <a name="lets-speak-the-same-language"></a>Aynı dili konuşalım.
Terim *mock* ne yazık ki çok test hakkında konuşurken yanlış. Birim testleri yazarken en yaygın *sahte* türleri aşağıda tanımlanır:

*Sahte* - Sahte bir saplama veya sahte bir nesne tanımlamak için kullanılabilecek genel bir terimdir. Bir saplama veya bir alay olup olmadığını kullanılan bağlam bağlıdır. Yani başka bir deyişle, sahte bir saplama ya da bir alay olabilir.

*Mock* - Sahte nesne, birim testinin geçip geçmediğine karar veren sistemdeki sahte bir nesnedir. Bir sahte karşı iddia edilene kadar bir Sahte olarak başlar.

*Saplama* - Saplama, sistemdeki varolan bir bağımlılık (veya ortak layıcı) için denetlenebilir bir değiştirmedir. Bir saplama kullanarak, doğrudan bağımlılık ile uğraşmadan kodunuzu sınayabilirsiniz. Varsayılan olarak, sahte bir saplama olarak başlar.

Aşağıdaki kod parçacıklarını göz önünde bulundurun:

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Bu saplama bir mock olarak anılacaktır bir örnek olacaktır. Bu durumda, bir saplama olduğunu. Anında `Purchase` (test altındaki sistem) yapabilmek için Sipariş'i sadece geçiyorsunuz. Adı `MockOrder` da çok yanıltıcı dır, çünkü yine, sipariş bir alay değildir.

Daha iyi bir yaklaşım olurdu

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Sınıfı yeniden `FakeOrder`adlandırarak, sınıfı çok daha genel hale getirdiniz, sınıf sahte veya saplama olarak kullanılabilir. Hangisi test çalışması için daha iyi. Yukarıdaki örnekte, `FakeOrder` saplama olarak kullanılır. İddia sırasında herhangi `FakeOrder` bir şekil veya biçimde kullanmıyorsunuz. `FakeOrder`sadece yapıcı gereksinimlerini `Purchase` karşılamak için sınıfa geçti.

Sahte olarak kullanmak için böyle bir şey yapabilirsin.

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

Bu durumda, Sahte bir özelliği kontrol (buna karşı iddia), bu yüzden yukarıdaki kod `mockOrder` snippet, bir Mock olduğunu.

> [!IMPORTANT]
> Bu terminolojiyi doğru yapmak önemlidir. Saplamalarınıza "alay" diyorsanız, diğer geliştiriciler niyetiniz hakkında yanlış varsayımlarda bulunurlar.

Alaylar ve saplamalar hakkında hatırlanması gereken en önemli şey, alayların saplamalar gibi olduğudur, ama siz sahte nesneye karşı iddiada bulunmaktadırsınız, oysa siz bir saplama ya karşı iddiada yoktur.

## <a name="best-practices"></a>En iyi uygulamalar

### <a name="naming-your-tests"></a>Testlerinizi adlandırma
Testinizin adı üç bölümden oluşmalıdır:

- Test edilen yöntemin adı.
- Test edildiği senaryo.
- Senaryo çağrıldığında beklenen davranış.

#### <a name="why"></a>Neden?

- Adlandırma standartları önemlidir, çünkü testin amacını açıkça ifade ederler.

Testler, kodunuzu çalıştığından emin olmaktan çok daha fazlasıdır, ayrıca belgeler de sağlar. Birim testleri paketine bakarak, kodunuzun davranışını kodun uzun bir bölümüne bakmadan çıkarabilmelisiniz. Ayrıca, testler başarısız olduğunda, tam olarak hangi senaryoların beklentilerinizi karşılamadığını görebilirsiniz.

#### <a name="bad"></a>Kötü:
[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a>Iyi:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a>Testlerinizi düzenleme
**Düzenleme, Hareket, Assert** birim test edildiğinde ortak bir desendir. Adından da anlaşılacağı gibi, üç ana eylemden oluşur:

- Nesnelerinizi *düzenleyin,* bunları oluşturup gerektiği gibi ayarlayın.
- Bir nesneye göre *hareket* edin.
- Bir şeyin beklendiği gibi olduğunu *iddia edin.*

#### <a name="why"></a>Neden?

- Test edilenleri *düzenleme* ve ileri *sayıliş* adımlarından açıkça ayırır.
- "Act" kodu ile iddiaları karıştırmak için daha az şans.

Okunabilirlik, bir test yazarken en önemli yönlerinden biridir. Testteki bu eylemlerin her birini ayırmak, kodunuzu aramak için gereken bağımlılıkları, kodunuzun nasıl çağrıldığını ve ne iddia etmeye çalıştığınızı açıkça vurgular. Bazı adımları birleştirmek ve testinizin boyutunu küçültmek mümkün olsa da, birincil amaç testi olabildiğince okunabilir hale getirmektir.

#### <a name="bad"></a>Kötü:
[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a>Iyi:
[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a>Minimum geçen testleri yazma
Birim testinde kullanılacak giriş, şu anda test ettiğiniz davranışı doğrulamak için mümkün olan en basit giriş olmalıdır.

#### <a name="why"></a>Neden?

- Testler, kod tabanındaki gelecekteki değişikliklere karşı daha esnek hale gelir.
- Uygulama üzerinde davranışı sınamaya daha yakın.

Testi geçmek için gerekenden daha fazla bilgi içeren testler, teste hata getirme olasılığı daha yüksektir ve testin amacını daha az net hale getirebilir. Testleri yazarken davranışa odaklanmak istersiniz. Modellerde fazladan özellikler ayarlama veya gerekli olmadığında sıfır olmayan değerleri kullanma, yalnızca kanıtlamaya çalıştığınız şeyi bozar.

#### <a name="bad"></a>Kötü:
[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a>Iyi:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a>Sihirli dizeleri kaçının
Birim testlerde değişkenleri adlandırma, üretim kodundaki değişkenleri adlandırmak kadar önemlidir. Birim testleri sihirli dizeleri içermemelidir.

#### <a name="why"></a>Neden?

- Değeri özel kılanın ne olduğunu anlamak için test okuyucusunun üretim kodunu incelemesi gereğini önler.
- *Başarmaya*çalışmaktansa *neyi kanıtlamaya* çalıştığınızı açıkça gösterir.

Sihirli dizeleri testlerinizi okuyucu için karışıklığa neden olabilir. Bir dize olağan dışı görünüyorsa, bir parametre veya geri dönüş değeri için neden belirli bir değerin seçildiğini merak edebilirler. Bu, teste odaklanmak yerine uygulama ayrıntılarına daha yakından bakmalarına neden olabilir.

> [!TIP]
> Testleri yazarken, mümkün olduğunca çok niyet ifade etmek amaçlamalısınız. Sihirli dizeleri söz konusu olduğunda, iyi bir yaklaşım sabitlere bu değerleri atamaktır.

#### <a name="bad"></a>Kötü:
[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a>Iyi:
[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a>Testlerde mantıktan kaçının
Birim testleri yazarken manuel dize concatenation `if`ve `while` `for`mantıksal `switch`koşullar gibi kaçının , , , , vb.

#### <a name="why"></a>Neden?

- Testlerinizin içinde bir hata tanıtmak için daha az şans.
- Uygulama ayrıntıları yerine sonuca odaklanın.

Test paketinize mantık kattığında, içine bir hata girme şansı önemli ölçüde artar. Hata bulmak istediğiniz son yer test paketinizdedir. Testlerinizin işe yarayacağına dair yüksek düzeyde bir güvene sahip olmalısınız, aksi takdirde onlara güvenmezsiniz. Güvenmediğiniz testler, herhangi bir değer sağlamaz. Bir test başarısız olduğunda, bir şeyin kodunuzda gerçekten yanlış olduğunu ve göz ardı edilemeyeceğini hissetmek istersiniz.

> [!TIP]
> Testinizdeki mantık kaçınılmaz görünüyorsa, testi iki veya daha fazla farklı teste bölmeyi düşünün.

#### <a name="bad"></a>Kötü:
[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a>Iyi:
[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a>Kurulum ve yıkma için yardımcı yöntemleri tercih etme
Testleriniz için benzer bir nesne veya durum gerekiyorsa, varsa Kurulum ve Yıkıntı özniteliklerinden yararlanmak yerine yardımcı yöntemi tercih edin.

#### <a name="why"></a>Neden?

- Kodun tümü her testin içinden görülebildiğinden testleri okurken daha az karışıklık.
- Verilen test için çok fazla veya çok az ayarlama şansı daha az.
- Aralarında istenmeyen bağımlılıklar yaratan testler arasında durum paylaşımı daha az şansı.

Birim test çerçevelerinde, `Setup` test paketinizdeki her birim testiöncesinde çağrılır. Bazı yararlı bir araç olarak görebilirsiniz, genellikle şişirilmiş ve testleri okumak zor yol biter. Her test, testi çalışır hale getirmek için genellikle farklı gereksinimlere sahip olacaktır. Ne `Setup` yazık ki, her test için tam olarak aynı gereksinimleri kullanmaya zorlar.

> [!NOTE]
> xUnit sürüm 2.x olarak hem SetUp ve TearDown kaldırdı

#### <a name="bad"></a>Kötü:
[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a>Iyi:
[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a>Birden fazla iddiadan kaçının
Testlerinizi yazarken, test başına yalnızca bir Assert eklemeyi deneyin. Yalnızca bir assert kullanarak ortak yaklaşımlar şunlardır:

- Her assert için ayrı bir test oluşturun.
- Parametreli testler kullanın.

#### <a name="why"></a>Neden?

- Bir Assert başarısız olursa, sonraki Asserts değerlendirilmez.
- Testlerinizde birden çok servis vakası iddia etmemenizi sağlar.
- Testlerinizin neden başarısız olduğuna ilgili resmin tamamını verir.

Bir test çalışmasına birden çok assert sayılırken, tüm ileri bulguların yürütüleceği garanti edilmez. Çoğu birim test çerçevesinde, bir birim testinde bir iddia başarısız olduğunda, devam eden testler otomatik olarak başarısız olarak kabul edilir. Bu, gerçekten çalışan işlevsellik olarak kafa karıştırıcı olabilir, başarısız olarak gösterilecek.

> [!NOTE]
> Bu kuralın yaygın bir istisnası, bir nesneye karşı ileri sayılmaktır. Bu durumda, nesnenin içinde olmasını beklediğiniz durumda olduğundan emin olmak için her özellik aleyhinde birden çok iddia olması genellikle kabul edilebilir.

#### <a name="bad"></a>Kötü:
[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a>Iyi:
[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a>Ortak yöntemleri birim test ederek özel yöntemleri doğrulama
Çoğu durumda, özel bir yöntemi sınamaya gerek olmamalıdır. Özel yöntemler bir uygulama ayrıntısIdir. Şöyle düşünebilirsiniz: özel yöntemler asla izole olarak bulunmaz. Bir noktada, uygulanmasının bir parçası olarak özel yöntem çağıran bir kamu bakan yöntem olacak. Dikkat etmesi gereken şey, özel yönteme çağıran genel yöntemin sonucudur.

Aşağıdaki örneği göz önünde bulundurun

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

İlk tepkiniz, yöntemin beklendiği `TrimInput` gibi çalıştığından emin olmak istediğiniz için bir test yazmaya başlamak olabilir. Ancak, hiç beklemediğiniz `ParseLogLine` şekilde `sanitizedInput` manipüle etmek, yararsız aleyhine `TrimInput` bir test oluşturmatamamen mümkündür.

Gerçek test kamu bakan yönteme `ParseLogLine` karşı yapılmalıdır, çünkü sonuçta ne hakkında bakım olmalıdır.

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

Bu bakış açısıyla, özel bir yöntem görürseniz, ortak yöntemi bulun ve testlerinizi bu yönteme karşı yazın. Özel bir yöntemin beklenen sonucu döndürmesi, sonunda özel yöntemi çağıran sistemin sonucu doğru kullandığı anlamına gelmez.

### <a name="stub-static-references"></a>Stub statik referanslar
Bir birim testinin ilkelerinden biri, test altında sistemin tam denetimine sahip olması gerektiğidir. Üretim kodu statik başvurulara çağrı içeriyorsa (örn. `DateTime.Now` Aşağıdaki kodu göz önünde bulundurun

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

Bu kod nasıl birim test edilebilir? Gibi bir yaklaşım deneyebilirsiniz

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

Ne yazık ki, hızlı bir şekilde testleri ile bir çift sorun olduğunu fark edecektir.

- Test paketi Salı günü çalıştırılırsa, ikinci test geçer, ancak ilk test başarısız olur.
- Test paketi başka bir gün çalıştırılırsa, ilk test geçer, ancak ikinci test başarısız olur.

Bu sorunları çözmek için, üretim kodunuza bir *dikiş* girmeniz gerekir. Bir yaklaşım, bir arabirimde denetlemeniz gereken kodu sarmak ve üretim kodunun bu arabirime bağlı olmasıdır.

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

Test paketiniz artık

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

Artık test paketi üzerinde `DateTime.Now` tam kontrole sahiptir ve yönteme araverirken herhangi bir değer saplayabilir.
