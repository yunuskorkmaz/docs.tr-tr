---
title: association set
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: 58d8794a21cc37ab84386c820b192fb29946095c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153436"
---
# <a name="association-set"></a>association set

*İlişki kümesi* , aynı türde [ilişki](association-type.md) örnekleri için mantıksal bir kapsayıcıdır. Bir ilişki kümesi, bir veri modelleme yapısı değildir; diğer bir deyişle, verilerin veya ilişkilerin yapısını tanımlamaz. Bunun yerine, bir ilişki kümesi, ilişki örneklerini gruplamak için bir barındırma veya depolama ortamı (ortak dil çalışma zamanı veya bir SQL Server veritabanı gibi) için bir yapı sağlar. böylece bir veri deposuna eşlenebilir.  
  
 Bir ilişki kümesi, [varlık kümelerinin](entity-set.md) ve ilişkilendirme kümelerinin mantıksal bir gruplandırması olan bir [varlık kapsayıcısı](entity-container.md)içinde tanımlanır.  
  
 İlişki kümesi için bir tanım aşağıdaki bilgileri içerir:  
  
- İlişki kümesi adı. Istenir  
  
- Örnek içereceği ilişki. Istenir  
  
- İki [ilişkilendirme kümesi sona erer](association-set-end.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy` ve `WrittenBy` . İlişki kümeleri hakkındaki bilgiler diyagramda bir şekilde gelse de, sonraki diyagramda bu modele göre ilişki kümelerinin ve varlık kümelerinin bir örneği gösterilmektedir.  
  
 ![Üç varlık türüne sahip örnek model](./media/association-set/example-model-three-entity-types.gif)  
  
 Aşağıdaki örnek, `PublishedBy` `Books` `Publishers` yukarıda gösterilen kavramsal modele bağlı olarak bir ilişki kümesi () ve iki varlık kümesini (ve) gösterir. `Books`Varlık kümesindeki bı, `Book` çalışma zamanında varlık türünün bir örneğini temsil eder. Benzer şekilde, PJ `Publisher` varlık kümesindeki bir örneği temsil eder `Publishers` . BiPj `PublishedBy` , ilişki kümesindeki ilişkilendirmenin bir örneğini temsil eder `PublishedBy` .  
  
 ![Bir küme örneği gösteren ekran görüntüsü.](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, Yukarıdaki diyagramda bulunan her ilişkilendirme için bir ilişki kümesiyle bir varlık kapsayıcısını tanımlar. Her ilişkilendirme kümesi için ad ve ilişkilendirmenin XML öznitelikleri kullanılarak tanımlandığını unutmayın.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 İki ilişkilendirme kümesi bir [ilişki kümesi ucu](association-set-end.md)paylaştığından, ilişkilendirme başına birden çok ilişki kümesi tanımlanması mümkündür. Aşağıdaki CSDL ilişki için iki ilişkilendirme kümesiyle bir varlık kapsayıcısını tanımlar `WrittenBy` . Ve varlık türleri için birden çok varlık kümesi tanımlandığından `Book` `Author` ve hiçbir ilişkilendirme kümesinin bir ilişki kümesi ucu paylaştığından emin olun.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
- [foreign key property](foreign-key-property.md)
