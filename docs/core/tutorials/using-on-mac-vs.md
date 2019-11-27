---
title: Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama
description: Bu konu, Mac için Visual Studio ve .NET Core kullanarak basit bir konsol uygulaması oluşturma konusunda size rehberlik eder.
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: feaed88e902080c5c3b07578b78f8437489a690c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428588"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama

Mac için Visual Studio .NET Core uygulamaları geliştirmek için tam özellikli bir tümleşik geliştirme ortamı (IDE) sağlar. Bu konu, Mac için Visual Studio ve .NET Core kullanarak basit bir konsol uygulaması oluşturma konusunda size rehberlik eder.

> [!NOTE]
> Geri bildiriminiz çok değerli. Mac için Visual Studio üzerinde geliştirme ekibine geri bildirimde bulunmak için kullanabileceğiniz iki yol vardır:
>
> * Mac için Visual Studio, menüden bir **sorun bildirmek** veya hoş geldiniz ekranından bir **sorun** bildirmek için > **Yardım** ' ı seçin. Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.
> * Bir öneride bulunmak için, **yardım** > menüden **bir öneri sağlayın** veya hoş geldiniz ekranından bir öneri **sağlayın** ve bu işlem sizi [Mac için Visual Studio Geliştirici topluluğu Web sayfasına](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)götürür.

## <a name="prerequisites"></a>Önkoşullar

Bkz. [.NET Core Dependencies ve Requirements](../install/dependencies.md?tabs=netcore30&pivots=os-macos) konusuna bakın.

.NET Core 'un desteklenen bir sürümünü kullandığınızdan emin olmak için [.NET Core destek](/visualstudio/mac/net-core-support) makalesine bakın.

## <a name="get-started"></a>başlarken

Önkoşulları ve Mac için Visual Studio zaten yüklediyseniz, bu bölümü atlayın ve [proje oluşturmaya](#creating-a-project)devam edin. Önkoşulları ve Mac için Visual Studio yüklemek için şu adımları izleyin:

[Mac için Visual Studio yükleyicisini](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)indirin. Yükleyiciyi çalıştırın. Lisans sözleşmesini okuyun ve kabul edin. Yüklemesi sırasında .NET Core 'u yüklemek için seçeneği belirleyin. Platformlar arası mobil uygulama geliştirme teknolojisi olan Xamarin 'i yükleyebilirsiniz. Xamarin ve ilgili bileşenlerinin yüklenmesi .NET Core geliştirmesi için isteğe bağlıdır. Mac için Visual Studio yüklemesi işlemini adım adım için [Mac için Visual Studio belgelerine](/visualstudio/mac/)bakın. Yüklemesi tamamlandığında Mac için Visual Studio IDE 'yi başlatın.

## <a name="creating-a-project"></a>Proje oluşturma

1. Başlangıç penceresinde **Yeni** ' yi seçin.

   ![Mac için Visual Studio başlangıç ekranında yeni düğme](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. **Yeni proje** iletişim kutusunda, **.NET Core** düğümünün altında **uygulama** ' yı seçin. **Konsol uygulaması** şablonunu ve ardından Ileri ' **yi**seçin.

   ![Yeni proje şablonları listesi](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. .NET Core 'un birden fazla sürümü yüklüyse, projeniz için hedef çerçeveyi seçin.

1. **Proje adı**Için "HelloWorld" yazın. **Oluştur**' u seçin.

   ![Yeni konsol uygulamanızı yapılandırma iletişim kutusu](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Projenin bağımlılıkları geri yüklenirken bekleyin. Projenin bir `Main` yöntemi ile C# `Program` sınıfınıiçeren tek bir dosyası vardır. `Console.WriteLine` deyimin "Merhaba Dünya!" çıktısı alınacaktır uygulama çalıştırıldığında konsola.

   ![Program.cs dosyasının açık olduğu ana pencere](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı hata ayıklama modunda ⌘ ↵ (komut + ENTER) kullanarak veya ⌥ ⌘ ↵ (Option + Command + ENTER) kullanarak yayın modunda çalıştırın.

![Uygulama çıkış bölmesi Merhaba Dünya gösterir!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Sonraki adım

[MacOS üzerinde Mac için Visual Studio konu başlığı kullanarak tüm .NET Core çözümü oluşturma](using-on-mac-vs-full-solution.md) , yeniden kullanılabilir bir kitaplık ve birim testi içeren bir .NET Core çözümünün nasıl oluşturulacağını göstermektedir.
