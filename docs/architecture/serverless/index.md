---
title: 'Sunucusuz uygulamalar: Mimari, desenler ve Azure’ı uygulama'
description: Sunucusuz mimari Kılavuzu. Kurumsal uygulamalarınız için (hizmet olarak altyapı [IaaS] veya hizmet olarak platform [PaaS]) ne zaman, neden ve nasıl uygulanacağını öğrenin.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 148a79e39c047897719e4f97efd84676b1b92636
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676756"
---
# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a>Sunucusuz uygulamalar: Mimari, desenler ve Azure’ı uygulama

![Sunucusuz uygulamalar eKitap kapağını gösteren ekran görüntüsü.](./media/index/serverless-apps-cover.jpg)

> INDIRME:<https://aka.ms/serverless-ebook>

YAYIMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı © 2018 Microsoft Corporation

Tüm hakları saklıdır. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.

Burada gösterilen bazı örnekler yalnızca gösterim amaçlıdır ve hayal ürünüdür. Hiçbir gerçek ilişkilendirme veya bağlantı amaçlanmaz veya çıkarsanmamalıdır.

Microsoft ve "ticari markalar" <https://www.microsoft.com> Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. ' in ticari markalarıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

Geliştirici

> **[Jeremy Liksizlik](https://twitter.com/jeremylikness)** , SR. Cloud Developer Advo, tepesinde, Microsoft Corp.

Mcý

> **[CECIL Phillip](https://twitter.com/cecilphillip)** , bulut GELIŞTIRICI Danışmanı II, tepesinde, Microsoft Corp.

Edit

> **[Bill Wagner](https://twitter.com/billwagner)** , kıdemli içerik GELIŞTIRICI, tepesinde, Microsoft Corp.

> **[Maira Wenzel](https://twitter.com/mairacw)** , kıdemli içerik GELIŞTIRICISI, tepesinde, Microsoft Corp.

Katılımcılar ve gözden geçirenler:

> **[Steve Smith](https://twitter.com/ardalis)** , Owner, Ardalış Hizmetleri.

## <a name="introduction"></a>Giriş

[Sunucusuz](https://azure.microsoft.com/solutions/serverless/) , bulut platformlarının saf bulut yerel kodu yönünde geliştiğinden oluşur. Sunucusuz, geliştiricilerin altyapı kaygılarından ayrı olarak iş mantığına yaklaşmasını sağlar. Bu, "sunucu yok", ancak bunun yerine "daha az sunucu" olmayan bir modeldir. Sunucusuz kod olay odaklı. Kod, geleneksel bir HTTP Web isteğinden bir zamanlayıcıya veya bir dosya yükleme sonucuna göre tetiklenebilir. Sunucusuz 'ın arkasındaki altyapı, esnek taleplerini karşılamak üzere anında ölçeklendirmeye olanak tanır ve gerçekten "kullandığınız kadar ödeyin" ile Micro-faturalandırma olanağı sunar. Sunucusuz, uygulama oluşturmaya yönelik yeni bir düşünce ve yaklaşım sağlar ve her sorun için doğru çözüm değildir. Bir geliştirici olarak, şunları yapmanız gerekir:

* Sunucusuz 'un olumlu ve olumsuz yönleri nelerdir?
* Kendi uygulamalarınız için neden sunucusuz düşünmeniz gerekir?
* Sunucusuz kodunuzu nasıl oluşturabilir, test edebilir, dağıtabilir ve bakımını yapabilirsiniz?
* Burada, mevcut uygulamalarda kodu sunucusuz olarak geçirmek ve bu dönüştürmeyi gerçekleştirmenin en iyi yolu nedir?

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz, sunucusuz kullanan uygulamaların yerel olarak geliştirilmesine odaklanır. Kitap, avantajları vurgular ve sunucusuz uygulamalar geliştirmenin olası dezavantajlarını sunar ve sunucusuz mimarilerin bir anketini sağlar. Sunucusuz 'ın nasıl kullanılabileceği hakkında birçok örnek, çeşitli sunucusuz tasarım desenleriyle birlikte gösterilmektedir.

Bu kılavuzda, Azure sunucusuz platformunun bileşenleri açıklanmakta ve özellikle de [Azure işlevleri](https://docs.microsoft.com/azure/azure-functions/functions-overview)kullanılarak sunucusuz uygulamaya odaklanılmıştır. Tetikleyiciler ve bağlamalar hakkında bilgi edineceksiniz ve dayanıklı işlevler kullanılarak duruma bağlı sunucusuz uygulamaların nasıl uygulanacağı hakkında bilgi edineceksiniz. Son olarak, iş örnekleri ve örnek olay incelemeleri, projelerinize yönelik doğru yaklaşım olup olmadığını tespit etmek için bağlam ve başvuru çerçevesinin sağlanmasına yardımcı olur.

## <a name="evolution-of-cloud-platforms"></a>Bulut platformlarının gelişi

Sunucusuz, bulut platformlarının birkaç yinelemesine ilişkin bir kültürde. Evrimler, veri merkezinde fiziksel metal ve hizmet olarak platform (IaaS) ve hizmet olarak platform (PaaS) üzerinden ilerlemedi.

![Şirket içinden sunucusuz 'a evle](./media/serverless-evolution-iaas-paas.png)

Buluttan önce, geliştirme ve işlemler arasında ayrılabilir bir sınır vardı. Uygulama dağıtımı, şunun gibi sayısız sorularını yanıtlayan:

* Hangi donanımların yüklenmesi gerekir?
* Makineye fiziksel erişim nasıl güvenlidir?
* Veri merkezi bir kesintisiz güç kaynağı (UPS) gerektiriyor mu?
* Depolama yedeklemeleri nereden gönderilir?
* Gereksiz güç olmalıdır mi?

Liste açık ve ek yük çok büyük. Birçok durumda, BT departmanları inanılmaz atık ile başa çıkmaya zorlandı. Çöp kutusu, daha fazla sunucu ayırmayı etkinleştirmek için olağanüstü durum kurtarma ve bekleme sunucularına yönelik yedekleme makineleri olarak aşırı ayrılmasından kaynaklanır. Neyse ki, sanallaştırma teknolojisinin ( [Hyper-V](/virtualization/hyper-v-on-windows/about/)gibi) sanal makineler (VM) ile kullanıma sunulması, hizmet olarak altyapı (IaaS) için bir artış vermiştir. Sanallaştırılmış altyapı, bir standart sunucu kümesini omurga olarak ayarlamaya izin verilir ve bu, "isteğe bağlı" benzersiz sunucular sağlayan esnek bir ortama önde gelen bir işlem sağlar. Daha önemli olan sanallaştırma, bulutu kullanarak "hizmet olarak" sanal makineleri sağlamaya yönelik aşamayı ayarladı. Şirketler, yedekli güç veya fiziksel makineler hakkında endişelenmeyi kolayca alabilirler. Bunun yerine, sanal ortama odaklanırlar.

IaaS, hala çeşitli görevlerden sorumlu olduğundan ağır yük gerektirir. Bu görevler aşağıdakileri içerir:

* Sunucuları düzeltme eki uygulama ve yedekleme.
* Paketler yükleniyor.
* İşletim sistemini güncel tutma.
* Uygulamayı izleme.

Sonraki evde bir hizmet olarak platform (PaaS) sağlayarak yükü azalttı. PaaS ile, bulut sağlayıcısı işletim sistemlerini, güvenlik düzeltme eklerini ve hatta belirli bir platformu desteklemek için gereken paketleri işler. Geliştiriciler, .NET Framework ve Internet Information Services (IIS) sunucularını yapılandırmak yerine, yalnızca "Web uygulaması" veya "API uç noktası" gibi bir "Platform hedefi" seçer ve kodu doğrudan dağıtır. Altyapı soruları şu şekilde azaltılır:

* Hangi boyut Hizmetleri gerekir?
* Hizmetler nasıl ölçeklendirilir (daha fazla sunucu veya düğüm ekleyin)?
* Hizmetler nasıl ölçeklendirilir (barındırma sunucularının veya düğümlerin kapasitesini artırın)?

Olay odaklı koda odaklanarak sunucusuz daha fazla sunucu soyutlar. Geliştiriciler bir platform yerine, bir şeyi yapan bir mikro hizmete odaklanabilir. Sunucusuz kod oluşturmaya yönelik iki temel soru şunlardır:

* Kod ne tetikler?
* Kod ne yapar?

Sunucusuz ile altyapı soyutlanmıştır. Bazı durumlarda, geliştirici artık ana bilgisayarla ilgili olarak hiçbir şey değildir. Web isteklerini yönetmek için IIS, Kestrel, Apache veya diğer Web sunucusunun bir örneğinin çalışıp çalışmadığını, geliştirici bir HTTP tetikleyicisine odaklanır. Tetikleyici, istek için standart, platformlar arası yük sağlar. Yük yalnızca geliştirme sürecini basitleştirir, ancak sınamayı kolaylaştırır ve bazı durumlarda kodu platformlar arasında kolayca taşınabilir hale getirir.

Sunucusuz 'ın başka bir özelliği mikro faturalandırmaya sahiptir. Web uygulamalarının Web API uç noktalarını barındırması yaygındır. Geleneksel çıplak, IaaS ve hatta PaaS uygulamalarında, API 'Leri barındırmak için kaynaklar sürekli olarak ödenir. Bu da, erişilmesi gerekmediği zaman uç noktaları barındırmak için ödeme yaparsınız. Genellikle bir API 'nin diğerlerinden daha fazla adı olduğunu fark edersiniz, bu nedenle tüm sistem popüler uç noktaları desteklemeye göre ölçeklendirilir. Sunucusuz, her bitiş noktasını bağımsız olarak ölçeklendirmenize ve kullanım için ödeme yapmanıza olanak tanıdığından, API 'Ler çağrılmaması durumunda herhangi bir maliyet tahakkuk etmemektedir. Geçiş, uç noktaları desteklemeye yönelik sürekli maliyeti önemli ölçüde azaltarak çok sayıda durumda olabilir.

## <a name="what-this-guide-doesnt-cover"></a>Bu kılavuzda ele alınmamıştır

Bu kılavuz, mimari yaklaşımları ve tasarım düzenlerini önemli bir şekilde vurgular ve Azure Işlevleri, [Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps)veya diğer sunucusuz platformların uygulama ayrıntılarına yakından bakış. Bu kılavuz, örneğin, çıkış noktaları arası kaynak paylaşımı 'nı (CORS) yapılandırma, özel etki alanları uygulama veya SSL sertifikalarını karşıya yükleme gibi Azure Işlevlerinin Logic Apps veya özelliklerine sahip gelişmiş iş akışlarını kapsamaz. Bu ayrıntılar çevrimiçi [Azure işlevleri belgeleri](https://docs.microsoft.com/azure/azure-functions/functions-reference)aracılığıyla sağlanır.

### <a name="additional-resources"></a>Ek kaynaklar

* [Azure mimari Merkezi](https://docs.microsoft.com/azure/architecture/)
* [Bulut uygulamaları için en iyi uygulamalar](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a>Kılavuzu kimler kullanmalıdır?

Bu kılavuz, şirket içinde veya bulutta sunucusuz bileşenleri kullanabilecek .NET ile kurumsal uygulamalar oluşturmak isteyen geliştiriciler ve çözüm mimarları için yazılmıştır. Geliştiriciler, mimarlar ve ile ilgili teknik karar mekanizmaları için yararlı olacaktır:

* Sunucusuz geliştirme uzmanlarının avantajlarını ve dezavantajlarını anlama
* Sunucusuz mimariye yaklaşımı öğrenme
* Sunucusuz uygulamaların örnek uygulamaları

## <a name="how-to-use-the-guide"></a>Kılavuzu kullanma

Bu kılavuzun ilk bölümü, farklı mimari yaklaşımlarını karşılaştırarak sunucusuz 'ın neden uygun bir seçenek olduğunu inceler. Yazılım geliştirmenin tüm yönleri mimari kararlara göre etkilendiğinden hem teknoloji hem de geliştirme yaşam döngüsünü inceler. Kılavuz daha sonra kullanım örneklerini ve tasarım düzenlerini inceler ve Azure Işlevleri 'ni kullanarak başvuru uygulamaları içerir. Her bölüm, belirli bir alan hakkında daha fazla bilgi edinmek için ek kaynaklar içerir. Kılavuz, daha az uygulama için izlenecek yollar ve uygulamalı araştırma kaynakları ile sonlanır.

## <a name="send-your-feedback"></a>Geri bildiriminizi gönderin

Kılavuz ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı! Bu kılavuzun nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.

>[!div class="step-by-step"]
>[Next](architecture-approaches.md)
