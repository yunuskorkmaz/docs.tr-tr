---
title: "Seçmeli seri hale getirme"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f583c0c7f2895b16ac0aea883dd98b4768179127
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="selective-serialization"></a>Seçmeli seri hale getirme
Bir sınıf genellikle seri hale döndürmemelidir alanları içerir. Örneğin, bir sınıf bir iş parçacığı kimliği bir üye değişkeni depolar varsayar. Sınıf serisi, iş parçacığı kimliği depolanan sınıfı zaman sıralandığı managementpack artık çalışmıyor; Bu nedenle bu değer seri hale getirme doesn't make Sense. Üye değişkenleri ile işaretlemeden tarafından seri hale gelen engelleyebilirsiniz [getirilmemiş](xref:System.NonSerializedAttribute) gibi özniteliği.  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

Mümkünse, güvenlik bakımından hassas verileri nonserializable içerebilecek bir nesne olun. Nesne seri hale, Uygula `NonSerialized` özniteliği hassas verileri depolamak için belirli alanları. Seri hale getirme bu alanların yok bıraksanız, depoladıkları veri seri hale getirmek için izne sahip herhangi bir kod sunulan unutmayın. Güvenli serileştirme kodu yazma hakkında daha fazla bilgi için bkz: [güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İkili seri hale getirme](binary-serialization.md)  
 [XML ve SOAP seri hale getirme](xml-and-soap-serialization.md)  
 [Güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md)