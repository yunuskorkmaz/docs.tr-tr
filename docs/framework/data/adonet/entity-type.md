---
title: "Varlık türü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1b84ff5a55cff4548539e81b16406e234dcb43f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-type"></a>Varlık türü
*Varlık türü* verilerin varlık veri modeli (EDM) ile yapısını açıklamak için temel yapı bloğu. Kavramsal modelde, müşteriler veya siparişler gibi üst düzey kavramlarını yapısını bir varlık türünü temsil eder. Bir varlık türünün varlık türü örnekleri için bir şablondur. Her şablon aşağıdaki bilgileri içerir:  
  
-   Benzersiz bir ad. (Gerekli)  
  
-   Bir [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) bir veya daha fazla özellikleri tarafından tanımlanan. (Gerekli)  
  
-   Veri biçiminde [özellikleri](../../../../docs/framework/data/adonet/property.md). (İsteğe bağlı.)  
  
-   [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) izin veren bir gezinti için [son](../../../../docs/framework/data/adonet/association-end.md) , bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) diğer bitiş. (İsteğe bağlı)  
  
 Bir uygulamada bir varlık türünün bir örneği (örneğin, belirli bir müşteri veya sipariş) belirli bir nesneyi temsil eder. Her bir varlık türünün örneğini benzersiz olmalıdır [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) içinde bir [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md).  
  
 İki varlık türü örnekleri yalnızca aynı türde olduğundan ve bunların varlık anahtarları aynı değerleri eşit olarak kabul edilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`:  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Kendi Varlık anahtarı oluşturan her bir varlık türü özelliklerini "(anahtar)" ile belirtilir unutmayın.  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `Book` Yukarıdaki diyagramda gösterildiği varlık türü:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık veri modeli temel kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [modeli](../../../../docs/framework/data/adonet/facet.md)
