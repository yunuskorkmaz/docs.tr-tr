---
title: Serileştirme işlemi adımları
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: f30dd550437e6bc1030c79865bf2edd2c0efbfa9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741045"
---
# <a name="steps-in-the-serialization-process"></a>Serileştirme işlemi adımları
<xref:System.Runtime.Serialization.Formatter.Serialize%2A> Yöntem bir [biçimlendirici](xref:System.Runtime.Serialization.Formatter)üzerinde çağrıldığında, nesne serileştirme aşağıdaki kural dizisine göre devam eder:

- Biçimlendirici bir vekil Seçici olup olmadığını belirlemek için bir onay yapılır. Biçimlendirici varsa, vekil Seçici belirtilen türe ait nesneleri işleme olup olmadığını denetleyin. Seçici, nesne türünü işlediğinde, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> vekil seçicide çağrılır.

- Vekil seçici yoksa veya nesne türünü işleyemiyorsa, nesnenin [serileştirilebilir](xref:System.SerializableAttribute) özniteliğiyle işaretlenip işaretlenmediğini belirlemekte bir denetim yapılır. Nesne yoksa, bir <xref:System.Runtime.Serialization.SerializationException> oluşturulur.

- Nesne uygun şekilde işaretlenmişse, nesnenin <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulayıp uygulamadığını kontrol edin. Nesne varsa, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> nesne üzerinde çağırılır.
  
- Nesne uygulamamışsa <xref:System.Runtime.Serialization.ISerializable>, varsayılan serileştirme ilkesi kullanılır ve [seri hale](xref:System.NonSerializedAttribute)getirilmemiş olarak işaretlenmemiş tüm alanlar serileştirilir.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkili serileştirme](binary-serialization.md)
- [XML ve SOAP serileştirme](xml-and-soap-serialization.md)
