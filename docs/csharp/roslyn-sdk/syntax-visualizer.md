---
title: Visual Studio 'da Roslyn sözdizimi görselleştiricisi ile kodu araştırma
description: Sözdizimi görselleştiricisi .NET Compiler Platform SDK 'nın kod için oluşturduğu modelleri araştırmak için görsel bir araç sağlar.
ms.date: 03/07/2018
ms.custom: mvc, vs-dotnet
ms.openlocfilehash: a911a99e78ad5a5f4c6771b91a3c541b1812d67c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167580"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Visual Studio 'da Roslyn sözdizimi görselleştiricisi ile kodu araştırma

Bu makalede, .NET Compiler Platform ("Roslyn") SDK 'sının bir parçası olarak gönderilen Syntax Visualizer aracına genel bakış sunulmaktadır. Syntax Visualizer, sözdizimi ağaçlarını incelemenize ve keşfetmenize yardımcı olan bir araç penceresidir. Analiz etmek istediğiniz kod modellerini anlamak için gerekli olan bir araçtır. Ayrıca, .NET Compiler Platform ("Roslyn") SDK 'sını kullanarak kendi uygulamalarınızı geliştirirken hata ayıklama yardımıdır. İlk çözümleyicinizi oluştururken bu aracı açın. Görselleştiricisi API 'Ler tarafından kullanılan modelleri anlamanıza yardımcı olur. Kod incelemek ve sözdizimi ağaçlarını anlamak için, [parça](https://sharplab.io) veya [linqpad](https://www.linqpad.net/) gibi araçları da kullanabilirsiniz.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

[Genel bakış](compiler-api-model.md) makalesini okuyarak .net Compiler Platform SDK 'sında kullanılan kavramları öğrenmeye çalışın. Sözdizimi ağaçları, düğümleri, belirteçleri ve trivia için bir giriş sağlar.

## <a name="syntax-visualizer"></a>Syntax Visualizer

**Syntax Visualizer** , VISUAL Studio IDE içindeki geçerli etkin düzenleyici penceresinde C# veya Visual Basic kod dosyası için sözdizimi ağacının incelemesini mümkün. Görselleştirici, **View**  >  **diğer Windows**  >  **Syntax Visualizer**görüntüle ' ye tıklanarak başlatılabilir.  Sağ üst köşedeki **Hızlı başlatma** araç çubuğunu da kullanabilirsiniz. "Sözdizimi" yazın ve **Syntax Visualizer** açmak için komut görünmelidir.

Bu komut Syntax Visualizer kayan bir araç penceresi olarak açar. Bir kod Düzenleyicisi penceresi açık değilse, aşağıdaki şekilde gösterildiği gibi görüntü boştur.

![Syntax Visualizer araç penceresi](media/syntax-visualizer/syntax-visualizer.png)

Bu araç penceresini, Visual Studio içinde, sol taraftaki gibi uygun bir konuma yerleştirin. Görselleştirici, geçerli kod dosyası hakkındaki bilgileri gösterir.

**Dosya**  >  **Yeni proje** komutunu kullanarak yeni bir proje oluşturun. Bir Visual Basic ya da C# projesi oluşturabilirsiniz. Visual Studio bu proje için ana kod dosyasını açtığında Görselleştirici kendisi için sözdizimi ağacını görüntüler. Bu Visual Studio örneğinde var olan herhangi bir C#/Visual Basic dosyasını açabilirsiniz ve Görselleştirici bu dosyanın sözdizimi ağacını görüntüler. Visual Studio içinde açık olan birden çok kod dosyanız varsa, Görselleştirici geçerli etkin kod dosyası (klavye odağına sahip kod dosyası) için sözdizimi ağacını görüntüler.

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

