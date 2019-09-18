---
title: Visual Studio C# 2017 ' de .NET Core ile Merhaba Dünya uygulaması oluşturma
description: Visual Studio 2017 C# kullanarak basit bir .NET Core konsol uygulaması derlemeyi öğrenin.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: b42a71993cb120c88b90e867b7af23873b99d280
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039590"
---
# <a name="build-a-c-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Visual Studio C# 2017 ' de .NET Core SDK Merhaba Dünya uygulama oluşturma

Bu konuda, Visual Studio 2017 ' de kullanarak C# basit bir .NET Core konsol uygulaması oluşturmaya, hata ayıklamanıza ve yayımlamaya yönelik adım adım bir giriş sunulmaktadır. Visual Studio 2017, .NET Core uygulamaları oluşturmak için tam özellikli bir geliştirme ortamı sağlar. Uygulama platforma özgü bağımlılıklara sahip olmadığı sürece, uygulama .NET Core 'un hedeflediği tüm platformlarda ve .NET Core yüklü olan herhangi bir sistemde çalışabilir.

## <a name="prerequisites"></a>Önkoşullar

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ".NET Core platformlar arası geliştirme" iş yükü yüklendi. Uygulamanızı .NET Core 2,1 veya sonraki sürümleriyle geliştirebilirsiniz.

Daha fazla bilgi için bkz. [Windows üzerinde .NET Core önkoşulları](../windows-prerequisites.md) .

## <a name="a-simple-hello-world-application"></a>Basit bir Merhaba Dünya uygulaması

Basit bir "Merhaba Dünya" konsol uygulaması oluşturarak başlayın. Aşağıdaki adımları uygulayın:

1. Visual Studio 2017 ' i başlatın. Menü çubuğundan **Dosya** > **Yeni** > **Proje** ' yi seçin. *Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin. Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin. **Ad** metin kutusuna "HelloWorld" yazın. **Tamam** düğmesini seçin.

   ![Konsol uygulaması seçiliyken yeni proje iletişim kutusu](./media/with-visual-studio/visual-studio-new-project.png)

1. Visual Studio, projenizi oluşturmak için şablonu kullanır. .Net C# Core konsol uygulaması şablonu, bağımsız değişken olarak bir `Program` <xref:System.String> dizi alan tek bir yöntemle `Main`bir sınıfını otomatik olarak tanımlar. `Main`uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir. Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/visual-studio-main-window.png)

   Şablon basit bir "Merhaba Dünya" uygulaması oluşturur. "Merhaba Dünya! <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> " değişmez dizesini göstermek için yöntemini çağırır Konsol penceresinde. Araç çubuğunda yeşil oklu **HelloWorld** düğmesini seçerek programı hata ayıklama modunda çalıştırabilirsiniz. Bunu yaparsanız, konsol penceresi kapanmadan önce yalnızca kısa bir zaman aralığı için görünür olur. Bu durum, yöntemin `Main` sonlandırdığı ve `Main` yöntemin bir tek deyimin yürütüldüğü anda sona erdiği için oluşur.

1. Uygulamanın konsol penceresini kapatmadan önce duraklatılmasına neden olmak için, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu ekleyin:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```

   Bu kod, kullanıcıdan herhangi bir tuşa basması ve bir tuşa basılana kadar programı duraklayacağını ister.

1. Menü çubuğunda Build**Build Solution**öğesini **seçin.**  >  Bu, programınızı bir tam zamanında (JıT) derleyicisi tarafından ikili koda dönüştürülen bir ara dile (IL) derler.

1. Araç çubuğunda yeşil oklu **HelloWorld** düğmesini seçerek programı çalıştırın.

   ![Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="enhancing-the-hello-world-application"></a>Merhaba Dünya uygulamasını geliştirme

Uygulamanızı, adını ve Tarih ve saat ile birlikte göstermek için kullanıcıyı geliştirin. Programı değiştirmek ve test etmek için aşağıdakileri yapın:

1. Aşağıdaki C# kodu, `static void Main(string[] args)` satırı izleyen açılış ayracından hemen sonra ve ilk kapanış parantezinden önce kod penceresine girin:

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Bu kod, `Main` yönteminin içeriğini değiştirir.

   ![Visual Studio program c-güncelleştirilmiş Main yöntemiyle diyez dosyası](./media/with-visual-studio/visual-csharp-code-window.png)

   Bu kod "adınız nedir?" görüntüler Konsol penceresinde ve ardından ENTER tuşuna basarak Kullanıcı bir dize girene kadar bekler. Bu dizeyi adlı `name`bir değişkende depolar. Ayrıca, geçerli yerel saati içeren <xref:System.DateTime.Now?displayProperty=nameWithType> özelliğinin değerini alır ve bunu adlı `date`bir değişkene atar. Son olarak, bu değerleri konsol penceresinde göstermek için bir [enterpolasyonlu dize](../../csharp/language-reference/tokens/interpolated.md) kullanır.

1. Build**Build Solution** **öğesini seçerek** > programı derleyin.

1. Araç çubuğundan yeşil oku seçerek, F5 tuşuna basarak veya **hata** > ayıklama**başlatma hata ayıklamayı Başlat** menü öğesini seçerek programı Visual Studio 'daki hata ayıklama modunda çalıştırın. Bir ad girip ENTER tuşuna basarak istemi yanıtlayın.

   ![Değiştirilen program çıkışıyla konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

Uygulamanızı oluşturdunuz ve çalıştırdık. Profesyonel bir uygulama geliştirmek için uygulamanızı yayın için hazırlamak üzere bazı ek adımlar gerçekleştirin:

- Uygulamanızda hata ayıklama hakkında bilgi için bkz. [Visual Studio 2017 kullanarak .NET Core Merhaba Dünya uygulamanızda hata ayıklama](debugging-with-visual-studio.md).

- Uygulamanızın dağıtılabilir bir sürümünü geliştirme ve yayımlama hakkında bilgi için bkz. [Visual Studio 2017 ile .NET Core Merhaba Dünya uygulamanızı yayımlama](publishing-with-visual-studio.md).

## <a name="related-topics"></a>İlgili konular

Konsol uygulaması yerine, .NET Core ve Visual Studio 2017 ile bir sınıf kitaplığı da oluşturabilirsiniz. Adım adım bir giriş için bkz. [Visual Studio 2017 ' de .NET Core ile C# bir sınıf kitaplığı oluşturma](library-with-visual-studio.md).

Ayrıca, indirilebilir bir kod Düzenleyicisi [Visual Studio Code](https://code.visualstudio.com/)kullanarak Mac, Linux ve Windows üzerinde bir .NET Core konsol uygulaması da geliştirebilirsiniz. Adım adım bir öğretici için bkz. [Visual Studio Code kullanmaya başlama](with-visual-studio-code.md).
