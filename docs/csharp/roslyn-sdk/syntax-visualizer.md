---
title: Visual Studio'da Roslyn sözdizimi görselleştiricisi ile kodu keşfedin
description: Sözdizimi görselleştiricisi, .NET Derleyici Platformu SDK'nın kod için oluşturduğu modelleri keşfetmek için görsel bir araç sağlar.
ms.date: 03/07/2018
ms.custom: mvc, vs-dotnet
ms.openlocfilehash: 27e5a1f0b31dd2af2ac779223538b03cdb4db0c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156993"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Visual Studio'da Roslyn sözdizimi görselleştiricisi ile kodu keşfedin

Bu makalede, .NET Derleyici Platformu ("Roslyn") SDK'nın bir parçası olarak gönderen Sözdizimi Görselleştirici aracına genel bir bakış sağlanmaktadır. Sözdizimi Görselleştiricisi, sözdizimi ağaçlarını incelemenize ve keşfetmenize yardımcı olan bir araç penceresidir. Çözümlemek istediğiniz kod modellerini anlamak için önemli bir araçtır. .NET Derleyici Platformu ("Roslyn") SDK'yı kullanarak kendi uygulamalarınızı geliştirdiğinizde de hata ayıklama yardımı olur. İlk çözümleyicilerinizi oluştururken bu aracı açın. Görselleştirici, API'ler tarafından kullanılan modelleri anlamanıza yardımcı olur. Kodu incelemek ve sözdizimi ağaçlarını anlamak için [SharpLab](https://sharplab.io) veya [LINQPad](https://www.linqpad.net/) gibi araçları da kullanabilirsiniz.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Genel [bakış](compiler-api-model.md) makalesini okuyarak .NET Derleyici Platformu SDK'da kullanılan kavramları yakından tanıtın. Sözdizimi ağaçları, düğümler, belirteçler ve ıvır zıvır için bir giriş sağlar.

## <a name="syntax-visualizer"></a>Sözdizimi Görselleştiricisi

**Sözdizimi Görselleştiricisi,** Visual Studio IDE'nin içindeki geçerli etkin düzenleyici penceresinde C# veya Visual Basic kod dosyası için sözdizimi ağacının incelenmesini sağlar. **Görselleştirici, Diğer Windows** > **Sözdizimini Görselleştiricisini** **Görüntüle'ye** > tıklayarak başlatılabilir.  Sağ üst köşedeki **Hızlı Başlatma** araç çubuğunu da kullanabilirsiniz. "Sözdizimi" yazın ve **Sözdizimi Görselleştiricisini** açmak için komut görünmelidir.

Bu komut, Sözdizimi Görselleştiricisini kayan bir araç penceresi olarak açar. Açık bir kod düzenleyicipencereniz yoksa, aşağıdaki şekilde gösterildiği gibi ekran boştur.

![Sözdizimi Görselleştirici araç penceresi](media/syntax-visualizer/syntax-visualizer.png)

Bu araç penceresini Visual Studio'nun sol tarafı gibi uygun bir konuma sabitle. Visualizer geçerli kod dosyası yla ilgili bilgileri gösterir.

