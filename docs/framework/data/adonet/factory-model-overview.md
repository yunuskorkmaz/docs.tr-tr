---
title: "Fabrika modeline genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0194cd6789ae6ddebeeee65abf1a4fca4a2bc0d6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="factory-model-overview"></a>Fabrika modeline genel bakış
ADO.NET 2.0 sunulan yeni temel sınıflarda <xref:System.Data.Common> ad alanı. Temel sınıflar soyut, bunlar doğrudan başlatılamaz anlamına gelir. İçerirler <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, ve <xref:System.Data.Common.DbDataAdapter> ve .NET Framework veri sağlayıcıları tarafından aşağıdaki gibi paylaşılan <xref:System.Data.SqlClient> ve <xref:System.Data.OleDb>. Temel sınıflar eklenmesi, yeni arabirimleri oluşturmak zorunda kalmadan .NET Framework Veri sağlayıcılarına ekleme işlevselliği basitleştirir.  
  
 ADO.NET 2.0 ayrıca belirli veri sağlayıcısında bağlı olmayan bir genel veri erişim kodu yazmak bir geliştirici etkinleştirmek soyut taban sınıfları sunulmuştur.  
  
## <a name="the-factory-design-pattern"></a>Fabrika tasarım deseni  
 Sağlayıcı bağımsız kod yazmak için programlama modelini arasında birden çok sağlayıcı access veritabanları için tek bir API kullanır "fabrika" tasarım deseni kullanımını temel alır. Yalnızca bir gerçek fabrikası gibi diğer nesneler oluşturmak için özel bir nesne kullanımı için çağırır gibi bu deseni aptly adlandırılır. Fabrika tasarım deseni daha ayrıntılı bir açıklaması için bkz: "[ASP.NET 2.0 ve ADO.NET 2.0 genel veri erişim kod yazma](http://go.microsoft.com/fwlink/?LinkId=55915)" ve "Genel kodlama ile ADO.NET 2.0 taban sınıfları ve oluşturucuları" [http:// MSDN.microsoft.com/library/default.asp?url=/library/dnvs05/HTML/vsgenerics.asp](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) konusuna bakın.  
  
 ADO.NET 2.0 ile başlayan <xref:System.Data.Common.DbProviderFactories> SAX `static` (veya `Shared` Visual Basic'te) oluşturmak için yöntemler bir <xref:System.Data.Common.DbProviderFactory> örneği. Örnek ardından sağlayıcı bilgilerini ve çalışma zamanında sağlanan bağlantı dizesi göre doğru kesin türü belirtilmiş bir nesne döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DbProviderFactory Alma](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand ve DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [DbDataAdapter ile Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
