---
title: Visual Studio 'da Roslyn sözdizimi görselleştiricisi ile kodu araştırma
description: Sözdizimi görselleştiricisi .NET Compiler Platform SDK 'nın kod için oluşturduğu modelleri araştırmak için görsel bir araç sağlar.
ms.date: 03/07/2018
ms.custom: mvc, vs-dotnet
ms.openlocfilehash: c4b4414dabcb6c9749a23d726e4a69334376d988
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346962"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Visual Studio 'da Roslyn sözdizimi görselleştiricisi ile kodu araştırma

Bu makalede, .NET Compiler Platform ("Roslyn") SDK 'sının bir parçası olarak gönderilen Syntax Visualizer aracına genel bakış sunulmaktadır. Syntax Visualizer, sözdizimi ağaçlarını incelemenize ve keşfetmenize yardımcı olan bir araç penceresidir. Analiz etmek istediğiniz kod modellerini anlamak için gerekli olan bir araçtır. Ayrıca, .NET Compiler Platform ("Roslyn") SDK 'sını kullanarak kendi uygulamalarınızı geliştirirken hata ayıklama yardımıdır. İlk çözümleyicinizi oluştururken bu aracı açın. Görselleştiricisi API 'Ler tarafından kullanılan modelleri anlamanıza yardımcı olur. Kod incelemek ve sözdizimi ağaçlarını anlamak için, [parça](https://sharplab.io) veya [linqpad](https://www.linqpad.net/) gibi araçları da kullanabilirsiniz.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

[Genel bakış](compiler-api-model.md) makalesini okuyarak .net Compiler Platform SDK 'sında kullanılan kavramları öğrenmeye çalışın. Sözdizimi ağaçları, düğümleri, belirteçleri ve trivia için bir giriş sağlar.

## <a name="syntax-visualizer"></a>Syntax Visualizer

**Syntax Visualizer** , VISUAL Studio IDE içindeki geçerli etkin düzenleyici penceresinde C# veya Visual Basic kod dosyası için sözdizimi ağacının incelemesini mümkün. Görselleştirici, **diğer Windows** > **Syntax Visualizer** > **görüntüle** ' ye tıklanarak başlatılabilir.  Sağ üst köşedeki **Hızlı başlatma** araç çubuğunu da kullanabilirsiniz. "Sözdizimi" yazın ve **Syntax Visualizer** açmak için komut görünmelidir.

Bu komut Syntax Visualizer kayan bir araç penceresi olarak açar. Bir kod Düzenleyicisi penceresi açık değilse, aşağıdaki şekilde gösterildiği gibi görüntü boştur. 

![Syntax Visualizer araç penceresi](media/syntax-visualizer/syntax-visualizer.png)

Bu araç penceresini, Visual Studio içinde, sol taraftaki gibi uygun bir konuma yerleştirin. Görselleştirici, geçerli kod dosyası hakkındaki bilgileri gösterir.

**Yeni proje** komutunu > **dosyayı** kullanarak yeni bir proje oluşturun. Bir Visual Basic ya C# da proje oluşturabilirsiniz. Visual Studio bu proje için ana kod dosyasını açtığında Görselleştirici kendisi için sözdizimi ağacını görüntüler. Bu Visual Studio örneğindeki herhangi C# bir mevcut/Visual Basic dosyasını açabilirsiniz ve Görselleştirici bu dosyanın sözdizimi ağacını görüntüler. Visual Studio içinde açık olan birden çok kod dosyanız varsa, Görselleştirici geçerli etkin kod dosyası (klavye odağına sahip kod dosyası) için sözdizimi ağacını görüntüler.

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Bir C# sözdizimi ağacını görselleştirme](media/syntax-visualizer/visualize-csharp.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
![Visual Basic sözdizimi ağacını görselleştirme](media/syntax-visualizer/visualize-visual-basic.png)

---

