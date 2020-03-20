---
title: ADO.NET kod örnekleri için örnek SQL Server veritabanlarını edinin
description: ADO.NET belgelerinde kod örneklerinde kullanılan örnek SQL Server veritabanlarının yanı sıra SQL Server ve yönetim araçlarını indirin
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 19d659cbe8f39d27b71dc59c738355f12fce92a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148393"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>kod örnekleri ADO.NET için örnek veritabanlarını edinin

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Belgelerdeki bir dizi örnek ve gözden geçirme de örnek SQL Server veritabanları nı ve SQL Server Express'i kullanır. Bu ürünleri Microsoft'tan ücretsiz olarak indirebilirsiniz.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>SQL Server için Northwind örnek veritabanını edinin

SQL Server `instnwnd.sql` için Northwind örnek veritabanını oluşturmak ve yüklemek için komut dosyasını aşağıdaki GitHub deposundan indirin:

[Northwind ve pubörnekleri Microsoft SQL Server için örnek veritabanları](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Northwind veritabanını kullanabilmek için, SQL Server `instnwnd.sql` [Management Studio](#get_ssms) veya benzer bir aracı kullanarak veritabanını SQL Server'ın bir örneğinde yeniden oluşturmak için indirilen komut dosyası dosyasını çalıştırmanız gerekir. Depodaki Readme dosyasındaki yönergeleri izleyin.

> [!TIP]
> Microsoft Access için Northwind veritabanını arıyorsanız, [Bkz. Microsoft Access için Northwind örnek veritabanını yükleyin.](#northwind_access)

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a>Microsoft Access için Northwind örnek veritabanını edinin

Microsoft Access için Northwind örnek veritabanı Microsoft İndirme Merkezi'nde kullanılamaz. Northwind'i doğrudan Access içinden yüklemek için aşağıdaki leri yapın:

1. Erişimi Aç.

1. **Çevrimiçi Şablonları Ara** kutusuna **Northwind'i** girin ve ardından **Enter'u**seçin.

1. Sonuçlar ekranında **Northwind'i**seçin. Northwind veritabanının açıklamasıyla birlikte yeni bir pencere açılır.

1. Yeni pencerede, **Dosya Adı** metin kutusunda, Northwind veritabanı kopyanız için bir dosya adı sağlayın.

1. **Oluştur'u**seçin. Access Northwind veritabanını karşıdan yükler ve dosyayı hazırlar.

1. Bu işlem tamamlandığında, veritabanı karşılama ekranıyla açılır.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>SQL Server için AdventureWorks örnek veritabanını edinin

SQL Server için AdventureWorks örnek veritabanını aşağıdaki GitHub deposundan indirin:

[AdventureWorks örnek veritabanları](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Veritabanı yedekleme (.bak)\*dosyalarından birini indirdikten sonra, SQL Server Management Studio (SSMS) kullanarak yedeklemeyi SQL Server örneğine geri yükleyin. Bkz. [SQL Server Management Studio alın.](#get_ssms)

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a>SQL Server Management Studio alın
İndirdiğiniz bir veritabanını görüntülemek veya değiştirmek istiyorsanız, SQL Server Management Studio 'yı (SSMS) kullanabilirsiniz. Aşağıdaki sayfadan SSMS indirin:

[SQL Server Management Studio’yu (SSMS) İndirme](/sql/ssms/download-sql-server-management-studio-ssms)

Ayrıca Visual Studio tümleşik geliştirme ortamında (IDE) veritabanlarını görüntüleyebilir ve yönetebilirsiniz. [Visual](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)Studio'da, SQL **Server Object Explorer'dan**veritabanına bağlanın veya **Server Explorer'daki**veritabanına bir Veri Bağlantısı oluşturun. Bu gezgin bölmelerini **Görünüm** menüsünden açın.

## <a name="get-sql-server-express"></a><a name="get_sql"></a>SQL Server Express alın

SQL Server Express, SQL Server'ın uygulamalarla yeniden dağıtabileceğiniz ücretsiz, giriş seviyesi bir sürümüdür. SQL Server Express'i aşağıdaki sayfadan indirin:
  
[SQL Server Express Sürümü](https://www.microsoft.com/sql-server/sql-server-editions-express)

[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)kullanıyorsanız, SQL Server Express LocalDB Visual Studio'nun ücretsiz Topluluk baskısına, Professional ve daha yüksek sürümlere dahildir.  

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started.md)
