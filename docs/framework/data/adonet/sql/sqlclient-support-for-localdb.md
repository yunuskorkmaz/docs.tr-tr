---
title: Yerel Veritabanı için SqlClient Desteği
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 200db3b1014278e711062bcbdff81be8d27c3351
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780784"
---
# <a name="sqlclient-support-for-localdb"></a>Yerel Veritabanı için SqlClient Desteği
SQL Server kod adından itibaren, LocalDB adlı bir SQL Server basit sürümü kullanıma sunulacaktır. Bu konuda, bir LocalDB veritabanına nasıl bağlanabileceği açıklanmaktadır.  
  
## <a name="remarks"></a>Açıklamalar  
 LocalDB 'yi yüklemek ve LocalDB örneğinizi yapılandırmak dahil olmak üzere LocalDB hakkında daha fazla bilgi için bkz. Books Online SQL Server.  
  
 LocalDB ile neler yapabileceğinizi özetlemek için:  
  
- SqlLocalDB. exe veya App. config dosyanız ile LocalDB örnekleri oluşturun ve başlatın.  
  
- LocalDB örneğindeki veritabanlarını eklemek ve değiştirmek için sqlcmd. exe ' yi kullanın. Örneğin: `sqlcmd -S (localdb)\myinst`.  
  
- LocalDB örneğiniz için bir veritabanı eklemek üzere bağlantıdizesianahtarsözcüğünükullanın.`AttachDBFilename` Kullanırken `AttachDBFilename`, `Database` bağlantı dizesi anahtar sözcüğü ile veritabanının adını belirtmezseniz, uygulama kapandığında veritabanı LocalDB örneğinden kaldırılır.  
  
- Bağlantı dizeniz için bir LocalDB örneği belirtin. Örneğin, örnek adınız `myInstance`, bağlantı dizesinde şunları içerir:  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 `User Instance=True`bir LocalDB veritabanına bağlanılırken izin verilmez.  
  
 LocalDB 'yi [Microsoft SQL Server 2012 özellik paketinden](https://www.microsoft.com/download/en/details.aspx?id=29065)indirebilirsiniz. LocalDB örneğinizdeki verileri değiştirmek için sqlcmd. exe ' yi kullanacaksanız, SQL Server 2012 özellik paketinden de alabileceğiniz SQL Server 2012 ' dan sqlcmd gerekir.  
  
## <a name="programmatically-create-a-named-instance"></a>Program aracılığıyla adlandırılmış bir örnek oluşturma  
 Bir uygulama, adlandırılmış bir örnek oluşturabilir ve aşağıdaki gibi bir veritabanı belirtebilir:  
  
- App. config dosyasında oluşturulacak LocalDB örneklerini aşağıda gösterildiği gibi belirtin.  Örneğin sürüm numarası, LocalDB yüklemenizin sürüm numarasıyla aynı olmalıdır.  
  
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
  
- `server` Bağlantı dizesi anahtar sözcüğünü kullanarak örneğin adını belirtin.  `server` Bağlantı dizesi anahtar sözcüğü içinde belirtilen örnek adı, App. config dosyasında belirtilen ad ile aynı olmalıdır.  
  
- Öğesini belirtmek için bağlantı dizesi anahtar sözcüğünü kullanın. `AttachDBFilename` MDF dosyası.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Özellikleri ve ADO.NET](sql-server-features-and-adonet.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
