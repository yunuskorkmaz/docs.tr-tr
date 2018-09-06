---
title: Fabrika modeline genel bakış
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 618a7c6d82facdda05517e4c201c266b84ac889c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855197"
---
# <a name="factory-model-overview"></a>Fabrika modeline genel bakış
ADO.NET 2.0 sunulan yeni taban sınıflardaki <xref:System.Data.Common> ad alanı. Temel sınıflar abstract, bunlar doğrudan oluşturulamaz anlamına gelir. İçerirler <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, ve <xref:System.Data.Common.DbDataAdapter> ve .NET Framework veri sağlayıcıları tarafından aşağıdaki gibi paylaşılan <xref:System.Data.SqlClient> ve <xref:System.Data.OleDb>. Temel sınıflar eklenmesi, yeni arayüz oluşturmaya gerek olmadan .NET Framework veri sağlayıcıları için işlevselliği ekleme basitleştirir.  
  
 ADO.NET 2.0, belirli veri sağlayıcısında bağlı olmayan genel veri erişim kodu yazmak bir geliştirici sağlayan soyut taban sınıfları de kullanıma sunulmuştur.  
  
## <a name="the-factory-design-pattern"></a>Fabrika tasarım deseni  
 Sağlayıcı-bağımsız kod yazmak için programlama modeli arasında birden çok sağlayıcı access veritabanları için tek bir API kullanır "fabrikası" tasarım desenini kullanımı temel alır. Yalnızca gerçek Fabrika gibi diğer nesneleri oluşturmak için özel bir nesne kullanımı için çağırdığı gibi bu düzen aptly adlandırılır. Fabrika tasarım deseni daha ayrıntılı bir açıklaması için bkz. "[ASP.NET 2.0 ve ADO.NET 2.0 genel veri erişim kodu yazarken](https://go.microsoft.com/fwlink/?LinkId=55915)" ve "Genel kodlama ile ADO.NET 2.0 temel sınıflar ve fabrikaları" [ http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp ](https://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) MSDN'de.  
  
 ADO.NET 2.0 ile başlayarak <xref:System.Data.Common.DbProviderFactories> sağlar sınıfını `static` (veya `Shared` Visual Basic'te) oluşturmak için yöntemleri bir <xref:System.Data.Common.DbProviderFactory> örneği. Örnek, ardından sağlayıcı bilgileri ve çalışma zamanında sağlanan bağlantı dizesi göre doğru türü kesin belirlenmiş bir nesne döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DbProviderFactory Alma](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand ve DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [DbDataAdapter ile Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
