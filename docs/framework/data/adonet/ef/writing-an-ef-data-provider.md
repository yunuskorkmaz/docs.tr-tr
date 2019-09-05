---
title: Entity Framework Veri Sağlayıcısı Yazma
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 6c5e6e2859b48db6c982862381d223a4c9deb2c5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248183"
---
# <a name="writing-an-entity-framework-data-provider"></a>Entity Framework Veri Sağlayıcısı Yazma
Bu bölümde, SQL Server dışında bir veri [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] kaynağını destekleyecek bir sağlayıcının nasıl yazılacağı açıklanmaktadır. , [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] SQL Server destekleyen bir sağlayıcı içerir.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Entity Framework sağlayıcı modeline giriş  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , Veritabanına bağımsızdır ve çeşitli veri kaynaklarına bağlanmak için ADO.NET sağlayıcı modelini kullanarak bir sağlayıcı yazabilirsiniz.  
  
 Entity Framework veri sağlayıcısı (ADO.NET Veri Sağlayıcısı modeli kullanılarak oluşturulan) aşağıdaki işlevleri gerçekleştirir:  
  
- Varlık Veri Modeli (EDM) temel türlerini sağlayıcı türlerine eşler.  
  
- Sağlayıcıya özgü işlevleri gösterir.  
  
- Sorguları desteklemek [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] için belirli bir DbQueryCommandTree için sağlayıcıya özel komutlar oluşturur.  
  
- İçindeki güncelleştirmeleri desteklemek için belirli bir DbModificationCommandTree için sağlayıcıya özgü güncelleştirme komutları oluşturur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
- Bir veritabanını temel alan bir modelin oluşturulmasını desteklemek için mağaza şeması tanımı için eşleme dosyalarını gösterir.  
  
- Kavramsal model aracılığıyla meta verileri (örneğin, tablolar ve görünümler) kullanıma sunar.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86,&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Örnek  
 SQL Server dışında bir veri kaynağını destekleyen bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcının örneği için [Entity Framework örnek sağlayıcısına](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) bakın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Üretimi](sql-generation.md)  
  
 [Değişiklik SQL Oluşturma](modification-sql-generation.md)  
  
 [Sağlayıcı Bildirimi Belirtimi](provider-manifest-specification.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Sağlayıcılarıyla Çalışma](working-with-data-providers.md)
