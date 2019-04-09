---
title: Varlık Veri Modeli Temel Kavramları
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: 2efa54b6bd656129812cc9dd7c2ce38a4fb2a89a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074462"
---
# <a name="entity-data-model-key-concepts"></a>Varlık Veri Modeli Temel Kavramları
Verilerin yapısını tanımlamak için üç temel kavramları varlık veri modeli (EDM) kullanır: *varlık türü*, *ilişkilendirme türü*, ve *özelliği*. Bu EDM herhangi bir uygulamada verilerin yapısını açıklayan en önemli kavramlar ücretlerdir.  
  
## <a name="entity-type"></a>Varlık türü  
 [Varlık türü](../../../../docs/framework/data/adonet/entity-type.md) varlık veri modeli ile verilerin yapısını tanımlamak için temel yapı taşı. Bir kavramsal modelde varlık türleri oluşturulan [özellikleri](../../../../docs/framework/data/adonet/property.md) ve müşteri gibi üst düzey kavramlar yapısını açıklayan ve siparişler bir iş uygulaması içinde. Bir bilgisayar programı, bir sınıf tanımı için bir şablonu olarak aynı şekilde örnekler, bir varlık türünün varlık için bir şablon sınıfıdır. Bir varlığa (örneğin, belirli müşteri veya sipariş) belirli bir nesneyi temsil eder. Her varlığın benzersiz olmalıdır [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) içinde bir [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md).  Bir varlık kümesi, bir varlığa türün örneklerinin koleksiyonudur. Varlık kümeleri (ve [ilişki Setleri](../../../../docs/framework/data/adonet/association-set.md)) mantıksal olarak gruplanmış bir [varlık kapsayıcısı](../../../../docs/framework/data/adonet/entity-container.md).  
  
 Devralma ile varlık türleri desteklenir: diğer bir deyişle, bir varlık türü başka bir uygulamadan elde edilebilir. Daha fazla bilgi için [varlık veri modeli: Devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="association-type"></a>İlişki türü  
 Bir [ilişkilendirme türü](../../../../docs/framework/data/adonet/association-type.md) (ilişkilendirme olarak da bilinir) ilişkilerini, varlık veri modeli tanımlamak için temel yapı taşı. Kavramsal bir modeli içinde iki varlık türleri (örneğin, müşteri ile sipariş) arasında bir ilişki bir ilişkiyi temsil eder. Her iki ilişkisi [ilişkilendirme ucu](../../../../docs/framework/data/adonet/association-end.md) ilişkilendirmesine katılan varlık türlerini belirtin. Ayrıca, her bir ilişkilendirme end belirtir bir [ilişkilendirme end çoğulluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) ilişkilendirme sonunda olabilir bir varlık sayısını gösterir. Bir ilişkilendirme end çoğulluk değeri (0..1) bir (1) sıfır veya bir veya birçok (*) olabilir. Bir ilişkilendirmenin bir ucunda varlıkları üzerinden erişilebilir [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md), veya bir varlık türünde gösteriliyorsa yabancı anahtarlar aracılığıyla. Daha fazla bilgi için [yabancı anahtar özelliği](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
 Bir uygulamada belirli bir ilişkilendirme (örneğin, müşteri örneği siparişi örnekleri arasındaki ilişkiyi) bir ilişki örneğini temsil eder. İlişkilendirme örnekleri mantıksal olarak gruplandırılır bir [ilişki kümesi](../../../../docs/framework/data/adonet/association-set.md). İlişki setleri (ve [varlık kümeleri](../../../../docs/framework/data/adonet/entity-set.md)) mantıksal olarak gruplanmış bir [varlık kapsayıcısı](../../../../docs/framework/data/adonet/entity-container.md).  
  
## <a name="property"></a>Özellik  
 [Varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) içeren [özellikleri](../../../../docs/framework/data/adonet/property.md) kendi yapısını ve özellikleri tanımlar. Örneğin, bir müşteri varlığı türü CustomerID, ad ve adres gibi özelliklere sahip olabilir.  
  
 Kavramsal modelde özellikleri, bilgisayar programı bir sınıfta tanımlanan özelliklere benzer. Bir sınıfındaki özellikleri sınıfı şeklini tanımlamak ve nesneler hakkında bilgi taşımak aynı şekilde, kavramsal model özelliklerinde bir varlık türü şeklini tanımlamak ve varlık türü örnekleri hakkında bilgi taşımak.  
  
 Bir özellik, temel veri (örneğin, bir dize, tamsayı veya Boolean değeri) veya yapılandırılmış veriler (örneğin, bir karmaşık tür) içerebilir. Daha fazla bilgi için [varlık veri modeli: Temel veri türlerinin](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
## <a name="representations-of-a-conceptual-model"></a>Kavramsal Model gösterimleri  
 A *kavramsal model* belirli bir gösterimiyse bazı verilerin yapısını, varlıkları ve ilişkileri. Kavramsal bir modeli temsil eden bir diyagram ile yoludur. Aşağıdaki diyagramda üç varlık türleri ile kavramsal bir modeli temsil eder (`Book`, `Publisher`, ve `Author`) ve iki ilişkilendirmelerini (`PublishedBy` ve `WrittenBy`):  
  
 ![Kavramsal bir modelle üç varlık türlerini gösteren diyagram.](./media/entity-data-model-key-concepts/conceptual-model-entity-types-associations.gif)  
  
 Modelle ilgili bazı ayrıntılar iletmek için söz konusu olduğunda bu gösterim, ancak bazı eksiklikleri vardır. Örneğin, özellik türü ve varlık kümesi bilgileri değil ilettiği diyagramda. Kavramsal model zenginliğine daha net bir şekilde bir etki alanına özgü dil (DSL) iletilmesi. [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) adlı bir XML tabanlı DSL kullanan *kavramsal şema tanım dili* ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Yukarıdaki diyagramda kavramsal modelde CSDL tanımı aşağıda verilmiştir:  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
