---
title: ML.NET ile otomatik makine öğrenimi
description: Otomatik model seçimine ve eğitimlere genel bakış
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: c6c369dc0b0375f180d33d85ef320ddb24102f3e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740103"
---
# <a name="automated-machine-learning-with-mlnet"></a>ML.NET ile otomatik makine öğrenimi

Otomatik makine öğrenimi, otomatik model seçme ve eğitim gerçekleştiren bir ML.NET özelliğidir. Machine Learning görevini belirtirsiniz ve bir veri kümesi sağlarsınız ve otomatik ML modeli en iyi ölçülerle seçer. It çıkışları:

- tahmin uygulamanıza yüklenebilen bir model dosyası
- tahminleri yapmak için uygulama kodu
- Özellik seçimi ve model eğitimi için kullanılan kaynak kodu (modeli anlamak için)

> [!NOTE]
> Bu özellik şu anda önizleme aşamasındadır ve malzemeler değişebilir.

Otomatik ML Şu anda ikili sınıflandırmanın makine öğrenimi [görevleriyle](resources/tasks.md) , birden çok Lass sınıflandırmasıyla ve gerileme ile sınırlıdır. Diğer makine öğrenimi görevleri sonraki sürümlerde desteklenecektir.

Otomatikleştirilmiş ML kullanmanın üç yolu vardır:

1. Grafik Kullanıcı arabirimiyle, [ml.net model Oluşturucu](automate-training-with-model-builder.md) ile
1. Komut satırında, [ml.net CLI](automate-training-with-cli.md) ile
1. [OTOMATIKLEŞTIRILMIŞ ml API 'si](how-to-guides/how-to-use-the-automl-api.md) ile bir uygulama aracılığıyla
