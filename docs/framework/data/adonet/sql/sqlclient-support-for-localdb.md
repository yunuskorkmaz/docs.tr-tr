---
title: Yerel veritabanı SqlClient desteği
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 33368ca4b2dc5397087d29e515db6c1094e350bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359803"
---
# <a name="sqlclient-support-for-localdb"></a>Yerel veritabanı SqlClient desteği
SQL Server kod adı Denali başlayarak, SQL Server yerel veritabanı, olarak adlandırılan, basit bir sürümü kullanılabilir. Bu konuda bir LocalDB veritabanına bağlanmak nasıl ele alınmıştır.  
  
## <a name="remarks"></a>Açıklamalar  
 Yerel veritabanı yüklemek ve LocalDB örneğinizi yapılandırmak da dahil olmak üzere yerel veritabanı hakkında daha fazla bilgi için SQL Server Books Online'a bakın.  
  
 Yerel veritabanı ile neler yapabileceğiniz özetlemek için:  
  
-   Oluşturun ve yerel veritabanı örnekleri sqllocaldb.exe veya app.config dosyasını ile başlatın.  
  
-   SqlCmd.exe eklemek ve bir yerel veritabanı örneği veritabanlarında değiştirmek için kullanın. Örneğin, `sqlcmd -S (localdb)\myinst`.  
  
-   Kullanım `AttachDBFilename` bağlantı dizesi anahtar sözcüğü bir veritabanı, yerel veritabanı örneğine ekleyin. Kullanırken `AttachDBFilename`, veritabanı adını belirtmezseniz, `Database` bağlantı dizesi anahtar sözcüğü, uygulama kapandığında veritabanı LocalDB örneğinden kaldırılacak.  
  
-   Bir yerel veritabanı örneği bağlantı dizenizi belirtin. Örneğin, örnek adı. `myInstance`, bağlantı dizesi içerir:  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 `User Instance=True` bir LocalDB veritabanına bağlanırken izin verilmiyor.  
  
 Gelen LocalDB indirebilirsiniz [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065). Yerel veritabanı örneğinde veri değiştirmek için sqlcmd.exe kullanacaksa, SQL Server 2012 özellik Paketi'nden almak SQL Server 2012 sqlcmd gerekir.  
  
## <a name="programmatically-create-a-named-instance"></a>Adlandırılmış bir örnek program aracılığıyla oluşturma  
 Bir uygulama, adlandırılmış bir örnek oluşturun ve bir veritabanı gibi belirtin:  
  
-   App.config dosyasında şu şekilde oluşturmak için yerel veritabanı örneği belirtin.  Örneğinin sürüm numarası LocalDB yüklemenizin sürüm numarası aynı olmalıdır.  
  
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
  
-   Kullanarak örnek adı belirtin `server` bağlantı dizesi anahtar sözcüğü.  Belirtilen örnek adı `server` bağlantı dizesi anahtar sözcüğü, app.config dosyasında belirtilen adı eşleşmelidir.  
  
-   Kullanım `AttachDBFilename` belirtmek için bağlantı dizesi anahtar sözcüğü. MDF dosyası.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Özellikleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
