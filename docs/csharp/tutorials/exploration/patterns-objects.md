---
title: Nesnelerdeki desenleri kullanma-C# öğreticisi
description: Bu öğretici, nesne davranışına yönelik daha iyi modeller oluşturmak için sınıf üyelerinde model eşleştirmeyi kullanma tekniklerini öğretir
ms.date: 11/05/2020
ms.openlocfilehash: 072f6f57696504c2d691473e3a43c1cda53f227f
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94332193"
---
# <a name="use-pattern-matching-to-build-your-class-behavior-for-better-code"></a>Daha iyi kod için sınıf davranışınızı derlemek için model eşleştirmeyi kullanın

C# ' deki model eşleştirme özellikleri, algoritmalarınızı ifade etmek için sözdizimi sağlar. Sınıflarınızda davranışı uygulamak için bu teknikleri kullanabilirsiniz. Gerçek dünyada nesneleri modellemesi sırasında kısa kod sağlamak için, veri odaklı bir uygulamayla nesne yönelimli sınıf tasarımını birleştirebilirsiniz.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:

> [!div class="checklist"]
>
> - Veri desenleri kullanarak nesne yönelimli sınıflarınızı hızlı bir şekilde ifade edin.
> - C# ' nin desen eşleştirme özelliklerini kullanarak bu desenleri uygulayın.
> - Uygulamanızı doğrulamak için derleyici tanılarından yararlanın.

## <a name="prerequisites"></a>Önkoşullar

C# 9,0 derleyicisi dahil olmak üzere, makinenizi .NET 5 çalıştıracak şekilde ayarlamanız gerekir. C# 9,0 derleyicisi, [Visual Studio 2019 sürüm 16,8 Preview](https://visualstudio.microsoft.com/vs/preview/) veya [.NET 5,0 SDK Preview](https://dotnet.microsoft.com/download/dotnet/5.0)ile başlayarak kullanılabilir.

## <a name="build-a-simulation-of-a-canal-lock"></a>Canal kilidi benzetimi oluşturma

