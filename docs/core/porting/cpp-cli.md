---
title: C++/CLI projelerini .NET Core'a geçirme
description: C++/CLI projelerini .NET Core'a taşıma hakkında bilgi edinin.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964932"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>C++/CLI projesini .NET Core'a taşıma

.NET Core 3.1 ve Visual Studio 2019 sürüm 16.4 ile başlayarak [C++/CLI projeleri](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) .NET Core'u hedefleyebilir. Bu destek, Windows masaüstü uygulamalarını C++/CLI interop katmanlarıile .NET Core'a taşımayı mümkün kılar. Bu makalede, C++/CLI projelerinin .NET Framework'den .NET Core 3.1'e nasıl bağlantı dalanıncaaçıklanmaktadır.

## <a name="ccli-net-core-limitations"></a>C++/CLI .NET Çekirdek sınırlamaları

C++/CLI projelerini .NET Core'a taşımanın diğer dillere göre bazı önemli sınırlamaları vardır:

* .NET Core için C++/CLI desteği yalnızca Windows'dur.
* C++/CLI projeleri .NET Standard'ı, yalnızca .NET Core'u (veya .NET Framework)'i hedef alamaz.
* C++/CLI projeleri yeni SDK tarzı proje dosya biçimini desteklemez. Bunun yerine, .NET Core hedeflediğinizde bile, C++/CLI projeleri varolan vcxproj dosya biçimini kullanır.
* C++/CLI projeleri birden çok .NET platformlarını birden fazla hedefleyemez. Hem .NET Framework hem de .NET Core için c++/CLI projesi oluşturmanız gerekiyorsa, ayrı proje dosyaları kullanın.
* .NET Core `-clr:pure` destek lemiyor `-clr:safe` veya derleme, `-clr:netcore` sadece yeni seçenek `-clr` (.NET Framework için eşdeğerdir).

## <a name="port-a-ccli-project"></a>Bir C++/CLI projesini portolarak

C++/CLI projesini .NET Core'a taşımak için vcxproj dosyasında aşağıdaki değişiklikleri yapın. C++/CLI projeleri SDK tarzı proje dosyalarını kullanmadığından, bu geçiş adımları diğer proje türleri için gereken adımlardan farklıdır.

