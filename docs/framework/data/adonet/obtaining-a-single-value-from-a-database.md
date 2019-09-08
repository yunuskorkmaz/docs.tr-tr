---
title: Veritabanından Tek Değer Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: fb43d21546a0e98e87aab23db9213309b62320b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794740"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Veritabanından Tek Değer Alma
Tablo veya veri akışı biçiminde değil, yalnızca tek bir değer olan veritabanı bilgilerini döndürmeniz gerekebilir. Örneğin, Count (\*), Sum (price) veya AVG (Quantity) gibi bir toplama işlevinin sonucunu döndürmek isteyebilirsiniz. **Komut** nesnesi, **ExecuteReader metodunu** yöntemini kullanarak tek değerler döndürme yeteneği sağlar. **ExecuteReader metodunu** yöntemi, bir skaler değer olarak sonuç kümesinin ilk satırının ilk sütununun değeri olarak döndürür.  
  
 Aşağıdaki kod örneği, kullanarak <xref:System.Data.SqlClient.SqlCommand>veritabanına yeni bir değer ekler. <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Yöntemi, ekli kaydın kimlik sütunu değerini döndürmek için kullanılır.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Komutlar ve Parametreler](commands-and-parameters.md)
- [Komut Yürütme](executing-a-command.md)
- [DbConnection, DbCommand ve DbException](dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
