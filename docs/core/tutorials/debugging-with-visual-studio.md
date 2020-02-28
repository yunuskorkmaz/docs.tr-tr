---
title: Visual Studio ile Merhaba Dünya .NET Core uygulamanızda hata ayıklama
description: Visual Studio ile C# veya Visual Basic yazılmış Merhaba Dünya bir uygulamada hata ayıklamayı öğrenin.
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: b2ee1401fc89f990c5f930d80d1a510a117e63a0
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156679"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>Visual Studio C# 'yu kullanarak veya Visual Basic .net Core Merhaba Dünya uygulamanızda hata ayıklayın

Şimdiye kadar, basit bir konsol uygulaması oluşturmak ve çalıştırmak için [Visual Studio 2019 ' de ilk .NET Core konsol uygulamanızı oluşturma](with-visual-studio.md) bölümündeki adımları izlediyseniz. Uygulamanızı yazdıktan ve derledikten sonra test etmeye başlayabilirsiniz. Visual Studio, uygulamanızda sorun gidermek için kullanabileceğiniz kapsamlı bir hata ayıklama araçları kümesi içerir.

## <a name="debug-build-configuration"></a>Derleme yapılandırmasında hata ayıkla

*Hata ayıklama* ve *yayın* , Visual Studio 'nun varsayılan derleme yapılandırmasından ikdir. Geçerli derleme yapılandırması araç çubuğunda gösterilir. Aşağıdaki araç çubuğu görüntüsünde, Visual Studio 'nun uygulamanın hata ayıklama sürümünü derlemek üzere yapılandırıldığı gösterilmektedir:

![Hata ayıklama vurgulanmış Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Uygulamanızın hata ayıklama sürümünü çalıştırarak başlayın. Hata ayıklama derleme yapılandırması, çoğu derleyici iyileştirmesini kapatır ve derleme işlemi sırasında daha zengin bilgiler sağlar.

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

Programınızı çalıştırın ve birkaç hata ayıklama özelliğini deneyin:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

1. Bu satırdaki kod penceresinin sol kenar boşluğuna tıklayarak `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` okuyan satırda bir *kesme noktası* ayarlayın. Ayrıca, giriş işaretini kod satırına yerleştirip **F9** tuşuna basarak veya menü çubuğundan **kesme noktası > geçiş noktasını** seçerek de bir kesme noktası ayarlayabilirsiniz.

   Kesme noktası, kesme noktası olan satır yürütülmeden *önce* uygulamanın yürütülmesini geçici olarak keser.

   Aşağıdaki görüntüde gösterildiği gibi, Visual Studio, kesme noktasının ayarlandığı çizgiyi vurgulayarak ve sol kenar boşluğunda kırmızı bir daire görüntüleyerek gösterir.

   ![Kesme noktası ayarlanmış Visual Studio program penceresi](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Araç çubuğunda yeşil ok ile **HelloWorld** düğmesini seçip **F5**tuşuna basarak veya hata **ayıklamayı başlatmak** > **Hata Ayıkla** ' yı seçerek programı hata ayıklama modunda çalıştırın.

1. Program bir ad isteminde bulunduğunda konsol penceresine bir dize girin ve ardından **ENTER**tuşuna basın.

1. Program yürütme, kesme noktasına ulaştığında ve `Console.WriteLine` yöntemi yürütmeden önce duraklar. **Yereller** penceresi, yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler.

   ![Visual Studio 'da bir kesme noktasının ekran görüntüsü](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. **Komut** penceresi, hata ayıklamanıza çalıştığınız uygulamayla etkileşime girebilmenizi sağlar. Programınızı nasıl etkilediğini görmek için değişkenlerin değerini etkileşimli olarak değiştirebilirsiniz.

   1. **Acil** pencere görünür değilse, **hata ayıkla** > **Windows** > **anında**öğesini seçerek bunu görüntüleyin.

   1. **Hemen** penceresine `name = "Gracie"` girin ve **ENTER** tuşuna basın.

   1. **Hemen** penceresine `date = DateTime.Parse("11/16/2019 5:25 PM")` girin ve **ENTER** tuşuna basın.

   **Komut** penceresi, dize değişkeninin ve <xref:System.DateTime> değerinin özelliklerinin değerini görüntüler. Ayrıca, değişkenlerin değerleri **Yereller** penceresinde güncelleştirilir.

   ![Visual Studio 2019 ' de Yereller ve anında Windows](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Araç çubuğundaki **devam** düğmesini seçerek veya **Hata Ayıkla** > **devam et**' i seçerek program yürütmeye devam edin. Konsol penceresinde görünen değerler, **hemen** penceresinde yaptığınız değişikliklere karşılık gelir.

   ![Girilen değerleri gösteren konsol penceresi](./media/debugging-with-visual-studio/console-window.png)

1. Uygulamadan çıkmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Bu satırdaki kod penceresinin sol kenar boşluğuna tıklayarak `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` okuyan satırda bir *kesme noktası* ayarlayın. Ayrıca, giriş işaretini istediğiniz satıra yerleştirip **hata ayıkla** > menü çubuğundan **kesme noktası** ' nı seçerek bir kesme noktası da ayarlayabilirsiniz.

   Kesme noktası, kesme noktası olan satır yürütülmeden *önce* uygulamanın yürütülmesini geçici olarak keser.

   Aşağıdaki şekilde gösterildiği gibi, Visual Studio, kesme noktasının ayarlandığı ve sol kenar boşluğunda kırmızı bir daire görüntülendiği satırı gösterir.

   ![Kesme noktası ayarlanmış Visual Studio program penceresi](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. Araç çubuğunda yeşil ok ile **HelloWorld** düğmesini seçip **F5**tuşuna basarak veya hata **ayıklamayı başlatmak** > **Hata Ayıkla** ' yı seçerek programı hata ayıklama modunda çalıştırın.

1. Program bir ad isteminde bulunduğunda konsol penceresine bir dize girin ve **ENTER**'a basın.

1. Program yürütme, kesme noktasına ulaştığında ve `Console.WriteLine` yöntemi yürütmeden önce duraklar. **Yereller** penceresi, yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler.

1. **Komut** penceresi, hata ayıklamanıza çalıştığınız uygulamayla etkileşime girebilmenizi sağlar. Programınızı nasıl etkilediğini görmek için değişkenlerin değerini etkileşimli olarak değiştirebilirsiniz.

   1. **Acil** pencere görünür değilse, **hata ayıkla** > **Windows** > **anında**öğesini seçerek bunu görüntüleyin.

   1. **Hemen** penceresine `name = "Gracie"` girin ve **ENTER** tuşuna basın.

   1. **Hemen** penceresine `date = DateTime.Parse("11/16/2019 5:25 PM")` girin ve **ENTER** tuşuna basın.

   Değişkenlerin değerleri **Yereller** penceresinde güncelleştirilir.

1. Araç çubuğundaki **devam** düğmesini seçerek veya **Hata Ayıkla** > **devam et** menü öğesini seçerek program yürütmeye devam edin. Konsol penceresinde görünen değerler, **hemen** penceresinde yaptığınız değişikliklere karşılık gelir.

   ![Girilen değerleri gösteren konsol penceresi](./media/debugging-with-visual-studio/console-window.png)

1. Uygulamadan çıkmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.

---

## <a name="set-a-conditional-breakpoint"></a>Koşullu kesme noktası ayarlama

Programınız kullanıcının girdiği dizeyi görüntüler. Kullanıcı hiçbir şey girmezse ne olur? Bunu, bir veya daha fazla koşul karşılandığında program yürütmesini kesen, *koşullu kesme noktası*adlı yararlı bir hata ayıklama özelliği ile test edebilirsiniz.

Koşullu bir kesme noktası ayarlamak ve Kullanıcı bir dize giremediğinde ne olacağını sınamak için aşağıdakileri yapın:

# <a name="c"></a>[C#](#tab/csharp)

1. Kesme noktasını temsil eden kırmızı noktaya sağ tıklayın. Bağlam menüsünde **koşullar** ' ı seçerek **kesme noktası ayarları** iletişim kutusunu açın. Henüz seçili değilse, **koşullar** kutusunu işaretleyin.

   ![Kesme noktası ayarları panelini gösteren düzenleyici-C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. **Koşullu ifade**için, "ör. x = = 5" yerine şunu yapın:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   `String.IsNullOrEmpty(name)` yöntemi `true` çağrısının, `name` bir değer atanmadığından ya da değeri boş bir dize ("") olduğundan, bu bir kod koşulu için test ediyorsunuz. Koşullu bir ifade yerine, bir deyim belirtilen sayıda yürütülmeden önce program yürütmeyi kesintiye uğramadan veya bir *filtre koşulunun*yanı sıra iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı olarak bu tür özniteliklere dayalı olarak program yürütmesini kesen bir *isabet sayısı*da belirtebilirsiniz.

1. İletişim kutusunu kapatmak için **Kapat** ' ı seçin.

1. **F5**'e basarak programı hata ayıklama ile başlatın.

1. Konsol penceresinde, adınızı girmeniz istendiğinde **ENTER** tuşuna basın.

1. Belirttiğiniz koşul, `name` `null` veya <xref:System.String.Empty?displayProperty=nameWithType>karşılandığından, bir program yürütme, kesme noktasına ulaştığında ve `Console.WriteLine` Yöntemi yürütülmeden önce durmaktadır.

1. Şu anda yürütülmekte olan metodun yerellerinin değerlerini gösteren **Yereller** penceresini seçin. Bu durumda, `Main` Şu anda yürütülmekte olan yöntemdir. `name` değişkeninin değerinin `""`veya <xref:System.String.Empty?displayProperty=nameWithType>olduğunu gözlemleyin.

1. Aşağıdaki ifadeyi **komut** penceresine girip **ENTER**tuşuna basarak değeri boş bir dize olduğunu onaylayın. Sonuç `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Deyimden sonra true değeri döndüren komut penceresi-C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Program yürütmeye devam etmek için araç çubuğundaki **devam** düğmesini seçin.

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve hata ayıklamayı durdurun.

1. Kod satırının sol kenarındaki noktaya tıklayarak veya kod satırı seçiliyken **kesme noktası > geçiş noktasını** seçerek kesme noktasını temizleyin.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Kesme noktasını temsil eden kırmızı noktaya sağ tıklayın. Bağlam menüsünde **koşullar** ' ı seçerek **kesme noktası ayarları** iletişim kutusunu açın. **Koşullar**kutusunu işaretleyin.

   ![Kesme noktası ayarları panelini gösteren düzenleyici-Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. **Koşullu ifade** için, "ör. x = 5" yerine şunu yapın:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   `String.IsNullOrEmpty(name)` yöntemi `true` çağrısının, `name` bir değer atanmadığından ya da değeri boş bir dize ("") olduğundan, bu bir kod koşulu için test ediyorsunuz. Koşullu bir ifade yerine, bir deyim belirtilen sayıda yürütülmeden önce program yürütmeyi kesintiye uğramadan veya bir *filtre koşulunun*yanı sıra iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı olarak bu tür özniteliklere dayalı olarak program yürütmesini kesen bir *isabet sayısı*da belirtebilirsiniz.

1. İletişim kutusunu kapatmak için **Kapat** ' ı seçin.

1. **F5**'e basarak programı hata ayıklama ile başlatın.

1. Konsol penceresinde, adınızı girmeniz istendiğinde **ENTER** tuşuna basın.

1. Belirttiğiniz koşul, `name` `null` veya <xref:System.String.Empty?displayProperty=nameWithType>karşılandığından, bir program yürütme, kesme noktasına ulaştığında ve `Console.WriteLine` Yöntemi yürütülmeden önce durmaktadır.

1. Şu anda yürütülmekte olan metodun yerellerinin değerlerini gösteren **Yereller** penceresini seçin. Bu durumda, `Main` Şu anda yürütülmekte olan yöntemdir. `name` değişkeninin değerinin `""`veya <xref:System.String.Empty?displayProperty=nameWithType>olduğunu gözlemleyin.

1. Aşağıdaki ifadeyi **komut** penceresine girip **ENTER**tuşuna basarak değeri boş bir dize olduğunu onaylayın. Sonuç `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![Deyimden sonra true değeri döndüren komut penceresi-Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. Program yürütmeye devam etmek için araç çubuğundaki **devam** düğmesini seçin.

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve hata ayıklamayı durdurun.

1. Kod penceresinin sol kenarındaki noktaya tıklayarak veya seçili satırı içeren bir **hata ayıkla > geçiş noktası** menü öğesini seçerek kesme noktasını temizleyin.

---
## <a name="step-through-a-program"></a>Programda adımla

Visual Studio Ayrıca, bir program aracılığıyla satıra göre çizgi ve yürütmeyi izlemeye de olanak tanır. Normalde, bir kesme noktası ayarlarsınız ve program kodunuzun küçük bir bölümünde program akışını izlemek için bu özelliği kullanabilirsiniz. Programınız küçük olduğundan, programın tamamında ilerlayabilirsiniz:

# <a name="c"></a>[C#](#tab/csharp)

1. Menü çubuğunda **hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. Visual Studio, sonraki yürütme satırının yanında bir ok görüntüler.

   ![Visual Studio adımla yöntemi-C#](./media/debugging-with-visual-studio/step-into-method.png)

   Bu noktada, **Yereller** penceresi programınızın yalnızca bir değişken `args`tanımlandığını gösterir. Herhangi bir komut satırı bağımsız değişkenini programa geçirmemiş olduğunuzdan, değeri boş bir dize dizisidir. Ayrıca, Visual Studio boş bir konsol penceresi açtı.

1. **Hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. Visual Studio artık bir sonraki yürütme satırını vurgulamaktadır. Görüntüde gösterildiği gibi, son deyimin ve bunun arasındaki kodu yürütmek için bir milisaniyelik daha az sürdü. `args`, yalnızca belirtilen değişken kalır ve konsol penceresi boş kalır.

   ![Metot kaynağı içinde Visual Studio adımı-C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. **Hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. Visual Studio, `name` değişken atamasını içeren ifadeyi vurgular. **Yereller** penceresi `name` `null`gösterir ve konsol penceresi "adınız nedir?" dizesini görüntüler.

1. Konsol penceresine bir dize girerek ve **ENTER**' a basarak istemi yanıtlayın. Konsol yanıt vermez ve girdiğiniz dize konsol penceresinde gösterilmez, ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi, yine de girişinizi yakalar.

1. **Hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. Visual Studio, `date` değişken atamasını içeren ifadeyi vurgular. **Yereller** penceresi <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemine yapılan çağrı tarafından döndürülen değeri gösterir. Konsol penceresinde, isteminde girdiğiniz dize de görüntülenir.

1. **Hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. **Yereller** penceresi, <xref:System.DateTime.Now?displayProperty=nameWithType> özelliğinden atamadan sonra `date` değişkeninin değerini gösterir. Konsol penceresi değiştirilmez.

1. **Hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> yöntemini çağırır. Konsol penceresi biçimlendirilen dizeyi görüntüler.

1. **Hata ayıkla** > **dışarı adımla** seçeneğini belirleyin veya **SHIFT**+**F11**tuşuna basın. Bu, adım adım yürütmeyi durduruyor. Konsol penceresinde bir ileti görüntülenir ve bir tuşa basmanız bekler.

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve hata ayıklamayı durdurun.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Menü çubuğunda **hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. Visual Studio, sonraki yürütme satırının yanında bir ok görüntüler.

   ![Visual Studio adımla yöntemi-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   Bu noktada, **Yereller** penceresi programınızın yalnızca bir değişken `args`tanımlandığını gösterir. Herhangi bir komut satırı bağımsız değişkenini programa geçirmemiş olduğunuzdan, değeri boş bir dize dizisidir. Ayrıca, Visual Studio boş bir konsol penceresi açtı.

1. **Hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. Visual Studio artık bir sonraki yürütme satırını vurgulamaktadır. Şeklin gösterdiği gibi, son deyimden bu ve arasındaki kodu yürütmek için bir milisaniyelik daha az sürdü. `args`, yalnızca belirtilen değişken kalır ve konsol penceresi boş kalır.

   ![Visual Studio adımla Yöntem kaynağı-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. **Hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. Visual Studio, `name` değişken atamasını içeren ifadeyi vurgular. **Yereller** penceresi `name` `Nothing`gösterir ve konsol penceresi "adınız nedir?" dizesini görüntüler.

1. Konsol penceresine bir dize girerek ve **ENTER**' a basarak istemi yanıtlayın. Konsol yanıt vermez ve girdiğiniz dize konsol penceresinde gösterilmez, ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi, yine de girişinizi yakalar.

1. **Hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. Visual Studio, `currentDate` değişken atamasını içeren ifadeyi vurgular. **Yereller** penceresi <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemine yapılan çağrı tarafından döndürülen değeri gösterir. Konsol penceresi ayrıca konsol giriş isteminde bulunduğunda girilen dizeyi görüntüler.

1. **Hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. Konsol penceresi değiştirilmez.

1. **Hata ayıkla** > **adımla** ' yı seçin veya **F11**tuşuna basın. Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> yöntemini çağırır. Konsol penceresi biçimlendirilen dizeyi görüntüler.

1. **Hata ayıkla** > **dışarı adımla** seçeneğini belirleyin veya **SHIFT**+**F11**tuşuna basın. Bu, adım adım yürütmeyi durduruyor. Konsol penceresinde bir ileti görüntülenir ve bir tuşa basmanız bekler.

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve hata ayıklamayı durdurun.

---

## <a name="build-a-release-version"></a>Yayın sürümü oluşturma

Uygulamanızın hata ayıklama sürümünü sınadıktan sonra yayın sürümünü derleyip test etmeniz gerekir. Yayın sürümü bazen bir uygulamanın davranışını olumsuz yönde etkileyebilecek derleyici iyileştirmeleri içerir. Örneğin, performansı artırmak için tasarlanan derleyici iyileştirmeleri, çok iş parçacıklı uygulamalarda yarış koşulları oluşturabilir.

Konsol uygulamanızın yayın sürümünü derlemek ve test etmek için, araç çubuğundaki derleme yapılandırmasını **Hata Ayıkla** 'dan **Release**olarak değiştirin.

![hata ayıklama vurgulanmış olarak varsayılan Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

**F5** tuşuna bastığınızda veya **Build** menüsünden **çözüm oluştur** ' u seçtiğinizde, Visual Studio uygulamanın yayın sürümünü derler. Hata ayıklama sürümünü yaptığınız gibi test edebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Uygulamanızda hata ayıkladıktan sonra, bir sonraki adım uygulamanın dağıtılabilir bir sürümünü yayımlamaktır. Bunun nasıl yapılacağı hakkında bilgi için bkz. [Visual Studio ile .NET Core Merhaba Dünya uygulamanızı yayımlama](publishing-with-visual-studio.md).
