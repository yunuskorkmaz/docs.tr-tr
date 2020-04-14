---
title: 'Öğretici: Iris çiçek kategorize - k-kümeleme anlamına gelir'
description: kümeleme senaryosunda ML.NET nasıl kullanılacağını öğrenin
author: pkulikov
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 03ce1a5f3ef4d4da01f848cac0c520a5a6aaf4bf
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242796"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Öğretici: ML.NET ile k-araçları kümeleme kullanarak iris çiçekler kategorize

Bu öğretici, [iris çiçek veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set)için bir [kümeleme modeli](../resources/tasks.md#clustering) oluşturmak için ML.NET nasıl kullanılacağını göstermektedir.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> - Sorunu anlama
> - Uygun makine öğrenimi görevini seçin
> - Verileri hazırlama
> - Verileri yükleme ve dönüştürme
> - Bir öğrenme algoritması seçin
> - Modeli eğitme
> - Öngörüler için modeli kullanma

## <a name="prerequisites"></a>Ön koşullar

- [Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.

## <a name="understand-the-problem"></a>Sorunu anlama

Bu sorun, çiçek özelliklerine göre farklı gruplarhalinde iris çiçek kümesi bölen ilgilidir. Bu özellikler bir sepal uzunluğu ve genişliği ve bir taç yaprağı uzunluğu ve genişliği vardır. Bu öğretici için, her çiçeğin türü bilinmiyor varsayalım. Özelliklerden bir veri kümesinin yapısını öğrenmek ve bir veri örneğinin bu yapıya nasıl uyduğunu tahmin etmek istiyorsunuz.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Her çiçeğin hangi gruba ait olduğunu bilmediğiniz için [denetimsiz makine öğrenimi](../resources/glossary.md#unsupervised-machine-learning) görevini seçersiniz. Bir veri kümesini, aynı gruptaki öğelerin diğer gruplardakiöğelere göre birbirine daha çok benzer şekilde gruplara bölmek için, bir [kümeleme](../resources/tasks.md#clustering) makinesi öğrenme görevi kullanın.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Visual Studio'yu açın. Menü çubuğundan**Yeni** > **Proje** **Dosyası'nı** > seçin. Yeni **Proje** iletişim kutusunda, **.NET Core** düğümünü izleyen **Visual C#** düğümünü seçin. Ardından **Konsol Uygulaması (.NET Core)** proje şablonu'nu seçin. **Ad** metin kutusunda "IrisFlowerClustering" yazın ve **ardından Tamam** düğmesini seçin.

1. Veri kümesini ve model dosyalarını depolamak için projenizde *Veri* adlı bir dizin oluşturun:

    **Çözüm Gezgini'nde**projeyi sağ tıklatın ve**Yeni Klasör** **Ekle'yi** > seçin. "Veri" yazın ve Enter tuşuna basın.

1. **Microsoft.ML** NuGet paketini yükleyin:

    **Çözüm Gezgini'nde**projeyi sağ tıklatın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, **Gözat** sekmesini seçin, **Microsoft.ML** arayın ve **Yükle** düğmesini seçin. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.

## <a name="prepare-the-data"></a>Verileri hazırlama

1. [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) veri kümesini indirin ve önceki adımda oluşturduğunuz *Veri* klasörüne kaydedin. Iris veri kümesi hakkında daha fazla bilgi [için, iris çiçek veri seti](https://en.wikipedia.org/wiki/Iris_flower_data_set) Vikipedi sayfasına ve veri kümesinin kaynağı olan [Iris Veri Seti](http://archive.ics.uci.edu/ml/datasets/Iris) sayfasına bakın.

1. **Çözüm Gezgini'nde** *iris.data* dosyasına sağ tıklayın ve **Özellikler'i**seçin. **Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.

*iris.data* dosyası, aşağıdakileri temsil eden beş sütun içerir:

- santimetre sepal uzunluğu
- santimetre sepal genişliği
- santimetre yaprak uzunluğu
- santimetre yaprak genişliği
- iris çiçek türü

Kümeleme örneğinin hatırına, bu öğretici son sütunu yok sayar.

## <a name="create-data-classes"></a>Veri sınıfları oluşturma

Giriş verileri ve öngörüler için sınıflar oluşturun:

1. **Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.
1. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *IrisData.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.
1. Yeni dosyaya aşağıdaki `using` yönergeyi ekleyin:

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

Varolan sınıf tanımını kaldırın ve IrisData.cs dosyasına `IrisData` `ClusterPrediction`sınıfları *IrisData.cs* ve , tanımlayan aşağıdaki kodu ekleyin:

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

`IrisData`giriş veri sınıfıdır ve veri kümesinden her özellik için tanımlar vardır. Veri kümesi dosyasındaki kaynak sütunların dizinlerini belirtmek için [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) özniteliğini kullanın.

Sınıf, `ClusterPrediction` bir `IrisData` örne uygulanan kümeleme modelinin çıktısını temsil eder. Sütun [Adı](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğini kullanarak `PredictedClusterId` alanları `Distances` ve alanları **Sırasıyla PredictedLabel** ve **Score** sütunlarına bağlayın. Kümeleme görevi söz konusu olduğunda bu sütunlar aşağıdaki anlamlara sahiptir:

- **PredictedLabel** sütunu, tahmin edilen kümenin kimliğini içerir.
- **Puan** sütunu küme centroids kare Öklid mesafeleri olan bir dizi içerir. Dizi uzunluğu küme sayısına eşittir.

> [!NOTE]
> Giriş `float` ve tahmin veri sınıflarında kayan nokta değerlerini temsil etmek için türü kullanın.

## <a name="define-data-and-model-paths"></a>Veri ve model yollarını tanımlama

*Program.cs* dosyasına geri dön ve veri kümesi dosyasına ve modeli kaydetmek için dosyaya giden yolları tutmak için iki alan ekleyin:

- `_dataPath`modeli eğitmek için kullanılan veri kümesi ile dosyaya giden yolu içerir.
- `_modelPath`ilgili modelin depolandığı dosyaya giden yolu içerir.

Bu yolları belirtmek için `Main` yöntemin hemen üstüne aşağıdaki kodu ekleyin:

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

Önceki kodu derlemek *için, Program.cs* `using` dosyasının üst kısmında aşağıdaki yönergeleri ekleyin:

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>ML bağlamı oluşturma

Program.cs dosyasının `using` üst bölümüne aşağıdaki *Program.cs* ek yönergeleri ekleyin:

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

`Main` Yöntemde, satırı `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin:

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

Sınıf <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> makine öğrenimi ortamını temsil eder ve veri yükleme, model eğitimi, tahmin ve diğer görevler için günlük ve giriş noktaları için mekanizmalar sağlar. Bu, kavramsal olarak `DbContext` Varlık Çerçevesi'nde kullanmakla karşılaştırılabilir.

## <a name="set-up-data-loading"></a>Veri yüklemeyi ayarlama

Verileri yükleme yöntemini `Main` ayarlamak için yönteme aşağıdaki kodu ekleyin:

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

Genel [ `MLContext.Data.LoadFromTextFile` uzantı yöntemi,](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri kümesi şeasını `IrisData` sağlanan türden <xref:Microsoft.ML.IDataView> çıkarve transformatörler için girdi olarak kullanılabilecek döndürür.

## <a name="create-a-learning-pipeline"></a>Öğrenme ardışık bir yol oluşturma

Bu öğretici için, kümeleme görevinin öğrenme ardışık iki adımı oluşur:

- yüklenen sütunları kümeleme eğitmeni tarafından kullanılan tek bir **Özellikler** sütununa dönüştürün;
- k-means++ kümeleme algoritmasını kullanarak modeli eğitmek için bir <xref:Microsoft.ML.Trainers.KMeansTrainer> eğitmen kullanın.

`Main` yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

Kod, veri kümesinin üç kümeye bölünmesi gerektiğini belirtir.

## <a name="train-the-model"></a>Modeli eğitme

Önceki bölümlerde eklenen adımlar, boru hattını eğitime hazırladı, ancak hiçbiri yürütülmedi. Veri yükleme ve `Main` model eğitimini gerçekleştirmek için yönteme aşağıdaki satırı ekleyin:

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Modeli kaydetme

Bu noktada, varolan veya yeni .NET uygulamalarınızdan herhangi biri ile entegre edilebilen bir modele sahip siniz. Modelinizi bir .zip dosyasına kaydetmek için `Main` yönteme aşağıdaki kodu ekleyin:

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Öngörüler için modeli kullanma

Öngörülerde bulunmak için, <xref:Microsoft.ML.PredictionEngine%602> transformatör ardışık lığından giriş türü örneklerini alan ve çıkış türünün örneklerini üreten sınıfı kullanın. Bu sınıfın bir `Main` örneğini oluşturmak için yönteme aşağıdaki satırı ekleyin:

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir. Tek dişli veya prototip ortamlarda kullanılabilir. Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın. ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.

> [!NOTE]
> `PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.

Test `TestIrisData` veri örneklerini barındıracak sınıf oluşturun:

1. **Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.
1. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *TestIrisData.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.
1. Sınıfı aşağıdaki örnekte olduğu gibi statik olacak şekilde değiştirin:

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

Bu öğretici, bu sınıf içinde bir iris veri örneği tanıtır. Modelle deneme yapmak için başka senaryolar ekleyebilirsiniz. Sınıfa `TestIrisData` aşağıdaki kodu ekleyin:

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

Belirtilen öğenin ait olduğu kümeyi bulmak için *Program.cs* dosyasına geri dön ve `Main` yönteme aşağıdaki kodu ekleyin:

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

Hangi kümenin belirtilen veri örneğini ve bu örnekten küme merkezlerine kare uzaklıklar içerdiğini görmek için programı çalıştırın. Sonuçlarınız aşağıdakilere benzer olmalıdır:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Tebrikler! Şimdi başarıyla iris kümeleme için bir makine öğrenme modeli inşa ettik ve tahminler yapmak için kullanılır. Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Sorunu anlama
> - Uygun makine öğrenimi görevini seçin
> - Verileri hazırlama
> - Verileri yükleme ve dönüştürme
> - Bir öğrenme algoritması seçin
> - Modeli eğitme
> - Öngörüler için modeli kullanma

Öğrenmeye devam etmek ve daha fazla örnek bulmak için GitHub depomuza göz atın.
> [!div class="nextstepaction"]
> [dotnet/machinelearning GitHub deposu](https://github.com/dotnet/machinelearning/)
