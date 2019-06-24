---
title: Otomatik makine öğrenimi ile ML.NET
description: Otomatik model seçimi ve eğitim genel bakış
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: 39e454d67f60280c6a43e3b80d788d873345ab77
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307382"
---
# <a name="automated-machine-learning-with-mlnet"></a>Otomatik makine öğrenimi ile ML.NET

Otomatik machine learning otomatik model seçimi ve eğitim gerçekleştiren ML.NET özelliğidir. Machine learning görev belirtin ve bir veri kümesi sağlayın ve otomatik ML model en iyi ölçümlerle seçer. Bunu verir:
- Tahmin uygulamanıza yüklenebilen bir model dosyası
- tahminlerde bulunmak üzere uygulama kodu
- Özellik Seçimi ve model (model anlamak) eğitimi için kullanılan kaynak kodu

> [!NOTE]
> Bu özellik şu anda Önizleme aşamasındadır ve malzeme değişiklik gösterebilir. 

Otomatik ML için machine learning şu anda sınırlı [görevleri](resources/tasks.md) ikili Sınıflandırma, çok sınıflı sınıflandırma ve regresyon. Görevlerin diğer makine öğrenimi, gelecek sürümlerde desteklenmeyecektir.

Otomatik ML kullanmanın üç yolu vardır:
1. Komut satırında ile [ML.NET CLI](automate-training-with-cli.md)
1. Bir uygulama yoluyla ile [ML API otomatik](how-to-guides/how-to-use-the-automl-api.md)
1. Bir grafik kullanıcı arabirimi ile ML.NET Model Oluşturucu
