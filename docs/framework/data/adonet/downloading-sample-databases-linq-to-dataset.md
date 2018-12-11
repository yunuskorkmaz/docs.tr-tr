---
title: Örnek Veritabanları (LINQ to DataSet) indirme
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: a98dd4e3d2ff113d3a5374d97fe30cec9524c095
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125567"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Örnek Veritabanları (LINQ to DataSet) indirme
Örnekler ve izlenecek yollarında [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] belgeleri AdventureWorks örnek veritabanını kullanın. Bu ürün ücretsiz olarak Microsoft Yükleme sitesinden indirebilirsiniz. Örnekler ve izlenecek yollarında [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] belgeleri, SQL Server veri deposu olarak kullanın. SQL Server Express ücret kullanılabilir Edition, SQL Server yerine veri deposu olarak da kullanılabilir.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>İndirme ve AdventureWorks veritabanını yükleme  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>İndirmek ve AdventureWorks örnek veritabanı için SQL Server yüklemek için  
  
1.  Internet Explorer’ı açın.  
  
2.  Git [SQL Server 2005 örnekleri ve örnek veritabanları](https://go.microsoft.com/fwlink/?linkid=31046) Web sitesi.  
  
3.  AdventureWorks örnek veritabanını (örneğin, AdventureWorksDB.msi) işlemci türünüz için yükleme yönergelerini izleyin ve kaydedin. MSI dosyası yerel bilgisayarınıza.  
  
4.  Karşıdan yükleme ya da SQL Server Kurulumu sırasında yüklenen AdventureWorks önceki bir sürümü varsa, AdventureWorks.msi çalıştırmadan önce kaldırmanız gerekir.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>AdventureWorks örnek veritabanı önceki bir yükleme kaldırmak için  
  
1.  AdventureWorks veya AdventureWorksDW veritabanını bırakın.  
  
2.  Gelen **Program Ekle veya Kaldır**seçin **AdventureWorksDB** veya **AdventureWorksBI** tıklatıp **Kaldır**.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Kurulum'u kullanarak daha önce yüklenmiş bir AdventureWorks örnek veritabanını kaldırmak için  
  
1.  AdventureWorks veya AdventureWorksDW veritabanını bırakın.  
  
2.  Gelen **Program Ekle veya Kaldır**seçin **Microsoft SQL Server 2005** tıklatıp **değişiklik**.  
  
3.  Gelen **Bileşen Seçimi**seçin **iş istasyonu bileşenleri** ve ardından **sonraki**.  
  
4.  Gelen **SQL Server yükleme Sihirbazına Hoş Geldiniz**, tıklayın **sonraki**.  
  
5.  Gelen **sistem yapılandırma denetimi**, tıklayın **sonraki**.  
  
6.  Gelen **değiştirme veya kaldırma örneği**, tıklayın **değişiklik bileşenlerin yüklü**.  
  
7.  Gelen **özellik seçimi**, genişletme **belgeler, örnekler ve örnek veritabanları** düğümü.  
  
8.  Seçin **örnek kod ve uygulamaları**. Genişletin **örnek veritabanları**, kaldırılacak ve örnek veritabanını seçmeniz **tüm özellik kullanılamaz**. **İleri**'ye tıklayın.  
  
9. Tıklayın **yükleme** ve Yükleme Sihirbazı'nı tamamlayın.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>SQL Server örneğine AdventureWorks örnek veritabanı dosyalarını eklemek için  
  
1.  Örnek veritabanı yükleyici dosyası indirilmeden sonra çift **AdventureWorksDB.msi** dosya (veya indirdiğiniz dosyanın) veritabanını yüklemek için. Varsayılan olarak, c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data veritabanı yüklenir.  
  
2.  AdventureWorks veritabanı dosyaları, SQL Server örneğine SQLCMD veya SQL Server Management Studio aşağıdaki betiği çalıştırarak ekleyin:  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Bu dosyalar farklı bir sürücü veya dizin yüklediyseniz, yürütmeden önce yolların uygun şekilde düzeltmeniz gerekir `sp_attach_db` saklı yordamı.  
  
## <a name="downloading-sql-server-express-edition"></a>SQL Server Express sürümü indiriliyor  
 Örnekler ve izlenecek yollarında [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] bölümü SQL Server 2005 veri deposu olarak kullanabilirsiniz, ancak SQL Server Express Edition kullanmayı değiştirilebilir. SQL Server Express Edition ücretsiz kullanılabilir ve uygulamaları yeniden dağıtabilirsiniz. Visual Studio kullanıyorsanız, SQL Server Express Edition Pro ve üzeri sürümlerinde bulunur.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>SQL Server Express Edition'ı indirip  
  
1.  Internet Explorer'ı başlatın.  
  
2.  Git [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) indirme sayfası.  
  
3.  Web sitesi yükleme yönergelerini izleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
