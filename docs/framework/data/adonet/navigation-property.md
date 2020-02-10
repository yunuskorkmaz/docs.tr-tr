---
title: Gezinti özelliği
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: eaf22ad4dd24b4bf046f14ccabd435a9ecd1776f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094390"
---
# <a name="navigation-property"></a>Gezinti özelliği

Bir *gezinti özelliği* , bir [ilişkinin](association-type.md) bir [sonundan](association-end.md) diğer bir uca gezinmesine izin veren bir [varlık türü](entity-type.md) üzerinde isteğe bağlı bir özelliktir. Diğer [özelliklerden](property.md)farklı olarak, gezinti özellikleri verileri taşımaz.

Bir gezinti özelliği tanımı şunları içerir:

- Bir ad. Istenir

- Gittiği ilişki. Istenir

- Gezindiğinde ilişkilendirmenin uçları. Istenir

Gezinme özellikleri, bir ilişkilendirmenin sonundaki her iki varlık türü için isteğe bağlıdır. Bir ilişkinin sonundaki bir varlık türünde bir gezinti özelliği tanımlarsanız, ilişkilendirmenin diğer sonundaki varlık türünde bir gezinti özelliği tanımlamanız gerekmez.

Gezinti özelliğinin veri türü, uzak [ilişki ucunun](association-end.md) [çoğulluğu](association-end-multiplicity.md) tarafından belirlenir. Örneğin, bir `Customer` varlık türünde `OrdersNavProp`bir gezinti özelliği olduğunu varsayalım ve `Customer` ile `Order`arasında bire çok ilişkilendirmeyi gider. Gezinti özelliği için uzak ilişki ucunun çok sayıda (\*) çoğulluğu olduğundan, veri türü bir koleksiyon (`Order`) olur. Benzer şekilde, `Order` varlık türünde bir gezinti özelliği varsa `CustomerNavProp`, uzak uçtaki çoğulluğu bir (1) olduğundan, veri türü `Customer`olur.

## <a name="example"></a>Örnek

Aşağıdaki diyagramda üç varlık türü olan kavramsal bir model gösterilmektedir: `Book`, `Publisher`ve `Author`. `Publisher` ve `Authors` gezinti özellikleri kitap varlık türü üzerinde tanımlanmıştır. Gezinti özelliği `Books` hem Yayımcı varlık türü hem de `Author` varlık türü üzerinde tanımlanmıştır.

![Üç varlık türü ile kavramsal bir modeli gösteren diyagram.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, Yukarıdaki diyagramda gösterilen `Book` varlık türünü tanımlar:

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

XML öznitelikleri, bir gezinti özelliği tanımlamak için gereken bilgileri iletmek için kullanılır: öznitelik `Name` özelliğin adını, `Relationship` gittiği ilişkinin adını içerir ve `FromRole` ve `ToRole` ilişkinin uçlarını içerir.

## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
- [İlişkiler, gezinti özellikleri ve yabancı anahtarlar](/ef/ef6/fundamentals/relationships)
