---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: Iç Içe geçmiş Koleksiyonlar döndüren bir sorgu yürütme'
title: 'Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 941b7471820c09224e6828fac6e17b92f70ff57e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650631"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a>Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme

Bu, bir nesne kullanarak bir kavramsal modele karşı bir komutun nasıl yürütüleceğini <xref:System.Data.EntityClient.EntityCommand> ve kullanarak iç içe geçmiş koleksiyon sonuçlarının nasıl alınacağını gösterir <xref:System.Data.EntityClient.EntityDataReader> .  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekteki kodu çalıştırmak için  
  
1. Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın. Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Örnek  

 *İç içe geçmiş koleksiyon* , başka bir koleksiyon içinde olan bir koleksiyondur. Aşağıdaki kod, bir koleksiyonunu `Contacts` ve her biriyle ilişkili iç içe geçmiş koleksiyonları alır `SalesOrderHeaders` `Contact` .  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework için EntityClient Sağlayıcısı](entityclient-provider-for-the-entity-framework.md)
