---
title: Varlık anahtarı
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: 02b877efb463e47f9147239c895c482f2d716714
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664034"
---
# <a name="entity-key"></a>Varlık anahtarı
Bir *Varlık anahtarı* olduğu bir [özelliği](../../../../docs/framework/data/adonet/property.md) veya özellikleri kümesi bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) kimliğini belirlemek için kullanılır. Bir varlık anahtarı oluşturan özelliklerini tasarım zamanında seçilir. Varlık anahtar özelliklerin değerlerini içinde bir varlık türü örneği benzersiz şekilde tanımlamalıdır bir [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md) çalışma zamanında. Bir varlık kümesindeki örneklerin benzersizliği garanti etmek için bir varlık anahtarı oluşturan özellikleri seçilmelidir.  
  
 Bir varlık anahtarı için bir özellikler kümesini için gereksinimleri şunlardır:  
  
-   Bir varlık kümesi içinde hiçbir iki varlık anahtarları aynı olabilir. Diğer bir deyişle, herhangi iki varlık için bir varlık kümesindeki bir anahtar oluşturan tüm özellikler için değerleri aynı olamaz. Ancak, bazı (Tümü değil) bir varlığı değerleri olan anahtar aynı olabilir.  
  
-   Varlık anahtarı NULL olmayan, sabit, kümesinden oluşmalıdır [ilkel tür özellikleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
-   Belirtilen varlık türü için bir varlık anahtarı oluşturan özelliklerini değiştiremezsiniz. Belirtilen varlık türü için olası Varlık anahtarı birden fazla izin veremez; vekil anahtarlar desteklenmez.  
  
-   Bir devralma hiyerarşisinde bir varlığı söz konusu olduğunda kök varlığın varlık anahtarı oluşturan tüm özelliklerini içermelidir ve varlık anahtarı üzerinde kök varlık türü olarak tanımlanmış olması gerekir. Daha fazla bilgi için [varlık veri modeli: Devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="example"></a>Örnek  
 Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`. Her varlık türünün varlık anahtarıyla olun özellikleri "(anahtar)" ile belirtilir. Unutmayın `Author` varlık türünde iki özelliklerini içeren bir varlık anahtarı `Name` ve `Address`.  
  
 ![Örnek Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `Book` Yukarıdaki diyagramda gösterilen varlık türü. Varlık anahtarı başvurarak tanımlandığını aklınızda bulundurun `ISBN` varlık türü özelliği.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 `ISBN` Özelliği olduğundan Varlık anahtarı için iyi bir seçim bir kitap tanıtan bir Uluslararası Standart Kitap sayısı (ISBN).  
  
 Aşağıdaki CSDL tanımlar `Author` Yukarıdaki diyagramda gösterilen varlık türü. Varlık anahtarı iki özellikten oluşur Not `Name` ve `Address`.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 Kullanarak `Name` ve `Address` çünkü aynı adlı iki yazarları aynı adresindeki live olasılığının düşük olduğu varlık için makul bir seçim anahtardır. Ancak, bu seçenek bir varlık anahtarı için bir varlık kümesindeki benzersiz varlık anahtarları kesinlikle garanti etmez. Bir özellik gibi ekleme `AuthorId`, benzersiz şekilde tanımlamak için kullanılabilir bir yazar önerilen bu durumda.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
