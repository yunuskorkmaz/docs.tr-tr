---
title: .NET Core ve C# Visual Studio 2017'Hello World uygulaması oluşturma
description: Basit bir .NET Core konsol uygulaması Visual Studio 2017 kullanarak C# ile oluşturmayı öğrenin.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.openlocfilehash: d68ae899e5dc7c37a9c92e79aeae452b000b0960
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="build-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>Bir C# Hello World uygulamasının Visual Studio 2017 .NET çekirdek ile derleme

Bu konuda oluşturma, hata ayıklama ve C# Visual Studio 2017 kullanarak basit bir .NET Core konsol uygulaması yayımlama için adım adım bir giriş sağlar. Visual Studio 2017 .NET Core uygulamaları oluşturmak için bir tam özellikli bir geliştirme ortamı sağlar. Uygulama platforma özgü bağımlılıklar yok sürece, uygulama .NET Core hedefleyen herhangi bir platformda çalışabilir ve .NET Core sahip herhangi bir sisteminde yüklü.

## <a name="prerequisites"></a>Önkoşullar

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) yüklü ".NET Core platformlar arası geliştirme" iş yükü ile. .NET Core 1.1 veya .NET Core 2.0 ile uygulamanızı geliştirebilirsiniz.

Daha fazla bilgi için bkz: [.NET Core Windows önkoşulları](../../core/windows-prerequisites.md) konu.

## <a name="a-simple-hello-world-application"></a>Basit bir Hello World uygulamasının

Basit bir "Hello World" konsol uygulaması oluşturarak başlayın. Aşağıdaki adımları uygulayın:

1. Visual Studio 2017 başlatın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde *yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna, "HelloWorld" yazın. Seçin **Tamam** düğmesi.

   ![Konsol seçilen uygulama ile yeni proje iletişim kutusu](./media/with-visual-studio/newproject.png)
   
1. Visual Studio projenizi oluşturmak için şablon kullanır. .NET Core için C# konsol uygulaması şablonu otomatik olarak bir sınıf tanımlar `Program`, tek bir yöntem ile `Main`, alan bir <xref:System.String> bağımsız değişken olarak bir dizi. `Main` Uygulama giriş noktası, uygulama başlatıldığında otomatik olarak çalışma zamanı tarafından çağrılan yöntemi niteliğindedir. Uygulama başlatıldığında sağlanan tüm komut satırı bağımsız değişkenleri kullanılabilir *args* dizi.

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/devenv.png)

   Şablon, basit bir "Hello World" uygulaması oluşturur. Çağırır <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> değişmez değer dize "Hello World!" görüntülenecek yöntemi Konsol penceresinde. Seçerek **HelloWorld** düğmesi araç çubuğundaki yeşil ok ile hata ayıklama modunda program çalışabilir. Bunu yaparsanız, kapanmadan önce konsol penceresi yalnızca kısa zaman aralığı için görünür olur. Bu kaynaklanır `Main` yöntemi sonlandırır ve uygulama sona tek deyiminde olan en kısa sürede `Main` yöntemini yürütür.

1. Konsol penceresinde kapanmadan önce duraklatmak uygulamanın neden için çağırdıktan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   Bu kod, kullanıcıdan herhangi bir tuşa basın ve bir tuşuna basılana kadar program duraklatılır.

1. Menü çubuğunda seçin **yapı** > **yapı çözümü**. Tam zamanında (JIT) derleyici tarafından ikili koda dönüştürülür bir ara dile (IL) programınızı derler.

1. Seçerek program Çalıştır **HelloWorld** araç çubuğundaki Yeşil oklu düğmesi.

   ![Devam etmek için herhangi bir tuşa Hello World tuşuna gösteren konsol penceresi](./media/with-visual-studio/helloworld1.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="enhancing-the-hello-world-application"></a>Hello World uygulamasının geliştirme

Kullanıcıdan adına ve tarih ve saati ile birlikte görüntülemek için uygulamanızı geliştirin. Program sınamak ve değiştirmek için aşağıdakileri yapın:

1. Aşağıdaki C# kodu code penceresinde aşağıdaki hemen ayraç sonra girin `static void Main(string[] args)` satır ve ilk ayraç önce:

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Bu kod varolan değiştirir <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, ve <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> deyimleri.

   ![Visual Studio Program c-sharp dosyasını güncelleştirilmiş Main yöntemi](./media/with-visual-studio/codewindow.png)

   Bu kodu ", adı nedir?" görüntüler Kullanıcı kadar bekler ve konsol penceresi Enter tuşuna bir dize girer. Bu dize adlı bir değişkende depolar `name`. Ayrıca değerini alır <xref:System.DateTime.Now?displayProperty=nameWithType> geçerli yerel saat içeren ve adlı bir değişkene atar özelliği `date`. Son olarak, kullanan bir [Ara değerli dize](../../csharp/language-reference/tokens/interpolated.md) konsol penceresinde bu değerleri görüntülemek için.

1. Program seçerek derleme **yapı** > **yapı çözümü**.

1. Araç çubuğundaki yeşil ok tuşunu seçerek, F5 tuşuna basarak veya belirleyerek Visual Studio'da hata ayıklama modunda programı çalıştırın **hata ayıklama** > **hata ayıklamayı Başlat** menü öğesi. Bir ad girin ve Enter tuşuna basarak komutuna yanıt.

   ![Değiştirilen program çıkış konsol penceresi](./media/with-visual-studio/helloworld2.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

Oluşturulan artık ve uygulamanızı çalıştırın. Profesyonel bir uygulama geliştirmek için uygulamanızı sürüm için hazır hale getirmek için bazı ek adımlar uygulayın:

- Uygulamanızın hatalarını ayıklama hakkında daha fazla bilgi için bkz: [C# Hello World uygulamanızı Visual Studio 2017 ile hata ayıklama](debugging-with-visual-studio.md).

- Geliştirme ve uygulamanızın dağıtılabilir sürümünü yayımlama hakkında daha fazla bilgi için bkz: [C# Hello World uygulamanızla Visual Studio 2017 yayımlama](publishing-with-visual-studio.md).

## <a name="related-topics"></a>İlgili konular

Bir konsol uygulaması yerine bir sınıf kitaplığı .NET Core ve Visual Studio 2017 ile de oluşturabilirsiniz. Adım adım bir giriş için bkz [oluşturma C# ve Visual Studio 2017 .NET çekirdek sınıf kitaplığına](library-with-visual-studio.md).

Mac, Linux ve Windows .NET Core konsol uygulaması kullanarak da geliştirebilirsiniz [Visual Studio Code](https://code.visualstudio.com/), indirilebilir Kod Düzenleyicisi. Adım adım bir öğretici için bkz: [Visual Studio Code ile çalışmaya başlama](with-visual-studio-code.md).
