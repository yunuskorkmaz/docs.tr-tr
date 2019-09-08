---
title: özellik
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 97d934ac581e7b1a923bf77dcf46121782fe8eab
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783178"
---
# <a name="property"></a>özellik
*Özellikler* [varlık türlerinin](entity-type.md) ve [karmaşık türlerin](complex-type.md)temel yapı taşlarıdır. Özellikler bir varlık türü örneği veya karmaşık tür örneği içereceği verilerin şeklini ve özelliklerini tanımlar. Kavramsal modeldeki özellikler, bir sınıfta tanımlanan özelliklerle benzerdir. Bir sınıftaki özellikler, sınıfın şeklini tanımlar ve nesneler hakkında bilgi taşıyan bir kavramsal modeldeki Özellikler bir varlık türünün şeklini tanımlar ve varlık türü örnekleri hakkında bilgi taşır.  
  
> [!NOTE]
> Bu konu başlığı altında açıklandığı gibi özellikler, gezinti özelliklerinden farklıdır. Daha fazla bilgi için bkz. [gezinme özellikleri](navigation-property.md).  
  
 Bir özellik tanımı aşağıdaki bilgileri içerir:  
  
- Özellik adı. Istenir  
  
- Bir özellik türü. Istenir  
  
- Bir dizi [model](facet.md). (İsteğe bağlı)  
  
 Bir özellik, ilkel veriler (örneğin, bir dize, bir tamsayı veya Boole değeri) veya yapılandırılmış veriler (karmaşık bir tür gibi) içerebilir. İlkel türdeki özellikler de skaler özellikler olarak adlandırılır. Daha fazla bilgi için bkz [. varlık veri modeli: İlkel veri türleri](entity-data-model-primitive-data-types.md).  
  
> [!NOTE]
> Karmaşık bir tür, karmaşık türler olan özelliklere sahip olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book`, `Publisher`, ve `Author`. Her varlık türünün bazı özellikleri vardır, ancak her bir özelliğin tür bilgisi diyagramda verilmez. [Varlık anahtarları](entity-key.md) olan Özellikler (anahtar) ile gösterilir.  
  
 ![Üç varlık türüne sahip örnek model](./media/property/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki csdl `Book` varlık türünü tanımlar (Yukarıdaki diyagramda gösterildiği gibi) ve XML özniteliklerini kullanarak her bir özelliğin türünü ve adını gösterir. İsteğe bağlı bir model `Nullable`, XML özniteliği kullanılarak da tanımlanır.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Diyagramda gösterilen özelliklerden biri karmaşık tür özelliği olabilir. `Address` Örneğin, `StreetAddress` varlıktüründeki`StateOrProvince`özelliği ,`Country`,,, ve`PostalCode`gibi çeşitli skaler özelliklerden oluşan karmaşık bir tür özelliği olabilir. `City` `Publisher` Böyle bir karmaşık türün CSDL temsili aşağıdaki gibi olacaktır:  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
