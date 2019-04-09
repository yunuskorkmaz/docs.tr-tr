---
title: entity container
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 4a629a800df63c67dc17d3fc1531a9862861e9c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144072"
---
# <a name="entity-container"></a>entity container
Bir *varlık kapsayıcısı* mantıksal bir gruplandırmasıdır [varlık kümeleri](../../../../docs/framework/data/adonet/entity-set.md), [ilişki Setleri](../../../../docs/framework/data/adonet/association-set.md), ve [işlev içeri aktarmalar](../../../../docs/framework/data/adonet/model-declared-function.md).  
  
 Aşağıdaki kavramsal modelde tanımlı bir varlık kapsayıcısının true olması gerekir:  
  
-   En az bir varlık kapsayıcısı her kavramsal modelde tanımlanması gerekir.  
  
-   Varlık kapsayıcısının her kavramsal model içinde benzersiz bir adı olmalıdır.  
  
 Varlık kapsayıcısı varlık kümeleri veya varlık türleri veya bir veya daha fazla ad alanı içinde tanımlanan ilişkileri kullanın ve ilişki Setleri tanımlayabilirsiniz. Daha fazla bilgi için [varlık veri modeli: Ad alanları](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).  
  
## <a name="example"></a>Örnek  
 Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`.  Daha fazla bilgi için sonraki örneğe bakın.  
  
 ![Üç varlık türleri ile örnek modeli](./media/entity-container/example-model-three-entity-types.gif)  
  
 Diyagram varlık kapsayıcı bilgilerini sağlamadığından olsa da, kavramsal modelin varlık kapsayıcısı tanımlamanız gerekir. [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Yukarıdaki diyagramda gösterilen kavramsal modelin varlık kapsayıcısı aşağıdaki CSDL tanımlar. Varlık kapsayıcı adı bir XML özniteliği tanımlandığını aklınızda bulundurun.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
