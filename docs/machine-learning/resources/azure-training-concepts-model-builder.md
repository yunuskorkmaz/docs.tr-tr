---
title: Model Oluşturucu Azure eğitim kaynakları
description: Azure Machine Learning kaynaklar Kılavuzu
ms.topic: reference
ms.date: 06/01/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 1321967cacdd373acc19923f992d30c5453ea869
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556225"
---
# <a name="model-builder-azure-training-resources"></a>Model Oluşturucu Azure eğitim kaynakları

Model Oluşturucu ile Azure 'da modelleri eğitmek için kullanılan kaynaklar hakkında daha fazla bilgi edinmenize yardımcı olacak bir kılavuz aşağıda verilmiştir.

## <a name="what-is-an-azure-machine-learning-experiment"></a>Azure Machine Learning deneme nedir?

Azure Machine Learning deneme, Azure 'da model Oluşturucu eğitimi çalıştırılmadan önce oluşturulması gereken bir kaynaktır.

Deneme, bir veya daha fazla makine öğrenimi eğitimi için yapılandırmayı ve sonuçları kapsar. Denemeleri, belirli bir çalışma alanına ait. Deneme ilk kez oluşturulduğunda, adı çalışma alanına kaydedilir. Sonraki tüm çalıştırmalar-aynı deneme adı kullanılırsa-aynı deneme kapsamında günlüğe kaydedilir. Aksi takdirde, yeni bir deneme oluşturulur.

## <a name="what-is-an-azure-machine-learning-workspace"></a>Azure Machine Learning çalışma alanı nedir?

Çalışma alanı, eğitim çalıştırmasının bir parçası olarak oluşturulan tüm Azure Machine Learning kaynakları ve yapıtlar için merkezi bir yer sağlayan bir Azure Machine Learning kaynağıdır.

Bir Azure Machine Learning çalışma alanı oluşturmak için aşağıdakiler gereklidir:

- Ad: çalışma alanınızın 3-33 karakter arasında bir adı. Adlar yalnızca alfasayısal karakterler ve kısa çizgiler içerebilir.
- Bölge: çalışma alanınızın ve kaynaklarınızın dağıtıldığı veri merkezinin coğrafi konumu. Sizin veya müşterilerinizin bulunduğu yere yakın bir konum seçmeniz önerilir.
- Kaynak grubu: bir Azure çözümü için ilgili tüm kaynakları içeren bir kapsayıcı.

## <a name="what-is-an-azure-machine-learning-compute"></a>Azure Machine Learning işlem nedir?

Azure Machine Learning işlem, eğitim için kullanılan bulut tabanlı bir Linux VM 'dir.

Bir Azure Machine Learning çalışma alanı oluşturmak için aşağıdakiler gereklidir:

- Ad: çalışma alanınızın 2-16 karakter arasında bir adı. Adlar yalnızca alfasayısal karakterler ve kısa çizgiler içerebilir.
- İşlem boyutu

    Model Oluşturucu, aşağıdaki GPU ile iyileştirilmiş işlem türlerinden birini kullanabilir:

    | Boyut | Sanal işlemci | Bellek: GiB | Geçici depolama (SSD) GiB | GPU | GPU belleği: GiB | Maksimum veri diskleri | En fazla NIC |
    |---|---|---|---|---|---|---|---|
    | Standard_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standard_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    GPU iyileştirilmiş işlem türleri hakkında daha fazla bilgi için [NC serisi LINUX VM belgelerini](/azure/virtual-machines/nc-series?bc=%252fazure%252fvirtual-machines%252flinux%252fbreadcrumb%252ftoc.json&toc=%252fazure%252fvirtual-machines%252flinux%252ftoc.json) ziyaret edin.
- İşlem önceliği

  - Düşük öncelikli: daha kısa yürütme sürelerine sahip görevlere uygundur. Kesintiler ve kullanılabilirlik olmaması olabilir. Azure 'daki daha fazla kapasitenin avantajlarından yararlandığından genellikle maliyetler daha düşüktür.
  - Adanmış: herhangi bir süre görev için uygundur, ancak özellikle uzun süreli işler. Kesintiler veya kullanılabilirlik olmamasından etkilenmez. Genellikle, görevleriniz için Azure 'da adanmış bir işlem kaynakları kümesini ayırdığından daha fazla maliyet daha yüksektir.

## <a name="training"></a>Eğitim

Azure eğitimi yalnızca model Oluşturucu görüntü sınıflandırma senaryosu için kullanılabilir. Bu modelleri eğmek için kullanılan algoritma, ResNet50 mimarisini temel alan derin bir sinir ağı. Eğitim süreci bir süre sürer ve zaman miktarı, seçilen işlem boyutuna ve veri miktarına bağlı olarak değişebilir. Visual Studio 'daki "geçerli çalışmayı Izle Azure portal" bağlantısını seçerek çalıştırmaların ilerlemesini izleyebilirsiniz.

## <a name="results"></a>Sonuçlar

Eğitim tamamlandıktan sonra, aşağıdaki son eklerle çözümünüze iki proje eklenir:

- *Consoleapp*: tahmine dayalı işlem hattı oluşturmak ve tahmin yapmak için başlangıç kodu sağlayan bir C# .NET Core konsol uygulaması.
- *Model*: giriş ve çıkış modeli verilerinin şemasını ve aşağıdaki varlıkları tanımlayan veri modellerini içeren bir C# .NET Standard uygulaması:

  - en iyi model. onnx: Open sinir Network Exchange (ONNX) biçiminde modelin serileştirilmiş bir sürümü. ONNX, ML.NET, PyTorch ve TensorFlow gibi çerçeveler arasında birlikte çalışabilirliği destekleyen AI modelleri için açık bir kaynak biçimidir.
  - bestModelMap.js: model çıkışını bir metin kategorisine eşlemek için tahminleri yaparken kullanılan kategorilerin listesi.
  - MLModel.zip: ML.NET tahmin işlem hattının seri hale getirilmiş bir sürümü, tahmine dayalı hale getirmek için model *. onnx* , dosya kullanarak çıkış ve eşleme yapmak için kullanılır `bestModelMap.json` .

## <a name="use-the-machine-learning-model"></a>Machine Learning modelini kullanma

`ModelInput` `ModelOutput` *Model* projesindeki ve sınıfları, modelin beklenen giriş ve çıkış şemasını sırasıyla tanımlar.

Bir resim sınıflandırması senaryosunda, `ModelInput` iki sütun içerir:

- `ImageSource`: Görüntü konumunun dize yolu.
- `Label`: Görüntünün ait olduğu gerçek kategori. `Label` yalnızca eğitim sırasında giriş olarak kullanılır ve tahmine dayalı hale geldiğinde sağlanması gerekmez.

`ModelOutput`İki sütun içerir:

- `Prediction`: Görüntünün tahmin edilen kategorisi.
- `Score`: Tüm kategoriler için olasılıkların listesi (en yüksek öğesine aittir `Prediction` ).

## <a name="troubleshooting"></a>Sorun giderme

### <a name="cannot-create-compute"></a>İşlem oluşturulamıyor

Azure Machine Learning işlem oluşturma sırasında bir hata oluşursa, bilgi işlem kaynağı hatalı durumda hala mevcut olabilir. Aynı ada sahip işlem kaynağını yeniden oluşturmayı denerseniz, işlem başarısız olur. Bu hatayı onarmak için aşağıdakilerden birini yapın:

- Farklı bir adla yeni işlem oluştur
- Azure portal gidin ve özgün işlem kaynağını kaldırın
