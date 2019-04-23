---
title: Temsilcilere giriş
description: Temel kavramları tanıtır ve temsilciler için dil tasarım hedefleri ele alınmaktadır genel bakış bölümüne temsilciler hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: 84e8bf8a03bd529d9c06ad049530c19daa380065
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979062"
---
# <a name="introduction-to-delegates"></a>Temsilcilere giriş

[Önceki](delegates-events.md)

Temsilciler sağlayan bir *geç bağlama* .NET mekanizması. Geç bağlama burada çağıran uygulayan algoritma parçası en az bir yöntemi de sağlayan bir algoritma oluşturmak anlamına gelir.

Örneğin, bir yıldız astronomi uygulamada listesini sıralama göz önünde bulundurun.
Bu yıldız dünya ya da büyüklük yıldız ya da kendi algılanan parlaklık kendi uzaklık olarak sıralamak tercih edebilirsiniz.

Bu durumlarda, Sort() yöntemi temelde aynı şeyi yapar: bazı karşılaştırma üzerine dayalı listesindeki öğeleri düzenler. İki yıldız karşılaştıran kod her sıralama sıralamalarının için farklıdır.

Bu çözüm türlerini yazılımda bir yarım yüzyıl için kullanılır.
C# Birinci sınıf dil desteği ve tür güvenliği kavramı çevresinde dil temsilci kavramı sağlar.

Bu seride anlatıldığı gibi C# algoritmalar için bu tür kullanımı uyumlu ve dilinden yararlanır ve derleyicinin sağlamak türleri eşleştirmek için bağımsız değişkenler ve dönüş türleri gibi kodları.

## <a name="language-design-goals-for-delegates"></a>Temsilciler için dil tasarım hedefleri

Dil tasarımcıları sonunda temsilciler dönüştü özelliği için çeşitli hedefleri numaralandırılır.

Takım tüm geç bağlama algoritmaları için kullanılabilecek bir ortak dil yapısı istiyordu. Bir kavram ve aynı bu kavramı arasında birçok farklı yazılım sorunlarını kullanmak geliştiricilerin sağlar.

İkinci olarak, hem tek ve çok noktaya yayın yöntem çağrıları desteklemek takım istiyordu. (Birden çok yöntem çağrılarını birlikte zincire temsilciler çok noktaya yayın temsilcileri içindir. Örnekler göreceksiniz [bu serideki sonraki](delegate-class.md).) 

Takım istediği geliştiriciler tümünden beklediğiniz aynı tür güvenliği desteklemek için temsilciler C# oluşturur. 

Son olarak, takım temsilcileri ya da geç herhangi bir bağlama algoritma çok yararlı olduğu bir olay deseni belirli bir düzeni olduğunu tanınır. Temsilciler için kod temeli için .NET olay deseni sağlayabilir takım sağlamaktı.

Tüm iş sonucu temsilci ve olay desteği olan C# ve .NET. Bu bölümdeki diğer makaleleri dil özellikleri, kitaplık desteği ve temsilciler ile çalışırken, kullanılan ortak deyimleri ele alınacaktır.

Hakkında bilgi edineceksiniz `delegate` anahtar sözcüğü ve hangi kod oluşturur. Özellikleri hakkında bilgi edineceksiniz `System.Delegate` sınıfı ve bu özelliklerden nasıl kullanılır. Tür güvenli temsilci oluşturmak nasıl ve temsilciler aracılığıyla çağrılan yöntemlerden oluşturulacağını öğreneceksiniz. Lambda ifadeleri kullanarak, temsilciler ve olaylar ile çalışma konusunda da öğreneceksiniz. Burada temsilciler biri yapı taşlarını LINQ için haline görürsünüz. Temsilciler .NET olay deseni için temel şeklini ve nasıl farklı olduğunu öğreneceksiniz.

Genel olarak, temsilciler .NET programlama ve framework API'ları ile çalışma bütünleyici şeklini görürsünüz.

Haydi başlayalım.

[Next](delegate-class.md)
