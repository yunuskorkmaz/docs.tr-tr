---
title: Yerel Veritabanı için SqlClient Desteği
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 841c455605b0b32668d26cab16a6207dc1c0f716
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203429"
---
# <a name="sqlclient-support-for-localdb"></a>Yerel Veritabanı için SqlClient Desteği

SQL Server kod adından itibaren, LocalDB adlı bir SQL Server basit sürümü kullanıma sunulacaktır. Bu konuda, bir LocalDB veritabanına nasıl bağlanabileceği açıklanmaktadır.  
  
## <a name="remarks"></a>Açıklamalar  

 LocalDB 'yi yüklemek ve LocalDB örneğinizi yapılandırmak dahil olmak üzere LocalDB hakkında daha fazla bilgi için bkz. Books Online SQL Server.  
  
 LocalDB ile neler yapabileceğinizi özetlemek için:  
  
- sqllocaldb.exe veya app.config dosyanız ile LocalDB örnekleri oluşturun ve başlatın.  
  
- LocalDB örneğindeki veritabanlarını eklemek ve değiştirmek için sqlcmd.exe kullanın. Örneğin, `sqlcmd -S (localdb)\myinst`.  
  
- `AttachDBFilename`LocalDB örneğiniz için bir veritabanı eklemek üzere bağlantı dizesi anahtar sözcüğünü kullanın. Kullanırken `AttachDBFilename` , `Database` bağlantı dizesi anahtar sözcüğü ile veritabanının adını belirtmezseniz, uygulama kapandığında veritabanı LocalDB örneğinden kaldırılır.  
  
- Bağlantı dizeniz için bir LocalDB örneği belirtin. Örneğin, örnek adınız `myInstance` , bağlantı dizesinde şunları içerir:  
  
    `server=(localdb)\\myInstance`  
  
 `User Instance=True` bir LocalDB veritabanına bağlanılırken izin verilmez.  
  
 LocalDB 'yi [Microsoft SQL Server 2012 özellik paketinden](https://www.microsoft.com/download/en/details.aspx?id=29065)indirebilirsiniz. LocalDB örneğinizdeki verileri değiştirmek için sqlcmd.exe kullanacaksanız, SQL Server 2012 Feature Pack 'ten de alabileceğiniz SQL Server 2012 ' den sqlcmd gerekir.  
  
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
