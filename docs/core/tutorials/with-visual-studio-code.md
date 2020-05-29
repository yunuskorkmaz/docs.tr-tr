---
title: Visual Studio Code kullanarak .NET Core ile bir konsol uygulaması oluşturma
description: Visual Studio Code ve .NET Core CLI kullanarak .NET Core konsol uygulaması oluşturmayı öğrenin.
ms.date: 05/22/2020
ms.openlocfilehash: 673c4a639a2cab26261b7cdafd5d8e20acfafb94
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201702"
---
# <a name="tutorial-create-a-console-application-with-net-core-using-visual-studio-code"></a>Öğretici: Visual Studio Code kullanarak .NET Core ile bir konsol uygulaması oluşturma

Bu öğreticide, Visual Studio Code ve .NET Core CLI kullanılarak .NET Core konsol uygulaması oluşturma ve çalıştırma gösterilmektedir. Proje oluşturma, derleme ve çalıştırma gibi proje görevleri CLı kullanılarak yapılır, bu nedenle bu öğreticiyi bir kod Düzenleyicisi ile izleyebilir ve tercih ediyorsanız komutları terminalde çalıştırabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

1. [C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yüklü [Visual Studio Code](https://code.visualstudio.com/) . Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).
2. [.NET Core 3,1 SDK veya üzeri](https://dotnet.microsoft.com/download)

## <a name="create-the-app"></a>Uygulama oluşturma

1. Visual Studio Code'u açın.

1. Bir proje oluşturun.

   1. **Dosya**  >  **Aç klasör**aç... ' ı seçin, / **Open...** ana menüden bir *HelloWorld* klasörü oluşturun ve klasör aç **Seç**' e tıklayın / **Open**.

      Klasör adı, varsayılan olarak proje adı ve ad alanı adı olur. Daha sonra, proje ad alanının olduğunu varsayan öğreticide kod ekleyeceksiniz `HelloWorld` .

   1. Ana menüden **Terminal görünümü ' nu** seçerek **View**Visual Studio Code açın  >  **Terminal** .

      **Terminal** , *HelloWorld* klasöründe komut istemiyle açılır.

   1. **Terminalde**aşağıdaki komutu girin:

      ```dotnetcli
      dotnet new console
      ```

.NET Core konsol uygulaması şablonu, `Program` `Main` bağımsız değişken olarak bir dizi alan tek bir yöntemle bir sınıfını tanımlar <xref:System.String> . *Program.cs* dosyası aşağıdaki koda sahiptir:

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

`Main`uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir. Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.

Şablon, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> "Merhaba Dünya!" öğesini göstermek için yöntemi çağıran basit bir uygulama oluşturur. Konsol penceresinde.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

**Terminalde**aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet run
```

Program "Merhaba Dünya!" görüntülüyor ve bitiyor.

![DotNet Run komutu](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a>Uygulamayı geliştirin

Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.

1. Üzerine tıklayarak *program.cs* açın.

   Visual Studio Code bir C# dosyasını ilk açışınızda, [Omnisharp](https://www.omnisharp.net/) düzenleyicide yüklenir.

   ![Program.cs dosyasını açın](media/with-visual-studio-code/open-program-cs.png)

1. Visual Studio Code, uygulamanızda derlemek ve hata ayıklamak için eksik varlıkları eklemenizi istediğinizde **Evet** ' i seçin.

   ![Eksik varlıklar için istem](media/with-visual-studio-code/missing-assets.png)

1. `Main`Aşağıdaki kodla, şu anda yalnızca çağıran satırı olan *program.cs*içindeki yönteminin içeriğini değiştirin `Console.WriteLine` :

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   Bu kod "adınız nedir?" görüntüler Konsol penceresinde ve ardından **ENTER** tuşuna basarak Kullanıcı bir dize girene kadar bekler. Bu dizeyi adlı bir değişkende depolar `name` . Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene atar `date` . Son olarak, bu değerleri konsol penceresinde görüntüler.

   `\n`Bir yeni satır karakterini temsil eder.

   `$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır. İfade değeri, ifadenin yerine dizeye eklenir. Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.

1. Yaptığınız değişiklikleri kaydedin.

   > [!IMPORTANT]
   > Visual Studio Code, değişiklikleri açıkça kaydetmeniz gerekir. Visual Studio 'dan farklı olarak, bir uygulamayı derleyip çalıştırdığınızda dosya değişiklikleri otomatik olarak kaydedilmez.

1. Programı yeniden çalıştırın:

   ```dotnetcli
   dotnet run
   ```

1. Bir ad girip **ENTER** tuşuna basarak istemi yanıtlayın.

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Değiştirilen program çıkışındaki Terminal penceresi":::

1. Programdan çıkmak için herhangi bir tuşa basın.

## <a name="additional-resources"></a>Ek kaynaklar

- [Visual Studio Code ayarlama](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir .NET Core uygulaması oluşturdunuz. Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.

> [!div class="nextstepaction"]
> [Visual Studio Code kullanarak bir .NET Core konsol uygulamasında hata ayıklama](debugging-with-visual-studio-code.md)
