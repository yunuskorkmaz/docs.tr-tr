---
title: Visual Studio Code kullanarak bir .NET Core konsol uygulamasında hata ayıklama
description: Visual Studio Code kullanarak bir .NET Core konsol uygulamasında hata ayıklamayı öğrenin.
ms.date: 05/26/2020
ms.openlocfilehash: 84c7b64ad7708cf2def084593cd7f96eb0ad82e5
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810670"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-code"></a>Öğretici: Visual Studio Code kullanarak bir .NET Core konsol uygulamasında hata ayıklama

Bu öğreticide, .NET Core uygulamalarıyla çalışmak üzere Visual Studio Code sağlanan hata ayıklama araçları tanıtılmaktadır.

## <a name="prerequisites"></a>Ön koşullar

- Bu öğretici, [Visual Studio Code bir .NET Core konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.

## <a name="use-debug-build-configuration"></a>Hata ayıklama derleme yapılandırmasını kullan

*Hata ayıklama* ve *yayın* .NET Core 'un yerleşik derleme yapılandırmalarıdır. Hata ayıklama oluşturma yapılandırması hata ayıklama için ve son sürüm dağıtımı için sürüm yapılandırması ' nı kullanırsınız.

Hata ayıklama yapılandırmasında, bir program tam sembolik hata ayıklama bilgileriyle derlenir ve iyileştirmesi yoktur. Kaynak kodu ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olduğundan iyileştirme, hata ayıklamayı karmaşıklaştırır. Bir programın yayın yapılandırmasında sembolik hata ayıklama bilgisi yoktur ve tamamen iyileştirilmiştir.

Varsayılan olarak, Visual Studio Code başlatma ayarları hata ayıklama derleme yapılandırmasını kullanır, bu nedenle hata ayıklamadan önce değiştirmeniz gerekmez.

1. Visual Studio Code’u başlatma.

1. [Visual Studio Code .NET Core konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz projenin klasörünü açın.

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

Kesme *noktası,* kesme noktası olan satır yürütülmeden önce uygulamanın yürütülmesini geçici olarak keser.

1. *Program.cs* dosyasını açın.

1. Kod penceresinin sol kenar boşluğuna tıklayarak adı, tarihi ve saati gösteren satırda bir *kesme noktası* ayarlayın. Sol kenar boşluğu satır numaralarının solunda bulunur. Bir kesme noktası ayarlamak için diğer yollar <kbd>F9</kbd> tuşuna basarak veya **Run**  >  kod satırı seçiliyken menüden**geçiş kesme noktası** Çalıştır ' i seçmekle belirlenir.

   Visual Studio Code, sol kenar boşluğunda kırmızı bir nokta görüntüleyerek kesme noktasının ayarlandığı satırı gösterir.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="Kesme noktası kümesi":::

## <a name="set-up-for-terminal-input"></a>Terminal girişi için ayarlama

Kesme noktası bir `Console.ReadLine` Yöntem çağrısından sonra bulunur. **Hata ayıklama konsolu** çalışan bir program için Terminal girişini kabul etmez. Hata ayıklarken Terminal girişini işlemek için tümleşik Terminal (Visual Studio Code Windows) veya harici bir terminalde kullanabilirsiniz. Bu öğreticide, tümleşik Terminal kullanılır.

1. *. Vscode/launch.js*açın.

1. `console`Ayarını olarak değiştirin `integratedTerminal` .

   Kimden:

   ```json
   "console": "internalConsole",
   ```

   Hedef:

   ```json
   "console": "integratedTerminal",
   ```

1. Yaptığınız değişiklikleri kaydedin.

## <a name="start-debugging"></a>Hata ayıklamayı Başlat

1. Sol taraftaki menüdeki hata ayıklama simgesini seçerek hata ayıklama görünümünü açın.

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Visual Studio Code hata ayıkla sekmesini açın":::

1. Bölmenin üst kısmındaki yeşil oku seçerek **.NET Core başlatma (konsol)**' nin yanına tıklayın. Programı hata ayıklama modunda başlatmak için başka bir yöntem de **Run**  >  menüden**hata ayıklamayı Başlat** Çalıştır ' i seçmektir.

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="Hata ayıklamayı Başlat":::

1. "Adınız nedir?" öğesini görmek için **Terminal** sekmesini seçin. programın yanıt beklemeden önce görüntülediğini iste.

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="Terminal sekmesini seçin":::

1. Bir ad istemine yanıt olarak **Terminal** penceresine bir dize girin ve ardından <kbd>ENTER</kbd>tuşuna basın.

   Program yürütme, kesme noktasına ulaştığında ve Yöntem yürütmeden önce duraklar `Console.WriteLine` . **Değişkenler** penceresinin **Yereller** bölümü, yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="Yerelleri gösteren kesme noktası isabet":::

## <a name="use-the-debug-console"></a>Hata ayıklama konsolunu kullanma

**Hata ayıklama konsolu** penceresi, hata ayıkladığınızda uygulamayla etkileşime girebilmenizi sağlar. Programınızı nasıl etkileyeceğini görmek için değişkenlerin değerini değiştirebilirsiniz.

1. **Hata ayıklama konsolu** sekmesini seçin.

1. `name = "Gracie"` **Hata ayıklama konsolu** penceresinin en altındaki Istemine yazın ve <kbd>ENTER</kbd> tuşuna basın.

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="Değişken değerlerini Değiştir":::

1. `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` **Hata ayıklama konsolu** penceresinin alt kısmına girin ve <kbd>ENTER</kbd> tuşuna basın.

   **Değişkenler** penceresi, ve değişkenlerinin yeni değerlerini görüntüler `name` `date` .

1. Araç çubuğundaki **devam** düğmesini seçerek program yürütmeye devam edin. Devam etmenin başka bir yolu da <kbd>F5</kbd>'e basılarak yapılır.

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="Hata ayıklamaya devam et":::

1. **Terminal** sekmesini yeniden seçin.

   Konsol penceresinde görünen değerler, **hata ayıklama konsolunda**yaptığınız değişikliklere karşılık gelir.

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="Girilen değerleri gösteren Terminal":::

1. Uygulamadan çıkmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.

## <a name="set-a-conditional-breakpoint"></a>Koşullu kesme noktası ayarlama

Program, kullanıcının girdiği dizeyi görüntüler. Kullanıcı hiçbir şey girmezse ne olur? Bunu, *koşullu kesme noktası*adında yararlı bir hata ayıklama özelliği ile test edebilirsiniz.

1. Kesme noktasını temsil eden kırmızı nokta üzerinde sağ tıklayın (macOS üzerinde<kbd>CTRL</kbd>+ tıklama). Bağlam menüsünde, bir koşullu ifade girmenize izin veren bir iletişim kutusu açmak için **kesme noktasını Düzenle** ' yi seçin.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="Kesme noktası bağlam menüsü":::

1. `Expression`Açılan kutudan seçim yapın, aşağıdaki koşullu ifadeyi girin ve <kbd>ENTER</kbd>tuşuna basın.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="Koşullu bir ifade girin":::

   Kesme noktası her isabet edildiğinde, hata ayıklayıcı `String.IsNullOrEmpty(name)` yöntemini çağırır ve yalnızca Yöntem çağrısı döndürürse bu satırı keser `true` .

   Koşullu bir ifade yerine, bir deyim belirtilen sayıda yürütülmeden önce program yürütmeyi kesen bir *isabet sayısı*belirtebilirsiniz. Diğer bir seçenek de bir *filtre koşulu*belirtmektir. Bu, iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı olarak bu tür özniteliklere dayalı olarak program yürütmeyi keser.

1. <kbd>F5</kbd>'e basarak programı hata ayıklama ile başlatın.

1. Adınızı girmeniz istendiğinde, **Terminal** sekmesinde <kbd>ENTER</kbd> tuşuna basın.

   Belirttiğiniz koşul ( `name` `null` veya <xref:System.String.Empty?displayProperty=nameWithType> ) karşılandı olduğundan, program yürütmesi kesme noktasına ulaştığında ve Yöntem yürütülmeden önce durmaktadır `Console.WriteLine` .

   **Değişkenler** penceresi `name` , değişkeninin değerinin veya olduğunu gösterir `""` <xref:System.String.Empty?displayProperty=nameWithType> .

1. **Hata ayıklama konsolu** istemine aşağıdaki ifadeyi girerek ve <kbd>ENTER</kbd>tuşuna basarak değerin boş bir dize olduğunu onaylayın. Sonuç olarak `true` .

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="Deyimden sonra true değeri döndüren hata ayıklama konsolu":::

1. Program yürütmeye devam etmek için araç çubuğundaki **devam** düğmesini seçin.

1. **Terminal** sekmesini seçin ve herhangi bir tuşa basarak programdan çıkın ve hata ayıklamayı durdurun.

1. Kod penceresinin sol kenarındaki noktaya tıklayarak kesme noktasını temizleyin. Bir kesme noktasını temizlemek için diğer yollar, kod satırı seçiliyken <kbd>F9</kbd> tuşuna basarak veya menüden **kesme noktası** ' nı seçerek >.

1. Kesme noktası koşulunun kaybolacağını belirten bir uyarı alırsanız, **kesme noktasını kaldır**' ı seçin.

## <a name="step-through-a-program"></a>Programda adımla

Visual Studio Code Ayrıca, bir program aracılığıyla satır içine girerek ve yürütmesini izlemenize olanak tanır. Normalde, bir kesme noktası ayarlar ve program kodunuzun küçük bir bölümünde program akışını takip edersiniz. Bu program küçük olduğundan programın tamamında ilerlayabilirsiniz.

1. Metodun açılış küme ayracı üzerinde bir kesme noktası ayarlayın `Main` .

1. Hata ayıklamaya başlamak için <kbd>F5</kbd>'e basın.

   Visual Studio Code kesme çizgisi çizgisini vurgular.

   Bu noktada, **değişkenler** penceresi `args` dizinin boş olduğunu ve `name` `date` varsayılan değerlere sahip olduğunu gösterir.

1. Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="Adımla düğmesi":::

   Visual Studio Code sonraki satırı vurgular.

1. Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.

   Visual Studio Code, `Console.WriteLine` ad istemi için öğesini yürütür ve sonraki yürütme satırını vurgular. Sonraki satır, `Console.ReadLine` içindir `name` . **Değişkenler** penceresi değiştirilmez ve **Terminal** sekmesi "adınız nedir?" olarak gösterilir. isteme.

1. Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.

   Visual Studio, `name` değişken atamasını vurgular. **Değişkenler** penceresi hala olduğunu gösterir `name` `null` .

1. Terminal sekmesine bir dize girerek ve <kbd>ENTER</kbd>' a basarak istemi yanıtlayın.

   **Terminal** sekmesi, girerken girdiğiniz dizeyi görüntülemeyebilir, ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Yöntem girişinizi yakalar.

1. Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.

   Visual Studio Code, `date` değişken atamasını vurgular. **Değişkenler** penceresi, yöntemine yapılan çağrı tarafından döndürülen değeri gösterir <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> . **Terminal** sekmesi, istemde girdiğiniz dizeyi görüntüler.

1. Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.

   **Değişkenler** penceresi, `date` özelliğinden atamadan sonraki değişkenin değerini gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> .

1. Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.

   Visual Studio Code yöntemini çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> . Konsol penceresi biçimlendirilen dizeyi görüntüler.

1. **Çalışma adımını Çalıştır**' ı seçin  >  **Step Out** veya <kbd>SHIFT</kbd> + <kbd>F11</kbd>tuşuna basın.

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="Adımla düğmesi":::

1. **Terminal** sekmesini seçin.

   Terminal "çıkmak için herhangi bir tuşa basın..." şeklinde görüntülenir.

1. Programdan çıkmak için herhangi bir tuşa basın.

## <a name="use-release-build-configuration"></a>Yayın derleme yapılandırmasını kullan

Uygulamanızın hata ayıklama sürümünü sınadıktan sonra yayın sürümünü derleyip test etmeniz gerekir. Yayın sürümü, bir uygulamanın davranışını etkileyebilecek derleyici iyileştirmeleri içerir. Örneğin, performansı artırmak için tasarlanan derleyici iyileştirmeleri, çok iş parçacıklı uygulamalarda yarış koşulları oluşturabilir.

Konsol uygulamanızın yayın sürümünü derlemek ve test etmek için **terminali** açın ve şu komutu çalıştırın:

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a>Ek kaynaklar

* [Visual Studio Code 'de hata ayıklama](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide hata ayıklama araçları Visual Studio Code kullandınız. Sonraki öğreticide, uygulamanın dağıtılabilir bir sürümünü yayımlarsınız.

> [!div class="nextstepaction"]
> [Visual Studio Code bir .NET Core konsol uygulaması yayımlama](publishing-with-visual-studio-code.md)
