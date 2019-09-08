---
title: 'Varlık Veri Modeli: Devralma'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 21dbdff63c07dbcdac8de7bf4b3a8e5d0ece7901
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784074"
---
# <a name="entity-data-model-inheritance"></a>Varlık Veri Modeli: Devralma
Varlık Veri Modeli (EDM), [varlık türleri](entity-type.md)için devralmayı destekler. EDM 'da devralma, nesne odaklı programlama dillerinde sınıfların devralmasına benzerdir. Nesne odaklı dillerdeki sınıflar gibi, kavramsal bir modelde, başka bir varlık türünden ( *temel tür*) devralan bir varlık türü ( *türetilmiş bir tür*) tanımlayabilirsiniz. Ancak, nesne odaklı programlamada sınıfların aksine, kavramsal bir modelde türetilmiş tür her zaman temel türün tüm [özelliklerini](property.md) ve [gezinti özelliklerini](navigation-property.md) devralır. Türetilmiş bir türdeki devralınan özellikleri geçersiz kılamazsınız.  
  
 Kavramsal modelde, türetilmiş bir türün başka bir türetilmiş türden devraldığı devralma hiyerarşileri oluşturabilirsiniz. Hiyerarşinin en üstündeki tür (türetilmiş tür olmayan hiyerarşide bir tür) *kök türü*olarak adlandırılır. Devralma hiyerarşisinde, [varlık anahtarının](entity-key.md) kök türünde tanımlanması gerekir.  
  
 Türetilmiş bir türün birden fazla türden devraldığı devralma hiyerarşileri derlenemez. Örneğin, varlık `Book` türü olan bir kavramsal modelde, türetilmiş türleri `FictionBook` tanımlayabilir ve `NonFictionBook` bunların her biri öğesinden `Book`devralınır. Ancak, `FictionBook` ve `NonFictionBook` türlerinden devralan bir tür tanımlayamazsınız.  
  
## <a name="example"></a>Örnek  

Aşağıdaki diyagramda dört varlık türü olan kavramsal model gösterilmektedir `Book`:, `FictionBook`, `Publisher`, ve `Author`. Varlık türü, `Book` varlık türünden devralan türetilmiş bir türdür. `FictionBook` Türü,`ISBN (Key)` ,ve`Revision` özelliklerini devralır ve adlı`Genre`ek bir özelliği tanımlar. `Title` `FictionBook`  
  
 ![Dört varlık türüyle kavramsal bir model gösteren diyagram.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki csdl, `Book` türünden devralan (Yukarıdaki diyagramda `FictionBook`olduğu gibi) bir varlık türünü tanımlar:  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
