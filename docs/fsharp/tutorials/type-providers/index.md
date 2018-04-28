---
title: Tür Sağlayıcıları
description: 'Nasıl bir F # tür sağlayıcısı türleri, özellikleri ve yöntemleri programlarınızı kullanmak için sağlayan bir bileşendir öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 04/02/2018
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 5b7bae6f960b9cfa91188e8eb80be949cda12b65
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="type-providers"></a>Tür Sağlayıcıları

Bir F# tür sağlayıcısı programınız içinde kullanmanız için türler, özellikler ve yöntemler sağlayan bir bileşendir. Tür sağlayıcıları oluşturmak ne olarak da bilinir **sağlanan türleri**, F # derleyici tarafından oluşturulan ve bir dış veri kaynağına göre.

Örneğin, bir SQL için F # tür sağlayıcısı tablolar ve sütunlar ilişkisel bir veritabanındaki temsil eden türleri oluşturabilir. Aslında, bu nedir [SQLProvider](https://fsprojects.github.io/SQLProvider/) türü sağlayıcısı.

Sağlanan tür sağlayıcısı giriş parametreleri türlerine bağlıdır. Bu tür giriş (örneğin, JSON şema dosyası gibi) bir örnek veri kaynağı olabilir doğrudan bir dış hizmet ya da bir veri kaynağı için bir bağlantı dizesi işaret eden bir URL. Tür sağlayıcısı türlerinin grupları isteğe bağlı olarak yalnızca genişletilir de sağlayabilirsiniz; türleri gerçekte programınız tarafından başvurulduğundan, diğer bir deyişle, bunlar genişletilir. Bu çevrimiçi veri marketleri gibi büyük ölçekli bilgi uzaylarının doğrudan, istek anında bütünleştirmesini türü kesin belirlenmiş olarak sağlar.

## <a name="generative-and-erased-type-providers"></a>Generative ve Silinen tür sağlayıcıları

Tür sağlayıcıları gelen iki biçimde: Generative ve silinebilir.

Generative tür sağlayıcıları .NET türleri olarak üretilen derlemeye yazılabilir türleri oluşturur. Bu diğer derlemelerden koddan tüketilmesi sağlar. Bu veri kaynağı türü belirtilmiş gösterimini genellikle .NET türleri ile temsil etmek için uygun olan bir olması gerektiği anlamına gelir.

Silme tür sağlayıcıları yalnızca derleme ya da bunlar oluşturulan proje tüketilebilir türleri oluşturur. Kısa ömürlü türleridir; diğer bir deyişle, bir derlemeye yazılmaz ve diğer derlemelerde kod tarafından kullanılamaz. İçerebilirler *Gecikmeli* üyeleri, büyük olasılıkla sonsuz bilgi alanından kullanım sağlanan türleri için izin verme. Bunlar, küçük bir alt büyük ve birbirine bağlı veri kaynağı kullanmak için kullanışlıdır.

## <a name="commonly-used-type-providers"></a>Tür sağlayıcıları yaygın olarak kullanılan

Aşağıdaki yaygın kullanılan kitaplıklar farklı amaçlarla tür sağlayıcıları içerir:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) JSON, XML, CSV ve HTML Belge biçimleri ve kaynaklar için tür sağlayıcıları içerir.
- [SQLProvider](https://fsprojects.github.io/SQLProvider/) bu veri kaynaklarının sorguları nesne eşleme ve F # LINQ üzerinden ilişkisi veritabanlarını kesin türü belirtilmiş erişmenizi sağlar.
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) sahip bir derleme zamanı tür sağlayıcıları işaretli T-SQL F # katıştırma.
- [Azure depolama türü sağlayıcısı](https://fsprojects.github.io/AzureStorageTypeProvider/) Azure BLOB'ları, tabloları ve Kuyruklar, programınızı boyunca dizeleri olarak kaynak adları belirtmek zorunda kalmadan bu kaynaklara erişmeyi sağlayan türler sağlar.
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) içeren **GraphQLProvider**, URL tarafından belirtilen bir GraphQL sunucusu temel türü sunar.

Gerektiğinde yapabilecekleriniz [kendi özel tür sağlayıcıları oluşturmak](creating-a-type-provider.md), veya başkaları tarafından oluşturulan tür sağlayıcıları başvuru. Örneğin, kuruluşunuz her biri kendi kararlı veri şemasına sahip çok ve artan sayıda adlandırılmış veri kümeleri sağlayan bir veri hizmetine sahip olduğunu varsayın. Şemaları okuyan ve en son kullanılabilir veri kümelerini programcıya türü kesin belirlenmiş bir biçimde sunan bir tür sağlayıcısı oluşturmayı seçebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
[Eğitmen: tür sağlayıcısı oluşturma](creating-a-type-provider.md)

[F# Dili Başvurusu](../../language-reference/index.md)

[Visual F#](../../index.md)