Bu öğreticide, bir [Canal kilisini](https://en.wikipedia.org/wiki/Lock_(water_navigation))taklit eden bir C# sınıfı oluşturacaksınız. Kısaca, Canal kilidi, farklı düzeylerde iki su arasında hareket eden Boats çıkaran ve alçalmış bir cihazdır. Bir kilidin iki kapısı ve su düzeyini değiştirmek için bazı mekanizması vardır.

Normal işleminde, bir bot bir kapıdan birine girdiğinde, kilit içindeki su düzeyi, bot 'ın girdiği taraftaki su düzeyiyle eşleşir. Kilitte bir kez, su düzeyi, bot 'un kilidi bırakacağı su düzeyiyle eşleşecek şekilde değiştirilir. Su düzeyi bu kenar ile eşleştiğinde, çıkış tarafındaki kapı açılır. Güvenlik önlemleri, bir işlecin Canal içinde tehlikeli bir durum oluşturmadığından emin olun. Su düzeyi yalnızca her iki kapı da kapalı olduğunda değiştirilebilir. En fazla bir kapı açık olabilir. Bir kapısı açmak için, kilit içindeki su düzeyi, açılmakta olan kapı dışında su düzeyiyle eşleşmelidir.

Bu davranışı modellemek için bir C# sınıfı derleyebilirsiniz. Bir `CanalLock` sınıf, iki ağ geçidini açmak veya kapatmak için komutları destekler. Su oluşturmak veya azaltmak için başka komutlara sahip olur. Sınıfı ayrıca, her iki kapıların ve su düzeyinin geçerli durumunu okumak için özellikleri desteklemelidir. Yöntemleriniz, güvenlik önlemlerini uygular.

## <a name="define-a-class"></a>Sınıf tanımlama

Sınıfınızı test etmek için bir konsol uygulaması oluşturacaksınız `CanalLock` . Visual Studio veya .NET CLı kullanarak .NET 5 için yeni bir konsol projesi oluşturun. Ardından, yeni bir sınıf ekleyin ve bunu adlandırın `CanalLock` . Sonra, genel API 'nizi tasarlayın, ancak uygulanmamış yöntemleri bırakın:

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="APIDesign":::

Yukarıdaki kod, her iki kapı da kapalı olacak şekilde nesneyi başlatır ve su düzeyi düşüktür. Ardından, `Main` sınıfının ilk uygulamasını oluştururken size rehberlik etmek için aşağıdaki test kodunu yöntemine yazın:

:::code language="csharp" source="snippets/pattern-objects/Program.cs" ID="HappyTests":::

Sonra, sınıfındaki her yöntemin ilk bir uygulamasını ekleyin `CanalLock` . Aşağıdaki kod, güvenlik kurallarına gerek kalmadan sınıfının yöntemlerini uygular. Güvenlik testlerini daha sonra ekleyeceksiniz:

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="FirstImplementation":::

Şimdiye kadar yazdığınız testler. Temel bilgileri uyguladık. Şimdi, ilk başarısızlık koşulu için bir test yazın. Önceki testlerin sonunda, her iki kapı da kapalıdır ve su düzeyi Low olarak ayarlanır. Üst ağ geçidini açmayı denemek için bir test ekleyin:

:::code language="csharp" source="snippets/pattern-objects/Program.cs" ID="HighGateSafetyTest":::

Ağ Geçidi açıldığı için bu test başarısız olur. İlk uygulama olarak, aşağıdaki kodla bu hatayı çözebilirsiniz:

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="SecondImplementation":::

Testleriniz başarılı. Ancak, daha fazla test eklediğinizde daha fazla ve daha fazla `if` yan tümce ekleyecek ve farklı özellikleri test edeceksiniz. Yakında, bu yöntemler daha fazla koşul eklerken çok karmaşık hale gelir.

## <a name="implement-the-commands-with-patterns"></a>Komutları desenlerle uygulama

Daha iyi bir yol, nesnenin bir komutu yürütmek için geçerli bir durumda olup olmadığını belirleme *alışkanlıkları* kullanmaktır. Üç değişkenin işlevi olarak bir komuta izin verilip verilmeyeceğini ifade edebilirsiniz: kapı durumu, su düzeyi ve yeni ayar:

| Yeni ayar | Kapı durumu | Su düzeyi | Sonuç             |
| ----------- | ---------- | ----------- | ------------------ |
| Kapatıldı      | Kapatıldı     | Yüksek        | Kapatıldı             |
| Kapatıldı      | Kapatıldı     | Düşük         | Kapatıldı             |
| Kapatıldı      | Aç       | Yüksek        | Aç               |
| ~~Kapatıldı~~  | ~~Aç~~   | ~~Düşük~~     | ~~Kapatıldı~~         |
| Aç        | Kapatıldı     | Yüksek        | Aç               |
| Aç        | Kapatıldı     | Düşük         | Kapalı (hata)     |
| Aç        | Aç       | Yüksek        | Aç               |
| ~~Aç~~    | ~~Aç~~   | ~~Düşük~~     | ~~Kapalı (hata)~~ |

Tablodaki dördüncü ve son satırlar, geçersiz oldukları için metnin üzerine çizili olmalıdır. Şimdi eklemekte olduğunuz kod, su düşük olduğunda yüksek su kapılı kapı olmadığından emin olmalıdır.  Bu durumlar tek bir anahtar ifadesi olarak kodlanabilir ( `false` "Closed" olduğunu unutmayın):

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="ThirdImplementation":::

Bu sürümü deneyin. Testler, kodu doğrulayarak geçer. Tam tablo, girişlerin ve sonuçların olası birleşimlerini gösterir. Diğer bir deyişle, sizin ve diğer geliştiriciler tabloya hızlı bir şekilde bakabilir ve tüm olası girişleri kapsadığınızı görebilirler. Daha da kolay olsa da, derleyici de yardımcı olabilir. Önceki kodu ekledikten sonra, derleyicinin bir uyarı üretdiğini görebilirsiniz: *CS8524* , switch ifadesinin tüm olası girişleri kapsamadığını gösterir. Bu uyarının nedeni girdilerden birinin bir tür olmasının nedenidir `enum` . Derleyici, temel alınan türden tüm girişler olarak "tüm olası girişleri" Yorumlar, genellikle bir `int` . Bu `switch` ifade yalnızca içinde belirtilen değerleri denetler `enum` . Uyarıyı kaldırmak için, ifadenin son ARM için bir catch-all atma kalıbı ekleyebilirsiniz. Bu durum geçersiz girişi gösterdiği için bir özel durum oluşturur:

```csharp
_  => throw new InvalidOperationException("Invalid internal state"),
```

Önceki anahtar ARM, `switch` tüm girişlerle eşleştiğinden deyiminizdeki en son bir olmalıdır. Daha önce sırayla taşıyarak deneyin. Bu, bir düzende erişilemeyen kod için derleyici hatası *CS8510* neden olur.  Anahtar ifadelerinin doğal yapısı, derleyicinin olası hatalara karşı hata ve uyarı oluşturmasını sağlar. "Güvenlik ağı" derleyicisi, daha az yinelemede doğru kod oluşturmanızı ve anahtar kolları joker karakterlerle birleştirme özgürlüğünü kolaylaştırır. Eğer kombinasyonunuzu beklemediğiniz şekilde sonuçlanırsa, derleyici hatalara neden olur ve gerekli olan bir ARM 'yi kaldırırsanız uyarılar oluşur.

İlk değişiklik, komutun ağ geçidini kapatan tüm kolları birleştirmek olur; Bu her zaman izin verilir. Aşağıdaki kodu, anahtar ifadenizde ilk ARM olarak ekleyin:

```csharp
(false, _, _) => false,
```

Önceki anahtar ARM 'yi ekledikten sonra, komutun olduğu her bir kolun üzerinde olmak üzere dört derleyici hatası alırsınız `false` . Bu kollar zaten yeni eklenen ARM tarafından kapsanıyor. Bu dört satırı güvenle kaldırabilirsiniz. Bu koşulların yerini alacak bu yeni anahtar Kolonu hedeflenmiştir.

Sonra, komutun ağ geçidini açmak için olduğu dört Kolonu basitleştirebilirsiniz. Su düzeyi yüksek olan her iki durumda da ağ geçidi açılabilir. (Bir arada zaten açıktır.) Su düzeyi düşük olan bir durum özel durum oluşturur ve diğeri gerçekleşmemelidir. Su kilidi zaten geçersiz durumdaysa aynı özel durumu oluşturması güvenli olmalıdır. Bu Koller için aşağıdaki basitleştirmeleri yapabilirsiniz:

```csharp
(true, _, WaterLevel.High) => true,
(true, false, WaterLevel.Low) => throw new InvalidOperationException("Cannot open high gate when the water is low"),
_ => throw new InvalidOperationException("Invalid internal state"),
```

Testlerinizi yeniden çalıştırın ve başarılı olurlar. Metodun son sürümü aşağıda verilmiştir `SetHighGate` :

:::code language="csharp" source="snippets/pattern-objects/CanalLock.cs" ID="FinalImplementaton":::

## <a name="implement-patterns-yourself"></a>Desenleri kendiniz uygulayın

Tekniği gördüğünüze göre, `SetLowGate` ve `SetWaterLevel` yöntemlerini kendiniz doldurmanız gerekir.  Bu yöntemlerde geçersiz işlemleri test etmek için aşağıdaki kodu ekleyerek başlayın:

:::code language="csharp" source="snippets/pattern-objects/Program.cs" ID="FinalTestCode":::

Uygulamanızı yeniden çalıştırın. Yeni testlerin başarısız olduğunu ve Canal kilidinin geçersiz bir duruma sahip olduğunu görebilirsiniz. Kalan yöntemleri kendiniz uygulamayı deneyin. Alt ağ geçidini ayarlama yöntemi, üst ağ geçidini ayarlamak için yönteme benzer olmalıdır. Su düzeyini değiştiren yöntemin farklı denetimleri vardır ancak benzer bir yapıyı izlemelidir. Su düzeyini ayarlayan yöntemi için aynı işlemi kullanmayı yararlı bulabilirsiniz. Dört girişin tümü ile başlayın: her iki kapıların durumu, su düzeyinin geçerli durumu ve istenen yeni su düzeyi. Switch ifadesinin başlaması gerekir:

```csharp
CanalLockWaterLevel = (newLevel, CanalLockWaterLevel, LowWaterGateOpen, HighWaterGateOpen) switch
{
    // elided
};
```

Doldurmanız gereken 16 toplam anahtar Kolonu olacak. Ardından, test edin ve basitleştirir.

Yöntem şöyle bir şey yaptınız mı?

:::code language="csharp" source="snippets/pattern-objects/CanalLock.cs" ID="FinalExercise":::

Testlerinizin geçmesi gerekir ve Canal kilidi güvenli bir şekilde çalışır.

## <a name="summary"></a>Özet

Bu öğreticide, bu durumda herhangi bir değişikliği uygulamadan önce bir nesnenin iç durumunu denetlemek için model eşleştirmeyi kullanmayı öğrendiniz. Özelliklerin birleşimlerini denetleyebilirsiniz. Bu geçişlerde herhangi biri için tablolar oluşturduktan sonra kodunuzu test edersiniz ve daha sonra okunabilirlik ve bakım için basitleştik. Bu ilk yeniden düzenlemeler, iç durumu doğrulayan veya diğer API değişikliklerini yöneten daha fazla yeniden düzenlemeler önerebilir. Bu öğretici, sınıfları ve nesneleri, bu sınıfları uygulamaya yönelik daha fazla veri odaklı, desenli bir yaklaşımla birleştirmelidir.
