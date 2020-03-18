---
title: "C'deki varsayılan arabirim yöntemlerini kullanarak arabirimleri güvenli bir şekilde güncelleyin #"
description: Bu gelişmiş öğretici, bu arabirimi uygulayan tüm sınıfları ve yapıları bozmadan varolan arabirim tanımlarına nasıl güvenle yeni özellikler ekleyebileceğinizi araştırır.
ms.date: 05/06/2019
ms.technlogy: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: 650aea78b421783b3f249b3670578aa60e800ab2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156785"
---
# <a name="tutorial-update-interfaces-with-default-interface-methods-in-c-80"></a>Öğretici: C# 8.0'da varsayılan arabirim yöntemleriyle arabirimleri güncelleştirme

.NET Core 3.0'daki C# 8.0 ile başlayarak, bir arabirimin üyesini beyan ettiğinizde bir uygulama tanımlayabilirsiniz. En yaygın senaryo, sayısız istemci tarafından zaten serbest bırakılmış ve kullanılan bir arabirime güvenli bir şekilde üye eklemektir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> * Uygulamalarla yöntemler ekleyerek arabirimleri güvenli bir şekilde genişletin.
> * Daha fazla esneklik sağlamak için parametreli uygulamalar oluşturun.
> * Uygulayıcıların geçersiz kılma şeklinde daha özel bir uygulama sağlamasını sağlayın.

## <a name="prerequisites"></a>Önkoşullar

C# 8.0 derleyicisi de dahil olmak üzere .NET Core'u çalıştıracak şekilde makinenizi ayarlamanız gerekir. C# 8.0 derleyicisi [Visual Studio 2019 sürüm 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

## <a name="scenario-overview"></a>Senaryoya genel bakış

Bu öğretici, müşteri ilişkileri kitaplığı sürümü 1 ile başlar. GitHub bizim [örnekleri repo](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship)üzerinde başlangıç uygulaması alabilirsiniz. Bu kütüphaneyi kuran şirket, mevcut uygulamaları olan müşterilerin kitaplıklarını benimsemelerini amaçlamıştır. Kitaplık kullanıcılarının uygulayabildikleri en az arabirim tanımları sağladılar. Bir müşteri için arayüz tanımı aşağıda verilmiştir:

