---
title: "Tür Sağlayıcıları"
description: "Nasıl bir F # tür sağlayıcısı türleri, özellikleri ve yöntemleri programlarınızı kullanmak için sağlayan bir bileşendir öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 25697ef6-465e-4248-9de5-1d199d4a8b59
ms.openlocfilehash: f721b5b378bf70fb594cad66bd90bd96a0320ee2
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="type-providers"></a>Tür Sağlayıcıları

> [!NOTE]
Bu kılavuz, F # 3.0 uygulamasından yazılmıştır ve güncelleştirilir.  Bkz: [FSharp.Data](https://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.

Bir F# tür sağlayıcısı programınız içinde kullanmanız için türler, özellikler ve yöntemler sağlayan bir bileşendir. Tür sağlayıcıları F# 3.0 bilgi zengin programlama desteğinin önemli bir parçasıdır. Bilgi zengin programlamanın anahtarı internette ve modern kurumsal ortamlarda bulunan çok çeşitli bilgi kaynakları ile çalışmadaki engelleri ortadan kaldırmaktır. Bir program içine bir bilgi kaynağını eklemekteki önemli engellerden biri bilgiyi programlama dili ortamında kullanmak için türler, özellikler ve yöntemler olarak temsil etme gereksinimidir. Bu türleri el ile yazmak çok zaman alıcıdır ve bakımı zordur. Yaygın bir alternatif projenize dosyalar ekleyen bir kod üretici kullanmaktır, ancak, kod üretiminin geleneksel türleri F# tarafından desteklenen keşifçi programlama modlarıyla iyi bir şekilde birleşemez çünkü üretilen kod her bir hizmet başvurusu değiştirildiğinde yenisiyle değiştirilmelidir.

F# tür sağlayıcıları tarafından sağlanan türler genellikle dış bilgi kaynaklarını temel alır. Örneğin, SQL için bir F# tür sağlayıcısı erişiminiz olan herhangi bir SQL veritabanı ile doğrudan çalışabilmeniz için gereken türleri, özellikleri ve yöntemleri sağlar. Benzer şekilde, WSDL web hizmetleri için bir tür sağlayıcısı herhangi bir WSDL web hizmeti ile doğrudan çalışmanız için gerekli türleri, özellikleri ve yöntemleri sağlar.

Bir F# tür sağlayıcısı tarafından sağlanan türler, özellikler ve yöntemler program kodu içinde verilen parametrelere bağlı olabilir. Örneğin, bir tür sağlayıcısı bir bağlantı dizesi ya da hizmet URL'sine bağlı olarak farklı türler sağlayabilir. Bu şekilde, bir bağlantı dizesi ya da URL aracılığıyla kullanılabilir olan bilgi uzayı doğrudan programınız içine dahil edilir. Bir tür sağlayıcısı ayrıca tür gruplarının yalnızca istek anında genişletilmesini sağlayabilir, yani, türler programınız tarafından başvurulduğunda genişletilirler. Bu çevrimiçi veri marketleri gibi büyük ölçekli bilgi uzaylarının doğrudan, istek anında bütünleştirmesini türü kesin belirlenmiş olarak sağlar.

F# Internet ve kurumsal veri hizmetlerinde yaygın olarak kullanılan birkaç yerleşik tür sağlayıcısı içerir. Bu tür sağlayıcıları SQL ilişkisel veritabanlarına ve ağ tabanlı OData ve WSDL hizmetlerine basit ve olağan erişim verir ve bu veri kaynaklarına karşı F# LINQ sorguları kullanımını destekler.

Gerekten yerlerde, kendi özel tür sağlayıcılarınızı oluşturabilir, ya da başkaları tarafından oluşturulan tür sağlayıcılarına başvurabilirsiniz. Örneğin, kuruluşunuz her biri kendi kararlı veri şemasına sahip çok ve artan sayıda adlandırılmış veri kümeleri sağlayan bir veri hizmetine sahip olduğunu varsayın. Şemaları okuyan ve en son kullanılabilir veri kümelerini programcıya türü kesin belirlenmiş bir biçimde sunan bir tür sağlayıcısı oluşturmayı seçebilirsiniz.


## <a name="related-topics"></a>İlgili Konular


|Başlık|Açıklama|
|-----|-----------|
|[İzlenecek yol: tür sağlayıcılarını kullanarak SQL veritabanına erişme](accessing-a-sql-database.md)|Bir SQL veritabanının tablolarına ve depolanmış yordamlarına erişim için, bir veritabanına doğrudan bağlanmak için bir bağlantı dizesini temel alan SqlDataConnection tür sağlayıcısının nasıl kullanıldığını açıklar. Erişim bir LINQ to SQL eşleştirmesi kullanır.|
|[İzlenecek yol: tür sağlayıcılarını ve varlıkları kullanarak SQL veritabanına erişme](accessing-a-sql-database-entities.md)|Bir SQL veritabanının tablolarına ve depolanmış yordamlarına erişim için, bir veritabanına doğrudan bağlanmak için bir bağlantı dizesini temel alan SqlEntityConnection tür sağlayıcısının nasıl kullanıldığını açıklar. Erişim bir LINQ to Entities eşlemesi kullanır. Bu yöntem herhangi bir veritabanı ile çalışabilir ancak gösterilen örnek SQL Server'dır.|
|[İzlenecek yol: tür sağlayıcılarını kullanarak OData hizmetine erişim](accessing-an-odata-service.md)|Bir hizmet URL'sini temel alarak bir OData hizmetine türü kesin belirlenmiş olarak erişmek için ODataService türü sağlayıcının nasıl kullanıldığını açıklar.|
|[İzlenecek yol: tür sağlayıcılarını kullanarak Web hizmetine erişim](accessing-a-web-service.md)|Bir hizmet URL'sini temel alarak bir WSDL web hizmetine türü kesin belirlenmiş olarak erişmek için WsdlService türü sağlayıcının nasıl kullanıldığını açıklar.|
|[İzlenecek yol: F &#35;oluşturma; DBML dosyasından türleri](generating-fsharp-types-from-dbml.md)|Bir DBML dosyasının Linq to SQL veritabanı şema belirtimi vermesini temel alarak bir SQL veritabanının tablolarına ve depolanmış yordamlarına erişim için DbmlFile türü sağlayıcının nasıl kullanıldığını açıklar.|
|[İzlenecek yol: F &#35;oluşturma; EDMX şema dosyasından türleri](generating-fsharp-types-from-edmx.md)|Bir EDMX dosyasının Varlık Çerçevesi şema belirtimi vermesini temel alarak bir SQL veritabanının tablolarına ve depolanmış yordamlarına erişim için EdmxFile tür sağlayıcısının nasıl kullanıldığını anlatır.|
|[Eğitmen: tür sağlayıcısı oluşturma](creating-a-type-provider.md)|Kendi özel tür sağlayıcılarınızı yazma konusu hakkında bilgi sağlar.|
|[Tür sağlayıcısı güvenliği](type-provider-security.md)|Tür sağlayıcıları geliştirirken dikkat edilmesi gereken güvenlik konuları hakkında bilgi sağlar.|
|[Tür Sağlayıcıları Sorunlarını Giderme](troubleshooting-type-providers.md)|Tür sağlayıcıları ile çalışırken ortaya çıkabilen yaygın sorunlar ve çözümler için öneriler hakkında bilgi sağlar.|

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](../../language-reference/index.md)

[Visual F#](../../index.md)
