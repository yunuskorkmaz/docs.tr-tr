---
title: Örnek veritabanları indiriliyor (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: c67ee699cf594f476a728c7345b47b0c32dea7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795170"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>Örnek veritabanları indiriliyor (LINQ to DataSet)
LINQ to DataSet belgelerindeki örnekler ve izlenecek yollar AdventureWorks örnek veritabanını kullanır. Bu ürünü Microsoft Download sitesinden ücretsiz olarak indirebilirsiniz. LINQ to DataSet belgelerindeki örnekler ve izlenecek yollar veri deposu olarak SQL Server kullanır. Ücret ödemeden kullanılabilen SQL Server Express sürümü, SQL Server yerine veri deposu olarak da kullanılabilir.  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>AdventureWorks veritabanını indirme ve yükleme  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>SQL Server için AdventureWorks örnek veritabanını indirmek ve yüklemek için  
  
1. Internet Explorer’ı açın.  
  
2. [SQL Server 2005 örnekleri ve örnek veritabanları](https://go.microsoft.com/fwlink/?linkid=31046) Web sitesine gidin.  
  
3. İşlemci türü (örneğin, AdventureWorksDB. msi) için AdventureWorks örnek veritabanını indirme yönergelerini izleyin ve öğesini kaydedin. MSI dosyasını yerel bilgisayarınıza.  
  
4. İndirmenin veya SQL Server Kurulum sırasında yüklü olan bir önceki AdventureWorks sürümüne sahipseniz, AdventureWorks. msi ' yi çalıştırmadan önce bu sürümü kaldırmanız gerekir.  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>AdventureWorks örnek veritabanının önceki bir indirmeyi kaldırmak için  
  
1. AdventureWorks veya AdventureWorksDW veritabanını bırakın.  
  
2. **Program Ekle veya Kaldır**' dan **AdventureWorksDB** veya **AdventureWorksBI** ' yi seçin ve **Kaldır**' ı tıklatın.  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>Daha önce kurulum kullanılarak yüklenen bir AdventureWorks örnek veritabanını kaldırmak için  
  
1. AdventureWorks veya AdventureWorksDW veritabanını bırakın.  
  
2. **Program Ekle veya Kaldır**' dan **Microsoft SQL Server 2005** ' i seçin ve **Değiştir**' e tıklayın.  
  
3. **Bileşen seçimi**' nden **iş istasyonu bileşenleri** ' ni seçin ve **İleri**' ye tıklayın.  
  
4. **SQL Server yükleme sihirbazına hoş geldiniz ' e**tıklayarak **İleri**' ye tıklayın.  
  
5. **Sistem yapılandırması denetiminden** **İleri**' ye tıklayın.  
  
6. **Değişiklik veya kaldırma örneğinden**, **yüklü bileşenleri Değiştir**' e tıklayın.  
  
7. **Özellik seçimi**' nden **belge, örnekler ve örnek veritabanları** düğümünü genişletin.  
  
8. **Örnek kod ve uygulamalar ' ı**seçin. **Örnek veritabanları**' nı genişletin, kaldırılacak örnek veritabanını seçin ve **Tüm özelliğin devre dışı olacağını**seçin. **İleri**'ye tıklayın.  
  
9. Yükleme **' ye** tıklayın ve yükleme sihirbazını sona erdirin.  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>AdventureWorks örnek veritabanı dosyalarını bir SQL Server örneğine eklemek için  
  
1. Dosya örnek veritabanı yükleyicisi dosyası indirildikten sonra, veritabanını yüklemek için **AdventureWorksDB. msi** dosyasını (veya indirdiğiniz dosyayı) çift tıklatın. Varsayılan olarak, veritabanı c:\Program Files\Microsoft SQL Server\mssql. 1\Mssql\datakonumuna yüklenir.  
  
2. Aşağıdaki betik SQLCMD veya SQL Server Management Studio yürüterek AdventureWorks veritabanı dosyalarını bir SQL Server örneğine ekleyin:  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Bu dosyaları farklı bir sürücüye veya dizine yüklediyseniz, `sp_attach_db` saklı yordamı yürütmeden önce yolları uygun şekilde düzeltmeniz gerekir.  
  
## <a name="downloading-sql-server-express-edition"></a>SQL Server Express Edition indiriliyor  
 LINQ to DataSet bölümündeki örnekler ve izlenecek yollar veri deposu olarak SQL Server 2005 kullanır, ancak bunun yerine SQL Server Express Edition kullanacak şekilde değiştirilebilir. SQL Server Express sürüm ücretsiz olarak kullanılabilir ve uygulamalar ile yeniden dağıtabilirsiniz. Visual Studio kullanıyorsanız, Pro ve üzeri sürümlerde SQL Server Express Edition bulunur.  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>SQL Server Express sürümünü indirmek ve yüklemek için  
  
1. Internet Explorer 'ı başlatın.  
  
2. [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) indirme sayfasına gidin.  
  
3. Web sitesindeki yükleme yönergelerini izleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-linq-to-dataset.md)
