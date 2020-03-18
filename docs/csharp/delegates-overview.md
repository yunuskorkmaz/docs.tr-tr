---
title: Temsilcilere Giriş
description: Temel kavramları tanıtan ve delegeler için dil tasarımı hedeflerini tartışan bu genel bakış konusundaki temsilciler hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: fd594f77c034533a1d5aee1d8279e9b727284311
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146235"
---
# <a name="introduction-to-delegates"></a>Temsilcilere Giriş

Temsilciler .NET'te *geç bağlama* mekanizması sağlar. Geç Bağlama, arayanın algoritmanın bir bölümünü uygulayan en az bir yöntem sağladığı bir algoritma oluşturduğunuz anlamına gelir.

Örneğin, bir astronomi uygulamasındaki yıldızların listesini sıralamayı düşünün.
Bu yıldızları dünya yla olan uzaklıklarına, yıldızın büyüklüğüne ya da algılanan parlaklıklarına göre sıralamayı seçebilirsiniz.

Tüm bu durumlarda, Sıralama() yöntemi temelde aynı şeyi yapar: listedeki öğeleri bazı karşılaştırmalara göre düzenler. İki yıldızı karşılaştıran kod, sıralama sıralamalarının her biri için farklıdır.

Bu tür çözümler yarım yüzyıl boyunca yazılımda kullanılmaktadır.
C# dil temsilcisi kavramı birinci sınıf dil desteği sağlar ve kavram etrafında sınıf güvenliği sağlar.

Bu serinin ilerleyen saatlerinde göreceğiniz gibi, bu gibi algoritmalar için yazdığınız C# kodu tür güvenlidir ve türlerin bağımsız değişkenler ve iade türleri için eşleştirdiğinden emin olmak için dili ve derleyiciyi kullanır.

## <a name="language-design-goals-for-delegates"></a>Delegeler için Dil Tasarımı Hedefleri

Dil tasarımcıları sonunda delege oldu özelliği için çeşitli hedefler numaralandırılmış.

Takım, geç bağlama algoritmaları için kullanılabilecek ortak bir dil yapısı istedi. Bu, geliştiricilerin bir kavramı öğrenmesini ve aynı kavramı birçok farklı yazılım sorununda kullanmasına olanak tanır.

İkinci olarak, takım hem tek hem de çok noktaya yayın yöntemi çağrılarını desteklemek istedi. (Çok noktaya yayın delegeleri, birden çok yöntem çağrısını birbirine zincirleyen temsilcilerdir.
[Bu serinin daha sonra](delegate-class.md)örneklerini görürsünüz .)

Ekip, temsilcilerin geliştiricilerin tüm C# yapılarından beklediği aynı tür güvenliğini desteklemelerini istedi.

Son olarak, takım, bir olay deseni, temsilcilerin veya herhangi bir geç bağlama algoritmasının çok yararlı olduğu belirli bir desen olduğunu fark etti. Takım, temsilciler için kodun .NET olay deseni için temel oluşturabileceğinden emin olmak istedi.

Tüm bu çalışmaların sonucu C# ve .NET'teki temsilci ve olay desteğiydi. Bu bölümdeki kalan makaleler, dil özelliklerini, kitaplık desteğini ve temsilcilerle çalışırken kullanılan yaygın deyimleri kapsayacaktır.

Anahtar kelimeyi `delegate` ve hangi kodu oluşturduğunu öğreneceksiniz. Sınıftaki özellikler ve bu `System.Delegate` özelliklerin nasıl kullanıldığı hakkında bilgi edineceksiniz. Türde güvenli temsilciler oluşturmayı ve temsilciler aracılığıyla çağrılabilecek yöntemleroluşturmayı öğreneceksiniz. Lambda ifadelerini kullanarak delegeler ve etkinliklerle nasıl çalışacağınızı da öğreneceksiniz. Delegelerin LINQ'nun yapı taşlarından biri haline geldiği yeri göreceksiniz. Temsilcilerin .NET olay deseninin temelini nasıl oluşturduklarını ve nasıl farklı olduklarını öğreneceksiniz.

Genel olarak, temsilcilerin .NET'te programlamanın ayrılmaz bir parçası olduğunu ve çerçeve API'leriyle nasıl çalıştığını görürsünüz.

Başlayalım.

[Sonraki](delegate-class.md)
