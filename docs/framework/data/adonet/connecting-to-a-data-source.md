---
title: ADO.NET'te veri kaynağına bağlanma
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: c04624be758e4bc7c8b1981ad6a9dc44430d62b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879989"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>ADO.NET'te veri kaynağına bağlanma
ADO.NET kullandığınız bir **bağlantı** bağlantı dizesinde gerekli kimlik doğrulama bilgileri vererek belirli bir veri kaynağına bağlanmak için nesne. **Bağlantı** kullandığınız nesne veri kaynağı türüne bağlıdır.  
  
 .NET Framework ile dahil her .NET Framework veri sağlayıcısı sahip bir <xref:System.Data.Common.DbConnection> nesne: OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbConnection> nesnesi, SQL Server için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.SqlClient.SqlConnection> nesnesi. ODBC için NET Framework Veri Sağlayıcısı'nı içeren bir <xref:System.Data.Odbc.OdbcConnection> nesne ve Oracle için .NET Framework Veri Sağlayıcısı'nı içeren bir <xref:System.Data.OracleClient.OracleConnection> nesne.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bağlantı Kurma](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 Nasıl kullanılacağını açıklayan bir **bağlantı** bir veri kaynağına bağlantı kurmak için nesne.  
  
 [Bağlantı Olayları ](../../../../docs/framework/data/adonet/connection-events.md)  
 Nasıl kullanılacağını açıklayan bir **InfoMessage** bir veri kaynağından bilgi iletilerini almak için olay.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)
- [Bağlantı Havuzu](../../../../docs/framework/data/adonet/connection-pooling.md)
- [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
