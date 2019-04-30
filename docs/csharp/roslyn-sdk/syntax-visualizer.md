---
title: Visual Studio'da Roslyn söz dizimi görselleştiricisi ile kod keşfedin
description: Söz dizimi görselleştiricisi .NET derleyici Platformu SDK'sı için kod oluşturur modelleri araştırmak için bir araç sağlar.
ms.date: 03/07/2018
ms.custom: mvc, vs-dotnet
ms.openlocfilehash: 2d1c6d0b9f65324ee2eadafaa7f98360f37e7bb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706949"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Visual Studio'da Roslyn söz dizimi görselleştiricisi ile kod keşfedin

Bu makalede .NET derleyici Platformu ("Roslyn") SDK'sı bir parçası gönderilen Syntax Visualizer aracına genel bakış sağlar. Söz dizimi görselleştiricisi inceleyin ve söz dizimi ağacı incelemenize yardımcı olan bir araç penceresidir. Analiz etmek istediğiniz kodu modelleri anlamak için önemli bir araçtır. .NET derleyici Platformu ("Roslyn") SDK'sını kullanarak kendi uygulamalarınızı geliştirirken ayrıca hata ayıklamaya yardımcı olur. Bu araç, ilk Çözümleyicileri oluştururken açın. Görselleştirici API'ları tarafından kullanılan modelleri anlamanıza yardımcı olur. Gibi araçları da kullanabilirsiniz [SharpLab](https://sharplab.io) veya [LINQPad](https://www.linqpad.net/) kod inceleme ve söz dizimi ağaçlarını anlama.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

.NET derleyici Platform SDK'larını yakalama kullanılan kavramları öğrenmeniz [genel bakış](compiler-api-model.md) makalesi. Bu, söz dizimi ağacı, düğümler, belirteçleri ve Meraklısına Notlar bir giriş sağlar.

## <a name="syntax-visualizer"></a>Söz dizimi görselleştiricisi

**Syntax Visualizer** Visual Studio IDE içinde geçerli aktif Düzenleyici penceresinde C# veya VB kod dosyası sözdizimi ağacı denetimi sağlar. Görselleştirici tıklanarak başlatılabilir **görünümü** > **diğer Windows** > **Syntax Visualizer**.  Ayrıca **hızlı başlatma** sağ üst köşedeki araç. Tür "söz dizimi" ve açmak için komuta **Syntax Visualizer** görünmelidir.

Bu komut söz dizimi görselleştiricisi kayan araç penceresi açılır. Açık bir kod düzenleyici penceresinde yoksa, ekranı aşağıdaki şekilde gösterildiği gibi boştur. 

![Söz dizimi görselleştiricisi araç penceresi](media/syntax-visualizer/syntax-visualizer.png)

Bu araç penceresi Visual Studio içinde sol tarafındaki gibi uygun bir konuma yerleştirme. Görselleştirici, geçerli kod dosyası hakkındaki bilgileri gösterir.

Kullanarak yeni bir proje oluşturma **dosya** > **yeni proje** komutu. Bir VB veya C# projesi oluşturabilirsiniz. Visual Studio bu proje için ana kod dosya açıldığında, görselleştiricisi için söz dizimi ağacı görüntüler. Açabileceğiniz tüm mevcut C# / VB dosyasında bu Visual Studio örneği ve Görselleştirici, dosyanın söz dizimi ağacı görüntüler. Visual Studio içinde açın birden çok kod dosyaları varsa Görselleştirici (klavye girintisine sahip kod dosyası.) şu anda etkin kod dosyasının söz dizimi ağacı görüntüler.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Bir C# sözdizimi ağacı Görselleştirme](media/syntax-visualizer/visualize-csharp.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
![Bir VB söz dizimi ağacı Görselleştirme](media/syntax-visualizer/visualize-visual-basic.png)

---

Görselleştiricisi araç penceresi söz dizimi ağacı önceki görüntüde gösterildiği gibi üst ve alt bir özellik kılavuzunda görüntüler. Özellik kılavuzunda .NET dahil olmak üzere ağacında seçili olan öğenin özelliklerini görüntüler *türü* ve *tür* (SyntaxKind) öğesi.

Sözdizimi ağacı oluşturan öğeleri – üç tür *düğümleri*, *belirteçleri*, ve *Meraklısına Notlar*. Bunlar hakkında daha fazla türleri okuyabilirsiniz [sözdizimiyle çalışmak](work-with-syntax.md) makalesi. Her türde öğeler, farklı bir renkte kullanılarak temsil edilir. Kullanılan renkleri genel bir bakış için 'Gösterge' düğmesine tıklayın.

Her öğe ağacında Ayrıca kendi görüntüler **span**. **Span** olduğundan bu düğümün metin dosyasında dizinleri (başlangıç ve bitiş konumu).  Önceki içinde C# örnek, seçili "UsingKeyword [0..5)" belirtecine sahip bir **yayılma** geniş, yani beş karakteri [0..5). "[.)" Başlangıç dizini aralığı bir parçasıdır, ancak bitiş dizini değil gösterimi anlamına gelir.

