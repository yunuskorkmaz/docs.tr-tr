---
title: ML.NET (kümeleme) küme Iris çiçek kullanın
description: ML.NET kümeleme senaryosunda kullanmayı öğrenin
author: pkulikov
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: eddafc14de3a38cbf6f238199733ee667e6868b3
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308571"
---
# <a name="tutorial-use-mlnet-to-cluster-iris-flowers-clustering"></a>Öğretici: Kullanımı ML.NET küme Iris çiçek (kümeleme) için

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu öğretici ML.NET oluşturmak için nasıl kullanılacağını gösterir. bir [kümeleme modelinin yerini](../resources/tasks.md#clustering) için [Iris Çiçeği veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set).

Bu öğreticide, şunların nasıl yapılır:
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

## <a name="create-a-console-application"></a>Bir konsol uygulaması oluşturun

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna "IrisClustering" yazın ve ardından **Tamam** düğmesi.

1. Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi ve model dosyaları depolamak için:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni klasör**. "Veri" yazın ve Enter tuşuna basın.

1. Yükleme **Microsoft.ML** NuGet paketi:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**. Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

## <a name="prepare-the-data"></a>Verileri hazırlama

1. İndirme [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) veri kümesi ve kaydetmesi *veri* önceki adımda oluşturduğunuz klasör. Iris veri kümesi hakkında daha fazla bilgi için bkz. [Iris Çiçeği veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia sayfasında ve [Iris veri kümesini](http://archive.ics.uci.edu/ml/datasets/Iris) sayfasında, veri kümesinin kaynağı.

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

   [!code-csharp[Add necessary usings](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#1)]

Varolan sınıf tanımına kaldırın ve sınıfları tanımlar aşağıdaki kodu ekleyin `IrisData` ve `ClusterPrediction`, *IrisData.cs* dosyası:

[!code-csharp[Define data classes](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#2)]

`IrisData` giriş verisi sınıfıdır ve veri kümesindeki her bir özellik tanımı yok. Kullanım [sütun](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) veri kümesi dosyasında kaynak sütun dizinlerini belirtmek için özniteliği.

`ClusterPrediction` Sınıfı temsil eder, uygulanan kümeleme modeli çıktısını bir `IrisData` örneği. Kullanım [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) bağlanacak öznitelik `PredictedClusterId` ve `Distances` alanlarını **PredictedLabel** ve **puanı** sütunları sırasıyla. Kümeleme görev olması durumunda bu sütun şu anlama gelir:

- **PredictedLabel** sütun tahmin edilen kümenin Kimliğini içerir.
- **Puan** küme centroids için kare Euclidean uzaklığa sahip bir dizi sütun içerir. Dizi uzunluğu küme sayısı eşittir.

> [!NOTE]
> Kullanım `float` giriş ve tahmin verilerini sınıflardaki kayan nokta değerlerini temsil eden tür.

## <a name="define-data-and-model-paths"></a>Veri ve model tanımlar

Geri Git *Program.cs* dosya ve veri kümesi dosyasını ve modeli kaydedin ve dosyaya yolları tutmak için iki alanları ekleyin:

- `_dataPath` modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.
- `_modelPath` eğitilen modelin depolandığı dosya yolu içerir.

Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için:

[!code-csharp[Initialize paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#1)]

Derleme, aşağıdaki ekleyin önceki kodun `using` üst kısmındaki yönergeleri *Program.cs* dosyası:

[!code-csharp[Add usings for paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#2)]

## <a name="create-a-learning-pipeline"></a>Öğrenme işlem hattı oluşturma

Aşağıdaki ek ekleyin `using` yönergeleri üstüne *Program.cs* dosyası:

[!code-csharp[Add Microsoft.ML usings](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#3)]

İçinde `Main` yöntemi Değiştir `Console.WriteLine("Hello World!")` aşağıdaki kod ile:

[!code-csharp[Call the Train method](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#4)]

`Train` Yöntemi modeli eğitir. Bu yöntem oluşturma hemen altına `Main` yöntemi, aşağıdaki kodu kullanarak:

```csharp
private static PredictionModel<IrisData, ClusterPrediction> Train()
{

}
```

Öğrenme işlem hattınızı tüm veri ve algoritmaları modeli eğitmek gerekli yükler. Aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[Initialize pipeline](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#5)]

## <a name="load-and-transform-data"></a>Veri yükleme ve dönüştürme

İlk adımı gerçekleştirmek için eğitim veri kümesine yüklenmesidir. Bu örnekte, tarafından tanımlanan bir yol ile metin dosyasında eğitim veri kümesi depolanır `_dataPath` alan. Bir dosyadaki sütunları virgülle ayrılmış (","). Aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[Add step to load data](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#6)]

Tüm özellik sütunlar birleştirmek için sonraki adımdır **özellikleri** sütun kullanarak <xref:Microsoft.ML.Transforms.ColumnConcatenator> dönüştürme sınıfı. Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun. Aşağıdaki kodu ekleyin:

[!code-csharp[Add step to concatenate columns](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#7)]

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

Veri ardışık düzenine eklemek ve giriş doğru biçime dönüştürme sonra bir öğrenme algoritması seçin (**learner**). Learner modeli eğitir. ML.NET sağlayan bir <xref:Microsoft.ML.Trainers.KMeansPlusPlusClusterer> uygulayan learner [k-ortalamaları algoritması](https://en.wikipedia.org/wiki/K-means_clustering) ilk küme centroids seçmeye yönelik geliştirilmiş bir yöntem.

Aşağıdaki kodu ekleyin `Train` önceki adımda eklenen koddan veri işleme yöntemi:

[!code-csharp[Add a learner step](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#8)]

Kullanım <xref:Microsoft.ML.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> özellik kümeleri sayısını belirtmek için. Yukarıdaki kod, veri kümesi üç kümelerinde ayrılmalıdır belirtir.

## <a name="train-the-model"></a>Modeli eğitme

Önceki bölümde eklediğiniz adımlar eğitim için ardışık düzen hazır, ancak hiçbiri yürütüldüğünü. `pipeline.Train<TInput, TOutput>` Yöntemi üreten bir örneğini alan modeli `TInput` türü ve örneği çıkaran `TOutput` türü. Aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[Train the model and return](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#9)]

### <a name="save-the-model"></a>Modeli kaydedin

Bu noktada, tüm mevcut veya yeni .NET uygulamalarınızı tümleşik bir model var. Modelinizi bir .zip dosyası olarak kaydetmek için aşağıdaki kodu ekleyin. `Main` çağrının altına yöntemi `Train` yöntemi:

[!code-csharp[Save the model](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#10)]

Kullanarak `await` içinde `Main` yöntemi anlamına gelir `Main` yöntemi olmalıdır `async` değiştiricisi ve dönüş bir `Task`:

[!code-csharp[Make the Main method async](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#11)]

Ayrıca aşağıdakileri eklemeniz gerekir `using` en üstündeki yönerge *Program.cs* dosyası:

[!code-csharp[Add System.Threading.Tasks using](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#12)]

Çünkü `async Main` yöntemi, C# 7.1 eklenen özelliğidir ve C# 7.0 projesi varsayılan dil sürümü değil, C# 7.1 veya üzeri dil sürümünü değiştirmeniz gerekir. Bunu yapmak için'nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**. Seçin **derleme** sekmenize **Gelişmiş** düğmesi. Açılır menüden seçin **C# 7.1** (veya üzeri bir sürüm). Seçin **Tamam** düğmesi.

## <a name="use-the-model-for-predictions"></a>Kullanım modeli tahminler elde etmek için

Oluşturma `TestIrisData` ev test veri örnekleri sınıfı:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TestIrisData.cs*. Ardından, **Ekle** düğmesi.
1. Sınıfı gibi aşağıdaki örnekte de statik olarak değiştirin:

   [!code-csharp[Make class static](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#1)]

Bu öğretici, bu sınıf içinde bir Iris veri örneği tanıtır. Modelle denemek için diğer senaryolar ekleyebilirsiniz. Aşağıdaki kodu ekleyin `TestIrisData` sınıfı:

[!code-csharp[Test data](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#2)]

Belirtilen öğenin ait olduğu küme öğrenmek için geri dön *Program.cs* dosya ve içine aşağıdaki kodu ekleyin `Main` yöntemi:

[!code-csharp[Predict and output results](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#13)]

Belirtilen veri örneği ve bu örneğe karesini uzaklıkta küme centroids için hangi küme içerip programı çalıştırın. Sonuçlar aşağıdakine benzer olmalıdır. İşlem hattı işlerken bir uyarı veya iletilerini işleme görüntülenebilir. Bunlar aşağıdaki çıktıya anlaşılması için kaldırılmıştır.

```text
Cluster: 2
Distances: 0.4192338 0.0008847713 0.9660053
```

Tebrikler! Bir machine learning modeli için kümeleme ve tahminlerde bulunmak üzere kullanılan Iris artık başarıyla oluşturdunuz. Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) GitHub deposu.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide şunları öğrendiniz: nasıl yapılır:
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
