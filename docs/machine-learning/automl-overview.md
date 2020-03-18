---
title: ML.NET ile otomatik makine öğrenimi
description: Otomatik model seçimi ve eğitimine genel bakış
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: acd6cae71d2d5d79209a77d34175e7f1b3c1ee35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849360"
---
# <a name="automated-machine-learning-with-mlnet"></a>ML.NET ile otomatik makine öğrenimi

Otomatik makine öğrenimi, otomatik model seçimi ve eğitimi gerçekleştiren ML.NET bir özelliğidir. Makine öğrenimi görevini belirtir ve bir veri kümesi tedarik eder ve otomatik ML modeli en iyi ölçümlere sahip olarak seçer. Bu çıkışlar:

- tahmin uygulamanıza yüklenebilecek bir model dosyası
- tahminlerde bulunmak için uygulama kodu
- özellik seçimi ve model eğitimi için kullanılan kaynak kodu (modeli anlamak için)

> [!NOTE]
> Bu özellik şu anda Önizleme'de dir ve malzeme değişebilir.

Otomatik ML şu anda ikili sınıflandırma, çok sınıflı sınıflandırma ve regresyon makine öğrenme [görevleri](resources/tasks.md) ile sınırlıdır. Diğer makine öğrenimi görevleri gelecek sürümlerde desteklenecektir.

Otomatik ML kullanmanın üç yolu vardır:

1. [ML.NET Model Builder](automate-training-with-model-builder.md) ile grafik kullanıcı arabirimi ile
1. Komut satırında, [cli ML.NET](automate-training-with-cli.md)
1. Otomatik [ML API](how-to-guides/how-to-use-the-automl-api.md) ile bir uygulama ile
