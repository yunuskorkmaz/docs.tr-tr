---
title: Model Oluşturucu Azure Eğitim Kaynakları
description: Azure Machine Learning için bir kaynak rehberi
ms.topic: reference
ms.date: 02/27/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a19e13955d0eaea344109eb817f3a3959c3dd883
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185816"
---
# <a name="model-builder-azure-training-resources"></a>Model Oluşturucu Azure Eğitim Kaynakları

Aşağıda, Model Oluşturucu ile Azure modellerini eğitmek için kullanılan kaynaklar hakkında daha fazla bilgi edinmenize yardımcı olacak bir kılavuz vekılavuz vekılavuz yer almaktadır.

## <a name="what-is-an-azure-machine-learning-experiment"></a>Azure Machine Learning denemesi nedir?

Azure Machine Learning denemesi, Azure'da Model Oluşturucu eğitimini çalıştırmadan önce oluşturulması gereken bir kaynaktır.

Deneme, bir veya daha fazla makine öğrenimi eğitimi için yapılandırmayı ve sonuçları kapsüller. Denemeler belirli bir çalışma alanına aittir. Bir deneme ilk oluşturulduğunda, adı çalışma alanına kaydedilir. Sonraki tüm çalıştırmalar -aynı deneme adı kullanılırsa- aynı denemenin parçası olarak günlüğe kaydedilir. Aksi takdirde, yeni bir deneme oluşturulur.

## <a name="what-is-an-azure-machine-learning-workspace"></a>Azure Makine Öğrenimi çalışma alanı nedir?

Çalışma alanı, tüm Azure Machine Learning kaynakları ve eğitim çalışmasının bir parçası olarak oluşturulan yapılar için merkezi bir yer sağlayan bir Azure Machine Learning kaynağıdır.

Azure Machine Learning çalışma alanı oluşturmak için aşağıdakiler gereklidir:

- Adı: 3-33 karakter arasında çalışma alanı için bir ad. Adlar yalnızca alfasayısal karakterler ve tireler içerebilir.
- Bölge: Çalışma alanınızın ve kaynaklarınızın dağıtıldığı veri merkezinin coğrafi konumu. Sizin veya müşterilerinizin bulunduğu yere yakın bir konum seçmeniz önerilir.
- Kaynak grubu: Azure çözümü için ilgili tüm kaynakları içeren kapsayıcı.

## <a name="what-is-an-azure-machine-learning-compute"></a>Azure Machine Learning bilgi işlem nedir?

Azure Machine Learning bilgi işlem, eğitim için kullanılan bulut tabanlı bir Linux VM'dir.

Azure Machine Learning çalışma alanı oluşturmak için aşağıdakiler gereklidir:

- Ad: Çalışma alanınız için 2-16 karakter arasında bir ad. Adlar yalnızca alfasayısal karakterler ve tireler içerebilir.
- İşlem boyutu

    Model Oluşturucu aşağıdaki GPU için optimize edilmiş bilgi işlem türlerinden birini kullanabilir:

    | Boyut | Sanal işlemci | Bellek: GiB | Geçici depolama (SSD) GiB | GPU | GPU bellek: GiB | Maksimum veri diskleri | En fazla NIC |
    |---|---|---|---|---|---|---|---|
    | Standard_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standard_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    GPU optimize edilmiş bilgi işlem türleri hakkında daha fazla bilgi için [NC serisi Linux VM belgelerini](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) ziyaret edin.

## <a name="training"></a>Eğitim

Azure'da eğitim yalnızca Model Oluşturucu görüntü sınıflandırma senaryosu için kullanılabilir. Bu modelleri eğitmek için kullanılan algoritma, ResNet50 mimarisine dayalı bir Derin Sinir Ağıdır. Eğitim süreci biraz zaman alır ve seçilen bilgi işlemin boyutuna ve veri miktarına bağlı olarak zaman değişebilir. Bir model ilk kez eğitildiğinde, kaynakların sağlanması gerektiği için biraz daha uzun bir eğitim süresi bekleyebilirsiniz. Visual Studio'daki "Azure portalında geçerli çalıştırmayı izle" bağlantısını seçerek koşularınızın ilerlemesini izleyebilirsiniz.

## <a name="results"></a>Sonuçlar

Eğitim tamamlandıktan sonra, aşağıdaki son eklerle çözümünüze iki proje eklenir:

- *ConsoleApp*: Tahmin hattını oluşturmak ve tahminlerde bulunmak için başlangıç kodu sağlayan C# .NET Core konsol uygulaması.
- *Model*: Giriş ve çıktı modeli verilerinin şemalarını tanımlayan veri modellerini ve aşağıdaki varlıkları içeren C# .NET Standard uygulaması:

  - bestModel.onnx: Açık Nöral Ağ Değişimi (ONNX) formatında modelin serileştirilmiş bir sürümü. ONNX, ML.NET, PyTorch ve TensorFlow gibi çerçeveler arasında birlikte çalışabilirliği destekleyen AI modelleri için açık kaynak koda dayalı bir biçimdir.
  - bestModelMap.json: Model çıktısını bir metin kategorisiyle eşlemek için öngörülerde bulunurken kullanılan kategorilerin listesi.
  - MLModel.zip: `bestModelMap.json` dosyayı kullanarak öngörüler ve haritalar çıkışları yapmak için model *bestModel.onnx* serileştirilmiş sürümünü kullanan ML.NET tahmin ardışık bir seri sürümü.

## <a name="use-the-machine-learning-model"></a>Makine öğrenme modelini kullanma

Model `ModelInput` `ModelOutput` projesindeki *Model* ve sınıflar, modelin beklenen girdi ve çıktısının şemasını tanımlar.

Görüntü sınıflandırma senaryosunda `ModelInput` iki sütun bulunur:

- `ImageSource`: Görüntü konumunun dize yolu.
- `Label`: Resmin ait olduğu gerçek kategori. `Label`yalnızca eğitim ve öngörüler yaparken sağlanması gerekmez bir giriş olarak kullanılır.

İki `ModelOutput` sütun içerir:

- `Prediction`: Görüntünün öngörülen kategorisi.
- `Score`: Tüm kategoriler için olasılıklar listesi (en yüksek `Prediction`olana aittir).

## <a name="troubleshooting"></a>Sorun giderme

### <a name="cannot-create-compute"></a>İşlem oluşturamıyor

Azure Machine Learning bilgi işlem oluşturma sırasında bir hata oluşursa, bilgi işlem kaynağı hata lı bir durumda hala bulunabilir. Aynı ada sahip bilgi işlem kaynağını yeniden oluşturmaya çalışırsanız, işlem başarısız olur. Bu hatayı düzeltmek için aşağıdakileri de:

- Farklı bir adla yeni işlem oluşturma
- Azure portalına gidin ve özgün bilgi işlem kaynağını kaldırın
