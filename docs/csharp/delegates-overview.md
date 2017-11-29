---
title: "Temsilciler giriş"
description: "Temel kavramları tanıtır ve temsilciler dil tasarım hedefleri ele bu genel bakış konusunun temsilcileri hakkında bilgi edinin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: dd4c68fb4f960d0c2d5cbdc9e699650070cacaf1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-delegates"></a>Temsilciler giriş

[Önceki](delegates-events.md)

Temsilciler sağlayan bir *geç bağlama* .NET mekanizması. Geç bağlama burada çağıran algoritmanın bölümü uygulayan en az bir yöntem de sağlayan bir algoritma oluşturmak anlamına gelir.

Örneğin, yıldız astronomide uygulamada listesini sıralama göz önünde bulundurun.
Bu yıldız dünya veya yıldız ya da kendi algılanan parlaklığını büyüklüğünü kendi mesafe göre sıralamak tercih edebilirsiniz.

Bu durumlarda, Sort() yöntemi temelde aynı şeyi yapar: bazı karşılaştırma üzerine dayalı listesindeki öğeleri düzenler. İki yıldız karşılaştırır kod her sıralama sıralamalarını için farklıdır.

Bu tür çözümler için yarım bir century yazılımda kullanıldı.
C# dili temsilci kavram, birinci sınıf dil desteği ve tür güvenliği kavramı çevresinde sağlar.

Bu seri içinde anlatıldığı gibi böyle algoritmalar için yazma C# kodu güvenli türü ve dili ve türleri için bağımsız değişken eşleşen ve dönüş türleri emin olmak için derleyici kullanır.

## <a name="language-design-goals-for-delegates"></a>Temsilciler için dil tasarım hedefleri

Dil tasarımcıları sonunda temsilciler hale geldi özelliği için çeşitli hedefleri numaralandırılır.

Takım herhangi geç bağlama algoritmaları için kullanılan ortak bir dil yapısı istedik. Geliştiricilerin bir kavram öğrenmek ve bu aynı kavram arasında birçok farklı yazılım sorunlarını kullanmak sağlar.

İkinci olarak, hem tek ve çok noktaya yayın yöntem çağrılarını desteklemek takım istedik. (Çok noktaya yayın temsilcileri temsilciler birden çok yöntem birlikte zincirlenen burada içindir. Örnekler görürsünüz [bu serideki sonraki](delegate-class.md). 

Takım tüm C# yapılarını geliştiriciler beklediğiniz aynı tür güvenliği desteklemek için temsilciler istedik. 

Son olarak, bir olay desen belirli bir desene olduğunu takım tanınan burada temsilcileri ya da herhangi bir geç bağlama algoritma) çok kullanışlıdır. Temsilciler kodunu .NET olay desenini temel sağlayabilir emin olmak takım istedik.

Tüm iş C# ve .NET temsilci ve olay desteği olduğunu sonucu. Bu bölümdeki kalan makaleleri dil özellikleri, kitaplık desteği ve temsilciler ile çalışırken, kullanılan ortak deyimleri ele alınacaktır.

Hakkında bilgi edineceksiniz `delegate` anahtar sözcüğü ve ne kod oluşturur. Özellikler hakkında bilgi edineceksiniz `System.Delegate` sınıfı ve bu özellikleri nasıl kullanılır. Türü güvenli temsilciler oluşturma ve temsilciler çağrılan yöntem oluşturulacağını öğreneceksiniz. Lambda ifadeleri kullanarak Temsilciler ve olaylar ile çalışmaya nasıl da öğreneceksiniz. Burada temsilciler yapı taşları birini LINQ hale görürsünüz. Temsilciler .NET olay düzeni için temel şeklini ve nasıl farklı bilgi edineceksiniz.

Genel olarak, nasıl temsilciler .NET ile programlama ve API framework ile çalışma ayrılmaz bir parçası olan görürsünüz.

Haydi başlayalım.

[Sonraki](delegate-class.md)
