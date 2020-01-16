---
title: /CLI C++projelerini .NET Core 'a geçirme
description: /CLI projelerini .NET C++Core 'a taşıma hakkında bilgi edinin.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964932"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>Bir/CLI projesinin .NET C++Core 'a bağlantı noktası oluşturma

.NET Core 3,1 ve Visual Studio 2019 sürüm 16,4 ile başlayarak, [ C++/CLI projeleri](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) .NET Core 'u hedefleyebilir. Bu destek, Windows masaüstü uygulamalarının/CLI çalışma katmanları ile C++.NET Core 'a bağlantı noktası oluşturmanızı mümkün kılar. Bu makalede, .NET Framework ' den C++.net Core 3,1 ' ye/CLI projelerinin bağlantı noktası nasıl yapılacağı açıklanır.

## <a name="ccli-net-core-limitations"></a>C++/CLı .NET Core sınırlamaları

/CLI projelerini diğer dillere kıyasla .NET Core C++'a taşıma konusunda bazı önemli sınırlamalar vardır:

* C++.NET Core için/CLı desteği yalnızca Windows içindir.
* C++/CLı projeleri yalnızca .NET Core (veya .NET Framework) .NET Standard hedeflemiyor.
* C++/CLı projeleri, yeni SDK stili proje dosyası biçimini desteklemez. Bunun yerine, .NET Core 'u hedeflerken C++bile,/CLI projeleri mevcut vcxproj dosya biçimini kullanır.
* C++/CLı projeleri çoklu .NET platformlarını çoklu hedefleyebilir. Hem .NET Framework hem de .NET Core C++için bir/CLI projesi oluşturmanız gerekiyorsa ayrı proje dosyaları kullanın.
* .NET Core `-clr:pure` veya `-clr:safe` derlemesini desteklemez, yalnızca yeni `-clr:netcore` seçeneği (.NET Framework için `-clr` eşdeğerdir).

## <a name="port-a-ccli-project"></a>Bir C++/CLI projesi bağlantı noktası

Bir C++/CLı projesinde .NET Core 'a bağlantı kurmak için vcxproj dosyasında aşağıdaki değişiklikleri yapın. Bu geçiş adımları diğer proje türleri için gerekli adımlardan farklıdır çünkü C++/CLı projeleri SDK stili proje dosyalarını kullanmaz.

1. `<CLRSupport>true</CLRSupport>` özelliklerini `<CLRSupport>NetCore</CLRSupport>`ile değiştirin. Bu özellik genellikle yapılandırmaya özgü özellik gruplarında olduğundan, bunu birden çok yerde değiştirmeniz gerekebilir.
2. `<TargetFrameworkVersion>` özelliklerini `<TargetFramework>netcoreapp3.1</TargetFramework>`ile değiştirin.
3. .NET Framework başvurularını kaldırın (`<Reference Include="System" />`gibi). `<CLRSupport>NetCore</CLRSupport>`kullanılırken .NET Core SDK derlemelere otomatik olarak başvurulur.
4. .NET Core 'da kullanılamayan API 'Leri kaldırmak için, cpp dosyalarındaki API kullanımını güncelleştirin. /CLI C++projeleri oldukça hafif birlikte çalışma katmanları gibi olduğundan, genellikle pek çok değişiklik yapılması gerekmez. [.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) , yalnızca yönetilen ikililer gibi/CLI ikilileri tarafından C++kullanılan desteklenmeyen .NET API 'lerini belirlemek için kullanılabilir. .NET Core API 'lerle çalışmak üzere kod taşınabilirliği ve güncelleştirme projelerinin belirlenmesi için yönergeler, [kitaplık taşıma kılavuzunda](./libraries.md#determine-portability)bulunabilir.

### <a name="wpf-and-windows-forms-usage"></a>WPF ve Windows Forms kullanımı

.NET Core C++/CLI projeleri, WINDOWS Forms ve WPF API 'lerini kullanabilir. Bu Windows Masaüstü API 'Lerini kullanmak için UI kitaplıklarına açık çerçeve başvuruları eklemeniz gerekir. Windows Masaüstü API 'Leri kullanan SDK stili projeler, `Microsoft.NET.Sdk.WindowsDesktop` SDK kullanarak gerekli Framework kitaplıklarına otomatik olarak başvurur. /CLI C++projeleri SDK stili proje biçimini kullanmadığından, .NET Core 'u hedeflerken açık çerçeve başvuruları eklemesi gerekir.

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

Ayrıca, MSBuild kullanılmadan/CLI projelerini C++derlemek de mümkündür. .NET Core için doğrudan C++ *CL. exe* ve *LINK. exe*ile bir/CLI projesi oluşturmak için aşağıdaki adımları izleyin:

1. Derlenirken, `-clr:netcore` *CL. exe*' ye geçirin.
2. Gerekli .NET Core başvuru Derlemeleriyle başvur.
3. Bağlama sırasında, .NET Core uygulama ana bilgisayar dizinini `LibPath` olarak sağlayın (Bu nedenle *ijwhost. lib* ' i bulabilirsiniz).
4. *İjwhost. dll* dosyasını (.NET Core uygulama ana bilgisayar dizininden) projenin çıkış dizinine kopyalayın.
5. Yönetilen kodu çalıştıracak uygulamanın ilk bileşeni için bir [runtimeconfig. JSON](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) dosyasının bulunduğundan emin olun. Uygulamanın yönetilen bir giriş noktası varsa, bir `runtime.config` dosyası otomatik olarak oluşturulur ve silinir. Uygulamanın yerel bir giriş noktası varsa, .NET Core çalışma zamanını kullanmak için ilk C++/CLI kitaplığı için bir `runtimeconfig.json` dosyası oluşturmanız gerekir.

## <a name="known-issues"></a>Bilinen sorunlar

.NET Core ' u hedefleyen C++/CLI projeleriyle çalışırken göz atmak için birkaç bilinen sorun vardır.

* .NET Core C++/CLı projelerindeki WPF çerçeve başvurusu Şu anda sembolleri içeri aktaramayacağından ilgili bazı ekstra uyarılara neden oluyor. Bu uyarılar güvenle yoksayılabilir ve kısa bir süre önce düzeltilmelidir.
* Uygulamanın yerel bir giriş noktası varsa, önce yönetilen kodu C++yürüten/CLI kitaplığı bir [runtimeconfig. JSON](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) dosyası gerektirir. Bu yapılandırma dosyası, .NET Core çalışma zamanı başladığında kullanılır. C++/CLı projeleri henüz derleme zamanında otomatik olarak `runtimeconfig.json` dosyaları oluşturmaz, bu nedenle dosya el ile oluşturulmalıdır. Bir C++/CLI kitaplığı yönetilen bir giriş noktasından çağrılırsa, C++/CLI kitaplığı bir `runtimeconfig.json` dosyasına gerek kalmaz (giriş noktası derlemesi çalışma zamanı başlatılırken kullanılan bir tane ile aynı olduğundan). Basit bir örnek `runtimeconfig.json` dosyası aşağıda gösterilmiştir. Daha fazla bilgi için [GitHub 'daki spec](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)'e bakın.

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
