---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: b5f2dbb687348afac98247cb21bae831dea26bfe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183318"
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
