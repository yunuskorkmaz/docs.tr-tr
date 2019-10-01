---
title: 'Öğretici: Iris çiçekleri kategorilere ayır-k-bir kümeleme'
description: Kümeleme senaryosunda ML.NET kullanmayı öğrenin
author: pkulikov
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: e360cf2418e2003f9f40628c714e9e8ebd7c3e40
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698555"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Öğretici: Iris çiçekler 'i k-ML.NET Kümelemesi kullanarak kategorilere ayırın

Bu öğreticide, [Iris çiçek veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set)için bir [kümeleme modeli](../resources/tasks.md#clustering) oluşturmak üzere ml.net 'in nasıl kullanılacağı gösterilmektedir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> - Sorunu anlama
> - Uygun makine öğrenimi görevini seçin
> - Verileri hazırlama
> - Verileri yükleme ve dönüştürme
> - Bir öğrenme algoritması seçin
> - Modeli eğitme
> - Tahmin için modeli kullanma

## <a name="prerequisites"></a>Prerequisites

- [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="understand-the-problem"></a>Sorunu anlama

Bu sorun, bir Iris çiçekler kümesini, çiçek özelliklerine göre farklı gruplarda bölmek için kullanılır. Bu özellikler, bir sepal 'ın uzunluğu ve genişliği ve Petal 'ın uzunluğu ve genişliği. Bu öğretici için, her çiçek türünün bilinmediğini varsayın. Özelliklerden bir veri kümesinin yapısını öğrenmek ve bir veri örneğinin bu yapıya nasıl uyduğunu tahmin etmek istiyorsunuz.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Her bir çiçek 'nin hangi gruba ait olduğunu bilmiyorsanız, denetimli [makine öğrenimi](../resources/glossary.md#unsupervised-machine-learning) görevini seçersiniz. Gruplardaki bir veri kümesini, aynı gruptaki öğelerin diğer gruplardaki diğer gruplardan birbirlerine benzer şekilde bölmek için, bir [kümeleme](../resources/tasks.md#clustering) Machine Learning görevi kullanın.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Visual Studio'yu açın. Menü çubuğundan **dosya** > **Yeni** > **Proje** ' yi seçin. **Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin. Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin. **Ad** metin kutusuna "ırisflowerkümeleme" yazın ve **Tamam** düğmesini seçin.

1. Veri kümesi ve model dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun:

    **Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin. "Data" yazın ve ENTER tuşuna basın.

1. **Microsoft.ml** NuGet paketini yükler:

    **Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, **Araştır** sekmesini seçin, **Microsoft.ml**için arama yapın, listeden **v 1.0.0** paketini seçin ve sonra da **Install** düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.

## <a name="prepare-the-data"></a>Verileri hazırlama

1. [Iris. Data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) veri kümesini indirin ve önceki adımda oluşturduğunuz *veri* klasörüne kaydedin. Iris veri kümesi hakkında daha fazla bilgi için, veri kümesinin kaynağı olan [Iris çiçek veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set) vikipi sayfasında ve [Iris veri kümesi](https://archive.ics.uci.edu/ml/datasets/Iris) sayfasına bakın.

1. **Çözüm Gezgini**, *Iris. Data* dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

*Iris. Data* dosyası, şunları temsil eden beş sütun içerir:

- santimetres cinsinden sepal uzunluğu
- santimetres cinsinden sepal genişliği
- santimetres 'de Petal uzunluğu
- santimetres 'de Petal genişliği
- Iris çiçek türü

Kümeleme örneği için bu öğretici son sütunu yoksayar.

## <a name="create-data-classes"></a>Veri sınıfları oluşturma

Giriş verileri ve tahminleri için sınıflar oluşturun:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *IrisData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.
1. Aşağıdaki `using` yönergesini yeni dosyaya ekleyin:

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

Mevcut sınıf tanımını kaldırın ve *IrisData.cs* dosyasına `IrisData` ve `ClusterPrediction` sınıflarını tanımlayan aşağıdaki kodu ekleyin:

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

`IrisData`, giriş veri sınıfıdır ve veri kümesindeki her bir özellik için tanımlara sahiptir. Veri kümesi dosyasındaki kaynak sütunlarının dizinlerini belirtmek için [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute) özniteliğini kullanın.

@No__t-0 sınıfı, bir `IrisData` örneğine uygulanan kümeleme modelinin çıkışını temsil eder. @No__t-1 ve `Distances` alanlarını tahmine **Tedlabel** öğesine bağlamak için [sütunadı](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğini kullanın ve sütunları sırasıyla **puan** yapın. Kümeleme görevi söz konusu sütunlarda aşağıdaki anlamı vardır:

- **Predictedlabel** sütunu, tahmin EDILEN kümenin kimliğini içerir.
- **Puan** sütunu, kare Içinde Euclidea uzaklıkları küme centroıd 'leri için olan bir dizi içeriyor. Dizi uzunluğu, küme sayısına eşittir.

> [!NOTE]
> Giriş ve tahmin veri sınıflarında kayan nokta değerlerini göstermek için `float` türünü kullanın.

## <a name="define-data-and-model-paths"></a>Veri ve model yollarını tanımlama

*Program.cs* dosyasına dönün ve veri kümesi dosyasına ve modelin kaydedileceği dosyanın yollarını barındıracak iki alan ekleyin:

- `_dataPath`, modeli eğitmek için kullanılan veri kümesiyle dosyanın yolunu içerir.
- `_modelPath`, eğitilen modelin depolandığı dosyanın yolunu içerir.

Bu yolları belirtmek için `Main` yönteminin üstüne aşağıdaki kodu ekleyin:

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

Yukarıdaki kodu derlemek için, *program.cs* dosyasının en üstüne aşağıdaki `using` yönergelerini ekleyin:

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>ML bağlamı oluştur

*Program.cs* dosyasının en üstüne aşağıdaki ek `using` yönergelerini ekleyin:

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

@No__t-0 yönteminde, `Console.WriteLine("Hello World!");` satırını aşağıdaki kodla değiştirin:

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

@No__t-0 sınıfı, Machine Learning ortamını temsil eder ve veri yükleme, model eğitimi, tahmin ve diğer görevler için günlüğe kaydetme ve giriş noktaları için mekanizmalar sağlar. Bu, kavramsal olarak Entity Framework `DbContext` kullanılmasına benzer.

## <a name="setup-data-loading"></a>Kurulum verilerini yükleme

Aşağıdaki kodu `Main` yöntemine ekleyerek verileri yükleme yolunu ayarlayın:

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

Genel [`MLContext.Data.LoadFromTextFile` uzantı yöntemi](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , belirtilen `IrisData` türünden veri kümesi şemasını kullanır ve dönüştürücüler için giriş olarak kullanılabilecek <xref:Microsoft.ML.IDataView> ' ü döndürür.

## <a name="create-a-learning-pipeline"></a>Öğrenme işlem hattı oluşturma

Bu öğreticide, kümeleme görevinin öğrenme işlem hattı aşağıdaki iki adımdan oluşur:

- yüklenen sütunları bir kümeleme işlemi tarafından kullanılan tek bir **Özellikler** sütununa birleştirme;
- <xref:Microsoft.ML.Trainers.KMeansTrainer> eğitmen kullanarak modeli k-ortalamalar + + kümeleme algoritmasını kullanarak eğitme.

@No__t-0 yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

Kod, veri kümesinin üç kümede bölünmesi gerektiğini belirtir.

## <a name="train-the-model"></a>Modeli eğitme

Önceki bölümlerde eklenen adımlar, eğitim için işlem hattını hazırlandı, ancak hiçbiri yürütülmedi. Veri yükleme ve model eğitimi gerçekleştirmek için aşağıdaki satırı `Main` yöntemine ekleyin:

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Modeli kaydetme

Bu noktada, mevcut veya yeni .NET uygulamalarından tümleştirilebilen bir modeliniz vardır. Modelinizi bir. zip dosyasına kaydetmek için, `Main` yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Tahmin için modeli kullanma

Tahmine dayalı hale getirmek için, transformatör işlem hattı aracılığıyla giriş türünün örneklerini alan <xref:Microsoft.ML.PredictionEngine%602> sınıfını kullanın ve çıkış türünün örneklerini üretir. Bu sınıfın bir örneğini oluşturmak için `Main` yöntemine aşağıdaki satırı ekleyin:

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın. [ASP.NET Core Web API 'sinde `PredictionEnginePool` ' i nasıl kullanacağınızı](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) öğrenmek için bu kılavuza bakın

> [!NOTE]
> `PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.

Test verileri örneklerini barındırmak için `TestIrisData` sınıfını oluşturun:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *TestIrisData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.
1. Aşağıdaki örnekte olduğu gibi, sınıfı statik olacak şekilde değiştirin:

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

Bu öğretici, bu sınıf içindeki bir Iris veri örneğini tanıtır. Modelle denemeler yapmak için başka senaryolar da ekleyebilirsiniz. @No__t-0 sınıfına aşağıdaki kodu ekleyin:

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

Belirtilen öğenin ait olduğu kümeyi bulmak için, *program.cs* dosyasına dönün ve `Main` yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

Hangi kümenin belirtilen veri örneğini içerdiğini ve bu örnekten gelen kare uzaklıkları küme centroıd 'lerini görmek için programı çalıştırın. Sonuçlarınız aşağıdakine benzer olmalıdır:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Mühendisi! Iris Kümelemesi için bir makine öğrenimi modeli başarıyla oluşturdunuz ve bu uygulamayı tahmine dayalı hale getirmek için kullandınız. Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, nasıl yapılacağını öğrendiniz:
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
