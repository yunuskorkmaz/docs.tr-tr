---
title: Machine learning değerlendirilecek ölçümlerini hesapla kalite - ML.NET modeli
description: Değerlendirmek ve makine öğrenimi model kalitesi ML.NET ile doğrulamak için ölçümlerini hesapla öğrenin
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 6fd4dfab6104b4398918e42ed70584b04169a8c1
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297676"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a>Machine learning değerlendirilecek ölçümlerini hesapla kalite - ML.NET modeli

Nasıl modeli eğitme sonra kalitesini değerlendirmek? Machine learning görev kalite değerlendirme için ölçümleri sunar.

Görevin karşılık gelen 'context', aşağıdaki örnekte olduğu gibi model değerlendirmek için kullanabilirsiniz:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```