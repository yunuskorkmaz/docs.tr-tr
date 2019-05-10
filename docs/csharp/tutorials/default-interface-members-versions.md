---
title: Arabirimleri varsayılan arabirim üyeleri kullanarak güvenli bir şekilde güncelleştirmeC#
description: Gelişmiş Bu öğretici, nasıl güvenli bir şekilde yeni özellikler mevcut arabirimi tanımları için tüm sınıfları ve bu arabirimi uygulayan yapıları bozmadan ekleyebileceğinizi açıklar.
ms.date: 05/06/2019
ms.custom: mvc
ms.openlocfilehash: ded3704428282b8f9f0542e938137585a07802b4
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65453174"
---
# <a name="tutorial-update-interfaces-with-default-interface-members-in-c-8"></a>Öğretici: Varsayılan arabirim üyeleri ile arabirimleri güncelleştirme C# 8

Başlayarak C# 8'de .NET Core 3.0 bir arabirim üyesi bildirdiğinizde uygulaması tanımlayabilirsiniz. Güvenli bir şekilde serbest ve innumerable istemciler tarafından kullanılan bir arabirim üyeleri eklemek için en yaygın senaryodur bakın.

Bu öğreticide şunları öğrenirsiniz nasıl yapılır:

> [!div class="checklist"]
> * Arabirimleri yöntemleri uygulamalarıyla birlikte ekleyerek güvenli bir şekilde genişletin.
> * Daha fazla esneklik sağlamak için parametreli uygulamaları oluşturun.
> * Bir geçersiz kılma biçiminde daha belirli bir uygulama sunmak amacıyla uygulayıcılar etkinleştirin.

## <a name="prerequisites"></a>Önkoşullar

.NET Core çalıştırmak için makinenizi ayarlamak ihtiyacınız olacak dahil olmak üzere C# 8.0 Önizleme derleyici. C# 8 preview derleyici sürümünden itibaren kullanılabilir [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), veya en son [.NET Core 3.0 Önizleme SDK'sı](https://dotnet.microsoft.com/download/dotnet-core/3.0). .NET Core 3.0 Önizleme 4 sürümlerinde kullanılabilir varsayılan arabirimi üyeleridir.

## <a name="scenario-overview"></a>Senaryoya genel bakış

