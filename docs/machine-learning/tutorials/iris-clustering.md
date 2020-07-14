---
title: 'Öğretici: Iris çiçekleri kategorilere ayır-k-bir kümeleme'
description: Kümeleme senaryosunda ML.NET kullanmayı öğrenin
author: pkulikov
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 8ee8b177dc9cc89c4f54956b8c0a274b1d093ece
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282092"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Öğretici: Iris çiçekler 'i k-ML.NET Kümelemesi kullanarak kategorilere ayırın

Bu öğreticide, [Iris çiçek veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set)için bir [kümeleme modeli](../resources/tasks.md#clustering) oluşturmak üzere ml.net 'in nasıl kullanılacağı gösterilmektedir.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:
> [!div class="checklist"]
>
> - Sorunu anlama
> - Uygun makine öğrenimi görevini seçin
> - Verileri hazırlama
> - Verileri yükleme ve dönüştürme
> - Bir öğrenme algoritması seçin
> - Modeli eğitme
> - Tahmin için modeli kullanma

## <a name="prerequisites"></a>Ön koşullar

- [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya üzeri ya da visual Studio 2017 sürüm 15,6 veya üzeri, ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="understand-the-problem"></a>Sorunu anlama

Bu sorun, bir Iris çiçekler kümesini, çiçek özelliklerine göre farklı gruplarda bölmek için kullanılır. Bu özellikler, bir sepal 'ın uzunluğu ve genişliği ve Petal 'ın uzunluğu ve genişliği. Bu öğretici için, her çiçek türünün bilinmediğini varsayın. Özelliklerden bir veri kümesinin yapısını öğrenmek ve bir veri örneğinin bu yapıya nasıl uyduğunu tahmin etmek istiyorsunuz.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Her bir çiçek 'nin hangi gruba ait olduğunu bilmiyorsanız, denetimli [makine öğrenimi](../resources/glossary.md#unsupervised-machine-learning) görevini seçersiniz. Gruplardaki bir veri kümesini, aynı gruptaki öğelerin diğer gruplardaki diğer gruplardan birbirlerine benzer şekilde bölmek için, bir [kümeleme](../resources/tasks.md#clustering) Machine Learning görevi kullanın.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Visual Studio'yu açın. Menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje** ' yi seçin. **Yeni proje** iletişim kutusunda, **Visual C#** düğümünü ve ardından **.NET Core** düğümünü seçin. Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin. **Ad** metin kutusuna "ırisflowerkümeleme" yazın ve **Tamam** düğmesini seçin.

1. Veri kümesi ve model dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun:

    **Çözüm Gezgini**, projeye sağ tıklayın ve **Add**  >  **Yeni klasör**Ekle ' yi seçin. "Data" yazın ve ENTER tuşuna basın.

1. **Microsoft.ml** NuGet paketini yükler:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    **Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, **Gözden** geçirme sekmesini seçin, **Microsoft.ml** araması yapın ve **yüklemeyi** seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.

## <a name="prepare-the-data"></a>Verileri hazırlama

1. [Iris. Data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) veri kümesini indirin ve önceki adımda oluşturduğunuz *veri* klasörüne kaydedin. Iris veri kümesi hakkında daha fazla bilgi için, veri kümesinin kaynağı olan [Iris çiçek veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set) vikipi sayfasında ve [Iris veri kümesi](http://archive.ics.uci.edu/ml/datasets/Iris) sayfasına bakın.

1. **Çözüm Gezgini**, *Iris. Data* dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

*Iris. Data* dosyası, şunları temsil eden beş sütun içerir:

- santimetre cinsinden sepal uzunluğu
- santimetre cinsinden sepal genişliği
- santimetre cinsinden Petal uzunluğu
- Genişlik cinsinden Petal genişliği
- Iris çiçek türü

Kümeleme örneği için bu öğretici son sütunu yoksayar.

## <a name="create-data-classes"></a>Veri sınıfları oluşturma

Giriş verileri ve tahminleri için sınıflar oluşturun:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *IrisData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.
1. Aşağıdaki `using` yönergeyi yeni dosyaya ekleyin:

   [!code-csharp[Add necessary usings](./snippets/iris-clustering/csharp/IrisData.cs#Usings)]

Mevcut sınıf tanımını kaldırın ve sınıfları `IrisData` ve `ClusterPrediction` *IrisData.cs* dosyasını tanımlayan aşağıdaki kodu ekleyin:

[!code-csharp[Define data classes](./snippets/iris-clustering/csharp/IrisData.cs#ClassDefinitions)]

`IrisData`, giriş veri sınıfıdır ve veri kümesindeki her bir özellik için tanımlar içerir. Veri kümesi dosyasındaki kaynak sütunlarının dizinlerini belirtmek için [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute) özniteliğini kullanın.

`ClusterPrediction`Sınıfı, bir örneğe uygulanan kümeleme modelinin çıkışını temsil eder `IrisData` . Ve alanlarını tahmine Tedlabel öğesine bağlamak için [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğini kullanın `PredictedClusterId` `Distances` ve **PredictedLabel** sütunları sırasıyla **puan** yapın. Kümeleme görevi söz konusu sütunlarda aşağıdaki anlamı vardır:

- **Predictedlabel** sütunu, tahmin EDILEN kümenin kimliğini içerir.
- **Puan** sütunu, kare Içinde Euclidea uzaklıkları küme centroıd 'leri için olan bir dizi içeriyor. Dizi uzunluğu, küme sayısına eşittir.

> [!NOTE]
> `float`Giriş ve tahmin veri sınıflarında kayan nokta değerlerini göstermek için türünü kullanın.

## <a name="define-data-and-model-paths"></a>Veri ve model yollarını tanımlama

*Program.cs* dosyasına dönün ve veri kümesi dosyasına ve modelin kaydedileceği dosyanın yollarını barındıracak iki alan ekleyin:

- `_dataPath`modeli eğitmek için kullanılan veri kümesiyle dosyanın yolunu içerir.
- `_modelPath`eğitilen modelin depolandığı dosyanın yolunu içerir.

Aşağıdaki kodu, `Main` Bu yolları belirtmek için yöntemine hemen ekleyin:

[!code-csharp[Initialize paths](./snippets/iris-clustering/csharp/Program.cs#Paths)]

Önceki kodu derlemek için, `using` *program.cs* dosyasının en üstüne aşağıdaki yönergeleri ekleyin:

[!code-csharp[Add usings for paths](./snippets/iris-clustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>ML bağlamı oluştur

`using` *Program.cs* dosyasının en üstüne aşağıdaki ek yönergeleri ekleyin:

[!code-csharp[Add Microsoft.ML usings](./snippets/iris-clustering/csharp/Program.cs#MLUsings)]

`Main`Yönteminde `Console.WriteLine("Hello World!");` satırını aşağıdaki kodla değiştirin:

[!code-csharp[Create ML context](./snippets/iris-clustering/csharp/Program.cs#CreateContext)]

<xref:Microsoft.ML.MLContext?displayProperty=nameWithType>Sınıfı, Machine Learning ortamını temsil eder ve veri yükleme, model eğitimi, tahmin ve diğer görevler için günlüğe kaydetme ve giriş noktaları için mekanizmalar sağlar. Bu, kavramsal olarak `DbContext` Entity Framework ' de kullanılmasına benzer.

## <a name="set-up-data-loading"></a>Veri yüklemeyi ayarlama

Aşağıdaki kodu `Main` yöntemine ekleyerek verileri yükleme yolunu ayarlayın:

[!code-csharp[Create text loader](./snippets/iris-clustering/csharp/Program.cs#CreateDataView)]

Genel [ `MLContext.Data.LoadFromTextFile` genişletme yöntemi](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri kümesi şemasını belirtilen `IrisData` tür ve döndürmektedir <xref:Microsoft.ML.IDataView> . Bu, dönüştürücüler için giriş olarak kullanılabilir.

## <a name="create-a-learning-pipeline"></a>Öğrenme işlem hattı oluşturma

Bu öğreticide, kümeleme görevinin öğrenme işlem hattı aşağıdaki iki adımdan oluşur:

- yüklenen sütunları bir kümeleme işlemi tarafından kullanılan tek bir **Özellikler** sütununa birleştirme;
- <xref:Microsoft.ML.Trainers.KMeansTrainer>k-ortalamalar + + kümeleme algoritmasını kullanarak modeli eğitme için bir seyahat kullanın.

`Main` yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[Create pipeline](./snippets/iris-clustering/csharp/Program.cs#CreatePipeline)]

Kod, veri kümesinin üç kümede bölünmesi gerektiğini belirtir.

## <a name="train-the-model"></a>Modeli eğitme

Önceki bölümlerde eklenen adımlar, eğitim için işlem hattını hazırlandı, ancak hiçbiri yürütülmedi. `Main`Veri yükleme ve model eğitimi gerçekleştirmek için aşağıdaki satırı yöntemine ekleyin:

[!code-csharp[Train the model](./snippets/iris-clustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Modeli kaydetme

Bu noktada, mevcut veya yeni .NET uygulamalarından tümleştirilebilen bir modeliniz vardır. Modelinizi bir. zip dosyasına kaydetmek için aşağıdaki kodu `Main` yöntemine ekleyin:

[!code-csharp[Save the model](./snippets/iris-clustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Tahmin için modeli kullanma

Tahmine dayalı hale getirmek için, <xref:Microsoft.ML.PredictionEngine%602> transformatör işlem hattı aracılığıyla giriş türünün örneklerini alan sınıfı kullanın ve çıkış türünün örneklerini üretir. Aşağıdaki satırı, `Main` Bu sınıfın bir örneğini oluşturmak için yöntemine ekleyin:

[!code-csharp[Create predictor](./snippets/iris-clustering/csharp/Program.cs#Predictor)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, `PredictionEnginePool` [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uygulamanız genelinde kullanılacak nesneleri oluşturan hizmetini kullanın. [ `PredictionEnginePool` ASP.NET Core Web API 'sinde kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.

> [!NOTE]
> `PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.

`TestIrisData`Test veri örneklerini barındırmak için sınıf oluşturun:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *TestIrisData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.
1. Aşağıdaki örnekte olduğu gibi, sınıfı statik olacak şekilde değiştirin:

   [!code-csharp[Make class static](./snippets/iris-clustering/csharp/TestIrisData.cs#Static)]

Bu öğretici, bu sınıf içindeki bir Iris veri örneğini tanıtır. Modelle denemeler yapmak için başka senaryolar da ekleyebilirsiniz. Sınıfına aşağıdaki kodu ekleyin `TestIrisData` :

[!code-csharp[Test data](./snippets/iris-clustering/csharp/TestIrisData.cs#TestData)]

Belirtilen öğenin ait olduğu kümeyi bulmak için, *program.cs* dosyasına dönün ve aşağıdaki kodu `Main` yöntemine ekleyin:

[!code-csharp[Predict and output results](./snippets/iris-clustering/csharp/Program.cs#PredictionExample)]

Hangi kümenin belirtilen veri örneğini içerdiğini ve bu örnekten gelen kare uzaklıkları küme centroıd 'lerini görmek için programı çalıştırın. Sonuçlarınız aşağıdakine benzer olmalıdır:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Tebrikler! Iris Kümelemesi için bir makine öğrenimi modeli başarıyla oluşturdunuz ve bu uygulamayı tahmine dayalı hale getirmek için kullandınız. Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub deposunda bulabilirsiniz.

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
> - Tahmin için modeli kullanma

Öğrenmeye devam etmek ve daha fazla örnek bulmak için GitHub depomuza göz atın.
> [!div class="nextstepaction"]
> [DotNet/machinöğrenim GitHub deposu](https://github.com/dotnet/machinelearning/)
