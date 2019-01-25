---
title: İlişki sonu
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 8c156ca1c05e22e540578adfb2be06cf477b29e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744953"
---
# <a name="association-end"></a>İlişki sonu
Bir *ilişkilendirme end* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) bir ucunda bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) ve varlık sayısı bu ilişkilendirmeyi sonunda bulunabilir örnekleri yazın. İlişkilendirme ucu ilişkilendirme bir parçası olarak tanımlanır; bir ilişkiyi tam olarak iki ilişkilendirme ucu olması gerekir. [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) gezinme bir ilişkilendirme end bölümünden diğerine sağlar.  
  
 Bir ilişkilendirme end tanımı, şu bilgileri içerir:  
  
-   İlişkilendirmesine katılan varlık türlerinden biri. (Gerekli)  
  
    > [!NOTE]
    >  Belirli bir ilişkilendirme için her bir ilişkilendirme end için belirtilen varlık türü aynı olabilir. Bu, kendi kendine bir ilişkilendirme oluşturur.  
  
-   Bir [ilişkilendirme end çoğulluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) ilişkilendirme sonunda olabilir bir varlık türü örneklerinin sayısını belirtir. Bir ilişkilendirme end çoğulluk değeri (0..1) bir (1) sıfır veya bir veya birçok (*) olabilir.  
  
-   İlişki sonu için bir ad. (İsteğe bağlı)  
  
-   İlişkilendirme ucundaki gibi cascade delete üzerinde gerçekleştirilen işlemleri hakkında bilgiler. (İsteğe bağlı)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `PublishedBy` ve `WrittenBy`. İlişkilendirme sona için `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri. Çokluğu `Publisher` sonudur bir (1) ve çeşitliliğini `Book` sonudur birçok (*), bir yayımcı bir çok kitap yayımlar ve bir yayımcı tarafından yayımlanan bir kitap gösteren.  
  
 ![Örnek Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET varlık çerçevesi kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterilen ilişkilendirme. Türü, adı ve her bir ilişkilendirme end'ün çoğulluğu, XML özniteliği tarafından belirtilen unutmayın ( `Type`, `Role`, ve `Multiplicity` öznitelikleri, sırasıyla). İsteğe bağlı bir bitiş üzerinde gerçekleştirilen işlemler hakkında bilgi belirtilen bir XML öğesi ( `OnDelete` öğesi). Bu durumda, bir yayımcı silinir, bu nedenle ilişkili tüm kitaplar demektir.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
