---
title: Visual Studio 'da Roslyn sözdizimi görselleştiricisi ile kodu araştırma
description: Sözdizimi görselleştiricisi .NET Compiler Platform SDK 'nın kod için oluşturduğu modelleri araştırmak için görsel bir araç sağlar.
ms.date: 03/07/2018
ms.custom: mvc, vs-dotnet
ms.openlocfilehash: fa3b4fdbb8d573805119e13e8aa93f156c4111f9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972009"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Visual Studio 'da Roslyn sözdizimi görselleştiricisi ile kodu araştırma

Bu makalede, .NET Compiler Platform ("Roslyn") SDK 'sının bir parçası olarak gönderilen Syntax Visualizer aracına genel bakış sunulmaktadır. Syntax Visualizer, sözdizimi ağaçlarını incelemenize ve keşfetmenize yardımcı olan bir araç penceresidir. Analiz etmek istediğiniz kod modellerini anlamak için gerekli olan bir araçtır. Ayrıca, .NET Compiler Platform ("Roslyn") SDK 'sını kullanarak kendi uygulamalarınızı geliştirirken hata ayıklama yardımıdır. İlk çözümleyicinizi oluştururken bu aracı açın. Görselleştiricisi API 'Ler tarafından kullanılan modelleri anlamanıza yardımcı olur. Kod incelemek ve sözdizimi ağaçlarını anlamak için, [parça](https://sharplab.io) veya [linqpad](https://www.linqpad.net/) gibi araçları da kullanabilirsiniz.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

[Genel bakış](compiler-api-model.md) makalesini okuyarak .net Compiler Platform SDK 'sında kullanılan kavramları öğrenmeye çalışın. Sözdizimi ağaçları, düğümleri, belirteçleri ve trivia için bir giriş sağlar.

## <a name="syntax-visualizer"></a>Syntax Visualizer

**Syntax Visualizer** , VISUAL Studio IDE içindeki geçerli etkin düzenleyici PENCERESINDE C# veya vb kod dosyası için sözdizimi ağacının incelemesini mümkün. Görselleştirici,**diğer Windows** > **Syntax Visualizer** **görüntüle** > ' ye tıklanarak başlatılabilir.  Sağ üst köşedeki **Hızlı başlatma** araç çubuğunu da kullanabilirsiniz. "Sözdizimi" yazın ve **Syntax Visualizer** açmak için komut görünmelidir.

Bu komut Syntax Visualizer kayan bir araç penceresi olarak açar. Bir kod Düzenleyicisi penceresi açık değilse, aşağıdaki şekilde gösterildiği gibi görüntü boştur. 

![Syntax Visualizer araç penceresi](media/syntax-visualizer/syntax-visualizer.png)

Bu araç penceresini, Visual Studio içinde, sol taraftaki gibi uygun bir konuma yerleştirin. Görselleştirici, geçerli kod dosyası hakkındaki bilgileri gösterir.

**Dosya** > **Yeni proje** komutunu kullanarak yeni bir proje oluşturun. Bir VB veya C# proje oluşturabilirsiniz. Visual Studio bu proje için ana kod dosyasını açtığında Görselleştirici kendisi için sözdizimi ağacını görüntüler. Bu Visual Studio örneğinde var C# olan herhangi bir/vb dosyasını açabilirsiniz ve Görselleştirici bu dosyanın sözdizimi ağacını görüntüler. Visual Studio içinde açık olan birden çok kod dosyanız varsa, Görselleştirici geçerli etkin kod dosyası (klavye odağına sahip kod dosyası) için sözdizimi ağacını görüntüler.

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Bir C# sözdizimi ağacını görselleştirme](media/syntax-visualizer/visualize-csharp.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
![VB sözdizimi ağacını görselleştirme](media/syntax-visualizer/visualize-visual-basic.png)

---

