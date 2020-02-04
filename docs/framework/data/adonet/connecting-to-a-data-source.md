---
title: Veri Kaynağına Bağlanma
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 84dc15c0965b7ac8209bd9115d611162e57d6dda
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980255"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>ADO.NET içinde bir veri kaynağına bağlanma
ADO.NET ' de, bir bağlantı dizesinde gerekli kimlik doğrulama bilgilerini sağlayarak belirli bir veri kaynağına bağlanmak için bir **bağlantı** nesnesi kullanırsınız. Kullandığınız **bağlantı** nesnesi, veri kaynağının türüne bağlıdır.  
  
 .NET Framework eklenen her bir .NET Framework veri sağlayıcısının bir <xref:System.Data.Common.DbConnection> nesnesi vardır: Veri Sağlayıcısı için .NET Framework OLE DB bir <xref:System.Data.OleDb.OleDbConnection> nesnesini içerir, .NET Framework veri sağlayıcısı SQL Server bir nesne içerir, ODBC için <xref:System.Data.SqlClient.SqlConnection> .NET Framework bir veri sağlayıcısı nesnesi içerir ve Oracle için <xref:System.Data.Odbc.OdbcConnection> .NET Framework bir Veri Sağlayıcısı nesnesi içerir.  
  
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