Ağaç gitmek için iki yolu vardır:
* Genişletin veya ağacındaki öğeleri tıklayın. Görselleştirici, bu öğenin aralık Kod düzenleyicisinde karşılık gelen metni otomatik olarak seçer.
* Kod düzenleyicisinde metin seçin veya tıklatın. Kod Düzenleyicisi'nde "Modülü Module1" içeren satırı seçin, önceki VB örnekte görselleştiricisi ağacında karşılık gelen ModuleStatement düğüme otomatik olarak gider. 

Görselleştirici düzenleyicide seçilen metni aralık, aralık en iyi eşleşen ağaç öğesinde vurgular.

Görselleştirici etkin kod dosyasındaki değişiklikleri eşleştirmek için ağaç yeniler. Bir çağrı ekleyin `Console.WriteLine()` içinde `Main()`. Siz yazarken görselleştiricisi ağaç yeniler.

Yazdığınız anda duraklatma yazılan `Console.`. Ağacı pembeyle gösterilmiştir renkli bazı öğeler içeriyor. Bu noktada, yazılan kod hataları ('Olarak Tanılama' da bilinir) vardır. Bu hatalar, belirteçleri ve trivia sözdizimi ağacındaki düğümlere eklenir. Görselleştirici, öğeleri bağlı hataları olan arka planda pembe vurgulama onlara gösterir. Öğenin üzerine gelerek Pembe renkli herhangi bir öğeyi hatalarda inceleyebilirsiniz. Görselleştirici söz dizimsel hatalar (Bu hataları ilgili yazılan kod söz dizimleri için); yalnızca görüntüler. Bu anlamsal hataları görüntülemez.
 
## <a name="syntax-graphs"></a>Söz dizimi grafikleri

Ağacın herhangi bir öğeye sağ tıklayın ve tıklayarak **yönlendirilmiş söz dizimi Grafı görüntüle**. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Görselleştirici seçili öğenin köklü grafik gösterimi görüntülenir. İçin aşağıdaki adımları deneyin **MethodDeclaration** düğüm karşılık gelen `Main()` C# örneği yöntemi. Görselleştirici şu şekilde görünür bir söz dizimi grafik görüntüler:

![Bir C# sözdizimi grafik görüntüleme](media/syntax-visualizer/csharp-syntax-graph.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

Aynı deneyin **SubBlock** düğüm karşılık gelen `Main()` önceki VB örnekte yöntemi. Görselleştirici şu şekilde görünür bir söz dizimi grafik görüntüler:

![Bir VB söz dizimi grafik görüntüleme](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Söz dizimi graf Görüntüleyicisi, renklendirme düzenini bir gösterge görüntüleme seçeneği vardır. Ayrıca, tek tek öğeleri söz dizimi grafiğinde öğeyle ilgili özellikleri görüntülemek için fareyle üzerine gelerek.

Grafiklerin her zaman Visual Studio içinde aynı pencerede görüntülenir ve söz dizimi grafiklerini farklı öğeler için sürekli olarak ağacında görüntüleyebilir. Yeni bir söz dizimi grafı görüntülemek için Sekmeler arasında geçiş yapmanız gerekmez, bu pencereyi Visual Studio içinde uygun bir konuma sabitleyebilirsiniz. Kod Düzenleyicisi'ni windows, aşağıdaki alt genellikle uygundur.

Yerleştirme düzeni görselleştiricisi araç penceresi ve söz dizimi grafik penceresi ile kullanmak için şu şekildedir:

![Görselleştirici ve söz dizimi grafik penceresi için bir yerleştirme düzeni](media/syntax-visualizer/docking-layout.png)

Başka bir seçenek, bir ikili izleme kurulumunda bir ikinci monitörde söz dizimi grafiği pencere eklemektir.

## <a name="inspecting-semantics"></a>İnceleme semantiği

Söz dizimi görselleştiricisi ilkel incelemesini simgeleri ve anlamsal bilgi sağlar. Tür `double x = 1 + 1;` C# örneğinde Main() içindeki. İfade seçip `1 + 1` kod düzenleyici penceresinde. Görselleştirici vurgular **AddExpression** Görselleştirici düğümü. Sağ bu tıklayın **AddExpression** tıklayın **görünümü simgesi (varsa)**. Menü öğelerinin çoğu "varsa" niteleyicisi olan dikkat edin. Söz dizimi görselleştiricisi özellikleri tüm düğümler için mevcut olmayabilir özellikleri dahil olmak üzere, bir düğüm olup olmadığını denetler. 

Aşağıdaki resimde gösterildiği gibi görselleştiricisi güncelleştirmeleri özellik kılavuzunda: İfade için Sembol bir **SynthesizedIntrinsicOperatorSymbol** ile **tür yöntemi =**.

![Sembol Özellikleri](media/syntax-visualizer/symbol-properties.png)

Deneyin **görünümü TypeSymbol (varsa)** için aynı **AddExpression** düğümü. Görselleştirici özellik kılavuzunda, seçili ifadenin türü olduğunu gösteren aşağıdaki şekilde gösterildiği gibi güncelleştirmeleri `Int32`.

![TypeSymbol özellikleri](media/syntax-visualizer/type-symbol-properties.png)

Deneyin **görünümü dönüştürülen TypeSymbol (varsa)** için aynı **AddExpression** düğümü. Özellik kılavuzunda güncelleştirmeleri olsa da ifadenin türü gösteren `Int32`, dönüştürülen ifade türü `Double` aşağıdaki şekilde gösterildiği gibi. Bu düğüm olduğundan dönüştürülmüş türü sembol bilgilerini içeren `Int32` ifade oluştuğu yeri, dönüştürülmesi gerekir bir bağlamda bir `Double`. Bu dönüştürme karşılayan `Double` değişkeni için belirtilen türü `x` atama işlecinin sol taraftaki.

![Dönüştürülen TypeSymbol özellikleri](media/syntax-visualizer/converted-type-symbol-properties.png)

Son olarak, deneyin **görünümü sabit değeri (varsa)** için aynı **AddExpression** düğümü. Özellik kılavuzunda değer ifadesinin değerine sahip bir derleme zamanı sabiti olduğunu gösterir `2`.

![Sabit değer](media/syntax-visualizer/constant-value.png)

Yukarıdaki örnekte, VB'de çoğaltılabilir Tür `Dim x As Double = 1 + 1` VB dosyasında. Seç ifadesi `1 + 1` kod düzenleyici penceresinde. Görselleştirici ilgili önemli noktalar **AddExpression** Görselleştirici düğümü. Bunun için önceki adımları yineleyin **AddExpression** ve aynı sonuçları görmeniz gerekir.

Daha fazla kod vb'de inceleyin Aşağıdaki kod ile ana VB dosyanızı güncelleştirin:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Bu kod bir diğer ad adlandırılmış tanıtır `C` türüne eşlenir `System.Console` dosyanın üst ve bu diğer adı içinde kullanan `Main()`. Bu diğer ad kullanımı seçin `C` içinde `C.WriteLine()`içine `Main()` yöntemi. Buna karşılık gelen görselleştiricisi seçer **Identifiername** Görselleştirici düğümü. Bu düğüme çift tıklayın ve tıklayarak **görünümü simgesi (varsa)**. Bu tanımlayıcı türe bağlı olduğu özellik kılavuzunda gösterir `System.Console` aşağıdaki şekilde gösterildiği gibi:

![Sembol Özellikleri](media/syntax-visualizer/symbol-visual-basic.png)

Deneyin **görünümü AliasSymbol (varsa)** için aynı **Identifiername** düğümü. Özellik kılavuzunda tanımlayıcı ada sahip bir diğer ad gösterir `C` bağlanan `System.Console` hedef. Diğer bir deyişle, özellik Kılavuzu bilgilerini sağlar ilgili **AliasSymbol** tanımlayıcısına karşılık gelen `C`.

![AliasSymbol özellikleri](media/syntax-visualizer/alias-symbol.png)

Karşılık gelen tüm bildirilen tür, yöntem, özellik sembol inceleyin. Görselleştirici içinde karşılık gelen düğümü seçin ve tıklayın **görünümü simgesi (varsa)**. Yöntemi seçin `Sub Main()`, yöntemin gövdesi de dahil olmak üzere. Tıklayarak **görünümü simgesi (varsa)** karşılık gelen için **SubBlock** Görselleştirici düğümü. Özellik Kılavuzu gösterir **MethodSymbol** bu **SubBlock** adına sahip `Main` dönüş türü ile `Void`.

![Yöntem bildiriminde simgesi görüntüleme](media/syntax-visualizer/method-symbol.png)

Yukarıdaki VB örnekleri kolayca C# ' de çoğaltılabilir. Tür `using C = System.Console;` yerine `Imports C = System.Console` diğer. C# önceki adımlarda görselleştiricisi penceresinde özdeş sonuçlar.

Anlam denetleme işlemleri yalnızca düğümlerinde kullanılabilir. Bunlar, belirteçleri veya Meraklısına Notlar mevcut değildir. Tüm düğümlerin incelemek için ilgi çekici anlamsal bilgilerin vardır. Anlamsal bilgilerin ilgi çekici bir düğüme sahip olmadığında tıklayarak **görünümü \* (varsa) simge** boş özellik kılavuzunda gösterir.

Daha fazla anlam analizi gerçekleştirmek için API'ler ile ilgili [semantik ile çalışma](work-with-semantics.md) genel bakış belgesi.

## <a name="closing-the-syntax-visualizer"></a>Söz dizimi görselleştiricisi kapatma

Bu kaynak kodunu incelemek için değil kullanırken görselleştiricisi penceresini kapatabilirsiniz. Düzenleme ve kaynağını değiştirme kodda gezinmesine gibi söz dizimi görselleştiricisi görünümünü güncelleştirir. Bunu kullanmadığınızda dikkat dağıtıcı alabilirsiniz. 