Önceki görüntülerde gösterildiği gibi, Görselleştirici araç penceresi üstteki sözdizimi ağacını ve alt kısımdaki bir özellik kılavuzunu görüntüler. Özellik Kılavuzu, öğenin .NET *türü* ve *türü* (ağacın syntaxkind içeren) dahil olmak üzere ağaçta seçili olan öğenin özelliklerini görüntüler.

Sözdizimi ağaçları, *düğüm*, *belirteç*ve *bilgi*olmak üzere üç öğe türünü kapsar. [Söz dizimi Ile çalışma](work-with-syntax.md) makalesinde bu türler hakkında daha fazla bilgi edinebilirsiniz. Her türün öğeleri farklı bir renk kullanılarak temsil edilir. Kullanılan renklere genel bakış için ' gösterge ' düğmesine tıklayın.

Ağaçtaki her öğe ayrıca kendi **yayılma alanını**da görüntüler. **Yayılma** , metin dosyasındaki bu düğümün indekslerini (başlangıç ve bitiş konumu).  Yukarıdaki C# örnekte, seçili "usinganahtar sözcüğü [0.. 5)" belirtecinin, beş karakter genişliğinde, [0.. 5) bir **yayılımı** vardır. "[..)" Gösterimi Başlangıç dizininin yayılma alanının parçası olduğu, ancak bitiş dizininin olmadığı anlamına gelir.

Ağaçta gezinmek için iki yol vardır:

* Ağaçtaki öğeler ' i genişletin veya tıklayın. Görselleştirici, kod düzenleyicisinde bu öğenin alanına karşılık gelen metni otomatik olarak seçer.
* Kod düzenleyicisinde metin ' e tıklayın veya seçin. Yukarıdaki Visual Basic örneğinde, kod düzenleyicisinde "Module Module1" içeren satırı seçerseniz, Görselleştirici otomatik olarak ağaçta karşılık gelen Moduledeyimdüğümüne gider. 

Görselleştirici, alanı düzenleyicide seçili olan metnin yayılımının en iyi şekilde eşleştiği ağaçtaki öğeyi vurgular.

Görselleştirici, etkin kod dosyasındaki değişikliklerle eşleşecek şekilde ağacı yeniler. `Main()`içinde `Console.WriteLine()` bir çağrı ekleyin. Siz yazarken, görselleştiricisi ağacı yeniler.

`Console.`yazdıktan sonra yazmayı duraklatın. Ağaçta, pembe renkte renkli bazı öğeler vardır. Bu noktada, yazılan koddaki hatalar (' Tanılama ' olarak da bilinir) vardır. Bu hatalar, söz dizimi ağacındaki düğümlere, belirteçlere ve üçlü öğesine eklenir. Görselleştirici, arka planı pembe olarak vurgulamada hangi öğelerin ekli hatalara sahip olduğunu gösterir. Öğenin üzerine gelerek pembe renkte renklendirilmiş hataları inceleyebilirsiniz. Görselleştirici yalnızca sözdizimsel hataları (yazılan kodun sözdizimiyle ilgili hatalar) görüntüler; hiçbir semantik hata görüntülemez.
 
## <a name="syntax-graphs"></a>Sözdizimi grafikleri

Ağaçtaki herhangi bir öğeye sağ tıklayın ve **yönlendirilmiş sözdizimi grafiğini görüntüle**' ye tıklayın. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Görselleştirici, seçili öğede kökü belirtilen alt ağacın grafik temsilini görüntüler. C# Örnekteki `Main()` yöntemine karşılık gelen **MethodDeclaration** düğümü için aşağıdaki adımları deneyin. Görselleştiricisi aşağıdaki gibi görünen bir sözdizimi grafiği görüntüler:

