---
title: Visual Studio 2017 ile C# veya Visual Basic Hello World .NET Core uygulamanızda hata ayıklama
description: C# veya Visual Basic Visual Studio 2017 ile yazılmış bir Hello World uygulama hata ayıklama öğrenin.
author: BillWagner
ms.author: wiwagn
ms.date: 12/15/2017
ms.openlocfilehash: 3c130c2eebdf79c1db171cb2171aa68dfff728a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="debug-your-hello-world-application-with-visual-studio-2017"></a>Visual Studio 2017 ile Hello World uygulamanızda hata ayıklama

Şu ana kadar adımları izledikten [bir C# Hello World uygulaması ile Visual Studio 2017 .NET Core yapı](.\with-visual-studio.md) veya [bir Visual Basic Hello World uygulaması ile Visual Studio 2017 .NET Core yapı](vb-with-visual-studio.md) oluşturmak için ve basit bir konsol uygulaması çalıştırın. Yazılan ve uygulamanızı derlenmiş sonra sınama başlayabilirsiniz. Visual Studio test etme ve sorun giderme uygulamanızı kullanabileceğiniz araçlar hata ayıklama kapsamlı kümesi içerir.

## <a name="debugging-in-debug-mode"></a>Hata ayıklama modunda hata ayıklama

*Hata ayıklama* ve *sürüm* iki Visual Studio'nun varsayılan derleme yapılandırmaları. Geçerli yapı yapılandırması araç çubuğunda gösterilir. Visual Studio, uygulamanızda derlemek için yapılandırıldığını aşağıdaki araç resim göstermektedir **hata ayıklama** modu.

   ![Visual Studio araç çubuğu](./media/debugging-with-visual-studio/toolbar1.png)

Hata ayıklama modunda programınızı test ederek her zaman başlamalısınız. Çoğu derleyici iyileştirmelerini modunu kapatır hata ayıklama ve yapılandırma işlemi sırasında daha zengin bilgi sağlar.

## <a name="setting-a-breakpoint"></a>Kesme noktası ayarlama

Hata ayıklama modunda programınızı çalıştırma ve birkaç deneyin hata ayıklama özellikleri:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. A *kesme noktası* geçici olarak uygulamanın çalışmasını kesintiye uğratır *önce* kesme satırıyla yürütülür. 

   Okur satırında bir kesme noktası belirleyerek `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` o satırdaki veya seçerek kod penceresinin sol kenar boşluğunda tıklayarak **hata ayıklama** > **kesme** satırı ile menü öğesi Seçili. Aşağıdaki şekilde gösterildiği gibi Visual Studio kesme noktası vurgulayarak ve sol kenar boşluğu içinde kırmızı bir daire görüntüleyerek ayarlamak satır gösterir.

   ![Visual Studio programı penceresiyle kesme noktası ayarlama](./media/debugging-with-visual-studio/setbreakpoint.png)

1. Program seçerek hata ayıklama modunda çalıştırılması **HelloWorld** yeşil ok F5 tuşuna basarak veya seçme araç çubuğundan düğme **hata ayıklama** > **hata ayıklamayıBaşlat**.

1. Program için bir ad istediğinde konsol penceresinde bir dize girin ve Enter tuşuna basın.

1. Program yürütme durdurur kesme noktasına ulaştığında ve önce `Console.WriteLine` yöntemini yürütür. **Otomobiller** penceresi geçerli satırında kullanılan değişkenlerin değerleri görüntüler. **Yereller** penceresi (tıklatarak görüntüleyebileceğiniz **Yereller** sekmesinde) şu anda yürütülen yönteminde tanımlı değişkenlerin değerleri görüntüler.

   ![Visual Studio uygulama penceresi](./media/debugging-with-visual-studio/break.png)

1. Programınızı nasıl etkilediği görmek için değişkenlerin değerini değiştirebilirsiniz. Varsa **komut penceresi** görünür durumda değilse seçerek görüntülemek **hata ayıklama** > **Windows** > **hemen**menü öğesi. **Komut penceresi** hata ayıklama uygulama ile etkileşim sağlar.

1. Değişkenlerin değerleri etkileşimli olarak değiştirebilirsiniz. ENTER `name = "Gracie"` içinde **komut penceresi** ve Enter tuşuna basın.

1. ENTER `date = new DateTime(2016,11,01,11,59,00)` içinde **komut penceresi** ve Enter tuşuna basın.

   **Komut penceresi** dize değişkenin değerini ve özelliklerini görüntüler <xref:System.DateTime> değeri. Ayrıca, değişkenlerin değerini güncelleştirilmiştir **otomobiller** ve **Yereller** windows.

   ![Otomatik değişkenler penceresi ve komut penceresi](./media/debugging-with-visual-studio/autosimmediate.png)

1. Program yürütme seçerek devam **devam** düğmesini seçerek veya araç çubuğunda **hata ayıklama** > **devam** menü öğesi. Konsol penceresinde görüntülenen değerler, yaptığınız değişiklikleri karşılık **komut penceresi**.

   ![Yazılı değerinde prizine ne gösteren konsol penceresi nedir? 11: 59'de 1/11/2016'Hello Gracie tarafından izlenen istemi](./media/debugging-with-visual-studio/changed.png)

1. Uygulama ve son hata ayıklama modundan çıkmak için herhangi bir tuşa basın.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. A *kesme noktası* geçici olarak uygulamanın çalışmasını kesintiye uğratır *önce* kesme satırıyla yürütülür. 

   Okur satırında bir kesme noktası belirleyerek `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` o satırdaki veya seçerek kod penceresinin sol kenar boşluğunda tıklayarak **hata ayıklama** > **kesme** satırı ile menü öğesi Seçili. Aşağıdaki şekilde gösterildiği gibi Visual Studio kesme noktası vurgulayarak ve sol kenar boşluğu içinde kırmızı bir daire görüntüleyerek ayarlamak satır gösterir.

   ![Visual Studio programı penceresiyle kesme noktası ayarlama](./media/debugging-with-visual-studio/vb-setbreakpoint.png)

1. Program seçerek hata ayıklama modunda çalıştırılması **HelloWorld** yeşil ok F5 tuşuna basarak veya seçme araç çubuğundan düğme **hata ayıklama** > **hata ayıklamayıBaşlat**.

1. Program için bir ad istediğinde konsol penceresinde bir dize girin ve Enter tuşuna basın.

1. Program yürütme durdurur kesme noktasına ulaştığında ve önce `Console.WriteLine` yöntemini yürütür. **Otomobiller** penceresi geçerli satırında kullanılan değişkenlerin değerleri görüntüler. **Yereller** penceresi (tıklatarak görüntüleyebileceğiniz **Yereller** sekmesinde) şu anda yürütülen yönteminde tanımlı değişkenlerin değerleri görüntüler.

   ![Visual Studio uygulama penceresi](./media/debugging-with-visual-studio/vb-break.png)

1. Programınızı nasıl etkilediği görmek için değişkenlerin değerini değiştirebilirsiniz. Varsa **komut penceresi** görünür durumda değilse seçerek görüntülemek **hata ayıklama** > **Windows** > **hemen**menü öğesi. **Komut penceresi** hata ayıklama uygulama ile etkileşim sağlar.

1. Değişkenlerin değerleri etkileşimli olarak değiştirebilirsiniz. ENTER `name = "Gracie"` içinde **komut penceresi** ve Enter tuşuna basın.

1. ENTER `currentDate = new DateTime(2016,11,01,11,59,00)` içinde **komut penceresi** ve Enter tuşuna basın.

1. Program yürütme seçerek devam **devam** düğmesini seçerek veya araç çubuğunda **hata ayıklama** > **devam** menü öğesi. Konsol penceresinde görüntülenen değerler, yaptığınız değişiklikleri karşılık **komut penceresi**.

   ![Komut penceresi içinde girilen değiştirilmiş değerleri gösteren konsol penceresi](./media/debugging-with-visual-studio/changed.png)

1. Uygulama ve son hata ayıklama modundan çıkmak için herhangi bir tuşa basın.
---

## <a name="setting-a-conditional-breakpoint"></a>Koşullu kesme noktası ayarlama

Programınızı kullanıcının girdiği dizesini görüntüler. Kullanıcı herhangi bir şey girmezse ne olur? Bu yararlı bir hata ayıklama özellik ile test edebilirsiniz *koşullu kesme noktası*, hangi sonları program yürütme biri veya daha fazla koşullar.

Koşullu kesme noktası ayarlayın ve kullanıcı bir dize girin başarısız olduğunda ne olacağını test etmek için aşağıdakileri yapın:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Kesme noktası temsil eden kırmızı nokta üzerinde sağ tıklayın. Bağlam menüsünde seçin **koşullar** açmak için **kesme noktası ayarları** iletişim. Onay kutusunu için **koşullar**.

   ![Kesme noktası ayarlar paneli](./media/debugging-with-visual-studio/breakpointsettings.png)

1. İçin **koşullu ifade** Değiştir "Örneğin x 5 ==" aşağıdaki:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Kod koşulu için test ediyorsanız, `String.IsNullOrEmpty(name)` yöntemi çağrısı `true` ya da çünkü *adı* bir değer atanmadı ya da boş bir dize değeri olduğu için (""). De belirtebilirsiniz bir *isabet sayısı*, belirtilen kaç kez, yürütülen bir açıklamadır önce hangi kesmeler yürütme programı veya bir *filtre koşulu*, kesmeleri programı gibi üzerinde temel yürütme bir iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı olarak öznitelikleri.

1. Seçin **kapatmak** düğmesi iletişim kutusunu kapatın.

1. Program hata ayıklama modunda çalıştırın.

1. Konsol penceresinde adınızı girmeniz istendiğinde Enter tuşuna basın.

1. Koşul biz belirtilmediğinden `name` ya `null` veya <xref:System.String.Empty?displayProperty=nameWithType>, memnun, program yürütme durdurur kesme noktasına ulaştığında ve önce `Console.WriteLine` yöntemini yürütür.

1. Seçin **Yereller** olduğundan şu anda yürütülen yönteme yerel değişkenlerin değerleri gösterir penceresi `Main` programınızdaki yöntemi. Görüntülendiğini değerini `name` değişken `""`, veya <xref:System.String.Empty?displayProperty=nameWithType>.

1. Değer boş bir dize aşağıdaki ifadeyi girerek onaylayın **komut penceresi**. Sonuç `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Deyim yürütüldükten sonra true değeri döndüren komut penceresi](./media/debugging-with-visual-studio/emptystring.png)

1. Seçin **devam** program yürütme devam etmek için araç çubuğunda.

1. Konsol penceresini kapatın ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.

1. Kesme noktası kod penceresinin sol kenar boşluğunda nokta tıklayarak veya seçerek temizleyin **hata ayıklama > kesme** menü öğesi seçili satır.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Kesme noktası temsil eden kırmızı nokta üzerinde sağ tıklayın. Bağlam menüsünde seçin **koşullar** açmak için **kesme noktası ayarları** iletişim. Onay kutusunu için **koşullar**.

   ![Kesme noktası ayarlar paneli](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. İçin **koşullu ifade** Değiştir "Örneğin x 5 =" aşağıdaki:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Kod koşulu için test ediyorsanız, `String.IsNullOrEmpty(name)` yöntemi çağrısı `True` ya da çünkü *adı* bir değer atanmadı ya da boş bir dize değeri olduğu için (""). De belirtebilirsiniz bir *isabet sayısı*, belirtilen kaç kez, yürütülen bir açıklamadır önce hangi kesmeler yürütme programı veya bir *filtre koşulu*, kesmeleri programı gibi üzerinde temel yürütme bir iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı olarak öznitelikleri.

1. Seçin **kapatmak** düğmesi iletişim kutusunu kapatın.

1. Program hata ayıklama modunda çalıştırın.

1. Konsol penceresinde adınızı girmeniz istendiğinde Enter tuşuna basın.

1. Koşul biz belirtilmediğinden `name` ya `null` veya <xref:System.String.Empty?displayProperty=nameWithType>, memnun, program yürütme durdurur kesme noktasına ulaştığında ve önce `Console.WriteLine` yöntemini yürütür.

1. Seçin **Yereller** olduğundan şu anda yürütülen yönteme yerel değişkenlerin değerleri gösterir penceresi `Main` programınızdaki yöntemi. Görüntülendiğini değerini `name` değişken `""`, veya <xref:System.String.Empty?displayProperty=nameWithType>.

1. Değer boş bir dize aşağıdaki ifadeyi girerek onaylayın **komut penceresi**. Sonuç `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```
  ![Deyim yürütüldükten sonra true değeri döndüren komut penceresi](./media/debugging-with-visual-studio/vb-emptystring.png)

1. Seçin **devam** program yürütme devam etmek için araç çubuğunda.

1. Konsol penceresini kapatın ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.

1. Kesme noktası kod penceresinin sol kenar boşluğunda nokta tıklayarak veya seçerek temizleyin **hata ayıklama > kesme** menü öğesi seçili satır.
---
## <a name="stepping-through-a-program"></a>Bir program aracılığıyla Adımlama

Visual Studio bir program aracılığıyla satır adım ve yürütülmesinin izlemenize olanak sağlar. Normalde, bir kesme noktası ayarlayın ve program kodunuzu küçük bir parçası olsa program akışı izlemek için bu özelliği kullanmak. Programınızı küçük olduğundan, aşağıdakileri yaparak tüm program aracılığıyla geçebilirsiniz:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Menü çubuğunda seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. Visual Studio vurgular ve bir sonraki satıra yürütme dönüşecektir görüntüler.

   ![Visual Studio penceresi](./media/debugging-with-visual-studio/stepinto1.png)

   Bu noktada, **otomobiller** penceresi gösterir, program, yalnızca bir değişken tanımlanmış `args`. Herhangi bir komut satırı bağımsız değişkeni programına aktarılan henüz çünkü değeri boş bir dize dizisi olduğu. Ayrıca, Visual Studio boş konsol penceresi açtı.

1. Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. Visual Studio artık yürütme sonraki satıra vurgular. Aşağıdaki şekilde gösterildiği gibi son deyim ve bunu arasında kod yürütmek için kısa bir milisaniye sürdü. `args` yalnızca bildirilen değişken kalır ve konsol penceresi boş kalır.

   ![Visual Studio penceresi](./media/debugging-with-visual-studio/stepinto2.png)

1. Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. Visual Studio vurgular içeren deyimi `name` değişken atama. **Otomobiller** penceresi gösterir `name` olan `null`, ve "Adınızı nedir?" dizesini konsol penceresinde görüntüler.

1. Konsol penceresinde bir dize girerek ve Enter tuşuna basarak komutuna yanıt. Konsol yanıt vermiyor ve girdiğiniz dize konsol penceresinde görüntülenmez ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi yine de girişinizi yakalayın.

1. Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. Visual Studio vurgular içeren deyimi `date` (C# ' ta) veya `currentDate` (Visual Basic'te) değişken atama. **Otomobiller** penceresi şunu gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> özellik değeri ve çağrı tarafından döndürülen değer <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi. Konsol penceresi de konsol için giriş istendiğinde girilen dizesini görüntüler.

1. Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. **Otomobiller** penceresi gösterir değerini `date` atama sonra değişken <xref:System.DateTime.Now?displayProperty=nameWithType> özelliği. Konsol penceresinde değiştirilmez.

1. Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. Visual Studio çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> yöntemi. Değerlerini `date` (veya `currentDate`) ve `name` değişkenleri görünür **otomobiller** ve konsol penceresinde görüntüler biçimlendirilmiş dize.

1. Seçin **hata ayıklama** > **Step Out** veya kaydırma ve F11 tuşuna basın. Bu adım adım çalışmayı durdurur. Konsol penceresinde bir ileti görüntüler ve herhangi bir tuşa basın için bekler.

1. Konsol penceresini kapatın ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Menü çubuğunda seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. Visual Studio vurgular ve bir sonraki satıra yürütme dönüşecektir görüntüler.

   ![Visual Studio penceresi](./media/debugging-with-visual-studio/vb-stepinto1.png)

   AT noktada, program için herhangi bir komut satırı bağımsız değişkeni geçirilen henüz çünkü **otomobiller** penceresi gösterir, değeri `args` değişkeni, boş bir dize dizisi. Ayrıca, Visual Studio boş konsol penceresi açtı.

1. Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. Visual Studio artık yürütme sonraki satıra vurgular. Aşağıdaki şekilde gösterildiği gibi son deyim ve bunu arasında kod yürütmek için kısa bir milisaniye sürdü. `args` yalnızca bildirilen değişken kalır ve konsol penceresi boş kalır.

   ![Visual Studio penceresi](./media/debugging-with-visual-studio/vb-stepinto2.png)

1. Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. Visual Studio vurgular içeren deyimi `name` değişken atama. **Otomobiller** penceresi gösterir `name` olan `Nothing`, ve "Adınızı nedir?" dizesini konsol penceresinde görüntüler.

1. Konsol penceresinde bir dize girerek ve Enter tuşuna basarak komutuna yanıt. Konsol yanıt vermiyor ve girdiğiniz dize konsol penceresinde görüntülenmez ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi yine de girişinizi yakalayın.

1. Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. Visual Studio vurgular içeren deyimi `date` (C# ' ta) veya `currentDate` (Visual Basic'te) değişken atama. **Otomobiller** penceresi şunu gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> özellik değeri ve çağrı tarafından döndürülen değer <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi. Konsol penceresi de konsol için giriş istendiğinde girilen dizesini görüntüler.

1. Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. **Otomobiller** penceresi gösterir değerini `date` atama sonra değişken <xref:System.DateTime.Now?displayProperty=nameWithType> özelliği. Konsol penceresinde değiştirilmez.

1. Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın. Visual Studio çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> yöntemi. Değerlerini `date` (veya `currentDate`) ve `name` değişkenleri görünür **otomobiller** ve konsol penceresinde görüntüler biçimlendirilmiş dize.

1. Seçin **hata ayıklama** > **Step Out** veya kaydırma ve F11 tuşuna basın. Bu adım adım çalışmayı durdurur. Konsol penceresinde bir ileti görüntüler ve herhangi bir tuşa basın için bekler.

1. Konsol penceresini kapatın ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.
---

## <a name="building-a-release-version"></a>Bir yayın sürümü oluşturma

Hata ayıklama derlemesi uygulamanızın test ettikten sonra ayrıca derlemek ve yayın sürümü test gerekir. Yayın sürümü uygulamanın davranışı bazen olumsuz şekilde etkileyebilecek derleyici iyileştirmeler içerir. Örneğin, performansı iyileştirmek için tasarlanmış derleyici iyileştirmelerini zaman uyumsuz veya birden çok iş parçacıklı uygulamalarda yarış durumları oluşturabilirsiniz.

Derleme ve sürümünü Konsol uygulamanızı test etmek için araç çubuğundaki derleme yapılandırması değiştirme **hata ayıklama** için **sürüm**.

![Görüntü](./media/debugging-with-visual-studio/toolbar2.png)

Ne zaman F5 tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsünde, Visual Studio konsol uygulamanızın sürümünü derler. Uygulama hata ayıklama sürümü yaptığınız gibi test edebilirsiniz.

Uygulamanızın hatalarını ayıklama bitirdikten sonra sonraki adım, uygulamanızın dağıtılabilir sürüm yayımlamaktır. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz: [Visual Studio 2017 Hello World uygulamayla yayımlama](./publishing-with-visual-studio.md).
