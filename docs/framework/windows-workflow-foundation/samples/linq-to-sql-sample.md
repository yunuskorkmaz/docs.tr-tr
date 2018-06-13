---
title: LINQ-SQL örneği
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 3cfcaf3de1a22b8bb5505083f127a9888b99dbd8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806724"
---
# <a name="linq-to-sql-sample"></a>LINQ-SQL örneği
Bu örnek, SQL Server veritabanlarını tablolardan SQL sorgu varlıklara LINQ kullanmak için bir etkinlik oluşturmak gösterilmiştir.  
  
> [!IMPORTANT]
>  WCF örnekleri makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  Bu dizin mevcut değilse, bu sayfanın üstündeki örnek bağlantıya tıklayın. Bu bağlantıyı indirir ve tüm yükler Not [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, ve [!INCLUDE[infocard](../../../../includes/infocard-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a>FindInSqlTable etkinliği ayrıntıları  
 Bu etkinlik, kullanıcıların LINQ-SQL kullanarak bir veritabanındaki tablolarda bulunan sorgu varlıklara sağlar. Etkinlik kullanıcılarının biçiminde sonuçlara filtre uygulamak için bir lambda ifadesi bir LINQ koşul da sağlayabilir. Hiçbir koşulu sağlanırsa, tüm tablo döndürülür. Aşağıdaki tabloda özellik ve dönüş değerleri etkinliğinin ayrıntılarını verir.  
  
|Özellik veya dönüş değeri|Açıklama|  
|------------------------------|-----------------|  
|`Collection` Özelliği|Kaynak koleksiyonu belirten gerekli bir özellik.|  
|`Predicate` Özelliği|Filtre koleksiyonu için bir lambda ifadesi biçiminde belirtir gerekli bir özellik.|  
|Dönüş Değeri|Filtrelenmiş koleksiyonu.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Özel Etkinlik kullanan örnek kod  
 Aşağıdaki kod örneğinde `FindInSqlTable` adlı bir SQL Server tablodaki tüm satırları bulmak için özel etkinlik `Employee` nerede `Role` sütun eşittir `SDE`.  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Bir komut istemi açın.  
  
2.  Bu örnek içeren klasöre gidin.  
  
3.  Setup.cmd komut dosyasını çalıştırın.  
  
    > [!NOTE]
    >  Yerel makinenizde SQL Server Express örnek veritabanını yüklemek Setup.cmd betik çalışır. Diğer SQL server örneği yüklemek istiyorsanız, Setup.cmd düzenleyin.  
  
     Setup.cmd komut dosyası aşağıdaki eylemleri gerçekleştirir.:  
  
    -   LinqToSqlSample adlı bir veritabanı oluşturur.  
  
    -   Rolleri bir tablo oluşturur.  
  
    -   Çalışanlar adında bir tablo oluşturur.  
  
    -   3 kayıtları rolleri tabloya ekler.  
  
    -   12 kayıtları çalışanların tabloya ekler.  
  
4.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], LinqToSQL.sln çözüm dosyasını açın.  
  
5.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
6.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a>LinqToSql örnek veritabanını kaldırmak için  
  
1.  Bir komut istemi açın.  
  
2.  Bu örnek içeren klasöre gidin.  
  
3.  Cleanup.cmd komut dosyasını çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL](http://go.microsoft.com/fwlink/?LinkId=150376)  
 [Başlarken (LINQ-SQL)](http://go.microsoft.com/fwlink/?LinkId=150377)
