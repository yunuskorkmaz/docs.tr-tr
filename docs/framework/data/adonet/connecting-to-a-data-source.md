---
title: Veri Kaynağına Bağlanma
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: a14fe179cf2fc8714a54e52252c53bd71346cad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287083"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>ADO.NET içinde bir veri kaynağına bağlanma

ADO.NET ' de, bir bağlantı dizesinde gerekli kimlik doğrulama bilgilerini sağlayarak belirli bir veri kaynağına bağlanmak için bir **bağlantı** nesnesi kullanırsınız. Kullandığınız **bağlantı** nesnesi, veri kaynağının türüne bağlıdır.  
  
 .NET Framework eklenen her bir .NET Framework veri sağlayıcısı bir nesnesine sahiptir <xref:System.Data.Common.DbConnection> : OLE DB için .NET Framework veri sağlayıcısı bir nesne içeriyorsa, .NET Framework için veri sağlayıcısı SQL Server bir nesne içerir, ODBC için .NET Framework veri sağlayıcısı bir nesnesi içerir <xref:System.Data.OleDb.OleDbConnection> <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.Odbc.OdbcConnection> ve Oracle için <xref:System.Data.OracleClient.OracleConnection> .NET Framework veri sağlayıcısı bir nesnesi içerir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bağlantı kuruluyor](establishing-the-connection.md)\
 Bir veri kaynağıyla bağlantı kurmak için bir **bağlantı** nesnesinin nasıl kullanılacağını açıklar.  
  
 [Bağlantı olayları](connection-events.md)\
 Bir veri kaynağından bilgilendirici iletileri almak için bir **InfoMessage** olayının nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı dizeleri](connection-strings.md)
- [Bağlantı Havuzu](connection-pooling.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [İşlemler ve Eşzamanlılık](transactions-and-concurrency.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
