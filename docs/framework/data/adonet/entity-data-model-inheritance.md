---
title: 'Varlık Veri Modeli: devralma'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 4c4abc371000006d40ede3d904b0437f3f85e3e7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738457"
---
# <a name="entity-data-model-inheritance"></a>Varlık Veri Modeli: devralma
Varlık Veri Modeli (EDM), [varlık türleri](entity-type.md)için devralmayı destekler. EDM 'da devralma, nesne odaklı programlama dillerinde sınıfların devralmasına benzerdir. Nesne odaklı dillerdeki sınıflar gibi, kavramsal bir modelde, başka bir varlık türünden ( *temel tür*) devralan bir varlık türü ( *türetilmiş bir tür*) tanımlayabilirsiniz. Ancak, nesne odaklı programlamada sınıfların aksine, kavramsal bir modelde türetilmiş tür her zaman temel türün tüm [özelliklerini](property.md) ve [gezinti özelliklerini](navigation-property.md) devralır. Türetilmiş bir türdeki devralınan özellikleri geçersiz kılamazsınız.  
  
 Kavramsal modelde, türetilmiş bir türün başka bir türetilmiş türden devraldığı devralma hiyerarşileri oluşturabilirsiniz. Hiyerarşinin en üstündeki tür (türetilmiş tür olmayan hiyerarşide bir tür) *kök türü*olarak adlandırılır. Devralma hiyerarşisinde, [varlık anahtarının](entity-key.md) kök türünde tanımlanması gerekir.  
  
 Türetilmiş bir türün birden fazla türden devraldığı devralma hiyerarşileri derlenemez. Örneğin, `Book` varlık türü olan bir kavramsal modelde, `FictionBook` türetilmiş türleri ve her birinin `Book`devraldığı `NonFictionBook` tanımlayabilirsiniz. Ancak, `FictionBook` ve `NonFictionBook` türlerinden devralan bir tür tanımlayamazsınız.  
  
## <a name="example"></a>Örnek  

Aşağıdaki diyagramda dört varlık türü olan kavramsal bir model gösterilmektedir: `Book`, `FictionBook`, `Publisher`ve `Author`. `FictionBook` varlık türü, `Book` varlık türünden devralan türetilmiş bir türdür. `FictionBook` türü `ISBN (Key)`, `Title`ve `Revision` özelliklerini devralır ve `Genre`adlı ek bir özellik tanımlar.  
  
 ![Dört varlık türüyle kavramsal bir model gösteren diyagram.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, `Book` türünden devralan `FictionBook`bir varlık türü tanımlar (Yukarıdaki diyagramda olduğu gibi):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
