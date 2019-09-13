---
title: ML.NET ile otomatik makine öğrenimi
description: Otomatik model seçimine ve eğitimlere genel bakış
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: da2d764e678debc78a25faeb8e48facb44fc4021
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929417"
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
