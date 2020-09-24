---
title: ADO.NET kod örnekleri için örnek SQL Server veritabanlarını alın
description: ADO.NET belgelerindeki kod örneklerinde kullanılan örnek SQL Server veritabanlarını ve ayrıca SQL Server ve yönetim araçlarını indirin
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: f7c0d1eb0089a6bfabc92e1deecf563c3e59cc6a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156062"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>ADO.NET kod örnekleri için örnek veritabanlarını al

Belgelerde birçok örnek ve İzlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] örnek SQL Server veritabanları ve SQL Server Express kullanır. Bu ürünleri Microsoft 'tan ücretsiz olarak indirebilirsiniz.

## <a name="get-the-northwind-sample-database-for-sql-server"></a>SQL Server için Northwind örnek veritabanını alın

`instnwnd.sql`SQL Server Için Northwind örnek veritabanı oluşturmak ve yüklemek üzere aşağıdaki GitHub deposundan betiği indirin:

[Microsoft SQL Server için Northwind ve pubs örnek veritabanları](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Northwind veritabanını kullanabilmeniz `instnwnd.sql` için, [SQL Server Management Studio](#get_ssms) veya benzer bir aracı kullanarak veritabanını bir SQL Server örneğine yeniden oluşturmak üzere indirilen betik dosyasını çalıştırmanız gerekir. Depodaki Benioku dosyasındaki yönergeleri izleyin.

> [!TIP]
> Microsoft Access için Northwind veritabanına bakıyorsanız, bkz. [Microsoft Access Için Northwind örnek veritabanını Install](#northwind_access).

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a> Microsoft Access için Northwind örnek veritabanını alın

Microsoft Access için Northwind örnek veritabanı Microsoft Indirme Merkezi ' nde bulunmamaktadır. Northwind 'yi doğrudan erişim içinden yüklemek için aşağıdaki işlemleri yapın:

1. Açık erişim.

1. **Çevrimiçi şablon ara** kutusuna **Northwind** girin ve ardından **ENTER**' u seçin.

1. Sonuçlar ekranında **Northwind**' i seçin. Northwind veritabanının açıklamasıyla birlikte yeni bir pencere açılır.

1. Yeni pencerede, **dosya adı** metin kutusunda, Northwind veritabanının kopyası için bir dosya adı belirtin.

1. **Oluştur**’u seçin. Access, Northwind veritabanını indirir ve dosyayı hazırlar.

1. Bu işlem tamamlandığında, veritabanı bir karşılama ekranı ile açılır.

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>SQL Server için AdventureWorks örnek veritabanını al

Aşağıdaki GitHub deposundan SQL Server için AdventureWorks örnek veritabanını indirin:

[AdventureWorks örnek veritabanları](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

Veritabanı yedekleme ( \* . bak) dosyalarından birini indirdikten sonra, SQL Server Management Studio (SSMS) kullanarak SQL Server bir örneğine yedeklemeyi geri yükleyin. Bkz. [Get SQL Server Management Studio](#get_ssms).

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a> SQL Server Management Studio al

İndirdiğiniz bir veritabanını görüntülemek veya değiştirmek istiyorsanız, SQL Server Management Studio (SSMS) kullanabilirsiniz. SSMS 'yi aşağıdaki sayfadan indirin:

[SQL Server Management Studio’yu (SSMS) İndirme](/sql/ssms/download-sql-server-management-studio-ssms)

Ayrıca, Visual Studio tümleşik geliştirme ortamında (IDE) veritabanlarını görüntüleyebilir ve yönetebilirsiniz. [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)'da **SQL Server Nesne Gezgini**veritabanına bağlanın veya **Sunucu Gezgini**veritabanında veritabanına bir veri bağlantısı oluşturun. **Görünüm** menüsünden bu gezgin bölmelerini açın.

## <a name="get-sql-server-express"></a><a name="get_sql"></a> SQL Server Express al

SQL Server Express, uygulamalarla yeniden dağıtacağınız SQL Server ücretsiz, giriş düzeyi bir sürümdür. Aşağıdaki sayfadan SQL Server Express indirin:
  
[SQL Server Express sürümü](https://www.microsoft.com/sql-server/sql-server-editions-express)

[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)kullanıyorsanız, SQL Server Express LocalDB, Visual Studio 'Nun ücretsiz topluluk sürümüne, Ayrıca profesyonel ve daha yüksek sürümlere dahil edilmiştir.  

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started.md)
