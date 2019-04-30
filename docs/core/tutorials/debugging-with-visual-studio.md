---
title: Hello World .NET Core uygulamanızı Visual Studio 2017 ile hata ayıklama
description: C# veya Visual Basic, Visual Studio 2017 ile yazılmış bir Hello World uygulamasında hata ayıklama hakkında bilgi edinin.
ms.date: 12/15/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 9b2375443c9947a32fcccea062642103601d5010
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648209"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio-2017"></a>Hata ayıklama, C# veya Visual Studio 2017'yi kullanarak Visual Basic .NET Core Merhaba Dünya uygulaması

Şu ana kadar adımları izlediğinizden [bir C# Merhaba Dünya uygulaması ile Visual Studio 2017'de .NET Core derleme](with-visual-studio.md) veya [bir Visual Studio 2017'de .NET Core ile Visual Basic Merhaba Dünya uygulaması derleme](vb-with-visual-studio.md) oluşturmak için ve basit bir konsol uygulaması çalıştırın. Yazılan ve uygulamanızın derlenmiş sonra test başlayabilirsiniz. Visual Studio test etme ve uygulamanızı sorun giderme kullanabileceğiniz araçları hata ayıklama kapsamlı içerir.

## <a name="debugging-in-debug-mode"></a>Hata ayıklama modunda hata ayıklama

*Hata ayıklama* ve *yayın* iki Visual Studio'nun varsayılan derleme yapılandırmaları şunlardır. Geçerli yapı yapılandırması, araç çubuğunda gösterilir. Visual Studio uygulamanızı derlemek için yapılandırıldığını aşağıdaki araç çubuğu görüntüsü gösterilmektedir **hata ayıklama** modu.

   ![Varsayılan Visual Studio araç ile vurgulanan hata ayıklama](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Her zaman, programınızın hata ayıklama modunda test ederek başlamalısınız. Hata ayıklama modu çoğu derleyici iyileştirmeleri kapatır ve yapı işlemi sırasında daha zengin bilgiler sağlar.

## <a name="setting-a-breakpoint"></a>Bir kesme noktası ayarlama

Programınızın hata ayıklama modunda çalıştırabilir ve birkaç deneyin hata ayıklama özellikleri:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. A *kesme noktası* geçici olarak uygulamanın yürütülmesini keser *önce* kesme noktasını içeren satırı yürütülür. 

   Yazan satıra bir kesme noktası ayarlamak `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` sol kenar boşluğunda kod penceresinin seçerek veya bu satıra tıklayarak **hata ayıklama** > **iki durumlu kesme noktası** satırı ile menü öğesi Seçili. Aşağıdaki şekilde gösterildiği gibi Visual Studio satırın üzerinde vurgulayarak ve sol alt köşede kırmızı bir daire görüntüleyerek Kesme noktasının ayarlandığını gösterir.

   ![Visual Studio Program penceresiyle kesme noktası ayarlama](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Program seçerek hata ayıklama modunda çalıştırmak **HelloWorld** F5 tuşuna basarak veya belirleyerek araç çubuğunda yeşil bir ok düğmesi **hata ayıklama** > **Start Debugging**.

1. Program için bir ad istediğinde, konsol penceresinde bir dize girin ve Enter tuşuna basın.

1. Kesme noktasına ulaştığında ve önce programın yürütülmesini durdurur `Console.WriteLine` yöntemini yürütür. **Otolar** penceresi, geçerli satırı kullanılan değişkenlerin değerlerini görüntüler. **Yereller** penceresi (tıklatarak görüntüleyebileceğiniz **Yereller** sekmesinde) o anda yürütülen yönteminde tanımlanan değişkenler değerlerini görüntüler.

   ![Visual Studio'da bir kesme noktasının ekran görüntüsü.](./media/debugging-with-visual-studio/breakpoint-console-window.png)

1. Değişkenleri, programınızın nasıl etkilediğini görmek için değerini değiştirebilirsiniz. Varsa **komut penceresi** görünmüyorsa, seçerek görüntüleyin **hata ayıklama** > **Windows** > **hemen**menü öğesi. **Komut penceresi** hata ayıklaması uygulama ile etkileşim sağlar.

1. Etkileşimli olarak değişkenlerin değerlerini değiştirebilirsiniz. ENTER `name = "Gracie"` içinde **komut penceresi** ve Enter tuşuna basın.

1. ENTER `date = new DateTime(2016,11,01,11,59,00)` içinde **komut penceresi** ve Enter tuşuna basın.

   **Komut penceresi** dize değişkeninin değerini ve özelliklerini görüntüler <xref:System.DateTime> değeri. Ayrıca, değişkenlerin değerini güncelleştirilmiştir **Otolar** ve **Yereller** windows.

   ![Otomatik değişkenler penceresi ve komut penceresi](./media/debugging-with-visual-studio/autos-immediate-window.png)

1. Program yürütme seçerek devam **devam** düğmesini seçerek veya araç çubuğunda **hata ayıklama** > **devam** menü öğesi. Konsol penceresinde görüntülenen değerleri, yaptığınız değişiklikleri karşılık **komut penceresi**.

   ![' % S'değeri Jack nedir gösteren konsol penceresi nedir? Hello Gracie tarafından izlenen istemi](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Uygulama ve son hata ayıklama modundan çıkmak için herhangi bir tuşa basın.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. A *kesme noktası* geçici olarak uygulamanın yürütülmesini keser *önce* kesme noktasını içeren satırı yürütülür. 

   Yazan satıra bir kesme noktası ayarlamak `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` sol kenar boşluğunda kod penceresinin seçerek veya bu satıra tıklayarak **hata ayıklama** > **iki durumlu kesme noktası** satırı ile menü öğesi Seçili. Aşağıdaki şekilde gösterildiği gibi Visual Studio satırın üzerinde vurgulayarak ve sol alt köşede kırmızı bir daire görüntüleyerek Kesme noktasının ayarlandığını gösterir.

   ![Visual Studio Program penceresiyle kesme noktası ayarlama](./media/debugging-with-visual-studio/vb-set-breakpoint-in-editor.png)

1. Program seçerek hata ayıklama modunda çalıştırmak **HelloWorld** F5 tuşuna basarak veya belirleyerek araç çubuğunda yeşil bir ok düğmesi **hata ayıklama** > **Start Debugging**.

1. Program için bir ad istediğinde, konsol penceresinde bir dize girin ve Enter tuşuna basın.

1. Kesme noktasına ulaştığında ve önce programın yürütülmesini durdurur `Console.WriteLine` yöntemini yürütür. **Otolar** penceresi, geçerli satırı kullanılan değişkenlerin değerlerini görüntüler. **Yereller** penceresi (tıklatarak görüntüleyebileceğiniz **Yereller** sekmesinde) o anda yürütülen yönteminde tanımlanan değişkenler değerlerini görüntüler.

   ![Visual Studio uygulama penceresinin kesme noktasında](./media/debugging-with-visual-studio/vb-stop-at-breakpoint.png)

1. Değişkenleri, programınızın nasıl etkilediğini görmek için değerini değiştirebilirsiniz. Varsa **komut penceresi** görünmüyorsa, seçerek görüntüleyin **hata ayıklama** > **Windows** > **hemen**menü öğesi. **Komut penceresi** hata ayıklaması uygulama ile etkileşim sağlar.

1. Etkileşimli olarak değişkenlerin değerlerini değiştirebilirsiniz. ENTER `name = "Gracie"` içinde **komut penceresi** ve Enter tuşuna basın.

1. ENTER `currentDate = new DateTime(2016,11,01,11,59,00)` içinde **komut penceresi** ve Enter tuşuna basın.

1. Program yürütme seçerek devam **devam** düğmesini seçerek veya araç çubuğunda **hata ayıklama** > **devam** menü öğesi. Konsol penceresinde görüntülenen değerleri, yaptığınız değişiklikleri karşılık **komut penceresi**.

   ![Yürütme penceresinde girilen değiştirilmiş değerleri gösteren konsol penceresi](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Uygulama ve son hata ayıklama modundan çıkmak için herhangi bir tuşa basın.
---

## <a name="setting-a-conditional-breakpoint"></a>Koşullu kesme noktası ayarlama

Programınız kullanıcının girdiği görüntüler. Kullanıcının herhangi bir şey girmezse ne olur? Bu yararlı bir hata ayıklama özelliği ile test edebilirsiniz *koşullu kesme noktası*, hangi sonları program yürütme sırasında bir veya daha fazla koşullar.

Koşullu kesme noktası ayarlayın ve bir dize girmek kullanıcının başarısız olduğunda ne olacağını test etmek için aşağıdakileri yapın:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Kesme noktasını temsil eden kırmızı noktayı sağ tıklayın. Bağlam menüsünde **koşullar** açmak için **kesme noktası ayarları** iletişim. İçin kutuyu **koşullar**.

   ![Düzenleyici gösteren kesme noktası ayarlar paneli-C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. İçin **koşullu ifade** Değiştir "örn. x == 5" aşağıdaki:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Kod koşulu için test ettiğiniz, `String.IsNullOrEmpty(name)` yöntem çağrısında `true` ya da çünkü *adı* bir değer atanmadı veya değeri boş bir dizedir (""). Belirtebilirsiniz bir *isabet sayısı*, belirtilen birkaç kez yürütülen bir deyim önce hangi kesme program yürütmesini veya *filtre koşulu*, kesmeleri programı gibi üzerinde temel yürütme bir iş parçacığı tanımlayıcısı, işlem adı ya da iş parçacığı adı olarak öznitelikleri.

1. Seçin **kapatmak** iletişim kutusunu kapatmak için düğme.

1. Programın hata ayıklama modunda çalıştırın.

1. Konsol penceresinde, adı girmeniz istendiğinde Enter tuşuna basın.

1. Koşul belirlemiş çünkü `name` ya da `null` veya <xref:System.String.Empty?displayProperty=nameWithType>, memnun, kesme noktasına ulaştığında ve önce programın yürütülmesini durdurur `Console.WriteLine` yöntemini yürütür.

1. Seçin **Yereller** olduğundan şu anda yürütülen yöntemi yerel değişkenlerin değerlerini gösteren penceresi `Main` programınızdaki yöntemi. Mesajının görüntülendiğini görün değerini `name` değişkendir `""`, veya <xref:System.String.Empty?displayProperty=nameWithType>.

1. Değer: boş bir dize içinde aşağıdaki ifadeyi girerek onaylayın **komut penceresi**. Sonuç `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Bir değer döndüren bir komut penceresi deyim yürütüldükten sonra - trueC#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Seçin **devam** program yürütme devam etmek için araç çubuğunda.

1. Konsol penceresini kapatın ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.

1. Kesme noktasını seçerek veya bir nokta kod penceresinin sol kenar boşluğunda tıklayarak Temizle **hata ayıklama > iki durumlu kesme noktası** menü öğesi seçilen satır.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Kesme noktasını temsil eden kırmızı noktayı sağ tıklayın. Bağlam menüsünde **koşullar** açmak için **kesme noktası ayarları** iletişim. İçin kutuyu **koşullar**.

   ![Düzenleyici gösteren kesme noktası ayarlar paneli - Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. İçin **koşullu ifade** Değiştir "örn. x 5 =" aşağıdaki:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Kod koşulu için test ettiğiniz, `String.IsNullOrEmpty(name)` yöntem çağrısında `True` ya da çünkü *adı* bir değer atanmadı veya değeri boş bir dizedir (""). Belirtebilirsiniz bir *isabet sayısı*, belirtilen birkaç kez yürütülen bir deyim önce hangi kesme program yürütmesini veya *filtre koşulu*, kesmeleri programı gibi üzerinde temel yürütme bir iş parçacığı tanımlayıcısı, işlem adı ya da iş parçacığı adı olarak öznitelikleri.

1. Seçin **kapatmak** iletişim kutusunu kapatmak için düğme.

1. Programın hata ayıklama modunda çalıştırın.

1. Konsol penceresinde, adı girmeniz istendiğinde Enter tuşuna basın.

1. Koşul belirlemiş çünkü `name` ya da `null` veya <xref:System.String.Empty?displayProperty=nameWithType>, memnun, kesme noktasına ulaştığında ve önce programın yürütülmesini durdurur `Console.WriteLine` yöntemini yürütür.

1. Seçin **Yereller** olduğundan şu anda yürütülen yöntemi yerel değişkenlerin değerlerini gösteren penceresi `Main` programınızdaki yöntemi. Mesajının görüntülendiğini görün değerini `name` değişkendir `""`, veya <xref:System.String.Empty?displayProperty=nameWithType>.

1. Değer: boş bir dize içinde aşağıdaki ifadeyi girerek onaylayın **komut penceresi**. Sonuç `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

  ![Deyim sonra yürütülen - Visual Basic true değerini döndüren bir komut penceresi](./media/debugging-with-visual-studio/vb-immediate-window-output.png)

1. Seçin **devam** program yürütme devam etmek için araç çubuğunda.

1. Konsol penceresini kapatın ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.

1. Kesme noktasını seçerek veya bir nokta kod penceresinin sol kenar boşluğunda tıklayarak Temizle **hata ayıklama > iki durumlu kesme noktası** menü öğesi seçilen satır.
---
## <a name="stepping-through-a-program"></a>Bir program aracılığıyla Adımlama

Visual Studio, bir program aracılığıyla satır adım ve yürütme izlemenize olanak tanır. Normalde, bir kesme noktası ayarlamak ve program kodunuza küçük bir bölümünü program akışını izlemek için bu özelliği kullanın. Programınızı küçük olduğundan, aşağıdakileri yaparak tüm program aracılığıyla geçebilirsiniz:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Menü çubuğunda, **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. Visual Studio vurgular ve bir sonraki satıra yürütme dönüşecektir görüntüler.

   ![Visual Studio adımla yöntemi-C#](./media/debugging-with-visual-studio/step-into-method.png)

   Bu noktada, **Otolar** penceresi gösterir, programınızın yalnızca tek bir değişken tanımladığı `args`. Herhangi bir komut satırı bağımsız değişkeni programa geçirilen henüz çünkü değeri boş bir dize dizisi ' dir. Ayrıca, Visual Studio, bir boş konsol penceresi açıldı.

1. Seçin **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. Visual Studio artık yürütme sonraki satırı vurgular. Şekilde gösterildiği gibi son deyim ve bunu arasında kod yürütmek için bir milisaniyeden kısa duruma getirdi. `args` yalnızca bildirilmiş bir değişken kalır ve konsol penceresinde boş kalır.

   ![Visual Studio yöntemi kaynakta adım-C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Seçin **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. Visual Studio vurgular içeren deyim `name` değişken ataması. **Otolar** penceresi gösterir `name` olduğu `null`, ve "Adınız ne?" dizesi konsol penceresinde görüntüler.

1. Konsol penceresinde bir dize girerek yazıp Enter tuşuna basarak istemine yanıt. Konsolu yanıt vermiyor ve dizenin konsol penceresinde görüntülenmez ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi yine de girişinizi yakalayın.

1. Seçin **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. Visual Studio vurgular içeren deyim `date` (C# ' de) veya `currentDate` (Visual Basic'te) değişken ataması. **Otolar** penceresi şunu gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> özellik değeri ve çağrısı tarafından döndürülen değer <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi. Konsol penceresi de konsol girişi için istendiğinde girilen dize görüntüler.

1. Seçin **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. **Otolar** penceresi değerini gösterir `date` sonra atamadan değişken <xref:System.DateTime.Now?displayProperty=nameWithType> özelliği. Konsol penceresinde değiştirilmez.

1. Seçin **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. Visual Studio çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> yöntemi. Değerlerini `date` (veya `currentDate`) ve `name` değişkenleri görünür **Otolar** biçimlendirilmiş dize penceresi ve konsol penceresinde görüntüler.

1. Seçin **hata ayıklama** > **Step Out** veya SHIFT ve F11 tuşuna basın. Bu adım adım yürütmeyi durdurur. Konsol penceresinde bir ileti görüntüler ve sizin için bir tuşa basın bekler.

1. Konsol penceresini kapatın ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Menü çubuğunda, **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. Visual Studio vurgular ve bir sonraki satıra yürütme dönüşecektir görüntüler.

   ![Visual Studio adımla yöntemi - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   AT noktada, herhangi bir komut satırı bağımsız değişkeni, programa geçirilen henüz çünkü **Otolar** penceresi gösterir, değerini `args` değişkeni, boş bir dize dizisi. Ayrıca, Visual Studio, bir boş konsol penceresi açıldı.

1. Seçin **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. Visual Studio artık yürütme sonraki satırı vurgular. Şekilde gösterildiği gibi son deyim ve bunu arasında kod yürütmek için bir milisaniyeden kısa duruma getirdi. `args` yalnızca bildirilmiş bir değişken kalır ve konsol penceresinde boş kalır.

   ![Visual Studio adım yöntemi kaynağına - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Seçin **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. Visual Studio vurgular içeren deyim `name` değişken ataması. **Otolar** penceresi gösterir `name` olduğu `Nothing`, ve "Adınız ne?" dizesi konsol penceresinde görüntüler.

1. Konsol penceresinde bir dize girerek yazıp Enter tuşuna basarak istemine yanıt. Konsolu yanıt vermiyor ve dizenin konsol penceresinde görüntülenmez ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi yine de girişinizi yakalayın.

1. Seçin **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. Visual Studio vurgular içeren deyim `date` (C# ' de) veya `currentDate` (Visual Basic'te) değişken ataması. **Otolar** penceresi şunu gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> özellik değeri ve çağrısı tarafından döndürülen değer <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi. Konsol penceresi de konsol girişi için istendiğinde girilen dize görüntüler.

1. Seçin **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. **Otolar** penceresi değerini gösterir `date` sonra atamadan değişken <xref:System.DateTime.Now?displayProperty=nameWithType> özelliği. Konsol penceresinde değiştirilmez.

1. Seçin **hata ayıklama** > **içine adımla** veya F11 tuşuna basın. Visual Studio çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> yöntemi. Değerlerini `date` (veya `currentDate`) ve `name` değişkenleri görünür **Otolar** biçimlendirilmiş dize penceresi ve konsol penceresinde görüntüler.

1. Seçin **hata ayıklama** > **Step Out** veya SHIFT ve F11 tuşuna basın. Bu adım adım yürütmeyi durdurur. Konsol penceresinde bir ileti görüntüler ve sizin için bir tuşa basın bekler.

1. Konsol penceresini kapatın ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.
---

## <a name="building-a-release-version"></a>Yayın sürümünü oluşturma

Uygulamanızı hata ayıklama yapısını test ettikten sonra ayrıca derleme ve yayın sürümünü test gerekir. Yayın sürümü, bazen bir uygulamanın davranışını olumsuz etkileyebilir derleyici iyileştirmeleri içerir. Örneğin, performansı iyileştirmek için tasarlanmış derleyici iyileştirmeleri, zaman uyumsuz veya birden çok iş parçacıklı uygulamalarda yarış durumları oluşturabilirsiniz.

Oluşturmak ve yeni sürümü Konsol uygulamanızı test etmek için araç çubuğundaki derleme yapılandırması değiştirme **hata ayıklama** için **yayın**.

![Varsayılan Visual Studio araç ile vurgulanan hata ayıklama](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

F5 tuşuna basın veya seçin, **Çözümü Derle** gelen **derleme** menüsünde, Visual Studio Konsol uygulamanızı sürümü derler. Uygulamayı hata ayıklama sürümünü yaptığınız gibi test edebilirsiniz.

Uygulamanızı hata ayıklama bitirdiğinizde, sonraki adım, uygulamanızın dağıtılabilir bir sürüm yayımlamaktır. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz: [Visual Studio 2017 Hello World uygulaması yayımlama](publishing-with-visual-studio.md).
