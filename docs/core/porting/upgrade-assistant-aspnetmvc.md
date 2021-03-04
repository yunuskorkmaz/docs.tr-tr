---
title: ASP.NET MVC uygulamalarını .NET 5 ' e yükseltme
description: Mevcut bir .NET Framework ASP.NET MVC uygulamasını .NET 5 ' e yükseltmek için .NET Yükseltme Yardımcısı 'nı kullanın. .NET Yükseltme Yardımcısı, bir uygulamayı .NET Framework 'tan .NET 5 ' e geçirmeye yardımcı olan bir CLı aracıdır.
author: ardalis
ms.date: 02/25/2021
ms.openlocfilehash: 0c9af9e12b78df7c4a2aaed18155f7ee9f02870d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108710"
---
# <a name="upgrade-an-aspnet-mvc-app-to-net-5-with-the-net-upgrade-assistant"></a>.NET Yükseltme Yardımcısı ile bir ASP.NET MVC uygulamasını .NET 5 ' e yükseltme

[.NET Yükseltme Yardımcısı](upgrade-assistant-overview.md) , .NET Framework ASP.NET MVC uygulamalarını .NET 5 ' e yükseltmeye yardımcı olabilecek bir komut satırı aracıdır. Bu makalede aşağıdakiler sunulmaktadır:

* .NET Framework ASP.NET MVC uygulamasında aracın nasıl çalıştırılacağını gösteren bir gösterim
* Sorun giderme ipuçları

## <a name="upgrade-net-framework-aspnet-mvc-apps"></a>.NET Framework ASP.NET MVC uygulamalarını yükseltme

Bu bölümde, yeni oluşturulan bir ASP.NET MVC uygulaması için .NET Yükseltme Yardımcısı 'Nın .NET Framework 4.6.1 ile çalıştırılması gösterilmektedir. Aracının nasıl yükleneceği hakkında daha fazla bilgi için bkz. [.NET Yükseltme Yardımcısı 'Na genel bakış](upgrade-assistant-overview.md).

### <a name="initial-demo-setup"></a>İlk tanıtım kurulumu

.NET Upgrade yardımcısını kendi .NET Framework uygulamanıza karşı çalıştırıyorsanız, bu adımı atlayabilirsiniz. Bunu yalnızca nasıl çalıştığını görmek için denemek istiyorsanız, bu adımda kullanılacak örnek bir ASP.NET MVC ve Web API (.NET Framework) projesini nasıl ayarlayabileceğinizi gösterir.

Visual Studio 'yu kullanarak .NET Framework kullanarak yeni bir ASP.NET Web uygulaması projesi oluşturun.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/new-project.png" alt-text="Visual Studio 'da yeni ASP.NET Web uygulaması projesi":::

Projeyi **Aspnetmvctest** olarak adlandırın. Projeyi **.NET Framework 4.6.1** kullanacak şekilde yapılandırın.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/configure-project.png" alt-text="Visual Studio 'da ASP.NET projesini yapılandırma":::

Sonraki iletişim kutusunda **MVC** uygulaması ' nı ve ardından **Oluştur**' u seçin.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/create-mvc-webapi.png" alt-text="Visual Studio 'da ASP.NET MVC projesi oluşturma":::

Oluşturulan projeyi ve dosyalarını, özellikle de onun proje dosyalarını gözden geçirin.

### <a name="run-upgrade-assistant"></a>Yükseltmeyi Çalıştır-Yardımcısı

Bir Terminal açın ve hedef projenin veya çözümün bulunduğu klasöre gidin. `upgrade-assistant`Hedeflemek istediğiniz projenin adını geçirerek komutunu çalıştırın (proje dosyasının yolu geçerli olduğu sürece komutu herhangi bir yerden çalıştırabilirsiniz).

```console
upgrade-assistant .\AspNetMvcTest.csproj
```

Araç çalışır ve bunu yapacağız adımların bir listesini gösterir.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/initial-run.png" alt-text=".NET Yükseltme Yardımcısı başlangıç ekranı":::

