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
ms.openlocfilehash: 74113979f0ebe77319ae308c2a669e91d8cb4209
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84278421"
---
# <a name="selective-serialization"></a><span data-ttu-id="e70cd-103">Seçmeli serileştirme</span><span class="sxs-lookup"><span data-stu-id="e70cd-103">Selective serialization</span></span>
<span data-ttu-id="e70cd-104">Bir sınıf genellikle serileştirilmemelidir alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="e70cd-104">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="e70cd-105">Örneğin, bir sınıf bir iş parçacığı kimliği bir üye değişkeni depolar varsayar.</span><span class="sxs-lookup"><span data-stu-id="e70cd-105">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="e70cd-106">Sınıf seri durumdan çıkarıldığında, sınıf seri hale getirilme sırasında KIMLIĞI depolanan iş parçacığı artık çalışmıyor olabilir; Bu nedenle bu değerin serileştirilmesi anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="e70cd-106">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="e70cd-107">Aşağıdaki gibi, [seri olmayan](xref:System.NonSerializedAttribute) özniteliğiyle işaretleyerek üye değişkenlerinin serileştirilmesine engel olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e70cd-107">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="e70cd-108">Mümkünse, güvenlik bakımından hassas verileri nonserializable içerebilecek bir nesne olun.</span><span class="sxs-lookup"><span data-stu-id="e70cd-108">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="e70cd-109">Nesnenin serileştirilmesi gerekiyorsa, `NonSerialized` Bu özniteliği hassas verileri depolayan belirli alanlara uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e70cd-109">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="e70cd-110">Bu alanları Serileştirmeden dışlamak istemiyorsanız, depotıkları verilerin serileştirme izni olan herhangi bir koda açık olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e70cd-110">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="e70cd-111">Güvenli serileştirme kodu yazma hakkında daha fazla bilgi için bkz. [güvenlik ve serileştirme](../../framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="e70cd-111">For more information about writing secure serialization code, see [Security and Serialization](../../framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="e70cd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e70cd-112">See also</span></span>

- [<span data-ttu-id="e70cd-113">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="e70cd-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="e70cd-114">XML ve SOAP serileştirme</span><span class="sxs-lookup"><span data-stu-id="e70cd-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="e70cd-115">Güvenlik ve Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e70cd-115">Security and Serialization</span></span>](../../framework/misc/security-and-serialization.md)