Önceki görüntülerde gösterildiği gibi, Görselleştirici araç penceresi üstteki sözdizimi ağacını ve alt kısımdaki bir özellik kılavuzunu görüntüler. Özellik Kılavuzu, öğenin .NET *türü* ve *türü* (ağacın syntaxkind içeren) dahil olmak üzere ağaçta seçili olan öğenin özelliklerini görüntüler.

Sözdizimi ağaçları, *düğüm*, *belirteç*ve *bilgi*olmak üzere üç öğe türünü kapsar. [Söz dizimi Ile çalışma](work-with-syntax.md) makalesinde bu türler hakkında daha fazla bilgi edinebilirsiniz. Her türün öğeleri farklı bir renk kullanılarak temsil edilir. Kullanılan renklere genel bakış için ' gösterge ' düğmesine tıklayın.

Ağaçtaki her öğe ayrıca kendi **yayılma alanını**da görüntüler. **Yayılma** , metin dosyasındaki bu düğümün indekslerini (başlangıç ve bitiş konumu).  Yukarıdaki C# örnekte, seçili "usinganahtar sözcüğü [0.. 5)" belirtecinin, beş karakter genişliğinde, [0.. 5) bir **yayılımı** vardır. "[..)" Gösterimi Başlangıç dizininin yayılma alanının parçası olduğu, ancak bitiş dizininin olmadığı anlamına gelir.

Ağaçta gezinmek için iki yol vardır:

* Ağaçtaki öğeler ' i genişletin veya tıklayın. Görselleştirici, kod düzenleyicisinde bu öğenin alanına karşılık gelen metni otomatik olarak seçer.
* Kod düzenleyicisinde metin ' e tıklayın veya seçin. Önceki VB örneğinde, kod düzenleyicisinde "Module Module1" içeren satırı seçerseniz, görselleştiricisi otomatik olarak ağaçtaki karşılık gelen Moduledeyimdüğümüne gider. 

Görselleştirici, alanı düzenleyicide seçili olan metnin yayılımının en iyi şekilde eşleştiği ağaçtaki öğeyi vurgular.

Görselleştirici, etkin kod dosyasındaki değişikliklerle eşleşecek şekilde ağacı yeniler. `Console.WriteLine()` İçine`Main()`bir çağrı ekleyin. Siz yazarken, görselleştiricisi ağacı yeniler.

Yazdıktan sonra `Console.`yazmayı duraklatın. Ağaçta, pembe renkte renkli bazı öğeler vardır. Bu noktada, yazılan koddaki hatalar (' Tanılama ' olarak da bilinir) vardır. Bu hatalar, söz dizimi ağacındaki düğümlere, belirteçlere ve üçlü öğesine eklenir. Görselleştirici, arka planı pembe olarak vurgulamada hangi öğelerin ekli hatalara sahip olduğunu gösterir. Öğenin üzerine gelerek pembe renkte renklendirilmiş hataları inceleyebilirsiniz. Görselleştirici yalnızca sözdizimsel hataları (yazılan kodun sözdizimiyle ilgili hatalar) görüntüler; hiçbir semantik hata görüntülemez.
 
## <a name="syntax-graphs"></a>Sözdizimi grafikleri

Ağaçtaki herhangi bir öğeye sağ tıklayın ve **yönlendirilmiş sözdizimi grafiğini görüntüle**' ye tıklayın. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Görselleştirici, seçili öğede kökü belirtilen alt ağacın grafik temsilini görüntüler. C# Örnekteki `Main()` yönteme karşılık gelen **MethodDeclaration** düğümü için aşağıdaki adımları deneyin. Görselleştiricisi aşağıdaki gibi görünen bir sözdizimi grafiği görüntüler:

