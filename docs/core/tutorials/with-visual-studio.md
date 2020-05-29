---
title: Visual Studio 'da .NET Core ile bir konsol uygulaması oluşturma
description: Visual Studio kullanarak C# veya Visual Basic .NET Core konsol uygulaması oluşturmayı öğrenin.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 9c3456cd8c940e53e8a70c1d3a7c3b09de77c21d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201593"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a>Öğretici: Visual Studio 2019 'de .NET Core konsol uygulaması oluşturma

Bu öğreticide, Visual Studio 2019 ' de .NET Core konsol uygulaması oluşturma ve çalıştırma gösterilmektedir.

## <a name="prerequisites"></a>Ön koşullar

- **.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,6 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) . .NET Core 3,1 SDK 'Sı, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.

  Daha fazla bilgi için, [.NET Core SDK](../install/sdk.md?pivots=os-windows) makalesine [Visual Studio ile install](../install/sdk.md?pivots=os-windows#install-with-visual-studio) bölümüne bakın.

## <a name="create-the-app"></a>Uygulama oluşturma

<!-- markdownlint-disable MD025 -->

1. Visual Studio 2019 ' i açın.

1. "HelloWorld" adlı yeni bir .NET Core konsol uygulaması projesi oluşturun.

   1. Başlangıç sayfasında **Yeni proje oluştur**' u seçin.

      ![Visual Studio başlangıç sayfasında yeni bir proje oluştur düğmesi seçili](./media/with-visual-studio/start-window.png)

   1. **Yeni proje oluştur** sayfasında, arama kutusuna **konsol** girin. Ardından, dil listesinden **C#** veya **Visual Basic** ' yi seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin. **Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

      ![Filtreler seçiliyken yeni bir proje penceresi oluştur](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > .NET Core şablonlarını görmüyorsanız, muhtemelen gerekli iş yükünün eksik olması gerekir. **Aradığınızı bulmuyor musunuz?** iletisi altında, **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. Visual Studio Yükleyicisi açılır. **.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğundan emin olun.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **HelloWorld** girin. Ardından **Oluştur**’u seçin.

      ![Yeni proje pencerenizi proje adı, konum ve çözüm adı alanlarıyla yapılandırın](./media/with-visual-studio/configure-new-project.png)

   .NET Core konsol uygulaması şablonu, `Program` `Main` bağımsız değişken olarak bir dizi alan tek bir yöntemle bir sınıfını tanımlar <xref:System.String> . `Main`uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir. Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.

   Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.

   ```csharp
   using System;

   namespace HelloWorld
   {
       class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   Şablon basit bir "Merhaba Dünya" uygulaması oluşturur. <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>"Merhaba Dünya!" öğesini göstermek için yöntemini çağırır Konsol penceresinde.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Programı çalıştırmak için araç çubuğunda **HelloWorld** ' ı seçin veya **F5**tuşuna basın.

   ![HelloWorld Run düğmesinin seçili olduğu Visual Studio araç çubuğu](./media/with-visual-studio/run-program.png)

   Bir konsol penceresi "Merhaba Dünya!" metniyle açılıyor ekranda ve bazı Visual Studio hata ayıklama bilgilerinde yazdırılır.

   ![Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="enhance-the-app"></a>Uygulamayı geliştirin

Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin. Aşağıdaki yönergeler uygulamayı değiştirip yeniden çalıştırır:

1. `Main`Aşağıdaki kod ile Şu anda yalnızca çağıran satırı olan yönteminin içeriğini değiştirin `Console.WriteLine` :

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="Snippet1":::

   Bu kod "adınız nedir?" görüntüler Konsol penceresinde ve ardından ENTER tuşuna basarak Kullanıcı bir dize girene kadar bekler. Bu dizeyi adlı bir değişkende depolar `name` . Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene `date` ( `currentDate` Visual Basic) atar. Son olarak, bu değerleri konsol penceresinde görüntüler.

   `\n`( `vbCrLf` Visual Basic), bir yeni satır karakterini temsil eder.

   `$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır. İfade değeri, ifadenin yerine dizeye eklenir. Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.

1. Programı çalıştırmak için araç çubuğunda **HelloWorld** ' ı seçin veya **F5**tuşuna basın.

1. Bir ad girip **ENTER** tuşuna basarak istemi yanıtlayın.

   ![Değiştirilen program çıkışıyla konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir .NET Core uygulaması oluşturdunuz. Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.

> [!div class="nextstepaction"]
> [Visual Studio 'da bir .NET Core konsol uygulamasında hata ayıklama](debugging-with-visual-studio.md)
