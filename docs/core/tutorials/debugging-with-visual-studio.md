---
title: Visual Studio 2017 ile Merhaba Dünya .NET Core uygulamanızda hata ayıklama
description: Visual Studio 2017 ile C# veya Visual Basic yazılmış Merhaba Dünya bir uygulamada hata ayıklamayı öğrenin.
ms.date: 12/15/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 7239ca52c0b90c4cfacd68581f569b9ac7d70eae
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969387"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio-2017"></a>Visual Studio 2017’yi kullanarak C# veya Visual Basic .NET Core Merhaba Dünya uygulamanızda hata ayıklama

Şimdiye kadar, [Visual studio 2017 ' de .NET Core ile C# Merhaba Dünya bir uygulama](with-visual-studio.md) oluşturma veya basit bir konsol uygulaması oluşturup çalıştırmak için [Visual Studio 2017 ' de .NET Core ile Visual Basic Merhaba Dünya uygulaması derleme](vb-with-visual-studio.md) bölümündeki adımları izlediyseniz. Uygulamanızı yazdıktan ve derledikten sonra test etmeye başlayabilirsiniz. Visual Studio, uygulamanızı test ederken ve sorunlarını giderirken kullanabileceğiniz kapsamlı bir hata ayıklama araçları kümesi içerir. 

## <a name="debugging-in-debug-mode"></a>Hata ayıklama modunda hata ayıklama

