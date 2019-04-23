---
title: Fabrika Modeline Genel Bakış
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 3b1d438ce5a7dbb22772d6c5dc97f196b3263d38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221840"
---
# <a name="factory-model-overview"></a>Fabrika Modeline Genel Bakış
ADO.NET 2.0 sunulan yeni taban sınıflardaki <xref:System.Data.Common> ad alanı. Temel sınıflar abstract, bunlar doğrudan oluşturulamaz anlamına gelir. İçerirler <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, ve <xref:System.Data.Common.DbDataAdapter> ve .NET Framework veri sağlayıcıları tarafından aşağıdaki gibi paylaşılan <xref:System.Data.SqlClient> ve <xref:System.Data.OleDb>. Temel sınıflar eklenmesi, yeni arayüz oluşturmaya gerek olmadan .NET Framework veri sağlayıcıları için işlevselliği ekleme basitleştirir.  
  
 ADO.NET 2.0, belirli veri sağlayıcısında bağlı olmayan genel veri erişim kodu yazmak bir geliştirici sağlayan soyut taban sınıfları de kullanıma sunulmuştur.  
  
## <a name="the-factory-design-pattern"></a>Fabrika tasarım deseni  
 Sağlayıcı-bağımsız kod yazmak için programlama modeli arasında birden çok sağlayıcı access veritabanları için tek bir API kullanır "fabrikası" tasarım desenini kullanımı temel alır. Yalnızca gerçek Fabrika gibi diğer nesneleri oluşturmak için özel bir nesne kullanımı için çağırdığı gibi bu düzen aptly adlandırılır. Fabrika tasarım deseni daha ayrıntılı bir açıklaması için bkz. [yazma genel veri erişim kodu ASP.NET 2.0 ve ADO.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=55915).
  
 ADO.NET 2.0 ile başlayarak <xref:System.Data.Common.DbProviderFactories> sağlar sınıfını `static` (veya `Shared` Visual Basic'te) oluşturmak için yöntemleri bir <xref:System.Data.Common.DbProviderFactory> örneği. Örnek, ardından sağlayıcı bilgileri ve çalışma zamanında sağlanan bağlantı dizesi göre doğru türü kesin belirlenmiş bir nesne döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DbProviderFactory Alma](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand ve DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [DbDataAdapter ile Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
