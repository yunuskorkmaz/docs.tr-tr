---
title: Mac için Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklama
description: Visual Studio Mac kullanarak bir .NET Core konsol uygulamasında hata ayıklamayı öğrenin.
ms.date: 06/08/2020
ms.openlocfilehash: 79936fb99d0bc37c1234eb8f227eb5415ae48b93
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867574"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a>Öğretici: Mac için Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklama

Bu öğreticide Mac için Visual Studio bulunan hata ayıklama araçları tanıtılmaktadır.

## <a name="prerequisites"></a>Önkoşullar

- Bu öğretici, [Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması oluşturma](with-visual-studio-mac.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.

## <a name="use-debug-build-configuration"></a>Hata ayıklama derleme yapılandırmasını kullan

*Hata ayıklama* ve *yayın* , Visual Studio 'nun yerleşik derleme yapılandırmalarıdır. Hata ayıklama oluşturma yapılandırması hata ayıklama için ve son sürüm dağıtımı için sürüm yapılandırması ' nı kullanırsınız.

Hata ayıklama yapılandırmasında, bir program tam sembolik hata ayıklama bilgileriyle derlenir ve iyileştirmesi yoktur. Kaynak kodu ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olduğundan iyileştirme, hata ayıklamayı karmaşıklaştırır. Bir programın yayın yapılandırmasında sembolik hata ayıklama bilgisi yoktur ve tamamen iyileştirilmiştir.

Varsayılan olarak, Visual Studio hata ayıklama derleme yapılandırmasını kullanır, bu nedenle hata ayıklamadan önce değiştirmeniz gerekmez.

1. Mac için Visual Studio başlatın.

1. [Mac için Visual Studio kullanarak .NET Core konsol uygulaması oluşturma](with-visual-studio-mac.md)bölümünde oluşturduğunuz projeyi açın.

   Geçerli derleme yapılandırması araç çubuğunda gösterilir. Aşağıdaki araç çubuğu görüntüsünde, Visual Studio 'nun uygulamanın hata ayıklama sürümünü derlemek üzere yapılandırıldığı gösterilmektedir:

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="Hata ayıklama vurgulanmış Visual Studio araç çubuğu":::

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

Kesme *noktası,* kesme noktası olan satır yürütülmeden önce uygulamanın yürütülmesini geçici olarak keser.

1. Ad, tarih ve saati gösteren satırda bir kesme noktası ayarlayın. Bunu yapmak için imleci kod satırına yerleştirin ve <kbd>⌘</kbd> <kbd>\\</kbd> (<kbd>komut</kbd>) tuşuna basın + <kbd>\\</kbd> . Bir kesme noktası ayarlamak için başka bir yol **Run**  >  da menüden**geçiş kesme noktası** Çalıştır ' i seçmektir.

   Visual Studio, kesme noktasının ayarlandığı çizgiyi gösterir ve sol kenar boşluğunda kırmızı bir nokta görüntüler.

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="Kesme noktası ayarlanmış Visual Studio program penceresi":::

1. <kbd>⌘</kbd><kbd>↵</kbd> <kbd>command</kbd> + Programı hata ayıklama modunda başlatmak için ⌘ ↵ (komut<kbd>ENTER</kbd>) tuşuna basın. Hata ayıklamayı başlatmak için başka bir yol **Run**  >  da, menüden**hata ayıklamayı Başlat** Çalıştır ' i seçmektir.

1. Program bir ad isteminde bulunduğunda Terminal penceresine bir dize girin ve ardından <kbd>ENTER</kbd>tuşuna basın.

1. Program yürütme, yöntemi yürütmeden önce kesme noktasına ulaştığında duraklar `Console.WriteLine` .

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Visual Studio 'da bir kesme noktasının ekran görüntüsü":::

## <a name="use-the-immediate-window"></a>Hemen penceresini kullanma

**Komut** penceresi, hata ayıklamanıza çalıştığınız uygulamayla etkileşime girebilmenizi sağlar. Programınızı nasıl etkilediğini görmek için değişkenlerin değerini etkileşimli olarak değiştirebilirsiniz.

1. **Hemen** penceresi görünür değilse, **View**  >  **hata ayıklama Pad**'i  >  **hemen**görüntüle ' yi seçerek bunu görüntüleyin.

1. `name = "Gracie"` **Hemen** penceresine girip <kbd>ENTER</kbd>tuşuna basın.

1. `date = date.AddDays(1)` **Hemen** penceresine girip <kbd>ENTER</kbd>tuşuna basın.

   **Komut** penceresi, dize değişkeninin yeni değerini ve değerin özelliklerini görüntüler <xref:System.DateTime> .

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Visual Studio 'da hemen penceresi":::

   **Yereller** penceresi, yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler. Yeni değiştirdiğiniz değişkenlerin değerleri **Locals** penceresinde güncellenir.

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Visual Studio 'da yerel öğeler penceresi":::

1. Hata <kbd>⌘</kbd>ayıklamaya devam etmek için ⌘<kbd>↵</kbd> (<kbd>komut</kbd> + <kbd>ENTER</kbd>) tuşuna basın.

   Terminalde görünen değerler, **komut** penceresinde yaptığınız değişikliklere karşılık gelir.

   Terminali görmüyorsanız, alt gezinti çubuğunda **Terminal-HelloWorld** ' i seçin.

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="Sol gezinti çubuğunda Terminal-Merhaba Dünya":::

1. Programdan çıkmak için herhangi bir tuşa basın.

1. Terminal penceresini kapatın.

## <a name="set-a-conditional-breakpoint"></a>Koşullu kesme noktası ayarlama

Program, kullanıcının girdiği dizeyi görüntüler. Kullanıcı hiçbir şey girmezse ne olur? Bunu, *koşullu kesme noktası*adında yararlı bir hata ayıklama özelliği ile test edebilirsiniz.

1. <kbd>CTRL tuşuna</kbd>basıp kesme noktasını temsil eden kırmızı noktaya tıklayın. Bağlam menüsünde, **kesme noktasını Düzenle**' yi seçin.

1. **Kesme noktasını Düzenle** iletişim kutusunda aşağıdaki alana aşağıdaki kodu girin **ve aşağıdaki koşul doğrudur**ve **Uygula**' yı seçin.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="Kesme noktası ayarları panelini gösteren düzenleyici":::

   Kesme noktası her isabet edildiğinde, hata ayıklayıcı `String.IsNullOrEmpty(name)` yöntemini çağırır ve yalnızca Yöntem çağrısı döndürürse bu satırı keser `true` .

   Koşullu bir ifade yerine, bir deyim belirtilen sayıda yürütülmeden önce program yürütmeyi kesen bir *isabet sayısı*belirtebilirsiniz.

1. Hata ayıklamayı başlatmak için <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>komut</kbd> + <kbd>ENTER</kbd>) tuşuna basın.

