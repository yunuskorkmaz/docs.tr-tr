---
title: ADO.NET içinde bir veri kaynağına bağlanma
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 01e4048fb9c7b53b1b1907d1965f822b9a4644a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786769"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>ADO.NET içinde bir veri kaynağına bağlanma
ADO.NET ' de, bir bağlantı dizesinde gerekli kimlik doğrulama bilgilerini sağlayarak belirli bir veri kaynağına bağlanmak için bir **bağlantı** nesnesi kullanırsınız. Kullandığınız **bağlantı** nesnesi, veri kaynağının türüne bağlıdır.  
  
 .NET Framework eklenen her .NET Framework veri sağlayıcısı bir <xref:System.Data.Common.DbConnection> nesnesine sahiptir: OLE DB için .NET Framework veri sağlayıcısı bir nesne <xref:System.Data.OleDb.OleDbConnection> içeriyorsa, .NET Framework veri sağlayıcısı SQL Server bir <xref:System.Data.SqlClient.SqlConnection> nesnesi içerir. ODBC için net Framework veri sağlayıcısı bir <xref:System.Data.Odbc.OdbcConnection> nesne içerir ve Oracle için .NET Framework veri sağlayıcısı bir <xref:System.Data.OracleClient.OracleConnection> nesnesi içerir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bağlantı Kurma](establishing-the-connection.md)  
 Bir veri kaynağıyla bağlantı kurmak için bir **bağlantı** nesnesinin nasıl kullanılacağını açıklar.  
  
 [Bağlantı Olayları ](connection-events.md)  
 Bir veri kaynağından bilgilendirici iletileri almak için bir **InfoMessage** olayının nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizeleri](connection-strings.md)
- [Bağlantı Havuzu](connection-pooling.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [İşlemler ve Eşzamanlılık](transactions-and-concurrency.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