1. Özellikleri `<CLRSupport>true</CLRSupport>` ' `<CLRSupport>NetCore</CLRSupport>`ile değiştirin Bu özellik genellikle yapılandırmaya özgü özellik gruplarında olduğundan, birden çok yerde değiştirmeniz gerekebilir.
2. Özellikleri `<TargetFrameworkVersion>` ' `<TargetFramework>netcoreapp3.1</TargetFramework>`ile değiştirin
3. .NET Framework başvurularını `<Reference Include="System" />`kaldırın (beğenin). .NET Core SDK derlemeleri kullanırken `<CLRSupport>NetCore</CLRSupport>`otomatik olarak başvurulur.
4. .NET Core'da kullanılamayan API'leri kaldırmak için gerektiğinde cpp dosyalarındaki API kullanımını güncelleştirin. C++/CLI projeleri oldukça ince interop katmanları olma eğiliminde olduğundan, genellikle çok fazla değişiklik gerekmez. [.NET Taşınabilirlik Çözümleyicisi,](../../standard/analyzers/portability-analyzer.md) c++/CLI ikilileri tarafından kullanılan desteklenmeyen .NET API'lerini tamamen yönetilen ikili lerde olduğu gibi tanımlamak için kullanılabilir. Kod taşınabilirliğini belirleme ve .NET Core API'larla çalışacak projeleri güncelleştirme [yönergeleri kitaplık taşıma kılavuzunda](./libraries.md#determine-portability)mevcuttur.

### <a name="wpf-and-windows-forms-usage"></a>WPF ve Windows Formlar kullanımı

.NET Core C++/CLI projeleri Windows Formlarını ve WPF API'lerini kullanabilir. Bu Windows masaüstü API'lerini kullanmak için, UI kitaplıklarına açık çerçeve başvuruları eklemeniz gerekir. Windows masaüstü API'lerini kullanan SDK tarzı projeler, SDK'yı kullanarak gerekli çerçeve kitaplıklarına otomatik olarak başvurur. `Microsoft.NET.Sdk.WindowsDesktop` C++/CLI projeleri SDK stili proje biçimini kullanmadığından, .NET Core'u hedefalırken açık çerçeve başvuruları eklemeleri gerekir.

Windows Forms API'lerini kullanmak için bu başvuruyu vcxproj dosyasına ekleyin:

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

WPF API'lerini kullanmak için bu başvuruyu vcxproj dosyasına ekleyin:

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

Hem Windows Formlarını hem de WPF API'lerini kullanmak için bu başvuruyu vcxproj dosyasına ekleyin:

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

Şu anda, Visual Studio'nun referans yöneticisini kullanarak bu başvuruları eklemek mümkün değildir. Bunun yerine, proje dosyasını el ile güncelleştirin. Bu güncelleştirme Visual Studio'da projeyi boşaltıp proje dosyasını düzenleyerek yapılabilir. VS Code gibi başka bir düzenleyici de kullanabilirsiniz.

## <a name="build-without-msbuild"></a>MSBuild olmadan yapı

MSBuild kullanmadan C++/CLI projeleri oluşturmak da mümkündür. .NET Core için doğrudan *cl.exe* ve *link.exe*ile c++/CLI projesi oluşturmak için aşağıdaki adımları izleyin:

1. Derleme yaparken `-clr:netcore` *cl.exe'ye*geç.
2. Referans gerekli .NET Çekirdek referans derlemeleri.
3. Bağlantı verirken,.NET Core uygulama ana `LibPath` dizinini *(ijwhost.lib'in* bulunabilmesi için) sağlayın.
4. *ijwhost.dll'yi* (.NET Core uygulama ana dizininden) projenin çıktı dizinine kopyalayın.
5. Yönetilen kodu çalıştıracak uygulamanın ilk bileşeni için [runtimeconfig.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) dosyasının bulunduğundan emin olun. Uygulamanın yönetilen bir giriş noktası `runtime.config` varsa, bir dosya oluşturulur ve otomatik olarak kopyalanır. Ancak uygulamanın yerel bir giriş noktası varsa, `runtimeconfig.json` .NET Core çalışma saatini kullanmak için ilk C++/CLI kitaplığı için bir dosya oluşturmanız gerekir.

## <a name="known-issues"></a>Bilinen sorunlar

.NET Core'u hedefleyen C++/CLI projeleri ile çalışırken dikkat etmesi gereken bilinen birkaç sorun vardır.

* .NET Core C++/CLI projelerindeki WPF çerçeve başvurusu şu anda sembolleri içe aktaramamak la ilgili bazı gereksiz uyarılara neden olur. Bu uyarılar güvenle yoksayılabilir ve yakında düzeltilmelidir.
* Uygulamanın yerel bir giriş noktası varsa, yönetilen kodu ilk yürüten C++/CLI kitaplığı bir [runtimeconfig.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) dosyasına ihtiyaç duyar. Bu config dosyası .NET Core çalışma zamanı başladığında kullanılır. C++/CLI projeleri henüz `runtimeconfig.json` oluşturma zamanında otomatik olarak dosya oluşturmaz, bu nedenle dosyanın el ile oluşturulması gerekir. Yönetilen bir giriş noktasından C++/CLI kitaplığı çağrılırsa, C++/CLI kitaplığı bir `runtimeconfig.json` dosyaya ihtiyaç duymaz (çünkü giriş noktası derlemesi çalışma saatini başlatırken kullanılan bir dosyaya sahip olur). Basit bir `runtimeconfig.json` örnek dosya aşağıda gösterilmiştir. Daha fazla bilgi için [GitHub'daki spec'e](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)bakın.

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