![C# sözdizimi ağacını görselleştirme](media/syntax-visualizer/visualize-csharp.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

![Visual Basic sözdizimi ağacını görselleştirme](media/syntax-visualizer/visualize-visual-basic.png)

---

Önceki görüntülerde gösterildiği gibi, Görselleştirici araç penceresi üstteki sözdizimi ağacını ve alt kısımdaki bir özellik kılavuzunu görüntüler. Özellik Kılavuzu, öğenin .NET *türü* ve *türü* (ağacın syntaxkind içeren) dahil olmak üzere ağaçta seçili olan öğenin özelliklerini görüntüler.

Sözdizimi ağaçları, *düğüm*, *belirteç*ve *bilgi*olmak üzere üç öğe türünü kapsar. [Söz dizimi Ile çalışma](work-with-syntax.md) makalesinde bu türler hakkında daha fazla bilgi edinebilirsiniz. Her türün öğeleri farklı bir renk kullanılarak temsil edilir. Kullanılan renklere genel bakış için ' gösterge ' düğmesine tıklayın.

Ağaçtaki her öğe ayrıca kendi **yayılma alanını**da görüntüler. **Yayılma** , metin dosyasındaki bu düğümün indekslerini (başlangıç ve bitiş konumu).  Önceki C# örneğinde, seçili "Usinganahtar sözcüğü [0.. 5)" belirtecinin, beş karakter genişliğinde, [0.. 5) bir **yayılımı** vardır. "[..)" Gösterimi Başlangıç dizininin yayılma alanının parçası olduğu, ancak bitiş dizininin olmadığı anlamına gelir.

Ağaçta gezinmek için iki yol vardır:

* Ağaçtaki öğeler ' i genişletin veya tıklayın. Görselleştirici, kod düzenleyicisinde bu öğenin alanına karşılık gelen metni otomatik olarak seçer.
* Kod düzenleyicisinde metin ' e tıklayın veya seçin. Yukarıdaki Visual Basic örneğinde, kod düzenleyicisinde "Module Module1" içeren satırı seçerseniz, Görselleştirici otomatik olarak ağaçta karşılık gelen Moduledeyimdüğümüne gider.

Görselleştirici, alanı düzenleyicide seçili olan metnin yayılımının en iyi şekilde eşleştiği ağaçtaki öğeyi vurgular.

Görselleştirici, etkin kod dosyasındaki değişikliklerle eşleşecek şekilde ağacı yeniler. İçine bir çağrı ekleyin `Console.WriteLine()` `Main()` . Siz yazarken, görselleştiricisi ağacı yeniler.

Yazdıktan sonra yazmayı duraklatın `Console.` . Ağaçta, pembe renkte renkli bazı öğeler vardır. Bu noktada, yazılan koddaki hatalar (' Tanılama ' olarak da bilinir) vardır. Bu hatalar, söz dizimi ağacındaki düğümlere, belirteçlere ve üçlü öğesine eklenir. Görselleştirici, arka planı pembe olarak vurgulamada hangi öğelerin ekli hatalara sahip olduğunu gösterir. Öğenin üzerine gelerek pembe renkte renklendirilmiş hataları inceleyebilirsiniz. Görselleştirici yalnızca sözdizimsel hataları (yazılan kodun sözdizimiyle ilgili hatalar) görüntüler; hiçbir semantik hata görüntülemez.

## <a name="syntax-graphs"></a>Sözdizimi grafikleri

Ağaçtaki herhangi bir öğeye sağ tıklayın ve **yönlendirilmiş sözdizimi grafiğini görüntüle**' ye tıklayın.

# <a name="c"></a>[C#](#tab/csharp)

Görselleştirici, seçili öğede kökü belirtilen alt ağacın grafik temsilini görüntüler. C# örneğinde yöntemine karşılık gelen **MethodDeclaration** düğümü için bu adımları deneyin `Main()` . Görselleştiricisi aşağıdaki gibi görünen bir sözdizimi grafiği görüntüler:

![C# sözdizimi grafiğini görüntüleme](media/syntax-visualizer/csharp-syntax-graph.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

Yukarıdaki Visual Basic örnekteki yönteme karşılık gelen **alt blok** düğümü için aynısını deneyin `Main()` . Görselleştiricisi aşağıdaki gibi görünen bir sözdizimi grafiği görüntüler:

![Visual Basic söz dizimi grafiğini görüntüleme](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Söz dizimi grafik görüntüleyicisinde, renklendirme şeması için bir gösterge görüntüleme seçeneği vardır. Ayrıca söz konusu öğeye karşılık gelen özellikleri görüntülemek için, söz dizimi grafiğinde tek tek öğelerin üzerine gelin.

Ağaçtaki farklı öğeler için sözdizimi grafiklerini art arda görüntüleyebilirsiniz ve grafikler her zaman Visual Studio içindeki aynı pencerede görüntülenir. Bu pencereyi Visual Studio içinde uygun bir konuma yerleştirebilirsiniz, böylece yeni bir sözdizimi grafiğini görüntülemek için sekmeler arasında geçiş yapmanız gerekmez. En alttaki kod Düzenleyicisi pencereleri, genellikle kullanışlıdır.

Görselleştiricisi araç penceresi ve söz dizimi grafik penceresi ile kullanılacak yerleştirme düzeni aşağıda verilmiştir:

![Görselleştirici ve söz dizimi grafik penceresi için bir yerleştirme düzeni](media/syntax-visualizer/docking-layout.png)

Diğer bir seçenek de, sözdizimi grafik penceresini ikinci bir monitöre bir çift izleyici kurulumuna koyulamıyor.

## <a name="inspecting-semantics"></a>Semantiğini İnceleme

Syntax Visualizer, sembolleri ve anlam bilgilerini ilkel denetlemesini mümkün. `double x = 1 + 1;`C# örneğinde Main () içine yazın. Ardından, `1 + 1` Kod Düzenleyicisi penceresinde ifadeyi seçin. Görselleştirici, görselleştiricide **AddExpression** düğümünü vurgular. Bu **AddExpression** öğesine sağ tıklayın ve **Görünüm simgesine (varsa)** tıklayın. Menü öğelerinin çoğunda "varsa" niteleyicisi olduğuna dikkat edin. Syntax Visualizer, tüm düğümler için mevcut olmayan özellikler de dahil olmak üzere bir düğümün özelliklerini inceler.

Aşağıdaki şekilde gösterildiği gibi görselleştiricisi güncelleştirmelerinde bulunan Özellik Kılavuzu: ifade sembolü, **Kind = yöntemi**Içeren bir **SynthesizedIntrinsicOperatorSymbol** .

![Sembol özellikleri](media/syntax-visualizer/symbol-properties.png)

Aynı **AddExpression** düğümü için **TypeSymbol (varsa) görüntülemeyi** deneyin. Aşağıdaki şekilde gösterildiği gibi, Görselleştirici güncelleştirmelerinde bulunan Özellik Kılavuzu, seçili ifadenin türünün olduğunu gösterir `Int32` .

![TypeSymbol özellikleri](media/syntax-visualizer/type-symbol-properties.png)

Aynı **AddExpression** düğümü Için **dönüştürülmüş TypeSymbol (varsa) görüntülemeyi** deneyin. Özellik Kılavuzu, ifadenin türü olsa da, `Int32` ifadenin dönüştürülmüş türünün `Double` aşağıdaki şekilde gösterildiği gibi olduğunu gösterir. Bu düğüm, dönüştürülmüş tür sembol bilgisini içerir, çünkü `Int32` ifade, öğesine dönüştürülmesi gereken bir bağlamda meydana gelir `Double` . Bu dönüştürme, `Double` `x` atama işlecinin sol tarafındaki değişken için belirtilen türü karşılar.

![Dönüştürülen TypeSymbol özellikleri](media/syntax-visualizer/converted-type-symbol-properties.png)

Son olarak, aynı **AddExpression** düğümü Için **sabit değeri (varsa) görüntülemeyi** deneyin. Özellik Kılavuzu, ifadenin değerinin değeri olan bir derleme zamanı sabiti olduğunu gösterir `2` .

![Sabit değer](media/syntax-visualizer/constant-value.png)

Yukarıdaki örnek, Visual Basic de çoğaltılabilir. `Dim x As Double = 1 + 1`Bir Visual Basic dosyasına yazın. `1 + 1`Kod Düzenleyicisi penceresinde ifadeyi seçin. Görselleştirici, görselleştiricide karşılık gelen **AddExpression** düğümünü vurgular. Bu **AddExpression** için önceki adımları tekrarlayın ve özdeş sonuçlar görmeniz gerekir.

Visual Basic daha fazla kod inceleyin. Ana Visual Basic dosyanızı aşağıdaki kodla güncelleştirin:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Bu kod, dosyanın en üstünde bulunan türle eşleşen adlı bir diğer ad tanıtır `C` `System.Console` ve bu diğer adı içinde kullanır `Main()` . İçindeki bu diğer adın kullanımını, `C` `C.WriteLine()` yöntemi içinde seçin `Main()` . Görselleştiricisi görselleştiricide karşılık gelen **IdentifierName** düğümünü seçer. Bu düğüme sağ tıklayın ve **Görünüm simgesine (varsa)** tıklayın. Özellik Kılavuzu, Bu tanımlayıcının `System.Console` aşağıdaki şekilde gösterildiği gibi türe bağlandığını gösterir:

![Sembol özellikleri](media/syntax-visualizer/symbol-visual-basic.png)

Aynı **IdentifierName** düğümü için **bir diğer simge (varsa) görüntülemeyi** deneyin. Özellik Kılavuzu, tanımlayıcının hedefe bağlanan ada sahip bir diğer ad olduğunu gösterir `C` `System.Console` . Diğer bir deyişle, özellik Kılavuzu tanımlayıcıya karşılık gelen **diğerad simgesiyle** ilgili bilgiler sağlar `C` .

![Diğerad sembol özellikleri](media/syntax-visualizer/alias-symbol.png)

Her türlü tanımlanmış türe, yönteme ve özelliğe karşılık gelen sembolü inceleyin. Görselleştirici içinde karşılık gelen düğümü seçin ve **Görünüm simgesine (varsa)** tıklayın. Yöntemin `Sub Main()` gövdesi dahil olmak üzere yöntemini seçin. Görselleştirici içindeki karşılık gelen **alt blok** düğümü Için **Görünüm simgesine (varsa)** tıklayın. Özellik Kılavuzu, bu **alt blok** Için **methodsymbol** 'ın `Main` dönüş türü olan ada sahip olduğunu gösterir `Void` .

![Yöntem bildirimi için simge görüntüleme](media/syntax-visualizer/method-symbol.png)

Yukarıdaki Visual Basic örnekleri C# dilinde kolayca çoğaltılabilir. `using C = System.Console;` `Imports C = System.Console` Diğer ad için yerine yazın. C# ' deki önceki adımlar, Görselleştirici penceresinde özdeş sonuçlar elde ediyor.

Anlamsal İnceleme işlemleri yalnızca düğümlerde kullanılabilir. Belirteçler veya trivia üzerinde kullanılamaz. Tüm düğümlerin incelemeye yönelik ilginç anlam bilgileri yoktur. Bir düğüm ilginç anlam bilgisine sahip olmadığında **Görünüm \* simgesine (varsa)** tıkladığınızda boş bir özellik ızgarası gösterilir.

[Semantiğe](work-with-semantics.md) genel bakış belgesinde semantik analizler gerçekleştirmek Için API 'ler hakkında daha fazla bilgi edinebilirsiniz.

## <a name="closing-the-syntax-visualizer"></a>Sözdizimi Görselleştiricisini kapatma

Kaynak kodu incelemek için kullanmıyorsanız Görselleştirici penceresini kapatabilirsiniz. Sözdizimi görselleştiricisi, kod içinde gezinerek, kaynak düzenlenirken ve değiştirirken görüntüsünü günceller. Bu, kullanmadığınız durumlarda dikkat dağıtıcı alabilir.
