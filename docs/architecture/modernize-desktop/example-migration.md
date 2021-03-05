---
title: .NET 5’e geçiş örneği
description: .NET Framework .NET 5 ' e hedefleme örnek uygulamaların nasıl geçirileceği gösteriliyor.
ms.date: 01/19/2021
ms.openlocfilehash: 5b3743c68ee0426efffda6f999dffea788f493e9
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206548"
---
# <a name="example-of-migrating-to-net"></a>.NET 'e geçme örneği

Bu bölümde, var olan uygulamanızın .NET Framework .NET 'e geçişini gerçekleştirmenize yardımcı olacak pratik yönergeler sunuyoruz.

İzleyebileceğiniz bir işlem ve her adımda göz önünde bulundurmanız gereken en önemli noktalar sunuyoruz.

Ardından, hem WinForms hem de WPF sürümlerinden örnek bir masaüstü uygulaması için adım adım geçiş sürecini belgeliyoruz.

## <a name="migration-process-overview"></a>Geçiş işlemine genel bakış

Geçiş işlemi dört sıralı adımdan oluşur:

1. **Hazırlık**: projenin, nelerin ilerimize dair bir fikir sahibi olması için bağımlılıkları anlayın. Bu adımda, geçerli projeyi geçiş için başlangıç noktasını basitleştiren bir duruma getirin.

2. **Proje dosyasını geçirme:** .net PROJELERI yeni SDK stili proje biçimini kullanır. Bu biçimle yeni bir proje dosyası oluşturun veya SDK stilini kullanmak için sahip olduğunuz güncelleştirmeyi güncelleştirin.

3. **Kodu ve derlemeyi onarma:** .NET ' te, .NET Framework ve .NET arasındaki API düzeyi farklılıklarına yönelik kod oluşturun. Gerekirse, üçüncü taraf paketleri .NET ' i destekleenlere güncelleştirin.

4. **Çalıştır ve test et:** Çalışma zamanına kadar gösterilmeyebilir farklılıklar olabilir. Bu nedenle, uygulamayı çalıştırmayı unutmayın ve her şeyin beklendiği gibi çalıştığından test edin.

### <a name="preparation"></a>Hazırlık

#### <a name="migrate-packagesconfig-file"></a>packages.config dosyayı geçir

