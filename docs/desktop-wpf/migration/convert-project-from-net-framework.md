---
title: WPF uygulamalarını .NET Core 3,0 ' e geçirme
description: Windows Presentation Foundation (WPF) uygulamasını .NET Core 3,0 ' e geçirmeyi öğrenin.
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: d8abcde4a941ac6e8f9f438cfe7e30f8d1e8a0bc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551952"
---
# <a name="migrating-wpf-apps-to-net-core"></a>WPF uygulamalarını .NET Core 'a geçirme

Bu makalede, .NET Framework bir Windows Presentation Foundation (WPF) uygulamasını .NET Core 3,0 ' e geçirmek için gereken adımlar ele alınmaktadır. Bağlantı noktası üzerinde bir WPF uygulamanız yoksa ancak işlemi denemek istiyorsanız, [GitHub](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader)'Da bulunan **çekirdeklere Trader** örnek uygulamasını kullanabilirsiniz. Özgün uygulama (hedefleme .NET Framework 4.7.2) NetFx\BeanTraderClient klasöründe bulunabilir. İlk olarak, genel olarak uygulama bağlantı noktası için gerekli adımları açıklayacak ve **çekirdeklere Trader** örneğine uygulanan belirli değişiklikleri adım adım inceleyeceğiz.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

.NET Core 'a geçiş yapmak için öncelikle şunları yapmanız gerekir:

01. NuGet bağımlılıklarını anlayın ve güncelleştirin:

    01. Biçimi kullanmak için NuGet bağımlılıklarını yükseltin `<PackageReference>` .
    01. .NET Core veya .NET Standard uyumluluğu için en üst düzey NuGet bağımlılıklarını gözden geçirin.
    01. NuGet paketlerini yeni sürümlere yükseltin.
    01. .Net bağımlılıklarını anlamak için [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) 'ni kullanın.

01. Proje dosyasını yeni SDK stili biçimine geçirin:

    01. Hem .NET Core hem de .NET Framework mi yoksa yalnızca .NET Core 'un mi hedefedilmeyeceğini seçin.
    01. İlgili proje dosyası özelliklerini ve öğelerini yeni proje dosyasına kopyalayın.

01. Derleme sorunlarını giderme:

    01. [Microsoft. Windows. uyumluluk](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/) paketine bir başvuru ekleyin.
    01. API düzeyi farklılıkları bulun ve onarın.
    01. Veya dışındaki *app.config* bölümlerini kaldırın `appSettings` `connectionStrings` .
    01. Gerekirse oluşturulan kodu yeniden oluşturun.

01. Çalışma zamanı testi:

    01. Bağlantı verilen uygulamanın beklendiği gibi çalıştığından emin olun.
    01. <xref:System.NotSupportedException>Özel durumlara dikkat edin.

## <a name="about-the-sample"></a>Örnek hakkında

Bu makale, gerçek dünyada WPF uygulamalarının sahip olabileceği gibi çeşitli bağımlılıklar kullandığından, [çekirdeklere Trader örnek uygulamasına](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader) başvurur. Uygulama büyük değildir, ancak karmaşıklık bakımından ' Merhaba Dünya ' öğesinden bir adım adım olmak üzere tasarlanmıştır. Uygulama, kullanıcıların gerçek uygulamaları taşıma sırasında karşılaşabileceği bazı sorunları gösterir. Uygulama bir WCF hizmeti ile iletişim kurar, bu nedenle düzgün çalışması için BeanTraderServer projesini çalıştırmanız gerekir (aynı GitHub deposunda mevcuttur) ve BeanTraderClient yapılandırmasının doğru uç noktayı işaret ettiğini doğrulayın. (Varsayılan olarak, örnek, sunucunun ' de aynı makinede çalıştığını varsayar `http://localhost:8090` , bu, BeanTraderServer 'ı yerel olarak başlatırsanız doğru olacaktır.)

Bu örnek uygulamanın .NET Core 'a yönelik güçlükleri ve çözümleri göstermesi gerektiğini aklınızda bulundurun. WPF en iyi yöntemlerini göstermek için tasarlanmamıştır. Aslında, taşıma sırasında en az birkaç ilginç zorluk çekdiğinizden emin olmak için bazı çapraz düzenleri kasıtlı olarak içerir.

## <a name="getting-ready"></a>Hazırlanma

.NET Framework uygulamayı .NET Core 'a geçirmeye yönelik birincil zorluk, bağımlılıklarının farklı şekilde çalışması veya hiç olmaması olabilir. Geçiş, şundan çok daha kolay; birçok NuGet paketi artık .NET Standard hedefleyin. .NET Core 2,0 ile başlayarak .NET Framework ve .NET Core yüzey alanları benzer hale gelmiştir. Bu nedenle bile, bazı farklılıklar (hem NuGet paketlerinden hem de kullanılabilir .NET API 'Lerinde desteklenir) kalır. Geçirilmekte olan ilk adım, uygulamanın bağımlılıklarını gözden geçirmekte ve başvuruların .NET Core 'a kolayca geçirilmiş bir biçimde olduğundan emin olmanızı sağlar.

### <a name="upgrade-to-packagereference-nuget-references"></a>`<PackageReference>`NuGet başvurularına yükselt

Daha eski .NET Framework projeler, genellikle NuGet bağımlılıklarını bir *packages.config* dosyasına listeler. Yeni SDK stili proje dosyası biçimi, NuGet paketlerine [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) ayrı bir yapılandırma dosyası yerine csproj dosyasındaki öğeler olarak başvurur.

Geçiş yaparken, stili başvuruların kullanılmasıyla iki avantajı vardır `<PackageReference>` :

