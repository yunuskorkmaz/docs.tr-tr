---
title: Windows Forms uygulamalarını .NET 5 ' e yükseltme
description: Mevcut bir .NET Framework Windows Forms uygulamasını .NET 5 ' e yükseltmek için .NET Yükseltme Yardımcısı 'nı kullanın. .NET Yükseltme Yardımcısı, bir uygulamayı .NET Framework 'tan .NET 5 ' e geçirmeye yardımcı olan bir CLı aracıdır.
author: ardalis
ms.date: 03/08/2021
ms.openlocfilehash: 1ba80964c52cb9b6960efdebbd8d4e8ef33d63e6
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604833"
---
# <a name="upgrade-a-windows-forms-app-to-net-5-with-the-net-upgrade-assistant"></a>.NET Yükseltme Yardımcısı ile bir Windows Forms uygulamasını .NET 5 ' e yükseltme

[.NET Yükseltme Yardımcısı](upgrade-assistant-overview.md) , .NET Framework Windows Forms (WinForms) uygulamalarını .NET 5 ' e yükseltmeye yardımcı olabilecek bir komut satırı aracıdır. Bu makalede aşağıdakiler sunulmaktadır:

- Aracının .NET Framework Windows Forms uygulamasına karşı nasıl çalıştırılacağını gösteren bir gösteri
- Sorun giderme ipuçları

## <a name="upgrade-net-framework-windows-forms-apps"></a>Uygulamaları Windows Forms .NET Framework yükseltme

Bu bölümde, .NET Framework 4.6.1 hedefleyen yeni oluşturulan Windows Forms uygulama için .NET Yükseltme Yardımcısı 'Nın çalıştırılması gösterilmektedir. Aracının nasıl yükleneceği hakkında daha fazla bilgi için bkz. [.NET Yükseltme Yardımcısı 'Na genel bakış](upgrade-assistant-overview.md).

### <a name="initial-demo-setup"></a>İlk tanıtım kurulumu

.NET Upgrade yardımcısını kendi .NET Framework uygulamanıza karşı çalıştırıyorsanız, bu adımı atlayabilirsiniz. Yalnızca nasıl çalıştığını görmek için denemek istiyorsanız, bu adım bir örnek .NET Windows Forms projesini kullanmak üzere nasıl ayarlayabileceğinizi gösterir.

Visual Studio 'yu kullanarak .NET Framework kullanarak yeni bir Windows Forms projesi oluşturun.

:::image type="content" source="media/upgrade-assistant-winforms-framework/vs-new-project-winforms.png" alt-text="Visual Studio 'da yeni Windows Forms projesi":::

Projeyi **Winformstest** olarak adlandırın. Projeyi **.NET Framework 4.6.1** kullanacak şekilde yapılandırın.

:::image type="content" source="media/upgrade-assistant-winforms-framework/vs-configure-project-winforms.png" alt-text="Visual Studio 'da Windows Forms projesi yapılandırma":::

Oluşturulan projeyi ve dosyalarını, özellikle de onun proje dosyalarını gözden geçirin.

### <a name="run-upgrade-assistant"></a>Yükseltmeyi Çalıştır-Yardımcısı

Bir Terminal açın ve hedef projenin veya çözümün bulunduğu klasöre gidin. `upgrade-assistant`Hedeflemek istediğiniz projenin adını geçirerek komutunu çalıştırın (proje dosyasının yolu geçerli olduğu sürece komutu herhangi bir yerden çalıştırabilirsiniz).

```console
upgrade-assistant .\WinformsTest.csproj
```

Araç çalışır ve bunu yapacağız adımların bir listesini gösterir.

:::image type="content" source="media/upgrade-assistant-winforms-framework/step1.png" alt-text=".NET Yükseltme Yardımcısı başlangıç ekranı":::

Her adım tamamlandığında, araç, kullanıcının bir sonraki adımı uygulamaya veya atlamaya izin veren bir komut kümesi sağlar, daha fazla ayrıntı için bkz. daha fazla ayrıntı, günlüğü yapılandırma veya işlemden çıkma. Araç, bir adımın hiçbir eylem gerçekleştirmediğini algılarsa, bu adımı otomatik olarak atlar ve gerçekleştirilecek eylemlere sahip olana kadar bir sonraki adıma devam eder. Başka seçim yapılmayacak şekilde ENTER tuşuna basmak sonraki adımı gerçekleştirir.

Bu örnekte, uygulanan adım her seferinde seçilir. İlk adım projeyi yedeklemedir.

