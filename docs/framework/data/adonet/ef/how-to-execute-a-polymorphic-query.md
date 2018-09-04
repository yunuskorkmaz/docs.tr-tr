---
title: 'Nasıl yapılır: çok biçimli sorgu yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: ae491d0eeda7f8703dca174bdf4c5c847f78e675
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489701"
---
# <a name="how-to-execute-a-polymorphic-query"></a>Nasıl yapılır: çok biçimli sorgu yürütme
Bu konuda, bir çok biçimli yürütülecek gösterilmektedir [!INCLUDE[esql](../../../../../includes/esql-md.md)] kullanarak sorgu [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) işleci.  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekte, kodu çalıştırmak için  
  
1.  Ekleme [Okul modeli](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) projenize ve projenizi Entity Framework kullanmak üzere yapılandırın. Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  İçindeki adımları izleyerek bir tablo başına hierrachy devralma için kavramsal model değiştirme [izlenecek yol: eşleme devralma - tablo başına hiyerarşi](https://msdn.microsoft.com/library/49b685cf-9db8-4d6d-b885-8837ed238f55).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, almak ve yalnızca koleksiyonunu görüntülemek için bir OFTYPE işleci kullanır. `OnsiteCourses` koleksiyonundan `Courses`.  
  
 [!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
 [!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity Framework için EntityClient Sağlayıcısı](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [Entity SQL Dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
