---
title: "karmaşık türü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6a7fbdace6403d2f1037beff8fe28d7c934d3174
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="complex-type"></a>karmaşık türü
A *karmaşık tür* üzerinde zengin, yapılandırılmış özelliklerini tanımlamak için bir şablon [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) veya başka karmaşık türler. Her bir şablon aşağıdakileri içerir:  
  
-   Benzersiz bir ad. (Gerekli)  
  
    > [!NOTE]
    >  Karmaşık bir tür adı aynı ad alanı içindeki bir varlık türü adı ile aynı olamaz.  
  
-   Bir veya daha fazla form verileri [özellikleri](../../../../docs/framework/data/adonet/property.md). (İsteğe bağlı.)  
  
    > [!NOTE]
    >  Karmaşık türde bir özellik, başka bir karmaşık tür olabilir.  
  
 Karmaşık bir tür, karmaşık bir tür veri yükü ilkel tür özellikleri biçiminde veya başka karmaşık türler taşıyabilir, bir varlık türüne benzerdir. Ancak, karmaşık türleri ve varlık türleri arasındaki bazı temel farklar vardır:  
  
-   Karmaşık türler kimliklerine sahip değil ve bu nedenle bağımsız olarak bulunamaz. Karmaşık türler yalnızca varlık türleri veya diğer karmaşık türler özellikleri olarak bulunabilir.  
  
-   Karmaşık türler olamaz katılmak [ilişkilendirmeleri](../../../../docs/framework/data/adonet/association-type.md). Bir ilişkilendirme hiçbiri sonuna bir karmaşık tür olabilir ve bu nedenle [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) karmaşık türlerinde tanımlanamaz.  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL bir karmaşık türü, adres, ilkel türü özellikleri ile tanımlayan `StreetAddress`, `City`, `StateOrProvince`, `Country`, ve `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Karmaşık türü tanımlamak için `Address` (yukarıda) bir varlık türünde bir özellik olarak, özellik türü varlık türü tanımında belirtmesi gerekir. Aşağıdaki CSDL bildirir `Address` özelliği bir karmaşık tür üzerinde bir varlık türü (yayımcı) olarak:  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
