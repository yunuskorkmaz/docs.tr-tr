---
title: Eski tek yapılı .NET Framework uygulamaları geçirme Windows kapsayıcıları
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Eski tek yapılı .NET Framework uygulamaları geçirme Windows kapsayıcıları
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: a12012f115629a79734c18c3bc75733ae2fc8195
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578839"
---
# <a name="migrating-legacy-monolithic-net-framework-applications-to-windows-containers"></a>Eski tek yapılı .NET Framework uygulamaları geçirme Windows kapsayıcıları

*Geliştirme geliştirmek ve test ortamları ve eski .NET Framework teknolojileri gibi Web tabanlı uygulamaları dağıtmak için bir yol olarak Windows kapsayıcıları kullanılabilir* *Forms. Bu şekilde eski uygulamalar için kapsayıcıları kullanma "yükseltme ve shift" senaryo olarak adlandırılır.*

Bu kılavuzun önceki bölümlerde iş uygulamaları farklı kapsayıcılar her küçük, odaklanmış bir hizmeti çalıştıran dağıtıldığı bir mikro mimarisi championed. Bu hedefe birçok avantaj vardır. Yeni geliştirme bu yaklaşımı önemle tavsiye edilir. İşletme açısından kritik uygulamalar yeterli rearchitecture ve yeniden uygulama maliyetini yaslamak için de yararlı olacaktır.

Ancak her uygulama yeterli maliyeti yaslamak için yararlı olacaktır. Bu uygulamaların kapsayıcı senaryosunda kullanılan anlamına gelmez.

Bu bölümde, biz eShopOnContainers, Şekil 7-1'de gösterilen için uygulama inceleyeceksiniz. Bu uygulamayı görüntülemek ve ürün kataloğu düzenlemek için eShopOnContainers Kurumsal takım üyeleri tarafından kullanılacak.

![](./media/image1.png)

**Şekil 7-1**. Bir Windows kapsayıcısı üzerinde ASP.NET Web Forms uygulaması (eski teknolojisi)

Bu, göz atın ve Katalog girişleri değiştirmek için kullanılan bir Web Forms uygulamasıdır. Web Forms bağımlılık Web Forms yeniden yazılmıştır ve ASP.NET Core MVC yerine kullanır sürece bu uygulama .NET Core üzerinde çalışmaz anlamına gelir. Bu değişiklik yapmadan kapsayıcılardaki gibi uygulamaları nasıl çalıştırabileceğiniz görürsünüz. Ayrıca, burada bazı işlevler ayrı mikro taşındı, ancak çoğu işlevselliği tek yapılı uygulamada kalır bir karma modda çalışmak için küçük değişiklikler nasıl yapabileceğiniz görürsünüz.

## <a name="benefits-of-containerizing-a-monolithic-application"></a>Tek yapılı bir uygulama containerizing avantajları

