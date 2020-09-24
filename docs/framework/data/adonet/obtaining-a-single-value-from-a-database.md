---
title: Veritabanından Tek Değer Alma
description: ADO.NET içinde tek bir değer döndürmeyi öğrenin. Bu örnek kod, ekli bir kayıt için kimlik sütunu değerini döndürür.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 9ce29bc1321814bd60cfaacd222fc55a3fbf12ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150732"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Veritabanından Tek Değer Alma

Tablo veya veri akışı biçiminde değil, yalnızca tek bir değer olan veritabanı bilgilerini döndürmeniz gerekebilir. Örneğin, COUNT ( \* ), Sum (price) veya AVG (Quantity) gibi bir toplama işlevinin sonucunu döndürmek isteyebilirsiniz. **Komut** nesnesi, **ExecuteReader metodunu** yöntemini kullanarak tek değerler döndürme yeteneği sağlar. **ExecuteReader metodunu** yöntemi, bir skaler değer olarak sonuç kümesinin ilk satırının ilk sütununun değeri olarak döndürür.  
  
 Aşağıdaki kod örneği, kullanarak veritabanına yeni bir değer ekler <xref:System.Data.SqlClient.SqlCommand> . <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>Yöntemi, ekli kaydın kimlik sütunu değerini döndürmek için kullanılır.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Komutlar ve Parametreler](commands-and-parameters.md)
- [Komut Yürütme](executing-a-command.md)
- [DbConnection, DbCommand ve DbException](dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
