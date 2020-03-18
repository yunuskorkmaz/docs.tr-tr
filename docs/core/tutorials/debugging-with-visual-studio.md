---
title: Visual Studio ile Hello World .NET Core uygulamanızı hata ayıklama
description: Visual Studio ile C# veya Visual Basic ile yazılmış bir Hello World uygulamasını nasıl hata ayıklamayı öğrenin.
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: b2ee1401fc89f990c5f930d80d1a510a117e63a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156679"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>Visual Studio'yu kullanarak C# veya Visual Basic .NET Core Hello World uygulamanızı hata ayıklama

Şimdiye kadar Visual [Studio 2019'da basit](with-visual-studio.md) bir konsol uygulaması oluşturmak ve çalıştırmak için ilk .NET Core konsol uygulamanızı oluştur adımlarını takip ettiniz. Başvurunuzu yazdıktan ve derledikten sonra, uygulamayı test etmeye başlayabilirsiniz. Visual Studio, uygulamanızı gidermek için kullanabileceğiniz kapsamlı bir hata ayıklama araçları kümesi içerir.

## <a name="debug-build-configuration"></a>Hata ayıklama yapı yapılandırması

*Hata Ayıklama* ve *Sürüm,* Visual Studio'nun varsayılan yapı yapılandırmalarından ikisidir. Geçerli yapı yapılandırması araç çubuğunda gösterilir. Aşağıdaki araç çubuğu görüntüsü Visual Studio'nun uygulamanın Hata Ayıklama sürümünü derlemek üzere yapılandırılmış olduğunu gösterir:

![Hata ayıklama vurgulanan Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Uygulamanızın Hata Ayıklama sürümünü çalıştırarak başlayın. Hata Ayıklama yapı yapılandırması çoğu derleyici optimizasyonunu kapatır ve yapı işlemi sırasında daha zengin bilgiler sağlar.

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

Programınızı çalıştırın ve birkaç hata ayıklama özelliği deneyin:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Satırdaki *breakpoint* kod penceresinin sol `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` kenar boşluğuna tıklayarak okuyan satıra bir kesme noktası ayarlayın. Ayrıca, dikkati kod satırına yerleştirip **F9** tuşuna basarak veya menü çubuğundan **Hata Ayıklama** > **Kesme Noktası'nı** seçerek bir kesme noktası ayarlayabilirsiniz.

   Kesme noktası, kesme noktası yla olan satır yürütülmeden *önce* uygulamanın yürütülmesini geçici olarak keser.

   Aşağıdaki resimde de görüldüğü gibi, Visual Studio kesme noktasının ayarlandığı satırı vurgulayarak ve sol kenar boşluğunda kırmızı bir daire görüntüleyerek gösterir.

   ![Kesme noktası setli Visual Studio Program penceresi](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Araç çubuğundaki yeşil okla **HelloWorld** düğmesini seçerek, **F5**tuşuna basarak veya **Hata** > **Ayıklama Başlatma Hata Ayıklama'yı**seçerek programı Hata Ayıklama modunda çalıştırın.

1. Program bir ad istediğinde konsol penceresine bir dize girin ve sonra **Enter**tuşuna basın.

1. Program yürütme, kesme noktasına ulaştığında ve `Console.WriteLine` yöntem yürütülmeden önce durur. **Yereller** penceresi, şu anda yürütülen yöntemde tanımlanan değişkenlerin değerlerini görüntüler.

   ![Visual Studio'da bir kırılma noktasının ekran görüntüsü](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. **Hemen** penceresi, hata ayıklama yaptığınız uygulamayla etkileşimkurmanızı sağlar. Programınızı nasıl etkilediğini görmek için değişkenlerin değerini etkileşimli olarak değiştirebilirsiniz.

   1. **Hemen** penceresi görünmüyorsa, **Hata Ayıklama** > **Windows** > **Immediate'ı**seçerek görüntüleyin.

   1. `name = "Gracie"` **Hemen** penceresine girin ve **Enter** tuşuna basın.

   1. `date = DateTime.Parse("11/16/2019 5:25 PM")` **Hemen** penceresine girin ve **Enter** tuşuna basın.

   **Hemen** penceresi dize değişkeninin değerini ve <xref:System.DateTime> değerin özelliklerini görüntüler. Ayrıca, değişkenlerin değerleri **Yereller** penceresinde güncelleştirilir.

   ![Visual Studio 2019'da Yerel Halk ve Acil Windows](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Araç çubuğundaki **Continue** düğmesini seçerek veya Hata **Ayıklama** > Devam'ı seçerek program yürütmeye devam**edin.** Konsol penceresinde görüntülenen **değerler, Hemen** penceresinde yaptığınız değişikliklere karşılık gelir.

   ![Girilen değerleri gösteren konsol penceresi](./media/debugging-with-visual-studio/console-window.png)

1. Uygulamadan çıkmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Satırdaki *breakpoint* kod penceresinin sol `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` kenar boşluğuna tıklayarak okuyan satıra bir kesme noktası ayarlayın. Ayrıca, caret'i istenilen satıra yerleştirip menü çubuğundan **Hata Ayıklama** > **Kesme Noktası'nı** seçerek bir kesme noktası ayarlayabilirsiniz.

   Kesme noktası, kesme noktası yla olan satır yürütülmeden *önce* uygulamanın yürütülmesini geçici olarak keser.

   Aşağıdaki şekilde nisması yla Visual Studio, kesme noktasının ayarlandığı satırı vurgulayarak ve sol kenar boşluğunda kırmızı bir daire görüntüleyerek gösterir.

   ![Kesme noktası setli Visual Studio Program penceresi](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. Araç çubuğundaki yeşil okla **HelloWorld** düğmesini seçerek, **F5**tuşuna basarak veya **Hata** > **Ayıklama Başlatma Hata Ayıklama'yı**seçerek programı Hata Ayıklama modunda çalıştırın.

1. Program bir ad istediğinde konsol penceresine bir dize girin ve **Enter**tuşuna basın.

1. Program yürütme, kesme noktasına ulaştığında ve `Console.WriteLine` yöntem yürütülmeden önce durur. **Yereller** penceresi, şu anda yürütülen yöntemde tanımlanan değişkenlerin değerlerini görüntüler.

1. **Hemen** penceresi, hata ayıklama yaptığınız uygulamayla etkileşimkurmanızı sağlar. Programınızı nasıl etkilediğini görmek için değişkenlerin değerini etkileşimli olarak değiştirebilirsiniz.

   1. **Hemen** penceresi görünmüyorsa, **Hata Ayıklama** > **Windows** > **Immediate'ı**seçerek görüntüleyin.

   1. `name = "Gracie"` **Hemen** penceresine girin ve **Enter** tuşuna basın.

   1. `date = DateTime.Parse("11/16/2019 5:25 PM")` **Hemen** penceresine girin ve **Enter** tuşuna basın.

   Değişkenlerin değerleri **Yereller** penceresinde güncelleştirilir.

1. Araç çubuğundaki **Continue** düğmesini seçerek veya **Hata Ayıklama** > **Devam** menüsü öğesini seçerek program yürütmeye devam edin. Konsol penceresinde görüntülenen **değerler, Hemen** penceresinde yaptığınız değişikliklere karşılık gelir.

   ![Girilen değerleri gösteren konsol penceresi](./media/debugging-with-visual-studio/console-window.png)

1. Uygulamadan çıkmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.

---

## <a name="set-a-conditional-breakpoint"></a>Koşullu bir kesme noktası ayarlama

Programınız kullanıcının girdiği dizeyi görüntüler. Kullanıcı bir şey girmezse ne olur? Bunu, bir veya daha fazla koşul yerine getirildiğinde program yürütmesini bozan *koşullu kesme noktası*adı verilen yararlı bir hata ayıklama özelliğiyle sınayabilirsiniz.

Koşullu bir kesme noktası ayarlamak ve kullanıcı dize giremediğinde ne olacağını sınamak için aşağıdakileri yapın:

# <a name="c"></a>[C #](#tab/csharp)

1. Kesme noktasını temsil eden kırmızı noktanın üzerine sağ tıklayın. Bağlam menüsünde, Kesme Noktası **Ayarları** iletişim kutusunu açmak için **Koşullar'ı** seçin. Zaten seçilmemişse **Koşullar** kutusunu işaretleyin.

   ![Kesme noktası ayarları panelini gösteren düzenleyici - C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. **Koşullu İfade**için "örneğin x == 5" yerine aşağıdakileri değiştirin:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Bir kod koşulu için sınama `String.IsNullOrEmpty(name)` konum, `true` yöntem `name` çağrısı ya bir değer atanmamış ya da değeri boş bir dize (""") olduğu için. Koşullu bir ifade yerine, bir deyim belirli sayıda yürütülmeden önce program yürütmeyi kesintiye uğratan bir *isabet sayısı*veya iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı gibi özniteliklere dayalı olarak program yürütmesini kesintiye uğratan bir *filtre koşulu*da belirtebilirsiniz.

1. İletişim kutusunu kapatmak için **Kapat'ı** seçin.

1. **F5**tuşuna basarak hata ayıklama ile programı başlatın.

1. Konsol penceresinde, adınızı girmeniz istendiğinde **Enter** tuşuna basın.

1. Belirttiğiniz `name` koşul, ya `null` veya <xref:System.String.Empty?displayProperty=nameWithType>, memnun olduğundan, program yürütme kesme noktasına ulaştığında `Console.WriteLine` ve yöntem yürütülmeden önce durur.

1. Şu anda yürütülen yönteme yerel olan değişkenlerin değerlerini gösteren **Yerel ler** penceresini seçin. Bu durumda, `Main` şu anda yürütülen yöntemdir. `name` Değişkenin değerinin `""`, veya <xref:System.String.Empty?displayProperty=nameWithType>.

1. **Hemen** penceresine aşağıdaki ifadeyi girerek ve **Enter**tuşuna basarak değerin boş bir dize olduğunu doğrulayın. Sonuç. `true`

   ```csharp
   ? name == String.Empty
   ```

   ![İfade yürütüldükten sonra doğru bir değeri döndüren Anında Pencere - C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Program yürütmeye devam etmek için araç çubuğundaki **Devam** et düğmesini seçin.

1. Konsol penceresini kapatmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.

1. Kod penceresinin sol kenar boşluğundaki noktayı tıklatarak veya kod satırı seçilirken **Hata Ayıklama > Toggle Breakpoint'i** seçerek kesme noktasını temizleyin.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Kesme noktasını temsil eden kırmızı noktanın üzerine sağ tıklayın. Bağlam menüsünde, Kesme Noktası **Ayarları** iletişim kutusunu açmak için **Koşullar'ı** seçin. **Koşullar**için kutuyu işaretleyin.

   ![Kesme noktası ayarları panelini gösteren düzenleyici - Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. **Koşullu İfade** için "örneğin x = 5" yerine aşağıdakileri aşar:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Bir kod koşulu için sınama `String.IsNullOrEmpty(name)` konum, `true` yöntem `name` çağrısı ya bir değer atanmamış ya da değeri boş bir dize (""") olduğu için. Koşullu bir ifade yerine, bir deyim belirli sayıda yürütülmeden önce program yürütmeyi kesintiye uğratan bir *isabet sayısı*veya iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı gibi özniteliklere dayalı olarak program yürütmesini kesintiye uğratan bir *filtre koşulu*da belirtebilirsiniz.

1. İletişim kutusunu kapatmak için **Kapat'ı** seçin.

1. **F5**tuşuna basarak hata ayıklama ile programı başlatın.

1. Konsol penceresinde, adınızı girmeniz istendiğinde **Enter** tuşuna basın.

1. Belirttiğiniz `name` koşul, ya `null` veya <xref:System.String.Empty?displayProperty=nameWithType>, memnun olduğundan, program yürütme kesme noktasına ulaştığında `Console.WriteLine` ve yöntem yürütülmeden önce durur.

1. Şu anda yürütülen yönteme yerel olan değişkenlerin değerlerini gösteren **Yerel ler** penceresini seçin. Bu durumda, `Main` şu anda yürütülen yöntemdir. `name` Değişkenin değerinin `""`, veya <xref:System.String.Empty?displayProperty=nameWithType>.

1. **Hemen** penceresine aşağıdaki ifadeyi girerek ve **Enter**tuşuna basarak değerin boş bir dize olduğunu doğrulayın. Sonuç. `true`

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![İfade yürütüldükten sonra doğru bir değeri döndüren Anında Pencere - Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. Program yürütmeye devam etmek için araç çubuğundaki **Devam** et düğmesini seçin.

1. Konsol penceresini kapatmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.

1. Kod penceresinin sol kenar boşluğundaki noktayı tıklatarak veya seçili satırla **Hata Ayıklama > Toggle Breakpoint** menü öğesini seçerek kesme noktasını temizleyin.

---
## <a name="step-through-a-program"></a>Bir programda adım atma

Visual Studio ayrıca bir program aracılığıyla satır satır adım ve yürütülmesini izlemek için izin verir. Normalde, bir kesme noktası ayarlar ve program kodunuzu küçük bir bölümünde program akışını izlemek için bu özelliği kullanırsınız. Programınız küçük olduğundan, tüm programı gözden geçirebilirsiniz:

# <a name="c"></a>[C #](#tab/csharp)

1. Menü çubuğunda **Hata Ayıklama** > **Adımını** seçin veya **F11 tuşuna**basın. Visual Studio vurgular ve yürütme sonraki satırı yanında bir ok görüntüler.

   ![Visual Studio metodiçine adım - C #](./media/debugging-with-visual-studio/step-into-method.png)

   Bu noktada, **Yerel Ler** penceresi programınızın yalnızca bir `args`değişken tanımladığını gösterir. Programa herhangi bir komut satırı bağımsız değişkeni geçirmediğiniz için, değeri boş bir dize dizisidir. Buna ek olarak, Visual Studio boş bir konsol penceresi açtı.

1. **Hata Ayıklama** > **Adım Adım'ı** seçin veya **F11 tuşuna**basın. Visual Studio şimdi yürütme sonraki satırı vurgulamaktadır. Görüntünün gösterdiği gibi, son deyim le bu ifade arasındaki kodu yürütmek bir milisaniyeden az sürmüştür. `args`bildirilen tek değişken kalır ve konsol penceresi boş kalır.

   ![Yöntem kaynağında Visual Studio adımı - C #](./media/debugging-with-visual-studio/step-into-source-method.png)

1. **Hata Ayıklama** > **Adım Adım'ı** seçin veya **F11 tuşuna**basın. Visual Studio `name` değişken atama içeren deyimi vurgular. **Locals** penceresi bunun `name` `null`olduğunu gösterir ve konsol penceresi "Adınız nedir?" dizesini görüntüler.

1. Konsol penceresine bir dize girerek ve **Enter**tuşuna basarak istemi yanıtlayın. Konsol yanıt vermiyor ve girdiğiniz dize konsol penceresinde görüntülenmiyor, <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> ancak yöntem yine de girişinizi yakalar.

1. **Hata Ayıklama** > **Adım Adım'ı** seçin veya **F11 tuşuna**basın. Visual Studio `date` değişken atama içeren deyimi vurgular. **Yerel ler** penceresi, <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yönteme yapılan çağrıyla döndürülen değeri gösterir. Konsol penceresi, istem sırasında girdiğiniz dizeyi de görüntüler.

1. **Hata Ayıklama** > **Adım Adım'ı** seçin veya **F11 tuşuna**basın. **Yereller** penceresi, <xref:System.DateTime.Now?displayProperty=nameWithType> özellikten `date` atama dan sonra değişkenin değerini gösterir. Konsol penceresi değişmedi.

1. **Hata Ayıklama** > **Adım Adım'ı** seçin veya **F11 tuşuna**basın. Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> yöntemi çağırır. Konsol penceresi biçimlendirilmiş dizeyi görüntüler.

1. **Hata Ayıklama** > **Adım At'ı** seçin veya **Shift**+**F11 tuşuna**basın. Bu, adım adım yürütmeyi durdurur. Konsol penceresi bir ileti görüntüler ve bir tuşa basmanızı bekler.

1. Konsol penceresini kapatmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Menü çubuğunda **Hata Ayıklama** > **Adımını** seçin veya **F11 tuşuna**basın. Visual Studio vurgular ve yürütme sonraki satırı yanında bir ok görüntüler.

   ![Visual Studio metoda adım - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   Bu noktada, **Yerel Ler** penceresi programınızın yalnızca bir `args`değişken tanımladığını gösterir. Programa herhangi bir komut satırı bağımsız değişkeni geçirmediğiniz için, değeri boş bir dize dizisidir. Buna ek olarak, Visual Studio boş bir konsol penceresi açtı.

1. **Hata Ayıklama** > **Adım Adım'ı** seçin veya **F11 tuşuna**basın. Visual Studio şimdi yürütme sonraki satırı vurgulamaktadır. Şekilde ki gibi, son deyim ve bu arasında kodu yürütmek için bir milisaniyeden az sürmüştür. `args`bildirilen tek değişken kalır ve konsol penceresi boş kalır.

   ![Visual Studio yöntem kaynağına adım - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. **Hata Ayıklama** > **Adım Adım'ı** seçin veya **F11 tuşuna**basın. Visual Studio `name` değişken atama içeren deyimi vurgular. **Locals** penceresi bunun `name` `Nothing`olduğunu gösterir ve konsol penceresi "Adınız nedir?" dizesini görüntüler.

1. Konsol penceresine bir dize girerek ve **Enter**tuşuna basarak istemi yanıtlayın. Konsol yanıt vermiyor ve girdiğiniz dize konsol penceresinde görüntülenmiyor, <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> ancak yöntem yine de girişinizi yakalar.

1. **Hata Ayıklama** > **Adım Adım'ı** seçin veya **F11 tuşuna**basın. Visual Studio `currentDate` değişken atama içeren deyimi vurgular. **Yerel ler** penceresi, <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yönteme yapılan çağrıyla döndürülen değeri gösterir. Konsol penceresi, konsol giriş istendiğinde girilen dizeyi de görüntüler.

1. **Hata Ayıklama** > **Adım Adım'ı** seçin veya **F11 tuşuna**basın. Konsol penceresi değişmedi.

1. **Hata Ayıklama** > **Adım Adım'ı** seçin veya **F11 tuşuna**basın. Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> yöntemi çağırır. Konsol penceresi biçimlendirilmiş dizeyi görüntüler.

1. **Hata Ayıklama** > **Adım At'ı** seçin veya **Shift**+**F11 tuşuna**basın. Bu, adım adım yürütmeyi durdurur. Konsol penceresi bir ileti görüntüler ve bir tuşa basmanızı bekler.

1. Konsol penceresini kapatmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.

---

## <a name="build-a-release-version"></a>Sürüm sürümü oluşturma

Uygulamanızın Hata Ayıklama sürümünü test ettikten sonra, Sürüm sürümünü de derlemeniz ve test edinmelisiniz. Sürüm sürümü, bazen bir uygulamanın davranışını olumsuz etkileyebilecek derleyici optimizasyonlarını içerir. Örneğin, performansı artırmak için tasarlanmış derleyici optimizasyonları çok iş parçacığı uygulamalarında yarış koşulları oluşturabilir.

Konsol uygulamanızın Sürüm sürümünü oluşturmak ve sınamak için, araç çubuğundaki yapı yapılandırmasını **Hata Ayıklama'dan** **Sürüm'e**değiştirin.

![hata ayıklama vurgulanan varsayılan Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

**F5 tuşuna** bastığında veya **Yapı** menüsünden **Çözüm Oluştur'u** seçtiğinizde, Visual Studio uygulamanın Sürüm sürümünü derler. Hata Ayıklama sürümünü yaptığınız gibi test edebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Uygulamanızı debugged sonra, bir sonraki adım uygulamanın dağıtılabilir bir sürümünü yayımlamaktır. Bunun nasıl yapılabildiğini öğrenmek için [bkz.](publishing-with-visual-studio.md)
