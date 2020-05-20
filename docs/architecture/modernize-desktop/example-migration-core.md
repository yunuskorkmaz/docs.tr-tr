---
title: .NET Core 3.1’e geçiş örneği
description: .NET Framework Hedefleme örnek uygulamaların .NET Core 3,1 ' ye nasıl geçirileceği gösteriliyor.
ms.date: 05/12/2020
ms.openlocfilehash: ef8a0c24ec81a21eb89411ed4c9a543d4d70d89f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423385"
---
# <a name="example-of-migrating-to-net-core-31"></a>.NET Core 3.1’e geçiş örneği

Bu bölümde, var olan uygulamanızın .NET Framework .NET Core 'a geçişini gerçekleştirmenize yardımcı olacak pratik yönergeler sunuyoruz.

İzleyebileceğiniz bir işlem ve her adımda göz önünde bulundurmanız gereken en önemli noktalar sunuyoruz.

Ardından, hem WinForms hem de WPF sürümlerinden örnek bir masaüstü uygulaması için adım adım geçiş sürecini belgeliyoruz.

## <a name="migration-process-overview"></a>Geçiş işlemine genel bakış

Geçiş işlemi dört sıralı adımdan oluşur:

1. **Hazırlık**: projenin, nelerin ilerimize dair bir fikir sahibi olması için bağımlılıkları anlayın. Bu adımda, geçerli projeyi geçiş için başlangıç noktasını basitleştiren bir duruma getirin.

2. **Proje dosyasını geçirme:** .NET Core PROJELERI yeni SDK stili proje biçimini kullanır. Bu biçimle yeni bir proje dosyası oluşturun veya SDK stilini kullanmak için sahip olduğunuz güncelleştirmeyi güncelleştirin.

3. **Kodu ve derlemeyi onarma:** .NET Core 'da, .NET Framework ve .NET Core arasındaki API düzeyi farklılıklar hakkında kod oluşturun. Gerekirse, üçüncü taraf paketleri .NET Core 'u destekleyen olanlarla güncelleştirin.

4. **Çalıştır ve test et:** Çalışma zamanına kadar gösterilmeyebilir farklılıklar olabilir. Bu nedenle, uygulamayı çalıştırmayı unutmayın ve her şeyin beklendiği gibi çalıştığından test edin.

### <a name="preparation"></a>Hazırlık

#### <a name="migrate-packagesconfig-file"></a>Packages. config dosyasını geçirme

.NET Framework bir uygulamada, dış paketlere yapılan tüm başvurular *Packages. config* dosyasında belirtilir. .NET Core 'da, artık *Packages. config* dosyasını kullanma gereksinimi yoktur. Bunun yerine, uygulamanızın NuGet paketlerini belirtmek için proje dosyasının içindeki [Packagereference](../../core/project-sdk/msbuild-props.md#packagereference) özelliğini kullanın.

Bu nedenle, bir biçimden diğerine geçiş yapmanız gerekir. Bu güncelleştirmeyi, *Packages. config* dosyasında bulunan bağımlılıkları alarak ve bunları biçimiyle proje dosyasına geçirerek el ile yapabilirsiniz `PackageReference` . Ya da, Visual Studio 'Nun bu işi sizin yerinize yapmasına izin verebilirsiniz: *Packages. config* dosyasına sağ tıklayıp **Packages. config ' i packagereference** ' a Geçir seçeneğini belirleyin.

#### <a name="verify-every-dependency-compatibility-in-net-core"></a>.NET Core 'da her bağımlılık uyumluluğunu doğrulama

