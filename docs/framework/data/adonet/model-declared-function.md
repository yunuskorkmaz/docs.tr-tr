---
title: model-declared function
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: cb2fca52604bd57f25469f5621c292a27638c76f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794803"
---
# <a name="model-declared-function"></a>model-declared function
Model olarak tanımlanmış bir *işlev* , kavramsal modelde belirtilen ancak bu kavramsal modelde tanımlı olmayan bir işlevdir. İşlev barındırma veya depolama ortamında tanımlanmış olabilir. Örneğin, model tarafından tanımlanan bir işlev, veritabanında tanımlanmış bir işlevle eşleştirilebilir ve bu nedenle kavramsal modelde sunucu tarafı işlevselliği ortaya çıkabilir.  
  
 Model tarafından tanımlanan bir işlevin bildirimi, aşağıdaki bilgileri içerir:  
  
- İşlevin adı. Istenir  
  
- Dönüş değerinin türü. (İsteğe bağlı)  
  
    > [!NOTE]
    > Dönüş değeri belirtilmemişse, dönüş türü void olur.  
  
- Parametre adı ve türü dahil olmak üzere parametre bilgileri. (İsteğe bağlı)  
  
## <a name="example"></a>Örnek  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. CSDL 'de, model tarafından tanımlanan bir işlevin bir uygulamasý bir işlev içeri aktarmasıdır ( [FunctionImport öğesi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)kullanılarak). Aşağıdaki CSDL, bir işlev içeri aktarma tanımına sahip bir varlık kapsayıcısını tanımlar. Dönüş türü belirtilmediği için işlevin dönüş türünün void olduğunu unutmayın.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
