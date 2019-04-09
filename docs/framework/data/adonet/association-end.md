---
title: association end
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: e549254533f8362ce3475fb3aa5dbaffb3e900e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108296"
---
# <a name="association-end"></a>association end
Bir *ilişkilendirme end* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) bir ucunda bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) ve varlık sayısı bu ilişkilendirmeyi sonunda bulunabilir örnekleri yazın. İlişkilendirme ucu ilişkilendirme bir parçası olarak tanımlanır; bir ilişkiyi tam olarak iki ilişkilendirme ucu olması gerekir. [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) gezinme bir ilişkilendirme end bölümünden diğerine sağlar.  
  
 Bir ilişkilendirme end tanımı, şu bilgileri içerir:  
  
-   İlişkilendirmesine katılan varlık türlerinden biri. (Gerekli)  
  
    > [!NOTE]
    >  Belirli bir ilişkilendirme için her bir ilişkilendirme end için belirtilen varlık türü aynı olabilir. Bu, kendi kendine bir ilişkilendirme oluşturur.  
  
-   Bir [ilişkilendirme end çoğulluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) ilişkilendirme sonunda olabilir bir varlık türü örneklerinin sayısını belirtir. Bir ilişkilendirme end çoğulluk değeri (0..1) bir (1) sıfır veya bir ya da birden çok olabilir (\*).  
  
-   İlişki sonu için bir ad. (İsteğe bağlı)  
  
-   İlişkilendirme ucundaki gibi cascade delete üzerinde gerçekleştirilen işlemleri hakkında bilgiler. (İsteğe bağlı)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `PublishedBy` ve `WrittenBy`. İlişkilendirme sona için `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri. Çokluğu `Publisher` sonudur bir (1) ve çeşitliliğini `Book` sonudur birçok (\*), bir yayımcı bir çok kitap yayımlar ve bir yayımcı tarafından yayımlanan bir kitap gösteren.  
  
 ![Üç varlık türleri ile örnek modeli](./media/association-end/example-model-three-entity-types.gif)  
  
 ADO.NET varlık çerçevesi kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterilen ilişkilendirme. Türü, adı ve her bir ilişkilendirme end'ün çoğulluğu, XML özniteliği tarafından belirtilen unutmayın ( `Type`, `Role`, ve `Multiplicity` öznitelikleri, sırasıyla). İsteğe bağlı bir bitiş üzerinde gerçekleştirilen işlemler hakkında bilgi belirtilen bir XML öğesi ( `OnDelete` öğesi). Bu durumda, bir yayımcı silinir, bu nedenle ilişkili tüm kitaplar demektir.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
