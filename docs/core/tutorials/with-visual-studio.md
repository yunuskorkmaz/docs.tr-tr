---
title: Visual Studio C# 2017 ' de .NET Core ile Merhaba Dünya uygulaması oluşturma
description: Visual Studio 2017 C# kullanarak basit bir .NET Core konsol uygulaması derlemeyi öğrenin.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: cc7d78006998b79fe9d522e71883ce1af817c051
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428555"
---
# <a name="build-a-c-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Visual Studio C# 2017 ' de .NET Core SDK Merhaba Dünya uygulama oluşturma

Bu makalede, Visual Studio 2017 ' de kullanarak C# basit bir .NET Core konsol uygulaması oluşturmaya, hata ayıklamanıza ve yayımlamaya yönelik adım adım bir giriş sunulmaktadır. Visual Studio 2017, .NET Core uygulamaları oluşturmak için tam özellikli bir geliştirme ortamı sağlar. Uygulama platforma özgü bağımlılıklara sahip olmadığı sürece, uygulama .NET Core 'un hedeflediği tüm platformlarda ve .NET Core yüklü olan herhangi bir sistemde çalışabilir.

## <a name="prerequisites"></a>Önkoşullar

".NET Core platformlar arası geliştirme" iş yükü yüklü olan [Visual Studio 2017 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) . Uygulamanızı .NET Core 2,1 veya sonraki sürümleriyle geliştirebilirsiniz.

Daha fazla bilgi için bkz. [.NET Core bağımlılıklar ve gereksinimler](../install/sdk.md?tabs=netcore30&pivots=os-windows#install-with-visual-studio)makalesi.

## <a name="a-simple-hello-world-application"></a>Basit bir Merhaba Dünya uygulaması

Basit bir "Merhaba Dünya" konsol uygulaması oluşturarak başlayın. Şu adımları uygulayın:

1. Visual Studio'yu başlatın. Menü çubuğundan **dosya** > **Yeni** > **projesi** öğesini seçin. **Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin. Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin. **Ad** metin kutusuna "HelloWorld" yazın. **Tamam** düğmesini seçin.

   ![Konsol uygulaması seçiliyken yeni proje iletişim kutusu](./media/with-visual-studio/visual-studio-new-project.png)

1. Visual Studio, projenizi oluşturmak için şablonu kullanır. .NET C# Core konsol uygulaması şablonu, bağımsız değişken olarak <xref:System.String> dizisi alan `Main`tek bir yöntemle `Program`bir sınıfını otomatik olarak tanımlar. `Main`, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntem olan uygulama giriş noktasıdır. Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/visual-studio-main-window.png)

   Şablon basit bir "Merhaba Dünya" uygulaması oluşturur. "Merhaba Dünya!" değişmez dizesini göstermek için <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemini çağırır Konsol penceresinde. Araç çubuğunda yeşil oklu **HelloWorld** düğmesini seçerek programı hata ayıklama modunda çalıştırabilirsiniz. Bunu yaparsanız, konsol penceresi kapanmadan önce yalnızca kısa bir zaman aralığı için görünür olur. Bu durum `Main` yöntemi sonlandırıldığında ve `Main` yönteminde tek bir deyimin yürütüldüğü anda uygulamanın sona erdiği için oluşur.

1. Uygulamanın konsol penceresini kapatmadan önce duraklatılmasını sağlamak için, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu ekleyin:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```

   Bu kod, kullanıcıdan herhangi bir tuşa basması ve bir tuşa basılana kadar programı duraklayacağını ister.

1. Menü çubuğunda **derleme** > **Build Solution**' ı seçin. Bu, programınızı bir tam zamanında (JıT) derleyicisi tarafından ikili koda dönüştürülen bir ara dile (IL) derler.

1. Araç çubuğunda yeşil oklu **HelloWorld** düğmesini seçerek programı çalıştırın.

   ![Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="enhancing-the-hello-world-application"></a>Merhaba Dünya uygulamasını geliştirme

Uygulamanızı, adını ve Tarih ve saat ile birlikte göstermek için kullanıcıyı geliştirin. Programı değiştirmek ve test etmek için aşağıdakileri yapın:

1. `static void Main(string[] args)` satırını izleyen C# açılış ayracından hemen sonra ve ilk kapanış küme ayracından önce kod penceresine aşağıdaki kodu girin:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Bu kod `Main` yönteminin içeriğini değiştirir.

   ![Visual Studio program c-güncelleştirilmiş Main yöntemiyle diyez dosyası](./media/with-visual-studio/visual-csharp-code-window.png)

   Bu kod "adınız nedir?" görüntüler Konsol penceresinde ve ardından ENTER tuşuna basarak Kullanıcı bir dize girene kadar bekler. Bu dizeyi `name`adlı bir değişkende depolar. Ayrıca, geçerli yerel saati içeren <xref:System.DateTime.Now?displayProperty=nameWithType> özelliğinin değerini alır ve bunu `date`adlı bir değişkene atar. Son olarak, bu değerleri konsol penceresinde göstermek için bir [enterpolasyonlu dize](../../csharp/language-reference/tokens/interpolated.md) kullanır.

1. **Build** > **Build Solution**öğesini seçerek programı derleyin.

1. Araç çubuğundan yeşil oku seçerek, F5 tuşuna basarak **veya hata ayıklama > ** **Başlat** menü öğesini seçerek programı Visual Studio 'daki hata ayıklama modunda çalıştırın. Bir ad girip ENTER tuşuna basarak istemi yanıtlayın.

   ![Değiştirilen program çıkışıyla konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

Uygulamanızı oluşturdunuz ve çalıştırdık. Profesyonel bir uygulama geliştirmek için uygulamanızı yayın için hazırlamak üzere bazı ek adımlar gerçekleştirin:

- Uygulamanızda hata ayıklama hakkında bilgi için bkz. [Visual Studio 2017 kullanarak .NET Core Merhaba Dünya uygulamanızda hata ayıklama](debugging-with-visual-studio.md).

- Uygulamanızın dağıtılabilir bir sürümünü geliştirme ve yayımlama hakkında bilgi için bkz. [Visual Studio 2017 ile .NET Core Merhaba Dünya uygulamanızı yayımlama](publishing-with-visual-studio.md).

## <a name="related-articles"></a>İlgili makaleler

Konsol uygulaması yerine, .NET Core ve Visual Studio 2017 ile bir sınıf kitaplığı da oluşturabilirsiniz. Adım adım bir giriş için bkz. [Visual Studio 2017 ' de .NET Core ile C# bir sınıf kitaplığı oluşturma](library-with-visual-studio.md).

Ayrıca, indirilebilir bir kod Düzenleyicisi [Visual Studio Code](https://code.visualstudio.com/)kullanarak Mac, Linux ve Windows üzerinde bir .NET Core konsol uygulaması da geliştirebilirsiniz. Adım adım bir öğretici için bkz. [Visual Studio Code kullanmaya başlama](with-visual-studio-code.md).