- Bu, yeni .NET Core proje dosyası için gerekli olan NuGet başvurusunun stilidir. Zaten kullanıyorsanız `<PackageReference>` , bu proje dosyası öğeleri kopyalanabilir ve doğrudan yeni projeye yapıştırılabilir.
- packages.config bir dosyanın aksine, `<PackageReference>` öğeler yalnızca projenizin doğrudan bağlı olduğu en üst düzey bağımlılıklara başvurur. Diğer tüm geçişli NuGet paketleri geri yükleme sırasında belirlenir ve dosyadaki otomatik olarak obj\project.assets.jskaydedilir. Bu, projenizin hangi bağımlılıklara sahip olduğunu belirlemeyi çok daha kolay hale getirir. Bu, gerekli bağımlılıkların .NET Core 'da çalışıp çalışmadığını belirlemede yararlı olur.

.NET Framework uygulamayı .NET Core 'a geçirmeye yönelik ilk adım, NuGet başvurularını kullanacak şekilde günceldir `<PackageReference>` . Visual Studio bu basit hale getirir. Visual Studio 'nun **Çözüm Gezgini**projenin *packages.config* dosyasına sağ tıklayıp, ardından packages.config geçir ' i seçerek **packagereference**.

![PackageReference 'a yükseltme](./media/convert-project-from-net-framework/package-reference-migration.png)

Hesaplanan en üst düzey NuGet bağımlılıklarını gösteren bir iletişim kutusu görünür ve diğer NuGet paketlerinin en üst düzeye yükseltilmesi gerektiğini sorar. Bu diğer paketlerin hiçbirinin, çekirdeklere Trader örneği için en üst düzey olması gerekmez, bu nedenle bu kutuların tümünün işaretini kaldırabilirsiniz. Ardından **Tamam** ' a tıklayın ve *packages.config* dosya kaldırılır ve `<PackageReference>` öğeler proje dosyasına eklenir.

`<PackageReference>`-Style başvuruları, NuGet paketlerini bir paketler klasöründe yerel olarak depolamaz. Bunun yerine, genel bir iyileştirme olarak depolanır. Geçiş tamamlandıktan sonra, csproj dosyasını düzenleyin ve ' `<Analyzer>` den daha önce gelen çözümleyiciler ile ilgili tüm öğeleri *kaldırın. \packages* dizini. Endişelenmeyin; NuGet paketi başvurularını hala içerdiğinden, çözümleyiciler projeye dahil edilir. Yalnızca eski packages.config stili öğeleri temizlemeniz gerekir `<Analyzer>` .

### <a name="review-nuget-packages"></a>NuGet paketlerini gözden geçir

Artık projenin bağımlı olduğu en üst düzey NuGet paketlerini görebilmeniz için, bu paketlerin .NET Core 'da kullanılabilir olup olmadığını gözden geçirebilirsiniz. [NuGet.org](https://www.nuget.org/)' deki bağımlılıklara bakarak bir paketin .NET Core 'u destekleyip desteklemediğini belirleyebilirsiniz. Topluluk tarafından oluşturulan [fuget.org](https://www.fuget.org/) sitesi, bu bilgileri paket bilgileri sayfasının en üstünde belirgin şekilde gösterir.

.NET Core 3,0 hedeflenirken, .NET Core veya .NET Standard hedefleyen tüm paketler çalışır (.NET Core .NET Standard Surface alanını gerçekleştirdiğinden). Bazı durumlarda, kullanılan bir paketin belirli sürümü .NET Core veya .NET Standard hedeflemiyor, ancak daha yeni sürümler olacak. Bu durumda, paketin en son sürümüne yükseltmeyi göz önünde bulundurmanız gerekir.

.NET Framework hedefleyen paketleri de kullanabilirsiniz, ancak bu da bazı riskler sağlar. .NET Core ve .NET Framework Surface alanları bu tür bağımlılıkların *genellikle* çalıştığı kadar benzer olduğundan, .net core 'a .NET Framework bağımlılıklara izin verilir. Ancak, paket .NET Core 'da mevcut olmayan bir .NET API kullanmaya çalışırsa, bir çalışma zamanı özel durumu ile karşılaşırsınız. Bu nedenle, başka seçenek yoksa yalnızca .NET Framework paketlerine başvurmalıdır ve bu işlemin bir test yükü uyguladığından emin olun.

.NET Core veya .NET Standard hedefleyen paketlere başvuruluyorsa, diğer alternatifleri düşünmek zorunda kalmazsınız:

- Bunun yerine kullanılabilecek başka benzer paketler var mı? Bazen NuGet yazarları ayrı olarak yayımlar '. .NET Core 'un özel olarak hedeflediği kitaplıkların temel sürümleri. Kurumsal kitaplık paketleri, topluluk yayımlamanın bir örneğidir ". NetCore "alternatifler. Diğer durumlarda, belirli bir hizmet için yeni SDK 'lar (bazen farklı paket adlarıyla birlikte) .NET Standard için kullanılabilir. Kullanılabilir alternatif yoksa, .NET Core üzerinde çalışırken bunları tamamen test etmeniz gerektiğini aklınızda bulundurarak .NET Framework hedefli paketleri kullanmaya devam edebilirsiniz.

Çekirdeklere Trader örneği aşağıdaki en üst düzey NuGet bağımlılıklara sahiptir:

- [**Role. Wınsörü, sürüm 4.1.1**](https://www.castleproject.org/projects/windsor/)  

  Bu paket, .NET Core üzerinde çalıştığından 1,6 .NET Standard hedefler.

- [**Microsoft. CodeAnalysis. Fxcopçözümleyiciler, sürüm 2.6.3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  Bu bir meta pakettir. bu nedenle, hangi platformların desteklediği, ancak [belge](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers) en yeni sürümünün (2.9.2) hem .NET Framework hem de .NET Core için çalıştığını gösterir.

- [**Nito. AsyncEx, sürüm 4.0.1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  Bu paket .NET Core 'u hedeflemiyor, ancak daha yeni 5,0 sürümü. Bu, geçiş sırasında yaygındır çünkü çok sayıda NuGet paketi son zamanlarda .NET Standard destek ekledi, ancak eski proje sürümleri yalnızca .NET Framework hedefleyecektir. Sürüm farkı yalnızca küçük bir sürüm farklılığı ise, daha yeni sürüme yükseltmek genellikle kolaydır. Bu bir ana sürüm değişikliği olduğundan, pakette önemli değişiklikler olabileceğinden, yükseltmenin dikkatli olması gerekir. Bir yol ileri olur, ancak bu iyi bir yoldur.

- [**MahApps. Metro, sürüm 1.6.5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  Bu paket ayrıca .NET Core 'u hedeflemez, ancak daha yeni bir yayın öncesi sürüm (2,0-Alpha) içerir. Yine de, son değişiklikleri gözden geçirin, ancak daha yeni paket teşvik.

Çekirdeklere Trader örneğinin NuGet bağımlılıkları her iki hedef .NET Standard/. NET Core veya daha yeni sürümlere sahiptir, bu nedenle burada herhangi bir engelleyici sorun olması düşüktür.

### <a name="upgrade-nuget-packages"></a>NuGet paketlerini yükselt

Mümkünse, bu noktada yalnızca .NET Core veya .NET Standard hedef olan tüm paketlerin sürümlerini yükseltmek iyi olabilir (proje, hala .NET Framework hedefleyerek), herhangi bir son değişiklik bulmayı ve bu değişiklikleri daha önce bulur ve adreslemesini sağlar.

Uygulamanın mevcut .NET Framework sürümünde herhangi bir malzeme değişikliği yapmayın, bu, .NET Core 'u hedefleyen yeni bir proje dosyası olana kadar bekleyebilir. Ancak, NuGet paketlerini .NET Core ile uyumlu sürümlere yükseltmek, yeni proje dosyasını oluşturduktan sonra geçiş işlemini daha da kolay hale getirir ve uygulamanın .NET Framework ve .NET Core sürümleri arasındaki farkları sayısını azaltır.

Çekirdeklere Trader örneğinde, tüm gerekli yükseltmeler (Visual Studio 'nun NuGet Paket Yöneticisi kullanılarak) tek bir özel durumla kolayca yapılabilir: **Mahapps 'den yükseltme. Metro 1.6.5** ile **2,0** arasında, tema ve vurgu yönetimi API 'leriyle ilgili önemli değişiklikler ortaya çıkarır.

İdeal olarak, uygulama paketin daha yeni sürümünü kullanacak şekilde güncelleştirilir (Bu, .NET Core üzerinde çalışmaya daha olasıdır). Ancak bazı durumlarda, bu işlem uygulanabilir olmayabilir. Bu gibi durumlarda, gerekli değişiklikler önemsiz olmadığından ve bu öğretici, .NET Core 3 ' e geçirmeye odaklandığından, mahapps. Metro 2 için değil, **mahapps. Metro** 'yı yükseltmeyin **.** Ayrıca, çekirdeklere Trader uygulaması yalnızca **Mahapps. Metro**'nın küçük bir kısmını sağladığından, bu düşük riskli .NET Framework bir bağımlılıkdır. Kuşkusuz, geçiş işlemi tamamlandıktan sonra her şeyin çalıştığından emin olmak için test gerekir. Bu gerçek dünyada bir senaryosa, daha önce bazı teknik borcunun gerisinde kalmasını sağlamak için, bu işlemi izlemek üzere **Mahapps. Metro** sürüm 2,0 ' ye geçiş yapmak için bir sorun gidermek iyi olacaktır.

NuGet paketleri son sürümlere güncelleştirildikten sonra, `<PackageReference>` çekirdeklere Trader örneğinin proje dosyasındaki öğe grubu şuna benzemelidir.

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

### <a name="net-framework-portability-analysis"></a>.NET Framework taşınabilirlik Analizi

Projenizin NuGet bağımlılıklarının durumunu anladığınızda, dikkate alınması gereken sonraki şey .NET Framework API bağımlılıklarıdır. [.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) Aracı, projenizin kullandığı .NET API 'lerinin hangisinin diğer .net platformlarında kullanılabildiğini anlamak için yararlıdır.

Araç, bir [Visual Studio eklentisi](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), bir [komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases)veya [basit bir GUI](https://github.com/Microsoft/dotnet-apiport-ui)'de Sarmalanan, seçeneklerini kolaylaştıran bir araç olarak sunulur. .NET taşınabilirlik Çözümleyicisi 'ni (API bağlantı noktası) kullanma hakkında daha fazla bilgiyi, [masaüstü uygulamalarında .NET Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/) blog gönderisine TAŞıMA bölümündeki GUI 'yi kullanarak bulabilirsiniz. Komut satırını kullanmayı tercih ediyorsanız, gereken adımlar şunlardır:

1. Henüz yoksa [.net taşınabilirlik Çözümleyicisi](https://github.com/Microsoft/dotnet-apiport/releases) 'ni indirin.
1. .NET Framework uygulamasının derlemeler için başarıyla bağlantı kurmak için olduğundan emin olun (Bu, geçişe bakılmaksızın iyi bir fikirdir).
1. API bağlantı noktasını aşağıdaki gibi bir komut satırıyla çalıştırın.

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    `-f`Bağımsız değişkeni, çözümlenecek ikilileri içeren yolu belirtir. `-r`Bağımsız değişkeni istediğiniz çıktı dosyası biçimini belirtir. `-t`Bağımsız değişkeni, API kullanımının analiz edileceği .NET platformunu belirtir. Bu durumda, .NET Core 'u istersiniz.

HTML raporu açtığınızda, ilk bölüm çözümlenmiş ikililerin tümünü ve kullandıkları .NET API 'lerinin yüzdesini listeler ve hedeflenen platformda bulunur. Yüzde, kendi kendine anlamlı değildir. Daha fazla yararlı olan API 'Ler, eksik olan API 'Leri görşeydir. Bunu yapmak için, bir derleme adı seçin ya da ayrı derlemeler için raporlara gidin.

Kaynak koduna sahip olduğunuz derlemelere odaklanın. Çekirdeklere Trader ApiPort raporunda, örneğin, listelenen çok sayıda ikili dosya vardır, ancak çoğu NuGet paketlerine aittir. `Castle.Windsor` .NET Core 'da eksik olan System. Web API 'Lerine bağlı olduğunu gösterir. Bu sorun, daha önce .NET Core ' u desteklediğini doğruladığınıza ilişkin bir sorun değildir `Castle.Windsor` . NuGet paketleri farklı .NET platformlarıyla kullanılmak üzere farklı ikililerin olması yaygındır. bu nedenle, ' nin .NET Framework sürümünün `Castle.Windsor` System. Web API 'lerini kullanması veya aynı zamanda paket .NET Standard veya .NET Core 'u (bunun yaptığı) hedeflediğinden, ilgisiz olup olmadığı.

Çekirdeklere Trader örneğinde, dikkate almanız gereken tek ikili bir **Beantraderclient** örneğidir ve rapor yalnızca Iki .NET API 'nin eksik olduğunu gösterir: `System.ServiceModel.ClientBase<T>.Close` ve `System.ServiceModel.ClientBase<T>.Open` .

![BeanTraderClient taşınabilirlik raporu](./media/convert-project-from-net-framework/portability-report.png)

WCF Istemci API 'Leri (çoğunlukla) .NET Core üzerinde desteklendiğinden, bu merkezi API 'lerde kullanılabilecek alternatifler olması gerektiğinden bunlar sorunları engelliyor olabilir. Aslında, `System.ServiceModel` .NET Core yüzey alanına (kullanarak <https://apisof.net> ) bakarak bunun yerine .NET Core 'ta zaman uyumsuz alternatifler olduğunu görürsünüz.

Bu rapor ve önceki NuGet bağımlılığı analizine dayalı olarak, çekirdeklere Trader örneğini .NET Core 'a geçirmede önemli bir sorun olmaması gerekir. Geçiş işlemine gerçekten başlayacaksınız bir sonraki adıma hazırsınız.

## <a name="migrating-the-project-file"></a>Proje dosyası geçiriliyor

Uygulamanız yeni [SDK stili proje dosyası biçimini](../../core/tools/csproj.md)kullanmıyor ise, .NET Core 'u hedeflemek için yeni bir proje dosyası gerekir. Var olan csproj dosyasını değiştirebilir veya mevcut projenin geçerli durumunda kalmasını tercih ediyorsanız, .NET Core 'u hedefleyen yeni bir csproj dosyası ekleyebilirsiniz. Çoklu [hedefleme](../../standard/library-guidance/cross-platform-targeting.md) (birden çok hedef belirterek) ile tek bir SDK stili proje dosyası ile .NET Framework ve .NET Core için uygulamanın sürümlerini oluşturabilirsiniz `<TargetFrameworks>` .

Yeni proje dosyasını oluşturmak için, Visual Studio 'da yeni bir WPF projesi oluşturabilir veya bir `dotnet new wpf` geçici dizinde komutunu kullanarak proje dosyasını oluşturabilir ve ardından doğru konuma kopyalayabilir/yeniden adlandırabilirsiniz. Ayrıca, bazı proje dosyası geçişini otomatikleştirebilen, topluluk tarafından oluşturulan bir araç olan [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017). Araç yararlı olmakla kalmaz, geçişin tüm ayrıntılarının doğru olduğundan emin olmak için sonuçları gözden geçirmesi gerekir. Aracın en iyi şekilde işlemeyen belirli bir alan, NuGet paketlerini *packages.config* dosyalarından geçirmektedir. Araç, NuGet paketlerine başvurmak için bir *packages.config* dosyası kullanan bir proje dosyasında çalışıyorsa, `<PackageReference>` öğeleri otomatik olarak öğelere geçirilir, ancak `<PackageReference>` yalnızca en üst düzey olanlar yerine *Tüm* paketlere yönelik öğeler ekler. `<PackageReference>`Visual Studio ile öğelere zaten geçiş yaptıysanız (Bu örnekte yaptığınız gibi), araç geri kalanında dönüştürmeye yardımcı olabilir. Scott Hanselman, [csproj dosyalarını geçirirken blog gönderisine](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx), el ile geçiş yaparak eğitim verme ve bağlantı noktası için yalnızca birkaç projeniz varsa daha iyi sonuçlar verecektir. Ancak onlarca veya yüzlerce proje dosyası aktarıyorsanız, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) gibi bir araç bir yardım olabilir.

Çekirdeklere Trader örneği için yeni bir proje dosyası oluşturmak için `dotnet new wpf` geçici bir dizinde çalıştırın ve oluşturulan *. csproj* dosyasını *beantraderclient* klasörüne taşıyın ve bu dosyayı **Beantraderclient. Core. csproj**olarak yeniden adlandırın.

Yeni proje dosyası biçimi, içinde veya dizininde bulduğu C# dosyalarını, *resx* dosyalarını ve xaml dosyalarını otomatik olarak içerdiğinden, proje dosyası zaten neredeyse tamamlanmıştır! Geçişi sona erdirmede, eski ve yeni proje dosyalarını yan yana açın ve içerdiği bilgilerin geçirilmesi gerekip gerekmediğini görmek için eskisini gözden geçirin. Çekirdeklere Trader örnek durumunda, aşağıdaki öğeler yeni projeye kopyalanmalıdır:

- `<RootNamespace>`, `<AssemblyName>` Ve `<ApplicationIcon>` özelliklerinin hepsi kopyalanmalıdır.

- Ayrıca `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` , çekirdeklere Trader örneği bir AssemblyInfo.cs dosyasındaki derleme düzeyi öznitelikleri (gibi) içerdiğinden yeni proje dosyasına bir özellik eklemeniz gerekir `[AssemblyTitle]` . Varsayılan olarak, yeni SDK stili projeler bu öznitelikleri csproj dosyasındaki özelliklere göre otomatik olarak üretir. Bu durumda bunun gerçekleşmesini istemediğiniz için (otomatik olarak oluşturulan öznitelikler AssemblyInfo.cs ile çakışacak), ile otomatik olarak oluşturulan öznitelikleri devre dışı bırakabilirsiniz `<GenerateAssemblyInfo>` .

- *Resx* dosyaları gömülü kaynaklar olarak otomatik olarak dahil edilse de, `<Resource>` görüntüler gibi diğer öğeler değildir. Bu nedenle, `<Resource>` görüntü ve simge dosyaları katıştırmak için öğeleri kopyalayın. Yeni proje dosyası biçiminin glob desenleri desteğini kullanarak tek bir satıra png başvurularını basitleştirebilirsiniz: `<Resource Include="**\*.png" />` .

- Benzer şekilde, `<None>` öğeler otomatik olarak eklenir, ancak varsayılan olarak çıkış dizinine kopyalanmaz. Çekirdeklere Trader projesi `<None>` çıkış dizinine (davranışlar kullanılarak) *is* kopyalanmış bir öğe içerdiğinden `PreserveNewest` , `<None>` Bu dosya için otomatik olarak doldurulmuş öğeyi güncelleştirmeniz gerekir.

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- Çekirdeklere Trader örneği, bir XAML dosyası (varsayılan. vurgu. xaml) ( `Content` as yerine `Page` ) içerir, çünkü bu dosyada tanımlanan Temalar ve vurgular, uygulamanın kendine gömülmesini yerine çalışma ZAMANıNDA dosyanın xaml 'den yüklenmesidir. Yeni proje sistemi, bir XAML dosyası olduğundan, bu dosyayı otomatik olarak bir olarak ekler `<Page>` . Bu nedenle, XAML dosyasını bir sayfa () olarak kaldırmanız `<Page Remove="**\Default.Accent.xaml" />` ve içerik olarak eklemeniz gerekir.

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- Son olarak, tüm öğeleri ile kopyalayarak NuGet başvuruları ekleyin `<ItemGroup>` `<PackageReference>` . NuGet paketlerini daha önce .NET Core ile uyumlu sürümlere yükseltmişseniz, artık paket başvurularının .NET Core 'a özgü bir projede olduğundan emin olabilirsiniz.

Bu noktada, yeni projeyi BeanTrader çözümüne eklemek ve Visual Studio 'da açmak mümkün olmalıdır. Proje, **Çözüm Gezgini**doğru görünmelidir ve `dotnet restore BeanTraderClient.Core.csproj` paketleri başarıyla geri yüklemeniz gerekir (.NET Framework hedef olarak kullandığınız Mahapps. Metro sürümü ile ilgili iki beklenen uyarıyla birlikte).

Her iki proje dosyasını yan yana tutmak mümkün olsa da (ve eski projeyi tamamen olduğu gibi oluşturmak istiyorsanız bile istenebilir), geçiş işlemini karmaşıklaştırır (iki proje aynı bin ve obj klasörlerini kullanmayı dener) ve genellikle gerekli değildir. Hem .NET Core hem de .NET Framework hedefleri için derlemek isterseniz, `<TargetFramework>netcoreapp3.0</TargetFramework>` Yeni proje dosyasındaki özelliğini `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>` bunun yerine ile değiştirebilirsiniz. Çekirdeklere Trader örneği için artık gerekli olmadığından eski proje dosyasını (BeanTraderClient. csproj) silin. Her iki proje dosyasını da tutmak isterseniz, bunların farklı çıkış ve ara çıkış yolları için derlendiğinizden emin olun.

## <a name="fix-build-issues"></a>Derleme sorunlarını giderme

Taşıma işleminin üçüncü adımı, oluşturulacak projeyi alıyor. Proje dosyası bir SDK stili projeye dönüştürüldükten sonra bazı uygulamalar başarıyla derlencektir. Uygulamanız için bu durum, tebrikler! 4. adım ' a gidebilirsiniz. Diğer uygulamalarda, .NET Core için derleme için bazı güncelleştirmeler gerekecektir. `dotnet build`Çekirdeklere Trader örnek projesinde, örneğin (veya Visual Studio 'da derleme) çalıştırmayı denerseniz, birçok hata olacaktır, ancak bunları hızlıca sabitleyebilirsiniz.

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>System. ServiceModel başvuruları ve Microsoft. Windows. Compatibility

.NET Core için kullanılabilen ancak .NET Core App metapackage içinde otomatik olarak bulunmayan API 'Ler için ortak hata Kaynakları eksik. Bunu çözmek için pakete başvurmanız gerekir `Microsoft.Windows.Compatibility` . Uyumluluk Paketi, WCF istemcisi, Dizin Hizmetleri, kayıt defteri, yapılandırma, ACL 'Ler API 'Leri ve daha fazlası gibi Windows masaüstü uygulamalarında ortak olan geniş bir API kümesini içerir.

Çekirdeklere Trader örneğinde, derleme hatalarının çoğunluğu eksik türler nedeniyle oluşur <xref:System.ServiceModel> . Bunlar, gerekli WCF NuGet paketlerine başvurarak çözülebilir. WCF istemci API 'Leri, pakette mevcut olanlar arasındadır `Microsoft.Windows.Compatibility` , ancak bu nedenle uyumluluk paketine başvurmak daha iyi bir çözümdür (Ayrıca, API 'lerle ilgili sorunları ve ayrıca uyumluluk paketinin KULLANıLABILDIĞI WCF sorunlarını çözümler) de ele alınmaktadır. Bu `Microsoft.Windows.Compatibility` paket çoğu .NET Core 3,0 WPF ve WinForms taşıma senaryolarında yardımcı olur. NuGet başvurusunu öğesine ekledikten sonra `Microsoft.Windows.Compatibility` yalnızca bir derleme hatası kalır!

### <a name="cleaning-up-unused-files"></a>Kullanılmayan dosyaları temizleme

Genellikle, *Tüm* kaynağı otomatik olarak IÇEREN yeni SDK stili projelere eklenen yapıya dahil olmayan C# ve xaml dosyalarıyla ilişkili bir tür geçiş sorunu vardır.

Çekirdeklere Trader örneğinde gördüğünüz sonraki derleme hatası, *OldUnusedViewModel.cs*içindeki hatalı bir arabirim uygulamasına başvurur. Dosya adı bir ipucu, ancak Denetim sırasında bu kaynak dosyanın yanlış olduğunu fark edeceksiniz. Bu, eski .NET Framework projesine dahil edilmediğinden, daha önce soruna neden olmadı. Diskte bulunan ancak eski *csproj* 'a dahil olmayan kaynak dosyaları şimdi otomatik olarak eklenir.

Bu gibi tek bir sorun varsa, dosyanın gerekli olmadığını doğrulamak için önceki *csproj* ile karşılaştırmak kolaydır ve sonra `<Compile Remove="" />` ya da kaynak dosya bundan böyle herhangi bir yerde gerekmiyorsa, silin. Bu durumda, yalnızca *OldUnusedViewModel.cs*silmek güvenlidir.

Bu şekilde dışlanmanız gereken çok sayıda kaynak dosyanız varsa, `<EnableDefaultCompileItems>` Proje dosyasında özelliği false olarak ayarlayarak C# dosyalarının otomatik olarak eklenmesini devre dışı bırakabilirsiniz. Daha sonra, `<Compile Include>` yalnızca dahil etmek istediğiniz kaynakları oluşturmak için eski proje dosyasındaki öğeleri yeni birine kopyalayabilirsiniz. Benzer şekilde, `<EnableDefaultPageItems>` xaml sayfalarının otomatik olarak eklenmesini devre dışı bırakmak ve `<EnableDefaultItems>` her ikisini de tek bir özellikle denetlemek için kullanılabilir.

### <a name="a-brief-aside-on-multi-pass-compilers"></a>Çok geçişli derleyicilere kısa bir açıklama

Soruna neden olan dosyayı çekirdeklere Trader örneğinden kaldırdıktan sonra, yeniden derleyebilir ve dört hata alırsınız. Daha önce hiç kimse yok mu? Neden hata sayısı? C# derleyicisi, [çok taramalı bir derleyicidir](/archive/blogs/ericlippert/how-many-passes). Bu, her kaynak dosyanın iki kez gittiği anlamına gelir. İlk olarak, derleyici her kaynak dosyasındaki meta verileri ve bildirimlere bakar ve bildirim düzeyindeki sorunları tanımlar. Bu hatalar düzeltildi. Ardından, C# kaynağını Il 'de oluşturmak için koddan yeniden gider; Bunlar, şu anda gördüğünüz ikinci hata kümesidir.

> [!NOTE]
> C# derleyicisi [yalnızca iki geçişte daha fazlasını](/archive/blogs/ericlippert/how-many-passes)yapar, ancak nihai sonuç, bu gibi büyük kod değişiklikleri için derleyici hatalarının iki dalgada elde edilmesine neden olur.

### <a name="third-party-dependency-fixes-castlewindsor"></a>Üçüncü taraf bağımlılık düzeltmeleri (Role. Wınsma)

Bazı geçiş senaryolarında yer alan başka bir sorun sınıfı, bağımlılıkların .NET Framework ve .NET Core sürümleri arasındaki API farklarıdır. Bir NuGet paketi hem .NET Framework hem de .NET Standard ya da .NET Core 'u hedefliyorsa, farklı .NET hedefleriyle kullanılmak üzere farklı kitaplıklar olabilir. Bu, paketlerin farklı uygulamalar gerektirebilecek birçok farklı .NET platformunu desteklemesini sağlar. Aynı zamanda, farklı .NET platformlarını hedeflerken kitaplıklarda küçük API farklılıkları olabileceğini de gösterir.

Çekirdeklere Trader örneğinde göreceğiniz sonraki hata kümesi, `Castle.Windsor` API 'lerle ilgilidir. .NET Core çekirdeklere Trader projesi, `Castle.Windsor` .NET Framework hedefli proje (4.1.1) ile aynı sürümünü kullanır, ancak bu iki platform için uygulamalar biraz farklıdır.

Bu durumda, düzeltilmesi gereken aşağıdaki sorunları görürsünüz:

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly` .NET Core 'da kullanılamaz. Bununla birlikte, benzer `Classes.FromAssemblyContaining` BIR API mevcuttur. bu nedenle, çağrısı ile her iki kullanımını `Classes.FromThisAssembly()` ' a `Classes.FromAssemblyContaining(t)` , ' ın `t` çağrısını yapan türdür.
1. Benzer şekilde, *Bootstrapper.cs*içinde `Castle.Windsor.Installer.FromAssembly` . Bu, .NET Core 'da kullanılamaz. Bunun yerine, bu çağrı ile değiştirilebilir `FromAssembly.Containing(typeof(Bootstrapper))` .

### <a name="updating-wcf-client-usage"></a>WCF istemci kullanımı güncelleştiriliyor

`Castle.Windsor`Farklılıkları düzelttikten sonra, .NET Core çekirdeklere Trader projesinde kalan son derleme hatası, `BeanTraderServiceClient` (öğesinden türetilmeyen `DuplexClientBase` ) bir yönteme sahip değildir `Open` . Bu, bu geçiş sürecinin başlangıcında .NET taşınabilirlik Çözümleyicisi tarafından vurgulanan bir API olduğundan bu değildir. `BeanTraderServiceClient`Daha büyük bir sorunla ilgilenmenizi sağlar, ancak. Bu WCF istemcisi [Svcutil.exe](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı tarafından otomatik olarak oluşturuldu.

**Svcutil tarafından oluşturulan WCF istemcileri .NET Framework kullanımı için tasarlanmıştır.**

Svcutil tarafından oluşturulan WCF istemcilerinin kullanıldığı çözümlerin, .NET Core ile kullanmak üzere .NET Standard uyumlu istemcileri yeniden oluşturması gerekir. Eski istemcilerin çalışmayabileceği başlıca nedenlerden biri, WCF bağlamaları ve uç noktaları tanımlamak için uygulama yapılandırmasına bağımlıdır. .NET Standard WCF API 'Leri platformlar arası çalışabildiğinden (System.Configmerkezi API 'Lerinin kullanılamadığı durumlarda), .NET Core ve .NET Standard senaryoları için WCF istemcilerinin, yapılandırma yerine, program aracılığıyla bağlamaları ve uç noktaları tanımlamalıdır.

Aslında `<system.serviceModel>` app.config bölümüne (Svcutil veya el ile oluşturulan) bağlı olan tüm WCF istemci kullanımları .NET Core üzerinde çalışacak şekilde değiştirilmelidir.

.NET Standard uyumlu WCF istemcilerini otomatik olarak oluşturmak için iki yol vardır:

- `dotnet-svcutil`Araç, aynı şekilde, Svcutil 'ın daha önce çalıştığı bir şekılde WCF istemcileri üreten bir .net aracıdır.
- Visual Studio, bağlı hizmetler özelliğinin [WCF Web hizmeti başvurusu](../../core/additional-tools/wcf-web-service-reference-guide.md) SEÇENEĞINI kullanarak WCF istemcileri oluşturabilir.

Her iki yaklaşım da geçerlidir. Alternatif olarak, WCF istemci kodunu kendiniz de yazabilirsiniz. Bu örnek için, Visual Studio bağlı hizmet özelliğini kullanmayı seçtim. Bunu yapmak için, Visual Studio 'nun Çözüm Gezgini ' nde *beantraderclient. Core* projesine sağ tıklayın ve **Add**  >  **bağlı hizmet**Ekle ' yi seçin. Ardından, WCF Web hizmeti başvuru sağlayıcısını seçin. Bu, arka uç çekirdeklere Trader Web hizmetinin adresini ( `localhost:8080` sunucuyu yerel olarak çalıştırıyorsanız) ve üretilen türlerin kullanması gereken ad alanını (örneğin,**Beantrader. Service**) belirtebileceğiniz bir iletişim kutusu getirir.

![WCF Web hizmeti başvurusu bağlı hizmeti Iletişim kutusu](./media/convert-project-from-net-framework/connected-service-dialog.png)

**Son** düğmesini seçtikten sonra, projeye yeni bir bağlı hizmetler düğümü eklenir ve çekirdeklere Trader hizmetine erişmek için yenı .NET Standard WCF istemcisini içeren düğüm altına bir Reference.cs dosyası eklenir. `GetEndpointAddress` `GetBindingForEndpoint` Bu dosyadaki veya metotlara baktığınızda, bağlamaların ve uç noktaların artık programlı olarak oluşturulduğunu görürsünüz (uygulama yapılandırması aracılığıyla değil). ' Bağlı hizmetler Ekle ' özelliği aynı zamanda proje dosyasındaki bazı System. ServiceModel paketlerine başvurular ekleyebilir, bu da gerekli tüm WCF paketleri Microsoft. Windows. Compatibility aracılığıyla dahil edilir. Ek System. ServiceModel öğelerinin eklenmiş olup olmadığını görmek için csproj `<PackageReference>` 'ı denetleyin ve varsa bunları kaldırın.

Projemizin şimdi yeni WCF istemci sınıflarına sahiptir ( *Reference.cs*içinde), ancak yine de eskileri de vardır (BeanTrader.cs içinde). Bu noktada iki seçenek vardır:

- Özgün .NET Framework projesini (yeni .NET Core 'a hedeflenmiş bir şekilde) oluşturabilmek istiyorsanız, `<Compile Remove="BeanTrader.cs" />` uygulamanın .NET Framework ve .NET Core sürümlerinin farklı WCF istemcileri kullanması için .NET Core projesinin csproj dosyasındaki bir öğeyi kullanabilirsiniz. Bu, var olan .NET Framework projesini değiştirmeden bırakma avantajına sahiptir, ancak, oluşturulan WCF istemcilerinin kullanıldığı kodun, .NET Core 'da .NET Framework projesi dışında bir şekilde farklı olması gerekebilir. bu nedenle, `#if` bazı WCF istemci kullanımını koşullu olarak derlemek için (örneğin, istemci oluşturma), .NET Core için inşa edildiğinde ve .NET Framework için inşa edildiğinde başka bir yolla çalışacak şekilde yönergeler kullanmanız gerekir.

- Diğer yandan, var olan .NET Framework projesindeki bazı kod karmaşıklığı kabul edilebilir ise, *BeanTrader.cs* tümünü de kaldırabilirsiniz. Yeni WCF istemcisi .NET Standard için oluşturulduğundan, hem .NET Core hem de .NET Framework senaryolarında çalışacaktır. .NET Core 'a ek olarak .NET Framework oluşturuyorsanız (çoklu hedefleyerek veya iki csproj dosyası içeriyorsa), bu yeni *Reference.cs* dosyasını her iki hedef için de kullanabilirsiniz. Bu yaklaşım, kodun iki farklı WCF istemcisini desteklemesi için bifurde gerek duymayabileceğinden faydalanır. her yerde aynı kod kullanılacaktır. Dezavantajı, (kabul edilebilir) .NET Framework projenin değiştirilmesini içerir.

Çekirdeklere Trader örneği söz konusu olduğunda, geçişi kolaylaştırmak için özgün projede küçük değişiklikler yapabilirsiniz, bu nedenle WCF istemci kullanımını mutabık kılmak için aşağıdaki adımları izleyin:

01. Çözüm Gezgini 'nden ' Varolan öğe Ekle ' bağlam menüsünü kullanarak yeni Reference.cs dosyasını .NET Framework *Beantraderclient. csproj* projesine ekleyin. Aynı dosyanın her iki proje tarafından da (C# dosyasını kopyalamaya karşı) kullanılması için ' as link ' eklediğinizden emin olun. Hem .NET Core için oluşturuyorsanız hem de tek bir csproj ile .NET Framework (Çoklu hedefleme kullanarak), bu adım gerekli değildir.

01. *BeanTrader.cs*silin.

01. Yeni WCF istemcisi eskisiyle benzerdir, ancak oluşturulan koddaki birçok ad alanı farklıdır. Bu nedenle, WCF istemci türlerinin BeanTrader. model yerine (veya seçtiğiniz herhangi bir ad alanı adı) bir ad alanı olmadan kullanılması için projeyi güncelleştirmeniz gerekir. *Beantraderclient. Core. csproj* oluşturma, bu değişikliklerin nerede yapılması gerektiğini belirlemesine yardımcı olur. Düzeltmelerin her ikisi de C# ve XAML kaynak dosyalarında gerekecektir.

01. Son olarak, *BeanTraderServiceClientFactory.cs* içinde bir hata olduğunu öğrenirsiniz çünkü bu tür için kullanılabilir oluşturucular `BeanTraderServiceClient` değişmiştir. Bir `InstanceContext` bağımsız değişken ( `CallbackHandler` `Castle.Windsor` ioc kapsayıcısından kullanılarak oluşturulmuş) sağlamak için kullanılır. Yeni oluşturucular yeni s oluştur `CallbackHandler` . Bununla birlikte, `BeanTraderServiceClient` temel türünde, istediğiniz şekilde eşleşen oluşturucular vardır. Otomatik olarak oluşturulan WCF istemci kodu kısmi sınıflarda bulunduğundan, kolayca genişletebilirsiniz. Bunu yapmak için, *BeanTraderServiceClient.cs* adlı yeni bir dosya oluşturun ve ardından aynı ada sahip kısmi bir sınıf oluşturun (BeanTrader. Service ad alanını kullanarak). Daha sonra, burada gösterildiği gibi kısmi türe bir Oluşturucu ekleyin.

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

Bu değişiklikler yapıldıktan sonra, çekirdeklere Trader örneği artık yeni .NET Standard uyumlu bir WCF istemcisi kullanacaktır ve `Open` bunun yerine *TradingService.cs* içindeki çağrıyı değiştirmenin son düzeltmesini yapabilirsiniz `await OpenAsync` .

WCF sorunları ele ılarak, çekirdeklere Trader örneğinin .NET Core sürümü artık düzgün şekilde oluşturulur!

## <a name="runtime-testing"></a>Çalışma zamanı testi

Proje .NET Core 'a karşı düzgün bir şekilde oluşturulsa geçiş işinin yapılmadığında emin olmak kolaydır. Ayrıca, bağlantı verilen uygulamayı test etmek için zaman bırakmanız önemlidir. İşlemler başarıyla kurulduktan sonra, özellikle de .NET Framework hedefleyen paketler kullanıyorsanız, uygulamanın çalıştığından ve beklendiği gibi çalıştığından emin olun.

Ayrıca, bağlantı noktası çekirdeklere Trader uygulamasını başlatmayı deneyelim ve neler olduğunu görelim. Uygulama aşağıdaki özel durumla başarısız olmadan önce değil.

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

Bu, kuşkusuz bir fikir sunar. WCF 'nin artık uygulama yapılandırması kullanmadığını unutmayın, bu nedenle app.config dosyanın eski System. serviceModel bölümünün kaldırılması gerekir. Güncelleştirilmiş WCF istemcisi, kodunda aynı bilgilerin tümünü içerir, bu nedenle yapılandırma bölümü artık gerekli değildir. WCF uç noktasının app.config yapılandırılabilmesine isterseniz, bunu bir uygulama ayarı olarak ekleyebilir ve WCF hizmet uç noktasını yapılandırmadan almak için WCF istemci kodunu güncelleştirebilirsiniz.

*app.config*System. ServiceModel bölümünü kaldırdıktan sonra, uygulama başlatılır ancak kullanıcı oturum açtığında başka bir özel durumla başarısız olur.

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

Desteklenmeyen API `Func<T>.BeginInvoke` . [DotNet/corefx # 5940](https://github.com/dotnet/corefx/issues/5940)' de açıklandığı gibi, .NET Core, `BeginInvoke` `EndInvoke` temel uzaktan iletişim bağımlılıkları nedeniyle temsilci türlerindeki ve yöntemlerini desteklemez. Bu sorun ve bu sorunun düzeltilmesi, .NET Core blog gönderisine [Ilişkin geçiş temsilcisi. BeginInvoke çağrılarında](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/) daha ayrıntılı bir şekilde açıklanmıştır, ancak bu, `BeginInvoke` `EndInvoke` çağrılarınız `Task.Run` (veya mümkünse zaman uyumsuz alternatifler) ile değiştirilmelidir. Genel çözümü buraya uygulayarak, `BeginInvoke` çağrı `Invoke` tarafından başlatılan bir çağrı ile değiştirilebilir `Task.Run` .

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

Kullanım kaldırıldıktan sonra `BeginInvoke` , çekirdeklere Trader uygulaması .NET Core 'da başarıyla çalışır!

![.NET Core üzerinde çalışan çekirdeklere Trader](./media/convert-project-from-net-framework/running-on-core.png)

Tüm uygulamalar farklıdır, bu nedenle kendi uygulamalarınızı .NET Core 'a geçirmek için gereken belirli adımlar farklılık gösterir. Ancak çekirdeklere Trader örneği, genel iş akışını ve beklenilen sorun türlerini gösterir. Bu makalenin uzunluğuna karşın, .NET Core üzerinde çalışmasını sağlamak için çekirdeklere Trader örneğinde gerekli olan gerçek değişiklikler oldukça sınırlı. Birçok uygulama aynı şekilde .NET Core 'a geçirilir; sınırlı ve hatta kod değişikliğine gerek yoktur.
