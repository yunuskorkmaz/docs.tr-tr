---
title: Entity Framework Veri Sağlayıcısı Yazma
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 29aa8cb1c6b31d9ada6b01860d76bcf03d37416c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854166"
---
# <a name="writing-an-entity-framework-data-provider"></a>Entity Framework Veri Sağlayıcısı Yazma
Bu bölümde, SQL Server dışında bir veri kaynağını desteklemek için Entity Framework sağlayıcısı yazma açıklanmaktadır. Entity Framework, SQL Server destekleyen bir sağlayıcı içerir.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Entity Framework sağlayıcı modeline giriş  
 Entity Framework, veritabanına bağımsızdır ve çeşitli veri kaynaklarına bağlanmak için ADO.NET sağlayıcı modelini kullanarak bir sağlayıcı yazabilirsiniz.  
  
 Entity Framework veri sağlayıcısı (ADO.NET Veri Sağlayıcısı modeli kullanılarak oluşturulan) aşağıdaki işlevleri gerçekleştirir:  
  
- Varlık Veri Modeli (EDM) temel türlerini sağlayıcı türlerine eşler.  
  
- Sağlayıcıya özgü işlevleri gösterir.  
  
- Entity Framework sorgularını desteklemek için belirli bir DbQueryCommandTree için sağlayıcıya özel komutlar oluşturur.  
  
- Entity Framework aracılığıyla güncelleştirmeleri desteklemek için belirli bir DbModificationCommandTree için sağlayıcıya özgü güncelleştirme komutları oluşturur.  
  
- Bir veritabanını temel alan bir modelin oluşturulmasını desteklemek için mağaza şeması tanımı için eşleme dosyalarını gösterir.  
  
- Kavramsal model aracılığıyla meta verileri (örneğin, tablolar ve görünümler) kullanıma sunar.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86,&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Örnek  
 SQL Server dışında bir veri kaynağını destekleyen bir Entity Framework sağlayıcısı örneği için [Entity Framework örnek sağlayıcısına](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) bakın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Üretimi](sql-generation.md)  
  
 [Değişiklik SQL Oluşturma](modification-sql-generation.md)  
  
 [Sağlayıcı Bildirimi Belirtimi](provider-manifest-specification.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Sağlayıcılarıyla Çalışma](working-with-data-providers.md)
