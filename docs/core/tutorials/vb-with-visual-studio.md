---
title: Visual Studio 2017 ' de Visual Basic ile .NET Core Merhaba Dünya uygulaması
description: Visual Studio 2017 kullanarak Visual Basic basit bir .NET Core konsol uygulaması derlemeyi öğrenin.
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 1200afb30c6bdebf66b2a1e080c62a776a7e9826
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100885"
---
# <a name="build-a-visual-basic-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Visual Studio 2017 ' de .NET Core SDK ile Visual Basic Merhaba Dünya uygulaması derleme

Bu konu, Visual Studio 2017 ' de Visual Basic kullanarak basit bir .NET Core konsol uygulaması oluşturmaya, hata ayıklamanıza ve yayımlamaya yönelik adım adım bir giriş sağlar. Visual Studio 2017, .NET Core uygulamaları oluşturmak için tam özellikli bir geliştirme ortamı sağlar. Uygulama platforma özgü bağımlılıklara sahip olmadığı sürece, uygulama .NET Core 'un hedeflediği tüm platformlarda ve .NET Core yüklü olan herhangi bir sistemde çalışabilir.

## <a name="prerequisites"></a>Prerequisites

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ".NET Core platformlar arası geliştirme" iş yükü yüklendi. Uygulamanızı .NET Core 2,1 veya sonraki sürümleriyle geliştirebilirsiniz.

Daha fazla bilgi için bkz. [Windows üzerinde .NET Core önkoşulları](../windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Basit bir Merhaba Dünya uygulaması

Basit bir "Merhaba Dünya" konsol uygulaması oluşturarak başlayın. Aşağıdaki adımları uygulayın:

1. Visual Studio 2017 ' i başlatın. Menü çubuğundan **dosya** > **Yeni** > **Proje** ' yi seçin. *Yeni proje** iletişim kutusunda **Visual Basic** düğümünü ve ardından **.NET Core** düğümünü seçin. Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin. **Ad** metin kutusuna "HelloWorld" yazın. **Tamam** düğmesini seçin.

   ![Konsol uygulaması seçiliyken yeni proje iletişim kutusu](./media/vb-with-visual-studio/visual-studio-new-project.png)

1. Visual Studio, projenizi oluşturmak için şablonu kullanır. .NET Core için Visual Basic konsol uygulaması şablonu, bağımsız değişken olarak <xref:System.String> dizisi alan `Main`tek bir yöntemle `Program`bir sınıfını otomatik olarak tanımlar. `Main`, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntem olan uygulama giriş noktasıdır. Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.

   ![Visual Studio ve yeni HelloWorld projesi](./media/vb-with-visual-studio/visual-studio-main-window.png)

   Şablon basit bir "Merhaba Dünya" uygulaması oluşturur. "Merhaba Dünya!" değişmez dizesini göstermek için <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemini çağırır Konsol penceresinde. Araç çubuğunda yeşil oklu **HelloWorld** düğmesini seçerek programı hata ayıklama modunda çalıştırabilirsiniz. Bunu yaparsanız, konsol penceresi kapanmadan önce yalnızca kısa bir zaman aralığı için görünür olur. Bu durum `Main` yöntemi sonlandırıldığında ve `Main` yönteminde tek bir deyimin yürütüldüğü anda uygulamanın sona erdiği için oluşur.

1. Uygulamanın konsol penceresini kapatmadan önce duraklatılmasını sağlamak için, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu ekleyin:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

   Bu kod, kullanıcıdan herhangi bir tuşa basması ve bir tuşa basılana kadar programı duraklayacağını ister.

1. Menü çubuğunda **derleme** > **Build Solution**' ı seçin. Bu, programınızı bir tam zamanında (JıT) derleyicisi tarafından ikili koda dönüştürülen bir ara dile (IL) derler.

1. Araç çubuğunda yeşil oklu **HelloWorld** düğmesini seçerek programı çalıştırın.

   ![Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="enhancing-the-hello-world-application"></a>Merhaba Dünya uygulamasını geliştirme

Uygulamanızı, adını ve Tarih ve saat ile birlikte göstermek için kullanıcıya bir ad isteyecek şekilde geliştirin. Programı değiştirmek ve test etmek için aşağıdakileri yapın:

1. Aşağıdaki Visual Basic kodu, `Sub Main(args As String())` satırını izleyen açma köşeli ayracından hemen sonra ve ilk kapanış ayracından önce kod penceresine girin:

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Bu kod `Main` yönteminin içeriğini değiştirir.

   ![Güncelleştirilmiş Main yöntemiyle Visual Studio program dosyası](./media/vb-with-visual-studio/visual-basic-code-window.png)

   Bu kod "adınız nedir?" görüntüler Konsol penceresinde ve ardından ENTER tuşuna basarak Kullanıcı bir dize girene kadar bekler. Bu dizeyi `name`adlı bir değişkende depolar. Ayrıca, geçerli yerel saati içeren <xref:System.DateTime.Now?displayProperty=nameWithType> özelliğinin değerini alır ve bunu `currentDate`adlı bir değişkene atar. Son olarak, bu değerleri konsol penceresinde göstermek için bir [enterpolasyonlu dize](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) kullanır.

1. **Build** > **Build Solution**öğesini seçerek programı derleyin.

1. Araç çubuğundan yeşil oku seçerek, F5 tuşuna basarak **veya hata ayıklama > ** **Başlat** menü öğesini seçerek programı Visual Studio 'daki hata ayıklama modunda çalıştırın. Bir ad girip ENTER tuşuna basarak istemi yanıtlayın.

   ![Değiştirilen program çıkışıyla konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

Uygulamanızı oluşturdunuz ve çalıştırdık. Profesyonel bir uygulama geliştirmek için uygulamanızı yayın için hazırlamak üzere bazı ek adımlar gerçekleştirin:

- Uygulamanızda hata ayıklamak için bkz. [Visual Studio 2017 kullanarak .NET Core Merhaba Dünya uygulamanızda hata ayıklama](debugging-with-visual-studio.md).

- Uygulamanızın dağıtılabilir bir sürümünü yayımlamak için bkz. [Visual Studio 2017 ile .NET Core Merhaba Dünya uygulamanızı yayımlama](publishing-with-visual-studio.md).

## <a name="related-topics"></a>İlgili konular

Konsol uygulaması yerine, Visual Basic, .NET Core ve Visual Studio 2017 ile .NET Standard bir sınıf kitaplığı da oluşturabilirsiniz. Adım adım bir giriş için bkz. [Visual Studio 2017 'de Visual Basic ve .NET Core SDK ile .NET Standard kitaplığı oluşturma](vb-library-with-visual-studio.md).
