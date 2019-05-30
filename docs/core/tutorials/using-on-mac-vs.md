---
title: Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama
description: Bu konu başlığı altında Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde size yol gösterir.
author: mairaw
ms.date: 06/12/2017
ms.custom: seodec18
ms.openlocfilehash: 4467842c0b65ea536cc26601981d9fcc2bc68f2d
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300045"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama

Mac için Visual Studio, .NET Core uygulamaları geliştirmek için bir tam özellikli tümleşik geliştirme ortamı (IDE) sağlar. Bu konu başlığı altında Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde size yol gösterir.

> [!NOTE]
> Geri bildiriminiz çok değerli. Mac için Visual Studio geliştirme ekibine geri bildirim sağlayabilirsiniz iki yolu vardır:
> * Mac için Visual Studio'da **yardımcı** > **sorun bildir** menüsünden veya **sorun bildir** Karşılama ekranında, bir pencere açılır bir hata raporu dosyalama. Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.
> * Bir öneride bulunmak için seçin **yardımcı** > **bir öneride** menüsünden veya **bir öneride** Karşılama ekranında, hangi yönlendirilirsiniz için [Mac Geliştirici topluluğu Web sayfası için visual Studio](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Önkoşullar

Bkz: [Mac üzerinde .NET Core önkoşulları](../../core/macos-prerequisites.md) konu.

## <a name="get-started"></a>Kullanmaya başlayın

Mac için Visual Studio ve önkoşullar önce yüklediğiniz, bu bölümü atlayarak devam [proje oluşturma](#creating-a-project). Mac için Visual Studio ve önkoşulları yüklemek için aşağıdaki adımları izleyin:

İndirme [yükleyicisi Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Yükleyiciyi çalıştırın. Okuyun ve lisans sözleşmesini kabul edin. Yükleme sırasında Xamarin, platformlar arası mobil uygulama geliştirme teknolojisinden yüklemek için bir fırsat sunulur. Xamarin ve ilgili bileşenlerini yüklemek için .NET Core geliştirme isteğe bağlıdır. Yükleme işlemi Mac için Visual Studio ile ilgili kılavuz için bkz: [belgeleri Mac için Visual Studio](/visualstudio/mac/). Yükleme tamamlandığında, Mac IDE için Visual Studio'yu başlatın.

## <a name="creating-a-project"></a>Proje oluşturma

1. Seçin **yeni proje** Hoş Geldiniz ekranında.

   ![Yeni Proje düğmesi Visual Studio Mac Hoş Geldiniz ekranı](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. İçinde **yeni proje** iletişim kutusunda **uygulama** altında **.NET Core** düğümü. Seçin **konsol uygulaması** şablonu ve ardından **sonraki**.

   ![Yeni proje şablonları listesi](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. "HelloWorld" türü **proje adı**. **Oluştur**’u seçin.

   ![Yeni konsol uygulaması iletişim kutusu yapılandırın](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Proje bağımlılıklarınızı geri yüklerken bekleyin. Tek bir projeye sahip C# dosyası *Program.cs*, kapsayan bir `Program` sınıfıyla birlikte bir `Main` yöntemi. `Console.WriteLine` Deyimi "Hello World!" çıkış Uygulamayı çalıştırdığınızda konsola.

   ![Program.cs dosyasının ana penceresi açın](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı hata ayıklama moduyla çalıştırma <kbd>F5</kbd> veya sürüm modu kullanarak <kbd>CTRL</kbd>+<kbd>F5</kbd>.

![Uygulama çıkış Bölmesi ' Hello World gösterir!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Sonraki adım

[Mac için Visual Studio kullanarak macos'ta eksiksiz bir .NET Core çözümü derleme](using-on-mac-vs-full-solution.md) konu, bir yeniden kullanılabilir bir kitaplık ve birim testi içeren eksiksiz bir .NET Core çözümü derleme nasıl gösterir.
