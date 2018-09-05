---
title: LINQ to SQL örneği
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 83dc8433459f64860baaca2e8309fbc85e2bb3a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515374"
---
# <a name="linq-to-sql-sample"></a>LINQ to SQL örneği
Bu örnek, LINQ, SQL Server veritabanlarını tablodan SQL sorgu varlıklara kullanmak için bir etkinlik oluşturma işlemini gösterir.  
  
> [!IMPORTANT]
>  WCF örnekleri makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  Bu dizin mevcut değil, bu sayfanın üstündeki örnek bağlantıya tıklayın. Bu bağlantı indirir ve yükler tüm Not [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, ve [!INCLUDE[infocard](../../../../includes/infocard-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a>FindInSqlTable için etkinlik ayrıntıları  
 Bu etkinlik, LINQ to SQL kullanarak bir veritabanındaki tablolarda bulunan sorgu varlıklara kullanıcıların sağlar. Kullanıcı etkinliğinin bir LINQ koşul sonuçları filtrelemek için bir lambda ifadesinin biçiminde de sağlayabilirsiniz. Hiçbir koşul sağlanırsa, tüm tablo döndürülür. Aşağıdaki tabloda özellik ve dönüş değerleri etkinliğinin ayrıntıları.  
  
|Özellik ya da dönüş değeri|Açıklama|  
|------------------------------|-----------------|  
|`Collection` Özelliği|Kaynak koleksiyonu belirtir. gerekli bir özellik.|  
|`Predicate` Özelliği|Filtre koleksiyonu için bir lambda ifadesinin biçiminde belirtir. gerekli bir özellik.|  
|Dönüş Değeri|Filtrelenmiş koleksiyonu.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Özel Etkinlik kullanan kod örneği  
 Aşağıdaki kod örneğinde `FindInSqlTable` adlı bir SQL Server tablodaki tüm satırları bulmak için özel etkinlik `Employee` burada `Role` sütun eşittir `SDE`.  
  
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
    >  Setup.cmd betik, yerel makinenizde SQL Server Express örnek veritabanını yüklemek çalışır. Diğer SQL server örneği'nde yüklemek istiyorsanız, Setup.cmd düzenleyin.  
  
     Setup.cmd komut aşağıdaki eylemleri yapar.:  
  
    -   LinqToSqlSample adlı bir veritabanı oluşturur.  
  
    -   Roller bir tablo oluşturur.  
  
    -   Çalışanlar bir tablo oluşturur.  
  
    -   3 kayıtları rolleri tabloya ekler.  
  
    -   12 kayıtları çalışanlar tabloya ekler.  
  
4.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], LinqToSQL.sln çözüm dosyasını açın.  
  
5.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
6.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a>LinqToSql örnek veritabanını kaldırmak için  
  
1.  Bir komut istemi açın.  
  
2.  Bu örnek içeren klasöre gidin.  
  
3.  Cleanup.cmd komut dosyasını çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL](https://go.microsoft.com/fwlink/?LinkId=150376)  
 [Başlarken (LINQ to SQL)](https://go.microsoft.com/fwlink/?LinkId=150377)
