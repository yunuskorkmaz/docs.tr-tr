---
title: özellik
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 80c4bb3ccbab75c17b098723fc10b8b996e40576
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409724"
---
# <a name="property"></a>özellik
*Özellikleri* temel yapı taşlarıdır [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) ve [karmaşık türler](../../../../docs/framework/data/adonet/complex-type.md). Bir varlık türü örneği veya karmaşık tür örneği içeren veri özelliklerini ve şekli özelliklerini tanımlayın. Kavramsal modelde özellikleri, bir sınıf üzerinde tanımlanan özelliklere benzer. Bir sınıfındaki özellikleri sınıfı şeklini tanımlamak ve nesneler hakkında bilgi taşımak aynı şekilde, kavramsal model özelliklerinde bir varlık türü şeklini tanımlamak ve varlık türü örnekleri hakkında bilgi taşımak.  
  
> [!NOTE]
>  Bu konuda açıklandığı gibi özellikleri, gezinti özellikleri farklıdır. Daha fazla bilgi için [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md).  
  
 Bir özellik tanımı, şu bilgileri içerir:  
  
-   Bir özellik adı. (Gerekli)  
  
-   Özellik türü. (Gerekli)  
  
-   Bir dizi [modelleri](../../../../docs/framework/data/adonet/facet.md). (İsteğe bağlı)  
  
 Bir özellik, temel veri (örneğin, bir dize, tamsayı veya Boolean değeri) veya yapılandırılmış veriler (örneğin, bir karmaşık tür) içerebilir. Temel eleman türü özellikleri, skaler özellikler olarak da adlandırılır. Daha fazla bilgi için [varlık veri modeli: Temel veri türlerinin](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
> [!NOTE]
>  Karmaşık bir tür kendisini, karmaşık türler özelliklere sahip olabilir.  
  
## <a name="example"></a>Örnek  
 Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`. Diyagramda her bir özellik için tür bilgilerini ilettiği değil ancak her varlık türü birden çok özellikleri vardır. Özellikler [varlık anahtarları](../../../../docs/framework/data/adonet/entity-key.md) (anahtar) ile belirtilir.  
  
 ![Üç varlık türleri ile örnek modeli](./media/property/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `Book` varlık (Yukarıdaki diyagramda gösterildiği gibi) yazın ve XML öznitelikleri kullanarak her bir özelliğin adını ve türünü belirtir. İsteğe bağlı bir modeli `Nullable`, ayrıca bir XML özniteliği kullanılarak tanımlanır.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Aşağıdaki diyagramda gösterilen özelliklerden biri bir karmaşık tür özelliği olduğunu mümkündür. Örneğin, `Address` özelliği `Publisher` varlık türü olabilir birkaç skaler özelliklerini oluşan bir karmaşık tür özelliği gibi `StreetAddress`, `City`, `StateOrProvince`, `Country`, ve `PostalCode`. Karmaşık bir tür CSDL gösterimini şu şekilde olacaktır:  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