1. Adınızı girmeniz istendiğinde, Terminal penceresinde <kbd>ENTER</kbd> tuşuna basın.

   Belirttiğiniz koşul (ya `name` da `null` <xref:System.String.Empty?displayProperty=nameWithType> ) karşılandığından, program yürütmesi kesme noktasına ulaştığında durmaktadır.

1. Şu anda yürütülmekte olan metodun yerellerinin değerlerini gösteren **Yereller** penceresini seçin. Bu durumda, `Main` Şu anda yürütülmekte olan yöntemdir. Değişkenin değerinin olduğunu, yani, olduğunu gözlemleyin `name` `""` <xref:System.String.Empty?displayProperty=nameWithType> .

1. Ayrıca, `name` **hemen** penceresinde değişken adını girip <kbd>ENTER</kbd>tuşuna basarak değerin boş bir dize olduğunu görebilirsiniz.

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="Adın bir boş dize olduğunu gösteren komut penceresi":::

1. Hata <kbd>⌘</kbd>ayıklamaya devam etmek için ⌘<kbd>↵</kbd> (<kbd>komut</kbd> + <kbd>ENTER</kbd>) tuşuna basın.

1. Terminal penceresinde programından çıkmak için herhangi bir tuşa basın.

1. Terminal penceresini kapatın.

1. Kod penceresinin sol kenarındaki kırmızı noktaya tıklayarak kesme noktasını temizleyin. Bir kesme noktasını temizlemek için başka bir yol da kod satırı seçili durumdayken > Çalıştır ' i seçerek **kesme noktasını değiştirir** .

