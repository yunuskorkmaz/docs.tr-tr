---
title: 'Sunucusuz uygulamalar: Azure uygulama mimarisi ve desenleri'
description: 'Sunucusuz bir mimari Kılavuzu. Neden ve ne zaman, öğrenin, kurumsal uygulamalar için sunucusuz bir mimari (aksine, bir hizmet [Iaas] veya [PaaS] hizmet olarak Platform olarak altyapı) uygulamak için.'
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 6/26/2018
---

# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a>Sunucusuz uygulamalar: Azure uygulama mimarisi ve desenleri

![Sunucusuz uygulamalar e-kitap kapak gösteren ekran görüntüsü.](./media/index/serverless-apps-cover.jpg)

> İNDİRME bulunabilir: <https://aka.ms/serverless-ebook>

TARAFINDAN YAYIMLANAN

Microsoft Geliştirici bölme, .NET ve Visual Studio ürün takımları

Microsoft Corporation'ın bir bölme

One Microsoft Way

Redmond, Washington 98052-6399

Telif Hakkı © 2018 Microsoft Corporation

Tüm hakları saklıdır. Bu kitap içeriğini bir parçası çoğaltılamaz veya herhangi bir araçla yayımcı yazılı izni olmadan herhangi bir biçimdeki aktarılamaz.

Bu kitap sağlanan "olarak-olduğunu" ve yazarın görünümleri ve düşünceleri son derece ifade eder. Görünümleri ve düşünceleri son derece bilgi URL ve diğer Internet Web sitesi referansları da dahil olmak üzere bu kitap, ifade verilmeksizin değiştirilebilir.

Burada açıklanan bazı örnekler yalnızca çizim için sağlanmıştır ve bu kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya çıkarılmamalıdır.

Microsoft ve adresinde listelenmiş ticari <https://www.microsoft.com> "Ticari" Web sayfasında Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS Apple Inc.'in ticari markalarıdır.

Diğer tüm işaretleri ve logoları sahiplerinin özelliği var.

Yazar:

