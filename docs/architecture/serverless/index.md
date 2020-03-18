---
title: "Sunucusuz uygulamalar: Mimari, desenler ve Azure'u uygulama"
description: Sunucusuz mimari kılavuzu. Kurumsal uygulamalarınız için sunucusuz bir mimarinin (Hizmet Olarak Altyapı [IaaS] veya Hizmet Olarak Platform [PaaS]' ın aksine) ne zaman, neden ve nasıl uygulanacağı öğrenin.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 9dea7dbccb5c9e125f792e6a7287a7dd2fad26f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73093541"
---
# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a>Sunucusuz uygulamalar: Mimari, desenler ve Azure'u uygulama

![Serverless Apps e-kitap kapağını gösteren ekran görüntüsü.](./media/index/serverless-apps-cover.jpg)

> DOWNLOAD kullanılabilir:<https://aka.ms/serverless-ebook>

YAYIMLAYAN

Microsoft Developer Division, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif Hakkı © 2018 Microsoft Corporation tarafından

Tüm hakları saklıdır. Bu kitabın içeriğinin hiçbir bölümü, yayımcının yazılı izni olmadan herhangi bir biçimde veya herhangi bir şekilde çoğaltılamaz veya aktarılamaz.

Bu kitap "olduğu gibi" sağlanır ve yazarın görüş ve görüşlerini ifade eder. URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu kitapta ifade edilen görüşler, görüşler ve bilgiler önceden haber verilmeden değişebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve "Ticari <https://www.microsoft.com> Markalar" web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. şirketinin ticari markalarıdır.

Diğer tüm işaretler ve logolar ilgili sahiplerinin mülkiyetindedir.

Yazar:

> **[Jeremy Likness](https://twitter.com/jeremylikness)**, Kıdemli Bulut Savunucusu, Microsoft Corp.

Katılımcı:

> **[Cecil Phillip](https://twitter.com/cecilphillip)**, Kıdemli Bulut Savunucusu, Microsoft Corp.

Editörler:

> **[Bill Wagner](https://twitter.com/billwagner)**, Kıdemli İçerik Geliştiricisi, Microsoft Corp.

> **[Maira Wenzel,](https://twitter.com/mairacw)** Kıdemli İçerik Geliştiricisi, Microsoft Corp.

Katılımcılar ve gözden geçirenler:

> **[Steve Smith](https://twitter.com/ardalis)**, Sahibi, Ardalis Hizmetleri.

## <a name="introduction"></a>Giriş

[Serverless,](https://azure.microsoft.com/solutions/serverless/) bulut platformlarının saf bulut yerel kodu yönünde evrimidir. Sunucusuz, geliştiricileri altyapı kaygılarından izole ederken iş mantığına daha da yaklaştırıyor. Bu"sunucu yok" anlamına gelmez, daha çok "daha az sunucu" anlamına gelen bir desendir. Sunucusuz kod olay odaklıdır. Kod, geleneksel bir HTTP web isteğinden zamanlayıcıya veya dosya yüklemenin sonucuolan herhangi bir şey tarafından tetiklenebilir. Sunucusuz arkasındaki altyapı, elastik talepleri karşılamak için anında ölçek sağlar ve gerçekten "kullandığınız kadar ödeme" mikro fatura lama sunar. Serverless düşünme ve uygulama oluşturmak için yaklaşım yeni bir yol gerektirir ve her sorun için doğru çözüm değildir. Bir geliştirici olarak, karar vermeniz gerekir:

- Sunucusuz artıları ve eksileri nelerdir?
- Neden kendi uygulamalarınız için sunucusuz düşünmelisiniz?
- Sunucusuz kodunuzu nasıl oluşturabilir, sınayabilir, dağıtabilir ve koruyabilirsiniz?
- Varolan uygulamalarda kodu sunucusuza geçirmek nerede mantıklıdır ve bu dönüşümü gerçekleştirmenin en iyi yolu nedir?

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz, sunucusuz kullanan uygulamaların bulut yerel gelişimine odaklanır. Kitap yararları vurgular ve sunucusuz uygulamalar geliştirme potansiyel sakıncaları ortaya çıkarır ve sunucusuz mimarileri bir anket sağlar. Sunucusuzların nasıl kullanılabileceğinin birçok örneği, çeşitli sunucusuz tasarım desenleri ile birlikte gösterilmiştir.

Bu kılavuz, Azure sunucusuz platformunun bileşenlerini açıklar ve özellikle [Azure İşlevlerini](https://docs.microsoft.com/azure/azure-functions/functions-overview)kullanarak sunucusuz ların uygulanmasına odaklanır. Tetikleyiciler ve bağlamaların yanı sıra dayanıklı işlevleri kullanarak duruma dayanan sunucusuz uygulamaların nasıl uygulanacağı hakkında bilgi edineceksiniz. Son olarak, iş örnekleri ve örnek incelemeler, sunucusuz projeleriniz için doğru yaklaşım olup olmadığını belirlemek için bağlam ve bir referans çerçevesi sağlamaya yardımcı olacaktır.

## <a name="evolution-of-cloud-platforms"></a>Bulut platformlarının evrimi

Serverless, bulut platformlarının birkaç yinelemesinin doruk noktasıdır. Evrim, veri merkezinde fiziksel metal ile başladı ve Altyapı hizmet olarak (IaaS) ve Platform as a Service (PaaS) ile ilerledi.

![Şirket içi sunucusuza evrim](./media/serverless-evolution-iaas-paas.png)

Bulutun önünde, geliştirme ve işlemler arasında fark edilebilir bir sınır vardı. Bir uygulamayı dağıtmak, aşağıdaki gibi sayısız soruyu yanıtlamak anlamına geliyordu:

- Hangi donanım yüklenmelidir?
- Makineye fiziksel erişim nasıl güvence altına alınmıştır?
- Veri merkezi kesintisiz güç kaynağı (UPS) gerektirir mi?
- Depolama yedekleri nereye gönderilir?
- Gereksiz güç olmalı mı?

Liste devam ediyor ve genel gider çok büyüktü. Birçok durumda, BT departmanları inanılmaz atıklarla uğraşmak zorunda kaldı. Atık, sunucuların olağanüstü durum kurtarma ve bekleme sunucuları için yedekleme makineleri olarak aşırı tahsisinden kaynaklanıyordu. Neyse ki, Sanal Makineler (VMs) ile sanallaştırma teknolojisi [(Hyper-V](/virtualization/hyper-v-on-windows/about/)gibi) giriş Bir Hizmet olarak Altyapı (IaaS) yol açtı. Sanallaştırılmış altyapı, operasyonların omurga olarak standart bir sunucu kümesi kurmasına izin vererek, "isteğe bağlı" benzersiz sunucular sağlama yeteneğine sahip esnek bir ortama yol açtı. Daha da önemlisi, sanallaştırma sanal makineleri "hizmet olarak" sağlamak için bulutu kullanma aşamasını belirlir. Şirketler kolayca gereksiz güç veya fiziksel makineler hakkında endişe iş çıkmak olabilir. Bunun yerine, sanal ortama odaklandılar.

Operasyonlar hala çeşitli görevlerden sorumlu olduğundan IaaS hala ağır genel merkez gerektirir. Bu görevler aşağıdakileri içerir:

- Sunucuları yama ve yedekleme.
- Paketleri yükleme.
- İşletim sistemini güncel tutmak.
- Uygulamayı izleme.

Bir sonraki evrim, Platform'u Hizmet Olarak (PaaS) sağlayarak yükü azalttı. Bulut sağlayıcısı, PaaS ile işletim sistemlerini, güvenlik yamaları ve hatta belirli bir platformu desteklemek için gerekli paketleri işler. Geliştiriciler, .NET Framework'ü yapılandırıp Internet Information Services (IIS) sunucularını ayağa kattıktan sonra bir VM oluşturmak yerine, "web uygulaması" veya "API bitiş noktası" gibi bir "platform hedefi" seçin ve kodu doğrudan dağıtın. Altyapı soruları aşağıdakilere indirgenir:

- Hangi boyutta hizmetlere ihtiyaç vardır?
- Hizmetler nasıl ölçeklendirilir (daha fazla sunucu veya düğüm ekleyin)?
- Hizmetler nasıl ölçeklendirilir (barındırma sunucularının veya düğümlerinin kapasitesini artırır)?

Sunucusuz daha fazla özet sunucular olay odaklı kod odaklanarak sunucular. Geliştiriciler bir platform yerine tek bir şey yapan bir mikro hizmete odaklanabilirler. Sunucusuz kodu oluşturmak için iki önemli soru şunlardır:

- Kodu ne tetikler?
- Kod ne işe yarıyor?

Sunucusuz, altyapı soyutlanır. Bazı durumlarda, geliştirici artık ana bilgisayar hakkında hiç endişe duymaz. Geliştirici, IIS, Kestrel, Apache veya başka bir web sunucusunun bir örneği web isteklerini yönetmek için çalışıyor olsun veya olmasın, bir HTTP tetikleyicisine odaklanır. Tetikleyici, istek için standart, çapraz platform yükünü sağlar. Yük yalnızca geliştirme sürecini basitleştirmekle kalmıyor, aynı zamanda sınamayı da kolaylaştırır ve bazı durumlarda kodu platformlar arasında kolayca taşınabilir hale getirir.

Sunucusuz bir diğer özelliği mikro faturalamadır. Web uygulamalarının Web API uç noktalarını barındırması yaygındır. Geleneksel çıplak metal, IaaS ve hatta PaaS uygulamalarında, API'lere ev sahipliği yapacak kaynaklar sürekli olarak ödenir. Bu, uç noktalara erişilemese bile ev sahipliği yapmak için ödeme yaptığınız anlamına gelir. Genellikle bir API diğerlerinden daha fazla denir bulacaksınız, bu nedenle tüm sistem popüler uç noktaları destekleyen dayalı ölçeklendirilir. Sunucusuz, her bitiş noktasını bağımsız olarak ölçeklendirmenize ve kullanım için ödeme yapmanızı sağlar, bu nedenle API'ler çağrılmadığında hiçbir maliyet tahakkuk etmez. Geçiş birçok durumda önemli ölçüde uç noktaları desteklemek için devam eden maliyeti azaltabilir.

## <a name="what-this-guide-doesnt-cover"></a>Bu kılavuzun kapsamadığı

Bu kılavuz özellikle mimari yaklaşımları ve tasarım desenlerini vurgular ve Azure İşlevlerinin, [Logic Apps'ın](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps)veya diğer sunucusuz platformların uygulama ayrıntılarına derinlemesine dalma değildir. Bu kılavuz, örneğin, Mantık Uygulamaları ile gelişmiş iş akışlarını veya Çapraz Başlangıç Kaynak Paylaşımı (CORS) yapılandırma, özel etki alanları uygulama veya SSL sertifikaları yükleme gibi Azure Işlevlerinin özelliklerini kapsamaz. Bu ayrıntılar, çevrimiçi [Azure İşlevleri belgeleri](https://docs.microsoft.com/azure/azure-functions/functions-reference)aracılığıyla kullanılabilir.

### <a name="additional-resources"></a>Ek kaynaklar

- [Azure Mimari merkezi](https://docs.microsoft.com/azure/architecture/)
- [Bulut uygulamaları için en iyi uygulamalar](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a>Kılavuzu kimler kullanmalı?

Bu kılavuz, .NET ile şirket içinde veya bulutta sunucusuz bileşenler kullanabilen kurumsal uygulamalar oluşturmak isteyen geliştiriciler ve çözüm mimarları için yazılmıştır. Aşağıdakilerle ilgilenen geliştiriciler, mimarlar ve teknik karar vericiler için yararlıdır:

- Sunucusuz geliştirmenin artılarını ve eksilerini anlama
- Sunucusuz mimariye nasıl yaklaşılabildiğini öğrenme
- Sunucusuz uygulamaların örnek uygulamaları

## <a name="how-to-use-the-guide"></a>Kılavuzu niçin kullanılır?

Bu kılavuzun ilk bölümü, birkaç farklı mimari yaklaşımları karşılaştırarak sunucusuz neden uygun bir seçenek olduğunu inceler. Yazılım geliştirmenin tüm yönleri mimari kararlardan etkiledığından, hem teknolojiyi hem de geliştirme yaşam döngüsünü inceler. Kılavuz daha sonra kullanım servis taleplerini ve tasarım modellerini inceler ve Azure İşlevlerini kullanarak başvuru uygulamalarını içerir. Her bölüm, belirli bir alan hakkında daha fazla bilgi edinmek için ek kaynaklar içerir. Kılavuz, yol boyunca ve sunucusuz uygulamanın uygulamalı keşfi için kaynaklarla sona erer.

## <a name="send-your-feedback"></a>Geri bildiriminizi gönderin

Kılavuz ve ilgili örnekler sürekli gelişmektedir, bu nedenle geribildirim memnuniyetle karşılanır! Bu kılavuzun nasıl geliştirilebileceği yle ilgili yorumlarınız varsa, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerine oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.

>[!div class="step-by-step"]
>[Sonraki](architecture-approaches.md)
