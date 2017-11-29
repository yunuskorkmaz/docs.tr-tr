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
# <a name="selective-serialization"></a><span data-ttu-id="9f6be-102">Seçmeli seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9f6be-102">Selective serialization</span></span>
<span data-ttu-id="9f6be-103">Bir sınıf genellikle seri hale döndürmemelidir alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="9f6be-103">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="9f6be-104">Örneğin, bir sınıf bir iş parçacığı kimliği bir üye değişkeni depolar varsayar.</span><span class="sxs-lookup"><span data-stu-id="9f6be-104">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="9f6be-105">Sınıf serisi, iş parçacığı kimliği depolanan sınıfı zaman sıralandığı managementpack artık çalışmıyor; Bu nedenle bu değer seri hale getirme doesn't make Sense.</span><span class="sxs-lookup"><span data-stu-id="9f6be-105">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="9f6be-106">Üye değişkenleri ile işaretlemeden tarafından seri hale gelen engelleyebilirsiniz [getirilmemiş](xref:System.NonSerializedAttribute) gibi özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9f6be-106">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="9f6be-107">Mümkünse, güvenlik bakımından hassas verileri nonserializable içerebilecek bir nesne olun.</span><span class="sxs-lookup"><span data-stu-id="9f6be-107">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="9f6be-108">Nesne seri hale, Uygula `NonSerialized` özniteliği hassas verileri depolamak için belirli alanları.</span><span class="sxs-lookup"><span data-stu-id="9f6be-108">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="9f6be-109">Seri hale getirme bu alanların yok bıraksanız, depoladıkları veri seri hale getirmek için izne sahip herhangi bir kod sunulan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9f6be-109">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="9f6be-110">Güvenli serileştirme kodu yazma hakkında daha fazla bilgi için bkz: [güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="9f6be-110">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="9f6be-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f6be-111">See also</span></span>  
 [<span data-ttu-id="9f6be-112">İkili seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9f6be-112">Binary Serialization</span></span>](binary-serialization.md)  
 [<span data-ttu-id="9f6be-113">XML ve SOAP seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9f6be-113">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)  
 [<span data-ttu-id="9f6be-114">Güvenlik ve Serileştirme</span><span class="sxs-lookup"><span data-stu-id="9f6be-114">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)