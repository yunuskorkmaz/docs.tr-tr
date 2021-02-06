---
description: 'Daha fazla bilgi edinin: DbProviderFactory'
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 735c78a846fc8df31a922acf90e587c6d96f4995
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651268"
---
# <a name="dbproviderfactories"></a>DbProviderFactories

<xref:System.Data.Common>Ad alanı, <xref:System.Data.Common.DbProviderFactory> belirli veri kaynaklarıyla çalışacak örnekler oluşturmak için sınıflar sağlar. Bir <xref:System.Data.Common.DbProviderFactory> örnek oluşturup veri sağlayıcısına ilişkin bilgileri geçirdiğinizde, `DbProviderFactory` sağlandığı bilgilere göre döndürülecek doğru ve kesin belirlenmiş bağlantı nesnesini belirleyebilir.  
  
 .NET Framework sürüm 4 ' ten başlayarak,, ve gibi veri <xref:System.Data.Odbc> sağlayıcıları <xref:System.Data.OleDb> <xref:System.Data.SqlClient> <xref:System.Data.OracleClient> artık machine.config dosyasında listelenmemiştir, ancak özel sağlayıcılar burada listelenmeye devam edecektir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Fabrika Modeline Genel Bakış](factory-model-overview.md)  
 Fabrika tasarımı düzenine ve programlama arabirimine genel bir bakış sağlar.  
  
 [DbProviderFactory Alma](obtaining-a-dbproviderfactory.md)  
 Yüklü veri sağlayıcılarının nasıl ekleneceğini ve kaynağından bir oluşturma işlemlerinin nasıl yapılacağını gösterir <xref:System.Data.Common.DbConnection> `DbProviderFactory` .  
  
 [DbConnection, DbCommand ve DbException](dbconnection-dbcommand-and-dbexception.md)  
 Ve ' nin nasıl oluşturulduğunu <xref:System.Data.Common.DbCommand> <xref:System.Data.Common.DbDataReader> ve kullanarak veri hatalarının nasıl işleneceğini gösterir <xref:System.Data.Common.DbException> .  
  
 [DbDataAdapter ile Verileri Değiştirme](modifying-data-with-a-dbdataadapter.md)  
 <xref:System.Data.Common.DbCommandBuilder> <xref:System.Data.Common.DbDataAdapter> Verileri almak ve değiştirmek için ile birlikte nasıl kullanılacağını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
