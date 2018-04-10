---
title: Visual Studio'da Roslyn sözdizimi Görselleştirici ile kod keşfetme
description: Sözdizimi Görselleştirici .NET derleyici Platform SDK'sı için kod oluşturur modelleri araştırmak için görsel bir araç sağlar.
author: billwagner
ms.author: wiwagn
ms.date: 03/07/2018
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 04452159c759a0c7236c1b93dc966e5e9c54574a
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Visual Studio'da Roslyn sözdizimi Görselleştirici ile kod keşfetme

Bu makalede, .NET derleme Platformu ("Roslyn") SDK'sı bir parçası olarak gönderilen sözdizimi Görselleştirici aracı genel bir bakış sağlar. Sözdizimi Görselleştirici inceleyin ve sözdizimi ağaçları incelemenize yardımcı olacak bir aracı penceredir. Kod analiz etmek istediğiniz modellerini anlamak için önemli bir araçtır. .NET derleme Platformu ("Roslyn") SDK'sını kullanarak kendi uygulamaları geliştirirken ayrıca hata ayıklamaya yardımcı olur. Bu araç, ilk çözümleyiciler oluştururken açın. Görselleştirici API'leri tarafından kullanılan modelleri anlamanıza yardımcı olur. Gibi araçları da kullanabilirsiniz [SharpLab](https://sharplab.io) veya [LINQPad](https://www.linqpad.net/) kodu incelemek ve sözdizimi ağaçları anlamak için.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

.NET derleme Platform SDK'ın okuyarak kullanılan kavramları öğrenmeniz [genel bakış](compiler-api-model.md) makalesi. Sözdizimi ağacı, düğümler, belirteçleri ve trivia bir giriş sağlar.

## <a name="syntax-visualizer"></a>Sözdizimi Görselleştirici

**Sözdizimi Görselleştirici** Visual Studio IDE içinde geçerli etkin Düzenleyicisi penceresini C# veya VB kod dosyasında sözdizimi ağacı incelemesini etkinleştirir. Görselleştirici tıklayarak başlatılabilir **Görünüm** > **diğer pencereler** > **sözdizimi Görselleştirici**.  Aynı zamanda **hızlı başlatma** araç çubuğunda sağ üst köşesinde. Türü "sözdizimi" ve açmak için komuta **sözdizimi Görselleştirici** görünmelidir.

Bu komut sözdizimi Görselleştirici kayan araç penceresi açar. Açık bir kod düzenleyicisi pencere yoksa, görüntü aşağıdaki resimde gösterildiği gibi boştur. 

![Sözdizimi Görselleştirici araç penceresi](media/syntax-visualizer/syntax-visualizer.png)

Bu araç penceresi Visual Studio içinde sol tarafındaki gibi uygun bir konuma yerleştir. Görselleştirici geçerli kod dosyası hakkındaki bilgileri gösterir.

Kullanarak yeni bir proje oluşturmak **dosya** > **yeni proje** komutu. VB veya C# projesi oluşturabilirsiniz. Visual Studio bu proje için ana kod dosya açıldığında Görselleştirici sözdizimi ağacı için gösterir. Tüm mevcut C# açabilirsiniz / VB dosyasında bu Visual Studio örneği ve Görselleştirici dosyanın sözdizimi ağacı görüntüler. Visual Studio içinde açık birden çok kod dosyaları varsa, Görselleştirici (klavye odağı olan kod dosyası.) şu anda etkin olan kod dosyasının sözdizimi ağacı görüntüler.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![C# sözdizimi ağacı Görselleştirme](media/syntax-visualizer/visualize-csharp.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
![VB sözdizimi ağacı Görselleştirme](media/syntax-visualizer/visualize-visual-basic.png)

---

Görselleştirici araç penceresi sözdizimi ağacı önceki görüntüleri gösterildiği gibi üst ve alt özellik Kılavuzu görüntüler. Özellik Kılavuzu .NET dahil olmak üzere ağacında seçili olan öğenin özelliklerini görüntüler *türü* ve *türü* (SyntaxKind) öğenin.

Sözdizimi ağacı oluşturan öğeler – üç tür *düğümleri*, *belirteçleri*, ve *trivia*. Bunlar hakkında daha fazla türleri okuyabilirsiniz [iş sözdizimiyle](work-with-syntax.md) makalesi. Her türdeki öğeleri, farklı bir renk kullanılarak gösterilir. Kullanılan renkleri genel bakış 'Gösterge' düğmesine tıklayın.

Her öğe ağacında Ayrıca kendi görüntüler **span**. **Span** bu düğümün metin dosyasında (başlangıç ve bitiş konumu) dizinlerini olduğu.  Önceki örnekte C#, seçili "UsingKeyword [0..5)" belirtecine sahip bir **aralık** diğer bir deyişle beş karakteri geniş, [0..5). "[.)" Gösterimi anlamına gelir başlangıç dizini aralık parçası olan, ancak bitiş dizini değil.