**Yeni Dosya Komutunu** > **New Project** kullanarak yeni bir proje oluşturun. Visual Basic veya C# projesi oluşturabilirsiniz. Visual Studio bu projenin ana kod dosyasını açtığında, görselleştirici bunun için sözdizimi ağacını görüntüler. Bu Visual Studio örneğinde varolan herhangi bir C# / Visual Basic dosyasını açabilirsiniz ve görselleştirici bu dosyanın sözdizimi ağacını görüntüler. Visual Studio'da birden çok kod dosyanız açıksa, görselleştirici şu anda etkin olan kod dosyasının sözdizimi ağacını (klavye odağı olan kod dosyası) görüntüler.

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)
![C# sözdizimi ağacını görselleştirme](media/syntax-visualizer/visualize-csharp.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)
![Visual Basic sözdizimi ağacını görselleştirme](media/syntax-visualizer/visualize-visual-basic.png)

---

Önceki resimlerde gösterildiği gibi, görselleştirici araç penceresi üstteki sözdizimi ağacını ve alttaki özellik ızgarasını görüntüler. Özellik ızgarası, .NET *Türü* ve maddenin *Türü* (Sözdizimi) de dahil olmak üzere ağaçta şu anda seçili olan öğenin özelliklerini görüntüler.

Sözdizimi ağaçları üç tür öğeden oluşur – *düğümler,* *belirteçler*ve *ıvır zıvır.* [Sözdizimi](work-with-syntax.md) makalesi ile Work'te bu türler hakkında daha fazla bilgi edinebilirsiniz. Her türdeki öğeler farklı bir renk kullanılarak temsil edilir. Kullanılan renklere genel bakış için 'Gösterge' düğmesine tıklayın.

Ağaçtaki her öğe de kendi **açıklığını**görüntüler. **Açıklık,** metin dosyasındaki düğümün endeksleridir (başlangıç ve bitiş konumu).  Önceki C# örneğinde, seçili "Anahtar Kelime Kullanma [0..5)" belirteci beş karakter genişliğinde bir **Yayılma Alanı** vardır, [0.5). "[..)" gösterimi, başlangıç dizininin açıklının bir parçası olduğu, ancak bitiş dizininin olmadığı anlamına gelir.

Ağaçta gezinmenin iki yolu vardır:

* Ağaçtaki öğeleri genişletin veya tıklatın. Görselleştirici, kod düzenleyicisinde bu öğenin yayılma süresine karşılık gelen metni otomatik olarak seçer.
* Kod düzenleyicisindeki metni tıklatın veya seçin. Önceki Visual Basic örneğinde, kod düzenleyicisinde "Modül Modülü1" içeren satırı seçerseniz, görselleştirici otomatik olarak ağaçtaki ilgili ModuleStatement düğümüne yönlendirilir.

Görselleştirici, açıklığı düzenleyicide seçilen metnin açıklığıyla en iyi eşleşen ağaçtaki öğeyi vurgular.

Görselleştirici, etkin kod dosyasındaki değişiklikleri eşleştirmek için ağacı yeniler. İçeriye `Console.WriteLine()` `Main()`bir çağrı ekleyin. Siz yazarken, görselleştirici ağacı yeniler.

Yazdıktan sonra yazmayı `Console.`duraklatın. Ağaç pembe renkli bazı öğeleri vardır. Bu noktada, yazılan kodda hatalar ('Tanılama' olarak da adlandırılır) vardır. Bu hatalar sözdizimi ağacındaki düğümlere, belirteçlere ve ıvır zıvıra eklenir. Görselleştirici, arka planı pembe yle vurgulayan öğelerin hangiöğelere eklenmiş olduğunu gösterir. Pembe renkli herhangi bir öğedeki hataları, öğenin üzerinde gezinerek inceleyebilirsiniz. Görselleştirici yalnızca sözdizimhataları (türüyazılan kodun sözdizimiyle ilgili hatalar) görüntüler; herhangi bir anlamsal hata görüntülemez.

## <a name="syntax-graphs"></a>Sözdizimi Grafikleri

Ağaçtaki herhangi bir öğeye sağ tıklayın ve **Yönlendirilen Sözdizimini Görüntüle Grafiği'ni görüntüle'ye**tıklayın.

# <a name="c"></a>[C #](#tab/csharp)

Görselleştirici, seçili öğede köksünün alt ağacının grafiksel bir gösterimini görüntüler. C# örneğindeki `Main()` **yönteme** karşılık gelen Yöntem Bildirimi düğümü için aşağıdaki adımları deneyin. Görselleştirici aşağıdaki gibi görünen bir sözdizimi grafiği görüntüler:

![C# sözdizimi grafiğini görüntüleme](media/syntax-visualizer/csharp-syntax-graph.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

Önceki Visual Basic **SubBlock** örneğinde `Main()` yönteme karşılık gelen Alt Blok düğümü için de aynısını deneyin. Görselleştirici aşağıdaki gibi görünen bir sözdizimi grafiği görüntüler:

![Visual Basic sözdizimi grafiğini görüntüleme](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Sözdizimi grafik görüntüleyici, bir göstergenin boyama düzenini görüntüleme seçeneğine sahiptir. Sözdizimi grafiğindeki tek tek öğelerin üzerine fareyle birlikte sözdizimine karşılık gelen özellikleri görüntüleyebilirsiniz.

Ağaçtaki farklı öğelerin sözdizimi grafiklerini art arda görüntüleyebilirsiniz ve grafikler her zaman Visual Studio'nun içindeki aynı pencerede görüntülenir. Yeni bir sözdizimi grafiğini görüntülemek için sekmeler arasında geçiş yapmak zorunda kalmamak için bu pencereyi Visual Studio'da uygun bir konuma sabitleyebilirsiniz. Alt, kod düzenleyicisi pencerelerin altında, genellikle uygundur.

Visualizer araç penceresi ve sözdizimi grafik penceresi ile kullanılacak yerleştirme düzeni aşağıda veda edebilirsiniz:

![Görselleştirici ve sözdizimi grafik penceresi için bir yerleştirme düzeni](media/syntax-visualizer/docking-layout.png)

Başka bir seçenek, sözdizimi grafik penceresini ikinci bir monitöre, çift monitör kurulumuna koymaktır.

## <a name="inspecting-semantics"></a>Semantik inceleme

Sözdizimi Görselleştiricisi sembollerin ve anlamsal bilgilerin temel olarak incelenmesini sağlar. C# örneğinde Main() içinde yazın. `double x = 1 + 1;` Ardından, kod `1 + 1` düzenleyicisi penceresindeki ifadeyi seçin. Görselleştirici, visualizer'daki **AddExpression** düğümlerini vurgular. Bu **AddExpression'a** sağ tıklayın ve **Görünüm Simgesi'ne (varsa)** tıklayın. Menü öğelerinin çoğunun "varsa" niteleyicisi olduğuna dikkat edin. Sözdizimi Görselleştiricisi, tüm düğümler için bulunamayan özellikler de dahil olmak üzere düğümün özelliklerini denetler.

Aşağıdaki şekilde gösterildiği gibi görselleştirici güncelleştirmeleri özellik ızgarası: Ifade sembolü **Kind = Yöntemi**ile **SynthesizedIntrinsicOperatorSymbol** olduğunu.

![Sembol özellikleri](media/syntax-visualizer/symbol-properties.png)

Aynı **AddExpression** düğümü için **TypeSymbol'ı (varsa) görünüm** dene. Aşağıdaki şekilde gösterildiği gibi görselleştirici güncelleştirmeleri özellik ızgara, seçili ifade türü `Int32`olduğunu belirten .

![TypeSymbol özellikleri](media/syntax-visualizer/type-symbol-properties.png)

Aynı **AddExpression** düğümü için **Dönüştürülmüş TypeSymbol'ı (varsa)** görüntüleyin'i deneyin. Özellik ızgarası, ifadenin türü olmasına `Int32`rağmen, ifadenin dönüştürülmüş türünün `Double` aşağıdaki şekilde gösterildiği gibi olduğunu belirten güncelleştirmelerdir. İfade bir `Int32` `Double`. dönüştürülmesi gereken bir bağlamda oluşur, çünkü bu düğüm dönüştürülmüş tür sembolü bilgileri içerir Bu dönüştürme, atama işlecinin `Double` sol `x` tarafındaki değişken için belirtilen türü karşılar.

![Dönüştürülmüş TypeSymbol özellikleri](media/syntax-visualizer/converted-type-symbol-properties.png)

Son olarak, aynı **AddExpression** düğümü için **Sabit Değeri Görüntüle'yi (varsa)** deneyin. Özellik ızgarası, ifadenin değerinin değeri `2`olan bir derleme zaman sabiti olduğunu gösterir.

![Sabit bir değer](media/syntax-visualizer/constant-value.png)

Önceki örnek Visual Basic'te de çoğaltılabilir. Visual `Dim x As Double = 1 + 1` Basic dosyasini yazın. Kod düzenleyicisi penceresindeki ifadeyi `1 + 1` seçin. Görselleştirici, visualizer'daki ilgili **AddExpression** düğümlerini vurgular. Bu **AddExpression** için önceki adımları yineleyin ve aynı sonuçları görmeniz gerekir.

Visual Basic'te daha fazla kodu inceleyin. Ana Visual Basic dosyanızı aşağıdaki kodla güncelleyin:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Bu kod, dosyanın `C` üst kısmındaki `System.Console` türle eşleyen ve bu diğer `Main()`adı içinde kullanan bir takma ad tanılar. Bu diğer adın kullanımını `C` seçin, `C.WriteLine()`in `Main()` , yöntemin içinde. Görselleştirici, visualizer'daki ilgili **TanımlayıcıName** düğümünü seçer. Bu düğüme sağ tıklayın ve **Görünüm Simgesi'ne tıklayın (varsa)**. Özellik ızgarası, bu tanımlayıcının aşağıdaki şekilde gösterildiği `System.Console` gibi türe bağlı olduğunu gösterir:

![Sembol özellikleri](media/syntax-visualizer/symbol-visual-basic.png)

Aynı **IdentifierName** düğümü için **AliasSymbol'u (varsa)** görüntüleyin'i deneyin. Özellik ızgarası, tanımlayıcının `C` `System.Console` hedefe bağlı adı olan bir diğer ad olduğunu gösterir. Başka bir deyişle, özellik ızgarası tanımlayıcıya karşılık gelen **AliasSymbol** `C`ile ilgili bilgiler sağlar.

![AliasSymbol özellikleri](media/syntax-visualizer/alias-symbol.png)

Beyan edilen herhangi bir türe, yönteme, özelliğe karşılık gelen sembolü inceleyin. Görselleştiricideki karşılık gelen düğümü seçin ve **Görünüm Simgesi'ni (varsa)** tıklatın. Yöntemin `Sub Main()`gövdesi de dahil olmak üzere yöntemi seçin. Görselleştiricideki ilgili **Alt Blok** düğümü için Görünüm Simgesi'ni **(varsa)** tıklatın. Özellik ızgarası, bu **Alt Blok** için `Main` `Void` **MethodSymbol'un** iade türüne sahip adı olduğunu gösterir.

![Yöntem bildirimi için görüntüleme simgesi](media/syntax-visualizer/method-symbol.png)

Yukarıdaki Visual Basic örnekleri C# ile kolayca çoğaltılabilir. Takma `using C = System.Console;` ad `Imports C = System.Console` yerine yazın. C#'daki önceki adımlar görselleştirici penceresinde aynı sonuçları verir.

Anlamsal denetim işlemleri sadece düğümlerde mevcuttur. Jeton veya ıvır zıvır da mevcut değildir. Tüm düğümleri incelemek için ilginç semantik bilgiler var. Bir düğümün ilginç anlamsal bilgileri yoksa, **Görünüm \* Simgesi'ni tıklattığınızda (varsa)** boş bir özellik ızgarası gösterilir.

Semantik genel bakış [belgesiyle Work'te](work-with-semantics.md) anlamsal analiz yapmak için API'ler hakkında daha fazla bilgi edinebilirsiniz.

## <a name="closing-the-syntax-visualizer"></a>Sözdizimi görselleştiricisini kapatma

Kaynak kodu incelemek için kullanmadığınızda görselleştirici pencereyi kapatabilirsiniz. Sözdizimi görselleştiricisi, kod, düzenleme ve kaynak değiştirme arasında gezinirken ekranını güncelleştirir. Kullanmadığınız zaman dikkat dağıtıcı olabilir.
