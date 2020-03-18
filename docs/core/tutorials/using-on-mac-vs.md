---
title: Mac için Visual Studio kullanarak .NET Core kullanmaya başlama
description: Bu konu, Mac için Visual Studio ve .NET Core'u kullanarak basit bir konsol uygulaması oluşturmanıza yol açabilirsiniz.
ms.date: 12/19/2019
ms.openlocfilehash: 4cd7e311411bce62698e291e763227496877ea39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740484"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama

Mac için Visual Studio, .NET Core uygulamalarını geliştirmek için tam özellikli entegre geliştirme ortamı (IDE) sağlar. Bu makale, Mac ve .NET Core için Visual Studio'yu kullanarak basit bir konsol uygulaması oluşturmanıza yöneliktir.

> [!NOTE]
> Geri bildiriminiz çok değerlidir. Mac için Visual Studio'daki geliştirme ekibine geri bildirim sağlamanın iki yolu vardır:
>
> * Mac için Visual Studio'da, menüden **Sorun Bildir'i** > **Report a Problem** veya hata raporu doldurmak için bir pencere açacak olan Karşılama ekranından Sorunu Bildir'i'ni seçin. **Report a Problem** Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.
> * Öneride bulunmak için, menüden **Öneri Sağlama'ya Yardım Et'i** > **Provide a Suggestion** veya Sizi Mac Developer Community web sayfası için [Visual Studio'ya](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)götürecek olan Karşılama ekranından Bir **Öneri Sağlayın'ı** seçin.

## <a name="prerequisites"></a>Önkoşullar

[.NET Çekirdek bağımlılıkları ve gereksinimleri](../install/dependencies.md?pivots=os-macos) makalesine bakın.

.NET Core'un desteklenen bir sürümünü kullandığınızdan emin olmak için [.NET Çekirdek Desteği](/visualstudio/mac/net-core-support) makalesini kontrol edin.

## <a name="get-started"></a>Başlarken

Mac için ön koşulları ve Visual Studio'yu zaten yüklediyseniz, bu bölümü atlayın ve proje oluşturmaya devam [edin.](#creating-a-project) Mac için ön koşulları ve Visual Studio'yu yüklemek için aşağıdaki adımları izleyin:

Mac [yükleyici için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)indirin. Yükleyiciyi çalıştırın. Lisans sözleşmesini okuyun ve kabul edin. Yükleme sırasında .NET Core'u yükleme seçeneğini seçin. Platformlar arası mobil uygulama geliştirme teknolojisi olan Xamarin'i yükleme fırsatı nasibini aldınız. Xamarin ve ilgili bileşenlerinin yüklenmesi .NET Core geliştirme için isteğe bağlıdır. Mac yükleme işlemi için Visual Studio'nun bir bölümü [için, Mac belgeleri için Visual Studio'ya](/visualstudio/mac/)bakın. Yükleme tamamlandığında, Mac IDE için Visual Studio'yu başlatın.

## <a name="creating-a-project"></a>Proje oluşturma

1. Başlangıç penceresinde **Yeni'yi** seçin.

   ![Mac Başlangıç ekranı için Visual Studio'da yeni düğme](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. Yeni **Proje** iletişim kutusunda,.NET **Core** düğümünün altındaki **Uygulamayı** seçin. Konsol **Uygulaması** şablonu ve ardından **Next'i**seçin.

   ![Yeni proje şablonları listesi](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. .NET Core'un birden fazla sürümü yüklüyse, projeniz için hedef çerçeveyi seçin.

1. **Proje Adı**için "HelloWorld" yazın. **Oluştur'u**seçin.

   ![Yeni Konsol Uygulaması iletişim günlüğüne yapıla](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Projenin bağımlılıkları geri yüklenirken bekleyin. Proje, *Program.cs,* bir yönteme sahip `Program` bir sınıf `Main` içeren tek bir C# dosyasına sahiptir. Açıklamada `Console.WriteLine` "Merhaba Dünya!" çıkacaktır. uygulama çalıştırıldığında konsola.

   ![Program.cs dosyaaçık ana pencere](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı Hata Ayıklama modunda (komut + enter) kullanarak veya Sürüm modunda (seçenek + komut + girin) kullanarak çalıştırın.

![Uygulama Çıktı sı, Hello World'u gösteriyor!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Sonraki adım

Mac konusu [için Visual Studio'yu kullanarak macOS'ta eksiksiz bir .NET Core çözümü oluşturma,](using-on-mac-vs-full-solution.md) yeniden kullanılabilir bir kitaplık ve birim testi içeren eksiksiz bir .NET Core çözüm oluşturmayı gösterir.
