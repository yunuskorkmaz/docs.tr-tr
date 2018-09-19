---
title: Seçmeli serileştirme
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: 74e21045ec70faf6ee82200a15362d51edf61433
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003535"
---
# <a name="selective-serialization"></a>Seçmeli serileştirme
Bir sınıf seri hale olmamalıdır alanlar genellikle içerir. Örneğin, bir sınıf bir iş parçacığı kimliği bir üye değişkeni depolar varsayar. Sınıf seri olduğunda, iş parçacığı kimliği depolanan sınıfı zaman seri duruma artık çalışmıyor; Bu nedenle bu değeri serileştirmek mantıklı değildir. Üye değişkenleri ile işaretleyerek serileştirilen öğesinden engelleyebilirsiniz [getirilmemiş](xref:System.NonSerializedAttribute) özniteliğini aşağıdaki gibi.  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

Mümkünse, güvenlik bakımından hassas verileri nonserializable içerebilecek bir nesne olun. Nesnenin serileştirildiği, Uygula `NonSerialized` öznitelik hassas verileri depolamak için belirli alanlar. Serileştirme bu alanlar dışarıda tutmamanızı, bunlar depolamak verileri seri hale getirmek için izni olan herhangi bir kod sunulan dikkat edin. Güvenli serileştirme kod yazma hakkında daha fazla bilgi için bkz. [güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkili Serileştirme](binary-serialization.md)  
- [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)  
- [Güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md)
