---
title: Örnek SQL Server veritabanları için ADO.NET kod örnekleri edinin
description: SQL Server ve yönetim araçlarının yanı sıra ADO.NET belgeler, kod örnekleri kullanılan örnek SQL Server veritabanları indirme
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 5580f06f3d28ed6d70f75b619498ac8de7bc3326
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307298"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>Örnek veritabanları için ADO.NET kod örnekleri edinin

Örnekler ve izlenecek yollar, bir dizi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] örnek SQL Server veritabanları ve SQL Server Express belgeleri kullanın. Microsoft bu ürünlerin ücretsiz olarak indirebilirsiniz.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>Northwind örnek veritabanını almak için SQL Server

Betiği indirin `instnwnd.sql` oluşturmak ve SQL Server için Northwind örnek veritabanını yüklemek için aşağıdaki GitHub deposundan:

[Northwind ve pubs örnek veritabanlarını Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Northwind veritabanı kullanabilmeniz için indirilen çalıştırmak zorunda `instnwnd.sql` komut dosyası kullanarak SQL Server örneği üzerinde veritabanı yeniden [SQL Server Management Studio](#get_ssms) veya benzer bir araç. Depodaki benioku dosyasındaki yönergeleri izleyin.

> [!TIP]
> Microsoft Access için Northwind veritabanı arıyorsanız bkz [Microsoft Access için Northwind örnek veritabanını yüklemek](#northwind_access).

## <a name="northwind_access"></a> Microsoft Access için Northwind örnek veritabanıyla kurulan Al

Microsoft Access için Northwind örnek veritabanı Microsoft Download Center kullanılabilir değil. Northwind doğrudan erişim içinde yüklemek için şunları yapın:

1. Erişimi'ni açın.

1. ENTER **Northwind** içinde **çevrimiçi şablonlar için arama** kutusuna ve ardından **Enter**.

1. Sonuçlar ekranda işaretleyin **Northwind**. Northwind veritabanı açıklaması ile yeni bir pencere açılır.

1. Yeni pencerede, **dosya adı** metin kutusunda, Northwind veritabanı kopyası için bir dosya adı sağlayın.

1. **Oluştur**’u seçin. Erişim, Northwind veritabanına yükler ve dosya hazırlar.

1. Bu işlem tamamlandığında veritabanı ile bir Hoş Geldiniz ekranı açılır.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>AdventureWorks örnek veritabanını almak için SQL Server

AdventureWorks örnek veritabanını SQL Server aşağıdaki GitHub deposundan indirin:

[AdventureWorks örnek veritabanları](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Bir veritabanı yedeğinin indirdikten sonra (\*.bak) dosyaları, SQL Server örneğine SQL Server Management Studio (SSMS) kullanarak yedeklemeyi geri yükleme. Bkz: [alma SQL Server Management Studio'yu](#get_ssms).

## <a name="get_ssms"></a> SQL Server Management Studio'yu edinin
Görüntülemek veya karşıdan yüklediğiniz bir veritabanı değiştirmek istiyorsanız, SQL Server Management Studio (SSMS) kullanabilirsiniz. SSMS aşağıdaki sayfasından indirin:

[SQL Server Management Studio'yu (SSMS) indirin](/sql/ssms/download-sql-server-management-studio-ssms) 

Ayrıca, görüntüleyin ve Visual Studio tümleşik geliştirme ortamı (IDE) veritabanlarında yönetin. İçinde [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), veritabanından bağlanma **SQL Server Nesne Gezgini**, ya da veritabanında veri bağlantısı oluşturma **Sunucu Gezgini**. Bu Gezgini bölmeden açın **görünümü** menüsü.

## <a name="get_sql"></a> SQL Server Express edinin

SQL Server Express, SQL Server, uygulamaları yeniden dağıtabilirsiniz, ücretsiz, giriş düzeyi bir sürümüdür. SQL Server Express'i aşağıdaki sayfadan indirebilirsiniz:
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

Kullanıyorsanız [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB Visual Studio'nun Ücretsiz Community edition, ek olarak profesyonel ve üzeri sürümleri dahil edilir.  

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
