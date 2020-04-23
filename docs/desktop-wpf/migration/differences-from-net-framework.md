---
title: .NET Framework ve .NET Core arasındaki farklar
description: Windows Presentation Foundation (WPF) ve .NET Core WPF'nin .NET Framework uygulaması arasındaki farkları açıklar. Uygulamanızı geçirerken, bu uyumsuzlukları göz önünde bulundurmalısınız.
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 341e576f17c522fbcbb9c417176e9d4a13ab1b18
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82072209"
---
# <a name="differences-in-wpf"></a>WPF'deki farklar

Bu makalede, .NET Core ve .NET Framework'de Windows Presentation Foundation (WPF) arasındaki farklar açıklanmaktadır. .NET Core için WPF, .NET Framework kaynak kodu için orijinal WPF'den çatallanmış açık [kaynak](https://github.com/dotnet/wpf) çerçevedir.

.NET Framework'ün .NET Core'un desteklemediği birkaç özelliği vardır. Desteklenmeyen teknolojiler hakkında daha fazla bilgi için [.NET Core'da bulunmayan .NET Framework teknolojilerine](../../core/porting/net-framework-tech-unavailable.md)bakın.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>SDK tarzı projeler

.NET Core, SDK tarzı proje dosyalarını kullanır. Bu proje dosyaları Visual Studio tarafından yönetilen geleneksel .NET Framework proje dosyalarından farklıdır. .NET Framework WPF uygulamalarınızı .NET Core'a geçirmek için projelerinizi dönüştürmeniz gerekir. Daha fazla bilgi için [WPF uygulamalarını .NET Core 3.0'a geçirin.](convert-project-from-net-framework.md)

## <a name="nuget-package-references"></a>NuPaket referansları alın

.NET Framework uygulamanız NuGet bağımlılıklarını *bir packages.config* dosyasında [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) listeliyorsa, biçime geçirin:

1. Visual Studio'da **Solution Explorer** bölmesini açın.
1. WPF projenizde **packagereference'a sağ tıkla.config** > **Migrate packages.config to PackageReference**.

![PackageReference'a yükseltme](media/differences-from-net-framework/package-reference-migration.png)

Hesaplanan üst düzey NuGet bağımlılıklarını gösteren ve hangi diğer NuGet paketlerinin en üst düzeye yükseltilmesi gerektiğini soran bir iletişim kutusu görüntülenir. **Tamam'ı** seçin ve *packages.config* dosyası projeden kaldırılır ve `<PackageReference>` öğeler proje dosyasına eklenir.

Projeniz kullandığında, `<PackageReference>`paketler *paketler* paketler klasöründe yerel olarak depolanır, genel olarak depolanır. Proje dosyasını açın `<Analyzer>` ve *Paketler* klasörüne yönlendirilen öğeleri kaldırın. Bu çözümleyiciler otomatik olarak NuGet paket başvurularına dahil edilir.

## <a name="code-access-security"></a>Kod Erişimi Güvenliği

Kod Erişim Güvenliği (CAS) .NET Core veya WPF tarafından .NET Core için desteklenmez. CAS ile ilgili tüm işlevler tam güven varsayımı altında ele alının. .NET Core için WPF, CAS ile ilgili kodu kaldırır. Bu tür deki çağrıların başarılı olduğundan emin olmak için bu tür lerin genel API yüzeyi hala mevcuttur.

Genel olarak tanımlanan CAS ile ilgili türler WPF derlemelerinden core .NET kitaplık derlemelerine taşındı. WPF derlemeleri, taşınan türlerin yeni konumuna tür iletme kümesine sahiptir.

| Kaynak derleme | Hedef montaj | Tür                |
| --------------- | --------------- | ------------------- |
| *WindowsBase.dll* | *System.Security.Permissions.dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *Sistem.Xaml.dll* | *System.Security.Permissions.dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *Sistem.Xaml.dll* | *System.Windows.Extension.dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> Taşıma sürtünmesini en aza indirmek için, aşağıdaki özelliklerle ilgili bilgilerin depolanması ve alınması `XamlAccessLevel` işlevi türde korunmuştur.
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>Sonraki adımlar

- [Bir .NET Framework WPF uygulamasını .NET Core'a nasıl ileteceklerini öğrenin.](convert-project-from-net-framework.md)
