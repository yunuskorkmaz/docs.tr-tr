---
title: Mac için Visual Studio kullanarak macos'ta .NET Core ile çalışmaya başlama
description: Bu konu başlığı altında Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde size yol gösterir.
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.openlocfilehash: f751e7532e9627de3d3733476f7214654089e468
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170737"
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak macos'ta .NET Core ile çalışmaya başlama

Mac için Visual Studio, .NET Core uygulamaları geliştirmek için bir tam özellikli tümleşik geliştirme ortamı (IDE) sağlar. Bu konu başlığı altında Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde size yol gösterir.

> [!NOTE]
> Geri bildiriminiz çok değerli. Mac için Visual Studio geliştirme ekibine geri bildirim sağlayabilirsiniz iki yolu vardır:
> * Mac için Visual Studio'da **yardımcı** > **sorun bildir** menüsünden veya **sorun bildir** Karşılama ekranında, bir pencere açılır bir hata raporu dosyalama. Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.
> * Bir öneride bulunmak için seçin **yardımcı** > **bir öneride** menüsünden veya **bir öneride** Karşılama ekranında, hangi yönlendirilirsiniz için [Mac Geliştirici topluluğu Web sayfası için visual Studio](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Önkoşullar

Bkz: [Mac üzerinde .NET Core önkoşulları](../../core/macos-prerequisites.md) konu.

## <a name="getting-started"></a>Başlarken

Mac için Visual Studio ve önkoşullar önce yüklediğiniz, bu bölümü atlayarak devam [proje oluşturma](#creating-a-project). Mac için Visual Studio ve önkoşulları yüklemek için aşağıdaki adımları izleyin:

İndirme [yükleyicisi Mac için Visual Studio](https://visualstudio.microsoft.com/vs/visual-studio-mac/). Yükleyiciyi çalıştırın. Okuyun ve lisans sözleşmesini kabul edin. Yükleme sırasında Xamarin, platformlar arası mobil uygulama geliştirme teknolojisinden yüklemek için bir fırsat sunulur. Xamarin ve ilgili bileşenlerini yüklemek için .NET Core geliştirme isteğe bağlıdır. Yükleme işlemi Mac için Visual Studio ile ilgili kılavuz için bkz: [Mac için Visual Studio ile tanışın](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/). Yükleme tamamlandığında, Mac IDE için Visual Studio'yu başlatın.

## <a name="creating-a-project"></a>Proje oluşturma

1. Seçin **yeni proje** Hoş Geldiniz ekranında.

   ![Yeni Proje düğmesi Visual Studio Mac Hoş Geldiniz ekranı](./media/using-on-mac-vs/vsmac1.png)

1. İçinde **yeni proje** iletişim kutusunda **uygulama** altında **.NET Core** düğümü. Seçin **konsol uygulaması** şablonu ve ardından **sonraki**.

   ![Yeni proje şablonları listesi](./media/using-on-mac-vs/vsmac2.png)

1. "HelloWorld" türü **proje adı**. Seçin **oluşturma**.

   ![Yeni konsol uygulaması iletişim kutusu yapılandırın](./media/using-on-mac-vs/vsmac3.png)

1. Proje bağımlılıklarınızı geri yüklerken bekleyin. Tek bir projeye sahip C# dosyası *Program.cs*, kapsayan bir `Program` sınıfıyla birlikte bir `Main` yöntemi. `Console.WriteLine` Deyimi "Hello World!" çıkış Uygulamayı çalıştırdığınızda konsola.

   ![Program.cs dosyasının ana penceresi açın](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırın

Uygulamayı hata ayıklama moduyla çalıştırma <kbd>F5</kbd> veya sürüm modu kullanarak <kbd>CTRL</kbd>+<kbd>F5</kbd>.

![Uygulama çıkış Bölmesi ' Hello World gösterir!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a>Sonraki adım

[Mac için Visual Studio kullanarak macos'ta eksiksiz bir .NET Core çözümü derleme](using-on-mac-vs-full-solution.md) konu, bir yeniden kullanılabilir bir kitaplık ve birim testi içeren eksiksiz bir .NET Core çözümü derleme nasıl gösterir.
