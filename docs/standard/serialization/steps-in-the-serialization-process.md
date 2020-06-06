---
title: Serileştirme işlemi adımları
description: Serileştirme işlemi, bir biçimlendirici üzerinde bir biçimlendirici yöntemi çağrıldığında başlar. Bu makalede olayların sırası açıklanır.
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: 1f749b9102182e78bc3fda436cf386a9f5759d5a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "83379094"
---
# <a name="steps-in-the-serialization-process"></a>Serileştirme işlemi adımları
<xref:System.Runtime.Serialization.Formatter.Serialize%2A>Yöntem bir [biçimlendirici](xref:System.Runtime.Serialization.Formatter)üzerinde çağrıldığında, nesne serileştirme aşağıdaki kural dizisine göre devam eder:

- Biçimlendirici bir vekil Seçici olup olmadığını belirlemek için bir onay yapılır. Biçimlendirici varsa, vekil Seçici belirtilen türe ait nesneleri işleme olup olmadığını denetleyin. Seçici, nesne türünü işlediğinde, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> vekil seçicide çağrılır.

- Vekil seçici yoksa veya nesne türünü işleyemiyorsa, nesnenin [serileştirilebilir](xref:System.SerializableAttribute) özniteliğiyle işaretlenip işaretlenmediğini belirlemekte bir denetim yapılır. Nesne yoksa, bir oluşturulur <xref:System.Runtime.Serialization.SerializationException> .

- Nesne uygun şekilde işaretlenmişse, nesnenin arabirimi uygulayıp uygulamadığını kontrol edin <xref:System.Runtime.Serialization.ISerializable> . Nesne varsa, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> nesne üzerinde çağırılır.
  
- Nesne uygulamamışsa <xref:System.Runtime.Serialization.ISerializable> , varsayılan serileştirme ilkesi kullanılır ve [seri hale](xref:System.NonSerializedAttribute)getirilmemiş olarak işaretlenmemiş tüm alanlar serileştirilir.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkili serileştirme](binary-serialization.md)
- [XML ve SOAP serileştirme](xml-and-soap-serialization.md)
