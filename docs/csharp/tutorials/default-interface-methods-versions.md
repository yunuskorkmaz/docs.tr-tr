---
title: İçindeki varsayılan arabirim yöntemlerini kullanarak arabirimleri güvenli bir şekilde GüncelleştirC#
description: Bu gelişmiş öğreticide, var olan arabirim tanımlarına, bu arabirimi uygulayan tüm sınıfları ve yapıları bozmadan nasıl güvenli bir şekilde yeni yetenekler ekleyebileceğiniz açıklanır.
ms.date: 05/06/2019
ms.custom: mvc
ms.openlocfilehash: 71fce2594dbf5ef3175a6b9bdf4e6edba754bb84
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72276003"
---
# <a name="tutorial-update-interfaces-with-default-interface-methods-in-c-80"></a>Öğretici: 8,0 içinde C# varsayılan arabirim yöntemleriyle arabirimleri güncelleştirme

.NET Core C# 3,0 ' de 8,0 ' den başlayarak, bir arabirimin üyesini bildirdiğinizde bir uygulama tanımlayabilirsiniz. En yaygın senaryo, önceden yayınlanan ve kullanılmayan istemciler tarafından kullanılan bir arabirime güvenli bir şekilde üye eklemektir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> * Uygulamalarla yöntemler ekleyerek arabirimleri güvenli bir şekilde genişletin.
> * Daha fazla esneklik sağlamak için parametreli uygulamalar oluşturun.
> * Bir geçersiz kılma biçiminde daha belirli bir uygulama sağlamak için uygulayıcıları etkinleştirin.

## <a name="prerequisites"></a>Önkoşullar

Makinenizi, C# 8,0 derleyicisi dahil .NET Core çalıştıracak şekilde ayarlamanız gerekir. 8,0 C# derleyicisi, [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

## <a name="scenario-overview"></a>Senaryoya genel bakış

