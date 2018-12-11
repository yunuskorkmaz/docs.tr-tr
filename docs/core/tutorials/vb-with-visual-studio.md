---
title: Visual Studio 2017'de Visual Basic ile .NET core Merhaba Dünya uygulaması
description: Visual Studio 2017'yi kullanarak Visual Basic ile basit bir .NET Core konsol uygulaması oluşturmayı öğrenin.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: e743cb496aca101b4594435c86e48951870cf8ef
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170034"
---
# <a name="build-a-net-core-visual-basic-hello-world-application-in-visual-studio-2017"></a>Visual Studio 2017'de .NET Core Visual Basic Merhaba Dünya uygulaması derleme

Bu konuda, derleme, hata ayıklama ve Visual Studio 2017'de Visual Basic kullanarak basit bir .NET Core konsol uygulaması yayımlama için adım adım bir giriş sağlar. Visual Studio 2017, .NET Core uygulamaları oluşturmaya yönelik tam özellikli bir geliştirme ortamı sağlar. Uygulama, platforma özel bağımlılıklar yok sürece, uygulama, .NET Core hedefleyen herhangi bir platformda çalışabilir ve .NET Core sahip herhangi bir sistemde yüklü.

## <a name="prerequisites"></a>Önkoşullar

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır. .NET Core 2.0 ile uygulamanızı geliştirebilirsiniz.

Daha fazla bilgi için [Windows üzerinde .NET Core önkoşulları](../../core/windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Basit bir Hello World uygulaması

Basit bir "Hello World" konsol uygulaması oluşturarak başlayın. Aşağıdaki adımları uygulayın:

1. Visual Studio 2017'yi başlatın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde *yeni proje** iletişim kutusunda **Visual Basic** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusunda, "HelloWorld" yazın. **Tamam** düğmesini seçin.

   ![Seçilen konsol uygulaması ile yeni proje iletişim kutusu](./media/vb-with-visual-studio/visual-studio-new-project.png)
   
1. Visual Studio, projenizi oluşturmak için şablon kullanır. .NET Core için Visual Basic konsol uygulaması şablonu otomatik olarak bir sınıf tanımlar `Program`, tek bir yöntemi olan `Main`, alan bir <xref:System.String> bağımsız değişken olarak bir dizi. `Main` uygulama başlatıldığında otomatik olarak çalışma zamanı tarafından çağrılır yöntemi uygulama giriş noktası niteliğindedir. Uygulama başlatıldığında sağlanan komut satırı bağımsız değişkenleri kullanılabilir *args* dizisi.

   ![Visual Studio ve yeni HelloWorld proje](./media/vb-with-visual-studio/visual-studio-main-window.png)

   Şablon, basit bir "Hello World" uygulaması oluşturur. Çağrı <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> "Hello World!" sabit dizesini görüntülemek için yöntemi Konsol penceresinde. Seçerek **HelloWorld** düğme araç çubuğundaki yeşil ok ile programın hata ayıklama modunda çalıştırabilir. Bunu yaparsanız, kapatılmadan önce konsol penceresi yalnızca kısa bir zaman aralığı için görülebilir. Bu durum oluşur `Main` yöntemi sonlandırır ve uygulama aşağıdaki tek deyimde olan en kısa sürede sona `Main` yöntemini yürütür.

1. Konsol penceresinde kapatılmadan önce beklenecek Uygulanmanın için çağırdıktan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   Bu kod, herhangi bir tuşa basın ister ve daha sonra bir tuşa basıldığında kadar program duraklatılır.

1. Menü çubuğunda, seçin **derleme** > **Çözümü Derle**. Bu, just-in-time (JIT) derleyici tarafından ikili koda dönüştürülür bir ara dile (IL) programınızı derler.

1. Programı çalıştırmayı seçerek tarafından **HelloWorld** araç çubuğundaki yeşil bir ok düğmesi.

   ![Devam etmek için herhangi bir tuşa Hello World tuşuna gösteren konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="enhancing-the-hello-world-application"></a>Hello World uygulaması geliştirme

Kullanıcıdan kendi ad ve tarih ve saat ile birlikte görüntülemek için uygulama geliştirin. Program sınama ve değiştirmek için aşağıdakileri yapın:

1. Aşağıdaki kod Visual Basic kod penceresinde izleyen hemen ayraç sonra girin `Sub Main(args As String())` satır ve ilk ayraç önce:

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Bu kodu varolan değiştirir <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, ve <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> deyimleri.

   ![Visual Studio Program dosyası ile güncelleştirilmiş Main yöntemi](./media/vb-with-visual-studio/visual-basic-code-window.png)

   Bu kod, "Adınız ne?" görüntüler. Kullanıcı kadar bekler ve konsol penceresinde Enter tuşuna basın, bir dize girer. Bu dize adlı bir değişkende depoladığı `name`. Ayrıca bir değeri alır <xref:System.DateTime.Now?displayProperty=nameWithType> geçerli yerel saat içerir ve adlı bir değişkene atar özelliği `currentDate`. Son olarak, bunu kullanan bir [ilişkilendirilmiş bir dizedir](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) bu değerleri konsol penceresinde görüntüler.

1. Program seçerek derleme **derleme** > **Çözümü Derle**.

1. Araç çubuğundaki yeşil oku seçerek, F5 tuşuna basarak veya seçerek Visual Studio'da hata ayıklama modunda programı çalıştırın **hata ayıklama** > **hata ayıklamayı Başlat** menü öğesi. Bir ad girmeniz ve Enter tuşuna basarak istemine yanıt.

   ![Konsol penceresi ile değiştirilmiş program çıktısı](./media/with-visual-studio/hello-world-update.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

Oluşturduğunuz ve uygulamanızı çalıştırın. Profesyonel uygulama geliştirmek için uygulamanız yayımlanmaya hazır hale getirmek için bazı ek adımlar uygulayın:

- Uygulamanızı hata ayıklama hakkında daha fazla bilgi için bkz: [Visual Studio 2017 ile C# Merhaba Dünya uygulamanızın hatalarını ayıklama](debugging-with-visual-studio.md).

- Geliştirme ve uygulamanızın dağıtılabilir bir sürümünü yayımlama hakkında daha fazla bilgi için bkz: [Visual Studio 2017 ile C# Merhaba Dünya uygulamanızı yayımlama](publishing-with-visual-studio.md).

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
