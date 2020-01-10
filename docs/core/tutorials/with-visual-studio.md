---
title: Visual Studio 'da .NET Core ile Merhaba Dünya uygulaması oluşturma
description: Visual Studio kullanarak ilk .NET Core konsol uygulamanızı C# veya Visual Basic oluşturma hakkında bilgi edinin.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714008"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>Öğretici: Visual Studio 2019 ' de ilk .NET Core konsol uygulamanızı oluşturma

Bu makalede, Visual Studio 2019 ' de Merhaba Dünya .NET Core konsol uygulaması oluşturmak ve çalıştırmak için adım adım bir giriş sunulmaktadır. Bir Merhaba Dünya uygulaması, genellikle yeni bir programlama diline yeni başlayanlar tanıtmak için kullanılır. Bu program yalnızca "Merhaba Dünya!" ifadesini görüntüler iletisini yazdırdı.

## <a name="prerequisites"></a>Prerequisites

- **.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,4 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) . .NET Core 3,1 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.

Daha fazla bilgi için, [.NET Core SDK](../install/sdk.md?pivots=os-windows) makalesine [Visual Studio ile install](../install/sdk.md?pivots=os-windows#install-with-visual-studio) bölümüne bakın.

## <a name="create-the-app"></a>Uygulama oluşturma

Aşağıdaki yönergeler basit bir Merhaba Dünya konsol uygulaması oluşturur:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Visual Studio 2019 ' i açın.

1. "HelloWorld" C# adlı yeni bir .NET Core konsol uygulaması projesi oluşturun.

   1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

      ![Visual Studio başlangıç penceresinde yeni bir proje oluştur düğmesi seçili](./media/with-visual-studio/start-window.png)

   1. **Yeni proje oluştur** sayfasında, arama kutusuna **konsol** girin. Ardından, dil **C#** listesinden seçim yapın ve ardından platform listesinden **tüm platformlar** ' ı seçin. **Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

      ![Filtreler seçiliyken yeni bir proje penceresi oluştur](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > .NET Core şablonlarını görmüyorsanız, muhtemelen gerekli iş yükünün yüklü olması eksik olabilir. **Aradığınızı bulmuyor musunuz?** iletisi altında, **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. Visual Studio Yükleyicisi açılır. **.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğundan emin olun.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **HelloWorld** girin. Ardından **Oluştur**' u seçin.

      ![Yeni proje pencerenizi proje adı, konum ve çözüm adı alanlarıyla yapılandırın](./media/with-visual-studio/configure-new-project.png)

   .NET C# Core konsol uygulaması şablonu, bağımsız değişken olarak <xref:System.String> dizisi alan `Main`tek bir yöntemle `Program`bir sınıfını otomatik olarak tanımlar. `Main`, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntem olan uygulama giriş noktasıdır. Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Visual Studio 2019 ' i açın.

1. "HelloWorld" adlı yeni bir Visual Basic .NET Core konsol uygulaması projesi oluşturun.

   1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

      ![Visual Studio başlangıç penceresinde yeni bir proje oluştur düğmesi seçili](./media/with-visual-studio/start-window.png)

   1. **Yeni proje oluştur** sayfasında, arama kutusuna **konsol** girin. Ardından, dil listesinden **Visual Basic** ' yi seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin. **Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

      ![Konsol uygulaması için Visual Basic şablonu seçin (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > .NET Core şablonlarını görmüyorsanız, muhtemelen gerekli iş yükünün yüklü olması eksik olabilir. **Aradığınızı bulmuyor musunuz?** iletisi altında, **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. Visual Studio Yükleyicisi açılır. **.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğundan emin olun.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **HelloWorld** girin. Ardından **Oluştur**' u seçin.

   .NET Core için konsol uygulaması şablonu, bağımsız değişken olarak <xref:System.String> dizisi alan `Main`tek bir yöntemle `Program`bir sınıfını otomatik olarak tanımlar. `Main`, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntem olan uygulama giriş noktasıdır. Uygulama başlatıldığında sağlanan komut satırı bağımsız değişkenleri `args` parametresinde kullanılabilir.

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   Şablon basit bir "Merhaba Dünya" uygulaması oluşturur. "Merhaba Dünya!" değişmez dizesini göstermek için <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemini çağırır Konsol penceresinde.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Programı çalıştırmak için araç çubuğunda **HelloWorld** ' ı seçin veya **F5**tuşuna basın.

   ![HelloWorld Run düğmesinin seçili olduğu Visual Studio araç çubuğu](./media/with-visual-studio/run-program.png)

   Bir konsol penceresi "Merhaba Dünya!" metniyle açılıyor ekranda ve bazı Visual Studio hata ayıklama bilgilerinde yazdırılır.

   ![Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="enhance-the-app"></a>Uygulamayı geliştirin

Uygulamanızı, adını ve Tarih ve saat ile birlikte göstermek için kullanıcıyı geliştirin. Aşağıdaki yönergeler uygulamayı yeniden değiştirip çalıştırın:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Aşağıdaki kodla, şu anda yalnızca `Console.WriteLine`çağıran satır olan `Main` yönteminin içeriğini değiştirin:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Bu kod "adınız nedir?" görüntüler Konsol penceresinde ve ardından ENTER tuşuna basarak Kullanıcı bir dize girene kadar bekler. Bu dizeyi `name`adlı bir değişkende depolar. Ayrıca, geçerli yerel saati içeren <xref:System.DateTime.Now?displayProperty=nameWithType> özelliğinin değerini alır ve bunu `date`adlı bir değişkene atar. Son olarak, bu değerleri konsol penceresinde göstermek için bir [enterpolasyonlu dize](../../csharp/language-reference/tokens/interpolated.md) kullanır.

1. **Build** > **Build Solution**öğesini seçerek programı derleyin.

1. Programı çalıştırmak için araç çubuğunda **HelloWorld** ' ı seçin veya **F5**tuşuna basın.

1. Bir ad girip **ENTER** tuşuna basarak istemi yanıtlayın.

   ![Değiştirilen program çıkışıyla konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Aşağıdaki kodla, şu anda yalnızca `Console.WriteLine`çağıran satır olan `Main` yönteminin içeriğini değiştirin:

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Bu kod "adınız nedir?" görüntüler Konsol penceresinde ve ardından ENTER tuşuna basarak Kullanıcı bir dize girene kadar bekler. Bu dizeyi `name`adlı bir değişkende depolar. Ayrıca, geçerli yerel saati içeren <xref:System.DateTime.Now?displayProperty=nameWithType> özelliğinin değerini alır ve bunu `date`adlı bir değişkene atar. Son olarak, bu değerleri konsol penceresinde göstermek için bir [enterpolasyonlu dize](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) kullanır.

1. **Build** > **Build Solution**öğesini seçerek programı derleyin.

1. Programı çalıştırmak için araç çubuğunda **HelloWorld** ' ı seçin veya **F5**tuşuna basın.

1. Bir ad girip **ENTER** tuşuna basarak istemi yanıtlayın.

   ![Değiştirilen program çıkışıyla konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

---

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede ilk .NET Core uygulamanızı oluşturdunuz ve çalıştırdık. Sonraki adımda, uygulamanızda hata ayıklaması yapın.

> [!div class="nextstepaction"]
> [Visual Studio 'da bir .NET Core Merhaba Dünya uygulamasında hata ayıklama](debugging-with-visual-studio.md)
