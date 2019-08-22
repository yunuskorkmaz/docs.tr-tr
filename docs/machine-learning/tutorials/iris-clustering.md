---
title: "Öğretici: Iris çiçekler ' i kategorilere ayırma-k-belirtir kümeleme"
description: Kümeleme senaryosunda ML.NET kullanmayı öğrenin
author: pkulikov
ms.date: 05/16/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 772558be14d207475d20083f5a6b729f03766471
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666641"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Öğretici: Iris çiçekler ile k-ML.NET Kümelemesi kullanarak kategorilere ayır

Bu öğreticide, [Iris çiçek veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set)için bir [kümeleme modeli](../resources/tasks.md#clustering) oluşturmak üzere ml.net 'in nasıl kullanılacağı gösterilmektedir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> - Sorunu anlama
> - Uygun makine öğrenimi görevini seçin
> - Verileri hazırlama
> - Verileri yükleme ve dönüştürme
> - Bir öğrenme algoritması seçin
> - Modeli eğitme
> - Tahmin için modeli kullanma

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="understand-the-problem"></a>Sorunu anlama

Bu sorun, bir Iris çiçekler kümesini, çiçek özelliklerine göre farklı gruplarda bölmek için kullanılır. Bu özellikler, bir sepal 'ın uzunluğu ve genişliği ve Petal 'ın uzunluğu ve genişliği. Bu öğretici için, her çiçek türünün bilinmediğini varsayın. Özelliklerden bir veri kümesinin yapısını öğrenmek ve bir veri örneğinin bu yapıya nasıl uyduğunu tahmin etmek istiyorsunuz.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Her bir çiçek 'nin hangi gruba ait olduğunu bilmiyorsanız, denetimli [makine öğrenimi](../resources/glossary.md#unsupervised-machine-learning) görevini seçersiniz. Gruplardaki bir veri kümesini, aynı gruptaki öğelerin diğer gruplardaki diğer gruplardan birbirlerine benzer şekilde bölmek için, bir [kümeleme](../resources/tasks.md#clustering) Machine Learning görevi kullanın.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Visual Studio'yu açın. Menü çubuğundan **Dosya** > **Yeni** > **Proje** ' yi seçin. **Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin. Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin. **Ad** metin kutusuna "ırisflowerkümeleme" yazın ve **Tamam** düğmesini seçin.

1. Veri kümesi ve model dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun:

    **Çözüm Gezgini**, projeye sağ tıklayın ve**Yeni klasör** **Ekle** > ' yi seçin. "Data" yazın ve ENTER tuşuna basın.

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

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *IrisData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.
1. Aşağıdaki `using` yönergeyi yeni dosyaya ekleyin:

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

Mevcut sınıf tanımını kaldırın ve sınıfları `IrisData` ve `ClusterPrediction`IrisData.cs dosyasını tanımlayan aşağıdaki kodu ekleyin:

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

`IrisData`, giriş veri sınıfıdır ve veri kümesindeki her bir özellik için tanımlar içerir. Veri kümesi dosyasındaki kaynak sütunlarının dizinlerini belirtmek için [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute) özniteliğini kullanın.

Sınıfı, bir `IrisData` örneğe uygulanan kümeleme modelinin çıkışını temsil eder. `ClusterPrediction` `PredictedClusterId` Ve [](xref:Microsoft.ML.Data.ColumnNameAttribute) alanlarını`Distances` tahmine **tedlabel** öğesine bağlamak için ColumnName özniteliğini kullanın ve sütunları sırasıyla puan yapın. Kümeleme görevi söz konusu sütunlarda aşağıdaki anlamı vardır:

- **Predictedlabel** sütunu, tahmin EDILEN kümenin kimliğini içerir.
- **Puan** sütunu, kare Içinde Euclidea uzaklıkları küme centroıd 'leri için olan bir dizi içeriyor. Dizi uzunluğu, küme sayısına eşittir.

> [!NOTE]
> Giriş ve tahmin veri sınıflarında kayan nokta değerlerini göstermek için türünükullanın.`float`

## <a name="define-data-and-model-paths"></a>Veri ve model yollarını tanımlama

*Program.cs* dosyasına dönün ve veri kümesi dosyasına ve modelin kaydedileceği dosyanın yollarını barındıracak iki alan ekleyin:

- `_dataPath`modeli eğitmek için kullanılan veri kümesiyle dosyanın yolunu içerir.
- `_modelPath`eğitilen modelin depolandığı dosyanın yolunu içerir.

Aşağıdaki kodu, bu yolları belirtmek için `Main` yöntemine hemen ekleyin:

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

Önceki kodu derlemek için, *program.cs* dosyasının en üstüne aşağıdaki `using` yönergeleri ekleyin:

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>ML bağlamı oluştur

*Program.cs* dosyasının en üstüne `using` aşağıdaki ek yönergeleri ekleyin:

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

`Main` Yönteminde `Console.WriteLine("Hello World!");` satırını aşağıdaki kodla değiştirin:

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<xref:Microsoft.ML.MLContext?displayProperty=nameWithType> Sınıfı, Machine Learning ortamını temsil eder ve veri yükleme, model eğitimi, tahmin ve diğer görevler için günlüğe kaydetme ve giriş noktaları için mekanizmalar sağlar. Bu, kavramsal olarak Entity Framework ' `DbContext` de kullanılmasına benzer.

## <a name="setup-data-loading"></a>Kurulum verilerini yükleme

Aşağıdaki kodu `Main` yöntemine ekleyerek verileri yükleme yolunu ayarlayın:

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

Genel `IrisData` [ `MLContext.Data.LoadFromTextFile` genişletme yöntemi](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri kümesi şemasını belirtilen tür ve döndürmektedir <xref:Microsoft.ML.IDataView> . Bu, dönüştürücüler için giriş olarak kullanılabilir.

## <a name="create-a-learning-pipeline"></a>Öğrenme işlem hattı oluşturma

Bu öğreticide, kümeleme görevinin öğrenme işlem hattı aşağıdaki iki adımdan oluşur:

- yüklenen sütunları bir kümeleme işlemi tarafından kullanılan tek bir **Özellikler** sütununa birleştirme;
- k- <xref:Microsoft.ML.Trainers.KMeansTrainer> ortalamalar + + kümeleme algoritmasını kullanarak modeli eğitme için bir seyahat kullanın.

`Main` Yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

Kod, veri kümesinin üç kümede bölünmesi gerektiğini belirtir.

## <a name="train-the-model"></a>Modeli eğitme

Önceki bölümlerde eklenen adımlar, eğitim için işlem hattını hazırlandı, ancak hiçbiri yürütülmedi. Veri yükleme ve model eğitimi gerçekleştirmek `Main` için aşağıdaki satırı yöntemine ekleyin:

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Modeli kaydetme

Bu noktada, mevcut veya yeni .NET uygulamalarından tümleştirilebilen bir modeliniz vardır. Modelinizi bir. zip dosyasına kaydetmek için aşağıdaki kodu `Main` yöntemine ekleyin:

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Tahmin için modeli kullanma

Tahmine dayalı hale getirmek için, transformatör <xref:Microsoft.ML.PredictionEngine%602> işlem hattı aracılığıyla giriş türünün örneklerini alan sınıfı kullanın ve çıkış türünün örneklerini üretir. Aşağıdaki satırı `Main` , bu sınıfın bir örneğini oluşturmak için yöntemine ekleyin:

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

Test veri örneklerini barındırmak için sınıfoluşturun:`TestIrisData`

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *TestIrisData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.
1. Aşağıdaki örnekte olduğu gibi, sınıfı statik olacak şekilde değiştirin:

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

Bu öğretici, bu sınıf içindeki bir Iris veri örneğini tanıtır. Modelle denemeler yapmak için başka senaryolar da ekleyebilirsiniz. `TestIrisData` Sınıfına aşağıdaki kodu ekleyin:

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

Belirtilen öğenin ait olduğu kümeyi bulmak için, *program.cs* dosyasına dönün ve aşağıdaki kodu `Main` yöntemine ekleyin:

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

Hangi kümenin belirtilen veri örneğini içerdiğini ve bu örnekten gelen kare uzaklıkları küme centroıd 'lerini görmek için programı çalıştırın. Sonuçlarınız aşağıdakine benzer olmalıdır:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Tebrikler! Iris Kümelemesi için bir makine öğrenimi modeli başarıyla oluşturdunuz ve bu uygulamayı tahmine dayalı hale getirmek için kullandınız. Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
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
