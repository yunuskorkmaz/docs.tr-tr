---
title: model olarak bildirilen işlev
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: f92bdfedaefca7182b5de72abae9852965d83ff7
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332052"
---
# <a name="model-declared-function"></a>model olarak bildirilen işlev
A *model olarak bildirilen işlev* kavramsal modelde bildirildi, ancak bu kavramsal modelde tanımlı değil, bir işlevdir. İşlevi barındırma veya depolama ortamında tanımlanabilir. Örneğin, bir model olarak bildirilen işlev dolayısıyla kavramsal modelde sunucu tarafında işlevselliği kullanıma sunma, bir veritabanında tanımlı bir işlev eşleştirilmiş olabilir.  
  
 Model olarak bildirilen bir işlevin bildirimi, aşağıdaki bilgileri içerir:  
  
-   İşlevin adı. (Gerekli)  
  
-   Dönüş değerinin türü. (İsteğe bağlı)  
  
    > [!NOTE]
    >  Dönüş değeri belirtilmişse, dönüş türü void alır.  
  
-   Parametre adı ve türü de dahil olmak üzere, parametre bilgileri. (İsteğe bağlı)  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. CSDL model olarak bildirilen bir işlevi bir uygulamasıdır bir [işlev içeri aktarma](https://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d). Aşağıdaki CSDL işlev tanımını içeri aktarma ile varlık kapsayıcısı tanımlar. Dönüş türü belirtildiği işlevi için dönüş türü void olduğunu unutmayın.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
