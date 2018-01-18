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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: dad95c70b87c3926390e9ac1eefc819db925e15c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="entity-data-model"></a>Varlık Veri Modeli
Varlık veri modeli (EDM) depolanan form bağımsız olarak verilerin yapısını açıklayan kavramları kümesidir. EDM varlık ilişkisi içinde 1976 Peter Chen tarafından açıklanan modelinden taşır, ancak ayrıca varlık ilişkisi modeline oluşturur ve geleneksel kullanımları genişletir.  
  
 EDM birçok formlarında depolanan verilere sahip olmak ortaya sorunlarını ele alır. Örneğin, ilişkisel veritabanları, metin dosyaları, XML dosyalarını, elektronik tablolar ve raporlar verilerini depolayan bir iş göz önünde bulundurun. Modelleme verileri, uygulama tasarımı ve veri erişimi önemli sorunları gösterir. Veri odaklı bir uygulama tasarlarken, sınama verimli ve sürdürülebilir kod verimli veri erişimi, depolama ve ölçeklenebilirlik ödün vermeden yazmaktır. Veri ilişkisel yapısı olduğunda, veri erişimi, depolama ve ölçeklenebilirlik çok verimli ancak verimli ve sürdürülebilir kod yazma daha zorlaşır. Verileri bir nesne yapısına sahip olduğunda, dengelemeler alınır: verimli ve sürdürülebilir kod yazma gelen verimli veri erişimi, depolama ve ölçeklenebilirlik artması pahasına olur. Bu dengelemeler arasında doğru dengeyi bulunabilir olsa bile, verileri bir biçimden diğerine taşındığında ve başka bir yeni zorluklar ortaya çıkar. Varlık veri modeli, varlıkları ve tüm depolama şeması bağımsız ilişkileri açısından verilerin yapısını açıklayarak bu sorunlarını ele alır. Bu veri depolanan form ilgisiz uygulama tasarımı ve geliştirme sağlar. Ayrıca, bir uygulama (değil, depolanan form) kullanıldığı gibi varlıkları ve ilişkileri veri yapısını tanımlamak için bir uygulama geliştikçe bunlar gelişmesi.  
  
 A `conceptual model` genellikle, EDM kavramlarını uygulayan bir etki alanına özgü dil (DSL) tanımlanan ve bir özel veri yapısını varlıkları ve ilişkileri olarak gösterimidir. [Kavramsal şema tanım dili (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) gibi bir etki alanına özgü dil örneğidir. Varlıkları ve ilişkileri kavramsal modelde tanımlanan, nesneler ve ilişkilendirmelerini uygulamadaki soyutlamalar olarak düşünülebilir. Bu depolama şema kaygısı olmadan kavramsal model odaklanmak yayınlamasına izin verir ve verimliliği ve bakımı aklınızda ile kod yazmanıza olanak sağlar. Bu sırada depolama şema tasarımcıları veri erişimi, depolama ve ölçeklenebilirlik verimliliğini odaklanabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 Bu bölümdeki konular, varlık veri modeli kavramlarını açıklar. EDM uygulayan DSL burada açıklanan kavramları içermelidir. Unutmayın [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) CSDL kavramsal modeller tanımlamak için kullanır. Daha fazla bilgi için bkz: [CSDL belirtimi](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).  
  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [Varlık Veri Modeli: Ad Alanları](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [Varlık Veri Modeli: Basit Veri Türleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [Varlık Veri Modeli: Devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET varlık veri modeli araçları](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [.edmx dosyasının genel bakış](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [CSDL Belirtimi](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
