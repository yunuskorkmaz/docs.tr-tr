---
title: association set
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: 43ab6cf9f1ee8cb971810add6b9a89467726f3e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785036"
---
# <a name="association-set"></a>association set
*İlişki kümesi* , aynı türde [ilişki](association-type.md) örnekleri için mantıksal bir kapsayıcıdır. Bir ilişki kümesi, bir veri modelleme yapısı değildir; diğer bir deyişle, verilerin veya ilişkilerin yapısını tanımlamaz. Bunun yerine, bir ilişki kümesi, ilişki örneklerini gruplamak için bir barındırma veya depolama ortamı (ortak dil çalışma zamanı veya bir SQL Server veritabanı gibi) için bir yapı sağlar. böylece bir veri deposuna eşlenebilir.  
  
 Bir ilişki kümesi, [varlık kümelerinin](entity-set.md) ve ilişkilendirme kümelerinin mantıksal bir gruplandırması olan bir [varlık kapsayıcısı](entity-container.md)içinde tanımlanır.  
  
 İlişki kümesi için bir tanım aşağıdaki bilgileri içerir:  
  
- İlişki kümesi adı. Istenir  
  
- Örnek içereceği ilişki. Istenir  
  
- İki [ilişkilendirme kümesi sona erer](association-set-end.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy`ve. `WrittenBy` İlişki kümeleri hakkındaki bilgiler diyagramda bir şekilde gelse de, sonraki diyagramda bu modele göre ilişki kümelerinin ve varlık kümelerinin bir örneği gösterilmektedir.  
  
 ![Üç varlık türüne sahip örnek model](./media/association-set/example-model-three-entity-types.gif)  
  
 Aşağıdaki örnek, yukarıda gösterilen kavramsal modele bağlı`PublishedBy`olarak bir ilişki kümesi ()`Books` ve `Publishers`iki varlık kümesini (ve) gösterir. Varlık kümesindeki bı, çalışma zamanında `Book` varlık türünün bir örneğini temsil eder. `Books` Benzer şekilde, PJ `Publisher` `Publishers` varlık kümesindeki bir örneği temsil eder. Bipj, `PublishedBy` `PublishedBy` ilişki kümesindeki ilişkilendirmenin bir örneğini temsil eder.  
  
 ![Bir küme örneği gösteren ekran görüntüsü.](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, Yukarıdaki diyagramda bulunan her ilişkilendirme için bir ilişki kümesiyle bir varlık kapsayıcısını tanımlar. Her ilişkilendirme kümesi için ad ve ilişkilendirmenin XML öznitelikleri kullanılarak tanımlandığını unutmayın.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 İki ilişkilendirme kümesi bir [ilişki kümesi ucu](association-set-end.md)paylaştığından, ilişkilendirme başına birden çok ilişki kümesi tanımlanması mümkündür. Aşağıdaki csdl `WrittenBy` ilişki için iki ilişkilendirme kümesiyle bir varlık kapsayıcısını tanımlar. `Book` Ve`Author` varlık türleri için birden çok varlık kümesi tanımlandığından ve hiçbir ilişkilendirme kümesinin bir ilişki kümesi ucu paylaştığından emin olun.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
- [foreign key property](foreign-key-property.md)