![Bir C# sözdizimi grafiğini görüntüleme](media/syntax-visualizer/csharp-syntax-graph.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

Önceki vb örneğinde `Main()` yöntemine karşılık gelen **alt blok** düğümü için aynısını deneyin. Görselleştiricisi aşağıdaki gibi görünen bir sözdizimi grafiği görüntüler:

![VB sözdizimi grafiğini görüntüleme](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Söz dizimi grafik görüntüleyicisinde gösterge renklendirme şeması görüntüleme seçeneği vardır. Ayrıca söz konusu öğeye karşılık gelen özellikleri görüntülemek için, söz dizimi grafiğinde tek tek öğelerin üzerine gelin.

Ağaçtaki farklı öğeler için sözdizimi grafiklerini art arda görüntüleyebilirsiniz ve grafikler her zaman Visual Studio içindeki aynı pencerede görüntülenir. Bu pencereyi Visual Studio içinde uygun bir konuma yerleştirebilirsiniz, böylece yeni bir sözdizimi grafiğini görüntülemek için sekmeler arasında geçiş yapmanız gerekmez. En alttaki kod Düzenleyicisi pencereleri, genellikle kullanışlıdır.

Görselleştiricisi araç penceresi ve söz dizimi grafik penceresi ile kullanılacak yerleştirme düzeni aşağıda verilmiştir:

![Görselleştirici ve söz dizimi grafik penceresi için bir yerleştirme düzeni](media/syntax-visualizer/docking-layout.png)

Diğer bir seçenek de, sözdizimi grafik penceresini ikinci bir monitöre bir çift izleyici kurulumuna koyulamıyor.

## <a name="inspecting-semantics"></a>Semantiğini İnceleme

Syntax Visualizer, sembolleri ve anlam bilgilerini ilkel denetlemesini mümkün. Örnekteki Main () içine yazın `double x = 1 + 1;`. C# Ardından, kod Düzenleyicisi penceresinde `1 + 1` ifadeyi seçin. Görselleştirici, görselleştiricide **AddExpression** düğümünü vurgular. Bu **AddExpression** öğesine sağ tıklayın ve **Görünüm simgesine (varsa)** tıklayın. Menü öğelerinin çoğunda "varsa" niteleyicisi olduğuna dikkat edin. Syntax Visualizer, tüm düğümler için mevcut olmayan özellikler de dahil olmak üzere bir düğümün özelliklerini inceler. 

Aşağıdaki şekilde gösterildiği gibi görselleştiricisi güncelleştirmelerinde Özellik Kılavuzu: İfade sembolü, **Kind = yöntemi**Içeren bir **SynthesizedIntrinsicOperatorSymbol** .

![Sembol özellikleri](media/syntax-visualizer/symbol-properties.png)

Aynı **AddExpression** düğümü için **TypeSymbol (varsa) görüntülemeyi** deneyin. Aşağıdaki şekilde gösterildiği gibi, Görselleştirici güncelleştirmelerinde bulunan Özellik Kılavuzu, seçili ifadenin `Int32`türünün olduğunu gösterir.

![TypeSymbol özellikleri](media/syntax-visualizer/type-symbol-properties.png)

Aynı **AddExpression** düğümü Için **dönüştürülmüş TypeSymbol (varsa) görüntülemeyi** deneyin. Özellik Kılavuzu, ifadenin `Int32`türü olsa da, `Double` ifadenin dönüştürülmüş türünün Aşağıdaki şekilde gösterildiği gibi olduğunu gösterir. Bu düğüm, dönüştürülmüş tür sembol bilgisini içerir, `Int32` çünkü ifade, `Double`öğesine dönüştürülmesi gereken bir bağlamda meydana gelir. Bu dönüştürme, atama `Double` işlecinin sol tarafındaki değişken `x` için belirtilen türü karşılar.

![Dönüştürülen TypeSymbol özellikleri](media/syntax-visualizer/converted-type-symbol-properties.png)

Son olarak, aynı **AddExpression** düğümü Için **sabit değeri (varsa) görüntülemeyi** deneyin. Özellik Kılavuzu, ifadenin değerinin değeri `2`olan bir derleme zamanı sabiti olduğunu gösterir.

![Sabit değer](media/syntax-visualizer/constant-value.png)

Yukarıdaki örnek VB 'de de çoğaltılabilir. Bir `Dim x As Double = 1 + 1` vb dosyası yazın. Kod Düzenleyicisi penceresinde `1 + 1` ifadeyi seçin. Görselleştirici, görselleştiricide karşılık gelen **AddExpression** düğümünü vurgular. Bu **AddExpression** için önceki adımları tekrarlayın ve özdeş sonuçlar görmeniz gerekir.

VB 'de daha fazla kod inceleyin. Ana VB dosyanızı aşağıdaki kodla güncelleştirin:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Bu kod, dosyanın en üstünde `C` bulunan türle `System.Console` eşleşen adlı bir diğer ad tanıtır ve bu diğer adı içinde `Main()`kullanır. `C` `Main()` İçindeki Budiğeradınkullanımını,yöntemiiçindeseçin`C.WriteLine()`. Görselleştiricisi görselleştiricide karşılık gelen **IdentifierName** düğümünü seçer. Bu düğüme sağ tıklayın ve **Görünüm simgesine (varsa)** tıklayın. Özellik Kılavuzu, Bu tanımlayıcının aşağıdaki şekilde gösterildiği gibi türe `System.Console` bağlandığını gösterir:

![Sembol özellikleri](media/syntax-visualizer/symbol-visual-basic.png)

Aynı **IdentifierName** düğümü için **bir diğer simge (varsa) görüntülemeyi** deneyin. Özellik Kılavuzu, tanımlayıcının `C` `System.Console` hedefe bağlanan ada sahip bir diğer ad olduğunu gösterir. Diğer bir deyişle, özellik Kılavuzu tanımlayıcıya `C`karşılık gelen **diğerad simgesiyle** ilgili bilgiler sağlar.

![Diğerad sembol özellikleri](media/syntax-visualizer/alias-symbol.png)

Her türlü tanımlanmış türe, yönteme ve özelliğe karşılık gelen sembolü inceleyin. Görselleştirici içinde karşılık gelen düğümü seçin ve **Görünüm simgesine (varsa)** tıklayın. Yöntemin gövdesi dahil `Sub Main()`olmak üzere yöntemini seçin. Görselleştirici içindeki karşılık gelen **alt blok** düğümü Için **Görünüm simgesine (varsa)** tıklayın. Özellik Kılavuzu, bu **alt blok** için **methodsymbol** 'ın dönüş türü `Void`olan `Main` ada sahip olduğunu gösterir.

![Yöntem bildirimi için simge görüntüleme](media/syntax-visualizer/method-symbol.png)

Yukarıdaki VB örnekleri ' de C#kolayca çoğaltılabilir. Diğer ad `using C = System.Console;`içinyerineyazın `Imports C = System.Console` . Yukarıdaki adımlar, Görselleştirici penceresinde özdeş sonuçlar elde ediyor C# .

Anlamsal İnceleme işlemleri yalnızca düğümlerde kullanılabilir. Belirteçler veya trivia üzerinde kullanılamaz. Tüm düğümlerin incelemeye yönelik ilginç anlam bilgileri yoktur. Bir düğüm ilginç anlam bilgisine sahip olmadığında **Görünüm \* simgesine (varsa)** tıkladığınızda boş bir özellik ızgarası gösterilir.

[Semantiğe](work-with-semantics.md) genel bakış belgesinde semantik analizler gerçekleştirmek Için API 'ler hakkında daha fazla bilgi edinebilirsiniz.

## <a name="closing-the-syntax-visualizer"></a>Sözdizimi Görselleştiricisini kapatma

Kaynak kodu incelemek için kullanmıyorsanız Görselleştirici penceresini kapatabilirsiniz. Sözdizimi görselleştiricisi, kod içinde gezinerek, kaynak düzenlenirken ve değiştirirken görüntüsünü günceller. Bu, kullanmadığınız durumlarda dikkat dağıtıcı alabilir. 
