---
title: Varlık Veri Modeli Temel Kavramları
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: d020de65ff64d93c0ea925b71e5f1546eb4402aa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191768"
---
# <a name="entity-data-model-key-concepts"></a>Varlık Veri Modeli Temel Kavramları

Varlık Veri Modeli (EDM), verilerin yapısını betimleyen üç temel kavram kullanır: *varlık türü*, *ilişki türü*ve *özellik*. Bunlar, EDM 'ın herhangi bir uygulamasındaki verilerin yapısını açıklayan en önemli kavramlardır.  
  
## <a name="entity-type"></a>Varlık türü  

 [Varlık türü](entity-type.md) , varlık veri modeli veri yapısını açıklamak için temel yapı taşıdır. Kavramsal modelde, varlık türleri [özelliklerden](property.md) oluşturulur ve bir iş uygulamasındaki müşteriler ve siparişler gibi en üst düzey kavramların yapısını tanımlarlar. Bir bilgisayar programındaki sınıf tanımının sınıf örnekleri için bir şablon olduğu şekilde, varlık türü varlıklar için bir şablondur. Bir varlık belirli bir nesneyi (örneğin, belirli bir müşteri veya sipariş) temsil eder. Her varlık bir [varlık kümesi](entity-set.md)içinde benzersiz bir [varlık anahtarına](entity-key.md) sahip olmalıdır.  Bir varlık kümesi, belirli bir varlık türünün örneklerinin bir koleksiyonudur. Varlık kümeleri (ve [ilişkilendirme kümeleri](association-set.md)) bir [varlık kapsayıcısında](entity-container.md)mantıksal olarak gruplandırılır.  
  
 Devralma varlık türleriyle desteklenir: diğer bir deyişle, bir varlık türü diğerinden türetilebilir. Daha fazla bilgi için bkz. [varlık veri modeli: devralma](entity-data-model-inheritance.md).  
  
## <a name="association-type"></a>İlişki türü  

 İlişki [türü](association-type.md) (ilişki olarak da bilinir) varlık veri modeli ilişkilerini açıklamak için temel yapı taşdır. Kavramsal modelde, ilişki iki varlık türü (müşteri ve sıra gibi) arasındaki ilişkiyi temsil eder. Her ilişkide, ilişkilendirmede yer alan varlık türlerini belirten iki [ilişkilendirme bitişi](association-end.md) vardır. Her ilişki ucu, ilişkilendirmenin o ucunda olabilecek varlık sayısını gösteren bir [ilişki ucu çoğulluğu](association-end-multiplicity.md) de belirtir. Bir ilişki uç çoğulluğu bir (1), sıfır veya bir (0.. 1) veya çok () değerine sahip olabilir \* . Bir ilişkinin bir sonundaki varlıklara, [Gezinti özellikleri](navigation-property.md)aracılığıyla veya bir varlık türü üzerinde sunulduklarında yabancı anahtarlar aracılığıyla erişilebilir. Daha fazla bilgi için bkz. [yabancı anahtar özelliği](foreign-key-property.md).  
  
 Bir uygulamada, bir ilişkinin örneği belirli bir ilişkilendirmeyi temsil eder (müşteri örneği ve sıra örnekleri arasındaki ilişki gibi). İlişki örnekleri bir [ilişki kümesinde](association-set.md)mantıksal olarak gruplandırılır. İlişki kümeleri (ve [varlık kümeleri](entity-set.md)) bir [varlık kapsayıcısında](entity-container.md)mantıksal olarak gruplandırılır.  
  
## <a name="property"></a>Özellik  

 [Varlık türleri](entity-type.md) , yapısını ve özelliklerini tanımlayan [özellikleri](property.md) içerir. Örneğin, Müşteri varlığı türü CustomerID, Name ve Address gibi özelliklere sahip olabilir.  
  
 Kavramsal modeldeki özellikler, bir bilgisayar programındaki bir sınıfta tanımlanan özelliklerle benzerdir. Bir sınıftaki özellikler, sınıfın şeklini tanımlar ve nesneler hakkında bilgi taşıyan bir kavramsal modeldeki Özellikler bir varlık türünün şeklini tanımlar ve varlık türü örnekleri hakkında bilgi taşır.  
  
 Bir özellik, ilkel veriler (örneğin, bir dize, bir tamsayı veya Boole değeri) veya yapılandırılmış veriler (karmaşık bir tür gibi) içerebilir. Daha fazla bilgi için bkz. [varlık veri modeli: Ilkel veri türleri](entity-data-model-primitive-data-types.md).  
  
## <a name="representations-of-a-conceptual-model"></a>Kavramsal modelin temsilleri  

 *Kavramsal model* , bazı verilerin yapısının varlık ve ilişki olarak belirli bir gösterimidir. Bir kavramsal modeli göstermenin bir yolu bir diyagramdır. Aşağıdaki diyagramda üç varlık türü ( `Book` , `Publisher` , ve `Author` ) ve iki ilişkilendirme ( `PublishedBy` ve `WrittenBy` ) içeren bir kavramsal model temsil etmektedir:  
  
 ![Üç varlık türü ile kavramsal bir modeli gösteren diyagram.](./media/entity-data-model-key-concepts/conceptual-model-entity-types-associations.gif)  
  
 Ancak, bu gösterim, model hakkında bazı ayrıntılar almak için olduğunda bazı eksikler içerir. Örneğin, özellik türü ve varlık kümesi bilgileri diyagramda verilmez. Kavramsal modelin zenginliği, etki alanına özgü dil (DSL) ile daha net bir şekilde alınabilir. [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlama *dili* ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı XML tabanlı bir DSL kullanarak kavramsal modeller tanımlar. Aşağıda, Yukarıdaki diyagramda kavramsal modelin CSDL tanımı verilmiştir:  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli](entity-data-model.md)
