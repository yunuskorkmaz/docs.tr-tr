---
title: Visual Studio kullanarak bir .NET konsol uygulaması oluşturma
description: Visual Studio kullanarak C# veya Visual Basic .NET konsol uygulaması oluşturmayı öğrenin.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 3986ef4083b964799be33d2876570ac4cf2082b8
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511859"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio"></a>Öğretici: Visual Studio kullanarak bir .NET konsol uygulaması oluşturma

Bu öğreticide, Visual Studio 2019 ' de bir .NET konsol uygulamasının nasıl oluşturulacağı ve çalıştırılacağı gösterilmektedir.

## <a name="prerequisites"></a>Önkoşullar

- **.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,8 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) . .NET 5,0 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.

  Daha fazla bilgi için bkz. [Visual Studio ile .NET SDK 'Yı yükler](../install/windows.md#install-with-visual-studio).

## <a name="create-the-app"></a>Uygulama oluşturma

"HelloWorld" adlı bir .NET konsol uygulaması projesi oluşturun.

1. Visual Studio 2019’u başlatın.

1. **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Önizleme özellikleri**' ni seçin ve ardından **Yeni projede tüm .NET Core şablonlarını göster ' i seçin (yeniden başlatma gerektirir)**.

   :::image type="content" source="media/with-visual-studio/dotnet-options.png" alt-text="Tüm .NET şablonları seçeneğini göster":::

1. Visual Studio 'Yu kapatın ve yeniden açın.

1. Başlangıç sayfasında **Yeni proje oluştur**' u seçin.

   :::image type="content" source="./media/with-visual-studio/start-window.png" alt-text="Visual Studio başlangıç sayfasında yeni bir proje oluştur düğmesi seçili":::

1. **Yeni proje oluştur** sayfasında, arama kutusuna **konsol** girin. Ardından, dil listesinden **C#** veya **Visual Basic** ' yi seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin. **Konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="./media/with-visual-studio/create-new-project.png" alt-text="Filtreler seçiliyken yeni bir proje penceresi oluştur":::

   > [!TIP]
   > .NET şablonlarını görmüyorsanız, muhtemelen gerekli iş yükü eksik olabilir. **Aradığınızı bulmuyor musunuz?** iletisi altında, **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. Visual Studio Yükleyicisi açılır. **.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğundan emin olun.

1. **Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı** kutusuna **HelloWorld** yazın. Ardından **İleri**' yi seçin.

   :::image type="content" source="./media/with-visual-studio/configure-new-project.png" alt-text="Yeni proje pencerenizi proje adı, konum ve çözüm adı alanlarıyla yapılandırın":::

1. **Ek bilgi** iletişim kutusunda **.NET 5,0 (geçerli)** öğesini seçin ve ardından **Oluştur**' u seçin.

   :::image type="content" source="media/with-visual-studio/additional-info.png" alt-text="Ek bilgi iletişim kutusu":::

Şablon basit bir "Merhaba Dünya" uygulaması oluşturur. <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>"Merhaba Dünya!" öğesini göstermek için yöntemini çağırır Konsol penceresinde.

Şablon kodu, `Program` `Main` bağımsız değişken olarak bir diziyi alan tek bir yöntemi olan sınıfını tanımlar <xref:System.String> :

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

`Main` uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir. Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.

Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. <kbd></kbd> + Programı hata ayıklamadan çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.

   Bir konsol penceresi "Merhaba Dünya!" metniyle açılıyor ekranda yazdırılır.

   :::image type="content" source="./media/with-visual-studio/hello-world-console.png" alt-text="Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi":::

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="enhance-the-app"></a>Uygulamayı geliştirin

Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.

1. *Program.cs* veya *program. vb*' de, yönteminin içeriğini, `Main` çağıran satırı, `Console.WriteLine` aşağıdaki kodla değiştirin:

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   Bu kod, konsol penceresinde bir istem görüntüler ve ardından <kbd>ENTER</kbd> tuşuna basarak Kullanıcı bir dize girene kadar bekler. Bu dizeyi adlı bir değişkende depolar `name` . Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene `date` ( `currentDate` Visual Basic) atar. Bu değerleri konsol penceresinde görüntüler. Son olarak, konsol penceresinde bir istem görüntüler ve <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> Kullanıcı girişini beklemek için yöntemini çağırır.

   <xref:System.Environment.NewLine> , bir satır kesmeyi göstermek için platformdan bağımsız ve dilden bağımsız bir yoldur. Alternatifler `\n` C# ve `vbCrLf` Visual Basic ' de bulunur.

   `$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır. İfade değeri, ifadenin yerine dizeye eklenir. Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.

1. <kbd></kbd> + Programı hata ayıklamadan çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.

1. Bir ad girip <kbd>ENTER</kbd> tuşuna basarak istemi yanıtlayın.

   :::image type="content" source="./media/with-visual-studio/hello-world-update.png" alt-text="Değiştirilen program çıkışıyla konsol penceresi":::

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

## <a name="additional-resources"></a>Ek kaynaklar

- [Geçerli yayınlar ve uzun süreli destek yayınları](../releases-and-support.md#net-core-and-net-5-version-lifecycles)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir .NET konsol uygulaması oluşturdunuz. Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.

> [!div class="nextstepaction"]
> [Visual Studio kullanarak bir .NET konsol uygulamasında hata ayıklama](debugging-with-visual-studio.md)
