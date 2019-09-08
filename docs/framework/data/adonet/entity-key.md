---
title: entity key
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: db867b3a853bd29f1faf1be2faf77776e48be2d2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795132"
---
# <a name="entity-key"></a>entity key
*Varlık anahtarı* , kimlik belirlemede kullanılan bir [varlık türünün](entity-type.md) bir [özelliğidir](property.md) . Bir varlık anahtarını oluşturan Özellikler tasarım zamanında seçilir. Varlık anahtarı özelliklerinin değerleri, çalışma zamanında bir [varlık kümesi](entity-set.md) içindeki bir varlık türü örneğini benzersiz şekilde tanımlamalıdır. Bir varlık kümesindeki örneklerin benzersizlik garantisi sağlamak için bir varlık anahtarı oluşturan Özellikler seçilmelidir.  
  
 Aşağıda bir varlık anahtarı olmak üzere bir özellik kümesinin gereksinimleri verilmiştir:  
  
- Bir varlık kümesi içinde iki varlık anahtarı aynı olamaz. Diğer bir deyişle, bir varlık kümesi içindeki tüm iki varlık için, bir anahtarı oluşturan tüm özelliklerin değerleri aynı olamaz. Ancak, bir varlık anahtarı oluşturan değerlerin bazıları (tümü değil) aynı olabilir.  
  
- Bir varlık anahtarı null yapılamayan, sabit, [ilkel tür özellikleri](entity-data-model-primitive-data-types.md)kümesinden oluşmalıdır.  
  
- Belirli bir varlık türü için bir varlık anahtarı oluşturan özellikler değiştirilemez. Belirli bir varlık türü için birden fazla olası varlık anahtarına izin verilemez; vekil anahtarlar desteklenmiyor.  
  
- Bir varlık devralma hiyerarşisine dahil edildiğinde, kök varlık varlık anahtarını oluşturan tüm özellikleri içermeli ve varlık anahtarı kök varlık türünde tanımlanmalıdır. Daha fazla bilgi için bkz [. varlık veri modeli: Devralma](entity-data-model-inheritance.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book`, `Publisher`, ve `Author`. Varlık anahtarını oluşturan her bir varlık türünün özellikleri "(Key)" ile belirtilir. `Author` Varlık türünün iki `Name` özelliklerden oluşan bir varlık anahtarına sahip olduğuna ve `Address`.  
  
 ![Üç varlık türüne sahip örnek model](./media/entity-key/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki csdl, Yukarıdaki diyagramda `Book` gösterilen varlık türünü tanımlar. Varlık anahtarının, varlık türünün `ISBN` özelliğine başvurarak tanımlandığını unutmayın.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Uluslararası `ISBN` bir standart defter numarası (ISBN) bir kitabı benzersiz bir şekilde tanımladığından, özelliği varlık anahtarı için iyi bir seçimdir.  
  
 Aşağıdaki csdl, Yukarıdaki diyagramda `Author` gösterilen varlık türünü tanımlar. Varlık anahtarının iki özellik `Name` ve `Address`olduğunu unutmayın.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 Varlık `Name` anahtarı `Address` için ve kullanılması makul bir seçimdir, çünkü aynı ada sahip iki yazar aynı adreste yaşlılıı düşüktür. Ancak, bir varlık anahtarı için bu seçenek bir varlık kümesindeki benzersiz varlık anahtarlarını kesinlikle garanti etmez. Bir yazarı benzersiz bir şekilde tanımlamak `AuthorId`için kullanılabilecek gibi bir özellik ekleme Bu durumda önerilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