*Hata ayıklama* ve *yayın* , Visual Studio 'nun varsayılan derleme yapılandırmasından ikdir. Geçerli derleme yapılandırması araç çubuğunda gösterilir. Aşağıdaki araç çubuğu görüntüsü, Visual Studio 'Nun uygulamanızı **hata ayıklama** modunda derlemek üzere yapılandırıldığını gösterir.

   ![hata ayıklama vurgulanmış olarak varsayılan Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Programınızı hata ayıklama modunda test ederek her zaman başlamanız gerekir. Hata ayıklama modu çoğu derleyici iyileştirmesini kapatır ve derleme işlemi sırasında daha zengin bilgiler sağlar.

## <a name="setting-a-breakpoint"></a>Bir kesme noktası ayarlama

Programınızı hata ayıklama modunda çalıştırın ve birkaç hata ayıklama özelliğini deneyin:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Kesme *noktası,* kesme noktası olan satır yürütülmeden *önce* uygulamanın yürütülmesini geçici olarak keser. 

   Bu satırdaki kod penceresinin sol kenar boşluğuna tıklayarak `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` veya seçili satırı içeren **hata ayıklama** > **kesme noktası göster** menü öğesini seçerek okunan satırda bir kesme noktası ayarlayın. Aşağıdaki şekilde gösterildiği gibi, Visual Studio, kesme noktasının ayarlandığı ve sol kenar boşluğunda kırmızı bir daire görüntülendiği satırı gösterir.

   ![Kesme noktası ayarlanmış Visual Studio program penceresi](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Araç çubuğunda yeşil ok ile **HelloWorld** düğmesini seçip F5 tuşuna basarak veya hata**ayıklamayı Başlat hata** **Ayıkla** > ' yı seçerek programı hata ayıklama modunda çalıştırın.

1. Program bir ad isteminde bulunduğunda konsol penceresine bir dize girin ve ENTER 'a basın.

1. Program yürütme, kesme noktasına ulaştığında ve `Console.WriteLine` Yöntem yürütmeden önce duraklar. **Oto** penceresi, geçerli satır etrafında kullanılan değişkenlerin değerlerini görüntüler. **Yereller** penceresi ( **Yereller** sekmesine tıklayarak görüntüleyebileceğiniz), şu anda yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler.

   ![Visual Studio 'da bir kesme noktasının ekran görüntüsü.](./media/debugging-with-visual-studio/breakpoint-console-window.png)

1. Programınızı nasıl etkilediğini görmek için değişkenlerin değerini değiştirebilirsiniz. **Komut penceresi** görünür değilse,**Windows** > 'u **Hata Ayıkla** > **menü öğesini** seçerek bunu görüntüleyin. **Komut penceresi** , hata ayıklamanıza çalıştığınız uygulamayla etkileşime girebilmenizi sağlar.

1. Değişkenlerin değerlerini etkileşimli bir şekilde değiştirebilirsiniz. `name = "Gracie"` **Hemen penceresine** girip ENTER tuşuna basın.

1. `date = new DateTime(2016,11,01,11,59,00)` **Hemen penceresine** girip ENTER tuşuna basın.

   **Komut penceresi** , dize değişkeninin değerini ve <xref:System.DateTime> değerin özelliklerini görüntüler. Ayrıca, değişkenlerin değeri, **oto** ve **Yereller** pencerelerinde güncelleştirilir.

   ![Oto penceresi ve hemen penceresi](./media/debugging-with-visual-studio/autos-immediate-window.png)

1. Araç çubuğundaki **devam** düğmesini seçerek veya **Hata Ayıkla** > **devam et** menü öğesini seçerek program yürütmeye devam edin. Konsol penceresinde görünen değerler, **hemen penceresinde**yaptığınız değişikliklere karşılık gelir.

   ![Adınızın adı ne olacak olan değer jakını gösteren konsol penceresi istem ve ardından Hello Gracıe](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Uygulamadan çıkmak ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Kesme *noktası,* kesme noktası olan satır yürütülmeden *önce* uygulamanın yürütülmesini geçici olarak keser. 

   Bu satırdaki kod penceresinin sol kenar boşluğuna tıklayarak `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` veya seçili satırı içeren **hata ayıklama** > **kesme noktası göster** menü öğesini seçerek okunan satırda bir kesme noktası ayarlayın. Aşağıdaki şekilde gösterildiği gibi, Visual Studio, kesme noktasının ayarlandığı ve sol kenar boşluğunda kırmızı bir daire görüntülendiği satırı gösterir.

   ![Kesme noktası ayarlanmış Visual Studio program penceresi](./media/debugging-with-visual-studio/vb-set-breakpoint-in-editor.png)

1. Araç çubuğunda yeşil ok ile **HelloWorld** düğmesini seçip F5 tuşuna basarak veya hata**ayıklamayı Başlat hata** **Ayıkla** > ' yı seçerek programı hata ayıklama modunda çalıştırın.

1. Program bir ad isteminde bulunduğunda konsol penceresine bir dize girin ve ENTER 'a basın.

1. Program yürütme, kesme noktasına ulaştığında ve `Console.WriteLine` Yöntem yürütmeden önce duraklar. **Oto** penceresi, geçerli satır etrafında kullanılan değişkenlerin değerlerini görüntüler. **Yereller** penceresi ( **Yereller** sekmesine tıklayarak görüntüleyebileceğiniz), şu anda yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler.

   ![Kesme noktasında Visual Studio uygulama penceresi](./media/debugging-with-visual-studio/vb-stop-at-breakpoint.png)

1. Programınızı nasıl etkilediğini görmek için değişkenlerin değerini değiştirebilirsiniz. **Komut penceresi** görünür değilse,**Windows** > 'u **Hata Ayıkla** > **menü öğesini** seçerek bunu görüntüleyin. **Komut penceresi** , hata ayıklamanıza çalıştığınız uygulamayla etkileşime girebilmenizi sağlar.

1. Değişkenlerin değerlerini etkileşimli bir şekilde değiştirebilirsiniz. `name = "Gracie"` **Hemen penceresine** girip ENTER tuşuna basın.

1. `currentDate = new DateTime(2016,11,01,11,59,00)` **Hemen penceresine** girip ENTER tuşuna basın.

1. Araç çubuğundaki **devam** düğmesini seçerek veya **Hata Ayıkla** > **devam et** menü öğesini seçerek program yürütmeye devam edin. Konsol penceresinde görünen değerler, **hemen penceresinde**yaptığınız değişikliklere karşılık gelir.

   ![Ilk pencerede girilen değiştirilen değerleri gösteren konsol penceresi](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Uygulamadan çıkmak ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.

---

## <a name="setting-a-conditional-breakpoint"></a>Koşullu kesme noktası ayarlama

Programınız kullanıcının girdiği dizeyi görüntüler. Kullanıcı hiçbir şey girmezse ne olur? Bunu, bir veya daha fazla koşul karşılandığında programın yürütülmesini kesen, *koşullu kesme noktası*olan yararlı bir hata ayıklama özelliği ile test edebilirsiniz.

Koşullu bir kesme noktası ayarlamak ve Kullanıcı bir dize giremediğinde ne olacağını sınamak için aşağıdakileri yapın:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Kesme noktasını temsil eden kırmızı noktaya sağ tıklayın. Bağlam menüsünde **koşullar** ' ı seçerek **kesme noktası ayarları** iletişim kutusunu açın. **Koşullar**kutusunu işaretleyin.

   ![Kesme noktası ayarları panelini gösteren düzenleyici-C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. **Koşullu ifade** için, "ör. x = = 5" yerine şunları yapın:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Bir kod koşulu için test ediliyoruz, `String.IsNullOrEmpty(name)` `true` çünkü *Name* değeri bir değer atanmamış ya da değeri boş bir dize ("") olduğundan. Ayrıca *, bir*deyimin belirtilen sayıda yürütülmesi için program yürütmeyi kesintiye uğramadan veya bir *filtre koşulunu*da belirtebilir ve bu da bir iş parçacığı tanımlayıcısı olarak bu tür özniteliklere göre program yürütmeyi kesintiye uğratır. ad veya iş parçacığı adı.

1. İletişim kutusunu kapatmak için **Kapat** düğmesini seçin.

1. Programı hata ayıklama modunda çalıştırın.

1. Konsol penceresinde, adınızı girmeniz istendiğinde ENTER tuşuna basın.

1. Belirttiğimiz `name` `Console.WriteLine` koşul veya <xref:System.String.Empty?displayProperty=nameWithType>karşılanmadığıiçin, program yürütme, kesme noktasına ulaştığında ve Yöntem yürütülmeden önce durduktan sonra durduruluyor. `null`

1. Programdaki `Main` yöntemi olan şu anda yürütülmekte olan yönteme ait değişkenlerin değerlerini gösteren **Yereller** penceresini seçin. `name` Değişkenin değerinin veya `""` olduğunugözlemleyin.<xref:System.String.Empty?displayProperty=nameWithType>

1. Aşağıdaki ifadeyi **komut penceresine**girerek değerin boş bir dize olduğunu onaylayın. Sonuç olarak `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Deyimden sonra true değeri döndüren komut penceresi-C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Program yürütmeye devam etmek için araç çubuğundaki **devam** düğmesini seçin.

1. Konsol penceresini kapatmak ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.

1. Kod penceresinin sol kenarındaki noktaya tıklayarak veya seçili satırı içeren bir **hata ayıkla > geçiş noktası** menü öğesini seçerek kesme noktasını temizleyin.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Kesme noktasını temsil eden kırmızı noktaya sağ tıklayın. Bağlam menüsünde **koşullar** ' ı seçerek **kesme noktası ayarları** iletişim kutusunu açın. **Koşullar**kutusunu işaretleyin.

   ![Kesme noktası ayarları panelini gösteren düzenleyici-Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. **Koşullu ifade** için, "ör. x = 5" yerine şunu yapın:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Bir kod koşulu için test ediliyoruz, `String.IsNullOrEmpty(name)` `True` çünkü *Name* değeri bir değer atanmamış ya da değeri boş bir dize ("") olduğundan. Ayrıca *, bir*deyimin belirtilen sayıda yürütülmesi için program yürütmeyi kesintiye uğramadan veya bir *filtre koşulunu*da belirtebilir ve bu da bir iş parçacığı tanımlayıcısı olarak bu tür özniteliklere göre program yürütmeyi kesintiye uğratır. ad veya iş parçacığı adı.

1. İletişim kutusunu kapatmak için **Kapat** düğmesini seçin.

1. Programı hata ayıklama modunda çalıştırın.

1. Konsol penceresinde, adınızı girmeniz istendiğinde ENTER tuşuna basın.

1. Belirttiğimiz `name` `Console.WriteLine` koşul veya <xref:System.String.Empty?displayProperty=nameWithType>karşılanmadığıiçin, program yürütme, kesme noktasına ulaştığında ve Yöntem yürütülmeden önce durduktan sonra durduruluyor. `null`

1. Programdaki `Main` yöntemi olan şu anda yürütülmekte olan yönteme ait değişkenlerin değerlerini gösteren **Yereller** penceresini seçin. `name` Değişkenin değerinin veya `""` olduğunugözlemleyin.<xref:System.String.Empty?displayProperty=nameWithType>

1. Aşağıdaki ifadeyi **komut penceresine**girerek değerin boş bir dize olduğunu onaylayın. Sonuç olarak `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

  ![Deyimden sonra true değeri döndüren komut penceresi-Visual Basic](./media/debugging-with-visual-studio/vb-immediate-window-output.png)

1. Program yürütmeye devam etmek için araç çubuğundaki **devam** düğmesini seçin.

1. Konsol penceresini kapatmak ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.

1. Kod penceresinin sol kenarındaki noktaya tıklayarak veya seçili satırı içeren bir **hata ayıkla > geçiş noktası** menü öğesini seçerek kesme noktasını temizleyin.

---
## <a name="stepping-through-a-program"></a>Program aracılığıyla adımla

Visual Studio Ayrıca, bir program aracılığıyla satıra göre çizgi ve yürütmeyi izlemeye de olanak tanır. Normalde, bir kesme noktası ayarlarsınız ve program kodunuzun küçük bir bölümünde program akışını izlemek için bu özelliği kullanabilirsiniz. Programınız küçük olduğundan, aşağıdakileri yaparak programın tamamında adım adım ilerleyerek izleyebilirsiniz:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Menü çubuğunda, **hata ayıklama** > **adımı** ' nı seçin veya F11 tuşuna basın. Visual Studio, sonraki yürütme satırının yanında bir ok görüntüler.

   ![Visual Studio adımla yöntemi-C#](./media/debugging-with-visual-studio/step-into-method.png)

   Bu noktada, programlarınızın yalnızca bir değişken `args`tanımladığınıza ilişkin bir pencere görüntülenir. Herhangi bir komut satırı bağımsız değişkenini programa geçirmemiş olduğunuzdan, değeri boş bir dize dizisidir. Ayrıca, Visual Studio boş bir konsol penceresi açtı.

1. **Hata ayıklama** > **adımını** seçin veya F11 tuşuna basın. Visual Studio artık bir sonraki yürütme satırını vurgulamaktadır. Şeklin gösterdiği gibi, son deyimden bu ve arasındaki kodu yürütmek için bir milisaniyelik daha az sürdü. `args`yalnızca belirtilen değişken kalır ve konsol penceresi boş kalır.

   ![Metot kaynağı içinde Visual Studio adımı-C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. **Hata ayıklama** > **adımını** seçin veya F11 tuşuna basın. Visual Studio, `name` değişken atamasını içeren ifadeyi vurgular. Bu **pencere,** olduğunu `name` `null`gösterir ve konsol penceresi "adınız nedir?" dizesini görüntüler.

1. Konsol penceresine bir dize girerek ve ENTER ' a basarak istemi yanıtlayın. Konsol yanıt vermez ve girdiğiniz dize konsol penceresinde gösterilmez, ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Yöntem, yine de girişinizi yakalar.

1. **Hata ayıklama** > **adımını** seçin veya F11 tuşuna basın. Visual Studio, `date` (içinde C#) veya `currentDate` (Visual Basic) değişken atamasını içeren ifadeyi vurgular. **Oto** penceresinde, <xref:System.DateTime.Now?displayProperty=nameWithType> Özellik değeri ve <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemine yapılan çağrı tarafından döndürülen değer gösterilir. Konsol penceresi ayrıca konsol giriş isteminde bulunduğunda girilen dizeyi görüntüler.

1. **Hata ayıklama** > **adımını** seçin veya F11 tuşuna basın. **Oto** penceresinde, `date` <xref:System.DateTime.Now?displayProperty=nameWithType> özelliğin atamasından sonra değişkenin değeri gösterilir. Konsol penceresi değiştirilmez.

1. **Hata ayıklama** > **adımını** seçin veya F11 tuşuna basın. Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> yöntemini çağırır. `date` (Veya `currentDate`) ve`name` değişkenlerinin değerleri, **oto** penceresinde görünür ve konsol penceresinde biçimlendirilen dize görüntülenir.

1. **Hata ayıklama** > **adımını kapat** ' ı seçin veya SHIFT tuşuna ve F11 tuşuna basın. Bu, adım adım yürütmeyi durduruyor. Konsol penceresinde bir ileti görüntülenir ve bir tuşa basmanız bekler.

1. Konsol penceresini kapatmak ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Menü çubuğunda, **hata ayıklama** > **adımı** ' nı seçin veya F11 tuşuna basın. Visual Studio, sonraki yürütme satırının yanında bir ok görüntüler.

   ![Visual Studio adımla yöntemi-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   Bu noktada, programa herhangi bir komut satırı bağımsız değişkeni geçirmediği için, **oto** , `args` değişkenin değerinin boş bir dize dizisi olduğunu gösterir. Ayrıca, Visual Studio boş bir konsol penceresi açtı.

1. **Hata ayıklama** > **adımını** seçin veya F11 tuşuna basın. Visual Studio artık bir sonraki yürütme satırını vurgulamaktadır. Şeklin gösterdiği gibi, son deyimden bu ve arasındaki kodu yürütmek için bir milisaniyelik daha az sürdü. `args`yalnızca belirtilen değişken kalır ve konsol penceresi boş kalır.

   ![Visual Studio adımla Yöntem kaynağı-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. **Hata ayıklama** > **adımını** seçin veya F11 tuşuna basın. Visual Studio, `name` değişken atamasını içeren ifadeyi vurgular. Bu **pencere,** olduğunu `name` `Nothing`gösterir ve konsol penceresi "adınız nedir?" dizesini görüntüler.

1. Konsol penceresine bir dize girerek ve ENTER ' a basarak istemi yanıtlayın. Konsol yanıt vermez ve girdiğiniz dize konsol penceresinde gösterilmez, ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Yöntem, yine de girişinizi yakalar.

1. **Hata ayıklama** > **adımını** seçin veya F11 tuşuna basın. Visual Studio, `date` (içinde C#) veya `currentDate` (Visual Basic) değişken atamasını içeren ifadeyi vurgular. **Oto** penceresinde, <xref:System.DateTime.Now?displayProperty=nameWithType> Özellik değeri ve <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemine yapılan çağrı tarafından döndürülen değer gösterilir. Konsol penceresi ayrıca konsol giriş isteminde bulunduğunda girilen dizeyi görüntüler.

1. **Hata ayıklama** > **adımını** seçin veya F11 tuşuna basın. **Oto** penceresinde, `date` <xref:System.DateTime.Now?displayProperty=nameWithType> özelliğin atamasından sonra değişkenin değeri gösterilir. Konsol penceresi değiştirilmez.

1. **Hata ayıklama** > **adımını** seçin veya F11 tuşuna basın. Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> yöntemini çağırır. `date` (Veya `currentDate`) ve`name` değişkenlerinin değerleri, **oto** penceresinde görünür ve konsol penceresinde biçimlendirilen dize görüntülenir.

1. **Hata ayıklama** > **adımını kapat** ' ı seçin veya SHIFT tuşuna ve F11 tuşuna basın. Bu, adım adım yürütmeyi durduruyor. Konsol penceresinde bir ileti görüntülenir ve bir tuşa basmanız bekler.

1. Konsol penceresini kapatmak ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.

---

## <a name="building-a-release-version"></a>Yayın sürümü oluşturma

Uygulamanızın hata ayıklama derlemesini sınadıktan sonra yayın sürümünü derleyip test etmeniz gerekir. Yayın sürümü bazen bir uygulamanın davranışını olumsuz yönde etkileyebilecek derleyici iyileştirmeleri içerir. Örneğin, performansı artırmak için tasarlanan derleyici iyileştirmeleri, zaman uyumsuz veya çok iş parçacıklı uygulamalarda yarış koşulları oluşturabilir.

Konsol uygulamanızın yayın sürümünü derlemek ve test etmek için, araç çubuğundaki derleme yapılandırmasını **Hata Ayıkla** 'dan **Release**olarak değiştirin.

![hata ayıklama vurgulanmış olarak varsayılan Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

F5 tuşuna bastığınızda veya **Build** menüsünden **çözüm oluştur** ' u seçtiğinizde, Visual Studio konsol uygulamanızın yayın sürümünü derler. Uygulamanın hata ayıklama sürümünü yaptığınız gibi test edebilirsiniz.

Uygulamanızda hata ayıklamayı tamamladıktan sonra, bir sonraki adım uygulamanızın dağıtılabilir bir sürümünü yayımlamaktır. Bunun nasıl yapılacağı hakkında bilgi için bkz. [Merhaba Dünya uygulamasını Visual Studio Ile yayımlama 2017](publishing-with-visual-studio.md).
