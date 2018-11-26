---
title: Bir Entity Framework veri sağlayıcısı yazma
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 513af001392ae0b7abe8e6c62dc74f09469b3655
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296639"
---
# <a name="writing-an-entity-framework-data-provider"></a>Bir Entity Framework veri sağlayıcısı yazma
Bu bölümde nasıl yazılacağını açıklar bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] SQL Server dışındaki bir veri kaynağını desteklemek için sağlayıcı. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] SQL Server'ı destekleyen bir sağlayıcı içerir.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Entity Framework sağlayıcısı modeli ile tanışın  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Veritabanı bağımsızdır ve farklı bir veri kaynağı kümesine bağlanmak için ADO.NET sağlayıcısı modeli kullanarak bir sağlayıcı yazabilirsiniz.  
  
 Entity Framework veri sağlayıcısı (ADO.NET veri sağlayıcı modeli kullanılarak oluşturulan), aşağıdaki işlevleri gerçekleştirir:  
  
-   Varlık veri modeli (EDM) ilkel tür sağlayıcısı türleri ile eşleştirir.  
  
-   Sağlayıcıya özgü işlevleri kullanıma sunar.  
  
-   Sağlayıcıya özgü komutlar için desteklemek belirli bir DbQueryCommandTree oluşturur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sorgular.  
  
-   Sağlayıcıya özgü güncelleştirme komutları aracılığıyla güncelleştirmeleri desteklemek belirli bir DbModificationCommandTree oluşturur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Kullanıma sunan bir veritabanını temel alan bir model oluşturulmasını desteklemek için depolama şema tanımı dosyaları eşleme.  
  
-   Metadata (tablolar ve görünümler, örneğin) bir kavramsal model üzerinden kullanıma sunar.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Örnek  
 Bkz: [Entity Framework örnek sağlayıcısı](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) gösteren bir örnek bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] destekleyen SQL Server dışındaki bir veri kaynağı sağlayıcı.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Üretimi](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [Değişiklik SQL Oluşturma](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [Sağlayıcı Bildirimi Belirtimi](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Sağlayıcılarıyla Çalışma](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
