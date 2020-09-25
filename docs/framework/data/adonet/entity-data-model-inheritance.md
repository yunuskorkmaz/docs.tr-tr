---
title: 'Varlık Veri Modeli: Devralma'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 057040eee411988c46adc9c4cabcfe5f5a185e1b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175466"
---
# <a name="entity-data-model-inheritance"></a>Varlık Veri Modeli: Devralma

Varlık Veri Modeli (EDM), [varlık türleri](entity-type.md)için devralmayı destekler. EDM 'da devralma, nesne odaklı programlama dillerinde sınıfların devralmasına benzerdir. Nesne odaklı dillerdeki sınıflar gibi, kavramsal bir modelde, başka bir varlık türünden ( *temel tür*) devralan bir varlık türü ( *türetilmiş bir tür*) tanımlayabilirsiniz. Ancak, nesne odaklı programlamada sınıfların aksine, kavramsal bir modelde türetilmiş tür her zaman temel türün tüm [özelliklerini](property.md) ve [gezinti özelliklerini](navigation-property.md) devralır. Türetilmiş bir türdeki devralınan özellikleri geçersiz kılamazsınız.  
  
 Kavramsal modelde, türetilmiş bir türün başka bir türetilmiş türden devraldığı devralma hiyerarşileri oluşturabilirsiniz. Hiyerarşinin en üstündeki tür (türetilmiş tür olmayan hiyerarşide bir tür) *kök türü*olarak adlandırılır. Devralma hiyerarşisinde, [varlık anahtarının](entity-key.md) kök türünde tanımlanması gerekir.  
  
 Türetilmiş bir türün birden fazla türden devraldığı devralma hiyerarşileri derlenemez. Örneğin, varlık türü olan bir kavramsal modelde `Book` , türetilmiş türleri tanımlayabilir `FictionBook` ve bunların `NonFictionBook` her biri öğesinden devralınır `Book` . Ancak, ve türlerinden devralan bir tür tanımlayamazsınız `FictionBook` `NonFictionBook` .  
  
## <a name="example"></a>Örnek  

Aşağıdaki diyagramda dört varlık türü olan kavramsal model gösterilmektedir: `Book` , `FictionBook` , `Publisher` , ve `Author` . `FictionBook`Varlık türü, varlık türünden devralan türetilmiş bir türdür `Book` . `FictionBook`Türü `ISBN (Key)` ,, `Title` ve özelliklerini devralır `Revision` ve adlı ek bir özelliği tanımlar `Genre` .  
  
 ![Dört varlık türüyle kavramsal bir model gösteren diyagram.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır. Aşağıdaki CSDL, `FictionBook` `Book` türünden devralan (Yukarıdaki diyagramda olduğu gibi) bir varlık türünü tanımlar:  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