Paket başvurularını geçirdikten sonra her bir başvuruyu uyumluluk için denetlemeniz gerekir. Uygulamanızın [NuGet.org](https://www.nuget.org/)üzerinde kullandığı her bir NuGet paketinin bağımlılıklarını inceleyebilirsiniz. Pakette .NET Standard bağımlılıklar varsa, .NET Core 3,1 tüm .NET Standard sürümlerini [desteklediğinden](../../standard/net-standard.md#net-implementation-support) .NET Core üzerinde çalışacaktır. Aşağıdaki görüntüde, paket için bağımlılıklar gösterilmektedir `Castle.Windsor` :

![Role. Wın_sor paketi için NuGet bağımlılıklarının ekran görüntüsü](./media/example-migration-core/nuget-dependencies.png)

Paket uyumluluğunu denetlemek için, <http://fuget.org> sürümler ve Bağımlılıklar hakkında daha ayrıntılı bilgi sunan aracı kullanabilirsiniz.

Proje, .NET Core 'u desteklemeyen eski paket sürümlerine başvuruyor, ancak bunu destekleyen daha yeni sürümleri bulabilirsiniz. Bu nedenle, paketleri daha yeni sürümlere güncelleştirmek genellikle iyi bir öneriydi. Ancak, paket sürümünün güncelleştirilmesi, kodunuzun güncelleştirilmesini zorlayan bazı önemli değişiklikler getirebileceğini göz önünde bulundurmanız gerekir.

Uyumlu bir sürüm bulamazsanız ne olur? Bu son değişiklikler nedeniyle bir paketin sürümünü güncelleştirmek istemiyorsanız ne yapmanız gerekir? Endişelenmeyin çünkü bir .NET Core uygulamasından .NET Framework paketlerine bağlı olabilir. Dış paket .NET Core 'da kullanılamayan bir API 'YI çağırırsa, çalışma zamanı hatalarına neden olabileceğinden, bunu kapsamlı olarak sınamayı unutmayın. Bu, güncelleştirileymeyen eski bir paket kullanırken ve yalnızca .NET Core üzerinde çalışacak şekilde yeniden hedefleyecekseniz için harika bir yoldur.

#### <a name="check-for-api-compatibility"></a>API uyumluluğunu denetle

.NET Framework ve .NET Core 'daki API yüzeyi benzer ancak özdeş olduğundan, .NET Core 'da hangi API 'Lerin kullanılabilir olduğunu ve hangilerinin olmadığını denetlemeniz gerekir. .NET Core üzerinde mevcut olmayan kullanılan API 'Leri kullanarak .NET taşınabilirlik Çözümleyicisi aracını kullanabilirsiniz. Uygulamanızın ikili düzeyine bakar, çağrılan tüm API 'Leri ayıklar ve hedef çerçeveinizdeki hangi API 'Lerin kullanılabilir olduğunu listeler (Bu durumda .NET Core 3,1).

Bu araçla ilgili daha fazla bilgiyi şurada bulabilirsiniz:

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

Bu aracın ilginç bir yönü, yalnızca kendi kodunuzla gelen farkları değil, farklı bir şekilde değişiklik yapamazsınız. Bu paketlerin çoğunu .NET Core ile çalışacak şekilde güncelleştirdiğinizden emin olun.

### <a name="migrate-project-file"></a>Proje dosyasını geçir

#### <a name="create-the-new-net-core-project"></a>Yeni .NET Core projesi oluşturma

Çoğu durumda, mevcut projenizi yeni .NET Core biçimiyle güncellemek isteyeceksiniz. Bununla birlikte, eskisini koruyarak da yeni bir proje oluşturabilirsiniz. Eski projeyi güncelleştirmeden asıl dezavantajı, tasarımcı desteğini kaybetmeniz ve sizin için önemli olabilir. Tasarımcıyı kullanmaya devam etmek istiyorsanız, eski bir .NET Core projesi oluşturup eskisiyle ve paylaşma varlıklarıyla paralel olarak oluşturmanız gerekir. Tasarımcıda Kullanıcı arabirimi öğelerini değiştirmeniz gerekiyorsa, bunu yapmak için eski projeye geçiş yapabilirsiniz. Varlıklar bağlı olduğundan, .NET Core projesinde de güncelleştirilecektir.

.NET Core için [SDK stili proje](../../core/project-sdk/msbuild-props.md) , .NET Framework proje biçiminden daha basittir. Daha önce bahsedilen `PackageReference` girdilerden ayrı olarak, çok daha fazlasını yapmanıza gerek kalmaz. Yeni proje biçimi, [by default](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects) `.cs` `.xaml` dosyaları proje dosyasına açıkça dahil etmek zorunda kalmadan, ve gibi belirli dosya uzantılarını varsayılan olarak içerir.

#### <a name="assemblyinfo-considerations"></a>Assembly.info konuları

Öznitelikler .NET Core projelerinde otomatik olarak oluşturulur. Proje bir *AssemblyInfo.cs* dosyası içeriyorsa, tanımlar çoğaltılır ve bu da derleme çakışmalarına neden olur. Eski *AssemblyInfo.cs* dosyasını silebilir veya aşağıdaki girişi .NET Core proje dosyasına ekleyerek, oto oluşturmayı devre dışı bırakabilirsiniz:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a>Kaynaklar

Gömülü kaynaklar otomatik olarak dahil edilir ancak kaynaklar değildir, bu nedenle kaynakları yeni proje dosyasına geçirmeniz gerekir.

#### <a name="package-references"></a>Paket başvuruları

**Packages. config 'ı PackageReference seçeneğine geçir** seçeneğiyle, dış paket başvurularınızı daha önce belirtildiği gibi yeni biçime kolayca taşıyabilirsiniz.

#### <a name="update-package-references"></a>Paket başvurularını Güncelleştir

Bulduğunuz paketlerin sürümlerini, önceki bölümde gösterildiği gibi güncelleştirin.

### <a name="fix-the-code-and-build"></a>Kodu ve derlemeyi düzeltir

#### <a name="microsoftwindowscompatibility"></a>Microsoft. Windows. Compatibility

Uygulamanız, kayıt defteri, ACL 'Ler veya WCF gibi .NET Core üzerinde kullanılamayan API 'Lere bağımlıysa, `Microsoft.Windows.Compatibility` Bu Windows 'a özgü API 'leri eklemek için pakete bir başvuru eklemeniz gerekir. Bunlar .NET Core üzerinde çalışır, ancak platformlar arası olmadıkları sürece dahil edilmez.

<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>Kodunuzla uyumlu olmayan API 'leri tanımanıza yardımcı olan API Çözümleyicisi () adlı bir araç vardır.

#### <a name="use-if-directives"></a>\#IF yönergeleri kullanın

.NET Framework ve .NET Core 'u hedeflerken farklı yürütme yollarına ihtiyacınız varsa, derleme sabitleri kullanmanız gerekir. \#Aynı kod tabanını her iki hedef için de tutmak üzere kodunuza bazı if yönergeleri ekleyin.

#### <a name="technologies-not-available-on-net-core"></a>.NET Core 'da sunulan teknolojiler

Bazı teknolojiler .NET Core üzerinde kullanılamaz, örneğin:

* Uygulama
* Uzaktan iletişim
* Kod Erişimi Güvenliği
* WCF sunucusu
* Windows Iş akışı

Bu nedenle, bunları uygulamanızda kullanıyorsanız bu teknolojilerin yerini bulmanız gerekir. Daha fazla bilgi için bkz. [.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../../core/porting/net-framework-tech-unavailable.md) makalesi.

#### <a name="regenerate-autogenerated-clients"></a>Otomatik olarak oluşturulan istemcileri yeniden üret

Uygulamanız bir WCF istemcisi gibi otomatik olarak oluşturulmuş kod kullanıyorsa, .NET Core 'u hedeflemek için bu kodu yeniden oluşturmanız gerekebilir. Bazen, bazı eksik başvuruları, varsayılan .NET Core derlemeleri kümesinin bir parçası olarak eklendiklerinden da bulabilirsiniz. Gibi bir araç kullanarak <https://apisof.net/> , eksik başvurunun bulunduğu derlemeyi kolayca bulabilir ve NuGet 'ten ekleyebilirsiniz.

#### <a name="rolling-back-package-versions"></a>Paket sürümleri geri alınıyor

Genel bir kural olarak, .NET Core ile uyumlu olmak için her tek paket sürümünü daha iyi güncelleştirdiniz. Bununla birlikte, bir derlemenin güncelleştirilmiş ve uyumlu bir sürümünü hedefleme için yalnızca ödeme yapmayın. Değişiklik maliyeti kabul edilebilir değilse, paket sürümlerinin .NET Framework ' de kullandıklarınızı tutarak geri almasını düşünebilirsiniz. .NET Core hedeflenmese de, desteklenmeyen bazı API 'Ler çağrıdıkça iyi çalışmalıdır.

### <a name="run-and-test"></a>Çalıştırma ve test etme

Uygulamanızın hatasız olarak oluşturulmasını sağlayarak, her işlevselliği test ederek geçişin son adımını başlatabilirsiniz.

Bu son adımda, uygulamanızın karmaşıklığına ve kullanmakta olduğunuz bağımlılıklara ve API 'Lere bağlı olarak çeşitli farklı sorunlar bulabilirsiniz.

Örneğin, yapılandırma dosyalarını (*app. config*) kullanıyorsanız, çalışma zamanında yapılandırma bölümleri gibi bazı hatalar bulabilirsiniz. `Microsoft.Extensions.Configuration`NuGet paketinin kullanılması bu hatayı düzeltir.

Hatalar için bir diğer neden, `BeginInvoke` `EndInvoke` .NET Core üzerinde desteklenmediğinden ve yöntemlerinin kullanılmasının bir nedenidir. .NET Core üzerinde mevcut olmayan bir uzaktan Iletişim bağımlılığı olduğundan, .NET Core üzerinde desteklenmez. Bu sorunu gidermek için `await` anahtar sözcüğünü (kullanılabilir olduğunda) veya yöntemini kullanmayı deneyin <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> .

Kodunuzda .NET Core ile çalışma zamanında sorunlara neden olabilecek API 'Leri ve kod düzenlerini tanımlamanızı sağlamak için uyumluluk Çözümleyicileri ' ni kullanabilirsiniz. <http://github.com/dotnet/platform-compat>' A gidin ve projenizde .NET API Çözümleyicisi ' ni kullanın.

## <a name="migrating-a-windows-forms-application"></a>Windows Forms uygulamasını geçirme

Bir Windows Forms uygulamasının tüm geçiş sürecini göstermek için, ' de bulunan eShop örnek uygulamasını geçirmeyi seçtik <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> . Geçişin tüm sonucunu ' de bulabilirsiniz <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .

Bu uygulama bir ürün kataloğu gösterir ve kullanıcının ürünlere gezinme, filtre uygulama ve arama yapmasına izin verir. Bir mimari görünümünden uygulama, bir arka uç veritabanına façlade görevi gören bir dış WCF hizmetini kullanır.

Ana uygulama penceresini aşağıdaki resimde görebilirsiniz:

![Ana uygulama penceresi](./media/example-migration-core/main-application-window.png)

*. Csproj* proje dosyasını açarsanız şuna benzer bir şey görebilirsiniz:

![CSPROJ dosya içeriğinin ekran görüntüsü](./media/example-migration-core/csproj-file.png)

Daha önce belirtildiği gibi, .NET Core projesi daha kompakt bir stile sahiptir ve proje yapısını yeni .NET Core SDK stiline geçirmeniz gerekir.

Çözüm Gezgini, Windows Forms projesine sağ tıklayın ve **Proje düzenlemeyi kaldır**' ı seçin  >  **Edit**.

Artık. csproj dosyasını güncelleştirebilirsiniz. İçeriğin tamamını silecek ve aşağıdaki kodla değiştirilecek:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWindowsForms>true</UseWindowsForms>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

Projeyi kaydedin ve yeniden yükleyin. Artık proje dosyasını güncellemeyi tamamladınız ve proje .NET çekirdeğini hedefliyor.

Projeyi bu noktada derlerseniz, WCF istemci başvurusuyla ilgili bazı hatalar bulacaksınız. Bu kod otomatik olarak oluşturulduğundan, .NET Core 'u hedeflemek için yeniden oluşturmanız gerekir.

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
2. *ConnectedService. JSON*: hizmete bağlanmak için yapılandırma parametreleri.
3. *Reference.cs*: gerçek WCF istemci kodu.

![Otomatik olarak oluşturulan üç dosyayı içeren Çözüm Gezgini penceresinin ekran görüntüsü](./media/example-migration-core/autogenerated-files.png)

Yeniden derlerseniz, *yardımcı* klasörü içindeki *. cs* dosyalarından gelen birçok hata görürsünüz. Bu klasör .NET Framework sürümünde vardı, ancak eski *. csproj*içinde yer almıyor. Ancak, yeni SDK stili projeyle, proje dosyası konumu altında bulunan her kod dosyası varsayılan olarak dahil edilir. Diğer bir deyişle, yeni .NET Core projesi, dosyaları *yardımcı* klasörü içinde derlemeye çalışır. Bu klasör gerekli olmadığından, güvenli bir şekilde silebilirsiniz.

Projeyi yeniden derleyip çalıştırırsanız, ürün görüntülerini görmezsiniz. Bu sorun, artık dosyaların yolunun daha az değişmiş olması. Bu sorunu gidermek için, yolda aşağıdaki şekilde bir derinlik düzeyi eklemeniz gerekir `CatalogView.cs` :

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

-

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
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWPF>true</UseWPF>
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

Eksik proje başvurusunu ekledikten sonra uygulama, .NET Core 'da beklendiği gibi derlenir ve çalışır.

>[!div class="step-by-step"]
>[Önceki](windows-migration.md) 
> [Sonraki](deploy-modern-applications.md)