Bu öğretici, bir müşteri ilişkisi kitaplığının 1. sürümüyle başlar. [GitHub 'daki örnek](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship)depolarımızda başlangıç uygulamasını edinebilirsiniz. Bu kitaplığın, kütüphanesini benimsemesini sağlayan, mevcut uygulamalarla müşterileri hedefleyen Şirket. Bunlar, kütüphanesinin kullanıcıları için en az sayıda arabirim tanımı sağladık. Müşterinin arabirim tanımı aşağıda verilmiştir:

[!code-csharp[InitialCustomerInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

Sıralamayı temsil eden ikinci bir arabirim tanımlarlar:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

Bu arabirimlerde, takım kullanıcılarına müşterilerine daha iyi bir deneyim oluşturmak için bir kitaplık oluşturabilir. Bu kişilerin hedefi, mevcut müşterilerle daha derin bir ilişki oluşturmak ve yeni müşterilerle ilişkilerini geliştirmektir.

Şimdi, bir sonraki sürüm için kitaplığı yükseltmeniz zaman atalım. İstenen özelliklerden biri, çok sayıda siparişi olan müşteriler için bağlılık programı indirimi sunar. Bu yeni bağlılık programı indirimi, bir müşteri sipariş yaptığında uygulanır. Belirli indirim, her müşterinin bir özelliğidir. @No__t-0 ' ın her uygulanması, bağlılık programı indirimi için farklı kurallar ayarlayabilir. 

Bu işlevi eklemenin en doğal yolu, `ICustomer` arabirimini tüm bağlılık programı indirimine uygulanacak bir yöntemle geliştirmektir. Bu tasarım önerisi, deneyimli geliştiriciler arasında sorun oluşmasına neden oldu: "arabirimler yayımlandıklarında sabittir! Bu bir son değişiklik! " C#8,0, arabirimleri yükseltmek için *varsayılan arabirim uygulamalarını* ekler. Kitaplık yazarları arabirime yeni üyeler ekleyebilir ve bu üyeler için varsayılan bir uygulama sağlar.

Varsayılan arabirim uygulamaları, geliştiricilerin bu uygulamayı geçersiz kılmak için herhangi bir uygulamayı etkinleştirirken bir arabirimi yükseltmesini sağlar. Kitaplığın kullanıcıları, varsayılan uygulamayı kırılmamış bir değişiklik olarak kabul edebilir. İş kuralları farklıysa, geçersiz kılınabilir.

## <a name="upgrade-with-default-interface-methods"></a>Varsayılan arabirim yöntemleriyle yükselt

Takım, en olası varsayılan uygulamada anlaşmıştır: müşteriler için bağlılık programı indirimi.

Yükseltme, iki özellik ayarlama işlevini sağlamalıdır: indirimle uygun olması gereken siparişlerin sayısı ve indirimin yüzdesi. Bu, varsayılan arabirim yöntemlerine yönelik kusursuz bir senaryo sağlar. @No__t-0 arabirimine bir yöntem ekleyebilirsiniz ve en olası uygulamayı sağlayabilirsiniz. Tüm mevcut ve tüm yeni uygulamalar varsayılan uygulamayı kullanabilir veya kendi özelliklerini sağlayabilir.

Önce, uygulamaya yeni yöntemi ekleyin:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

Kitaplık yazarı, uygulamayı denetlemek için bir ilk test yazdı:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

Testin aşağıdaki kısmına dikkat edin:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

@No__t-0 ' dan `ICustomer` ' e dönüştürme gereklidir. @No__t-0 sınıfının `ComputeLoyaltyDiscount` için bir uygulama sağlaması gerekmez; Bu, `ICustomer` arabirimi tarafından sunulur. Ancak `SampleCustomer` sınıfı, arabirimlerinden üyeleri almıyor. Bu kural değiştirilmedi. Arabirimde bildirildiği ve uygulanan herhangi bir yöntemi çağırmak için, bu örnekte, değişken arabirimin türü, `ICustomer` olmalıdır.

## <a name="provide-parameterization"></a>Parametreleştirme sağlama

Bu iyi bir başlangıç. Ancak, varsayılan uygulama çok kısıtlayıcıdır. Bu sistemin pek çok tüketicisi, satın alma sayısı, farklı üyelik uzunluğu veya farklı bir yüzde indirimi için farklı eşikler seçebilirler. Bu parametreleri ayarlamak için bir yol sağlayarak daha fazla müşteri için daha iyi bir yükseltme deneyimi sağlayabilirsiniz. Varsayılan uygulamayı denetleyen bu üç parametreyi ayarlayan statik bir yöntem ekleyelim:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

Bu küçük kod parçasında gösterilen birçok yeni dil özelliği vardır. Arabirimler artık alanlar ve yöntemler dahil statik üyeleri içerebilir. Farklı erişim değiştiricileri de etkinleştirilir. Ek alanlar özeldir, yeni yöntem geneldir. Arabirim üyelerinde değiştiricilerin herhangi birine izin verilir.

Bağlılık programı iskontosunu hesaplamak için genel formülü kullanan uygulamalar, ancak farklı parametreler, özel bir uygulama sağlanması gerekmez; bağımsız değişkenleri statik bir yöntem aracılığıyla ayarlayabilirler. Örneğin, aşağıdaki kod, birden fazla aya ait üyeliğe sahip herhangi bir müşteriyi yeniden karşılayan bir "müşteri değer artırma" ayarlıyor:

[!code-csharp[SetLoyaltyThresholds](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>Varsayılan uygulamayı genişletme

Şimdiye kadar eklemiş olduğunuz kod, kullanıcıların varsayılan uygulama gibi bir şey istediği veya ilgisiz bir kural kümesi sağladığı senaryolar için uygun bir uygulama sağladı. Son bir özellik için, kullanıcıların varsayılan uygulamada derlemek isteyebileceğiniz senaryolara olanak tanımak için kodu bir bit yeniden düzenleyin. 

Yeni müşterileri çekmek isteyen bir başlatma düşünün. Yeni bir müşterinin ilk siparişi için %50 indirim sağlar. Aksi halde, mevcut müşteriler standart iskontoyu alır. Kitaplık yazarının varsayılan uygulamayı bir `protected static` yöntemine taşıması gerekir; böylece bu arabirimi uygulayan herhangi bir sınıf kendi uygulamalarında kodu yeniden kullanabilir. Arabirim üyesinin varsayılan uygulanması, bu paylaşılan yöntemi de çağırır:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

Bu arabirimi uygulayan bir sınıfın uygulamasında, geçersiz kılma statik yardımcı yöntemini çağırabilir ve "yeni müşteri" indirimi sağlamak için bu mantığı genişletebilir:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

Tüm tamamlanmış kodu [GitHub 'daki örnek](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/finished/customer-relationship)depoımızda görebilirsiniz. [GitHub 'daki örnek](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship)depolarımızda başlangıç uygulamasını edinebilirsiniz.

Bu yeni özellikler, bu yeni üyeler için makul bir varsayılan uygulama olduğunda arabirimlerin güvenli bir şekilde güncelleştirilemeyeceği anlamına gelir. Birden çok sınıf tarafından uygulanabilen tek işlevsel fikirlerin hızlı bir şekilde tasarlanması. Bu, aynı işlevsel fikir için yeni gereksinimler bulunduğunda bu arabirim tanımlarını yükseltmeyi kolaylaştırır.