Her adım tamamlandığında, araç, kullanıcının bir sonraki adımı uygulamaya veya atlamaya izin veren bir komut kümesi sağlar, daha fazla ayrıntı için bkz. daha fazla ayrıntı, günlüğü yapılandırma veya işlemden çıkma. Araç, bir adımın hiçbir eylem gerçekleştirmediğini algılarsa, otomatik olarak bu adımı atlar ve gerçekleştirilecek eylemleri olan birine ulaşana kadar sonraki adıma devam eder. Başka seçim yapılmayacak şekilde <kbd>ENTER</kbd> tuşuna basmak sonraki adımı gerçekleştirir.

Bu örnekte, uygulanan adım her seferinde seçilir. İlk adım projeyi yedeklemedir.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/backup-project.png" alt-text=".NET Yükseltme Yardımcısı proje yedeklemesi":::

Araç, yedekleme için özel bir yol ister ve varsayılan olarak, proje yedeklemesini uzantılı aynı klasöre yerleştirir `.backup` . Aracın bir sonraki adımı, proje dosyasını SDK stiline dönüştürmelidir.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/convert-project.png" alt-text=".NET Yükseltme Yardımcısı projeyi SDK stiline Dönüştür":::

Proje biçimi güncelleştirildikten sonra, bir sonraki adım projenin TFı 'sini güncelleştirmedir.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-tfm.png" alt-text=".NET Yükseltme Yardımcısı projeyi SDK stiline Dönüştür":::

Ardından araç, projenin NuGet paketlerini güncelleştirir. Birkaç pakete güncelleştirmeler gerekiyor ve yeni bir çözümleyici paketi ekleniyor.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-nuget-packages.png" alt-text=".NET Yükseltme Yardımcısı güncelleştirme NuGet paketleri":::

Paketler güncelleştirildikten sonra, bir sonraki adım, varsa şablon dosyaları eklemektir. Araç notları, eklenmesi gereken dört beklenen şablon öğesi olduğunu ve sonra bunları eklemesini sağlar. Bunlar aşağıdaki dosyaları içerir:

- `Program.cs`
- `Startup.cs`
- `appsettings.json`
- `appsettings.Development.json`

Bu dosyalar, [uygulama başlatma](/aspnet/core/fundamentals/startup) ve [yapılandırma](/aspnet/core/fundamentals/configuration)için ASP.NET Core tarafından kullanılır.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/add-template-files.png" alt-text=".NET Yükseltme Yardımcısı şablon dosyaları Ekle":::

Ardından araç, yapılandırma dosyalarını geçirir. Araç, uygulama ayarlarını tanımlar ve desteklenmeyen yapılandırma bölümlerini devre dışı bırakır, sonra `appSettings` yapılandırma değerlerini geçirir.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config.png" alt-text=".NET Yükseltme Yardımcısı geçiş yapılandırması":::

Araç, geçiş yaparak yapılandırma dosyalarının geçişini tamamlar `system.web.webPages.razor/pages/namespaces` .

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config2.png" alt-text=".NET Yükseltme Yardımcısı geçiş yapılandırması":::

Araç, C# başvurularını yeni karşılıklarına geçirmek için bilinen düzeltmeleri uygular.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-csharp.png" alt-text=".NET Yükseltme Yardımcısı C# kaynağını güncelleştir":::

Bu son proje olduğundan, sonraki adım "sonraki projeye geç", çözümün tamamını geçirme sürecini tamamlamayı ister.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/complete-solution.png" alt-text="Çözümü tamamlayan .NET Yükseltme Yardımcısı":::

Bu işlem tamamlandıktan sonra proje dosyasını açın ve gözden geçirin. Şu şekilde statik dosyaları arayın:

```xml
  <ItemGroup>
    <Content Include="fonts\glyphicons-halflings-regular.woff2" />
    <Content Include="fonts\glyphicons-halflings-regular.woff" />
    <Content Include="fonts\glyphicons-halflings-regular.ttf" />
    <Content Include="fonts\glyphicons-halflings-regular.eot" />
    <Content Include="Content\bootstrap.min.css.map" />
    <Content Include="Content\bootstrap.css.map" />
    <Content Include="Content\bootstrap-theme.min.css.map" />
    <Content Include="Content\bootstrap-theme.css.map" />
    <Content Include="Scripts\jquery-3.4.1.slim.min.map" />
    <Content Include="Scripts\jquery-3.4.1.min.map" />
  </ItemGroup>
```

