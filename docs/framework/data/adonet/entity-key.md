---
title: entity key
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: bf8ab7ffacd7565e408e4851ed0f1ef4636b5d80
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599652"
---
# <a name="entity-key"></a>entity key
Bir *Varlık anahtarı* olduğu bir [özelliği](../../../../docs/framework/data/adonet/property.md) veya özellikleri kümesi bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) kimliğini belirlemek için kullanılır. Bir varlık anahtarı oluşturan özelliklerini tasarım zamanında seçilir. Varlık anahtar özelliklerin değerlerini içinde bir varlık türü örneği benzersiz şekilde tanımlamalıdır bir [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md) çalışma zamanında. Bir varlık kümesindeki örneklerin benzersizliği garanti etmek için bir varlık anahtarı oluşturan özellikleri seçilmelidir.  
  
 Bir varlık anahtarı için bir özellikler kümesini için gereksinimleri şunlardır:  
  
- Bir varlık kümesi içinde hiçbir iki varlık anahtarları aynı olabilir. Diğer bir deyişle, herhangi iki varlık için bir varlık kümesindeki bir anahtar oluşturan tüm özellikler için değerleri aynı olamaz. Ancak, bazı (Tümü değil) bir varlığı değerleri olan anahtar aynı olabilir.  
  
- Varlık anahtarı NULL olmayan, sabit, kümesinden oluşmalıdır [ilkel tür özellikleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
- Belirtilen varlık türü için bir varlık anahtarı oluşturan özelliklerini değiştiremezsiniz. Belirtilen varlık türü için olası Varlık anahtarı birden fazla izin veremez; vekil anahtarlar desteklenmez.  
  
- Bir devralma hiyerarşisinde bir varlığı söz konusu olduğunda kök varlığın varlık anahtarı oluşturan tüm özelliklerini içermelidir ve varlık anahtarı üzerinde kök varlık türü olarak tanımlanmış olması gerekir. Daha fazla bilgi için [varlık veri modeli: Devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## <a name="example"></a>Örnek  
 Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`. Her varlık türünün varlık anahtarıyla olun özellikleri "(anahtar)" ile belirtilir. Unutmayın `Author` varlık türünde iki özelliklerini içeren bir varlık anahtarı `Name` ve `Address`.  
  
 ![Üç varlık türleri ile örnek modeli](./media/entity-key/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `Book` Yukarıdaki diyagramda gösterilen varlık türü. Varlık anahtarı başvurarak tanımlandığını aklınızda bulundurun `ISBN` varlık türü özelliği.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 `ISBN` Özelliği olduğundan Varlık anahtarı için iyi bir seçim bir kitap tanıtan bir Uluslararası Standart Kitap sayısı (ISBN).  
  
 Aşağıdaki CSDL tanımlar `Author` Yukarıdaki diyagramda gösterilen varlık türü. Varlık anahtarı iki özellikten oluşur Not `Name` ve `Address`.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 Kullanarak `Name` ve `Address` çünkü aynı adlı iki yazarları aynı adresindeki live olasılığının düşük olduğu varlık için makul bir seçim anahtardır. Ancak, bu seçenek bir varlık anahtarı için bir varlık kümesindeki benzersiz varlık anahtarları kesinlikle garanti etmez. Bir özellik gibi ekleme `AuthorId`, benzersiz şekilde tanımlamak için kullanılabilir bir yazar önerilen bu durumda.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
