---
title: C++/CLı projelerini .NET Core 'a geçirme
description: C++/CLı projelerini .NET Core 'a taşıma hakkında bilgi edinin.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: 1194e1ce03e5b86052d7e2584aa5c15acd01874b
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873698"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>C++/CLı projesinde .NET Core 'a bağlantı noktası oluşturma

.NET Core 3,1 ve Visual Studio 2019 sürüm 16,4 ile başlayarak, [C++/CLI projeleri](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) .NET Core 'u hedefleyebilir. Bu destek, Windows masaüstü uygulamalarının C++/CLı birlikte çalışma katmanları ile .NET Core 'a bağlantı noktası kullanmasını mümkün kılar. Bu makalede, C++/CLı projelerinin .NET Framework 'dan .NET Core 3,1 ' e nasıl bağlantı kurulacağı açıklanmaktadır.

## <a name="ccli-net-core-limitations"></a>C++/CLı .NET Core sınırlamaları

C++/CLı projelerinin diğer dillere kıyasla .NET Core 'a taşıma açısından bazı önemli sınırlamalar vardır:

* .NET Core için C++/CLı desteği yalnızca Windows içindir.
* C++/CLı projeleri yalnızca .NET Core (veya .NET Framework) .NET Standard hedeflemiyor.
* C++/CLı projeleri, yeni SDK stili proje dosyası biçimini desteklemez. Bunun yerine, .NET Core hedeflenirken bile, C++/CLı projeleri mevcut vcxproj dosya biçimini kullanır.
* C++/CLı projeleri çoklu .NET platformlarını çoklu hedefleyebilir. Hem .NET Framework hem de .NET Core için bir C++/CLı projesi oluşturmanız gerekiyorsa ayrı proje dosyaları kullanın.
* .NET Core `-clr:pure` `-clr:safe` , yalnızca yeni `-clr:netcore` seçeneği (.NET Framework için eşdeğer) desteklemez veya derlemesini desteklemez `-clr` .

## <a name="port-a-ccli-project"></a>Bir C++/CLı projesi bağlantı noktası

C++/CLı projesinde .NET Core 'a bağlantı kurmak için, vcxproj dosyasında aşağıdaki değişiklikleri yapın. C++/CLı projeleri SDK stili proje dosyalarını kullanmadığından, bu geçiş adımları diğer proje türleri için gereken adımlardan farklıdır.

