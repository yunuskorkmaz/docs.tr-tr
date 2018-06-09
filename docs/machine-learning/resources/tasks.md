---
title: Makine öğrenimi görevlerini
description: İçinde ML.NET desteklenen görev öğrenme farklı makine keşfedin.
ms.date: 06/04/2018
author: aditidugar
ms.author: johalex
ms.openlocfilehash: 22249ac2d275a4168dbd8b03b90d9698fe90f2d1
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "35017304"
---
# <a name="machine-learning-tasks"></a>Makine öğrenimi görevlerini

Machine learning modeli oluştururken, ilk verilerinizle elde etmek umarak tanımlamanız gerekir. Sonra görev durumunuz için öğrenme sağ makine seçebilirsiniz. Aşağıdaki listede farklı makine öğrenimi aralarından seçim yapabileceğiniz görevleri açıklar ve bazı yaygın kullanım. 

> [!NOTE]
> ML.NET şu anda önizlemede değil. Tüm makine öğrenimi görevlerini şu anda desteklenir. Belirli bir görev için bir istek göndermek için bir sorun açın [dotnet/machinelearning depo](https://github.com/dotnet/machinelearning/issues).

> [!NOTE]
> Şu anda ML.NET makine öğrenimi görevlerini görüntülerle desteklemez. Destek gelecek sürümlerde eklenir. 

## <a name="binary-classification"></a>ikili sınıflandırma

A [denetimli makine öğrenme](glossary.md#supervised-machine-learning) veri örneği ait olduğu iki sınıf (kategori) tahmin etmek için kullanılan görev. Bir sınıflandırma algoritmasıdır giriş etiketli örnekler, her etiket 0 veya 1 bir tamsayı olduğu kümesidir. Bir ikili sınıflandırma algoritmasıdır çıktısını yeni etiketlenmemiş örnekleri sınıfının tahmin etmek için kullanabileceğiniz bir sınıflandırıcı ' dir. İkili sınıflandırma senaryoları örnekleri şunlardır:

* [Twitter açıklamaların anlama düşünceleri](../tutorials/sentiment-analysis.md) "pozitif" veya "negatif" olarak.
* Bir süre bekleyin veya belirli bir Hastalık olup tanılama.
* İstenmeyen posta"veya"olarak bir e-posta işaretlemek için bir kararı.

## <a name="multi-class-classification"></a>Birden çok sınıf sınıflandırma

A [denetimli makine öğrenme](glossary.md#supervised-machine-learning) veri örneği sınıfı (kategori) tahmin etmek için kullanılan görev. Bir sınıflandırma algoritmasıdır giriş etiketli örnekler kümesidir. Her etiket 0 ile k-1, arasında bir tamsayı k sınıfların sayısı olduğu. Bir sınıflandırma algoritmasıdır çıktısını yeni etiketlenmemiş örnekleri sınıfının tahmin etmek için kullanabileceğiniz bir sınıflandırıcı ' dir. Birden çok sınıf sınıflandırma senaryoları örnekleri şunlardır:

* Köpek bir "Siberian Husky", "Altın alıcısı", "Şu dar", vb. olarak belirleniyor.
* Film anlama "pozitif", "nötr" veya "negatif" inceler.
* Otel kategorilere ayrılması "Konum", "price", "cleanliness" vb. inceler.

## <a name="regression"></a>regresyon

A [denetimli makine öğrenme](glossary.md#supervised-machine-learning) ilgili özellik kümesinden etiket değeri tahmin etmek için kullanılan görev. Etiket herhangi bir gerçek değer olabilir ve bir sınırlı değil sınıflandırma görevleri olduğu gibi değerlerin ayarlanır. Regresyon algoritmaları modeli etiketi özellik değerleri olarak nasıl değiştireceğini belirlemek için ilgili özellikleri etikette bağımlılığı çeşitli. Örnekler etiketleri bilinen değerleri içeren bir regresyon algoritmasıdır. giriş kümesidir. Bir regresyon algoritmasıdır. çıkış herhangi yeni bir giriş özellikleri kümesi için etiket değeri tahmin etmek için kullanabileceğiniz bir işlev değil. Regresyon senaryoları örnekleri şunlardır:

* Yatak, konum veya boyut sayısı gibi ev özniteliklerini temel alarak ev fiyatları tahmin etmeye.
* Geçmiş verileri ve geçerli Pazar eğilimleri göre gelecekteki hisse senedi fiyatları tahmin etmeye.
* Satış bütçeleri reklam dayalı bir ürünün tahmin.

> [!NOTE]
> Şu anda ML.NET hala zaman serisi içeren regresyon görevleri için destek oluşturuyor.

## <a name="clustering"></a>Kümeleme

Bir [Denetimsiz makine öğrenme](glossary.md#unsupervised-machine-learning) benzer özelliklere içeren kümeler halinde veri grubu örnekleri için kullanılan görev. Kümeleme Ayrıca, değil mantıksal olarak türetilen bir veri kümesinde ilişkileri tanımlamak için gözatma veya basit gözlem tarafından kullanılabilir. Girişleri ve çıkışları kümeleme algoritması, seçilen metodolojiye bağlıdır. Dağıtım, kütle merkezini, bağlantı veya yoğunluğu dayalı yaklaşım alabilir. ML.NET şu anda K-ortalamaları kümeleme kullanarak kütle merkezini tabanlı bir yaklaşım destekler. Kümeleme senaryoları örnekleri şunlardır:

* Alışkanlıklarınıza ve Otel seçimler özelliklerine göre otel konuklar parçalarını anlama.
* Müşteri kesimine ve demografisine hedeflenen reklam kampanyası oluşturmanıza yardımcı olmak için tanımlayıcı.
* Ölçümleri üretim alarak envanteri kategorilere ayrılması.

## <a name="anomaly-detection-coming-soon"></a>Anomali algılama (*yakında*)

## <a name="ranking-coming-soon"></a>Sıralama (*yakında*)

## <a name="recommendation-coming-soon"></a>Öneri (*yakında*)

