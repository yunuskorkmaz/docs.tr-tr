---
title: "Mac için Visual Studio kullanarak macOS üzerinde .NET Core'u kullanmaya başlama"
description: "Bu konu, Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde açıklanmaktadır."
keywords: .NET, .NET core macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8902e849-dd17-42c0-8264-cc7ae3927a0c
ms.openlocfilehash: 893999f9abcc299da4fb0923fe47c371079f695c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak macOS üzerinde .NET Core'u kullanmaya başlama

Mac için Visual Studio .NET Core uygulamaları geliştirmek için bir tam özellikli tümleşik geliştirme ortamı (IDE) sağlar. Bu konu, Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde açıklanmaktadır.

> [!NOTE]
> Geri bildiriminiz yüksek değerli. Mac için Visual Studio geliştirme ekibine geribildirim sağlayabilir iki yolu vardır:
> * Mac için Visual Studio'da seçin **yardımcı** > **bir sorun bildirmek** menüsünden veya **bir sorun bildirmek** Karşılama ekranında olduğu için bir pencere açılır bir hata raporu dosyalama. Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.
> * Bir öneride bulunmak için seçin **yardımcı** > **bir öneride bulunmak** menüsünden veya **bir öneride bulunmak** Karşılama ekranında, hangi yönlendirilirsiniz için [Mac UserVoice Web sayfası için visual Studio](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

## <a name="prerequisites"></a>Önkoşullar

Bkz: [.NET Core Mac üzerinde önkoşulları](../../core/macos-prerequisites.md) konu.

## <a name="getting-started"></a>Başlarken

Mac için Önkoşullar ve Visual Studio zaten yüklediniz, bu bölüm atlayın ve devam [proje oluşturma](#creating-a-project). Mac için Visual Studio ve önkoşulları yüklemek için aşağıdaki adımları izleyin:

Karşıdan [Mac Yükleyicisi için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/). Yükleyiciyi çalıştırın. Okuyun ve Lisans Sözleşmesi'ni kabul edin. Yükleme sırasında Xamarin, platformlar arası mobil uygulama geliştirme teknolojisi yükleme fırsatı sağlanan. Xamarin ve ilgili bileşenlerini yüklemek için .NET Core geliştirme isteğe bağlıdır. Visual Studio Mac yükleme işlemi için kılavuz için bkz: [Mac için Visual Studio Tanıtımı](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/). Yükleme tamamlandığında, Mac IDE için Visual Studio'yu başlatın.

## <a name="creating-a-project"></a>Proje oluşturma

1. Seçin **yeni proje** Hoş Geldiniz ekranında.

   ![Mac Hoş Geldiniz ekranı için Visual Studio yeni proje düğmesinde](./media/using-on-mac-vs/vsmac1.png)

1. İçinde **yeni proje** iletişim kutusunda **uygulama** altında **.NET Core** düğümü. Seçin **konsol uygulaması** şablonu ve ardından **sonraki**.

   ![Yeni proje şablonları listesi](./media/using-on-mac-vs/vsmac2.png)

1. "HelloWorld" türü **proje adı**. Seçin **oluşturma**.

   ![Yeni konsol uygulaması iletişim yapılandırın](./media/using-on-mac-vs/vsmac3.png)

1. Proje bağımlılıkları geri bekleyin. Tek bir C# dosyası, projenin içerdiğinden *Program.cs*, içeren bir `Program` ile sınıf bir `Main` yöntemi. `Console.WriteLine` Deyimi "Hello World!" çıktı Uygulama çalıştırıldığında konsola.

   ![Program.cs dosyasını ana penceresi açın](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırın

Hata ayıklama modunu kullanarak uygulama çalıştırma <kbd>F5</kbd> veya yayın modunu kullanarak <kbd>CTRL</kbd>+<kbd>F5</kbd>.

![Uygulama çıkış Bölmesi ' Hello World gösterir!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a>Sonraki adım

[Mac için Visual Studio kullanarak macOS üzerinde eksiksiz bir .NET Core çözümü derleme](using-on-mac-vs-full-solution.md) konu yeniden kullanılabilir kitaplık ve birim testi içeren tam bir .NET Core çözümünü nasıl oluşturulacağını gösterir.