1. `<CLRSupport>true</CLRSupport>`Özellikleri ile değiştirin `<CLRSupport>NetCore</CLRSupport>` . Bu özellik genellikle yapılandırmaya özgü özellik gruplarında olduğundan, bunu birden çok yerde değiştirmeniz gerekebilir.
2. `<TargetFrameworkVersion>`Özellikleri ile değiştirin `<TargetFramework>netcoreapp3.1</TargetFramework>` .
3. .NET Framework başvurularını kaldırın (gibi `<Reference Include="System" />` ). .NET Core SDK derlemeler kullanılırken otomatik olarak başvurulur `<CLRSupport>NetCore</CLRSupport>` .
4. .NET Core 'da kullanılamayan API 'Leri kaldırmak için, cpp dosyalarındaki API kullanımını güncelleştirin. C++/CLı projeleri oldukça hafif birlikte çalışma katmanları olarak eğiltiğinden, genellikle pek çok değişiklik yapılması gerekmez. [.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) , C++/CLI ikili dosyaları tarafından yalnızca yönetilen ikililer gibi kullanılan desteklenmeyen .NET API 'lerini belirlemek için kullanılabilir. .NET Core API 'lerle çalışmak üzere kod taşınabilirliği ve güncelleştirme projelerinin belirlenmesi için yönergeler, [kitaplık taşıma kılavuzunda](./libraries.md#determine-portability)bulunabilir.

### <a name="wpf-and-windows-forms-usage"></a>WPF ve Windows Forms kullanımı

.NET Core C++/CLı projeleri, Windows Forms ve WPF API 'Lerini kullanabilir. Bu Windows Masaüstü API 'Lerini kullanmak için UI kitaplıklarına açık çerçeve başvuruları eklemeniz gerekir. Windows Masaüstü API 'Leri kullanan SDK stili projeler, SDK kullanarak gerekli Framework kitaplıklarına otomatik olarak başvurur `Microsoft.NET.Sdk.WindowsDesktop` . C++/CLı projeleri SDK stili proje biçimini kullanmadığından, .NET Core 'u hedeflerken açık çerçeve başvuruları eklemesi gerekir.

Windows Forms API 'Lerini kullanmak için, bu başvuruyu vcxproj dosyasına ekleyin:

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

WPF API 'Lerini kullanmak için, bu başvuruyu vcxproj dosyasına ekleyin:

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

Hem Windows Forms hem de WPF API 'Lerini kullanmak için, bu başvuruyu vcxproj dosyasına ekleyin:

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

Şu anda, Visual Studio 'nun başvuru Yöneticisi 'ni kullanarak bu başvuruları eklemek mümkün değildir. Bunun yerine, proje dosyasını el ile güncelleştirin. Bu güncelleştirme, projeyi kaldırarak ve ardından proje dosyasını düzenleyerek Visual Studio 'da yapılabilir. VS Code gibi başka bir düzenleyiciyi de kullanabilirsiniz.

## <a name="build-without-msbuild"></a>MSBuild olmadan derleme

MSBuild kullanmadan C++/CLı projelerini derlemek de mümkündür. Doğrudan *cl.exe* ve *link.exe* ile .NET Core için bir C++/CLI projesi oluşturmak için bu adımları izleyin:

1. Derlerken `-clr:netcore` *cl.exe* geçirin.
2. Gerekli .NET Core başvuru Derlemeleriyle başvur.
3. Bağlama sırasında, .NET Core uygulama ana bilgisayar dizinini `LibPath` ( *ijwhost. lib* 'nin bulunabilmesi için) olarak sağlayın.
4. *ijwhost.dll* (.NET Core uygulama ana bilgisayar dizininden) projenin çıkış dizinine kopyalayın.
5. Yönetilen kodu çalıştıracak uygulamanın ilk bileşeni için dosya [runtimeconfig.js](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md) bulunduğundan emin olun. Uygulamanın yönetilen bir giriş noktası varsa, bir `runtime.config` dosya otomatik olarak oluşturulup kopyalanacaktır. Uygulamanın yerel bir giriş noktası varsa, `runtimeconfig.json` .NET Core çalışma zamanını kullanmak için Ilk C++/CLI kitaplığı için bir dosya oluşturmanız gerekir.

## <a name="known-issues"></a>Bilinen sorunlar

.NET Core ' u hedefleyen C++/CLı projeleriyle çalışırken göz atmak için birkaç bilinen sorun vardır.

* .NET Core C++/CLı projelerinde bir WPF çerçeve başvurusu Şu anda sembolleri içeri aktaramayacağından ilgili bazı ekstra uyarılara neden oluyor. Bu uyarılar güvenle yoksayılabilir ve kısa bir süre önce düzeltilmelidir.
* Uygulamanın yerel bir giriş noktası varsa, önce yönetilen kodu yürüten C++/CLı kitaplığı, dosyasında bir [runtimeconfig.js](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md) gerekir. Bu yapılandırma dosyası, .NET Core çalışma zamanı başladığında kullanılır. C++/CLı projeleri `runtimeconfig.json` henüz derleme zamanında otomatik olarak dosya oluşturmaz, bu nedenle dosya el ile oluşturulmalıdır. Bir C++/CLı kitaplığı yönetilen bir giriş noktasından çağrılırsa, C++/CLı kitaplığı bir dosyaya gerek kalmaz `runtimeconfig.json` (giriş noktası derlemesi, çalışma zamanı başlatılırken kullanılan bir tane ile aynı olduğundan). Basit bir örnek `runtimeconfig.json` dosya aşağıda gösterilmiştir. Daha fazla bilgi için [GitHub 'daki spec](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md)'e bakın.

    ```json
    {
          "runtimeOptions": {
             "tfm": "netcoreapp3.1",
             "framework": {
                "name": "Microsoft.NETCore.App",
                "version": "3.1.0"
             }
          }
    }
    ```
