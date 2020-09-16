---
title: Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması oluşturma
description: Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması oluşturmayı öğrenin.
ms.date: 06/02/2020
ms.openlocfilehash: ca933bc9322109ba7d1f808fcc44696a9766a6d4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537606"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-for-mac"></a>Öğretici: Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması oluşturma

Bu öğreticide Mac için Visual Studio kullanarak bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve çalıştırılacağı gösterilmektedir.

> [!NOTE]
> Geri bildiriminiz çok değerli. Mac için Visual Studio üzerinde geliştirme ekibine geri bildirimde bulunmak için kullanabileceğiniz iki yol vardır:
>
> * Mac için Visual Studio, **Help**  >  menüden**sorun bildir** veya hoş geldiniz ekranından **sorun** bildir ' i seçerek bir hata raporu dosyalayarak bir pencere açar. Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.
> * Öneride bulunmak için, **Help**  >  menüden**bir öneri sağlayın** veya hoş geldiniz ekranından bir öneri **Provide a Suggestion** sağlayın. Bu işlem sizi [Mac için Visual Studio Geliştirici topluluğu Web sayfasına](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)götürür.

## <a name="prerequisites"></a>Önkoşullar

* [Sürüm 8,6 veya üzeri Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). .NET Core ' u yüklemek için seçeneği belirleyin. .NET Core geliştirmesi için Xamarin 'in yüklenmesi isteğe bağlıdır. Daha fazla bilgi için aşağıdaki kaynaklara bakın:

  * [Öğretici: Mac için Visual Studio yüklemesi](/visualstudio/mac/installation).
  * [Desteklenen macOS sürümleri](../install/windows.md).
  * [Mac için Visual Studio tarafından desteklenen .NET Core sürümleri](/visualstudio/mac/net-core-support).

## <a name="create-the-app"></a>Uygulama oluşturma

"HelloWorld" adlı bir .NET Core konsol uygulaması projesi oluşturun.

1. Mac için Visual Studio başlatın.

1. Başlangıç penceresinde **Yeni** ' yi seçin.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Mac için Visual Studio başlangıç ekranında yeni düğme":::

1. **Yeni proje** Iletişim kutusunda **Web ve konsol** düğümü altında **uygulama** ' yı seçin. **Konsol uygulaması** şablonunu seçin ve **İleri**' yi seçin.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="Yeni proje şablonları listesi":::

1. **Yeni konsol uygulamanızı yapılandırma** Iletişim kutusunun **hedef çerçeve** açılır penceresinde, **.NET Core 3,1**' ı seçin ve **İleri**' yi seçin.

   :::image type="content" source="media/with-visual-studio-mac/target-framework.png" alt-text="Hedef Framework 'Ü seçin":::

1. **Proje adı**Için "HelloWorld" yazın ve **Oluştur**' u seçin.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="Yeni konsol uygulamanızı yapılandırma iletişim kutusu":::

Şablon basit bir "Merhaba Dünya" uygulaması oluşturur. <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>"Merhaba Dünya!" öğesini göstermek için yöntemini çağırır , Terminal penceresinde.

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

`Main` uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir. Uygulama başlatıldığında sağlanan tüm komut satırı bağımsız değişkenleri `args` dizide kullanılabilir.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> <kbd>option</kbd> + <kbd>command</kbd> + Uygulamayı hata ayıklamadan çalıştırmak için ⌥ ⌘ ↵ (Option komut<kbd>ENTER</kbd>) tuşuna basın.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="Terminal Merhaba Dünya gösterir!":::

1. **Terminal** penceresini kapatın.

## <a name="enhance-the-app"></a>Uygulamayı geliştirin

Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.

1. *Program.cs*' de, `Main` aşağıdaki kodla birlikte çağıran satırı olan yönteminin içeriğini değiştirin `Console.WriteLine` :

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   Bu kod, konsol penceresinde bir istem görüntüler ve ardından <kbd>ENTER</kbd> tuşuna basarak Kullanıcı bir dize girene kadar bekler. Bu dizeyi adlı bir değişkende depolar `name` . Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene atar `date` . Bu değerleri konsol penceresinde görüntüler. Son olarak, konsol penceresinde bir istem görüntüler ve <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> Kullanıcı girişini beklemek için yöntemini çağırır.

   `\n`Bir yeni satır karakterini temsil eder.

   `$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır. İfade değeri, ifadenin yerine dizeye eklenir. Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.

1. Uygulamayı çalıştırmak için <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>seçenek</kbd> + <kbd>komut</kbd> + <kbd>ENTER</kbd>) tuşuna basın.

1. Bir ad girip <kbd>ENTER</kbd>tuşuna basarak istemi yanıtlayın.

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="Terminal değiştirilen program çıktısını gösterir":::

1. Terminali kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir .NET Core konsol uygulaması oluşturdunuz. Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.

> [!div class="nextstepaction"]
> [Mac için Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklama](debugging-with-visual-studio-mac.md)
