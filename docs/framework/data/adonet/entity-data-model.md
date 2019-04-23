---
title: Varlık Veri Modeli
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: 8e96890d97f652295a3fdb67c48ec37710280eec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197925"
---
# <a name="entity-data-model"></a>Varlık Veri Modeli
Varlık veri modeli (EDM) depolanan hâli ne olursa olsun, veri yapısını açıklayan kavramları kümesidir. EDM varlık ilişkisi içinde 1976 Peter Chen tarafından açıklanan modelinden taşır, ancak ayrıca varlık ilişkisi modeli üzerinde oluşturur ve geleneksel kullanımları genişletir.  
  
 EDM birçok formlarında depolanan verileri kalmamasını ortaya çıkan sorunları giderir. Örneğin, ilişkisel veritabanları, metin dosyaları, XML dosyaları, elektronik tablolar ve raporlar veri depolayan bir iş göz önünde bulundurun. Bu veri modelleme, uygulama tasarımı ve veri erişimi önemli zorluklar teşkil etmektedir. Veri odaklı bir uygulama tasarlarken, verimli veri erişimi, depolama ve ölçeklenebilirlik ödün vermeden verimli ve sürdürülebilir kod yazma zorluktur. Veri ilişkisel bir yapısı varsa, veri erişimi, depolama ve ölçeklenebilirlik çok verimli, ancak verimli ve sürdürülebilir kod yazmaya daha zor hale gelir. Nesne yapısını veri sahip olduğunda stillerden alınır: Verimli ve sürdürülebilir kod yazma, verimli veri erişimi, depolama ve ölçeklenebilirlik karşılığında sunulur. Bu stillerden arasındaki doğru dengeyi bulunabilir olsa bile, yeni zorluklar verileri başka bir biçimden diğerine taşındığında ortaya çıkar. Varlık veri modeli, varlıklar ve ilişkiler herhangi bir depolama şema bağımsız açısından verilerin yapısını açıklayan tarafından bu sorunlarını ele alır. Bu veri depolanmış formu ilgisiz uygulama tasarımı ve geliştirme sağlar. Ayrıca, bir uygulamada (değil, depolanmış formu) kullanıldığı gibi varlıklar ve ilişkiler verilerin yapısını tanımlamak için uygulamanın geliştikçe bunlar geliştirebilirsiniz.  
  
 A `conceptual model` belirli bir gösterimiyse veri yapısı, varlıklar ve ilişkiler olarak ve genellikle, EDM kavramlarını uygulayan bir etki alanına özgü dil (DSL) tanımlanır. [Kavramsal şema tanım dili (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) böyle bir etki alanına özgü dil örneğidir. Varlıklar ve ilişkiler kavramsal modelde tanımlanan, nesneleri ve ilişkileri bir uygulamada özetlerini olarak düşünülebilir. Bu hizmet sayesinde geliştiriciler depolama şema kaygısı olmadan kavramsal model odaklanmak için ve verimliliği ve unutmayın yaşatılabilirlik kod yazmanızı sağlar. Bu arada depolama şema tasarımcıları verimliliğini veri erişimi, depolama ve ölçeklenebilirlik üzerinde odaklanabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 Bu bölümdeki konular, varlık veri modeli kavramlarını açıklar. EDM uygulayan herhangi bir DSL burada açıklanan kavramlar içermelidir. Unutmayın [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) CSDL kavramsal modeller tanımlamak için kullanır. Daha fazla bilgi için [CSDL belirtimi](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).  
  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [Varlık veri modeli: Ad alanları](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [Varlık veri modeli: Basit veri türleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [Varlık veri modeli: Devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [association end](../../../../docs/framework/data/adonet/association-end.md)  
  
 [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [association set](../../../../docs/framework/data/adonet/association-set.md)  
  
 [association set end](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [association type](../../../../docs/framework/data/adonet/association-type.md)  
  
 [complex type](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [entity container](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [entity key](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [entity set](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [entity type](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [facet](../../../../docs/framework/data/adonet/facet.md)  
  
 [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [model-declared function](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [model-defined function](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [navigation property](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [property](../../../../docs/framework/data/adonet/property.md)  
  
 [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET varlık veri modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [.edmx dosyasını genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [CSDL Belirtimi](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
