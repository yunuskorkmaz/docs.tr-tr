---
title: Seçmeli serileştirme
description: Bu makalede, alanları serileştirilmiş olmayan özniteliğiyle işaretlemek, bu da alanın serileştirilmesi önlenir.
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: 3c99a3be92beb992ff20188b02ff33a92f196baf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722186"
---
# <a name="selective-serialization"></a>Seçmeli serileştirme

Bir sınıf genellikle serileştirilmemelidir alanları içerir. Örneğin, bir sınıf bir iş parçacığı kimliği bir üye değişkeni depolar varsayar. Sınıf seri durumdan çıkarıldığında, sınıf seri hale getirilme sırasında KIMLIĞI depolanan iş parçacığı artık çalışmıyor olabilir; Bu nedenle bu değerin serileştirilmesi anlamlı değildir. Aşağıdaki gibi, [seri olmayan](xref:System.NonSerializedAttribute) özniteliğiyle işaretleyerek üye değişkenlerinin serileştirilmesine engel olabilirsiniz.  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

Mümkünse, güvenlik bakımından hassas verileri nonserializable içerebilecek bir nesne olun. Nesnenin serileştirilmesi gerekiyorsa, `NonSerialized` Bu özniteliği hassas verileri depolayan belirli alanlara uygulayın. Bu alanları Serileştirmeden dışlamak istemiyorsanız, depotıkları verilerin serileştirme izni olan herhangi bir koda açık olduğunu unutmayın. Güvenli serileştirme kodu yazma hakkında daha fazla bilgi için bkz. [güvenlik ve serileştirme](../../framework/misc/security-and-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkili serileştirme](binary-serialization.md)
- [XML ve SOAP serileştirme](xml-and-soap-serialization.md)
- [Güvenlik ve serileştirme](../../framework/misc/security-and-serialization.md)