[!code-csharp[InitialCustomerInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

Bir siparişi temsil eden ikinci bir arabirim tanımladılar:

[!code-csharp[InitialOrderInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

Bu arabirimlerden, takım kullanıcılarının müşterileri için daha iyi bir deneyim oluşturması için bir kitaplık oluşturabilir. Amaçları mevcut müşterilerle daha derin bir ilişki kurmak ve yeni müşterilerle ilişkilerini geliştirmekti.

Şimdi, bir sonraki sürüm için kitaplığı yükseltme zamanı. İstenen özelliklerden biri, çok sayıda siparişi olan müşteriler için bir sadakat indirimi sağlar. Bu yeni sadakat indirimi, bir müşteri sipariş verdiğinde uygulanır. Belirli indirim her müşterinin bir özelliğidir. Her uygulama `ICustomer` sadakat indirimi için farklı kurallar belirleyebilirsiniz.

Bu işlevselliği eklemenin en doğal `ICustomer` yolu, herhangi bir sadakat indirimi uygulamak için bir yöntem ile arayüzü geliştirmektir. Bu tasarım önerisi deneyimli geliştiriciler arasında endişeye neden oldu: "Arayüzler serbest bırakıldıktan sonra değişmez! Bu bir kırılma değişikliktir!" C# 8.0 arabirimleri yükseltmek için *varsayılan arabirim uygulamalarını* ekler. Kitaplık yazarları arabirime yeni üyeler ekleyebilir ve bu üyeler için varsayılan bir uygulama sağlayabilir.

Varsayılan arabirim uygulamaları, geliştiricilerin arabirimi yükseltmesini sağlarken, uygulayıcıların bu uygulamayı geçersiz kılmasını da sağlar. Kitaplığın kullanıcıları varsayılan uygulamayı kırılmayan bir değişiklik olarak kabul edebilir. İş kuralları farklıysa, geçersiz kılınabilir.

## <a name="upgrade-with-default-interface-methods"></a>Varsayılan arabirim yöntemleriyle yükseltme

Takım en olası varsayılan uygulama üzerinde anlaştılar: müşteriler için bir sadakat indirimi.

Yükseltme, iki özellik ayarlamak için işlevselliği sağlamalıdır: iskontoya uygun olması için gereken sipariş sayısı ve iskonto yüzdesi. Bu varsayılan arabirim yöntemleri için mükemmel bir senaryo yapar. `ICustomer` Arabirime bir yöntem ekleyebilir ve en olası uygulamayı sağlayabilirsiniz. Varolan tüm ve tüm yeni uygulamalar varsayılan uygulamayı kullanabilir veya kendi uygulamalarını sağlayabilir.

İlk olarak, uygulamaya yeni yöntem ekleyin:

[!code-csharp[InitialOrderInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

Kitaplık yazarı uygulamayı denetlemek için ilk test yazdı:

[!code-csharp[TestDefaultImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

Testin aşağıdaki bölümüne dikkat edin:

[!code-csharp[TestDefaultImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

O alçı `SampleCustomer` `ICustomer` gerekli. Sınıf `SampleCustomer` için `ComputeLoyaltyDiscount`bir uygulama sağlamak gerekmez; `ICustomer` bu arayüz tarafından sağlanmaktadır. Ancak, `SampleCustomer` sınıf kendi arabirimlerinden üyeleri devralmaz. Bu kural değişmedi. Arabirimde bildirilen ve uygulanan herhangi bir yöntemi aramak için, değişken bu `ICustomer` örnekte arabirimin türü olmalıdır.

## <a name="provide-parameterization"></a>Parametrelendirme sağlama

Bu iyi bir başlangıç. Ancak, varsayılan uygulama çok kısıtlayıcıdır. Bu sistemin birçok tüketicisi satın alma sayısı, farklı bir üyelik uzunluğu veya farklı bir yüzde indirimi için farklı eşikler seçebilir. Bu parametreleri ayarlamak için bir yol sağlayarak daha fazla müşteri için daha iyi bir yükseltme deneyimi sağlayabilir. Varsayılan uygulamayı denetleyen bu üç parametreyi ayarlayan statik bir yöntem ekleyelim:

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

Bu küçük kod parçasında gösterilen birçok yeni dil yeteneği vardır. Arabirimler artık alanlar ve yöntemler de dahil olmak üzere statik üyeleri içerebilir. Farklı erişim değiştiriciler de etkinleştirilir. Ek alanlar özel, yeni yöntem geneldir. Değiştiricilerden herhangi biri arabirim üyelerine izin verilir.

Sadakat indirimini hesaplamak için genel formülü kullanan, ancak farklı parametreleri kullanan uygulamaların özel bir uygulama sağlaması gerekmez; bağımsız değişkenleri statik bir yöntemle ayarlayabilirler. Örneğin, aşağıdaki kod, herhangi bir müşteriyi bir aydan fazla üyelikle ödüllendiren bir "müşteri takdiri" ayarlar:

[!code-csharp[SetLoyaltyThresholds](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>Varsayılan uygulamayı genişletme

Şimdiye kadar eklediğiniz kod, kullanıcıların varsayılan uygulama gibi bir şey istediği veya ilgisiz bir kural kümesi sağladığı senaryolar için kullanışlı bir uygulama sağlamıştır. Son bir özellik için, kullanıcıların varsayılan uygulama üzerinde oluşturmak isteyebileceği senaryoları etkinleştirmek için kodu biraz yeniden oluşturalım.

Yeni müşteriler çekmek isteyen bir başlangıç düşünün. Yeni bir müşterinin ilk siparişinde %50 indirim sunarlar. Aksi takdirde, mevcut müşteriler standart indirimden yararlanabilir. Kitaplık yazarının, bu arabirimi `protected static` uygulayan herhangi bir sınıfın kodu uygulamalarında yeniden kullanabilmesi için varsayılan uygulamayı bir yönteme taşıması gerekir. Arabirim üyesinin varsayılan uygulaması da bu paylaşılan yöntemi çağırır:

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

Bu arabirimi uygulayan bir sınıfın uygulamasında, geçersiz kılma statik yardımcı yöntemini arayabilir ve "yeni müşteri" iskontosunu sağlamak için bu mantığı genişletebilir:

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

[GitHub'da örneklerimiz repo'da](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/finished/customer-relationship)bitmiş kodun tamamını görebilirsiniz. GitHub bizim [örnekleri repo](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship)üzerinde başlangıç uygulaması alabilirsiniz.

Bu yeni özellikler, bu yeni üyeler için makul bir varsayılan uygulama olduğunda arabirimlerin güvenli bir şekilde güncelleştirilebildiği anlamına gelir. Birden çok sınıf tarafından uygulanabilecek tek işlevsel fikirleri ifade etmek için arayüzleri dikkatle tasarlayın. Bu, aynı işlevsel fikir için yeni gereksinimler keşfedildiğinde bu arabirim tanımlarını yükseltmeyi kolaylaştırır.
