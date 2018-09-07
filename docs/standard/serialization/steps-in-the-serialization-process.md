---
title: Serileştirme işlemi adımları
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: ef81ecc7ca177fa9360f53a6b66015412d282065
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084927"
---
# <a name="steps-in-the-serialization-process"></a>Serileştirme işlemi adımları
Zaman <xref:System.Runtime.Serialization.Formatter.Serialize*> yöntemi çağrıldığında bir [biçimlendirici](xref:System.Runtime.Serialization.Formatter), nesne seri hale getirme aşağıdaki kuralları dizisini göre devam eder:

- Biçimlendirici bir vekil Seçici olup olmadığını belirlemek için bir onay yapılır. Biçimlendirici varsa, vekil Seçici belirtilen türe ait nesneleri işleme olup olmadığını denetleyin. Nesne türü Seçici işliyorsa <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> vekil seçici üzerinde çağrılır.

- Hiçbir vekil Seçici yok veya nesne türü işlemez, nesne ile işaretlenmiş olup olmadığını belirlemek için bir onay yapılır [Serializable](xref:System.SerializableAttribute) özniteliği. Nesne, yoksa bir <xref:System.Runtime.Serialization.SerializationException> oluşturulur.

- Nesne uygun şekilde işaretlenmişse, nesne uygulayan olup olmadığını denetleyin. <xref:System.Runtime.Serialization.ISerializable> arabirimi. Nesne varsa, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> nesnesinde çağrılır.
  
- Nesne uygulamazsa <xref:System.Runtime.Serialization.ISerializable>, varsayılan seri hale getirme İlkesi kullanılır, tüm alanları serileştirmek işaretlenmemiş olarak [getirilmemiş](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkili Serileştirme](binary-serialization.md)  
- [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)