Catalog.WebForms uygulama eShopOnContainers GitHub deposunda kullanılabilir (<https://github.com/dotnet/eShopOnContainers>). Bu uygulama, yüksek kullanılabilirlik veri deposuna erişilirken tek başına bir web uygulamasıdır. Buna rağmen bir kapsayıcıda uygulama çalıştırmanın avantajı vardır. Uygulama için bir görüntü oluşturun. O noktadan itibaren her dağıtım aynı ortamda çalışır. Her kapsayıcı aynı işletim sistemi sürümünü kullanır, yüklü bağımlılıkları aynı sürümü, aynı çerçevesi kullanır ve aynı işlemi kullanılarak oluşturulur. Visual Studio 2017 Şekil 7-2 yüklenen uygulama görebilirsiniz.

![](./media/image2.png)

**Şekil 7-2**. Katalog Yönetimi Visual Studio 2017 Web Forms uygulamasında

Ayrıca, geliştiricilerin tüm uygulama tutarlı bu ortamda çalıştırabilirsiniz. Yalnızca belirli sürümleriyle görünür sorunları hemen bir hazırlık veya üretim ortamında görünmesini yerine geliştiriciler için görünür. Uygulamaları kapsayıcılarında çalıştırdığınızda geliştirme ortamları ve geliştirme ekibi arasında arasındaki farklar daha az önemli.

Son olarak, kapsayıcılı uygulamaların daha düz genişleme eğri vardır. Sahip olduğunuz öğrenilen nasıl kapsayıcılı uygulamaların daha fazla kapsayıcı bir VM'de veya fiziksel bir makine daha fazla kapsayıcılarını sağlamak. Bu daha yüksek yoğunluk ve daha az gerekli dönüşür kaynakları.

Bu nedenlerle, bir "yükseltme ve shift" işlemini kullanarak bir Docker kapsayıcısı içinde çalışan eski tek yapılı uygulamalar göz önünde bulundurun. "Kaldırın ve shift" açıklar görevin kapsamı tümcecik:, *Yükselt* bir fiziksel veya sanal makine, tüm uygulama ve *shift* içine bir kapsayıcı. İdeal durumlarda bir kapsayıcıda çalıştırmak için uygulama kodu herhangi bir değişiklik yapmak gerekmez.

## <a name="possible-migration-paths"></a>Olası geçiş yolları

Tek yapılı bir uygulama, veri erişim kitaplıkları da dahil olmak üzere tüm kodu içeren bir web uygulaması Catalog.Webforms uygulamasıdır. Veritabanını farklı bir yüksek kullanılabilirlik makinede çalıştırır. Bu yapılandırma sahte katalog hizmetini kullanarak örnek kodda benzetimli: Saf yükseltme shift senaryo benzetimini yapmak için bu sahte verileri karşı Catalog.WebForms uygulamayı çalıştırabilirsiniz. Bu kod değişiklikleri olmadan bir kapsayıcıdaki tüm çalıştırmak için varolan varlıkları taşımak en basit geçiş yol gösterir. Bu yol tamamlandıktan ve mikro hizmetler için taşıma işlevselliği en az etkileşimiyle sahip uygulamalar için uygundur.

Ancak, eShopOnContainers Web sitesi zaten farklı senaryolar için mikro kullanarak veri depolama erişiyor. Bazı küçük ek değişiklikler katalog düzenleyiciye Kataloğu veri depolama doğrudan erişimini yerine katalog mikro hizmet yararlanmak için yapılabilir.

Bu değişiklikler, kendi uygulamalarınız için continuum gösterir. Mevcut uygulamaların tamamen tamamen yeni bir katılmak için uygulamanın yeniden yazma işlemi için yeni mikro bazıları erişmesine olanak veren küçük değişiklikler yapmak kapsayıcıları, varolan bir uygulamayı değişiklik olmadan taşınmasını gelen herhangi bir şey yapabilirsiniz mikro hizmet tabanlı mimari. Doğru yol maliyeti geçişi ve hiçbir geçirmeden avantajları bağlıdır.

## <a name="application-tour"></a>Uygulama turu

Catalog.WebForms çözüm yükleyin ve uygulamayı bir tek başına uygulama olarak çalıştırın. Bu yapılandırmada, kalıcı depolama veritabanı yerine, verileri döndürmek için sahte bir hizmet uygulaması kullanır. Uygulama Autofac kullanır (<https://autofac.org/>) bir tersine çevirme (IOC) denetim kapsayıcısının olarak. Bağımlılık ekleme (dı) kullanarak, sahte verileri veya dinamik Kataloğu veri hizmeti kullanmak için uygulamayı yapılandırabilirsiniz. (Biz daha dı hakkında kısa bir süre içinde anlatılmıştır.) Başlangıç kodu useFake ayarı web.config dosyalarından okur ve sahte veri hizmeti veya dinamik katalog hizmeti eklemesine Autofac kapsayıcı yapılandırır. Uygulamanın web.config dosyasında false olarak ayarlanmış useFake çalıştırırsanız, katalog verilerini görüntüleme Web Forms uygulaması bakın.

Bu uygulamada kullanılan teknikleri çoğunu Web Forms kullanan herkes için çok bilgi sahibi olmanız gerekir. Ancak, katalog mikro hizmet tanınmayan olabilir iki teknikleri tanıtır: bağımlılık ekleme (hangi daha önce değinilen dı) ve zaman uyumsuz veri depolarında Web Forms ile çalışır.

DI tüm gerekli kaynakları tahsis sınıfları yazma tipik olan nesne yönelimli stratejisi tersine çevirir. Bunun yerine, sınıflar, hizmet kapsayıcısından bağımlılıklarını isteyin. DI avantajı, test veya diğer ortamlarını desteklemek için fakes ile (mocks) dış hizmetler değiştirebilir ' dir.

DI kapsayıcı sahte katalog verilerini veya çalışan hizmetin canlı verileri kullanıp kullanmayacağınızı denetlemek için web.config appSettings yapılandırması kullanır. Uygulama kapsayıcı oluşturur ve bağımlılıkları eklemesine öncesi istek işleyicisi kaydeden bir HTTP nesne kaydeder. Bu kodu aşağıdaki gibi görünen Modules/AutoFacHttpModule.cs dosyasında görebilirsiniz:

```cs
private static IContainer CreateContainer()
{
  // Configure AutoFac:
  // Register Containers:

  var settings = WebConfigurationManager.AppSettings;
  var useFake = settings["usefake"];
  bool fake = useFake == "true";
  var builder = new ContainerBuilder();

  if (fake)
  {
    builder.RegisterType<CatalogMockService>()
    .As<ICatalogService>();
  }
  else
  {
    builder.RegisterType<CatalogService>()
    .As<ICatalogService>();
    builder.RegisterType<RequestProvider>()
    .As<IRequestProvider>();
  }

  var container = builder.Build();
  return container;
}

private void InjectDependencies()
{
  if (HttpContext.Current.CurrentHandler is Page page)
  {
    // Get the code-behind class that we may have written
    var pageType = page.GetType().BaseType;

    // Determine if there is a constructor to inject, and grab it
    var ctor = (from c in pageType.GetConstructors()
                where c.GetParameters().Length > 0
                select c).FirstOrDefault();

    if (ctor != null)
    {
      // Resolve the parameters for the constructor
      var args = (from parm in ctor.GetParameters()
                  select Container.Resolve(parm.ParameterType))
                  .ToArray();

      // Execute the constructor method with the arguments resolved
      ctor.Invoke(page, args);
    }

    // Use the Autofac method to inject any
    // properties that can be filled by Autofac
    Container.InjectProperties(page);
  }
}
```

Uygulama sayfaları (Default.aspx.cs ve EditPage.aspx.cs) Bu bağımlılıklar ele oluşturucular tanımlayın. Varsayılan Oluşturucu hala mevcut ve erişilebilir olduğunu unutmayın. Aşağıdaki kod altyapısı gerekir.

```cs
protected _Default() { }

public _Default(ICatalogService catalog) => this.catalog = catalog;
```

Katalog API'leri tüm zaman uyumsuz yöntem bulunmaktadır. Web Forms artık destekliyor bunlar tüm veri denetimleri için. Catalog.WebForms uygulama model bağlama için listesi kullanır ve sayfaları; sayfalarında Denetimler görev döndüren zaman uyumsuz işlemleri belirtin SelectMethod, UpdateMethod, InsertMethod ve DeleteMethod özellikleri tanımlayın. Bir denetime bağlı yöntemleri zaman uyumsuz olduğunda web Forms denetimleri anlayın. Zaman uyumsuz select yöntemleri kullanarak disk belleği destekleyemez olduğunda tek kısıtlama karşılaştığınız. Out parametresi disk belleği imza gerektirir ve zaman uyumsuz yöntemleri out Parametreleri olamaz. Bu aynı teknik veri Kataloğu hizmetinden gerektiren diğer sayfalarında kullanılır.

Web Forms uygulama kataloğu için varsayılan yapılandırmayı catalog.api hizmetinin sahte bir uygulama kullanır. Bu mock geliştirme ortamlarında catalog.api hizmet bağımlılık kaldırarak bazı görevler basitleştirir, veriler için sabit kodlanmış bir veri kümesi kullanır.

## <a name="lifting-and-shifting"></a>Kaldırma ve kaydırma

Visual Studio, uygulama containerizing için harika desteği sağlar. Proje düğümüne sağ tıklayın ve ardından **Ekle** ve **Docker Destek**. Docker proje şablonu adlı çözüm için yeni bir proje ekler **docker-oluşturan**. Proje oluşturma (ya da derleme) gerekir ve gerekli kapsayıcıları çalışmaya başladıktan görüntüleri Docker varlıklar Şekil 7-3'te gösterildiği gibi içeriyor.

Kolay yükseltme ve shift senaryolarda, Web Forms uygulaması için kullandığınız tek hizmet uygulaması olacaktır. Şablon de işaret etmek için başlangıç projesi değiştirir **docker compose'u** projesi. CTRL + F5'e veya F5 tuşuna basarak şimdi Docker görüntüsünü oluşturur ve Docker kapsayıcısı başlatır.

![](./media/image3.png)

**Şekil 7-3**. **Docker compose'u** Web Forms çözümde proje

Çözüm çalıştırmadan önce Windows kapsayıcılar kullanmak için Docker yapılandırma emin olmanız gerekir. Bunu yapmak için Docker simgesi Windows seçip sağ tıklatın. **geçiş Windows kapsayıcılara**Şekil 7-4'te gösterildiği gibi.

![](./media/image4.png)

**Şekil 7-4**. Windows Docker görev simgesinden Windows kapsayıcılara değiştirme

Menü öğesi diyorsa **geçiş Linux kapsayıcılara**, Docker ile Windows kapsayıcıları zaten çalışıyor.

Çözümü çalıştırırken, Docker ana bilgisayarı yeniden başlatır. Oluşturma sırasında uygulama ve Web Forms projesi için Docker görüntü oluşturun. Bunu ilk kez uzun zaman alır. Derleme işlemi ASP.NET için temel Windows Server görüntüsü ve ek görüntü aşağı çeker olmasıdır. Sonraki derleme ve çalıştırma döngüleri çok daha hızlı olacaktır.

Docker proje şablonu tarafından eklenen dosyalar daha derin bir göz atalım. Sizin için birkaç dosyası oluşturuldu. Visual Studio Docker görüntüsünü oluşturmak ve bir kapsayıcı başlatmak için bu dosyaları kullanır. Docker komutları el ile çalıştırmak için CLI aynı dosyaları kullanabilirsiniz.

Aşağıdaki Dockerfile örnek, bir ASP.NET sitesi çalıştıran Windows ASP.NET görüntüyü temel alarak bir Docker görüntüsü oluşturmak için temel ayarlarını gösterir.

```
FROM microsoft/aspnet

ARG source

WORKDIR /inetpub/wwwroot

COPY ${source:-obj/Docker/publish} .
```

Bu Dockerfile çok benzer bir ASP.NET Core uygulama Linux kapsayıcılarında çalıştırmak için oluşturulan arar. Ancak, birkaç önemli farklılıklar vardır. En önemli fark temel görüntü .NET Framework içeren geçerli bir Windows Server görüntü olan microsoft/aspnet olmasıdır. Diğer farklar kaynak dizininden kopyalanır dizinleri farklı ' dir.

Diğer dosyaları **docker-oluşturan** proje olan geliştirmek ve kapsayıcılar yapılandırmak için gereken Docker varlıklar. Visual Studio, bunların nasıl kullanıldığı vurgulamak için bir düğümü altındaki çeşitli docker-compose.yml dosyaları yerleştirir. Temel docker-compose dosyası tüm yapılandırmalar için ortak olan yönergeleri içerir. Ortam değişkenleri ve ilgili geçersiz kılmalar Geliştirici yapılandırması için docker compose.override.yml dosyası içerir. Çeşitleri olan. vs.debug ve. vs.release ekleme ve çalışan kapsayıcı yönetmek Visual Studio'nun ortam ayarlarını sağlayın.

Visual Studio tümleştirmesi çözümünüz için Docker destek ekleyen bir parçası olsa da, ayrıca yapı ve docker kullanarak komut satırından çalıştırma-komutu, önceki bölümlerde anlatıldığı gibi oluşturun.

## <a name="getting-data-from-the-existing-catalog-net-core-microservice"></a>Varolan katalog .NET Core mikro hizmet verileri alma

Web Forms uygulamayı sahte veri kullanmak yerine veri almak için eShopOnContainers katalog mikro kullanacak şekilde yapılandırabilirsiniz. Bunu yapmak için web.config dosyasını düzenleyin ve useFake anahtarının değerini false olarak ayarlayın. DI kapsayıcı sabit kodlanmış verileri döndürür sınıfı yerine canlı katalog mikro erişen sınıfını kullanır. Diğer bir kod değişiklikleri gereklidir.

Canlı Kataloğu hizmetine erişim anlamına güncellemeniz gerekir **docker compose'u** proje Kataloğu hizmet yansıması oluştur ve kataloğu hizmet kapsayıcısı başlatın. Windows CE docker Linux kapsayıcıları ve Windows kapsayıcıları destekler, ancak aynı anda değil. Katalog mikro hizmet çalıştırmak için Windows tabanlı bir kapsayıcı üstünde katalog mikro hizmet çalıştıran bir görüntü oluşturmak gerekir. Bu yaklaşım, önceki bölümlerde gördüğünüz daha farklı bir Dockerfile mikro projesi için gerektirir. Dockerfile.windows dosyası bir Windows kapsayıcıda çalışır katalog API kapsayıcı görüntü oluşturmak için yapılandırma ayarlarını içerir — örneğin, bir Windows Nano Docker görüntüyü kullanmak için.

Katalog mikro hizmet üzerinde SQL Server veritabanını kullanır. Bu nedenle, bir SQL Server Docker Windows tabanlı görüntüsü de kullanmanız gerekir.

Bu değişikliklerden sonra uygulamayı başlatmak için daha fazla docker-compose proje yapar. Projeyi şimdi Windows tabanlı SQL sunucu görüntüsü kullanarak SQL Server başlatır. Bir Windows kapsayıcısında katalog mikro hizmet başlar. Ve Windows kapsayıcısında Web Forms katalog Düzenleyicisi kapsayıcısı da başlatır. Görüntüleri hiçbirini yapı gerekiyorsa, görüntüleri ilk oluşturulur.

## <a name="development-and-production-environments"></a>Geliştirme ve üretim ortamları

Birkaç geliştirme yapılandırması ve üretim yapılandırması arasındaki farklar vardır. Geliştirme ortamında aynı Docker ana bir parçası olarak Web Forms uygulaması, katalog mikro hizmet ve SQL Server Windows kapsayıcılardaki çalıştırın. Önceki bölümlerde, Linux tabanlı Docker ana bilgisayardaki diğer .NET Core tabanlı hizmetler aynı Docker ana bilgisayarın SQL Server görüntülerinin dağıtılmış belirtiliyor. Birden çok mikro aynı Docker ana bilgisayarı (veya küme) çalıştıran avantajı, daha az ağ iletişimi yoktur ve kapsayıcılar arasındaki iletişimi daha düşük gecikme süresine sahip olmasıdır.

Geliştirme ortamında aynı işletim sisteminde tüm kapsayıcıları çalıştırmanız gerekir. Windows CE docker aynı anda çalışan Windows ve Linux tabanlı kapsayıcılar desteklemez. Üretimde uygulama Linux kapsayıcısında farklı bir üzerinde çalışan katalog mikro hizmet örneği ile iletişim kurabilir Web Forms olması veya tek bir Docker ana bilgisayar (veya küme) Windows kapsayıcısında katalog mikro hizmet çalıştırmak istediğiniz karar verebilirsiniz Docker ana bilgisayar. Bunu nasıl, ağ gecikmesi için en iyi duruma getirmek istediğiniz yere bağlıdır. Çoğu durumda, aynı Docker ana bilgisayar (veya swarm) dağıtım kolaylığı ve düşük iletişim gecikmesi için üzerinde çalışan uygulamalarınızı bağımlı mikro istiyor. Bu yapılandırmalarda mikro hizmet örnekleri ve kalıcı veri depolama için yüksek kullanılabilirlik sunucuları yalnızca pahalı iletişimleri arasındadır.

>[!div class="step-by-step"]
[Önceki] (.. / net-core-single-containers-linux-windows-server-hosts/index.md) [sonraki] (.. /multi-Container-microservice-NET-Applications/index.MD)
