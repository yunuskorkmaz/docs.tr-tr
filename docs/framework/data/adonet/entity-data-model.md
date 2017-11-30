---
title: "Varlık Veri Modeli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 69b72a824e6f9468c9b3d86073243d506382e766
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-data-model"></a>Varlık Veri Modeli
Varlık veri modeli (EDM) depolanan form bağımsız olarak verilerin yapısını açıklayan kavramları kümesidir. EDM varlık ilişkisi içinde 1976 Peter Chen tarafından açıklanan modelinden taşır, ancak ayrıca varlık ilişkisi modeline oluşturur ve geleneksel kullanımları genişletir.  
  
 EDM birçok formlarında depolanan verilere sahip olmak ortaya sorunlarını ele alır. Örneğin, ilişkisel veritabanları, metin dosyaları, XML dosyalarını, elektronik tablolar ve raporlar verilerini depolayan bir iş göz önünde bulundurun. Modelleme verileri, uygulama tasarımı ve veri erişimi önemli sorunları gösterir. Veri odaklı bir uygulama tasarlarken, sınama verimli ve sürdürülebilir kod verimli veri erişimi, depolama ve ölçeklenebilirlik ödün vermeden yazmaktır. Veri ilişkisel yapısı olduğunda, veri erişimi, depolama ve ölçeklenebilirlik çok verimli ancak verimli ve sürdürülebilir kod yazma daha zorlaşır. Verileri bir nesne yapısına sahip olduğunda, dengelemeler alınır: verimli ve sürdürülebilir kod yazma gelen verimli veri erişimi, depolama ve ölçeklenebilirlik artması pahasına olur. Bu dengelemeler arasında doğru dengeyi bulunabilir olsa bile, verileri bir biçimden diğerine taşındığında ve başka bir yeni zorluklar ortaya çıkar. Varlık veri modeli, varlıkları ve tüm depolama şeması bağımsız ilişkileri açısından verilerin yapısını açıklayarak bu sorunlarını ele alır. Bu veri depolanan form ilgisiz uygulama tasarımı ve geliştirme sağlar. Ayrıca, bir uygulama (değil, depolanan form) kullanıldığı gibi varlıkları ve ilişkileri veri yapısını tanımlamak için bir uygulama geliştikçe bunlar gelişmesi.  
  
 A `conceptual model` genellikle, EDM kavramlarını uygulayan bir etki alanına özgü dil (DSL) tanımlanan ve bir özel veri yapısını varlıkları ve ilişkileri olarak gösterimidir. [Kavramsal şema tanım dili (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) gibi bir etki alanına özgü dil örneğidir. Varlıkları ve ilişkileri kavramsal modelde tanımlanan, nesneler ve ilişkilendirmelerini uygulamadaki soyutlamalar olarak düşünülebilir. Bu depolama şema kaygısı olmadan kavramsal model odaklanmak yayınlamasına izin verir ve verimliliği ve bakımı aklınızda ile kod yazmanıza olanak sağlar. Bu sırada depolama şema tasarımcıları veri erişimi, depolama ve ölçeklenebilirlik verimliliğini odaklanabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 Bu bölümdeki konular, varlık veri modeli kavramlarını açıklar. EDM uygulayan DSL burada açıklanan kavramları içermelidir. Unutmayın [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) CSDL kavramsal modeller tanımlamak için kullanır. Daha fazla bilgi için bkz: [CSDL belirtimi](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).  
  
 [Varlık veri modeli temel kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [Varlık veri modeli: ad alanları](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [Varlık veri modeli: Basit veri türleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [Varlık veri modeli: devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [ilişki ucu](../../../../docs/framework/data/adonet/association-end.md)  
  
 [İlişki uç Çokluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [ilişkilendirme kümesi](../../../../docs/framework/data/adonet/association-set.md)  
  
 [İlişki sonu Ayarla](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [ilişki türü](../../../../docs/framework/data/adonet/association-type.md)  
  
 [karmaşık türü](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [Varlık kapsayıcısı](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [Varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [varlık türü](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [modeli](../../../../docs/framework/data/adonet/facet.md)  
  
 [yabancı anahtar özelliği](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [Model bildirilen işlevi](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [Model tanımlı işlevi](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [Gezinme özelliği](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [özelliği](../../../../docs/framework/data/adonet/property.md)  
  
 [başvuru bütünlüğü kısıtlaması](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET varlık veri modeli araçları](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [.edmx dosyasının genel bakış](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [CSDL belirtimi](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
