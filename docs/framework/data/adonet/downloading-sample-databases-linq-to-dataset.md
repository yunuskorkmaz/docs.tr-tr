---
title: "Örnek Veritabanları (LINQ-DataSet) yükleniyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b984fdef7f7f43e266ec4ba42b04990aced159c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Örnek Veritabanları (LINQ-DataSet) yükleniyor
Örnekler ve izlenecek yollarda [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] belgeleri AdventureWorks örnek veritabanını kullanın. Bu ürün ücretsiz Microsoft sitesinden indirebilirsiniz. Örnekler ve izlenecek yollarda [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] belgeleri SQL Server veri deposu olarak kullanın. SQL Server Express ücretsiz kullanılabilir olan Edition yerine SQL Server veri deposu olarak da kullanılabilir.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>İndirme ve AdventureWorks veritabanını yükleme  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>İndirmek ve SQL Server için AdventureWorks örnek veritabanını yüklemek için  
  
1.  Internet Explorer’ı açın.  
  
2.  Git [SQL Server 2005 örnekler ve örnek veritabanları](http://go.microsoft.com/fwlink/?linkid=31046) Web sitesi.  
  
3.  AdventureWorks örnek veritabanı, işlemci türü (örneğin, AdventureWorksDB.msi) için karşıdan yüklemek için yönergeleri izleyin ve kaydedin. MSI dosyası yerel bilgisayarınızda.  
  
4.  Karşıdan yükleme veya SQL Server Kurulumu sırasında yüklenen AdventureWorks önceki bir sürümü varsa, AdventureWorks.msi çalıştırmadan önce kaldırmanız gerekir.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>Önceki bir yükleme AdventureWorks örnek veritabanını kaldırmak için  
  
1.  AdventureWorks veya AdventureWorksDW veritabanını bırakın.  
  
2.  Gelen **Program Ekle veya Kaldır**seçin **AdventureWorksDB** veya **AdventureWorksBI** tıklatıp **kaldırmak**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Kurulum'u kullanarak daha önce yüklenmiş bir AdventureWorks örnek veritabanını kaldırmak için  
  
1.  AdventureWorks veya AdventureWorksDW veritabanını bırakın.  
  
2.  Gelen **Program Ekle veya Kaldır**seçin **Microsoft SQL Server 2005** tıklatıp **değişiklik**.  
  
3.  Gelen **Bileşen Seçimi**seçin **iş istasyonu bileşenleri** ve ardından **sonraki**.  
  
4.  Gelen **SQL Server yükleme Sihirbazına Hoş Geldiniz**, tıklatın **sonraki**.  
  
5.  Gelen **sistem yapılandırma denetimi**, tıklatın **sonraki**.  
  
6.  Gelen **Değiştir veya Kaldır örnek**, tıklatın **değişiklik bileşenlerinin yüklü**.  
  
7.  Gelen **özellik seçimi**, genişletin **belgeler, örnekler ve örnek veritabanları** düğümü.  
  
8.  Seçin **örnek kod ve uygulamaları**. Genişletme **örnek veritabanları**, kaldırılması ve seçmek için örnek veritabanını seçin **tüm özelliği kullanılamaz**. **İleri**'ye tıklayın.  
  
9. Tıklatın **yükleme** ve Yükleme Sihirbazı'nı tamamlayın.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>SQL Server örneğine AdventureWorks örnek veritabanı dosyalarını eklemek için  
  
1.  Örnek veritabanı yükleyici dosyası indirilmeden sonra çift tıklayarak **AdventureWorksDB.msi** dosyası (veya indirdiğiniz dosyası) veritabanını yüklemek için. Varsayılan olarak, veritabanı c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data sırasında yüklenir.  
  
2.  AdventureWorks veritabanı dosyaları, aşağıdaki komut dosyası SQLCMD veya SQL Server Management Studio yürüterek SQL Server örneğine ekleyin:  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Bu dosyalar farklı bir sürücü veya dizin yüklediyseniz, çalıştırmadan önce yolları uygun şekilde düzeltmeniz gerekir `sp_attach_db` saklı yordamı.  
  
## <a name="downloading-sql-server-express-edition"></a>SQL Server Express sürümü indirme  
 Örnekler ve izlenecek yollarda [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] bölüm veri deposu olarak SQL Server 2005 kullanır ancak SQL Server Express Edition kullanmayı değiştirilebilir. SQL Server Express Edition ücretsiz kullanılabilir ve uygulamalarla yeniden dağıtabilirsiniz. Kullanıyorsanız [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], SQL Server Express Edition Pro ve sonraki sürümlerinde bulunur.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>SQL Server Express sürümünü karşıdan yükleyip  
  
1.  Internet Explorer'ı başlatın.  
  
2.  Git [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) sayfa indirin.  
  
3.  Web sitesindeki yükleme yönergeleri izleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