Web sunucusu tarafından sunulması gereken statik dosyalar, adlı kök düzeyindeki bir klasör içinde uygun bir klasöre taşınmalıdır `wwwroot` . Ayrıntılar için [ASP.NET Core Içindeki statik dosyalara](/aspnet/core/fundamentals/static-files?view=aspnetcore-5.0) bakın. Dosyalar taşındıktan sonra, `<Content>` Proje dosyasındaki bu dosyalara karşılık gelen öğeler silinebilir. Aslında, tüm `<Content>` öğeler ve kapsayan grupları kaldırılabilir. Ayrıca, `<PackageReference>` veya gibi bir istemci tarafı Kitaplığı `bootstrap` ve `jQuery` kaldırılması gerekir.

Varsayılan olarak, proje bir sınıf kitaplığı olarak dönüştürülür. İlk satırın `Sdk` özniteliğini olarak değiştirin ve öğesini `Microsoft.NET.Sdk.Web` `<TargetFramework>` olarak ayarlayın `net5.0` . Projeyi derleyin. Bu noktada, hata sayısı oldukça küçük olmalıdır. Yeni bir ASP.NET 4.6.1 MVC projesi taşıma sırasında, kalan hatalar klasördeki dosyalara başvurur `App_Start` :

- BundleConfig.cs
- FilterConfig.cs
- RouteConfig.cs

Bu dosyalar-ve tüm `App_Start` klasör-silinebilir. Benzer şekilde, `Global.asax` ve `Global.asax.cs` dosyaları da kaldırılabilir.

Bu noktada, kalan tek hata paketleme ile ilgilidir. [ASP.NET Core içinde paketleme ve küçültmeye yönelik çeşitli yollar](/aspnet/core/migration/mvc?view=aspnetcore-5.0#configure-bundling-and-minification)vardır. Projeniz için en mantıklı şeyi seçin.

## <a name="troubleshooting-tips"></a>Sorun giderme ipuçları

.NET Yükseltme Yardımcısı kullanılırken oluşabilecek birçok bilinen sorun vardır. Bazı durumlarda, bunlar .NET Yükseltme Yardımcısı 'Nın dahili olarak kullandığı [TRY-Convert aracı](https://github.com/dotnet/try-convert) ile ilgili sorunlardır. Bu araç daha fazla senaryoyu ele almak için sık sık güncelleştiriliyor, bu nedenle son sürümü kullandığınızdan emin olun.

- **TRY-Convert** aracının yüklü olması ve en az sürüm _0.7.212201_'e güncelleştirilmeleri gerekir.
- **TRY-Convert** aracının önceki sürümleri özel hedef veya özellik dosyalarını desteklemiyor. En son sürüme yükseltirsiniz, bu sorunları el ile ele almanız gerekebilir. Hedef proje dosyası özel hedeflere veya props dosyalarına başvurular içeriyorsa, .NET Yükseltme Yardımcısı tarafından çalıştırılmadan önce bu başvuruların dosyadan el ile silinmesi gerekebilir.

```xml
<Import Project="packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props" Condition="Exists('packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props')" />
```

[Aracın GitHub deposunda,](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) daha fazla sorun giderme ipuçları ve bilinen sorunlar vardır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Yükseltme Yardımcısı ile bir WPF uygulamasını .NET 5 ' e yükseltme](upgrade-assistant-wpf-framework.md)
- [.NET Yükseltme Yardımcısı ile bir Windows Forms uygulamasını .NET 5 ' e yükseltme](upgrade-assistant-winforms-framework.md)
- [.NET Yükseltme Yardımcısı 'na genel bakış](upgrade-assistant-overview.md)
- [.NET Yükseltme Yardımcısı GitHub deposu](https://github.com/dotnet/upgrade-assistant)
