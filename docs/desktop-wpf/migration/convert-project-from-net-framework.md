---
title: WPF Uygulamalarını .NET Core 3.0'a geçirme
description: Bir Windows Presentation Foundation (WPF) uygulamasını .NET Core 3.0'a nasıl geçirteceklerini öğrenin.
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: f52005e7c8a6312b8c4e09a950f1f635af1894e4
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "82071313"
---
# <a name="migrating-wpf-apps-to-net-core"></a>WPF uygulamalarını .NET Core'a geçirme

Bu makale, bir Windows Presentation Foundation (WPF) uygulamasını .NET Framework'den .NET Core 3.0'a geçirmek için gereken adımları kapsar. Bağlantı noktasına elinizde bir WPF uygulamanız yoksa, ancak işlemi denemek istiyorsanız, [GitHub'da](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader)bulunan **Bean Trader** örnek uygulamasını kullanabilirsiniz. Orijinal uygulama (hedefleme .NET Framework 4.7.2) NetFx\BeanTraderClient klasöründe mevcuttur. Önce uygulamaları genel olarak taşımanız için gerekli adımları açıklayacağız ve ardından **Bean Trader** örneğine uygulanan belirli değişiklikleri gözden geçireceğiz.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

.NET Core'a geçiş yapmak için önce şunları belirtmelisiniz:

01. NuGet bağımlılıklarını anlayın ve güncelleyin:

    01. Biçimi kullanmak için NuGet `<PackageReference>` bağımlılıklarını yükseltin.
    01. .NET Core veya .NET Standart uyumluluğu için üst düzey NuGet bağımlılıklarını gözden geçirin.
    01. NuGet paketlerini yeni sürümlere yükseltin.
    01. .NET bağımlılıklarını anlamak için [.NET Taşınabilirlik Çözümleyicisini](../../standard/analyzers/portability-analyzer.md) kullanın.

01. Proje dosyasını yeni SDK stili biçimine geçirin:

    01. Hem .NET Core hem de .NET Framework'u mi yoksa yalnızca .NET Core'u mu hedefleyeceğinizi seçin.
    01. İlgili proje dosyası özelliklerini ve öğelerini yeni proje dosyasına kopyalayın.

01. Yapı sorunlarını giderin:

    01. [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/) paketine bir başvuru ekleyin.
    01. API düzeyindeki farklılıkları bulun ve düzeltin.
    01. *App.config* bölümlerini `appSettings` kaldırın `connectionStrings`veya .
    01. Gerekirse oluşturulan kodu yeniden oluşturun.

01. Çalışma zamanı testi:

    01. Taşınan uygulamanın beklendiği gibi çalıştığını doğrulayın.
    01. İstisnalara dikkat edin. <xref:System.NotSupportedException>

## <a name="about-the-sample"></a>Örnek hakkında

Bu makalede, gerçek dünya WPF uygulamalarının sahip olabileceği ne benzer çeşitli bağımlılıklar kullandığından [Bean Trader örnek uygulamasına](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader) başvurur. Uygulama büyük değildir, ancak karmaşıklık açısından 'Hello World' bir adım olması gerekiyordu. Uygulama, kullanıcıların gerçek uygulamaları taşıma sırasında karşılaşabilecekleri bazı sorunları gösteriyor. Uygulama bir WCF hizmeti ile iletişim kurar, bu nedenle düzgün çalışması için, ayrıca BeanTraderServer proje (aynı GitHub deposunda mevcuttur) çalıştırmak ve beanTraderClient yapılandırma doğru bitiş noktasına puan emin olmak gerekir. (Varsayılan olarak, örnek sunucu aynı makineüzerinde çalışıyor *http://localhost:8090*varsayar , yerel BeanTraderServer başlattığınızda doğru olacaktır.)

Bu örnek uygulamanın .NET Core taşıma zorluklarını ve çözümlerini göstermeyi amaçladığını unutmayın. Bu WPF en iyi uygulamaları göstermek için değil. Aslında, kasıtlı olarak bazı anti-desenler ilerlerken en az birkaç ilginç zorlukla karşılaştığınızı emin olmak için.

## <a name="getting-ready"></a>Hazırlanma

Bir .NET Framework uygulamasını .NET Core'a geçirmenin temel zorluğu, bağımlılıklarının farklı veya hiç çalışmamasıdır. Geçiş eskisinden çok daha kolaydır; birçok NuGet paketi artık .NET Standard'ı hedef alıyor. .NET Core 2.0 ile başlayarak ,NET Framework ve .NET Core yüzey alanları benzer hale gelmiştir. Buna rağmen, bazı farklılıklar (nuget paketleri ve mevcut .NET API'ler hem destek) kalır. Geçişteki ilk adım, uygulamanın bağımlılıklarını gözden geçirmek ve başvuruların .NET Core'a kolayca geçirilen bir biçimde olduğundan emin olmaktır.

### <a name="upgrade-to-packagereference-nuget-references"></a>NuGet `<PackageReference>` referanslarına yükseltme

Eski .NET Framework projeleri genellikle NuGet bağımlılıklarını bir *packages.config* dosyasında listeler. Yeni SDK tarzı proje dosya biçimi, [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) NuGet paketlerini ayrı bir config dosyasıyerine csproj dosyasındaki öğeler olarak başvurur.

Geçiş yaparken, -stil başvuruları `<PackageReference>`kullanmanın iki avantajı vardır:

- Bu, yeni .NET Core proje dosyası için gerekli olan NuGet başvuru stilidir. Zaten kullanıyorsanız, `<PackageReference>`bu proje dosyası öğeleri kopyalanabilir ve doğrudan yeni projeye yapıştırılabilir.
- Packages.config dosyasının `<PackageReference>` aksine, öğeler yalnızca projenizin doğrudan bağlı olduğu üst düzey bağımlılıkları ifade eder. Diğer tüm geçişli NuGet paketleri geri yükleme zamanında belirlenecek ve otomatik olarak üretilen obj\project.assets.json dosyasına kaydedilecektir. Bu, projenizin hangi bağımlılıklara sahip olduğunu belirlemeyi çok daha kolay hale getirir ve bu da gerekli bağımlılıkların .NET Core'da çalışıp çalışmayacağını belirlerken yararlıdır.

Bir .NET Framework uygulamasını .NET Core'a geçirmenin ilk `<PackageReference>` adımı NuGet başvurularını kullanmak üzere güncelleştirmektir. Visual Studio bunu basitleştiriyor. Visual Studio'nun **Solution Explorer'ında**projenin *paketleri.config* dosyasına sağ tıklayın ve ardından **PackageReference'a geçir packages.config'i**seçin.

![PackageReference'a yükseltme](./media/convert-project-from-net-framework/package-reference-migration.png)

Hesaplanan üst düzey NuGet bağımlılıklarını gösteren ve hangi diğer NuGet paketlerinin üst düzeye yükseltilmesi gerektiğini soran bir iletişim kutusu görüntülenir. Bu diğer paketlerin hiçbiri Bean Trader örnek için üst düzey olması gerekir, böylece tüm bu kutuların kontrolden çekebilirsiniz. Daha sonra **Tamam'ı** tıklatın ve *packages.config* dosyası kaldırılır ve `<PackageReference>` öğeler proje dosyasına eklenir.

`<PackageReference>`-stil başvuruları NuGet paketlerini bir paket klasöründe yerel olarak saklamaz. Bunun yerine, bir optimizasyon olarak küresel olarak saklanır. Geçiş tamamlandıktan sonra, csproj dosyasını edin ve daha önce gelen çözümleyicilere atıfta bulunan öğeleri `<Analyzer>` *kaldırın. \paketleri* dizini. Merak etme; NuGet paket başvurularıhala sizde olduğundan, çözümleyiciler projeye dahil edilecektir. Sadece eski paketleri temizlemen gerekiyor. `<Analyzer>`

### <a name="review-nuget-packages"></a>NuGet paketlerini inceleyin

Artık projenin bağlı olduğu üst düzey NuGet paketlerini görebildiğinize göre, bu paketlerin .NET Core'da kullanılabilir olup olmadığını gözden geçirebilirsiniz. Bir paketin .NET Core'u destekleyip desteklemediğini [nuget.org](https://www.nuget.org/)bağımlılıklarına bakarak belirleyebilirsiniz. Topluluk tarafından oluşturulan [fuget.org](https://www.fuget.org/) sitesi, bu bilgileri paket bilgileri sayfasının en üstünde belirgin bir şekilde gösterir.

.NET Core 3.0 hedeflediğinde,.NET Core veya .NET Standard'ı hedefleyen paketler çalışmalıdır (.NET Core .NET Standart yüzey alanını uyguladığından). Bazı durumlarda, kullanılan bir paketin belirli sürümü .NET Core veya .NET Standard'ı hedeflemez, ancak yeni sürümler hedeflenecektir. Bu durumda, paketin en son sürümüne yükseltmeyi düşünmelisiniz.

.NET Framework'u hedefleyen paketleri de kullanabilirsiniz, ancak bu bazı riskler sunar. .NET Core to .NET Framework bağımlılıklarına izin verilir, çünkü .NET Core ve .NET Framework yüzey alanları bu tür bağımlılıkların *genellikle* çalıştığı kadar benzerdir. Ancak, paket .NET Core'da bulunmayan bir .NET API kullanmaya çalışırsa, çalışma zamanı özel bir durumla karşılaşırsınız. Bu nedenle, sadece .NET Framework paketlerine başka seçenek olmadığında başvurmalı ve bunu yapmanın bir test yükü yüklediğini anlamalısınız.

.NET Core veya .NET Standard'ı hedeflememeyen başvurulan paketler varsa, diğer alternatifleri düşünmeniz gerekir:

- Bunun yerine kullanılabilecek başka benzer paketler var mı? Bazen NuGet yazarları ayrı 'yayınlamak. Özellikle .NET Core hedefleyen kendi kütüphanelerinin Core sürümleri. Kurumsal Kütüphane paketleri topluluk yayıncılık bir örnektir ". NetCore" alternatifleri. Diğer durumlarda, .NET Standard için belirli bir hizmet için daha yeni SDK'lar (bazen farklı paket adlarıyla) kullanılabilir. Herhangi bir alternatif yoksa, .NET Framework hedefli paketleri kullanarak ,NET Core'da çalışırken iyice test etmeniz gerektiğini göz önünde bulundurarak devam edebilirsiniz.

Bean Trader örneği aşağıdaki üst düzey NuGet bağımlılıklarına sahiptir:

- [**Castle.Windsor, sürüm 4.1.1**](https://www.castleproject.org/projects/windsor/)  

  Bu paket .NET Standart 1.6'yı hedefler, bu nedenle .NET Core'da çalışır.

- [**Microsoft.CodeAnalysis.FxCopAnalyzers, sürüm 2.6.3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  Bu bir meta paketidir, bu nedenle hangi platformları desteklediği hemen belli değildir, ancak [belgeler](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers) en yeni sürümünün (2.9.2) hem .NET Framework hem de .NET Core için çalışacağını gösterir.

- [**Nito.AsyncEx, sürüm 4.0.1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  Bu paket .NET Core'u hedeflemez, ancak yeni 5.0 sürümü hedeflemektedir. Birçok NuGet paketi son zamanlarda .NET Standard desteği eklence, ancak eski proje sürümleri yalnızca .NET Framework'u hedeflediğiiçin, bu geçiş yaparken yaygındır. Sürüm farkı yalnızca küçük bir sürüm farkıysa, yeni sürüme yükseltmek genellikle kolaydır. Bu önemli bir sürüm değişikliği olduğundan, pakette değişiklikler kırılabileceğinden, dikkatli yükseltme niz gerekir. Ama ileriye giden bir yol var, ki bu iyi bir şey.

- [**MahApps.Metro, sürüm 1.6.5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  Bu paket aynı zamanda .NET Core'u da hedeflemez, ancak daha yeni bir ön sürüm (2.0-alfa) vardır. Yine, değişiklikleri kırma için dikkat etmek zorunda, ama yeni paket cesaret verici.

Bean Trader örneğinin NuGet bağımlılıkları ya .NET Standard/.NET Core'u hedef alır ya da yeni sürümleri vardır, bu nedenle burada herhangi bir engelleme sorunu olması olası değildir.

### <a name="upgrade-nuget-packages"></a>NuGet paketlerini yükseltin

Mümkünse, herhangi bir kırılma değişikliğini erken keşfetmek ve gidermek için bu noktada (proje hala .NET Framework'ü hedefleyen projeyle) yalnızca .NET Core veya .NET Standard'ı hedefleyen paketlerin sürümlerini yükseltmek iyi olacaktır.

Uygulamanın varolan .NET Framework sürümünde herhangi bir önemli değişiklik yapmak istemiyorsanız, bu işlem .NET Core'u hedefleyen yeni bir proje dosyanız olana kadar bekleyebilir. Ancak, NuGet paketlerini .NET Core uyumlu sürümlere önceden yükseltmek, yeni proje dosyasını oluşturduğunuzda geçiş işlemini daha da kolaylaştırır ve uygulamanın .NET Framework ve .NET Core sürümleri arasındaki fark sayısını azaltır.

Bean Trader örneği ile, gerekli tüm yükseltmeleri kolayca yapılabilir (Visual Studio's NuGet paket yöneticisi kullanılarak) bir istisna dışında: **MahApps.Metro 1.6.5** den **2.0** yükseltme tema ve aksan yönetimi API'ler ile ilgili kırılma değişiklikleri ortaya koymaktadır.

İdeal olarak, uygulama paketin yeni sürümünü kullanmak üzere güncellenir (bu daha fazla .NET Core üzerinde çalışmak olasıdır). Ancak bazı durumlarda bu mümkün olmayabilir. Bu gibi durumlarda, gerekli değişiklikler önemsiz olmadığından ve bu öğretici **MahApps.Metro 2'ye** değil ,.NET Core 3'e geçiş yapmaya odaklandığından **MahApps.Metro'yu** yükseltmeyin. Ayrıca, bu düşük riskli .NET Framework bağımlılığı çünkü Bean Trader uygulaması sadece **MahApps.Metro**küçük bir kısmını egzersizleri. Tabii ki, geçiş tamamlandıktan sonra her şeyin çalıştığından emin olmak için test edilmesi gerekecek. Bu gerçek bir senaryo olsaydı, şimdi bazı teknik borç geride bırakır göç yapmadığıiçin **MahApps.Metro** sürümü 2.0 taşımak için iş izlemek için bir sorun dosya iyi olurdu.

NuGet paketleri son sürümlere güncelleştirildikten sonra, Bean Trader örneğinin proje dosyasındaki `<PackageReference>` madde grubu bu şekilde görünmelidir.

```xml
<ItemGroup>
  <PackageReference Include="Castle.Windsor">
    <Version>4.1.1</Version>
  </PackageReference>
  <PackageReference Include="MahApps.Metro">
    <Version>1.6.5</Version>
  </PackageReference>
  <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers">
    <Version>2.9.2</Version>
  </PackageReference>
  <PackageReference Include="Nito.AsyncEx">
    <Version>5.0.0</Version>
  </PackageReference>
</ItemGroup>
```

### <a name="net-framework-portability-analysis"></a>.NET Çerçeve taşınabilirlik analizi

Projenizin NuGet bağımlılıklarının durumunu anladığınızda, göz önünde bulundurulması gereken bir sonraki şey .NET Framework API bağımlılıklarıdır. [.NET Taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) aracı, projenizin hangi .NET API'lerinin diğer .NET platformlarında kullanılabildiği konusunda yararlıdır.

Araç bir [Visual Studio eklentisi](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)olarak geliyor , bir [komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases), ya da basit bir [GUI](https://github.com/Microsoft/dotnet-apiport-ui)sarılmış , hangi seçeneklerini kolaylaştırır. Porting masaüstü uygulamalarındaki GUI'yi kullanarak .NET Taşınabilirlik Çözümleyicisini (API Bağlantı Noktası) kullanarak [.NET Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/) blog gönderisine ilişkin daha fazla bilgi edinebilirsiniz. Komut satırını kullanmayı tercih ederseniz, gerekli adımlar şunlardır:

1. Zaten yoksa [.NET Taşınabilirlik Çözümleyicisini](https://github.com/Microsoft/dotnet-apiport/releases) indirin.
1. Taşınabilir .NET Framework uygulamasının başarıyla oluşturduğundan emin olun (bu, geçişten önce iyi bir fikirdir).
1. API Bağlantı Noktasını böyle bir komut satırıyla çalıştırın.

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    Bağımsız `-f` değişken, çözümlemek için ikilileri içeren yolu belirtir. Bağımsız `-r` değişken, istediğiniz çıktı dosya biçimini belirtir. Bağımsız `-t` değişken, API kullanımını analiz etmek için hangi .NET platformuna karşı olduğunu belirtir. Bu durumda, .NET Core'u istiyorsunuz.

HTML raporunu açtığınızda, ilk bölümde analiz edilen tüm ikililer ve kullandıkları .NET API'lerinin yüzde kaçının hedeflenen platformda kullanılabilir olduğu listelenir. Yüzde tek başına anlamlı değildir. Daha yararlı olan, eksik olan belirli API'leri görmektir. Bunu yapmak için, bir derleme adı seçin veya tek tek derlemeler için raporlara gidin.

Kaynak kodun sahibi olduğunuz derlemelere odaklanın. Bean Trader ApiPort raporunda, örneğin, listelenen birçok ikili vardır, ancak bunların çoğu NuGet paketleriaittir. `Castle.Windsor`.NET Core'da eksik olan bazı System.Web API'lerine bağlı olduğunu gösterir. Bu bir sorun değildir, çünkü daha `Castle.Windsor` önce .NET Core'u destekleyen leri doğruladığınız için. NuGet paketlerinin farklı .NET platformlarında kullanılmak üzere farklı ikili lere sahip olması `Castle.Windsor` yaygındır, bu nedenle System.Web API'lerinin .NET Framework sürümünün .NET Standard veya .NET Core'u da hedeflediği sürece .NET Standard veya .NET Core'u (ki öyle) kullanması önemsizdir.

Bean Trader örnek ile, dikkate almanız gereken tek ikili **BeanTraderClient** ve rapor sadece iki .NET API eksik olduğunu gösterir: `System.ServiceModel.ClientBase<T>.Close` ve `System.ServiceModel.ClientBase<T>.Open`.

![BeanTraderClient taşınabilirlik raporu](./media/convert-project-from-net-framework/portability-report.png)

WCF İstemci API'leri (çoğunlukla) .NET Core'da desteklendirildik, bu nedenle bu merkezi API'ler için alternatifler olması gerektiğinden, bu sorunların engellenmesi olası değildir. `System.ServiceModel`Aslında,'ın .NET Core yüzey alanına <https://apisof.net>(kullanarak) baktığınızda,.NET Core'da async alternatifleri olduğunu görürsünüz.

Bu rapor ve önceki NuGet bağımlılık analizine dayanarak, Bean Trader örneğini .NET Core'a geçiren önemli bir sorun olmaması gerekir gibi görünüyor. Göçü başlatacağınız bir sonraki adımiçin hazırsınız.

## <a name="migrating-the-project-file"></a>Proje dosyasını geçirme

Uygulamanız yeni [SDK tarzı proje dosya biçimini](../../core/tools/csproj.md)kullanmıyorsa, .NET Core'u hedeflemek için yeni bir proje dosyasına ihtiyacınız vardır. Varolan csproj dosyasını değiştirebilir veya varolan projeyi geçerli durumunda el değmemiş olarak tutmayı tercih ederseniz, .NET Core'u hedefleyen yeni bir csproj dosyası ekleyebilirsiniz. Uygulamanın .NET Framework ve .NET Core sürümlerini, [çok hedeflemeli](../../standard/library-guidance/cross-platform-targeting.md) tek bir SDK tarzı `<TargetFrameworks>` proje dosyasıyla (birden çok hedef belirterek) oluşturabilirsiniz.

Yeni proje dosyasını oluşturmak için Visual Studio'da yeni bir `dotnet new wpf` WPF projesi oluşturabilir veya proje dosyasını oluşturmak ve sonra doğru konuma kopyalamak/yeniden adlandırmak için komutu geçici bir dizinde kullanabilirsiniz. Ayrıca topluluk tarafından oluşturulan bir araç, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017), bazı proje dosyası geçiş otomatikleştirebilirsiniz. Araç yararlıdır, ancak yine de geçişin tüm ayrıntılarının doğru olduğundan emin olmak için sonuçları gözden geçirmek için bir insana ihtiyaç duyar. Aracın en iyi şekilde işlemediği belirli bir alan, NuGet paketlerini *packages.config* dosyalarından geçirmektir. Araç, NuGet paketlerine başvurmak için hala bir *packages.config* dosyası kullanan bir `<PackageReference>` proje dosyasında çalışıyorsa, otomatik olarak öğelere geçiş yapacaktır, ancak yalnızca üst düzey paketler yerine `<PackageReference>` *tüm* paketler için öğeler ekler. Visual Studio ile öğelere`<PackageReference>` zaten geçiş yaptıysanız (bu örnekte yaptığınız gibi), araç dönüşümün geri kalanında yardımcı olabilir. Scott Hanselman [csproj dosyaları göç yaptığı blog yazısı](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx)önerir gibi, elle taşıma eğitim ve sadece limana birkaç proje varsa daha iyi sonuçlar verecektir. Ancak düzinelerce veya yüzlerce proje dosyası taşımanız durumunda, [CsprojToVs2017] gibi bir araç yardımcı olabilir.

Bean Trader örneği için yeni bir proje `dotnet new wpf` dosyası oluşturmak için, geçici bir dizinde çalıştırın ve oluşturulan *.csproj* dosyasını *BeanTraderClient* klasörüne taşıyın ve **beanTraderClient.Core.csproj**adını yeniden adlandırın.

Yeni proje dosyası biçimi otomatik olarak C# dosyalarını, *resx* dosyalarını ve dizininin altında bulduğu XAML dosyalarını içerdiğinden, proje dosyası zaten neredeyse tamamlandı! Geçişi tamamlamak için, eski ve yeni proje dosyalarını yan yana açın ve içerdiği herhangi bir bilginin geçirilip geçirilmeihtiyacı olup olmadığını görmek için eskidosyaya bakın. Bean Trader örnek durumda, aşağıdaki öğeler yeni projeye kopyalanmalıdır:

- , `<RootNamespace>` `<AssemblyName>`ve `<ApplicationIcon>` özellikleritüm kopyalanmalıdır.

- Bean Trader örneği `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` AssemblyInfo.cs bir dosyadaki montaj düzeyinde öznitelikleri (beğen) `[AssemblyTitle]`içerdiğinden, yeni proje dosyasına bir özellik eklemeniz gerekir. Varsayılan olarak, yeni SDK tarzı projeler bu öznitelikleri csproj dosyasındaki özelliklere göre otomatik olarak oluşturur. Bu durumda bunun olmasını istemediğiniz için (otomatik oluşturulan öznitelikler AssemblyInfo.cs gelenlerle çakışacak), otomatik `<GenerateAssemblyInfo>`olarak oluşturulan öznitelikleri .

- *resx* dosyaları otomatik olarak katıştırılmış `<Resource>` kaynaklar olarak dahil edilebilse de, görüntüler gibi diğer öğeler dahil edilmez. Bu nedenle, `<Resource>` görüntü ve simge dosyalarını katıştırma öğelerini kopyalayın. Globbing desenleri için yeni proje dosya biçiminin desteğini kullanarak tek bir satıra png başvurularını basitleştirebilirsiniz: `<Resource Include="**\*.png" />`.

- Benzer şekilde, `<None>` öğeler otomatik olarak dahil edilir, ancak varsayılan olarak çıktı dizinine kopyalanmıyor. Bean Trader projesi çıktı `<None>` dizinine *kopyalanan* bir öğe içerdiğinden (davranışları kullanarak), `PreserveNewest` bu dosya `<None>` için otomatik olarak doldurulan öğeyi güncelleştirmeniz gerekir, bu gibi.

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- Bean Trader örneği, bu dosyada tanımlanan temalar ve aksanlar uygulamanın `Page`kendisine gömülmek yerine dosyanın XAML'sinden yüklendiğinden, bir XAML dosyası (Default.Accent.xaml) `Content` (yerine) içerir. Yeni proje sistemi otomatik olarak bir `<Page>`XAML dosyası olduğundan, bir , ancak bu dosyayı içerir. Bu nedenle, XAML dosyasını hem sayfa`<Page Remove="**\Default.Accent.xaml" />`olarak kaldırmanız hem de içerik olarak eklemeniz gerekir.

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- Son olarak, tüm öğeleri `<ItemGroup>` ile kopyalayarak `<PackageReference>` NuGet referansları ekleyin. NuGet paketlerini daha önce .NET Core uyumlu sürümlere yükseltmemiş olsaydınız, paket başvuruları .NET Core'a özgü bir projede olduğu için bunu şimdi yapabilirdiniz.

Bu noktada, BeanTrader çözümüne yeni proje eklemek ve Visual Studio açmak mümkün olmalıdır. Proje **Solution Explorer'da**doğru `dotnet restore BeanTraderClient.Core.csproj` görünmeli ve paketleri başarıyla geri yüklemeli (.NET Framework'ü hedeflemek için kullandığınız MahApps.Metro sürümüyle ilgili iki beklenen uyarıyla).

Her iki proje dosyasını yan yana tutmak mümkün olsa da (ve eski projeyi tam olarak oluşturmaya devam etmek istiyorsanız bile istenebilir), geçiş işlemini karmaşıklaştırır (iki proje aynı bin ve obj klasörlerini kullanmaya çalışır) ve genellikle gerekli değildir. Hem .NET Core hem de .NET Framework hedefleri için `<TargetFramework>netcoreapp3.0</TargetFramework>` oluşturmak istiyorsanız, yeni `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>` proje dosyasındaki özelliği yerine değiştirebilirsiniz. Bean Trader örnek için, artık gerekli olduğundan eski proje dosyası (BeanTraderClient.csproj) silin. Her iki proje dosyasını da saklamayı tercih ederseniz, farklı çıktı ve ara çıktı yollarına oluşturmalarını unutmayın.

## <a name="fix-build-issues"></a>Yapı sorunlarını düzeltme

Taşıma işleminin üçüncü adımı, projenin oluşturulmasını sağlamaktır. Proje dosyası SDK tarzı bir projeye dönüştürüldükten sonra bazı uygulamalar zaten başarılı bir şekilde oluşturur. Uygulamanız için durum buysa, tebrikler! Adım 4'e gidebilirsin. Diğer uygulamaların .NET Core için bina almak için bazı güncelleştirmelere ihtiyacı vardır. Örneğin, (veya `dotnet build` Visual Studio'da inşa etmek) şimdi Bean Trader örnek proje üzerinde çalıştırmaya çalışırsanız, birçok hata olacaktır, ancak bunları hızlı bir şekilde sabit alırsınız.

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>System.ServiceModel referansları ve Microsoft.Windows.Compatibility

.NET Core için kullanılabilen ancak otomatik olarak .NET Core uygulama meta paketine dahil olmayan API'ler için yaygın bir hata kaynağı olan başvurular eksiktir. Bu sorunu gidermek için `Microsoft.Windows.Compatibility` pakete başvurmanız gerekir. Uyumluluk paketi, WCF istemcisi, dizin hizmetleri, kayıt defteri, yapılandırma, APC'ler API'leri ve daha fazlası gibi Windows masaüstü uygulamalarında yaygın olan geniş bir API kümesi içerir.

Bean Trader örneği ile, yapı hatalarının çoğu <xref:System.ServiceModel> eksik türleri kaynaklanmaktadır. Bunlar, gerekli WCF NuGet paketlerine başvurarak ele alınabilir. WCF istemci API'leri `Microsoft.Windows.Compatibility` pakette bulunanlar arasındadır, bu nedenle uyumluluk paketine başvurmak daha da iyi bir çözümdür (çünkü API'lerle ilgili tüm sorunları ve uyumluluk paketinin kullanıma sunduğu WCF sorunlarına yönelik çözümleri de ele alıyor). Paket, `Microsoft.Windows.Compatibility` .NET Core 3.0 WPF ve WinForms taşıma senaryolarının çoğunda yardımcı olur. NuGet referansını ekledikten `Microsoft.Windows.Compatibility`sonra, yalnızca bir yapı hatası kalır!

### <a name="cleaning-up-unused-files"></a>Kullanılmayan dosyaları temizleme

Sık sık gelen bir geçiş sorunu, *tüm* kaynağı otomatik olarak içeren yeni SDK tarzı projeler tarafından alınan yapıya daha önce dahil edilmeyen C# ve XAML dosyalarıyla ilgilidir.

Bean Trader örneğinde gördüğünüz bir sonraki yapı hatası *OldUnusedViewModel.cs*kötü bir arayüz uygulaması anlamına gelir. Dosya adı bir ipucudur, ancak denetimde bu kaynak dosyanın yanlış olduğunu göreceksiniz. Orijinal .NET Framework projesine dahil edilmediği için daha önce sorunlara neden olmadı. Diskte bulunan ancak eski *csproj'a* dahil olmayan kaynak dosyalar artık otomatik olarak eklenmiştir.

Bu gibi tek seferlik sorunlar için, dosyanın gerekli olmadığını onaylamak için önceki *csproj* ile `<Compile Remove="" />` karşılaştırmak kolaydır ve sonra ya o ya da, kaynak dosya artık herhangi bir yerde gerekli değilse, silin. Bu durumda, sadece *OldUnusedViewModel.cs*silmek güvenlidir.

Bu şekilde dışlanması gereken çok sayıda kaynak dosyanız varsa, `<EnableDefaultCompileItems>` özelliği proje dosyasında false olarak ayarlayarak C# dosyalarının otomatik olarak eklenmesini devre dışı bırakabilirsiniz. Ardından, yalnızca `<Compile Include>` eklemeyi planladığınız kaynakları oluşturmak için öğeleri eski proje dosyasındaki öğeleri yenisine kopyalayabilirsiniz. Benzer şekilde, `<EnableDefaultPageItems>` XAML sayfalarının otomatik olarak eklenmesini `<EnableDefaultItems>` kapatmak için kullanılabilir ve her ikisini de tek bir özellik ile denetleyebilir.

### <a name="a-brief-aside-on-multi-pass-compilers"></a>Çok geçişli derleyiciler hakkında kısa bir kenara

Sorunlu dosyayı Bean Trader örneğinden çıkardıktan sonra yeniden oluşturabilirsiniz ve dört hata alabilirsiniz. Daha önce de yok muydu? Hata sayısı neden arttı? C# derleyicisi çok geçişli bir [derleyicidir.](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes) Bu, her kaynak dosyayı iki kez geçtiği anlamına gelir. İlk olarak, derleyici yalnızca her kaynak dosyadaki meta verilere ve bildirimlere bakar ve bildirim düzeyi sorunlarını tanımlar. Bunlar düzelttin hatalar. Sonra c# kaynağını IL'ye dönüştürmek için kodu tekrar gözden geçirir; bunlar şu anda gördüğünüz ikinci hata kümesidir.

> [!NOTE]
> C# derleyicisi [sadece iki geçer daha](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes)fazlasını yapar, ancak sonuç bu gibi büyük kod değişiklikleri için derleyici hataları iki dalga gelme eğilimindedir.

### <a name="third-party-dependency-fixes-castlewindsor"></a>Üçüncü taraf bağımlılık düzeltmeleri (Castle.Windsor)

Bazı geçiş senaryolarında ortaya çıkan bir diğer sorun sınıfı da .NET Framework ve .NET Çekirdek sürümleri arasındaki API farklarıdır. Bir NuGet paketi hem .NET Framework'u hem de .NET Standard'ı veya .NET Core'u hedef alsa bile, farklı .NET hedefleri ile kullanılmak üzere farklı kitaplıklar olabilir. Bu, paketlerin farklı uygulamalar gerektirebilecek birçok farklı .NET platformlarını desteklemesine olanak tanır. Ayrıca, farklı .NET platformlarını hedefalırken kitaplıklarda küçük API farklılıkları olabileceği anlamına gelir.

Bean Trader örneğinde göreceğiniz bir sonraki hata kümesi `Castle.Windsor` API'larla ilgilidir. .NET Core Bean Trader projesi ,NET Framework hedefli proje (4.1.1) `Castle.Windsor` ile aynı sürümü kullanır, ancak bu iki platform için uygulamalar biraz farklıdır.

Bu durumda, düzeltilmesi gereken aşağıdaki sorunları görürsünüz:

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly`.NET Core'da kullanılamaz. Ancak, `Classes.FromAssemblyContaining` mevcut benzer API, bu nedenle aramaların `Classes.FromThisAssembly()` her iki `Classes.FromAssemblyContaining(t)`kullanım `t` ları değiştirebilirsiniz , arama yapan türü nerede.
1. Benzer şekilde, *Bootstrapper.cs*Bootstrapper.cs `Castle.Windsor.Installer.FromAssembly`, . Bu ,NET Core'da kullanılamaz. Bunun yerine, bu çağrı `FromAssembly.Containing(typeof(Bootstrapper))`' ile değiştirilebilir.

### <a name="updating-wcf-client-usage"></a>WCF istemci kullanımını güncelleme

`Castle.Windsor` Farkları giderdikten sonra, .NET Core Bean Trader projesinde `BeanTraderServiceClient` kalan son yapı `DuplexClientBase`hatası (türetilmiştir) bir `Open` yöntem emamasıdır. Bu, bu geçiş işleminin başında .NET Taşınabilirlik Çözümleyicisi tarafından vurgulanan bir API olduğundan bu şaşırtıcı değildir. Baktığımızda `BeanTraderServiceClient` daha büyük bir soruna dikkatimizi çekiyor. Bu WCF istemcisi [Svcutil.exe](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı tarafından otomatik olarak oluşturuldu.

**Svcutil tarafından oluşturulan WCF istemcileri .NET Framework'de kullanılmak üzere hazırdır.**

Svcutil tarafından oluşturulan WCF istemcilerini kullanan çözümlerin .NET Core ile kullanılmak üzere .NET Standart uyumlu istemcileri yeniden oluşturması gerekir. Eski istemcilerin çalışmamalarının başlıca nedenlerinden biri, WCF bağlamalarını ve uç noktalarını tanımlamak için uygulama yapılandırmalarına bağımlı olmalarıdır. .NET Standart WCF API'leri çapraz platformda (System.Configuration API'lerinin bulunmadığı yerlerde) çalışabildiği için, .NET Core ve .NET Standart senaryoları için WCF istemcileri yapılandırma yerine programlamak üzere bağlamaları ve uç noktaları tanımlamalıdır.

Aslında, app.config bölümüne `<system.serviceModel>` (Svcutil ile veya el ile oluşturulmuş olsun) bağlı herhangi bir WCF istemci kullanımı .NET Core üzerinde çalışmak için değiştirilmesi gerekir.

.NET Standart uyumlu WCF istemcilerini otomatik olarak oluşturmanın iki yolu vardır:

- Araç, `dotnet-svcutil` WCF istemcilerini Svcutil'in daha önce çalıştığı şekilde oluşturan bir .NET aracıdır.
- Visual Studio, Bağlı Hizmetler özelliğinin [WCF Web Service Reference](../../core/additional-tools/wcf-web-service-reference-guide.md) seçeneğini kullanarak WCF istemcileri oluşturabilir.

Her iki yaklaşım da iyi çalışıyor. Alternatif olarak, tabii ki, WCF istemci kodunu kendiniz yazabilirsiniz. Bu örnek için Visual Studio Connected Service özelliğini kullanmayı seçtim. Bunu yapmak için Visual Studio'nun çözüm kaşifindeki *BeanTraderClient.Core* projesine sağ tıklayın ve**Bağlı Hizmet** **Ekle'yi** > seçin. Ardından, WCF Web Servis Başvuru Sağlayıcısı'nı seçin. Bu arka uç Bean Trader web hizmetinin adresini belirtebilirsiniz bir`localhost:8080` iletişim getirecek (eğer yerel sunucu çalıştırıyorsanız) ve oluşturulan türleri kullanmanız gereken ad alanı **(BeanTrader.Service**, örneğin).

![WCF Web Hizmeti Referans Bağlı Hizmet İletişim](./media/convert-project-from-net-framework/connected-service-dialog.png)

**Bitiş** düğmesini seçtikten sonra projeye yeni bir Bağlı Hizmetler düğümü eklenir ve Bean Trader hizmetine erişmek için yeni .NET Standart WCF istemcisini içeren düğümün altına bir Reference.cs dosyası eklenir. Bu dosyadaki `GetEndpointAddress` veya `GetBindingForEndpoint` yöntemlere bakarsanız, bağlamaların ve uç noktaların artık programlı olarak oluşturulduğunu görürsünüz (uygulama config yerine). 'Bağlı Hizmetler Ekle' özelliği, gerekli tüm WCF paketleri Microsoft.Windows.Compatibility üzerinden dahil edildiği için gerekli olmayan proje dosyasındaki bazı System.ServiceModel paketlerine de referanslar ekleyebilir. Ek bir System.ServiceModel `<PackageReference>` öğesi ekleyip eklemedigini görmek için csproj' u kontrol edin ve eğer öyleyse kaldırın.

Projemiz şimdi yeni WCF istemci sınıfları *(Reference.cs),* ama yine de eskileri (BeanTrader.cs) vardır. Bu noktada iki seçenek vardır:

- Orijinal .NET Framework projesini (yeni .NET Core hedefli projeyle birlikte) oluşturmak istiyorsanız, `<Compile Remove="BeanTrader.cs" />` .NET Core projesinin csproj dosyasındaki bir öğeyi kullanarak uygulamanın .NET Framework ve .NET Core sürümlerinin farklı WCF istemcilerini kullanmasını sağlayabilirsiniz. Bu, varolan .NET Framework projesini değiştirmeden bırakma avantajına sahiptir, ancak oluşturulan WCF istemcilerini kullanan kodun .NET Core durumunda .NET Framework projesinde olduğundan biraz `#if` farklı olması gerekebilir, bu nedenle ,.NET Framework için inşa edildiğinde bir şekilde çalışmak için bazı WCF istemci kullanımını (örneğin istemci oluşturma) koşullu olarak derlemek için yönergeleri kullanmanız gerekir.

- Diğer taraftan, varolan .NET Framework projesinde bazı kod karmaşası kabul edilebilirse, *BeanTrader.cs* hep birlikte kaldırabilirsiniz. Yeni WCF istemcisi .NET Standard için üretilmiştir, hem .NET Core hem de .NET Framework senaryolarında çalışır. .NET Core'a ek olarak .NET Framework için (çok hedefleme veya iki csproj dosyasına sahip olarak) oluşturuyorsanız, bu yeni *Reference.cs* dosyasını her iki hedef için de kullanabilirsiniz. Bu yaklaşım, kodun iki farklı WCF istemcisini desteklemek için ikiye ayırmasına gerek kalmayacağı avantajına sahiptir; aynı kod her yerde kullanılacaktır. Dezavantajı (muhtemelen kararlı) .NET Framework proje değiştirme içerir.

Bean Trader örneğinde, geçişi kolaylaştırıyorsa orijinal projede küçük değişiklikler yapabilirsiniz, bu nedenle WCF istemci kullanımını uzlaştırmak için aşağıdaki adımları uygulayın:

01. Çözüm gezgininden 'Varolan öğeekle' bağlam menüsünü kullanarak yeni Reference.cs dosyasını .NET Framework *BeanTraderClient.csproj* projesine ekleyin. Aynı dosyanın her iki proje tarafından da kullanılması için 'bağlantı olarak' eklediğinizden emin olun (C# dosyasını kopyalamanın aksine). Eğer tek bir csproj (çoklu hedefleme kullanarak) ile hem .NET Core ve .NET Framework için oluşturuyorsanız, bu adım gerekli değildir.

01. *BeanTrader.cs*silin.

01. Yeni WCF istemcisi eskisine benzer, ancak oluşturulan koddaki birkaç ad alanı farklıdır. Bu nedenle, WCF istemci türleri BeanTrader.Service (ya da seçtiğiniz ne olursa olsun namespace adı) yerine BeanTrader.Model veya bir isim alanı olmadan kullanılan proje güncellemek için gereklidir. Bina *BeanTraderClient.Core.csproj* nerede bu değişikliklerin yapılması gerektiğini belirlemek için yardımcı olacaktır. Hem C# hem de XAML kaynak dosyalarında düzeltmeler gerekir.

01. Son olarak, `BeanTraderServiceClient` tür için kullanılabilir oluşturucular değiştiğinden *BeanTraderServiceClientFactory.cs* bir hata olduğunu keşfedeceksiniz. Bir `InstanceContext` bağımsız değişken `CallbackHandler` `Castle.Windsor` (IoC konteyner bir kullanılarak oluşturulan) sağlamak için kullanılır. Yeni yapıcılar yeni `CallbackHandler`s oluştururlar. Ancak, 'temel türünde `BeanTraderServiceClient`istediğinizle eşleşen yapıcılar vardır. Otomatik oluşturulan WCF istemci kodunun tümü kısmi sınıflarda bulunduğundan, kolayca genişletebilirsiniz. Bunu yapmak *için, BeanTraderServiceClient.cs* adında yeni bir dosya oluşturun ve ardından aynı ada sahip kısmi bir sınıf oluşturun (BeanTrader.Service ad alanını kullanarak). Daha sonra, burada gösterildiği gibi kısmi türüne bir oluşturucu ekleyin.

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

Yapılan bu değişikliklerle, Bean Trader örneği artık yeni bir .NET Standart uyumlu WCF istemcisi `Open` kullanacak ve `await OpenAsync` bunun yerine kullanmak için *TradingService.cs* aramayı değiştirmenin son düzeltmesini yapabilirsiniz.

WCF sorunları ele ile, Bean Trader örnek .NET Core sürümü şimdi temiz oluşturur!

## <a name="runtime-testing"></a>Çalışma zamanı testi

Proje .NET Core'a karşı temiz bir şekilde inşa olur olmaz geçiş çalışmalarının yapılmadığını unutmak kolaydır. Taşınan uygulamayı test etmek için de zaman bırakmak önemlidir. İşler başarılı bir şekilde inşa olduktan sonra, özellikle .NET Framework'u hedefleyen herhangi bir paket kullanıyorsanız, uygulamanın beklendiği gibi çalıştığından ve çalıştığından emin olun.

Portlu Bean Trader uygulamasını başlatmayı deneyelim ve neler olacağını görelim. Uygulama aşağıdaki istisna dışında başarısız olmadan önce çok uzak almaz.

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

Bu mantıklı, tabii ki. WCF'nin artık uygulama yapılandırmasını kullanmadığını unutmayın, bu nedenle app.config dosyasının eski system.serviceModel bölümünün kaldırılması gerekir. Güncelleştirilmiş WCF istemcisi kodunda aynı bilgilerin tümünü içerir, bu nedenle config bölümüne artık gerek yoktur. WCF bitiş noktasının app.config'de yapılandırılabilir olmasını istiyorsanız, bunu bir uygulama ayarı olarak ekleyebilir ve WCF hizmet bitiş noktasını yapılandırmadan almak için WCF istemci kodunu güncelleştirebilirsiniz.

*app.config*system.serviceModel bölümünü kaldırdıktan sonra, uygulama başlatıyor ancak kullanıcı girdiğinde başka bir istisna dışında başarısız oluyor.

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

Desteklenmeyen API. `Func<T>.BeginInvoke` [dotnet/corefx#5940'da](https://github.com/dotnet/corefx/issues/5940)açıklandığı gibi ,NET Core, `BeginInvoke` `EndInvoke` temel remoting bağımlılıkları nedeniyle temsilci türlerine ilişkin yöntemleri ve yöntemleri desteklemez. Bu sorun ve düzeltmesi,.NET Core blog gönderisi [için Gelen Temsilci.BeginInvoke](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/) Çağrıları'nda `BeginInvoke` `EndInvoke` daha ayrıntılı olarak `Task.Run` açıklanır, ancak özü şudur ve aramalar (veya mümkünse eşitleme alternatifleri) ile değiştirilmelidir. Genel çözümü burada uygulayarak, `BeginInvoke` arama tarafından `Invoke` `Task.Run`başlatılan bir çağrı ile değiştirilebilir.

```csharp
Task.Run(() =>
{
    return userInfoRetriever.Invoke();
}).ContinueWith(result =>
{
    // BeginInvoke's callback is replaced with ContinueWith
    var task = result.ConfigureAwait(false);
    CurrentTrader = task.GetAwaiter().GetResult();
}, TaskScheduler.Default);
```

`BeginInvoke` Bean Trader uygulaması kullanımı kaldırdıktan sonra .NET Core'da başarıyla çalışır!

![.NET Core üzerinde çalışan Fasulye Trader](./media/convert-project-from-net-framework/running-on-core.png)

Tüm uygulamalar farklıdır, bu nedenle kendi uygulamalarınızı .NET Core'a geçirmek için gereken belirli adımlar değişir. Ama umarım Bean Trader örnek genel iş akışı ve beklenebilir sorunların türleri gösterir. Ve, bu makalenin uzunluğuna rağmen, .NET Core üzerinde çalışması için Bean Trader örneğinde gerekli olan gerçek değişiklikler oldukça sınırlıydı. Birçok uygulama .NET Core'a aynı şekilde geçiş yapar; sınırlı veya hiç kod değişikliği gerektirmiyor.
