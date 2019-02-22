---
title: Iris çiçek bir kümeleme learner - ML.NET kullanarak küme
description: ML.NET kümeleme senaryosunda kullanmayı öğrenin
author: pkulikov
ms.author: johalex
ms.date: 01/11/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 03a584095badf4b1c3318833f6e67367f27b32ba
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583725"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a>Öğretici: Küme Iris çiçek kümeleme learner ML.NET ile kullanma

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu öğretici ML.NET oluşturmak için nasıl kullanılacağını gösterir. bir [kümeleme modelinin yerini](../resources/tasks.md#clustering) için [Iris Çiçeği veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set).

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> - Sorunu anlama
> - Uygun makine öğrenimi görevini seçin
> - Verileri hazırlama
> - Yükleme ve dönüştürme
> - Bir öğrenme algoritması seçin
> - Modeli eğitme
> - Kullanım modeli tahminler elde etmek için

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.

## <a name="understand-the-problem"></a>Sorunu anlama

Iris çiçek çiçek özelliklere göre farklı gruplardaki kümesini bölme hakkında bu sorun oluşur. Bu, genişlik ve bir sepal uzunluğu ve bir petal genişliği ve uzunluğu özellikleridir. Bu öğretici için her çiçek türü bilinmiyor varsayılır. Özellikleri bir veri kümesinden yapısını öğrenin ve bir veri örneği bu yapı nasıl uyduğunu tahmin etmek istiyorsunuz.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Her çiçek hangi gruba ait bilinmiyor olarak seçtiğiniz [Denetimsiz machine learning](../resources/glossary.md#unsupervised-machine-learning) görev. Bir veri kümesi gruplarında aynı gruptaki öğelerin birbirine daha fazla benzer diğer grupları şekilde bölmek için kullanın. bir [Kümeleme](../resources/tasks.md#clustering) machine learning görev.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna "IrisFlowerClustering" yazın ve ardından **Tamam** düğmesi.

1. Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi ve model dosyaları depolamak için:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni klasör**. "Veri" yazın ve Enter tuşuna basın.

1. Yükleme **Microsoft.ML** NuGet paketi:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**. Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

## <a name="prepare-the-data"></a>Verileri hazırlama

1. İndirme [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) veri kümesi ve kaydetmesi *veri* önceki adımda oluşturduğunuz klasör. Iris veri kümesi hakkında daha fazla bilgi için bkz. [Iris Çiçeği veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia sayfasında ve [Iris veri kümesini](https://archive.ics.uci.edu/ml/datasets/Iris) sayfasında, veri kümesinin kaynağı.

1. İçinde **Çözüm Gezgini**, sağ *iris.data* seçin ve dosya **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

*İris.data* dosyasını temsil eden beş sütunları içerir:

- santimetre sepal uzunluğu
- santimetre sepal genişliği
- santimetre Petal uzunluğu
- santimetre Petal genişliği
- Iris çiçek türü

Kümeleme örnek için bu öğreticinin son sütun yok sayar.

## <a name="create-data-classes"></a>Veri sınıfları oluşturma

Girdi verilerini ve Öngörüler için sınıflar oluşturun:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *IrisData.cs*. Ardından, **Ekle** düğmesi.
1. Aşağıdaki `using` yönerge yeni dosya için:

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

Varolan sınıf tanımına kaldırın ve sınıfları tanımlar aşağıdaki kodu ekleyin `IrisData` ve `ClusterPrediction`, *IrisData.cs* dosyası:

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

`IrisData` giriş verisi sınıfıdır ve veri kümesindeki her bir özellik tanımı yok. Kullanım [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) veri kümesi dosyasında kaynak sütun dizinlerini belirtmek için özniteliği.

`ClusterPrediction` Sınıfı temsil eder, uygulanan kümeleme modeli çıktısını bir `IrisData` örneği. Kullanım [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) bağlanacak öznitelik `PredictedClusterId` ve `Distances` alanlarını **PredictedLabel** ve **puanı** sütunları sırasıyla. Kümeleme görev olması durumunda bu sütun şu anlama gelir:

- **PredictedLabel** sütun tahmin edilen kümenin Kimliğini içerir.
- **Puan** küme centroids için kare Euclidean uzaklığa sahip bir dizi sütun içerir. Dizi uzunluğu küme sayısı eşittir.

> [!NOTE]
> Kullanım `float` giriş ve tahmin verilerini sınıflardaki kayan nokta değerlerini temsil eden tür.

## <a name="define-data-and-model-paths"></a>Veri ve model tanımlar

Geri Git *Program.cs* dosya ve veri kümesi dosyasını ve modeli kaydedin ve dosyaya yolları tutmak için iki alanları ekleyin:

- `_dataPath` modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.
- `_modelPath` eğitilen modelin depolandığı dosya yolu içerir.

Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için:

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

Derleme, aşağıdaki ekleyin önceki kodun `using` üst kısmındaki yönergeleri *Program.cs* dosyası:

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>ML bağlamı oluşturur

Aşağıdaki ek ekleyin `using` yönergeleri üstüne *Program.cs* dosyası:

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

İçinde `Main` yöntemi Değiştir `Console.WriteLine("Hello World!");` satırı aşağıdaki kod ile:

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<xref:Microsoft.ML.MLContext?displayProperty=nameWithType> Sınıf makine öğrenimi ortamını temsil eden ve veri yükleme, model eğitiminin, tahmin ve diğer görevler için günlüğü ve giriş noktaları için mekanizmaları sağlar. Bu kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework.

## <a name="setup-data-loading"></a>Veri yükleme kurulumu

Aşağıdaki kodu ekleyin `Main` yöntemi veri yükleme şekilde ayarlamak için:

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SetupTextLoader)]

Kullanım [genel `CreateTextLoader` ](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%60%601(Microsoft.ML.DataOperationsCatalog,System.Boolean,System.Char,System.Boolean,System.Boolean,System.Boolean)) dataset şemanın çıkarsandığı yöntemi `IrisData` sınıf tanımını.

Kullanım örneği <xref:Microsoft.ML.Data.TextLoader> oluşturmak için örnek bir <xref:Microsoft.Data.DataView.IDataView> temsil eden bir eğitim veri kümesi için veri kaynağı örneği:

[!code-csharp[Create IDataView](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

## <a name="create-a-learning-pipeline"></a>Öğrenme işlem hattı oluşturma

Bu öğreticide, öğrenme işlem hattınızı kümeleme görevin aşağıdaki iki adımdan oluşur:

- yüklenen sütunu bir birleştirme **özellikleri** kümeleme Eğitmen tarafından; kullanılan sütun
- kullanan bir <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> k kullanarak modeli eğitmek için Eğitmen-anlamına gelir ++ kümeleme algoritması.

Aşağıdaki kodu ekleyin `Main` yöntemi:

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

Kod üç kümelerinde veri kümesi ayrılmalıdır belirtir.

## <a name="train-the-model"></a>Modeli eğitme

Önceki bölümde eklediğiniz adımlar eğitim için ardışık düzen hazır, ancak hiçbiri yürütüldüğünü. Aşağıdaki satırı ekleyin `Main` gerçekleştirmek için veri yükleme ve model eğitiminin yöntemi:

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Modeli kaydedin

Bu noktada, tüm mevcut veya yeni .NET uygulamalarınızı tümleşik bir model var. Modelinizi bir .zip dosyası olarak kaydetmek için aşağıdaki kodu ekleyin. `Main` yöntemi:

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Kullanım modeli tahminler elde etmek için

Öngörüler yapma <xref:Microsoft.ML.PredictionEngine%602> giriş türü dönüştürücü ardışık düzeninden örneklerini alır ve çıktı türü örneklerini üretir sınıfı. Aşağıdaki satırı ekleyin `Main` yöntemi bu sınıfın bir örneğini oluşturmak için:

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

Oluşturma `TestIrisData` ev test veri örnekleri sınıfı:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TestIrisData.cs*. Ardından, **Ekle** düğmesi.
1. Sınıfı gibi aşağıdaki örnekte de statik olarak değiştirin:

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

Bu öğretici, bu sınıf içinde bir Iris veri örneği tanıtır. Modelle denemek için diğer senaryolar ekleyebilirsiniz. Aşağıdaki kodu ekleyin `TestIrisData` sınıfı:

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

Belirtilen öğenin ait olduğu küme öğrenmek için geri dön *Program.cs* dosya ve içine aşağıdaki kodu ekleyin `Main` yöntemi:

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

Belirtilen veri örneği ve bu örneğe karesini uzaklıkta küme centroids için hangi küme içerip programı çalıştırın. Sonuçlar aşağıdakine benzer olmalıdır:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Tebrikler! Bir machine learning modeli için kümeleme ve tahminlerde bulunmak üzere kullanılan Iris artık başarıyla oluşturdunuz. Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub deposu.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> - Sorunu anlama
> - Uygun makine öğrenimi görevini seçin
> - Verileri hazırlama
> - Yükleme ve dönüştürme
> - Bir öğrenme algoritması seçin
> - Modeli eğitme
> - Kullanım modeli tahminler elde etmek için

Almaya devam etmek ve diğer örnekleri bulmak için GitHub depomuza denetleyin.
> [!div class="nextstepaction"]
> [DotNet/machinelearning GitHub deposu](https://github.com/dotnet/machinelearning/)
