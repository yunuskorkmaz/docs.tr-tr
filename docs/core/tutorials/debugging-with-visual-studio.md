---
title: Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklama
description: Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklamayı öğrenin.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 0555c6b4185da088333503c1e744da2dd7b4f2e4
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867600"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a>Öğretici: Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklama

Bu öğreticide, Visual Studio 'da kullanılabilen hata ayıklama araçları tanıtılmaktadır.

## <a name="prerequisites"></a>Önkoşullar

- Bu öğretici, [Visual Studio kullanarak bir .NET Core konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.

## <a name="use-debug-build-configuration"></a>Hata ayıklama derleme yapılandırmasını kullan

*Hata ayıklama* ve *yayın* , Visual Studio 'nun yerleşik derleme yapılandırmalarıdır. Hata ayıklama oluşturma yapılandırması hata ayıklama için ve son sürüm dağıtımı için sürüm yapılandırması ' nı kullanırsınız.

Hata ayıklama yapılandırmasında, bir program tam sembolik hata ayıklama bilgileriyle derlenir ve iyileştirmesi yoktur. Kaynak kodu ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olduğundan iyileştirme, hata ayıklamayı karmaşıklaştırır. Bir programın yayın yapılandırmasında sembolik hata ayıklama bilgisi yoktur ve tamamen iyileştirilmiştir.

 Varsayılan olarak, Visual Studio Code hata ayıklama derleme yapılandırmasını kullanır, bu nedenle hata ayıklamadan önce değiştirmeniz gerekmez.

1. Visual Studio’yu çalıştırın.

1. [Visual Studio kullanarak .NET Core konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz projeyi açın.

   Geçerli derleme yapılandırması araç çubuğunda gösterilir. Aşağıdaki araç çubuğu görüntüsünde, Visual Studio 'nun uygulamanın hata ayıklama sürümünü derlemek üzere yapılandırıldığı gösterilmektedir:

   ![Hata ayıklama vurgulanmış Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

Kesme *noktası,* kesme noktası olan satır yürütülmeden önce uygulamanın yürütülmesini geçici olarak keser.

1. Bu satırdaki kod penceresinin sol kenar boşluğuna tıklayarak adı, tarihi ve saati gösteren satırda bir *kesme noktası* ayarlayın. Sol kenar boşluğu satır numaralarının solunda bulunur.  Bir kesme noktası ayarlamak için başka bir yol ise imleci kod satırına yerleştirip, sonra da menü çubuğunda **Hata Ayıkla**  >  **geçiş kesme noktası** ' nı seçerek yapılır.

   Aşağıdaki görüntüde gösterildiği gibi, Visual Studio, kesme noktasının ayarlandığı ve sol kenar boşluğunda kırmızı bir nokta görüntüleyen çizgiyi gösterir.

   ![Kesme noktası ayarlanmış Visual Studio program penceresi](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Programı hata ayıklama modunda çalıştırmak için <kbd>F5</kbd> tuşuna basın. Hata ayıklamayı başlatmak için başka bir yol da **Debug**menüden hata ayıklama  >  **başlatma hata** Ayıkla ' yı seçmektir.

1. Program bir ad isteminde bulunduğunda konsol penceresine bir dize girin ve ardından <kbd>ENTER</kbd>tuşuna basın.

1. Program yürütme, kesme noktasına ulaştığında ve Yöntem yürütmeden önce duraklar `Console.WriteLine` . **Yereller** penceresi, yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler.

   ![Visual Studio 'da bir kesme noktasının ekran görüntüsü](./media/debugging-with-visual-studio/breakpoint-hit.png)

## <a name="use-the-immediate-window"></a>Hemen penceresini kullanma

**Komut** penceresi, hata ayıklamanıza çalıştığınız uygulamayla etkileşime girebilmenizi sağlar. Programınızı nasıl etkilediğini görmek için değişkenlerin değerini etkileşimli olarak değiştirebilirsiniz.

1. **Komut** penceresi görünür değilse, Windows anında **Hata Ayıkla**' yı seçerek bunu görüntüleyin  >  **Windows**  >  **Immediate**.

1. `name = "Gracie"` **Hemen** penceresine girip <kbd>ENTER</kbd> tuşuna basın.

1. `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` **Hemen** penceresine girip <kbd>ENTER</kbd> tuşuna basın.

   **Komut** penceresi, dize değişkeninin değerini ve değerin özelliklerini görüntüler <xref:System.DateTime> . Ayrıca, değişkenlerin değerleri **Yereller** penceresinde güncelleştirilir.

   ![Visual Studio 2019 ' de Yereller ve anında Windows](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Program yürütmeye devam etmek için <kbd>F5</kbd> tuşuna basın. Devam etmenin başka bir yolu da menüden **Debug**  >  **devam et** ' i seçmekten.

   Konsol penceresinde görünen değerler, **hemen** penceresinde yaptığınız değişikliklere karşılık gelir.

   ![Girilen değerleri gösteren konsol penceresi](./media/debugging-with-visual-studio/console-window.png)

1. Uygulamadan çıkmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.

## <a name="set-a-conditional-breakpoint"></a>Koşullu kesme noktası ayarlama

Program, kullanıcının girdiği dizeyi görüntüler. Kullanıcı hiçbir şey girmezse ne olur? Bunu, *koşullu kesme noktası*adında yararlı bir hata ayıklama özelliği ile test edebilirsiniz.

1. Kesme noktasını temsil eden kırmızı noktaya sağ tıklayın. Bağlam menüsünde **koşullar** ' ı seçerek **kesme noktası ayarları** iletişim kutusunu açın. Henüz seçili değilse, **koşullar** kutusunu seçin.

   ![Kesme noktası ayarları panelini gösteren düzenleyici-C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. **Koşullu ifade**için, 5 ise testlerin örnek kodunu gösteren alana aşağıdaki kodu girin `x` . Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Kesme noktası her isabet edildiğinde, hata ayıklayıcı `String.IsNullOrEmpty(name)` yöntemini çağırır ve yalnızca Yöntem çağrısı döndürürse bu satırı keser `true` .

   Koşullu bir ifade yerine, bir deyim belirtilen sayıda yürütülmeden önce program yürütmeyi kesen bir *isabet sayısı*belirtebilirsiniz. Diğer bir seçenek de bir *filtre koşulu*belirtmektir. Bu, iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı olarak bu tür özniteliklere dayalı olarak program yürütmeyi keser.

1. İletişim kutusunu kapatmak için **Kapat** ' ı seçin.

1. <kbd>F5</kbd>'e basarak programı hata ayıklama ile başlatın.

1. Konsol penceresinde, adınızı girmeniz istendiğinde <kbd>ENTER</kbd> tuşuna basın.

1. Belirttiğiniz koşul ( `name` veya ya da `null` <xref:System.String.Empty?displayProperty=nameWithType> ) karşılandığından, program yürütmesi kesme noktasına ulaştığında ve Yöntem yürütülmeden önce durduktan sonra duraklar `Console.WriteLine` .

1. Şu anda yürütülmekte olan metodun yerellerinin değerlerini gösteren **Yereller** penceresini seçin. Bu durumda, `Main` Şu anda yürütülmekte olan yöntemdir. Değişkenin değerinin veya olduğunu gözlemleyin `name` `""` <xref:System.String.Empty?displayProperty=nameWithType> .

1. Aşağıdaki ifadeyi **komut** penceresine girip <kbd>ENTER</kbd>tuşuna basarak değeri boş bir dize olduğunu onaylayın. Sonuç olarak `true` .

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   Soru işareti, [bir ifadeyi değerlendirmek](/visualstudio/ide/reference/immediate-window#enter-commands)için hemen penceresini yönlendirir.

   ![Deyimin yürütülmesi yapıldıktan sonra bir true değeri döndüren komut penceresi-C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Program yürütmeye devam etmek için <kbd>F5</kbd> tuşuna basın.

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve hata ayıklamayı durdurun.

1. Kod penceresinin sol kenarındaki noktaya tıklayarak kesme noktasını temizleyin. Bir kesme noktasını temizlemek için başka bir yol da, kod satırı seçiliyken **kesme noktası > geçiş noktası** ' nı seçmektir.

## <a name="step-through-a-program"></a>Programda adımla

Visual Studio Ayrıca, bir program aracılığıyla satıra göre çizgi ve yürütmeyi izlemeye de olanak tanır. Normalde, bir kesme noktası ayarlar ve program kodunuzun küçük bir bölümünde program akışını takip edersiniz. Bu program küçük olduğundan programın tamamında ilerlayabilirsiniz.

1. **Hata ayıklama**  >  **adımını**seçin. Tek seferde bir ifadede hata ayıklamanın başka bir yolu da <kbd>F11</kbd>tuşuna basılarak yapılır.

   Visual Studio, sonraki yürütme satırının yanında bir ok görüntüler.

   C#

   ![Visual Studio Step into yöntemi-C #](./media/debugging-with-visual-studio/step-into-method.png)

   Visual Basic

   ![Visual Studio adımla yöntemi-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   Bu noktada, **Yereller** penceresi `args` dizinin boş olduğunu ve `name` `date` varsayılan değerlere sahip olduğunu gösterir. Ayrıca, Visual Studio boş bir konsol penceresi açtı.

1. <kbd>F11</kbd>tuşuna basın. Visual Studio artık bir sonraki yürütme satırını vurgulamaktadır. **Yereller** penceresi değiştirilmez ve konsol penceresi boş kalır.

   C#

   ![Metot kaynağı-C içindeki Visual Studio adımı #](./media/debugging-with-visual-studio/step-into-source-method.png)

   Visual Basic

   ![Visual Studio adımla Yöntem kaynağı-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <kbd>F11</kbd>tuşuna basın. Visual Studio, değişken atamasını içeren ifadeyi vurgular `name` . **Yereller** penceresi olduğunu gösterir `name` `null` ve konsol penceresi "adınız nedir?" dizesini görüntüler.

1. Konsol penceresine bir dize girerek ve <kbd>ENTER</kbd>' a basarak istemi yanıtlayın. Konsol yanıt vermiyor ve girdiğiniz dize konsol penceresinde görüntülenmiyor, ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Yöntem yine de girişinizi yakalayacak.

1. <kbd>F11</kbd>tuşuna basın. Visual Studio, `date` değişken atamasını (Visual Basic) içeren ifadeyi vurgular `currentDate` . **Yereller** penceresi, yöntemi çağrısının döndürdüğü değeri gösterir <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> . Konsol penceresinde, isteminde girdiğiniz dize de görüntülenir.

1. <kbd>F11</kbd>tuşuna basın. **Yereller** penceresi, `date` özelliğinden atamasından sonra değişkenin değerini gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> . Konsol penceresi değiştirilmez.

1. <kbd>F11</kbd>tuşuna basın. Visual Studio yöntemini çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> . Konsol penceresi biçimlendirilen dizeyi görüntüler.

1. **Hata ayıklama**  >  **adımını**seçin. Adım adım yürütmeyi durdurmaya yönelik başka bir yöntem de <kbd>SHIFT</kbd> + <kbd>F11</kbd>tuşuna basmaktır.

   Konsol penceresinde bir ileti görüntülenir ve bir tuşa basmanız bekler.

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve hata ayıklamayı durdurun.

## <a name="use-release-build-configuration"></a>Yayın derleme yapılandırmasını kullan

Uygulamanızın hata ayıklama sürümünü sınadıktan sonra yayın sürümünü derleyip test etmeniz gerekir. Yayın sürümü bazen bir uygulamanın davranışını olumsuz yönde etkileyebilecek derleyici iyileştirmeleri içerir. Örneğin, performansı artırmak için tasarlanan derleyici iyileştirmeleri, çok iş parçacıklı uygulamalarda yarış koşulları oluşturabilir.

Konsol uygulamanızın yayın sürümünü derlemek ve test etmek için, araç çubuğundaki derleme yapılandırmasını **Hata Ayıkla** 'dan **Release**olarak değiştirin.

![hata ayıklama vurgulanmış olarak varsayılan Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<kbd>F5</kbd> tuşuna bastığınızda veya **Build** menüsünden **çözüm oluştur** ' u seçtiğinizde, Visual Studio uygulamanın yayın sürümünü derler. Hata ayıklama sürümünü yaptığınız gibi test edebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, Visual Studio hata ayıklama araçları 'nı kullandınız. Sonraki öğreticide, uygulamanın dağıtılabilir bir sürümünü yayımlarsınız.

> [!div class="nextstepaction"]
> [Visual Studio kullanarak bir .NET Core konsol uygulaması yayımlama](publishing-with-visual-studio.md)
