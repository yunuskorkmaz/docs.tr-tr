---
title: 'Nasıl yapılır: EntityCommand kullanarak parametreli varlık SQL sorgusu yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: a9b4069004cc48fa05efa29b4467aa1dca47fb29
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610103"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a>Nasıl yapılır: EntityCommand kullanarak parametreli varlık SQL sorgusu yürütme
Bu konu nasıl çalıştırılacağını gösteren bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] kullanarak parametreleri olan sorgu bir <xref:System.Data.EntityClient.EntityCommand> nesne.  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekte, kodu çalıştırmak için  
  
1.  Ekleme [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) projenize ve projenizi kullanmak üzere yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki parametre ile bir sorgu dizesi oluşturmak gösterilmektedir. Ardından oluşturur bir <xref:System.Data.EntityClient.EntityCommand>, iki parametre için ekler <xref:System.Data.EntityClient.EntityParameter> , koleksiyonu <xref:System.Data.EntityClient.EntityCommand>ve koleksiyonu yineleme `Contact` öğeleri.  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Parametreli bir sorgu yürütme](https://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)
- [Entity SQL Dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