## <a name="step-through-a-program"></a>Programda adımla

Visual Studio Ayrıca, bir program aracılığıyla satıra göre çizgi ve yürütmeyi izlemeye de olanak tanır. Normalde, bir kesme noktası ayarlar ve program kodunuzun küçük bir bölümünde program akışını takip edersiniz. Bu program küçük olduğundan programın tamamında ilerlayabilirsiniz.

1. Yöntemin başlangıcını işaretleyen küme ayracı üzerinde bir kesme noktası ayarlayın `Main` ( <kbd>Command</kbd>tuşuna basın + <kbd>\\</kbd> ).

1. Hata ayıklamayı başlatmak için <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>komut</kbd> + <kbd>ENTER</kbd>) tuşuna basın.

   Visual Studio kesme noktası ile satır üzerinde durmaktadır.

1. Bir satıra ilerlemek için <kbd>⇧</kbd><kbd>⌘</kbd><kbd>ı</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>ı</kbd>) veya Select Step **Run**with '  >  **a** basın.

   Visual Studio, sonraki yürütme satırının yanında bir ok görüntüler.

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Visual Studio Step into yöntemi":::

   Bu noktada, **Yereller** penceresi `args` dizinin boş olduğunu ve `name` `date` varsayılan değerlere sahip olduğunu gösterir. Ayrıca, Visual Studio boş bir Terminal açtı.

1. <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>ı</kbd>) tuşuna basın.

   Visual Studio, değişken atamasını içeren ifadeyi vurgular `name` . **Yereller** penceresi olduğunu gösterir `name` `null` ve Terminal "adınız nedir?" dizesini görüntüler.

1. Konsol penceresine bir dize girerek ve <kbd>ENTER</kbd>' a basarak istemi yanıtlayın.

1. <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>ı</kbd>) tuşuna basın.

   Visual Studio, değişken atamasını içeren ifadeyi vurgular `date` . **Yereller** penceresi, yöntemi çağrısının döndürdüğü değeri gösterir <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> . Terminal, istemde girdiğiniz dizeyi görüntüler.

1. <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>ı</kbd>) tuşuna basın.

   **Yereller** penceresi, `date` özelliğinden atamasından sonra değişkenin değerini gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> . Terminal değiştirilmez.

1. <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>ı</kbd>) tuşuna basın.

   Visual Studio yöntemini çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> . Terminal, biçimlendirilen dizeyi görüntüler.

1. <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>SHIFT</kbd> + <kbd>komutu</kbd> + <kbd>U</kbd>) tuşuna basın veya **çalışma adımını Çalıştır**' ı seçin  >  **Step Out**.

   Terminal bir ileti görüntüler ve bir tuşa basmanız için bekler.

1. Programdan çıkmak için herhangi bir tuşa basın.

## <a name="use-release-build-configuration"></a>Yayın derleme yapılandırmasını kullan

Uygulamanızın hata ayıklama sürümünü sınadıktan sonra yayın sürümünü derleyip test etmeniz gerekir. Yayın sürümü, bir uygulamanın davranışını olumsuz yönde etkileyebilecek derleyici iyileştirmeleri içerir. Örneğin, performansı artırmak için tasarlanan derleyici iyileştirmeleri, çok iş parçacıklı uygulamalarda yarış koşulları oluşturabilir.

Konsol uygulamasının yayın sürümünü derlemek ve test etmek için aşağıdaki adımları uygulayın:

1. Araç çubuğundaki derleme yapılandırmasını **Hata Ayıkla** 'dan **Release**olarak değiştirin.

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="hata ayıklama vurgulanmış olarak varsayılan Visual Studio araç çubuğu":::

1. <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> <kbd>option</kbd> + <kbd>command</kbd> + Hata ayıklamadan çalıştırmak için ⌥ ⌘ ↵ (seçenek komut<kbd>ENTER</kbd>) tuşuna basın.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, Visual Studio hata ayıklama araçları 'nı kullandınız. Sonraki öğreticide, uygulamanın dağıtılabilir bir sürümünü yayımlarsınız.

> [!div class="nextstepaction"]
> [Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması yayımlama](publishing-with-visual-studio-mac.md)
