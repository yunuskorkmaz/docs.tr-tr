---
title: Temsilcilere Giriş
description: Bu genel bakış makalesindeki, temel kavramları tanıtan ve temsilciler için dil tasarımı hedeflerini tartışarak Temsilciler hakkında bilgi edinin.
ms.date: 02/02/2021
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: 72086301a6dd0552ab25baf732978802ad62669b
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548350"
---
# <a name="introduction-to-delegates"></a>Temsilcilere Giriş

Temsilciler, .NET ' te bir *geç bağlama* mekanizması sağlar. Geç bağlama, çağıranın, algoritmanın bir kısmını uygulayan en az bir yöntem sağladığı bir algoritma oluşturduğunuz anlamına gelir.

Örneğin, bir astronomi uygulamasındaki yıldızın bir listesini sıralamayı düşünün.
Bu yıldızları Dünya uzaklığına veya yıldızın büyüklüğüne göre ya da algılanan parlaklığını göre sıralamayı tercih edebilirsiniz.

Tüm bu durumlarda, Sort () yöntemi temelde aynı şeyi yapar: listedeki öğeleri, bazı karşılaştırmaya göre düzenler. İki yıldızı karşılaştıran kod, sıralama sıralarında her biri için farklıdır.

Bu tür çözümler yazılımda yarı bir yüzyıl için kullanılmıştır.
C# dil temsilcisi kavramı, birinci sınıf dil desteğini sağlar ve kavram etrafında güvenlik yazın.

Bu serinin ilerleyen kısımlarında göreceğiniz gibi, bu gibi algoritmalar için yazdığınız C# kodu tür güvenlidir ve türlerin bağımsız değişkenlerle ve dönüş türleriyle eşleşmesini sağlamak için dil kurallarını ve derleyiciyi kullanır.

[İşlev işaretçileri](~/_csharplang/proposals/csharp-9.0/function-pointers.md) , çağırma kuralı üzerinde daha fazla denetime ihtiyaç duyduğunuz benzer senaryolar Için C# 9 ' a eklenmiştir. Bir temsilciyle ilişkili kod, bir temsilci türüne eklenen bir sanal yöntem kullanılarak çağrılır. İşlev işaretçilerini kullanarak farklı kurallar belirtebilirsiniz.

## <a name="language-design-goals-for-delegates"></a>Temsilciler için dil tasarımı hedefleri

Dil tasarımcıları, son olarak temsilci haline gelen özellik için birkaç amaç numaralandırmış.

Ekip, herhangi bir geç bağlama algoritması için kullanılabilecek ortak bir dil yapısı istedi. Temsilciler, geliştiricilerin bir kavram öğrenmesine ve aynı kavramı birçok farklı yazılım sorununa karşı kullanmasına olanak sağlar.

İkincisi, takım hem tek hem çok noktaya yayın yöntemi çağrılarını desteklemek istedi. (Çok noktaya yayın temsilcileri, birden çok yöntem çağrısı zincirlenen temsilcidir.
[Bu serinin ilerleyen kısımlarında](delegate-class.md)örnekleri görürsünüz.)

Ekip, geliştiricilerin tüm C# yapılarını beklediği tür güvenliğini desteklemek için temsilciler istedi.

Son olarak, takım bir olay deseninin kabul edildiği, temsilcilerin veya herhangi bir geç bağlama algoritmasının çok faydalı olduğu belirli bir modeldir. Ekip, temsilcilerle ilgili kodun .NET olay deseninin temelini sağlayabilmemesini sağlamak istedi.

Bu çalışmanın sonucu, C# ve .NET sürümündeki temsilci ve olay desteiydi. Bu bölümdeki diğer makaleler, temsilcilerle çalışırken kullanılan dil özelliklerini, kitaplık desteğini ve yaygın deyimleri kapsar.

`delegate`Anahtar sözcüğü ve ürettiği kod hakkında bilgi edineceksiniz. `System.Delegate`Sınıftaki özellikler ve bu özelliklerin nasıl kullanıldığı hakkında bilgi edineceksiniz. Tür güvenli temsilciler oluşturmayı ve temsilciler aracılığıyla çağrılabilecek Yöntemler oluşturmayı öğreneceksiniz. Ayrıca lambda ifadeleri kullanarak temsilcilerle ve olaylarla nasıl çalışacağınızı öğreneceksiniz. Temsilcilerin LINQ için yapı taşlarından birine nerede geldiğini görürsünüz. Temsilcilerin .NET olay deseninin temelini ve bunların nasıl farklı olduğunu öğrenirsiniz.

Haydi başlayalım.

[Sonraki](delegate-class.md)
