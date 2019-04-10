---
title: 'Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
ms.openlocfilehash: 78d6c9287c5c69c41bd2f50abd8d57dcd1cb4e06
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337584"
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a>Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme
Bu konuda kullanarak kavramsal modeline karşı komut yürütme işlemi gösterilmektedir bir <xref:System.Data.EntityClient.EntityCommand>ve nasıl alınacağını <xref:System.Data.Metadata.Edm.PrimitiveType> kullanarak sonuçları bir <xref:System.Data.EntityClient.EntityDataReader>.  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekte, kodu çalıştırmak için  
  
1. Ekleme [AdventureWorks satışları modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) projenize ve projenizi kullanmak üzere yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Örnek  
 Bu örnek döndüren bir sorgu yürütür bir <xref:System.Data.Metadata.Edm.PrimitiveType> sonucu. Bağımsız değişken olarak aşağıdaki sorguyu geçirirseniz `ExecutePrimitiveTypeQuery` işlevi, işlev ortalama liste fiyatı tüm görüntüler `Products`:  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 Aşağıdaki gibi parametreli bir sorgu başarılı olursa <xref:System.Data.EntityClient.EntityParameter> nesneleri için <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> özelliği <xref:System.Data.EntityClient.EntityCommand> nesne.  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity Framework için EntityClient Sağlayıcısı](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
