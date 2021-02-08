---
description: 'Daha fazla bilgi edinin: gezinti özelliği'
title: Gezinti özelliği
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 4655c8ef1b18972697e41fa1c7c6185945335aa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786244"
---
# <a name="navigation-property"></a>Gezinti özelliği

Bir *gezinti özelliği* , bir [ilişkinin](association-type.md) bir [sonundan](association-end.md) diğer bir uca gezinmesine izin veren bir [varlık türü](entity-type.md) üzerinde isteğe bağlı bir özelliktir. Diğer [özelliklerden](property.md)farklı olarak, gezinti özellikleri verileri taşımaz.

Bir gezinti özelliği tanımı şunları içerir:

- Bir ad. Istenir

- Gittiği ilişki. Istenir

- Gezindiğinde ilişkilendirmenin uçları. Istenir

Gezinme özellikleri, bir ilişkilendirmenin sonundaki her iki varlık türü için isteğe bağlıdır. Bir ilişkinin sonundaki bir varlık türünde bir gezinti özelliği tanımlarsanız, ilişkilendirmenin diğer sonundaki varlık türünde bir gezinti özelliği tanımlamanız gerekmez.

Gezinti özelliğinin veri türü, uzak [ilişki ucunun](association-end.md) [çoğulluğu](association-end-multiplicity.md) tarafından belirlenir. Örneğin, bir gezinti özelliğinin bir `OrdersNavProp` `Customer` varlık türünde var olduğunu ve ve arasında bire çok ilişkilendirmesi gezindiğini varsayalım `Customer` `Order` . Gezinti özelliği için uzak ilişki ucunun çok sayıda () çoğulluğu olduğundan \* , veri türü bir koleksiyon (/) olur `Order` . Benzer şekilde, bir gezinti özelliği `CustomerNavProp` `Order` varlık türünde varsa, `Customer` uzak uçtaki çoğulluğu bir (1) olduğundan, veri türü olacaktır.

## <a name="example"></a>Örnek

Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book` , `Publisher` , ve `Author` . Gezinti özellikleri `Publisher` ve `Authors` kitap varlık türü üzerinde tanımlanmıştır. Gezinti özelliği `Books` hem Yayımcı varlık türü hem de varlık türü üzerinde tanımlanmıştır `Author` .

![Üç varlık türü ile kavramsal bir modeli gösteren diyagram.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, `Book` Yukarıdaki diyagramda gösterilen varlık türünü tanımlar:

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

XML öznitelikleri, bir gezinti özelliği tanımlamak için gereken bilgileri iletmek için kullanılır: öznitelik, `Name` özelliğin adını içerir, `Relationship` gezindiği ilişkinin adını içerir ve `FromRole` `ToRole` ilişkinin uçlarını içerir.

## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
- [İlişkiler, gezinti özellikleri ve yabancı anahtarlar](/ef/ef6/fundamentals/relationships)
