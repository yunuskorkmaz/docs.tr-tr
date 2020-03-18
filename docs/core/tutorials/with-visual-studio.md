---
title: Visual Studio'da .NET Core ile Bir Merhaba Dünya uygulaması oluşturun
description: Visual Studio'yu kullanarak C# veya Visual Basic ile ilk .NET Core konsol uygulamanızı nasıl oluşturabilirsiniz öğrenin.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714008"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>Öğretici: Visual Studio 2019'da ilk .NET Core konsol uygulamanızı oluşturun

Bu makale, Visual Studio 2019'da Hello World .NET Core konsol uygulaması oluşturmak ve çalıştırmak için adım adım giriş sağlar. Bir Hello World uygulaması geleneksel olarak yeni bir programlama dili yeni başlayanlar tanıtmak için kullanılır. Bu program sadece ifade görüntüler "Merhaba Dünya!" iletisini yazdırdı.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2019 sürüm 16.4 veya](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) daha sonraki bir sürümü **.NET Core çapraz platform geliştirme** iş yükü yüklü. .NET Core 3.1 Bu iş yükünü seçtiğinizde Otomatik olarak yüklenir.

Daha fazla bilgi için [,.NET Core SDK](../install/sdk.md?pivots=os-windows) makalesini [yükleyin Visual Studio ile Yükle](../install/sdk.md?pivots=os-windows#install-with-visual-studio) bölümüne bakın.

## <a name="create-the-app"></a>Uygulama oluşturma

Aşağıdaki talimatlar basit bir Hello World konsol uygulaması oluşturur:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Görsel Stüdyo 2019'u açın.

1. "HelloWorld" adında yeni bir C# .NET Core konsol uygulaması projesi oluşturun.

   1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

      ![Visual Studio başlangıç penceresinde seçilen yeni bir proje düğmesi oluşturma](./media/with-visual-studio/start-window.png)

   1. Yeni **bir proje oluştur** sayfasında, arama kutusuna **konsolgirin.** Ardından, Dil listesinden **C#'yi** seçin ve ardından Platform listesinden **Tüm platformları** seçin. Konsol **Uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri'yi**seçin.

      ![Filtreler seçili yeni bir proje penceresi oluşturma](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > .NET Core şablonlarını görmüyorsanız, yüklü olan gerekli iş yükünü büyük olasılıkla kaçırıyorsunuz. **Aradığınızı bulamıyor?** iletinin **altında, daha fazla araç ve özellik yükle** bağlantısını seçin. Visual Studio Yükleyici açılır. **.NET Core çapraz platform geliştirme** iş yükünün yüklü olduğundan emin olun.

   1. Yeni **proje sayfanızı Yapılandır'da,** **Project ad** kutusuna **HelloWorld'u** girin. Ardından **Oluştur'u**seçin.

      ![Yeni proje pencerenizi Proje adı, konum ve çözüm adı alanlarıyla yapılandırma](./media/with-visual-studio/configure-new-project.png)

   .NET Core için C# Console Application şablonu, `Program`bir <xref:System.String> diziyi `Main`bağımsız değişken olarak alan bir sınıfı otomatik olarak tanımlar. `Main`uygulama giriş noktasıdır, uygulamayı başlattığında çalışma süresine göre otomatik olarak çağrılan yöntemdir. Uygulama başlatıldığında sağlanan tüm komut satırı bağımsız *değişkenleri args* dizisinde kullanılabilir.

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Görsel Stüdyo 2019'u açın.

1. "HelloWorld" adlı yeni bir Visual Basic .NET Core konsol uygulaması projesi oluşturun.

   1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

      ![Visual Studio başlangıç penceresinde seçilen yeni bir proje düğmesi oluşturma](./media/with-visual-studio/start-window.png)

   1. Yeni **bir proje oluştur** sayfasında, arama kutusuna **konsolgirin.** Ardından, Dil listesinden **Visual Basic'i** seçin ve ardından Platform listesindeki **Tüm platformları** seçin. Konsol **Uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri'yi**seçin.

      ![Konsol Uygulaması için Visual Basic şablonu (.NET Framework) seçeneğini seçin](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > .NET Core şablonlarını görmüyorsanız, yüklü olan gerekli iş yükünü büyük olasılıkla kaçırıyorsunuz. **Aradığınızı bulamıyor?** iletinin **altında, daha fazla araç ve özellik yükle** bağlantısını seçin. Visual Studio Yükleyici açılır. **.NET Core çapraz platform geliştirme** iş yükünün yüklü olduğundan emin olun.

   1. Yeni **proje sayfanızı Yapılandır'da,** **Project ad** kutusuna **HelloWorld'u** girin. Ardından **Oluştur'u**seçin.

   .NET Core konsol uygulaması şablonu, bir `Program` <xref:System.String> diziyi bağımsız değişken `Main`olarak alan bir sınıfı otomatik olarak tek bir yöntemle tanımlar. `Main`uygulama giriş noktasıdır, uygulamayı başlattığında çalışma süresine göre otomatik olarak çağrılan yöntemdir. Uygulama başlatıldığında sağlanan tüm komut satırı bağımsız `args` değişkenleri parametrede kullanılabilir.

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   Şablon basit bir "Hello World" uygulaması oluşturur. Bu kelime <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> dizesini görüntülemek için yöntem çağırır "Merhaba Dünya!" konsol penceresinde.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Programı çalıştırmak için araç çubuğunda **HelloWorld'u** seçin veya **F5 tuşuna**basın.

   ![HelloWorld çalıştır düğmesi seçili Visual Studio araç çubuğu](./media/with-visual-studio/run-program.png)

   "Merhaba Dünya!" metniyle bir konsol penceresi açılır. ekrana ve bazı Visual Studio hata ayıklama bilgileri yazdırılır.

   ![Devam etmek için Hello World Press tuşlarını gösteren konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="enhance-the-app"></a>Uygulamayı geliştirin

Kullanıcıdan adını almak için uygulamanızı geliştirin ve tarih ve saatle birlikte görüntüleyin. Aşağıdaki talimatlar uygulamayı değiştirip yeniden çalıştırın:

# <a name="c"></a>[C #](#tab/csharp)

1. Şu anda `Main` sadece çağıran satır `Console.WriteLine`olan yöntemin içeriğini aşağıdaki kodla değiştirin:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Bu kod "Adınız nedir?" konsol penceresinde ve kullanıcı enter tuşu ardından bir dize girene kadar bekler. Bu dizeyi . `name` Ayrıca, geçerli yerel saati <xref:System.DateTime.Now?displayProperty=nameWithType> içeren özelliğin değerini alır ve onu adlı `date`bir değişkene atar. Son olarak, konsol penceresinde bu değerleri görüntülemek için [bir enterpolasyonlu dize](../../csharp/language-reference/tokens/interpolated.md) kullanır.

1. **Yapı** > **Çözüm'üne**seçerek programı derle.

1. Programı çalıştırmak için araç çubuğunda **HelloWorld'u** seçin veya **F5 tuşuna**basın.

1. Bir ad girerek ve **Enter** tuşuna basarak istemi yanıtlayın.

   ![Değiştirilmiş program çıktılı konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Şu anda `Main` sadece çağıran satır `Console.WriteLine`olan yöntemin içeriğini aşağıdaki kodla değiştirin:

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Bu kod "Adınız nedir?" konsol penceresinde ve kullanıcı enter tuşu ardından bir dize girene kadar bekler. Bu dizeyi . `name` Ayrıca, geçerli yerel saati <xref:System.DateTime.Now?displayProperty=nameWithType> içeren özelliğin değerini alır ve onu adlı `date`bir değişkene atar. Son olarak, konsol penceresinde bu değerleri görüntülemek için [bir enterpolasyonlu dize](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) kullanır.

1. **Yapı** > **Çözüm'üne**seçerek programı derle.

1. Programı çalıştırmak için araç çubuğunda **HelloWorld'u** seçin veya **F5 tuşuna**basın.

1. Bir ad girerek ve **Enter** tuşuna basarak istemi yanıtlayın.

   ![Değiştirilmiş program çıktılı konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

---

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, ilk .NET Core uygulamanızı oluşturdunuz ve çalıştırın. Bir sonraki adımda, uygulamanızı hata ayıklama.

> [!div class="nextstepaction"]
> [Visual Studio'da Hata Ayıklama .NET Core Hello World uygulaması](debugging-with-visual-studio.md)