Bu öğreticide, bir müşteri ilişkisi kitaplığı 1 sürümü ile başlar. Başlangıç uygulaması alma bizim [depo github'da örnekleri](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship). Bu kitaplık yerleşik şirket kendi kitaplığı benimsemek için var olan uygulamalarla birlikte müşterilere yöneliktir. Bunlar, kullanıcıların en küçük arabirim tanımlarını uygulamak için kendi kitaplığı sağlanır. Bir müşteri için arabirim tanımı aşağıda verilmiştir:

[!code-csharp[InitialCustomerInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

Bunlar, bir sipariş temsil eden ikinci bir arabirim tanımlanan:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

Bu arabirimden ekip müşterileri için daha iyi bir deneyim oluşturmak kullanıcıları için bir kitaplık. Mevcut müşterilerle daha derin bir ilişki oluşturun ve aralarındaki ilişkiler ile yeni müşterilere geliştirmek için kendi hedef oluştu.

Şimdi, kitaplık bir sonraki sürümü için yükseltme zamanı geldi. İstenen özelliklerden biri, çok sayıda siparişleri olan müşteriler için bir bağlılık indirim sağlar. Bir müşteri sipariş yaptığında bu yeni bağlılık indirim uygulanır. Belirli indirim, tek tek her müşteri için kullanılan bir özelliktir. Her uygulaması ICustomer bağlılık indirim için farklı kuralları ayarlayabilirsiniz. 

Bu işlevsellik eklemek için en iyi şekilde geliştirmektir `ICustomer` arabirimi herhangi bir bağlılık indirim uygulamak için bir yöntem. Deneyimli geliştiriciler arasında önemli neden bu tasarımı öneri: "Kullanıma sunduk sonra arabirimleri sabittir! Bir değişiklik budur!" C#8.0 ekler *arabirim uygulamalarını varsayılan* arabirimleri yükseltme. Kitaplık yazarlar arabirimine yeni üyeler ekleyebilir ve bu üyeler için varsayılan bir uygulama sağlayın.

Varsayılan arabirim uygulamalarına yine de bu uygulamayı geçersiz kılmak herhangi bir implementors etkinleştirilirken bir arabirim yükseltmek geliştiricilerin sağlar. Kitaplığın kullanıcılar varsayılan uygulaması bir hataya neden olmayan değişiklik kabul edebilir. Kendi iş kuralları farklı olduğunda geçersiz kılabilirsiniz.

## <a name="upgrade-with-default-interface-members"></a>Varsayılan arabirim üyeleri ile yükseltme

Takım büyük olasılıkla varsayılan uygulama üzerinde anlaşılan: müşterilerin sadakatini indirim.

Yükseltme iki özelliği ayarlamak için işlevselliği sağlamalıdır: siparişler indirim ve indirim yüzdesi için uygun olması için gerekli. Bu mükemmel bir senaryo için varsayılan arabirim üyeleri sağlar. ICustomer arabirimi için bir yöntem ekleyin ve büyük olasılıkla uygulanmasını sağlar. Tüm mevcut ve yeni tüm uygulamaları varsayılan uygulamasını kullanın veya kendi sağlayın.

İlk olarak, uygulama için yeni yöntemi ekleyin:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

Kitaplık Yazar uygulama denetlemek için bir ilk testi şöyle yazmış:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

Test aşağıdaki bölümü dikkat edin:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

Bu tür dönüştürme `SampleCustomer` için `ICustomer` gereklidir. `SampleCustomer` Sınıfı için bir uygulama sağlaması gerekmez `ComputeLoyaltyDiscount`; tarafından sağlanan `ICustomer` arabirimi. Ancak, `SampleCustomer` sınıfı üyeleri arabirimlerinden devralır değil. Bu kural değişmedi. Bildirildi ve arabiriminde uygulanan herhangi bir yöntemi çağırmak için değişkenin arabirim türü olmalıdır `ICustomer` Bu örnekte.

## <a name="provide-parameterization"></a>Parametreleştirme sağlayın

Bu, iyi bir başlangıç noktasıdır. Ancak varsayılan çok kısıtlayıcı uygulamasıdır. Birçok tüketicileri bu sistemin farklı satın alma işlemleri, üyelik farklı bir uzunlukta veya farklı bir yüzde indirim sayısı eşiği tercih edebilirsiniz. Bu parametreleri ayarlamak için bir yol sağlayarak daha iyi bir yükseltme deneyimi için daha fazla müşteriye sağlayabilir. Varsayılan uygulama denetleme bu üç parametreleri ayarlar statik bir yöntem ekleyelim:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

Bu küçük kod parçasını gösterildiği çok sayıda yeni dil özellikleri yoktur. Arabirimleri artık alanlar ve yöntemler statik üyelerini içerebilir. Farklı erişim değiştiricileri de etkinleştirilir. Ek özel alanlar, yeni genel yöntemdir. Herhangi bir değiştiriciler, arabirim üyeleri üzerinde izin verilir.

Bağlılık indirim, ancak farklı parametreler, bilgi işlem genel formülü kullanan uygulamalar, özel bir uygulama sunmak amacıyla gerekmez; statik bir yöntem aracılığıyla bağımsız değişkenler ayarlayabilirler. Örneğin, aşağıdaki kod, "herhangi bir ayın üyelik birden fazla müşteriyle kazandırır bir müşteri artırma" ayarlar:

[!code-csharp[SetLoyaltyThresholds](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>Varsayılan uygulama genişletme

Şu ana kadar eklediğiniz kod kullanıcılar ilişkisiz bir kural kümesi sağlamak için veya, varsayılan uygulama gibi bir şey istediğiniz bu senaryoları için uygun bir uygulama sağlamıştır. Son bir özellik için şimdi biraz kullanıcıların üzerinde varsayılan uygulama oluşturmak için burada isteyebilirsiniz senaryolara olanak kodu yeniden düzenleyin. 

Yeni müşterilerin ilgisini çekin isteyen bir başlangıç göz önünde bulundurun. Bunlar, yeni bir müşterinin ilk sırada % 50 indirim sağlar. Aksi takdirde, mevcut müşteriler standart indirim kazanın. Kitaplık Yazar varsayılan uygulamasına taşınması gereken bir `protected static` herhangi bir sınıf için bu arabirimi uygulayan yöntemi, uygulama kodunda yeniden kullanın. Varsayılan uygulama arabirim üyesinin de paylaşılan bu yöntemi çağırır:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

Bu arabirimi uygulayan bir sınıfın bir uygulamada geçersiz kılma statik yardımcı yöntemini çağırın ve "yeni müşteri" sağlamak için bu mantığı genişletmek indirim:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

Tüm tamamlanan kodunda gördüğünüz bizim [depo github'daki örnekler] (başlangıç uygulaması alma bizim [depo github'da örnekleri](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/finished/customer-relationship).

Bu yeni özellikler, bu yeni üyeler için makul bir varsayılan bir uygulama olduğunda arabirimleri güvenli bir şekilde güncelleştirilmesi anlamına gelir. Birden çok sınıfları tarafından uygulanabilir tek işlevsel fikirleri ifade etmek için arabirimleri dikkatli bir şekilde tasarlayın. Bu yeni gereksinimleri için aynı işlev fikir bulunduğunda bu arabirim tanımları yükseltmek kolaylaştırır.
