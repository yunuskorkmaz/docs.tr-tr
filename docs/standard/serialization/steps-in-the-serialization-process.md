---
title: Seri hale getirme işlemi adımları
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: b44b3b0539237c0f0d0a4af877e8955c6f612003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="steps-in-the-serialization-process"></a>Seri hale getirme işlemi adımları
Zaman <xref:System.Runtime.Serialization.Formatter.Serialize*> yöntemi çağrıldığında bir [biçimlendirici](xref:System.Runtime.Serialization.Formatter), nesneyi seri hale getirme aşağıdaki kuralları dizisi göre devam eder:

- Biçimlendirici bir vekil Seçici olup olmadığını belirlemek için bir onay yapılır. Biçimlendirici varsa, vekil Seçici belirtilen türe ait nesneleri işleme olup olmadığını denetleyin. Seçici nesne türü işliyorsa <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> yedek seçicisinde olarak adlandırılır.

- Hiçbir yedek Seçici yok veya nesne türündeki işlemiyor, nesne ile işaretlenmiş olup olmadığını belirlemek için bir denetim gerçekleştirilir [Serializable](xref:System.SerializableAttribute) özniteliği. Nesne, yoksa bir <xref:System.Runtime.Serialization.SerializationException> oluşturulur.

- Nesne uygun şekilde işaretlenir nesne uygulayan olup olmadığını kontrol edin <xref:System.Runtime.Serialization.ISerializable> arabirimi. Nesne varsa, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> nesnede olarak adlandırılır.
  
- Nesne uygulamazsa <xref:System.Runtime.Serialization.ISerializable>, varsayılan seri hale getirme ilke kullanılır, tüm alanları serileştirmek işaretlenmemiş olarak [getirilmemiş](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İkili Serileştirme](binary-serialization.md)  
 [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)