---
description: 'Daha fazla bilgi edinin: LocalDB için SqlClient desteği'
title: Yerel Veritabanı için SqlClient Desteği
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: f99c46277638c810c91f7ceffd0e47c896125c63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767173"
---
# <a name="sqlclient-support-for-localdb"></a>Yerel Veritabanı için SqlClient Desteği

Bu makalede bir LocalDB veritabanına nasıl bağlanabileceği açıklanır. LocalDB SQL Server basit bir sürümüdür.
  
## <a name="remarks"></a>Açıklamalar
  
 LocalDB ile neler yapabileceğinizi özetlemek için:  
  
- sqllocaldb.exe veya app.config dosyanız ile LocalDB örnekleri oluşturun ve başlatın.  
  
- LocalDB örneğindeki veritabanlarını eklemek ve değiştirmek için sqlcmd.exe kullanın. Örneğin, `sqlcmd -S (localdb)\myinst`.  
  
- `AttachDBFilename`LocalDB örneğiniz için bir veritabanı eklemek üzere bağlantı dizesi anahtar sözcüğünü kullanın. Kullanırken `AttachDBFilename` , `Database` bağlantı dizesi anahtar sözcüğü ile veritabanının adını belirtmezseniz, uygulama kapandığında veritabanı LocalDB örneğinden kaldırılır.  
  
- Bağlantı dizeniz için bir LocalDB örneği belirtin. Örneğin, örnek adınız `myInstance` , bağlantı dizesinde şunları içerir:  
  
    `server=(localdb)\\myInstance`  
  
 `User Instance=True` bir LocalDB veritabanına bağlanılırken izin verilmez.  
  
LocalDB 'yi yükleme hakkında daha fazla bilgi için bkz. [SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb).
  
## <a name="programmatically-create-a-named-instance"></a>Program aracılığıyla adlandırılmış bir örnek oluşturma  

 Bir uygulama, adlandırılmış bir örnek oluşturabilir ve aşağıdaki gibi bir veritabanı belirtebilir:  
  
- app.config dosyasında oluşturulacak LocalDB örneklerini aşağıda gösterildiği gibi belirtin.  Örneğin sürüm numarası, LocalDB yüklemenizin sürüm numarasıyla aynı olmalıdır.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- Bağlantı dizesi anahtar sözcüğünü kullanarak örneğin adını belirtin `server` .  `server`Bağlantı dizesi anahtar sözcüğü içinde belirtilen örnek adının app.config dosyasında belirtilen adla eşleşmesi gerekir.  
  
- Öğesini `AttachDBFilename` belirtmek için bağlantı dizesi anahtar sözcüğünü kullanın. MDF dosyası.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Özellikleri ve ADO.NET](sql-server-features-and-adonet.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
