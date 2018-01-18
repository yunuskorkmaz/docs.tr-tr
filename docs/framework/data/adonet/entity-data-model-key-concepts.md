---
title: "Varlık veri modeli temel kavramları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f75a4fc0e529b602aca91aa3cfd2dff35e4fe640
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="entity-data-model-key-concepts"></a>Varlık veri modeli temel kavramları
Varlık veri modeli (EDM) verilerin yapısını tanımlamak için üç temel kavramları kullanır: *varlık türü*, *ilişkilendirme türü*, ve *özelliği*. EDM herhangi bir uygulamada verilerin yapısını açıklayan en önemli kavramlar bunlar.  
  
## <a name="entity-type"></a>Varlık türü  
 [Varlık türü](../../../../docs/framework/data/adonet/entity-type.md) varlık veri modeli ile verilerin yapısını açıklayan için temel yapı bloğu. Kavramsal modelde, varlık türleri gelen oluşturulan [özellikleri](../../../../docs/framework/data/adonet/property.md) ve bir müşteriler gibi üst düzey kavramlarını yapısını açıklar ve bir iş uygulaması siparişler. Aynı şekilde, bilgisayar programı bir sınıf tanımı için bir şablon olduğunu örnekleri sınıfı, bir varlıklar için bir şablon varlık türüdür. Bir varlığı temsil eder (örneğin, belirli bir müşteri veya sipariş) belirli bir nesnesi. Her varlığın benzersiz olmalıdır [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) içinde bir [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md).  Bir varlık kümesini, belirli bir varlık türünün örneklerini koleksiyonudur. Varlık kümeleri (ve [ilişki kümeleri](../../../../docs/framework/data/adonet/association-set.md)) mantıksal olarak gruplandırılmıştır bir [varlık kapsayıcısının](../../../../docs/framework/data/adonet/entity-container.md).  
  
 Devralma ile varlık türleri desteklenir: başka bir deyişle, bir varlık türü diğerinden elde edilebilir. Daha fazla bilgi için bkz: [varlık veri modeli: Devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="association-type"></a>İlişki türü  
 Bir [ilişkilendirme türü](../../../../docs/framework/data/adonet/association-type.md) (bir ilişki olarak da bilinir) varlık veri modeli ilişkilerde açıklamak için temel yapı bloğu. Kavramsal modelde, iki varlık türleri (örneğin, müşteri ve sırası) arasında bir ilişki bir ilişkiyi temsil eder. Her iki bir ilişkiye [ilişki uçları](../../../../docs/framework/data/adonet/association-end.md) ilişkiye katılan varlık türlerini belirtin. Ayrıca her ilişki ucu belirtir bir [ilişkilendirme son Çokluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) bu ilişkilendirmeyi sonunda olabilir varlıkların sayısını gösterir. Bir ilişkilendirme end Çokluk bir değer (0.. 1 çokluğa) bir (1), sıfır veya bir veya birçok (*) olabilir. Bir ilişkilendirme end varlık üzerinden erişilebilir [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md), veya bir varlık türü gösteriliyorsa yabancı anahtarlar üzerinden. Daha fazla bilgi için bkz: [yabancı anahtar özelliği](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
 Bir uygulamada bir ilişki örneği (örneğin, müşteri örneği ve sipariş örnekleri arasında bir ilişki) belirli bir ilişkiyi temsil eder. İlişkilendirme örnekleri mantıksal olarak gruplandırılmış bir [ilişkilendirme kümesi](../../../../docs/framework/data/adonet/association-set.md). İlişki kümeleri (ve [varlık kümeleri](../../../../docs/framework/data/adonet/entity-set.md)) mantıksal olarak gruplandırılmıştır bir [varlık kapsayıcısının](../../../../docs/framework/data/adonet/entity-container.md).  
  
## <a name="property"></a>Özellik  
 [Varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) içeren [özellikleri](../../../../docs/framework/data/adonet/property.md) kendi yapısını ve özellikleri tanımlayın. Örneğin, bir müşteri varlık türü CustomerID, ad ve adres gibi özelliklere sahip olabilir.  
  
 Kavramsal model özelliklerinde, bilgisayar programı sınıfında tanımlanan özelliklere benzer. Aynı şekilde bir sınıfındaki özellikleri şekil sınıfının tanımlamak ve nesneler hakkındaki bilgileri taşımak, kavramsal model özelliklerinde bir varlık türü şeklini tanımlayın ve varlık türü örnekleri hakkında bilgi taşımak.  
  
 Bir özellik, temel verileri (örneğin, bir dize, tamsayı veya Boolean değeri) veya yapılandırılmış verileri (örneğin, bir karmaşık tür) içerebilir. Daha fazla bilgi için bkz: [varlık veri modeli: Basit veri türleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
## <a name="representations-of-a-conceptual-model"></a>Kavramsal Model gösterimlerini  
 A *kavramsal model* bir belirli bazı verilerin yapısını varlıkları ve ilişkileri olarak gösterimidir. Kavramsal model temsil etmek için bir diyagram ile yoludur. Aşağıdaki diyagramda bir kavramsal model üç varlık türü ile temsil eder (`Book`, `Publisher`, ve `Author`) ve iki ilişkilendirmelerini (`PublishedBy` ve `WrittenBy`):  
  
 ![Model Gezinti özellikleri ile](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 Modelle ilgili bazı ayrıntılar iletmek için geldiğinde bu gösterim ancak, bazı eksiklikleri vardır. Örneğin, özellik türü ve varlık kümesi bilgilerini değil ilettiği diyagramı. Kavramsal model zenginliğinin daha net bir şekilde bir etki alanına özgü dil (DSL) iletilmesi. [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) adlı bir XML tabanlı DSL kullanan *kavramsal şema tanım dili* ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Yukarıdaki diyagramda kavramsal modelde CSDL tanımı aşağıda verilmiştir:  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
