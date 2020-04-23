---
title: .NET Framework ve .NET Core arasındaki farklılıklar
description: Windows Presentation Foundation (WPF) ve .NET Core WPF .NET Framework uygulama arasındaki farkları açıklar. Uygulamanızı geçirirken, bu uyumsuzlukları göz önünde bulundurmanız gerekir.
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
# <a name="differences-in-wpf"></a>WPF farkları

Bu makalede, .NET Core ve .NET Framework Windows Presentation Foundation (WPF) arasındaki farklar açıklanmaktadır. .NET Core için WPF, .NET Framework kaynak kodu için özgün WPF tarafından ele alınan [Açık kaynaklı bir çerçevedir](https://github.com/dotnet/wpf) .

.NET Core 'un desteklemediği .NET Framework birkaç özelliği vardır. Desteklenmeyen teknolojiler hakkında daha fazla bilgi için bkz. [.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../../core/porting/net-framework-tech-unavailable.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>SDK stili projeler

.NET Core, SDK stili proje dosyalarını kullanır. Bu proje dosyaları, Visual Studio tarafından yönetilen geleneksel .NET Framework proje dosyalarından farklıdır. .NET Framework WPF uygulamalarınızı .NET Core 'a geçirmek için projelerinizi dönüştürmeniz gerekir. Daha fazla bilgi için bkz. [WPF uygulamalarını .NET Core 3,0 'ye geçirme](convert-project-from-net-framework.md).

## <a name="nuget-package-references"></a>NuGet paket başvuruları

.NET Framework uygulamanız, NuGet bağımlılıklarını bir *Packages. config* dosyasında listelediğinden şu [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) biçime geçin:

1. Visual Studio 'da **Çözüm Gezgini** bölmesini açın.
1. WPF projenizde **Packages. config** > Packages. config 'i**packagereference**' a geçirin.

![PackageReference 'a yükseltme](media/differences-from-net-framework/package-reference-migration.png)

Hesaplanan en üst düzey NuGet bağımlılıklarını gösteren bir iletişim kutusu görünür ve diğer NuGet paketlerinin en üst düzeye yükseltilmesi gerektiğini sorar. **Tamam** ' ı seçtiğinizde, *Packages. config* dosyası projeden kaldırılacak ve `<PackageReference>` öğeler proje dosyasına eklenecektir.

Projeniz kullandığında `<PackageReference>`, paketler yerel olarak bir *paketler* klasöründe depolanmaz. Proje dosyasını açın ve *paketler* klasörüne başvuruda `<Analyzer>` bulunan tüm öğeleri kaldırın. Bu çözümleyiciler, NuGet paket başvurularına otomatik olarak eklenir.

## <a name="code-access-security"></a>Kod Erişimi Güvenliği

.NET Core için .NET Core veya WPF tarafından kod erişim güvenliği (CAS) desteklenmez. Tüm CA 'larla ilgili işlevler tam güven varsayımına göre değerlendirilir. .NET Core için WPF, CA ile ilgili kodu kaldırır. Bu türlerin ortak API 'SI yüzeyi, bu türlere yapılan çağrıların başarılı olduğundan emin olmak için hala var.

Ortak olarak tanımlanan CA 'larla ilgili türler WPF derlemelerinden ve çekirdek .NET kitaplığı derlemelerinden taşındı. WPF derlemelerinin tür iletme türü, taşınan türlerin yeni konumuna ayarlanır.

| Kaynak derleme | Hedef derleme | Tür                |
| --------------- | --------------- | ------------------- |
| *WindowsBase. dll* | *System. Security. Permissions. dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *System. xaml. dll* | *System. Security. Permissions. dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *System. xaml. dll* | *System. Windows. Extension. dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> Savunma savunma durumunu en aza indirmek için, aşağıdaki özelliklerle ilgili bilgileri depolama ve alma işlevleri `XamlAccessLevel` türünde tutulur.
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Framework WPF uygulamasının .NET Core 'a nasıl bağlantı sağladığını öğrenin.](convert-project-from-net-framework.md)
