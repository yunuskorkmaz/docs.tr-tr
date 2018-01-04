---
title: "Hello World uygulamasının .NET Core ve Visual Studio 2017'de Visual Basic ile oluşturma"
description: "Visual Studio 2017 kullanarak Visual Basic ile basit bir .NET Core konsol uygulaması oluşturmayı öğrenin."
keywords: ".NET core, .NET Core konsol uygulaması, Visual Studio 2017"
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-vb
dev_langs: vb
ms.workload: dotnetcore
ms.openlocfilehash: 058e8740ed523d606da0ad46e052f91f31b3b2d9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="build-a-visual-basic-hello-world-application-with-net-core-in-visual-studio-2017"></a>Visual Basic Hello World uygulamasının Visual Studio 2017 .NET çekirdek ile derleme

Bu konuda oluşturma, hata ayıklama ve Visual Basic Visual Studio 2017 kullanarak basit bir .NET Core konsol uygulaması yayımlama için adım adım bir giriş sağlar. Visual Studio 2017 .NET Core uygulamaları oluşturmak için bir tam özellikli bir geliştirme ortamı sağlar. Uygulama platforma özgü bağımlılıklar yok sürece, uygulama .NET Core hedefleyen herhangi bir platformda çalışabilir ve .NET Core sahip herhangi bir sisteminde yüklü.

## <a name="prerequisites"></a>Önkoşullar

[Visual Studio 2017](https://www.visualstudio.com/downloads/) yüklü ".NET Core platformlar arası geliştirme" iş yükü ile. .NET Core 2.0 ile uygulamanızı geliştirebilirsiniz.

Daha fazla bilgi için bkz: [.NET Core Windows önkoşulları](../../core/windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Basit bir Hello World uygulamasının

Basit bir "Hello World" konsol uygulaması oluşturarak başlayın. Aşağıdaki adımları uygulayın:

1. Visual Studio 2017 başlatın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde *yeni proje** iletişim kutusunda **Visual Basic** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna, "HelloWorld" yazın. Seçin **Tamam** düğmesi.

   ![Konsol seçilen uygulama ile yeni proje iletişim kutusu](./media/vb-with-visual-studio/new-project.png)
   
1. Visual Studio projenizi oluşturmak için şablon kullanır. Visual Basic konsol uygulaması şablonu .NET Core için otomatik olarak bir sınıf tanımlar `Program`, tek bir yöntem ile `Main`, alan bir <xref:System.String> bağımsız değişken olarak bir dizi. `Main`Uygulama giriş noktası, uygulama başlatıldığında otomatik olarak çalışma zamanı tarafından çağrılan yöntemi niteliğindedir. Uygulama başlatıldığında sağlanan tüm komut satırı bağımsız değişkenleri kullanılabilir *args* dizi.

   ![Visual Studio ve yeni HelloWorld projesi](./media/vb-with-visual-studio/devenv.png)

   Şablon, basit bir "Hello World" uygulaması oluşturur. Çağırır <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> değişmez değer dize "Hello World!" görüntülenecek yöntemi Konsol penceresinde. Seçerek **HelloWorld** düğmesi araç çubuğundaki yeşil ok ile hata ayıklama modunda program çalışabilir. Bunu yaparsanız, kapanmadan önce konsol penceresi yalnızca kısa zaman aralığı için görünür olur. Bu kaynaklanır `Main` yöntemi sonlandırır ve uygulama sona tek deyiminde olan en kısa sürede `Main` yöntemini yürütür.

1. Konsol penceresinde kapanmadan önce duraklatmak uygulamanın neden için çağırdıktan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   Bu kod, kullanıcıdan herhangi bir tuşa basın ve bir tuşuna basılana kadar program duraklatılır.

1. Menü çubuğunda seçin **yapı** > **yapı çözümü**. Tam zamanında (JIT) derleyici tarafından ikili koda dönüştürülür bir ara dile (IL) programınızı derler.

1. Seçerek program Çalıştır **HelloWorld** araç çubuğundaki Yeşil oklu düğmesi.

   ![Devam etmek için herhangi bir tuşa Hello World tuşuna gösteren konsol penceresi](./media/with-visual-studio/helloworld1.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="enhancing-the-hello-world-application"></a>Hello World uygulamasının geliştirme

Kendi adı için kullanıcıya sor ve tarih ve saati ile birlikte görüntülemek için uygulamanızı geliştirin. Program sınamak ve değiştirmek için aşağıdakileri yapın:

1. Aşağıdaki Visual Basic kodu code penceresinde aşağıdaki hemen ayraç sonra girin `Sub Main(args As String())` satır ve ilk ayraç önce:

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Bu kod varolan değiştirir <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, ve <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> deyimleri.

   ![Güncelleştirilmiş Main yöntemi ile Visual Studio Program dosyası](./media/vb-with-visual-studio/codewindow.png)

   Bu kodu ", adı nedir?" görüntüler Kullanıcı kadar bekler ve konsol penceresi Enter tuşuna bir dize girer. Bu dize adlı bir değişkende depolar `name`. Ayrıca değerini alır <xref:System.DateTime.Now?displayProperty=nameWithType> geçerli yerel saat içeren ve adlı bir değişkene atar özelliği `currentDate`. Son olarak, kullanan bir [Ara değerli dize](../../csharp/language-reference/keywords/interpolated-strings.md) konsol penceresinde bu değerleri görüntülemek için.

1. Program seçerek derleme **yapı** > **yapı çözümü**.

1. Araç çubuğundaki yeşil ok tuşunu seçerek, F5 tuşuna basarak veya belirleyerek Visual Studio'da hata ayıklama modunda programı çalıştırın **hata ayıklama** > **hata ayıklamayı Başlat** menü öğesi. Bir ad girin ve Enter tuşuna basarak komutuna yanıt.

   ![Değiştirilen program çıkış konsol penceresi](./media/with-visual-studio/helloworld2.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

Oluşturulan artık ve uygulamanızı çalıştırın. Profesyonel bir uygulama geliştirmek için uygulamanızı sürüm için hazır hale getirmek için bazı ek adımlar uygulayın:

- Uygulamanızın hatalarını ayıklama hakkında daha fazla bilgi için bkz: [C# Hello World uygulamanızı Visual Studio 2017 ile hata ayıklama](debugging-with-visual-studio.md).

- Geliştirme ve uygulamanızın dağıtılabilir sürümünü yayımlama hakkında daha fazla bilgi için bkz: [C# Hello World uygulamanızla Visual Studio 2017 yayımlama](publishing-with-visual-studio.md).

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
