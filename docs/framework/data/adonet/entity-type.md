---
title: entity type
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 3f99667a06d8aa439232802d4909290dfe9db97c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194784"
---
# <a name="entity-type"></a>entity type

*Varlık türü* , VARLıK VERI MODELI (EDM) ile veri yapısını açıklamak için temel yapı taşdır. Kavramsal modelde, varlık türü, müşteriler veya siparişler gibi üst düzey kavramların yapısını temsil eder. Varlık türü, varlık türü örnekleri için bir şablondur. Her şablon aşağıdaki bilgileri içerir:  
  
- Benzersiz bir ad. (Gerekli.)  
  
- Bir veya daha fazla özellik tarafından tanımlanan bir [varlık anahtarı](entity-key.md) . (Gerekli.)  
  
- [Özellikler](property.md)biçimindeki veriler. (İsteğe bağlı.)  
  
- Bir [ilişkinin](association-type.md) bir [sonundan](association-end.md) diğer uçtan gezintiye izin veren [Gezinti özellikleri](navigation-property.md) . (İsteğe bağlı)  
  
 Bir uygulamada, varlık türünün bir örneği belirli bir nesneyi (örneğin, belirli bir müşteri veya sipariş) temsil eder. Bir varlık türünün her örneğinin bir [varlık kümesi](entity-set.md)içinde benzersiz bir [varlık anahtarı](entity-key.md) olmalıdır.  
  
 İki varlık türü örneği, yalnızca aynı türde olmaları durumunda ve varlık anahtarlarının değerleri aynı ise eşit olarak değerlendirilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki diyagramda üç varlık türü olan bir kavramsal model gösterilmektedir: `Book` , `Publisher` ve `Author` :  
  
 ![Üç varlık türüne sahip örnek model](./media/entity-type/example-model-three-entity-types.gif)  
  
 Varlık anahtarını oluşturan her varlık türünün özelliklerinin "(Key)" ile birlikte gösterilir.  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, `Book` Yukarıdaki diyagramda gösterilen varlık türünü tanımlar:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
- [facet](facet.md)