> **[Jeremy Likness](https://twitter.com/jeremylikness)**, üst düzey bulut Geliştirici Danışmanı, TEPE, Microsoft Corp.

Katkıda bulunan:

> **[Cecil Phillip](https://twitter.com/cecilphillip)**, bulut Geliştirici Danışmanı II, TEPE, Microsoft Corp.

Düzenleyiciler:

> **[Fatura Wagner](https://twitter.com/billwagner)**, üst düzey içerik geliştirici, TEPE, Microsoft Corp.

> **[Maira Wenzel](https://twitter.com/mairacw)**, üst düzey içerik geliştirici, TEPE, Microsoft Corp.

Katılımcılar ve gözden geçirenler:

> **[Steve Smith](https://twitter.com/ardalis)**, sahibi, Ardalis Hizmetleri.

## <a name="introduction"></a>Giriş

[Sunucusuz](https://azure.microsoft.com/solutions/serverless/) bulut platformları bulut saf yerel kod yönünde evrimidir. Sunucusuz, altyapıdan kaynaklanan yüklerden insulating sırasında iş mantığı geliştiriciler yakın getirir. "Hiçbir" server ancak bunun yerine, "daha az sunucu." açık olmayan bir modelidir Olay temelli sunucusuz kodudur. Kod, geleneksel bir HTTP web istek bir zamanlayıcı ya da bir dosya karşıya yükleme sonucu herhangi bir şey tarafından tetiklenebilir. Sunucusuz arkasında altyapı esnek taleplerini karşılamak üzere anında ölçek sağlar ve gerçek anlamda "kullandığınız kadarı için ödeme yaparsınız için." micro-fatura sunar Sunucusuz uygulamalar oluşturmak için yeni bir yol düşünmek ve yaklaşım gerektirir ve her sorun için doğru çözüm değildir. Bir geliştirici olarak size karar vermeniz gerekir:

* Avantajları ve dezavantajları sunucusuz nelerdir?
* Neden, kendi uygulamalarınıza sunucusuz göz önünde bulundurmalıyım?
* Nasıl, derleme, test, dağıtma ve sunucusuz kod bakımı?
* Burada, mevcut uygulamalarda sunucusuz kod geçirmek için mantıklı ve bu dönüşümü gerçekleştirmek için en iyi yolu nedir?

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz bulut yerel sunucusuz kullanan uygulamaların geliştirilmesini üzerinde odaklanır. Kitap avantajlarını vurgular ve sunucusuz uygulamalar geliştirme olası engelleri kullanıma sunar ve sunucusuz mimarileri araştırma sağlar. Nasıl sunucusuz birçok örnekleri kullanılabilir yanı sıra çeşitli sunucusuz tasarım desenlerini gösterilmiştir.

Bu kılavuz, Azure sunucusuz platformu bileşenlerini açıklar ve sunucusuz kullanmanın özellikle mantığınız odaklanır [Azure işlevleri](https://docs.microsoft.com/azure/azure-functions/functions-overview). Dayanıklı işlevler kullanarak durumuna bağlı sunucusuz uygulamalar uygulamak Tetikleyicileri ve bağlamaları nasıl erişileceği hakkında öğreneceksiniz. Son olarak, iş örnekler ve örnek olay incelemeleri bağlam ve belirlemek için başvuru çerçevesi sağlamaya yardımcı sunucusuz olmadığını doğru projeleriniz için bir yaklaşımdır.

## <a name="evolution-of-cloud-platforms"></a>Bulut platformları evrimi

Bir bulut platformunda birkaç yinelemelerin culmination sunucusuz. Gelişimi veri merkezindeki fiziksel metal başlamış ve bir hizmet (PaaS) altyapısı aracılığıyla bir hizmet (Iaas) ve Platform olarak progressed.

![Sunucusuz için şirket içi evrimi](./media/serverless-evolution-iaas-paas.png)

Geliştirme ve operasyon arasında önce bulut, anlaşılabilir bir sınırı vardı. Uygulama dağıtma gibi çok soruyu yanıtlayarak anlamına gelir:

* Donanım yüklensin mi?
* Nasıl güvenli bir makineye fiziksel erişimi var mı?
* Veri Merkezi kesintisiz güç kaynağı (UPS) gerektiriyor mu?
* Burada depolama yedekleri gönderilir?
* Yedek güç olması?

Liste ve ek yükü muazzamdı. Çoğu durumda, BT departmanlarının inanılmaz harcadığınız dağıtılacak zorlanan. Atık genişleme etkinleştirmek olağanüstü durum kurtarma ve bekleme sunucuları için yedekleme makinelerle sunucuların aşırı ayırma nedeniyle oluştu. Neyse ki, sanallaştırma teknolojisi sunulmasıyla (gibi [Hyper-V](/virtualization/hyper-v-on-windows/about/)) ile sanal makineleri (VM'ler) (Iaas) hizmet olarak altyapı için ortaya çıkmasına neden verdi. Sanallaştırılmış bir altyapı sunucularının standart ayarlama "üzerine." benzersiz sunucuları sağlama işlemini özelliğine sahip esnek bir ortam için önde gelen bir omurga olarak ayarlamak işlemlerine izin Daha da önemlisi, sanallaştırma aşama için "hizmet olarak." sanal makineler sağlamak için Bulutu kullanarak ayarlayın Şirketler, yedek güç veya fiziksel makineler hakkında endişelenmeden, iş dışında kolayca alabilirsiniz. Bunun yerine, sanal ortamda odaklanır.

İşlemler için çeşitli görevler yine siz sorumlu olduğundan Iaas hala ağır yükü gerektirir. Bu görevler aşağıdakileri içerir:

* Düzeltme eki uygulama ve sunucularını yedekleme.
* Paketleri yükleniyor.
* İşletim sisteminin güncel kalmasını sağlar.
* Uygulama izleme.

Bir sonraki aşamasıdır (PaaS) hizmet olarak Platform sağlayarak ek yükü azaltıldı. PaaS ile bulut sağlayıcısı işletim sistemleri güvenlik düzeltme eklerinin ve hatta belirli bir platforma desteklemek için gerekli paketleri işler. Bir VM oluşturma, ardından .NET Framework'ün güncelleştirilmesi ve Internet Information Services (IIS) sunucularını duran, yerine geliştiriciler basit bir "platform hedefi" "web uygulaması" veya "API uç noktası" gibi seçin ve doğrudan kod dağıtma. Altyapısıyla ilgili sorular için azaltılır:

* Boyutu hangi hizmetlerin gerekli mi?
* Ne Hizmetleri ölçeğini genişletme (daha fazla sunucuları veya düğümleri Ekle)?
* Ne Hizmetleri ölçeği artırma (sunucular veya düğümleri barındırma sunucusunun kapasitesini artırmak)?

Daha fazla sunucusuz, olay temelli kod üzerinde odaklanarak sunucuları soyutlar. Bir platform yerine, geliştiricilerin bir şey yapan bir mikro hizmet üzerinde odaklanabilirsiniz. Sunucusuz bir kod oluşturmak için iki anahtar sorular şunlardır:

* Neyin kod tetikleyeceğini?
* Kod ne yapar?

İle sunucusuz, altyapı soyutlanır. Bazı durumlarda, geliştirici artık konak hakkında hiç worries. Geliştirici, web isteklerini yönetmek için IIS, Kestrel, Apache veya başka bir web sunucusu bir örneği çalışıyor olsun veya olmasın, HTTP tetikleyicisi üzerinde odaklanır. Tetikleyici isteği için standart, platformlar arası yükü sağlar. Yükü yalnızca geliştirme sürecini basitleştirir, ancak test kolaylaştırır ve bazı durumlarda, kod platformlar arasında kolayca taşınabilir yapar.

Başka bir sunucusuz micro-fatura özelliğidir. Konak Web API uç noktaları için web uygulamaları için yaygındır. Geleneksel çıplak, Iaas ve PaaS hatta uygulamaları API'leri barındırmak için gereken kaynakları için sürekli olarak ödenir. Zaman bile, erişilen olmayan uç noktalarını barındırmak ödeme anlamına gelir. Genellikle tüm sistemin popüler uç noktaları destekleyen göre ölçeklendirilir için API adlı diğerlerinden daha fazla, bulabilirsiniz. Sunucusuz API'ler çağrıldığında değil, herhangi bir maliyet uygulanır için kullanım için ödeme yaparsınız ve her uç noktayı bağımsız olarak ölçeklendirme sağlar. Geçiş, çoğu durumda uç noktalarını desteklemek için sürekli maliyetleri önemli ölçüde azaltabilir.

## <a name="what-this-guide-doesnt-cover"></a>Bu kılavuzda ele alınmamıştır

Bu kılavuz, özellikle mimari yaklaşımları vurgular ve tasarım desenleri ve Azure işlevleri, uygulama ayrıntıları yakından değil [Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps), veya diğer sunucusuz platformları. Bu kılavuz, örneğin, Logic Apps veya Azure işlevleri, çıkış noktaları arası kaynak paylaşımı (CORS) yapılandırma, uygulama özel etki alanları veya SSL sertifikalarını karşıya yükleme gibi özellikleri ile Gelişmiş iş akışlarının kapsamıyordur. Bu ayrıntıları online kullanılabilir [Azure işlevleri belgelerinde](https://docs.microsoft.com/azure/azure-functions/functions-reference).

### <a name="additional-resources"></a>Ek kaynaklar

* [Azure Mimari Merkezi](https://docs.microsoft.com/azure/architecture/)
* [Bulut uygulamalarına yönelik en iyi yöntemler](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a>Kılavuzu kim kullanacak

Bu kılavuzda, geliştiricilere ve sunucusuz bileşenlerini şirket içinde veya kullanabilir .NET ile Kurumsal uygulamalar oluşturmak isteyen çözüm mimarlarına bulut için yazılmıştır. Geliştiriciler, mimarlar ve ilginizi teknik karar verenler için kullanışlıdır:

* Artıları ve eksileri sunucusuz geliştirme anlama
* Sunucusuz bir mimari yaklaşım öğrenme
* Sunucusuz uygulamalar örnek uygulamalar

## <a name="how-to-use-the-guide"></a>Kılavuz nasıl kullanılır?

Bu kılavuzun ilk bölümü nedenini inceler birkaç farklı mimari yaklaşım karşılaştırarak kaydının uygulanabilir bir seçenek sunucusuz. Yazılım geliştirme tüm yönlerini mimari kararlar tarafından etkilenen olduğundan teknolojiye ve geliştirme yaşam döngüsü, inceler. Kılavuzu sonra kullanım durumları inceler ve tasarım desenleri ve Azure işlevleri'ni kullanarak başvuru uygulamaları içerir. Her bölüm, belirli bir alanla ilgili daha fazla bilgi için ek kaynaklar içerir. İzlenecek yollar ve sunucusuz uygulaması pratik incelenmesi için kaynaklara sahip Kılavuzu burada sona eriyor.

## <a name="send-your-feedback"></a>Geri bildirim gönderin

Geri bildiriminiz Hoş Geldiniz için kılavuz ve ilgili örnekler sürekli, gelişen! Bu kılavuz nasıl geliştirilebilir hakkında açıklamalar varsa, üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın [GitHub sorunları](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Next](architecture-approaches.md)