:::image type="content" source="media/upgrade-assistant-winforms-framework/backup-project.png" alt-text=".NET Yükseltme Yardımcısı proje yedeklemesi":::

Araç, yedekleme için özel bir yol ister ve varsayılan olarak, proje yedeklemesini uzantılı aynı klasöre yerleştirir `.backup` . Aracın bir sonraki adımı, proje dosyasını SDK stiline dönüştürmelidir.

:::image type="content" source="media/upgrade-assistant-winforms-framework/convert-project.png" alt-text=".NET Yükseltme Yardımcısı projeyi SDK stiline Dönüştür":::

Proje biçimi güncelleştirildikten sonra, bir sonraki adım projenin TFı 'sini güncelleştirmedir.

:::image type="content" source="media/upgrade-assistant-winforms-framework/update-tfm.png" alt-text=".NET Yükseltme Yardımcısı güncelleştirme tfd":::

Ardından araç, projenin NuGet paketlerini güncelleştirir.

:::image type="content" source="media/upgrade-assistant-winforms-framework/update-nuget-packages.png" alt-text=".NET Yükseltme Yardımcısı güncelleştirme NuGet paketleri":::

Paketler güncelleştirildikten sonra, bir sonraki adım, varsa şablon dosyaları eklemektir. Bu durumda, eklenmesi gereken hiçbir şablon dosyası yoktur. Bu adım, uygulama yapılandırma dosyalarını ve güncelleştirme C# kaynağını aşağıda gösterildiği gibi düzeltmeleri uygulamak için devam ettirir ve geçirir. Bu proje herhangi bir yapılandırma dosyası veya kaynak kodu değişikliğine ihtiyaç duymadı, bu nedenle bu adımlar otomatik olarak devam eder.

:::image type="content" source="media/upgrade-assistant-winforms-framework/add-template-files.png" alt-text=".NET Yükseltme Yardımcısı şablon dosyaları Ekle ve yapılandırmayı geçir":::

Bu son proje olduğundan, sonraki adım "sonraki projeye geç", çözümün tamamını geçirme sürecini tamamlamayı ister.

:::image type="content" source="media/upgrade-assistant-winforms-framework/complete-solution.png" alt-text="Çözümü tamamlayan .NET Yükseltme Yardımcısı":::

Bu işlem tamamlandıktan sonra, geçirilen Windows Forms projesi şuna benzer şekilde görünür:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net5.0-windows</TargetFramework>
    <OutputType>WinExe</OutputType>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
    <PackageReference Include="Microsoft.DotNet.UpgradeAssistant.Extensions.Default.Analyzers" Version="0.2.211730">
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="5.0.2" />
  </ItemGroup>
</Project>
```

.NET Yükseltme Yardımcısı 'Nın Ayrıca, yükseltme işlemine devam eden bir projeye çözümleyiciler eklediğine dikkat edin.

## <a name="troubleshooting-tips"></a>Sorun giderme ipuçları

.NET Yükseltme Yardımcısı kullanılırken oluşabilecek birçok bilinen sorun vardır. Bazı durumlarda, bunlar .NET Yükseltme Yardımcısı 'Nın dahili olarak kullandığı [TRY-Convert aracı](https://github.com/dotnet/try-convert) ile ilgili sorunlardır. Bu araç daha fazla senaryoyu ele almak için sık sık güncelleştiriliyor, bu nedenle son sürümü kullandığınızdan emin olun.

- **TRY-Convert** aracının yüklü olması ve en az sürüm _0.7.212201_'e güncelleştirilmeleri gerekir.
- **TRY-Convert** aracının önceki sürümleri özel hedef veya özellik dosyalarını desteklemiyor. En son sürüme yükseltirsiniz, bu sorunları el ile ele almanız gerekebilir. Hedef proje dosyası özel hedeflere veya props dosyalarına başvurular içeriyorsa, .NET Yükseltme Yardımcısı tarafından çalıştırılmadan önce bu başvuruların dosyadan el ile silinmesi gerekebilir.

[Aracın GitHub deposunda](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) ek sorun giderme ipuçları ve bilinen sorunlar vardır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Yükseltme Yardımcısı ile bir WPF uygulamasını .NET 5 ' e yükseltme](upgrade-assistant-wpf-framework.md)
- [.NET Yükseltme Yardımcısı ile bir ASP.NET MVC uygulamasını .NET 5 ' e yükseltme](upgrade-assistant-aspnetmvc.md)
- [.NET Yükseltme Yardımcısı 'na genel bakış](upgrade-assistant-overview.md)
- [.NET Yükseltme Yardımcısı GitHub deposu](https://github.com/dotnet/upgrade-assistant)
