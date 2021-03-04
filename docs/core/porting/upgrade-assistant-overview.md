---
title: .NET Yükseltme Yardımcısı 'na genel bakış
description: .NET Framework geçiş ve projelerinizi .NET 5 ' e yükseltmelerine yardımcı olan .NET Yükseltme Yardımcısı aracına giriş.
author: ardalis
ms.date: 02/25/2021
ms.openlocfilehash: bd1c904586d170d93b76ae058914adb334289f89
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108685"
---
# <a name="overview-of-the-net-upgrade-assistant"></a>.NET Yükseltme Yardımcısı 'na genel bakış

Şu anda .NET 5 ' e taşıma konusunda ilgilendiğiniz .NET Framework çalışan uygulamalarınız olabilir. .NET Yükseltme Yardımcısı aracı bu işleme yardımcı olabilir. Bu makalede aşağıdakiler sunulmaktadır:

* .NET Yükseltme Yardımcısı 'na genel bakış.
* .NET Yükseltme Yardımcısı 'Nı nasıl yükleyeceksiniz.

## <a name="what-is-the-net-upgrade-assistant"></a>.NET Yükseltme Yardımcısı nedir?

.NET Yükseltme Yardımcısı, farklı türlerde .NET Framework uygulamalarda çalıştırılabilen bir komut satırı aracıdır. .NET Framework uygulamalarını .NET 5 ' e yükseltmeye yardımcı olmak üzere tasarlanmıştır. Araç çalıştırıldıktan sonra, **çoğu durumda uygulama geçişi tamamlamaya daha fazla çaba gerektirir**. Araç, geçişin tamamlanmasına yardımcı olabilecek çözümleyiciler yüklemeyi içerir.

Şu anda araç şu .NET Framework uygulama türlerini destekler:

- .NET Framework Windows Forms uygulamalar
- WPF uygulamalarını .NET Framework
- .NET Framework ASP.NET MVC uygulamaları
- .NET Framework konsol uygulamaları
- .NET Framework sınıf kitaplıkları

.NET Yükseltme Yardımcısı şu anda ön sürüme sahiptir ve sık sık güncelleştirmeler alıyor. Aracı kullanarak sorun buldıysanız, lütfen aracın [GitHub deposunda](https://github.com/dotnet/upgrade-assistant)bunları bildirin.

## <a name="how-to-install-the-net-upgrade-assistant"></a>.NET yükseltme yardımcısını nasıl yüklenir

[Kullanmaya başlama öğreticisi](https://aka.ms/dotnet-upgrade-assistant-install) , .NET Yükseltme Yardımcısı 'nı nasıl yükleyip kullanacağınızı adım adım göstermektedir.

### <a name="prerequisites"></a>Önkoşullar

1. Bu araç proje dosyalarıyla çalışmak için MSBuild kullanır. MSBuild 'in son sürümünün yüklü olduğundan emin olun. Bunu yapmanın kolay bir yolu, [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)' i yüklemektir.
1. Bu araç [TRY-Convert 'e](https://github.com/dotnet/try-convert)bağımlıdır. Aracın doğru çalışması için, proje dosyalarını yeni SDK stiline dönüştürmek üzere TRY-Convert aracını yüklemelisiniz. Zaten bir **deneme** sürümüne sahipseniz, bunun yerine güncelleştirmeniz gerekebilir ( **yükseltmeden sonra Yükseltme Yardımcısı** _0.7.212201_ veya üzeri sürüme bağlıdır)
    1. TRY-Convert ' i yüklemek için: `dotnet tool install -g try-convert`
    1. Güncelleştirmek için dene-Dönüştür: `dotnet tool update -g try-convert`

### <a name="installation-steps"></a>Yükleme adımları

Araç aşağıdakileri çalıştırarak bir .NET CLı aracı olarak yüklenebilir: `dotnet tool install -g upgrade-assistant --add-source https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet-tools/nuget/v3/index.json`

Benzer şekilde, .NET Yükseltme Yardımcısı bir .NET CLı aracı olarak yüklendiği için şu şekilde çalıştırılarak kolayca güncelleştirilebilirler: `https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet-tools/nuget/v3/index.json`

Ayrıntılı yükleme yönergeleri için lütfen projenin [Benioku](https://github.com/dotnet/upgrade-assistant)dosyasına bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Yükseltme Yardımcısı ile bir WPF uygulamasını .NET 5 ' e yükseltme](upgrade-assistant-wpf-framework.md)
- [.NET Yükseltme Yardımcısı ile bir Windows Forms uygulamasını .NET 5 ' e yükseltme](upgrade-assistant-winforms-framework.md)
- [.NET Yükseltme Yardımcısı ile bir ASP.NET MVC uygulamasını .NET 5 ' e yükseltme](upgrade-assistant-aspnetmvc.md)
- [.NET Yükseltme Yardımcısı GitHub deposu](https://github.com/dotnet/upgrade-assistant)