![Bir C# sözdizimi grafiğini görüntüleme](media/syntax-visualizer/csharp-syntax-graph.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

Önceki Visual Basic örneğinde `Main()` yöntemine karşılık gelen **alt blok** düğümü için aynısını deneyin. Görselleştiricisi aşağıdaki gibi görünen bir sözdizimi grafiği görüntüler:

![Visual Basic söz dizimi grafiğini görüntüleme](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Söz dizimi grafik görüntüleyicisinde gösterge renklendirme şeması görüntüleme seçeneği vardır. Ayrıca söz konusu öğeye karşılık gelen özellikleri görüntülemek için, söz dizimi grafiğinde tek tek öğelerin üzerine gelin.

Ağaçtaki farklı öğeler için sözdizimi grafiklerini art arda görüntüleyebilirsiniz ve grafikler her zaman Visual Studio içindeki aynı pencerede görüntülenir. Bu pencereyi Visual Studio içinde uygun bir konuma yerleştirebilirsiniz, böylece yeni bir sözdizimi grafiğini görüntülemek için sekmeler arasında geçiş yapmanız gerekmez. En alttaki kod Düzenleyicisi pencereleri, genellikle kullanışlıdır.

Görselleştiricisi araç penceresi ve söz dizimi grafik penceresi ile kullanılacak yerleştirme düzeni aşağıda verilmiştir:

![Görselleştirici ve söz dizimi grafik penceresi için bir yerleştirme düzeni](media/syntax-visualizer/docking-layout.png)

Diğer bir seçenek de, sözdizimi grafik penceresini ikinci bir monitöre bir çift izleyici kurulumuna koyulamıyor.

## <a name="inspecting-semantics"></a>Semantiğini İnceleme

Syntax Visualizer, sembolleri ve anlam bilgilerini ilkel denetlemesini mümkün. C# Örnekteki Main () içine `double x = 1 + 1;` yazın. Ardından, kod Düzenleyicisi penceresinde `1 + 1` ifadeyi seçin. Görselleştirici, görselleştiricide **AddExpression** düğümünü vurgular. Bu **AddExpression** öğesine sağ tıklayın ve **Görünüm simgesine (varsa)** tıklayın. Menü öğelerinin çoğunda "varsa" niteleyicisi olduğuna dikkat edin. Syntax Visualizer, tüm düğümler için mevcut olmayan özellikler de dahil olmak üzere bir düğümün özelliklerini inceler. 

Aşağıdaki şekilde gösterildiği gibi görselleştiricisi güncelleştirmelerinde bulunan Özellik Kılavuzu: ifade sembolü, **Kind = yöntemi**Içeren bir **SynthesizedIntrinsicOperatorSymbol** .

![Sembol özellikleri](media/syntax-visualizer/symbol-properties.png)

Aynı **AddExpression** düğümü için **TypeSymbol (varsa) görüntülemeyi** deneyin. Aşağıdaki şekilde gösterildiği gibi, Görselleştirici güncelleştirmelerinde bulunan Özellik Kılavuzu, seçili ifadenin türünün `Int32`olduğunu gösterir.

![TypeSymbol özellikleri](media/syntax-visualizer/type-symbol-properties.png)

Aynı **AddExpression** düğümü Için **dönüştürülmüş TypeSymbol (varsa) görüntülemeyi** deneyin. Özellik Kılavuzu, ifadenin türü `Int32`olsa da, ifadenin dönüştürülmüş türünün, aşağıdaki şekilde gösterildiği gibi `Double` olduğunu gösterir. Bu düğüm dönüştürülmüş tür sembol bilgisini içerir çünkü `Int32` ifadesi bir `Double`dönüştürülmesi gereken bir bağlamda meydana gelir. Bu dönüştürme, atama işlecinin sol tarafındaki `x` değişkeni için belirtilen `Double` türünü karşılar.

![Dönüştürülen TypeSymbol özellikleri](media/syntax-visualizer/converted-type-symbol-properties.png)

Son olarak, aynı **AddExpression** düğümü Için **sabit değeri (varsa) görüntülemeyi** deneyin. Özellik Kılavuzu, ifadenin değerinin `2`değeri olan bir derleme zamanı sabiti olduğunu gösterir.

![Sabit değer](media/syntax-visualizer/constant-value.png)

Yukarıdaki örnek, Visual Basic de çoğaltılabilir. Visual Basic bir dosyaya `Dim x As Double = 1 + 1` yazın. Kod Düzenleyicisi penceresinde `1 + 1` ifade seçin. Görselleştirici, görselleştiricide karşılık gelen **AddExpression** düğümünü vurgular. Bu **AddExpression** için önceki adımları tekrarlayın ve özdeş sonuçlar görmeniz gerekir.

Visual Basic daha fazla kod inceleyin. Ana Visual Basic dosyanızı aşağıdaki kodla güncelleştirin:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Bu kod, dosyanın üst kısmında `System.Console` tür ile eşleyen `C` adlı bir diğer ad tanıtır ve bu diğer adı `Main()`içinde kullanır. Bu diğer adın kullanımını, `Main()` yönteminin içindeki `C.WriteLine()``C` seçin. Görselleştiricisi görselleştiricide karşılık gelen **IdentifierName** düğümünü seçer. Bu düğüme sağ tıklayın ve **Görünüm simgesine (varsa)** tıklayın. Özellik Kılavuzu, Bu tanımlayıcının aşağıdaki şekilde gösterildiği gibi tür `System.Console` bağlandığını gösterir:

![Sembol özellikleri](media/syntax-visualizer/symbol-visual-basic.png)

Aynı **IdentifierName** düğümü için **bir diğer simge (varsa) görüntülemeyi** deneyin. Özellik Kılavuzu, tanımlayıcının `System.Console` hedefine bağlanan `C` adlı bir diğer ad olduğunu gösterir. Diğer bir deyişle, özellik Kılavuzu `C`tanımlayıcı **sembolüyle** ilgili bilgiler sağlar.

![Diğerad sembol özellikleri](media/syntax-visualizer/alias-symbol.png)

Her türlü tanımlanmış türe, yönteme ve özelliğe karşılık gelen sembolü inceleyin. Görselleştirici içinde karşılık gelen düğümü seçin ve **Görünüm simgesine (varsa)** tıklayın. Yöntemin gövdesi dahil `Sub Main()`yöntemini seçin. Görselleştirici içindeki karşılık gelen **alt blok** düğümü Için **Görünüm simgesine (varsa)** tıklayın. Özellik Kılavuzu, bu **alt blok** Için **methodsymbol** 'ın `Void`dönüş türü `Main` adına sahip olduğunu gösterir.

![Yöntem bildirimi için simge görüntüleme](media/syntax-visualizer/method-symbol.png)

Yukarıdaki Visual Basic örnekleri ' de C#kolayca çoğaltılabilir. Diğer ad için `Imports C = System.Console` yerine `using C = System.Console;` yazın. Yukarıdaki adımlar, Görselleştirici penceresinde özdeş sonuçlar elde ediyor C# .

Anlamsal İnceleme işlemleri yalnızca düğümlerde kullanılabilir. Belirteçler veya trivia üzerinde kullanılamaz. Tüm düğümlerin incelemeye yönelik ilginç anlam bilgileri yoktur. Bir düğüm ilginç anlam bilgisine sahip olmadığında **görünüm \* simgesine tıklamak (varsa)** boş bir özellik kılavuzunu gösterir.

[Semantiğe](work-with-semantics.md) genel bakış belgesinde semantik analizler gerçekleştirmek Için API 'ler hakkında daha fazla bilgi edinebilirsiniz.

## <a name="closing-the-syntax-visualizer"></a>Sözdizimi Görselleştiricisini kapatma

Kaynak kodu incelemek için kullanmıyorsanız Görselleştirici penceresini kapatabilirsiniz. Sözdizimi görselleştiricisi, kod içinde gezinerek, kaynak düzenlenirken ve değiştirirken görüntüsünü günceller. Bu, kullanmadığınız durumlarda dikkat dağıtıcı alabilir. 
