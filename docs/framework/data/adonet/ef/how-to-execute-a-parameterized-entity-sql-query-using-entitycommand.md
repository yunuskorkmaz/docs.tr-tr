---
title: 'Nasıl yapılır: EntityCommand Kullanarak Parametreli Entity SQL Sorgusu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: d66b77553e677c42ccedf7e66bf4f5763db92fa4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192236"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a>Nasıl yapılır: EntityCommand Kullanarak Parametreli Entity SQL Sorgusu Yürütme

Bu konu [!INCLUDE[esql](../../../../../includes/esql-md.md)] , bir nesnesi kullanarak parametreleri olan bir sorgunun nasıl yürütüleceğini gösterir <xref:System.Data.EntityClient.EntityCommand> .  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekteki kodu çalıştırmak için  
  
1. Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın. Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, iki parametreli bir sorgu dizesi oluşturmayı gösterir. Daha sonra bir oluşturur <xref:System.Data.EntityClient.EntityCommand> , bunun koleksiyonuna iki parametre ekler <xref:System.Data.EntityClient.EntityParameter> <xref:System.Data.EntityClient.EntityCommand> ve öğe koleksiyonunda yinelenir `Contact` .  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Parametreli sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))
- [Entity SQL Dili](./language-reference/entity-sql-language.md)
