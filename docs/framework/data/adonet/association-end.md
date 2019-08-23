---
title: association end
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 575157cd1d125d3315e1859aad72cc8b08d8b4cf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932211"
---
# <a name="association-end"></a>association end
Bir *ilişkilendirme End* 'i, bir ilişkilendirmenin bir sonundaki [varlık türünü](../../../../docs/framework/data/adonet/entity-type.md) ve [](../../../../docs/framework/data/adonet/association-type.md) bir ilişkinin o ucunda bulunabilir varlık türü örneklerinin sayısını tanımlar. İlişki uçları bir ilişkinin parçası olarak tanımlanır; bir ilişkilendirme tam olarak iki ilişkilendirme bitmelidir. [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) , bir ilişkilendirme ucundan diğerine kadar gezinmesine izin verir.  
  
 Bir ilişkilendirme End tanımı aşağıdaki bilgileri içerir:  
  
- İlişkilendirmede yer alan varlık türlerinden biri. Istenir  
  
    > [!NOTE]
    > Belirli bir ilişki için, her ilişkilendirme ucu için belirtilen varlık türü aynı olabilir. Bu, kendine ilişkilendirme oluşturur.  
  
- İlişkilendirmenin bir ucunda olabilecek varlık türü örneklerinin sayısını gösteren bir [ilişkilendirme End çoğulluğu](../../../../docs/framework/data/adonet/association-end-multiplicity.md) . Bir ilişki uç çoğulluğu bir (1), sıfır veya bir (0.. 1) veya çok (\*) değerine sahip olabilir.  
  
- İlişki ucu için bir ad. (İsteğe bağlı)  
  
- İlişki ucunda gerçekleştirilen, silme sırasında Cascade gibi işlemler hakkında bilgiler. (İsteğe bağlı)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy` ve. `WrittenBy` İlişkilendirme için `PublishedBy` `Publisher` ilişkilendirme sonlanır `Book` ve varlık türleridir. `Publisher` Ucun çoğulluğu bir (1) ve `Book` ucun çoğulluğu birçok (\*), bir yayımcının çok sayıda kitap yayımladığını ve bir kitabın bir yayımcı tarafından yayımlandığını belirtir.  
  
 ![Üç varlık türüne sahip örnek model](./media/association-end/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) adlı bir etki alanına özgü DIL (DSL) kullanır. Aşağıdaki csdl, Yukarıdaki diyagramda `PublishedBy` gösterilen ilişkilendirmeyi tanımlar. Her ilişkilendirme ucunun türü, adı ve çoğulluk özelliklerinin, XML öznitelikleri ( `Type` `Role`sırasıyla, ve `Multiplicity` öznitelikleri) tarafından belirtildiğine unutmayın. Bir uçta gerçekleştirilen işlemlerle ilgili isteğe bağlı bilgiler bir XML öğesinde ( `OnDelete` öğesi) belirtilir. Bu durumda, bir yayımcı silinirse tüm ilişkili kitaplardır.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
