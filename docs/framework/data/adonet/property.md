---
title: "özellik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 929815e70678e535485e922616fe19d629b0fb41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="property"></a>özellik
*Özellikler* temel yapı taşlarıdır [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) ve [karmaşık türler](../../../../docs/framework/data/adonet/complex-type.md). Bir varlık türü örneği veya karmaşık türü örneği içeren veri özelliklerini ve Şekil özellikleri tanımlayın. Kavramsal model özelliklerinde bir sınıf üzerinde tanımlanan özellikleri benzer. Aynı şekilde bir sınıfındaki özellikleri şekil sınıfının tanımlamak ve nesneler hakkındaki bilgileri taşımak, kavramsal model özelliklerinde bir varlık türü şeklini tanımlayın ve varlık türü örnekleri hakkında bilgi taşımak.  
  
> [!NOTE]
>  Bu konuda açıklandığı gibi özellikleri, gezinti Özellikleri ' farklıdır. Daha fazla bilgi için bkz: [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md).  
  
 Özellik tanımı aşağıdaki bilgileri içerir:  
  
-   Bir özellik adı. (Gerekli)  
  
-   Bir özellik türü. (Gerekli)  
  
-   Bir dizi [modelleri](../../../../docs/framework/data/adonet/facet.md). (İsteğe bağlı)  
  
 Bir özellik, temel verileri (örneğin, bir dize, tamsayı veya Boolean değeri) veya yapılandırılmış verileri (örneğin, bir karmaşık tür) içerebilir. İlkel tür özellikleri, skaler özellikleri olarak da adlandırılır. Daha fazla bilgi için bkz: [varlık veri modeli: Basit veri türleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
> [!NOTE]
>  Karmaşık bir tür kendisi, karmaşık türleri olan özellikler olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`. Tür bilgileri her bir özellik için diyagramda ilettiği değil ancak her bir varlık türü birçok özelliğe sahiptir. Özellikler [varlık anahtarları](../../../../docs/framework/data/adonet/entity-key.md) (anahtarla) belirtilir.  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `Book` varlık yazın (Yukarıdaki diyagramda gösterildiği gibi) ve XML öznitelikleri kullanarak her özelliğin adını ve türünü gösterir. İsteğe bağlı bir model `Nullable`, ayrıca bir XML özniteliği kullanılarak tanımlanır.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Aşağıdaki çizimde gösterilen özellikleri biri bir karmaşık tür özelliği olduğunu mümkündür. Örneğin, `Address` özelliği `Publisher` varlık türü olabilir birkaç skaler özelliklerini oluşan bir karmaşık tür özelliği gibi `StreetAddress`, `City`, `StateOrProvince`, `Country`, ve `PostalCode`. Karmaşık bir tür CSDL gösterimini aşağıdaki gibi olur:  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