.NET Framework bir uygulamada, dış paketlere yapılan tüm başvurular *packages.config* dosyasında belirtilir. .NET sürümünde artık *packages.config* dosyasını kullanma gereksinimi yoktur. Bunun yerine, uygulamanızın NuGet paketlerini belirtmek için proje dosyasının içindeki [Packagereference](../../core/project-sdk/msbuild-props.md#packagereference) özelliğini kullanın.

Bu nedenle, bir biçimden diğerine geçiş yapmanız gerekir. *packages.config* dosyasında bulunan bağımlılıkları alarak ve bunları biçimiyle proje dosyasına geçirerek güncelleştirmeyi el ile yapabilirsiniz `PackageReference` . Ya da, Visual Studio 'Nun işi sizin yerinize yapmasına izin verebilirsiniz: *packages.config* dosyasına sağ tıklayıp **packages.config Packagereference 'a geçir** seçeneğini belirleyin.

#### <a name="verify-every-dependency-compatibility-in-net"></a>.NET 'teki tüm bağımlılık uyumluluğunu doğrulayın

Paket başvurularını geçirdikten sonra her bir başvuruyu uyumluluk için denetlemeniz gerekir. Uygulamanızın [NuGet.org](https://www.nuget.org/)üzerinde kullandığı her bir NuGet paketinin bağımlılıklarını inceleyebilirsiniz. Pakette .NET Standard bağımlılıklar varsa, .NET, tüm .NET Standard sürümlerini [desteklediğinden](../../standard/net-standard.md#net-implementation-support) .NET 5,0 üzerinde çalışacaktır. Aşağıdaki görüntüde, paket için bağımlılıklar gösterilmektedir `Castle.Windsor` :

![Role. Wın_sor paketi için NuGet bağımlılıklarının ekran görüntüsü](./media/example-migration-core/nuget-dependencies.png)

Paket uyumluluğunu denetlemek için, <https://fuget.org> sürümler ve Bağımlılıklar hakkında daha ayrıntılı bilgi sunan aracı kullanabilirsiniz.

Proje, .NET desteklemeyen eski paket sürümlerine başvuruda bulunuyor, ancak bunu destekleyen daha yeni sürümleri bulabilirsiniz. Bu nedenle, paketleri daha yeni sürümlere güncelleştirmek genellikle iyi bir öneriydi. Ancak, paket sürümünün güncelleştirilmesi, kodunuzun güncelleştirilmesini zorlayan bazı önemli değişiklikler getirebileceğini göz önünde bulundurmanız gerekir.

Uyumlu bir sürüm bulamazsanız ne olur? Bu son değişiklikler nedeniyle bir paketin sürümünü güncelleştirmek istemiyorsanız ne yapmanız gerekir? Endişelenmeyin çünkü bir .NET uygulamasından .NET Framework paketlerine bağlı olabilir. Dış paket .NET üzerinde kullanılamayan bir API 'YI çağırırsa çalışma zamanı hatalarına neden olabileceğinden, bunu kapsamlı olarak sınamayı unutmayın. Bu, güncelleştirileymeyen eski bir paket kullanırken ve yalnızca .NET üzerinde çalışacak şekilde yeniden hedefleyecekseniz için harika bir yoldur.

#### <a name="check-for-api-compatibility"></a>API uyumluluğunu denetle

.NET Framework ve .NET sürümündeki API yüzeyi benzer ancak özdeş olduğundan, .NET üzerinde hangi API 'Lerin kullanılabilir olduğunu ve hangilerinin olmadığını denetlemeniz gerekir. .Net taşınabilirlik Çözümleyicisi Aracı 'nı .NET üzerinde mevcut olmayan bir şekilde kullanabilirsiniz. Uygulamanızın ikili düzeyine bakar, çağrılan tüm API 'Leri ayıklar ve hedef çerçeveinizdeki hangi API 'Lerin kullanılabilir olduğunu listeler (Bu durumda .NET 5,0).

Bu araçla ilgili daha fazla bilgiyi şurada bulabilirsiniz:

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

Bu aracın ilginç bir yönü, yalnızca kendi kodunuzla gelen farkları değil, farklı bir şekilde değişiklik yapamazsınız. Bu paketlerin çoğunu .NET ile çalışacak şekilde güncelleştirdiğinizden emin olun.

### <a name="migrate-with-try-convert-tool"></a>TRY Dönüştürme aracıyla geçir

[Dönüştürmeyi dene](https://github.com/dotnet/try-convert/releases) Aracı, bir projeyi geçirmek için harika bir yoldur. Bu, proje dosyanızı eski stilden yeni SDK stiline yükseltmeyi ve ilgili projeleri .NET 5 ' e yeniden hedeflemesini deneyen küresel bir araçtır. Yüklendikten sonra aşağıdaki komutları çalıştırabilirsiniz:

```dotnetcli
try-convert -p "<path to your project file>"
```

Veya

```dotnetcli
try-convert -w "<path to your solution>"
```

> [!NOTE]
> TRY-Convert Aracı, [.NET Yükseltme Yardımcısı aracının](https://aka.ms/dotnet-upgrade-assistant)bir parçası olarak otomatik olarak çalıştırılır. Tam yükseltme yardımcısını çalıştırmayı deneyin ve yalnızca dönüştürmeyi deneyin.

Araç dönüştürmeyi denemeden sonra, çalıştırmak ve test etmek için dosyalarınızı Visual Studio 'da yeniden yükleyin. Dönüştürme işleminin, projenizin özellikleri nedeniyle dönüştürme işlemini gerçekleştiremeyeceği bir olasılık vardır. Bu durumda, aşağıdaki adımlara bakabilirsiniz.

#### <a name="migrate-manually"></a>El ile geçiş yapma

1. Yeni .NET projesi oluşturma

Çoğu durumda, mevcut projenizi yeni .NET biçimine güncelleştirmek isteyeceksiniz. Bununla birlikte, eskisini koruyarak da yeni bir proje oluşturabilirsiniz. Eski projeyi güncelleştirmenin ana dezavantajı, sizin ve geliştirme ekibiniz için önemli olabilecek tasarımcı desteğini kaybetmeniz olabilir. Tasarımcıyı kullanmaya devam etmek istiyorsanız, eski bir .NET projesi oluşturup eskisiyle ve paylaşma varlıklarıyla paralel olarak oluşturmanız gerekir. Tasarımcıda Kullanıcı arabirimi öğelerini değiştirmeniz gerekiyorsa, bunu yapmak için eski projeye geçiş yapabilirsiniz. Varlıklar bağlı olduğundan, .NET projesinde de güncelleştirilecektir.

.NET için [SDK stili proje](../../core/project-sdk/msbuild-props.md) , .NET Framework proje biçiminden çok daha basittir. Daha önce bahsedilen girdilerden ayrı `PackageReference` olarak, çok daha fazlasını yapmanız gerekmez. Yeni proje biçimi, [belirli uzantılara sahip dosyaları](../../core/project-sdk/overview.md#default-includes-and-excludes), örneğin `.cs` ve `.xaml` dosyaları proje dosyasına açıkça dahil etmek zorunda kalmadan, varsayılan olarak içerir.

#### <a name="assemblyinfo-considerations"></a>AssemblyInfo konuları

Öznitelikler, .NET projelerinde otomatik olarak oluşturulur. Proje bir *AssemblyInfo.cs* dosyası içeriyorsa, tanımlar çoğaltılır ve bu da derleme çakışmalarına neden olur. Eski *AssemblyInfo.cs* dosyasını silebilir veya aşağıdaki girişi .NET proje dosyasına ekleyerek, oto oluşturmayı devre dışı bırakabilirsiniz:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a>Kaynaklar

Gömülü kaynaklar otomatik olarak dahil edilir ancak kaynaklar değildir, bu nedenle kaynakları yeni proje dosyasına geçirmeniz gerekir.

#### <a name="package-references"></a>Paket başvuruları

packages.config, **PackageReference 'A geçir** seçeneğiyle, dış paket başvurularınızı daha önce belirtildiği gibi yeni biçime kolayca taşıyabilirsiniz.

#### <a name="update-package-references"></a>Paket başvurularını Güncelleştir

Bulduğunuz paketlerin sürümlerini, önceki bölümde gösterildiği gibi güncelleştirin.

### <a name="fix-the-code-and-build"></a>Kodu ve derlemeyi düzeltir

#### <a name="microsoftwindowscompatibility"></a>Microsoft. Windows. Compatibility

Uygulamanız, kayıt defteri, ACL 'Ler veya WCF gibi .NET üzerinde kullanılamayan API 'Lere bağımlıysa, `Microsoft.Windows.Compatibility` Bu Windows 'a özgü API 'leri eklemek için pakete bir başvuru eklemeniz gerekir. Bunlar .NET üzerinde çalışır, ancak platformlar arası olmadıklarından dahil değildir.

<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>Kodunuzla uyumlu olmayan API 'leri tanımanıza yardımcı olan API Çözümleyicisi () adlı bir araç vardır.

#### <a name="use-if-directives"></a>\#IF yönergeleri kullanın

.NET Framework ve .NET hedeflenirken farklı yürütme yollarına ihtiyacınız varsa, derleme sabitlerini kullanmanız gerekir. \#Aynı kod tabanını her iki hedef için de tutmak üzere kodunuza bazı if yönergeleri ekleyin.

#### <a name="technologies-not-available-on-net"></a>.NET üzerinde sunulan teknolojiler

Bazı teknolojiler .NET üzerinde kullanılamaz, örneğin:

* Uygulama
* Uzaktan iletişim
* Kod Erişimi Güvenliği
* WCF sunucusu
* Windows Iş akışı

Bu nedenle, bunları uygulamanızda kullanıyorsanız bu teknolojilerin yerini bulmanız gerekir. Daha fazla bilgi için [.NET Core ve .NET 5 + makalesinde kullanılamayan .NET Framework teknolojileri](../../core/porting/net-framework-tech-unavailable.md) bölümüne bakın.

#### <a name="regenerate-autogenerated-clients"></a>Otomatik olarak oluşturulan istemcileri yeniden üret

Uygulamanız bir WCF istemcisi gibi otomatik olarak oluşturulmuş kod kullanıyorsa, .NET hedeflemek için bu kodu yeniden oluşturmanız gerekebilir. Bazen, bazı eksik başvuruları, varsayılan .NET derlemeleri kümesinin bir parçası olarak dahil edildiklerinden, bulabilirsiniz. Gibi bir araç kullanarak <https://apisof.net/> , eksik başvurunun bulunduğu derlemeyi kolayca bulabilir ve NuGet 'ten ekleyebilirsiniz.

#### <a name="rolling-back-package-versions"></a>Paket sürümleri geri alınıyor

Genel bir kural olarak, .NET ile uyumlu olmak için her tek paket sürümünü daha iyi güncelleştirdiniz. Bununla birlikte, bir derlemenin güncelleştirilmiş ve uyumlu bir sürümünü hedefleme için yalnızca ödeme yapmayın. Değişiklik maliyeti kabul edilebilir değilse, paket sürümlerinin .NET Framework ' de kullandıklarınızı tutarak geri almasını düşünebilirsiniz. .NET hedeflenmese de, desteklenmeyen bazı API 'Leri çağırmadığı müddetçe iyi çalışmalıdır.

### <a name="run-and-test"></a>Çalıştırma ve test etme

Uygulamanızın hatasız olarak oluşturulmasını sağlayarak, her işlevselliği test ederek geçişin son adımını başlatabilirsiniz.

Bu son adımda, uygulamanızın karmaşıklığına ve kullanmakta olduğunuz bağımlılıklara ve API 'Lere bağlı olarak çeşitli farklı sorunlar bulabilirsiniz.

Örneğin, yapılandırma dosyalarını (*app.config*) kullanıyorsanız, çalışma zamanında yapılandırma bölümlerinin olmadığı gibi bazı hatalar bulabilirsiniz. `Microsoft.Extensions.Configuration`NuGet paketinin kullanılması bu hatayı düzeltir.

Hatalar için bir diğer neden, `BeginInvoke` .net üzerinde desteklenmediğinden ve yöntemlerinin kullanılmasının bir nedenidir `EndInvoke` . .Net üzerinde mevcut olmayan bir uzaktan Iletişim bağımlılığı olduğundan, .NET üzerinde desteklenmez. Bu sorunu gidermek için `await` anahtar sözcüğünü (kullanılabilir olduğunda) veya yöntemini kullanmayı deneyin <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> .

Kodunuzda .NET ile çalışma zamanında sorun oluşmasına neden olabilecek API 'Leri ve kod düzenlerini tanımlamanızı sağlamak için uyumluluk Çözümleyicileri ' ni kullanabilirsiniz. <https://github.com/dotnet/platform-compat>' A gidin ve projenizde .NET API Çözümleyicisi ' ni kullanın.

## <a name="migrating-a-windows-forms-application"></a>Windows Forms uygulamasını geçirme

Bir Windows Forms uygulamasının tüm geçiş sürecini göstermek için, ' de bulunan eShop örnek uygulamasını geçirmeyi seçtik <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> . Geçişin tüm sonucunu ' de bulabilirsiniz <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .

Bu uygulama bir ürün kataloğu gösterir ve kullanıcının ürünlere gezinme, filtre uygulama ve arama yapmasına izin verir. Bir mimari görünümünden uygulama, bir arka uç veritabanına façlade görevi gören bir dış WCF hizmetini kullanır.

Ana uygulama penceresini aşağıdaki resimde görebilirsiniz:

![Ana uygulama penceresi](./media/example-migration-core/main-application-window.png)

*. Csproj* proje dosyasını açarsanız şuna benzer bir şey görebilirsiniz:

![CSPROJ dosya içeriğinin ekran görüntüsü](./media/example-migration-core/csproj-file.png)

Daha önce belirtildiği gibi, .NET projesi daha kompakt bir stile sahiptir ve proje yapısını yeni .NET SDK stiline geçirmeniz gerekir.

Çözüm Gezgini, Windows Forms projesine sağ tıklayın ve **Proje düzenlemeyi kaldır**' ı seçin  >  .

Artık. csproj dosyasını güncelleştirebilirsiniz. İçeriğin tamamını silecek ve aşağıdaki kodla değiştirilecek:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

Projeyi kaydedin ve yeniden yükleyin. Artık proje dosyasını güncellemeyi tamamladınız ve proje .NET 'i hedefliyor.

Projeyi bu noktada derlerseniz, WCF istemci başvurusuyla ilgili bazı hatalar bulacaksınız. Bu kod otomatik olarak oluşturulduktan sonra, .NET hedeflemek için yeniden oluşturmanız gerekir.

![Visual Studio 'da derleme hatalarının ekran görüntüsü](./media/example-migration-core/winforms-compilation-errors.png)

*Reference.cs* dosyasını silin ve yeni bir hizmet istemcisi oluşturun.

**Bağlı hizmetler** ' e sağ tıklayın ve **bağlı hizmet ekle** seçeneğini belirleyin.

![Bağlı hizmet ekle seçeneği belirlenmiş olan bağlı hizmetler menüsünün ekran görüntüsü](./media/example-migration-core/add-connected-service.png)

Bağlı hizmetler penceresi açılır. **MICROSOFT WCF Web hizmeti** seçeneğini belirleyin.

![Bağlı hizmetler penceresinin ekran görüntüsü](./media/example-migration-core/connected-services-window.png)

Bu örnekteki aynı çözümde WCF hizmeti varsa, bir hizmet URL 'SI belirtmek yerine **bulma** seçeneğini belirleyebilirsiniz.

![WCF Web hizmeti başvurusunu Yapılandır penceresinin ekran görüntüsü](./media/example-migration-core/configure-wcf-reference.png)

Hizmet konumlandırıldıktan sonra araç, hizmet tarafından uygulanan API sözleşmesini yansıtır. Ad alanının adını `eShopServiceReference` aşağıdaki görüntüde gösterildiği gibi olacak şekilde değiştirin:

![API sözleşmesinin ve ad alanının değiştiği ekran görüntüsü](./media/example-migration-core/api-contract-namespace.png)

**Son** düğmesini seçin. Bir süre sonra, üretilen kodu görürsünüz.

Üç adet otomatik olarak oluşturulan dosya görmeniz gerekir:

1. *Başlarken*: WCF ile ilgili bazı bilgiler sağlamak için GitHub bağlantısı.
2. *ConnectedService.js*: hizmete bağlanmak için yapılandırma parametreleri.
3. *Reference.cs*: gerçek WCF istemci kodu.

![Otomatik olarak oluşturulan üç dosyayı içeren Çözüm Gezgini penceresinin ekran görüntüsü](./media/example-migration-core/autogenerated-files.png)

Yeniden derlerseniz, *yardımcı* klasörü içindeki *. cs* dosyalarından gelen birçok hata görürsünüz. Bu klasör .NET Framework sürümünde vardı, ancak eski *. csproj* içinde yer almıyor. Ancak, yeni SDK stili projeyle, proje dosyası konumu altında bulunan her kod dosyası varsayılan olarak dahil edilir. Diğer bir deyişle, yeni .NET Core projesi, dosyaları *yardımcı* klasörü içinde derlemeye çalışır. Bu klasör gerekli olmadığından, güvenli bir şekilde silebilirsiniz.

Projeyi yeniden derleyip çalıştırırsanız, ürün görüntülerini görmezsiniz. Bu sorun, artık dosyaların yolunun daha az değişmiş olması. Bu sorunu gidermek için, yolda aşağıdaki şekilde bir derinlik düzeyi eklemeniz gerekir `CatalogView.cs` :

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

kullanıcısı

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

Bu değişiklikten sonra uygulamanın, .NET Core 'da beklenildiği ve çalıştığını kontrol edebilirsiniz.

## <a name="migrating-a-wpf-application"></a>WPF uygulamasını geçirme

`Shop.ClassicWPF`Geçiş işlemini gerçekleştirmek için örnek uygulamayı kullanacağız. Aşağıdaki görüntüde geçişten önce uygulamanın ekran görüntüsü gösterilmektedir:

![Geçişten önceki örnek uygulama](./media/example-migration-core/app-before-migration.png)

Bu uygulama, ürün kataloğu bilgilerini tutmak için yerel bir SQL Server Express veritabanı kullanır. Bu veritabanına doğrudan WPF uygulamasından erişilir.

İlk olarak, *. csproj* dosyasını .NET Core uygulamaları tarafından kullanılan yeni SDK stiline güncelleştirmeniz gerekir. Windows Forms geçişte açıklanan adımların aynısını kullanacaksınız: projeyi kaldıracaksınız, *. csproj* dosyasını açacak, içeriğini güncelleştirtireceksiniz ve projeyi yeniden yükleyeceksiniz.

Bu durumda, *. csproj* dosyasının tüm içeriğini silin ve aşağıdaki kodla değiştirin:

```xml
 <Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWpf>true</UseWpf>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

Projeyi yeniden yükler ve derlerseniz, şu hatayı alırsınız:

![Visual Studio 'da derleme hatalarının ekran görüntüsü](./media/example-migration-core/wpf-compilation-error.png)

Tüm *. csproj* içeriğini sildiyseniz, eski projede mevcut bir proje başvuru belirtimini kaybettiniz. Proje başvurusunu geri eklemek için bu satırı *. csproj* dosyasına eklemeniz yeterlidir:

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

Ayrıca, **Bağımlılıklar** düğümüne sağ tıklayıp **proje başvurusu Ekle**' yi seçerek Visual Studio 'nun size yardımcı olmasına izin verebilirsiniz. Çözümdeki projeyi seçin ve **Tamam**' a tıklayın:

![EShop. SqlProvider projesi seçili olan başvuru Yöneticisi iletişim kutusunun ekran görüntüsü](./media/example-migration-core/reference-manager.png)

Eksik proje başvurusunu ekledikten sonra uygulama, .NET üzerinde beklendiği gibi derlenir ve çalışır.

>[!div class="step-by-step"]
>[Önceki](windows-migration.md) 
> [Sonraki](deploy-modern-applications.md)