Ağaç gitmek için iki yolu vardır:
* Genişletin veya ağacındaki öğeleri tıklayın. Görselleştirici bu öğenin aralık Kod düzenleyicisinde karşılık gelen metin otomatik olarak seçer.
* ' I tıklatın veya Kod düzenleyicisinde metni seçin. Kod Düzenleyicisi'nde "Module Module1" içeren satırı seçerseniz önceki VB örnekte Görselleştirici ağacında karşılık gelen ModuleStatement düğüme otomatik olarak gider. 

Görselleştirici Metin Düzenleyicisi'nde seçili aralık, aralık en iyi eşleşen ağacını öğesinde vurgular.

Görselleştirici etkin kod dosyasında değişiklikleriyle eşleşecek şekilde ağaç yeniler. Bir çağrı ekleyin `Console.WriteLine()` içinde `Main()`. Siz yazarken, Görselleştirici ağaç yeniler.

Bir kez yazdığınız Duraklat yazılan `Console.`. Ağaç Pembe olarak renkli bazı öğeler vardır. Bu noktada, yazılan kod hataları ('Olarak Tanılama' da denir) vardır. Bu hatalar düğümleri, belirteçleri ve sözdizimi ağacında trivia eklenir. Görselleştirici hangi bağlı hataları öğeleriniz arka planda pembe vurgulama onlara gösterir. Öğenin üzerine gelerek Pembe renkli herhangi bir öğeyi hataları inceleyebilirsiniz. Görselleştirici söz dizimi hataları (Bu hatalar yazılan kod sözdizimi için ilgili); yalnızca görüntüler. anlamsal hataları görüntülemez.
 
## <a name="syntax-graphs"></a>Sözdizimi grafikleri

Ağacındaki herhangi bir öğeyi sağ tıklayın ve tıklayın **görünüm yönlendirilmiş sözdizimi grafik**. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Seçili öğeyi kökü alt ağacı grafik gösterimi Görselleştirici görüntüler. İçin aşağıdaki adımları deneyin **MethodDeclaration** düğümü karşılık gelen `Main()` C# örnek yöntemi. Görselleştirici aşağıdaki gibi görünen bir sözdizimi grafiği görüntüler:

![Bir C# sözdizimi grafik görüntüleme](media/syntax-visualizer/csharp-syntax-graph.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)

Aynı deneyin **SubBlock** düğümü karşılık gelen `Main()` önceki VB örnekte yöntemi. Görselleştirici aşağıdaki gibi görünen bir sözdizimi grafiği görüntüler:

![VB sözdizimi grafik görüntüleme](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Sözdizimi grafik Görüntüleyicisi'ni renklendirme düzenini bir gösterge görüntüleme seçeneği vardır. Bu öğeye karşılık gelen özelliklerini görüntülemek için fare ile sözdizimi grafik öğeleri ayrı ayrı üzerinden gelebilirsiniz.

Grafikleri always Visual Studio içinde aynı pencerede görüntülenir ve art arda ağacında farklı öğeleri için sözdizimi grafikleri görüntüleyebilir. Yeni bir sözdizimi grafik görüntülemek için Sekmeler arasında geçiş yapmanız gerekmez, bu pencereyi Visual Studio içindeki uygun bir konumda sabitleyebilirsiniz. Kod Düzenleyicisi windows, aşağıda alt genellikle uygundur.

Görselleştirici araç penceresi ve sözdizimi grafik penceresi ile kullanılacak yerleştirme düzenini şöyledir:

![Görselleştirici ve sözdizimi grafik penceresi için bir yerleştirme düzeni](media/syntax-visualizer/docking-layout.png)

Bir çift monitör kurulumunda bir ikinci monitörde sözdizimi grafiği pencere put başka bir seçenektir.

# <a name="inspecting-semantics"></a>İnceleme semantiği

Sözdizimi Görselleştirici sembolleri ve anlamsal bilgilerin ilkel incelemesini etkinleştirir. Türü `double x = 1 + 1;` C# örnekte Main() içinde. İfade seçip `1 + 1` Kod Düzenleyicisi penceresinde. Görselleştirici vurgular **AddExpression** Görselleştirici düğümünde. Sağ bu tıklayın **AddExpression** ve tıklayın **görünümü simgesi (varsa)**. Menü öğelerinin çoğunu "varsa" niteleyicisi sahip dikkat edin. Sözdizimi Görselleştirici tüm düğümler için bulunmayabilir özellikler de dahil olmak üzere bir düğümü özelliklerini inceler. 

Görselleştirici özellik kılavuzunda aşağıdaki çizimde gösterildiği gibi güncelleştirir: simge ifadesi için bir **SynthesizedIntrinsicOperatorSymbol** ile **türü = yöntemi**.

![Sembol Özellikleri](media/syntax-visualizer/symbol-properties.png)

Deneyin **görünüm TypeSymbol (varsa)** aynı için **AddExpression** düğümü. Görselleştirici özellik kılavuzunda, seçilen ifade türü olduğunu gösteren aşağıdaki şekilde gösterildiği gibi güncelleştirmeleri `Int32`.

![TypeSymbol özellikleri](media/syntax-visualizer/type-symbol-properties.png)

Deneyin **görünüm dönüştürülen TypeSymbol'nı (varsa)** aynı için **AddExpression** düğümü. Özellik Kılavuzu güncelleştirmeleri ifade türü olmasına karşın gösteren `Int32`, dönüştürülmüş ifade türüdür `Double` aşağıdaki resimde gösterildiği gibi. Bu düğüm olduğundan dönüştürülen türü sembol bilgilerini içerir `Int32` ifade oluşur burada bunu dönüştürülmesi gerekir bağlamda bir `Double`. Bu dönüştürme karşılayan `Double` değişken için belirtilen türü `x` atama işlecinin sol tarafındaki.

![Dönüştürülen TypeSymbol özellikleri](media/syntax-visualizer/converted-type-symbol-properties.png)

Son olarak, deneyin **görünüm sabit değer (varsa)** aynı için **AddExpression** düğümü. Özellik Kılavuzu ifadesinin değerini değerine sahip bir derleme zamanı sabiti gösterir `2`.

![Sabit bir değer](media/syntax-visualizer/constant-value.png)

Önceki örnekte de VB'de çoğaltılabilir Tür `Dim x As Double = 1 + 1` VB dosyasında. İfadeyi seçin `1 + 1` Kod Düzenleyicisi penceresinde. Karşılık gelen Görselleştirici vurgular **AddExpression** Görselleştirici düğümünde. Bunun için önceki adımları yineleyin **AddExpression** ve aynı sonuçları görmeniz gerekir.

Daha fazla kod vb'deki inceleyin Ana VB dosyanızı aşağıdaki kod ile güncelleştirin:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Bu kod bir diğer ad adlandırılmış tanıtır `C` türüne eşlenir `System.Console` dosyasının üst ve bu diğer adı içinde kullanır `Main()`. Bu diğer adı kullanın `C` içinde `C.WriteLine()`içine `Main()` yöntemi. Karşılık gelen Görselleştirici seçer **IdentifierName** Görselleştirici düğümünde. Bu düğüme sağ tıklayın ve tıklayın **görünümü simgesi (varsa)**. Bu tanımlayıcı türüne bağlıdır ve özellik ızgarasının gösterir `System.Console` aşağıdaki resimde gösterildiği gibi:

![Sembol Özellikleri](media/syntax-visualizer/symbol-visual-basic.png)

Deneyin **görünüm AliasSymbol (varsa)** aynı için **IdentifierName** düğümü. Özellik Kılavuzu tanımlayıcı adı içeren bir diğer ad gösterir `C` için bağlı `System.Console` hedef. Diğer bir deyişle, özellik Kılavuzu bilgilerini sağlar ilgili **AliasSymbol** tanımlayıcısına karşılık gelen `C`.

![AliasSymbol özellikleri](media/syntax-visualizer/alias-symbol.png)

Karşılık gelen hiçbir bildirilen türü, yöntemi, özelliği simgesi inceleyin. Görselleştirici karşılık gelen düğümü seçin ve tıklayın **görünümü simgesi (varsa)**. Yöntem `Sub Main()`, yönteminin gövdesi dahil olmak üzere. Tıklayın **görünümü simgesi (varsa)** karşılık gelen için **SubBlock** Görselleştirici düğümünde. Özellik Kılavuzu gösterir **MethodSymbol** bu **SubBlock** adına sahip `Main` ile dönüş türü `Void`.

![Simge bir yöntem bildirimi için görüntüleme](media/syntax-visualizer/method-symbol.png)

Yukarıdaki VB örnekleri kolayca C# ' ta çoğaltılabilir. Tür `using C = System.Console;` yerine `Imports C = System.Console` diğer. Önceki adımlarda C# Görselleştirici penceresinde aynı sonuçlar.

Anlam denetleme işlemleri yalnızca düğümler üzerinde kullanılabilir. Bunlar belirteçleri veya trivia kullanılabilir değildir. Tüm düğümlerin incelemek için ilginç anlamsal bilgilerin vardır. Bir düğüm anlamsal bilgilerin ilginç sahip olmadığında tıklayarak **Görünüm * (varsa) sembol** boş özellik Kılavuzu gösterir.

Daha fazla bilgiyi anlamsal analiz gerçekleştirme API'leri hakkında [iş semantiği ile](work-with-semantics.md) genel bakış belgesi.

## <a name="closing-the-syntax-visualizer"></a>Sözdizimi Görselleştirici kapatma

Bu kaynak kodunu incelemek için kullandığında Görselleştirici pencereyi kapatabilirsiniz. Düzenleme ve kaynağını değiştirme kodda gezinmesine gibi sözdizimi Görselleştirici görünümünü güncelleştirir. Bunu kullanmadığınızda dikkat dağıtıcı alabilirsiniz. 
