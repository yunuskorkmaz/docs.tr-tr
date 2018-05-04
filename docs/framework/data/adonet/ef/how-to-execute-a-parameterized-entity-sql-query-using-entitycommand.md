---
title: 'Nasıl yapılır: EntityCommand kullanarak parametreli varlık SQL sorgusu yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: c8469f8f13178a09c636d33070fd5ad4cbb912aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a>Nasıl yapılır: EntityCommand kullanarak parametreli varlık SQL sorgusu yürütme
Bu konuda nasıl yürütüleceği gösterilmektedir bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] kullanarak parametreye sahip sorgu bir <xref:System.Data.EntityClient.EntityCommand> nesnesi.  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekte kodu çalıştırmak için  
  
1.  Ekleme [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) projenize ve kullanmak için projenizin yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Uygulamanız için kod sayfasında aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki parametreli bir sorgu dizesi oluşturmak gösterilmiştir. Daha sonra oluşturur bir <xref:System.Data.EntityClient.EntityCommand>, iki parametreyi ekler <xref:System.Data.EntityClient.EntityParameter> , koleksiyonunu <xref:System.Data.EntityClient.EntityCommand>ve toplulukta tekrarlanan `Contact` öğeleri.  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: parametreleştirilmiş sorgu yürütme](http://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
 [Entity SQL Dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
