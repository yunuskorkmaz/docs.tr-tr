---
title: Gezinme özelliğinin - ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: b57ecf9329aa9ea8afc07507613c9e3961bfd0a9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836606"
---
# <a name="navigation-property"></a>Gezinme özelliği

A *gezinti özelliği* üzerinde isteğe bağlı bir özellik olan bir [varlık türü](entity-type.md) olanak tanıyan bir gezinti için [son](association-end.md) , bir [ilişkilendirme](association-type.md) için diğer sonu. Diğer aksine [özellikleri](property.md), gezinti özellikleri veri taşıyan değil.

Bir gezinti özelliği tanımı aşağıdakileri içerir:

- Bir ad. (Gerekli)

- Bu varlıklardan ilişkilendirme. (Gerekli)

- Bu varlıklardan ilişkilendirmenin sona erer. (Gerekli)

Gezinti özellikleri her iki varlık türlerini ilişkilendirme ucunda isteğe bağlı olduğunu unutmayın. İlişkilendirme sonunda bir varlık türünün gezinme özelliğinin tanımlarsanız, ilişkinin diğer ucundaki varlık türünün gezinme özelliğinin tanımlamak zorunda değil.

Veri türü bir gezinti özelliği tarafından belirlenir [çoğulluk](association-end-multiplicity.md) kendi uzak [ilişkilendirme end](association-end.md). Örneğin, bir gezinti özelliği varsayalım `OrdersNavProp`, bulunuyor. bir `Customer` varlık türü ve arasında bir-çok ilişkisi gider `Customer` ve `Order`. Gezinti özelliği için Uzak ilişkilendirme end çok çeşitlilik sahip olduğundan (\*), kendi veri türüne koleksiyonudur (, `Order`). Benzer şekilde, bir gezinti özelliği, `CustomerNavProp`, bulunuyor `Order` varlık türü, veri türü olacak `Customer`, uzak uç çokluğu bir (1) olduğundan.

## <a name="example"></a>Örnek

Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`. Gezinti özellikleri `Publisher` ve `Authors`, kitap varlık türünde tanımlanır. Gezinti özelliği `Books` hem Yayımcı varlık türü üzerinde tanımlanan ve `Author` varlık türü.

 ![Kavramsal bir modelle üç varlık türlerini gösteren diyagram.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

[ADO.NET Entity Framework](./ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](./ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Aşağıdaki CSDL tanımlar `Book` Yukarıdaki diyagramda gösterilen varlık türü:

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

XML özniteliği bir gezinti özelliği tanımlamak gereken bilgileri iletişim kurmak için kullanıldığını unutmayın: Öznitelik `Name` özelliğin adını içeren `Relationship` bunu gider, ilişkilendirmenin adı içerir ve `FromRole` ve `ToRole` ilişki sonu içerir.

## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
- [İlişkiler, gezinti özellikleri ve yabancı anahtarlar](/ef/ef6/fundamentals/relationships)
