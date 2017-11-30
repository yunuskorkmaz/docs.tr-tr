---
title: "Yerel veritabanı SqlClient desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: abe9487f9c2ebbb93c2e712959237f722ee707b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sqlclient-support-for-localdb"></a>Yerel veritabanı SqlClient desteği
' Den başlayarak [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] kod adı Denali, hafif bir sürümüdür ve [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], yerel veritabanı olarak adlandırılan, kullanılabilir olacaktır. Bu konuda bir LocalDB veritabanına bağlanmak nasıl ele alınmıştır.  
  
## <a name="remarks"></a>Açıklamalar  
 Yerel veritabanı yüklemek ve LocalDB örneğinizi yapılandırmak da dahil olmak üzere yerel veritabanı hakkında daha fazla bilgi için bkz: [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.  
  
 Yerel veritabanı ile neler yapabileceğiniz özetlemek için:  
  
-   Oluşturun ve yerel veritabanı örnekleri sqllocaldb.exe veya app.config dosyasını ile başlatın.  
  
-   SqlCmd.exe eklemek ve bir yerel veritabanı örneği veritabanlarında değiştirmek için kullanın. Örneğin, `sqlcmd -S (localdb)\myinst`.  
  
-   Kullanım `AttachDBFilename` bağlantı dizesi anahtar sözcüğü bir veritabanı, yerel veritabanı örneğine ekleyin. Kullanırken `AttachDBFilename`, veritabanı adını belirtmezseniz, `Database` bağlantı dizesi anahtar sözcüğü, uygulama kapandığında veritabanı LocalDB örneğinden kaldırılacak.  
  
-   Bir yerel veritabanı örneği bağlantı dizenizi belirtin. Örneğin, örnek adı. `myInstance`, bağlantı dizesi içerir:  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 `User Instance=True`bir LocalDB veritabanına bağlanırken izin verilmiyor.  
  
 Gelen LocalDB indirebilirsiniz [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065). Yerel veritabanı örneğinde veri değiştirmek için sqlcmd.exe kullanacaksa, gelen sqlcmd gerekir [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] nden de edinebilirsiniz 2012 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 özellik paketi.  
  
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
 [SQL Server özellikleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
