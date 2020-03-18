---
title: 'Öğretici: Model Oluşturucu ile sağlık ihlallerini sınıflandırma'
description: Bu öğretici, San Francisco'daki restoran sağlık ihlali şiddetini sınıflandırmak için ML.NET Model Builder kullanarak çok sınıflı bir sınıflandırma modelinin nasıl oluşturulabildiğini göstermektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: e94313277a025d482105a6d78b6608d4df442c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185829"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>Öğretici: Model Builder ile restoran sağlık ihlallerinin şiddetini sınıflandırmak

Sağlık denetimleri sırasında bulunan restoran ihlallerinin risk düzeyini kategorilere ayırmak için Model Builder'ı kullanarak çok sınıflı bir sınıflandırma modeli oluşturmayı öğrenin.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:

> [!div class="checklist"]
>
> - Verileri hazırlama ve anlama
> - Bir senaryo seçin
> - Veritabanından veri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Öngörüler için modeli kullanma

> [!NOTE]
> Model Oluşturucu şu anda Önizleme'de.

## <a name="prerequisites"></a>Önkoşullar

Ön koşullar ve yükleme yönergeleri listesi için [Model Oluşturucu yükleme kılavuzunu ziyaret edin.](../how-to-guides/install-model-builder.md)

## <a name="model-builder-multiclass-classification-overview"></a>Model Builder çok sınıflı sınıflandırmaya genel bakış

Bu örnek, Model Builder ile oluşturulmuş bir makine öğrenme modeli kullanarak sistem durumu ihlali riskini kategorize eden bir C# .NET Core konsol uygulaması oluşturur. Bu öğreticinin kaynak kodunu [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub deposunda bulabilirsiniz.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "RestaurantViolations" adlı bir **C# .NET Core konsol uygulaması** oluşturun. Çözüm **ve projeyi aynı dizindeki yerleştir** çözümve proje **işaretsiz** olduğundan emin olun (VS 2019) veya **çözüm için create directory** (VS 2017) **işaretlenir.**

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

