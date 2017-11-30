---
title: "Varlık anahtarı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d0d7df7ff1a0e8e732688e10befb4bffa86599d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-key"></a>Varlık anahtarı
Bir *Varlık anahtarı* olan bir [özelliği](../../../../docs/framework/data/adonet/property.md) veya özelliklerini kümesi bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) kimliğini belirlemek için kullanılır. Bir varlık anahtarı oluşturan özellikleri tasarım zamanında seçilir. Varlık anahtarı özelliklerinin değerlerini bir varlık türü örneği içinde tanımlamalıdır bir [varlık kümesini](../../../../docs/framework/data/adonet/entity-set.md) çalışma zamanında. Bir varlık kümesindeki örnekleri benzersizliğini güvence altına almak için varlık anahtarı oluşturan özellikleri seçilmelidir.  
  
 Bir varlık anahtarı olması için bir özellikler kümesi için gereksinimleri şunlardır:  
  
-   Bir varlık kümesi içinde hiçbir iki varlık anahtarları aynı olabilir. Diğer bir deyişle, bir varlık kümesi içinde her iki varlıklar için bir anahtar oluşturan tüm özellikler için değerleri aynı olamaz. Ancak, bazı (ancak tüm) bir varlık değerleri, anahtar aynı olabilir.  
  
-   Bir varlık anahtarı null, sabit, kümesinden oluşmalıdır [ilkel tür özellikleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
-   Belirtilen varlık türü için varlık anahtarı oluşturan özelliklerini değiştiremezsiniz. Belirtilen varlık türü için birden fazla olası Varlık anahtarı izin veremez; yedek anahtarlar desteklenmez.  
  
-   Bir varlık bir devralma hiyerarşisinde söz konusu olduğunda, kök varlığın varlık anahtarı oluşturan tüm özellikleri içermelidir ve varlık anahtarı kök varlık türünde tanımlanmış olması gerekir. Daha fazla bilgi için bkz: [varlık veri modeli: Devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`. Kendi Varlık anahtarı oluşturan her bir varlık türü özelliklerini "(anahtar)" ile gösterilir. Unutmayın `Author` varlık türüne sahip iki özelliklerini içeren varlık anahtarı `Name` ve `Address`.  
  
 ![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. CSDL tanımlar `Book` Yukarıdaki diyagramda gösterildiği varlık türü. Varlık anahtarı başvurarak tanımlanır Not `ISBN` varlık türü özelliği.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 `ISBN` Özelliği olduğundan Varlık anahtarı için iyi bir seçimdir bir Uluslararası Standart Kitap numarası (ISBN) kitap benzersiz şekilde tanımlar.  
  
 CSDL tanımlar `Author` Yukarıdaki diyagramda gösterildiği varlık türü. Varlık anahtarı iki özelliklerini oluşur Not `Name` ve `Address`.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 Kullanarak `Name` ve `Address` aynı adı taşıyan iki yazarları aynı adresinde Canlı olası olduğundan varlık için makul bir seçim anahtarıdır. Ancak, bu seçenek bir varlık anahtarı için bir varlık kümesindeki benzersiz varlık anahtarları kesinlikle garanti etmez. Bir özellik gibi ekleme `AuthorId`, benzersiz şekilde tanımlamak için kullanılabilirdi yazar bu durumda önerilen.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık veri modeli temel kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
