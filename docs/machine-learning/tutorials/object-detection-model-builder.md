---
title: 'Öğretici: model Oluşturucu ile görüntülerde nesneleri algılama'
description: Bu öğreticide, görüntülerde durma işaretlerini algılamak için ML.NET model Oluşturucu ve Azure ML kullanarak bir nesne algılama modelinin nasıl oluşturulacağı gösterilmektedir.
author: briacht
ms.author: brachtma
ms.date: 03/12/2021
ms.topic: tutorial
ms.custom: mlnet-tooling
ms.openlocfilehash: 21b672b84c7f55578a76459fa9f02aca3455d719
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104657917"
---
# <a name="tutorial-detect-stop-signs-in-images-with-model-builder"></a>Öğretici: model Oluşturucu ile görüntülerde durma işaretlerini Algıla

Görüntülerde durma işaretlerini algılayıp bulmak için ML.NET model Oluşturucu ve Azure ML kullanarak bir nesne algılama modeli oluşturmayı öğrenin.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Verileri hazırlama ve anlama
> - Senaryoyu seçin
> - Eğitim ortamını seçin
> - Verileri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Tahmin için modeli kullanma

> [!NOTE]
> Model Oluşturucu Şu anda önizleme aşamasındadır.

## <a name="prerequisites"></a>Önkoşullar

Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.

## <a name="model-builder-object-detection-overview"></a>Model Oluşturucu nesne algılamaya genel bakış

Nesne algılama bir bilgisayar vizyonu sorunudur. Görüntü sınıflandırmasıyla yakından ilgili olarak, nesne algılama görüntü sınıflandırmasını daha ayrıntılı bir ölçekte gerçekleştirir. Nesne algılama hem görüntüler içindeki varlıkları bulur _hem_ de kategorilere ayırır. Görüntüler farklı türlerde birden çok nesne içerdiğinde nesne algılamayı kullanın.

![Resim sınıflandırmasına karşı nesne sınıflandırmasına karşı ekran görüntüleri.](./media/object-detection-onnx/img-classification-obj-detection.PNG)

Nesne algılama için bazı kullanım örnekleri şunları içerir:

- Self-Driving otomobiller
- Robotics
- Yüz Algılama
- Çalışma alanı güvenliği
- Nesne sayımı
- Etkinlik tanıma

Bu örnek, model Oluşturucu ile oluşturulmuş bir makine öğrenimi modeli kullanarak görüntülerde durma işaretlerini algılayan bir C# .NET Core konsol uygulaması oluşturur. Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/ObjectDetection_StopSigns) GitHub deposunda bulabilirsiniz.

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

