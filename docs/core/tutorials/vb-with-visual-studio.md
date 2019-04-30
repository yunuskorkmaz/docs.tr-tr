---
title: Visual Studio 2017'de Visual Basic ile .NET core Merhaba Dünya uygulaması
description: Visual Studio 2017'yi kullanarak Visual Basic ile basit bir .NET Core konsol uygulaması oluşturmayı öğrenin.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: faa801d8ded90b1a0f68eac1824e60ee6ba468a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647143"
---
# <a name="build-a-visual-basic-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Visual Studio 2017'de .NET Core SDK'sı ile bir Visual Basic Merhaba Dünya uygulaması derleme

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

- Uygulamanızda hata ayıklamak için bkz: [Visual Studio 2017 kullanarak .NET Core Merhaba Dünya uygulamanızın hatalarını](debugging-with-visual-studio.md).

- Uygulamanızı bir dağıtılabilir sürümünü yayımlamak için bkz: [Visual Studio 2017 ile .NET Core Merhaba Dünya uygulamanızı yayımlama](publishing-with-visual-studio.md).

## <a name="related-topics"></a>İlgili konular

Bir konsol uygulaması yerine bir .NET Standard sınıf kitaplığı Visual Basic, .NET Core ve Visual Studio 2017 ile de oluşturabilirsiniz. Adım adım bir giriş için bkz. [Visual Basic ve Visual Studio 2017'de .NET Core SDK'sı ile bir .NET Standard kitaplığı derleme](vb-library-with-visual-studio.md).