> Makine öğrenimi modelini eğitmek ve değerlendirmek için kullanılan veri seti aslında [San Francisco Halk Sağlığı Restoran Güvenlik Puanları Bölümü'ndendir.](https://www.sfdph.org/dph/EH/Food/score/default.asp) Kolaylık sağlamak için, veri kümesi yalnızca modeli eğitmek ve tahminlerde bulunmak la ilgili sütunları içerecek şekilde yoğunlaştırılmıştır. [Veri kümesi](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0)hakkında daha fazla bilgi edinmek için aşağıdaki web sitesini ziyaret edin.

[Restoran Güvenlik Puanları veri setini indirin](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) ve zip'ini çıkarın.

Veri kümesindeki her satır, Sağlık Bakanlığı'nın teftişi sırasında gözlemlenen ihlallerle ilgili bilgiler ve bu ihlallerin halk sağlığı ve güvenliği nezdinde mevcut olduğu tehdidin risk değerlendirmesini içerir.

| Denetim Tipi | İhlal Açıklaması | Risk Kategorisi |
| --- | --- | --- |
| Rutin - Planlanmamış | Yetersiz olarak temizlenmiş veya dezenfekte edilmiş gıda temas yüzeyleri | Orta Risk |
| Yeni Sahiplik | Yüksek riskli haşarat istilası | Yüksek Risk |
| Rutin - Planlanmamış | Temiz olmayan veya düzgün depolanmayan veya yetersiz dezenfektan olmayan bezleri silme | Düşük Risk |

- **InspectionType**: denetim türü. Bu ya yeni bir kuruluş, rutin bir denetim, bir şikayet muayene ve diğer birçok tür için ilk kez muayene olabilir.
- **İhlal Açıklaması**: Denetim sırasında bulunan ihlalin açıklaması.
- **RiskKategorisi**: bir ihlalin halk sağlığı ve güvenliği için oluşturduğu risk şiddeti.

Tahmin `label` etmek istediğiniz sütundur. Bir sınıflandırma görevi gerçekleştirirken, amaç bir kategori (metin veya sayısal) atamaktır. Bu sınıflandırma senaryosunda, ihlalin önem derecesidüşük, orta veya yüksek risk değeria atanır. Bu nedenle, **RiskKategorisi** etikettir. Modeli `features` tahmin etmek için verdiğiniz `label`girdiler. Bu durumda, **Denetim Türü** ve **İhlal Açıklaması** **RiskKategorisi'ni**tahmin etmek için özellik veya girdi olarak kullanılır.

## <a name="choose-a-scenario"></a>Bir senaryo seçin

![Model Oluşturucu sihirbazı Visual Studio'da](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Modelinizi eğitmek için Model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim inizi seçin. Bu durumda, senaryo *Sorun*Sınıflandırmasıdır.

1. **Solution Explorer'da** *RestaurantViolations* projesine sağ tıklayın ve**Machine Learning** **Ekle'yi** > seçin.
1. Bu örnek için senaryo çok sınıflı sınıflandırmadır. Model Oluşturucu'nun *Senaryo* adımında, **Sorun Sınıflandırma** senaryosunu seçin.

## <a name="load-the-data"></a>Verileri yükleme

Model Oluşturucu, SQL Server veritabanından veya `csv` yerel `tsv` bir dosyadaki veya biçimdeki verileri kabul eder.

1. Model Oluşturucu aracının veri adımında, veri kaynağı açılır tarafından **SQL Server'ı** seçin.
1. **SQL Server veritabanına bağlan** metin kutusunun yanındaki düğmeyi seçin.
    1. Veri **Seç** iletişim kutusunda **Microsoft SQL Server Database File'yi**seçin.
    1. **Her Zaman bu seçim** onay kutusunu kullan denetiminden kaldırın ve Devam **et'i**seçin.
    1. Bağlantı **Özellikleri** iletişim kutusunda **Gözat'ı** seçin ve indirilen *RestaurantScores.mdf* dosyasını seçin.
    1. **Tamam'ı**seçin.
1. **Tablo Adı** açılır tarafından **Ihlaller'i** seçin.
1. **Açılan düşüşü tahmin etmek (Etiketlemek) için Sütundaki RiskKategorisi'ni** seçin. **RiskCategory**
1. **Giriş Sütunları (Özellikler)** açılır durumda denetlenen varsayılan sütun seçimlerini, **Denetim Türü** ve **ViolationDescription'ı**bırakın.
1. Model Oluşturucu'da bir sonraki adıma geçmek için **Tren** bağlantısını seçin.

## <a name="train-the-model"></a>Modeli eğitme

Bu öğreticide konu sınıflandırma modelini eğitmek için kullanılan makine öğrenimi görevi çok sınıflı sınıflandırmadır. Model eğitim süreci sırasında Model Builder, veri setiniz için en iyi performans gösteren modeli bulmak için farklı çok sınıflı sınıflandırma algoritmaları ve ayarları kullanarak ayrı modeller eğitir.

Modelin eğitilmesi için gereken süre veri miktarıyla orantılıdır. Model Oluşturucu, veri kaynağınızın boyutuna bağlı **olarak, eğitme Süresi (saniye)** için varsayılan bir değer seçer.

1. Model Oluşturucu, **(saniye) eğitmek için Zamanın** değerini 10 saniyeye ayarlasa da, bunu 30 saniyeye yükseltin. Daha uzun bir süre için eğitim Model Builder algoritmaları ve en iyi modeli arama parametrelerinin kombinasyonu daha fazla sayıda keşfetmek için izin verir.
1. **Start Training'i**seçin.

    Eğitim süreci boyunca, ilerleme verileri tren `Progress` adımı bölümünde görüntülenir.

    - **Durum,** eğitim sürecinin tamamlanma durumunu görüntüler.
    - **En iyi doğruluk,** Model Builder tarafından şimdiye kadar bulunan en iyi performans gösteren modelin doğruluğunu görüntüler. Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin ettiği anlamına gelir.
    - **En iyi algoritma,** Model Builder tarafından şimdiye kadar bulunan en iyi performans gösteren algoritmanın adını görüntüler.
    - **Son algoritma,** modeli eğitmek için Model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.

1. Eğitim tamamlandıktan sonra, bir sonraki adıma geçmek için **Değerlendir** bağlantısını seçin.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Eğitim adımının sonucu en iyi performansa sahip bir modeldir. Model Oluşturucu'nun değerlendirme adımında, çıkış **bölümü, Best Model** **Doğruluğu'ndaki**ölçümlerle birlikte En İyi Model girişinde en iyi performans gösteren model tarafından kullanılan algoritmayı içerir. Ayrıca, keşfedilen ve ölçümleri görüntülenen en fazla beş model içeren bir özet tablo.

Doğruluk ölçümlerinizden memnun değilseniz, model doğruluğunu iyileştirmeyi denemenin bazı kolay yolları, modeli eğitmek veya daha fazla veri kullanmak için gereken süreyi artırmakiçindir. Aksi takdirde, Model Oluşturucu'da son adıma geçmek için **kod** bağlantısını seçin.

## <a name="add-the-code-to-make-predictions"></a>Tahminlerde bulunmak için kodu ekleme

Eğitim süreci sonucunda iki proje oluşturulur.

- RestaurantViolationsML.ConsoleApp: Model eğitimi ve örnek tüketim kodunu içeren bir C# .NET Core Console uygulaması.
- RestaurantViolationsML.Model: Giriş ve çıktı modeli verilerinin şemasını tanımlayan veri modellerini, eğitim sırasında en iyi performans gösteren modelin kaydedilmiş sürümünü `ConsumeModel` ve tahminde bulunmak için çağrılan yardımcı sınıfı içeren bir .NET Standart sınıf kitaplığı.

1. Model Oluşturucu'nun kod adımında, çözüme otomatik oluşturulan projeleri eklemek için **Projeler Ekle'yi** seçin.
1. *RestaurantViolations* projesinde *Program.cs* dosyasını açın.
1. *RestaurantViolationsML.Model* projesine başvurmak için aşağıdaki ifadesini ekleyin:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. Modeli kullanarak yeni veriler üzerinde bir tahminde bulunmak `ModelInput` için, `Main` uygulama yöntemi içinde sınıfın yeni bir örneğini oluşturun. Risk kategorisinin girişin bir parçası olmadığını unutmayın. Bunun nedeni, modelin bunun için tahmin oluşturmasıdır.

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. Sınıftaki `Predict` `ConsumeModel` yöntemi kullanın. Yöntem, `Predict` eğitilen modeli yükler, model için bir model [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) oluşturur ve yeni veriler üzerinde öngörülerde bulunmak için kullanır.

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. Uygulamayı çalıştırın.

    Program tarafından oluşturulan çıktı aşağıdaki snippet benzer görünmelidir:

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

Oluşturulan projeleri başka bir çözüm içinde daha sonra göndermeniz gerekiyorsa, bunları `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizinin içinde bulabilirsiniz.

Tebrikler! Model Oluşturucu'yu kullanarak sağlık ihlali riskini kategorilere ayırmak için başarılı bir makine öğrenme modeli oluşturmuşsunuz. Bu öğreticinin kaynak kodunu [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub deposunda bulabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

Bu eğitimde bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:

- [Model Oluşturucu Senaryolar](../automate-training-with-model-builder.md#scenarios)
- [Çok Sınıflı Sınıflandırma](../resources/glossary.md#multiclass-classification)
- [Çok Sınıflı Sınıflandırma Modeli Ölçümleri](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
