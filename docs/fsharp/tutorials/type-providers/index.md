---
title: Tür Sağlayıcıları
description: Bilgi nasıl bir F# tür sağlayıcısı türleri, özellikleri ve yöntemleri programlarınızda kullanmak için sağlayan bir bileşenidir.
ms.date: 04/02/2018
ms.openlocfilehash: 39000fd1ca2af78afd1c333816fe9d5c0e2517cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967771"
---
# <a name="type-providers"></a>Tür Sağlayıcıları

Bir F# tür sağlayıcısı programınız içinde kullanmanız için türler, özellikler ve yöntemler sağlayan bir bileşendir. Tür sağlayıcıları oluşturma olarak bilinir ne **sağlanan türleri**, tarafından oluşturulmuş F# derleyici ve tanımladığınıza göre bir dış veri kaynağında.

Örneğin, bir F# tür sağlayıcısı SQL tabloları ve sütunları ilişkisel bir veritabanındaki temsil eden türleri oluşturabilir. Aslında, bunun ne olduğunu [SQLProvider](https://fsprojects.github.io/SQLProvider/) tür sağlayıcısı yok.

Sağlanan giriş parametreleri için bir tür sağlayıcısı türleri bağlıdır. Bir örnek veri kaynağını (örneğin, JSON şema dosyası gibi) bu tür girişi olabilir doğrudan bir dış hizmete veya bir veri kaynağı bağlantı dizesine işaret eden bir URL. Bir tür sağlayıcısı ayrıca tür gruplarının yalnızca istek üzerine genişletilir sağlayabilirsiniz; diğer bir deyişle, türler gerçekten programınız tarafından başvurulduğunda, bunlar genişletilir. Bu çevrimiçi veri marketleri gibi büyük ölçekli bilgi uzaylarının doğrudan, istek anında bütünleştirmesini türü kesin belirlenmiş olarak sağlar.

## <a name="generative-and-erased-type-providers"></a>Games'in ve Silinen tür sağlayıcıları

Tür sağlayıcıları iki biçimde gelir: Games'in ve silinebilir.

Games'in tür sağlayıcılarını .NET türleri olarak üretilmiş bütünleştirilmiş kod içine yazılabilir türleri üretir. Bu diğer bütünleştirilmiş koddan Tüketilecek sağlar. Bu veri kaynağı türü belirtilmiş gösterimini genellikle .NET türleriyle temsil etmek için uygun olan birini olması gerektiğini anlamına gelir.

Tür sağlayıcıları silme yalnızca derleme veya öğesinden oluşturulan proje kullanılabilecek türleri üretir. Kısa ömürlü türleridir; diğer bir deyişle, bir derlemeye yazılmaz ve diğer bütünleştirilmiş kodla tüketilemiyor. İçerebilirler *Gecikmeli* üyeleri, olası sonsuz bilgi alanından sağlanan kullanım türlerine izin verme. Bunlar, küçük bir alt birbirine ve büyük ölçekli veri kaynağını kullanmak için kullanışlıdır.

## <a name="commonly-used-type-providers"></a>Tür sağlayıcıları yaygın olarak kullanılan

Aşağıdaki yaygın olarak kullanılan kitaplıklar farklı kullanımları tür sağlayıcıları içerir:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) JSON, XML, CSV ve HTML biçimleri ve kaynak belge için tür sağlayıcıları içerir.
- [SQLProvider](https://fsprojects.github.io/SQLProvider/) nesne eşleme aracılığıyla ilişkisi veritabanlarına erişim türü kesin belirlenmiş sağlar ve F# LINQ sorguları bu veri kaynaklarına karşı.
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) sahip bir derleme zamanı için tür sağlayıcıları kümesini iade T-SQL ekleme F#.
- [Azure depolama tür sağlayıcısı](https://fsprojects.github.io/AzureStorageTypeProvider/) Azure Blobları, tablolar ve Kuyruklar, programınız üzerinden dize olarak kaynak adları belirtilmesine gerek olmadan bu kaynakları erişmenize olanak tanıyan için türler sağlar.
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) içeren **GraphQLProvider**, URL ile belirtilen bir GraphQL sunucuda temel türleri sağlar.

Gerekten yerlerde, aşağıdakileri yapabilirsiniz [kendi özel tür sağlayıcılarınızı oluşturabilir](creating-a-type-provider.md), veya başkaları tarafından oluşturulan tür sağlayıcılarına başvurabilirsiniz. Örneğin, kuruluşunuz her biri kendi kararlı veri şemasına sahip çok ve artan sayıda adlandırılmış veri kümeleri sağlayan bir veri hizmetine sahip olduğunu varsayın. Şemaları okuyan ve en son kullanılabilir veri kümelerini programcıya türü kesin belirlenmiş bir biçimde sunan bir tür sağlayıcısı oluşturmayı seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Bir tür sağlayıcısı oluşturma](creating-a-type-provider.md)
- [F# Dili Başvurusu](../../language-reference/index.md)
- [Visual F#](../../index.md)