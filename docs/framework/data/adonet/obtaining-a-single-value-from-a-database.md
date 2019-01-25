---
title: Bir veritabanından tek değer alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: e362a71f902739663961099cf2f43dff90b4743c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711466"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Bir veritabanından tek değer alma
Yalnızca tek bir değer dönüş veritabanı bilgileri yerine bir tablo veya veri akışını biçiminde gerekebilir. Örneğin, sonuç sayısı gibi bir toplama işlevinin isteyebilirsiniz (\*), SUM(Price) veya AVG(Quantity). **Komut** nesnesi kullanarak tek değerler döndürülecek yeteneği sağlar **ExecuteScalar** yöntemi. **ExecuteScalar** yöntemi döndürür, skaler değer olarak, sonuç kümesi ilk satırının ilk sütununu değeri.  
  
 Aşağıdaki kod örneği kullanarak veritabanını yeni bir değer ekler. bir <xref:System.Data.SqlClient.SqlCommand>. <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Yöntemi eklenen kaydın Kimlik sütununda değer döndürmek için kullanılır.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Komut Yürütme](../../../../docs/framework/data/adonet/executing-a-command.md)
- [DbConnection, DbCommand ve DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
