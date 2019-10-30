---
title: Temsilcilere Giriş
description: Bu genel bakış konusunun, temel kavramları tanıtan ve temsilciler için dil tasarımı hedeflerini tartışarak Temsilciler hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: deff297ccce6cd14a7cd21c49638a9c6030a9996
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037410"
---
# <a name="introduction-to-delegates"></a>Temsilcilere Giriş

Temsilciler, .NET ' te bir *geç bağlama* mekanizması sağlar. Geç bağlama, çağıranın, algoritmanın bir kısmını uygulayan en az bir yöntem sağladığı bir algoritma oluşturduğunuz anlamına gelir.

Örneğin, bir astronomi uygulamasındaki yıldızın bir listesini sıralamayı düşünün.
Bu yıldızları Dünya uzaklığına veya yıldızın büyüklüğüne göre ya da algılanan parlaklığını göre sıralamayı tercih edebilirsiniz.

Tüm bu durumlarda, Sort () yöntemi temelde aynı şeyi yapar: listedeki öğeleri, bazı karşılaştırmaya göre düzenler. İki yıldızı karşılaştıran kod, sıralama sıralarında her biri için farklıdır.

Bu tür çözümler yazılımda yarı bir yüzyıl için kullanılmıştır.
C# Dil temsilcisi kavramı ilk sınıf dil desteğini sağlar ve kavram etrafında güvenlik yazın.

Bu serinin ilerleyen kısımlarında göreceğiniz gibi, bu gibi algoritmalar C# için yazdığınız kod tür güvenlidir ve türlerin bağımsız değişkenlerle ve dönüş türleriyle eşleşmesini sağlamak için dilin ve derleyicinin yararlanır.

## <a name="language-design-goals-for-delegates"></a>Temsilciler için dil tasarımı hedefleri

Dil tasarımcıları, son olarak temsilci haline gelen özellik için birkaç amaç numaralandırmış.

Ekip, herhangi bir geç bağlama algoritması için kullanılabilecek ortak bir dil yapısı istedi. Bu, geliştiricilerin tek bir kavram öğrenmesine ve aynı kavramı birçok farklı yazılım sorunu üzerinde kullanmasına olanak sağlar.

İkincisi, takım hem tek hem çok noktaya yayın yöntemi çağrılarını desteklemek istedi. (Çok noktaya yayın temsilcileri, birden çok yöntem çağrısı zincirlenen temsilcidir. [Bu serinin ilerleyen kısımlarında](delegate-class.md)örnekleri görürsünüz.) 

Ekip, geliştiricilerin tüm C# yapılar için beklediği tür güvenliğini desteklemek için temsilciler istedi. 

Son olarak, takım bir olay deseninin temsilcilerin veya herhangi bir geç bağlama algoritmasının çok faydalı olduğu belirli bir model olduğunu kabul eder. Ekip, temsilcilerle ilgili kodun .NET olay deseninin temelini sağlayabildiğinden emin olmak istedi.

Bu çalışmanın sonucu, C# ve .net sürümündeki temsilci ve olay desteiydi. Bu bölümdeki diğer makaleler dil özelliklerini, kitaplık desteğini ve temsilcilerle çalışırken kullanılan yaygın deyimleri kapsar.

`delegate` anahtar sözcüğünü ve ürettiği kodu öğrenirsiniz. `System.Delegate` sınıftaki özellikler ve bu özelliklerin nasıl kullanıldığı hakkında bilgi edineceksiniz. Tür güvenli temsilciler oluşturmayı ve temsilciler aracılığıyla çağrılabilecek Yöntemler oluşturmayı öğreneceksiniz. Ayrıca lambda ifadeleri kullanarak temsilcilerle ve olaylarla nasıl çalışacağınızı öğreneceksiniz. Temsilcilerin LINQ için yapı taşlarından birine nerede geldiğini görürsünüz. Temsilcilerin .NET olay deseninin temelini ve bunların nasıl farklı olduğunu öğrenirsiniz.

Genel olarak, temsilcilerin .NET 'teki programlama kapsamında nasıl bir parçası olduğunu ve Framework API 'Leriyle çalıştığını göreceksiniz.

Haydi başlayın.

[Next](delegate-class.md)