Dur Işareti veri kümesi, her biri en az bir Dur işareti içeren [50 görüntüden indirilen](https://unsplash.com/)görüntüden oluşur.

Yapmanız gereken ilk şey, resimlerinize not ekleme veya her görüntüde durdurma işaretlerinin etrafında sınırlayıcı kutular çizmektir. Bu öğreticide, resimlerinize [Vott](https://github.com/microsoft/VoTT)adlı bir araçla açıklama eklenir.

> Aşağıdaki veri etiketleme adımlarını atlamak istiyorsanız, veri [kümesinin bu sürümünü indirebilir](https://aka.ms/mlnet-object-detection-tutorial-assets) ve [bir konsol uygulaması oluşturmak](object-detection-model-builder.md#create-a-console-application)için atlayabilirsiniz.

### <a name="create-a-new-vott-project"></a>Yeni bir VoTT projesi oluşturma

1. 50 [veri kümesini indirin](https://aka.ms/mlnet-object-detection-tutorial-dataset) ve görüntüleri imzalayın.
1. [VoTT 'Yi indirin](https://github.com/Microsoft/VoTT/releases) (görsel nesne etiketleme aracı).
1. VoTT 'yi açın ve **Yeni proje**'yi seçin.

    ![VoTT giriş ekranı](./media/object-detection-model-builder/vott.png)

1. **Proje ayarları**' nda, **görünen adı** "StopSignObjDetection" olarak değiştirin.
1. **Güvenlik belirtecini** *yeni güvenlik belirteci oluşturacak* şekilde değiştirin.
1. **Kaynak bağlantısı**' nın yanındaki **bağlantı ekle**' yi seçin.
1. **Bağlantı ayarları**' nda, kaynak **bağlantının görünen adını** "stopsignımages" olarak değiştirin ve **sağlayıcı** olarak *yerel dosya sistemi* ' ni seçin. **Klasör yolu** için 50 eğitim görüntülerini Içeren *durdurma işaretleri* klasörünü seçin ve ardından **Bağlantıyı Kaydet**' i seçin.

    ![VoTT yeni bağlantı Iletişim kutusu](./media/object-detection-model-builder/vott-new-connection.png)

1. **Proje ayarları**' nda, **kaynak bağlantısını** *stopsignımages* (yeni oluşturduğunuz bağlantı) olarak değiştirin.
1. **Hedef bağlantıyı** Ayrıca *stopsignımages* ile değiştirin. **Proje ayarlarınız** şu ekran görüntüsüne benzer şekilde görünmelidir:

    ![VoTT proje ayarları Iletişim kutusu](./media/object-detection-model-builder/vott-new-project.png)

1. **Projeyi kaydet**' i seçin.

### <a name="add-tag-and-label-images"></a>Etiket ve etiket görüntüleri ekleme

Şimdi, sol taraftaki tüm eğitim görüntülerinin önizlemesi, ortadaki seçili görüntünün önizlemesi ve sağ taraftaki **Etiketler** sütunu ile bir pencere görmeniz gerekir. Bu ekran **Etiketler düzenleyicisidir**.

1. Yeni bir etiket eklemek için **Etiketler** araç çubuğunda ilk (artı-şekillendirilmiş) simgesini seçin.

    ![VoTT yeni etiket simgesi](./media/object-detection-model-builder/vott-new-tag-icon.png)

1. "Durdur-Imzala" etiketini adlandırın ve klavyenizde <kbd>ENTER</kbd> tuşuna basın.

    ![VoTT yeni etiketi](./media/object-detection-model-builder/vott-new-tag.png)

1. Görüntüde her bir durdurma işaretini çevreleyen bir dikdörtgen çizmek için tıklayın ve sürükleyin. İmleç bir dikdörtgen çizmenize izin vermezse, üstteki araç çubuğundan **dikdörtgen çiz** aracını seçmeyi veya <kbd>R</kbd>klavye kısayolunu kullanmayı deneyin.
1. Dikdörtgeninizi çizdikten sonra, etiketi sınırlayıcı kutuya eklemek için önceki adımlarda oluşturduğunuz **Durdur-imzala** etiketini seçin.
1. Veri kümesindeki bir sonraki görüntünün önizleme görüntüsüne tıklayın ve bu işlemi tekrarlayın.
1. Her görüntüde her durdurma oturumu için 3-4 adıma devam edin.

    ![VoTT resimleri açıklama ekleme](./media/object-detection-model-builder/vott-annotating.gif)

### <a name="export-your-vott-json"></a>VoTT JSON 'nizi dışarı aktarma

Tüm eğitim görüntülerinizi etiketledikten sonra, eğitim için model Oluşturucu tarafından kullanılacak dosyayı dışarı aktarabilirsiniz.

1. **Dışa aktarma ayarlarına** gitmek için sol araç çubuğundaki dördüncü simgeyi (bir kutudaki çapraz oka sahip olan) seçin.
1. **Sağlayıcıyı** *vott JSON* olarak bırakın.
1. **Varlık durumunu** *yalnızca etiketli varlıklar* olarak değiştirin.
1. **Görüntüleri içer** işaretini kaldırın. Görüntüleri eklerseniz, eğitim görüntüleri oluşturulan dışarı aktarma klasörüne kopyalanır ve bu gerekli değildir.
1. **Dışarı aktarma ayarlarını kaydet**' i seçin.

    ![VoTT dışarı aktarma ayarları](./media/object-detection-model-builder/vott-export.png)

1. **Etiketler düzenleyiciye** geri dönün (sol araç çubuğundaki ikinci simge bir şerit gibi). Üstteki araç çubuğunda **projeyi dışarı aktar** simgesini (bir kutudaki ok gibi) seçin veya <kbd>CTRL</kbd> + <kbd>E</kbd>klavye kısayolunu kullanın.

    ![VoTT dışarı aktarma düğmesi](./media/object-detection-model-builder/vott-export-button.png)

Bu dışarı aktarma işlemi, *Dur-imzala* klasörünüzde *vott-JSON-Export* adlı yeni bir klasör oluşturur ve bu yeni klasörde *STOPSIGNOBJDETECTION-Export* adlı bir JSON dosyası oluşturur. Bu JSON dosyasını, model Oluşturucu 'da bir nesne algılama modelini eğitmek için sonraki adımlarda kullanacaksınız.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Visual Studio 'da, *Stopsigndetection* adlı bir **C# .NET Core konsol uygulaması** oluşturun.

## <a name="choose-a-scenario"></a>Senaryo seçin

1. **Çözüm Gezgini**, *stopsigndetection* projesine sağ tıklayın ve   >  model Oluşturucu kullanıcı arabirimini açmak için **Machine Learning** Ekle ' yi seçin.
1. Bu örnek için, senaryo nesne algılamasında bulunur. Model oluşturucunun **senaryo** adımında, **nesne algılama** senaryosunu seçin.

![Visual Studio 'da model Oluşturucu Sihirbazı](./media/object-detection-model-builder/obj-det-scenario.png)

> Senaryolar listesinde *nesne algılamayı* görmüyorsanız, [model Oluşturucu sürümünüzü güncelleştirmeniz](https://marketplace.visualstudio.com/items?itemName=MLNET.07)gerekebilir.

## <a name="choose-the-training-environment"></a>Eğitim ortamını seçin

Şu anda, model Oluşturucu yalnızca Azure Machine Learning olan eğitim nesne algılama modellerini destekler, bu nedenle Azure eğitim ortamı varsayılan olarak seçilidir.

![Azure eğitim ortamı seçimi](./media/object-detection-model-builder/obj-det-environment.png)

Azure ML 'yi kullanarak bir modeli eğmek için model Oluşturucu 'dan bir Azure ML denemesi oluşturmanız gerekir.

**Azure ML** denemesi, bir veya daha fazla makine öğrenimi eğitiminin çalıştığı yapılandırmayı ve sonuçları kapsülleyen bir kaynaktır.

Azure ML denemesi oluşturmak için öncelikle ortamınızı Azure 'da yapılandırmanız gerekir. Bir deneme çalışması için aşağıdakiler gerekir:

- Bir Azure aboneliği
- **Çalışma alanı**: eğitim çalıştırmasının bir parçası olarak oluşturulan tüm Azure ML kaynakları ve yapıtları için merkezi bir yer sağlayan BIR Azure ML kaynağı.
- **İşlem**: Azure Machine Learning işlem, eğitim için kullanılan bulut tabanlı BIR Linux VM 'dir. [Model Oluşturucu tarafından desteklenen işlem türleri](../resources/azure-training-concepts-model-builder.md#what-is-an-azure-machine-learning-compute)hakkında daha fazla bilgi edinin.

### <a name="set-up-an-azure-ml-workspace"></a>Azure ML çalışma alanı ayarlama

Ortamınızı yapılandırmak için:

1. **Çalışma alanını ayarla** düğmesini seçin.
1. **Yeni deneme oluştur** Iletişim kutusunda Azure aboneliğinizi seçin.
1. Mevcut bir çalışma alanını seçin veya yeni bir Azure ML çalışma alanı oluşturun.

    Yeni bir çalışma alanı oluşturduğunuzda, aşağıdaki kaynaklar sağlanır:

    - Azure Machine Learning çalışma alanı
    - Azure Storage
    - Azure Application Insights
    - Azure Container Registry
    - Azure Key Vault

    Sonuç olarak, bu işlem birkaç dakika sürebilir.

1. Mevcut bir işlem seçin veya yeni bir Azure ML işlemi oluşturun. Bu işlem birkaç dakika sürebilir.
1. Varsayılan deneme adını bırakıp **Oluştur**' u seçin.

    ![Azure çalışma alanı kurulum Iletişim kutusu](./media/object-detection-model-builder/azure-dialog.png)

İlk deneme oluşturulur ve deneme adı çalışma alanına kaydedilir. Sonraki tüm çalıştırmalar (aynı deneme adı kullanılırsa) aynı denemenin bir parçası olarak günlüğe kaydedilir. Aksi takdirde, yeni bir deneme oluşturulur.

Yapılandırmanızla memnun kaldıysanız, **veri** adımına geçmek Için model Oluşturucu 'daki **sonraki adım** düğmesini seçin.

## <a name="load-the-data"></a>Verileri yükleme

Model oluşturucunun **veri** adımında eğitim veri kümenizi seçersiniz.

>Model Oluşturucu Şu anda yalnızca VoTT tarafından oluşturulan JSON biçimini kabul eder, ancak takım daha sonra daha fazla biçim desteği eklemeyi planlıyor. Model Oluşturucu 'da desteklendiğini görmek istediğiniz nesne algılama için bir veri kümesi biçimi varsa, geri bildiriminizi [GitHub](https://github.com/dotnet/machinelearning-modelbuilder/issues/new?assignees=&labels=&template=data_suggestion.md&title=)' da bırakın.

1. **Klasör Seç** metin kutusunun yanındaki düğmeyi seçin ve `StopSignObjDetection-export.json` *Durdur-imzalar/vott-JSON-Export* dizininde bulunması gereken öğesini bulmak için dosya Gezgini 'ni kullanın.

    ![Model Oluşturucu verileri adımı](./media/object-detection-model-builder/obj-det-data.png)

1. Verileriniz **veri önizlemesinde** doğru görünüyorsa, **eğitme** adımına geçmek için **İleri adım** ' ı seçin.

## <a name="train-the-model"></a>Modeli eğitme

Sonraki adım modelinize eğitedir.

Model Oluşturucu **eğitme** ekranında **eğitime başla** düğmesini seçin.

Bu noktada Verileriniz Azure Storage 'a yüklenir ve eğitim süreci Azure ML 'de başlar.

>Eğitim süreci bir süre sürer ve bu süre, seçilen işlem boyutuna ve veri miktarına bağlı olarak değişebilir. Bir modelin Azure 'da eğitildiği ilk sefer, kaynakların sağlanması gerektiğinden biraz daha uzun bir eğitim süresi bekleyebilir. Bu 50 görüntü örneği için eğitim yaklaşık 16 dakika sürdü.

Azure Machine Learning portalında çalıştırmaların ilerlemesini, Visual Studio 'da **geçerli çalışmayı izle Azure Portal** bağlantısını seçerek izleyebilirsiniz.

Eğitim tamamlandıktan sonra, **değerlendir** adımına geçmek için **sonraki adım** düğmesini seçin.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Değerlendirme ekranında, model doğruluğu dahil olmak üzere eğitim sürecinin sonuçlarına ilişkin bir genel bakış elde edersiniz.

![Model Oluşturucu adımı değerlendir](./media/object-detection-model-builder/obj-det-evaluate.png)

Bu durumda, doğruluk %100 diyor ve bu da modelin veri kümesindeki çok az sayıda görüntü nedeniyle büyük *olasılıkla büyük* olduğu anlamına gelir.

Modelinizin beklendiği gibi çalışıp çalışmadığını hızlı bir şekilde denetlemek için **modelinize deneme** deneyimini kullanabilirsiniz.

**Bir görüntüye gözatıp** , tercihen modelin eğitim kapsamında kullanmadığından bir test görüntüsü belirtin.

![Model Oluşturucu modelinizi deneyin](./media/object-detection-model-builder/obj-det-try-model.png)

Algılanan her bir sınırlayıcı kutusunda gösterilen puan, algılanan nesnenin **güvenilirlikli** olduğunu gösterir. Örneğin, yukarıdaki ekran görüntüsünde, durdurma işareti etrafındaki sınırlayıcı kutudaki puan, modelin %99 olduğunu ve algılanan nesnenin bir Dur işareti olduğundan emin olduğunu gösterir.

Eşik kaydırıcıyla arttırılabilen veya azaltılan **puan eşiği**, puanlarına göre algılanan nesneleri ekler ve kaldırır. Örneğin, eşik. 51 ise, model yalnızca Güvenirlik puanı. 51 veya üzeri olan nesneleri gösterir. Eşiği artırdıkça, daha az algılanan nesneler görürsünüz ve eşiği azaltdıkça, algılanan daha fazla nesne görürsünüz.

Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu artırmanın kolay bir yolu daha fazla veri kullanmaktır. Aksi takdirde, model Oluşturucu 'daki **kod** adımına geçmek için **sonraki adım** bağlantısını seçin.

## <a name="add-the-code-to-make-predictions"></a>Tahminleri yapmak için kodu ekleyin

Eğitim sürecinin bir sonucu olarak iki proje oluşturulur.

- *StopSignDetectionML. ConsoleApp*: model eğitim kodunu ve örnek tüketim kodunu içeren bir C# .NET Core konsol uygulaması.
- *StopSignDetectionML. model*: giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini, eğitim sırasında en iyi gerçekleştirme modelinin kaydedilmiş sürümünü ve tahmin yapmak için çağrılan bir yardımcı sınıfı içeren .NET Standard bir sınıf kitaplığı `ConsumeModel` .

1. Model oluşturucunun kod adımında, otomatik olarak oluşturulan projeleri çözüme eklemek için **Proje Ekle** ' yi seçin.
1. *Stopsigndetection* projesinde *program. cs* dosyasını açın ve *StopSignDetectionML. model* projesine başvurmak için dosyanın en üstüne aşağıdaki using ifadesini ekleyin:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L2)]

1. Aşağıdaki [Test görüntüsünü](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/test-image1.jpeg)indirin.
1. `ModelInput` `ImageSource` Uygulamanızın yöntemi içindeki test görüntünüzün FilePath öğesine ayarlanmış özelliği ile sınıfının yeni bir örneğini oluşturun `Main` . "Merhaba Dünya" ifadesini aşağıdaki kodla değiştirin:

    [!code-csharp [InputData](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L10-L15)]

1. `Predict` `ConsumeModel` Eğitilen modeli yüklemek, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) model için bir oluşturmak ve yeni verilerde tahmine dayalı hale getirmek için sınıfından yöntemi kullanın. Aşağıdaki kodu deyimin altına ekleyin `ModelInput` :

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L15)]

1. Aşağıdaki kodu ekleyerek tahmine ait çıktıyı, etiket, koordinat ve skor dahil olmak üzere Yazdır:

    [!code-csharp [PrintResults](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L17-L18)]

1. Uygulamayı çalıştırın.

    Program tarafından oluşturulan çıkış aşağıdaki kod parçacığına benzemelidir:

    ```bash
    Predicted Boxes:
    
    Top: 89.453415, Left: 481.95343, Right: 724.8073, Bottom: 388.32385, Label: Stop-Sign, Score: 0.99539465
    ```

Tebrikler! Model Oluşturucu 'Yu kullanarak görüntülerde durma işaretlerini algılamaya yönelik bir makine öğrenimi modeli oluşturdunuz. Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/ObjectDetection_StopSigns) GitHub deposunda bulabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:

- [Model Oluşturucu senaryoları](../automate-training-with-model-builder.md#scenario)
- [ML.NET içinde ONNX kullanarak nesne algılama](object-detection-onnx.md)
