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
ms.openlocfilehash: c7203c4ea13c65f8d88c55de96988d3b1d9e9611
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379170"
---
# <a name="selective-serialization"></a><span data-ttu-id="418e0-103">Seçmeli serileştirme</span><span class="sxs-lookup"><span data-stu-id="418e0-103">Selective serialization</span></span>
<span data-ttu-id="418e0-104">Bir sınıf genellikle serileştirilmemelidir alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="418e0-104">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="418e0-105">Örneğin, bir sınıf bir iş parçacığı kimliği bir üye değişkeni depolar varsayar.</span><span class="sxs-lookup"><span data-stu-id="418e0-105">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="418e0-106">Sınıf seri durumdan çıkarıldığında, sınıf seri hale getirilme sırasında KIMLIĞI depolanan iş parçacığı artık çalışmıyor olabilir; Bu nedenle bu değerin serileştirilmesi anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="418e0-106">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="418e0-107">Aşağıdaki gibi, [seri olmayan](xref:System.NonSerializedAttribute) özniteliğiyle işaretleyerek üye değişkenlerinin serileştirilmesine engel olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="418e0-107">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="418e0-108">Mümkünse, güvenlik bakımından hassas verileri nonserializable içerebilecek bir nesne olun.</span><span class="sxs-lookup"><span data-stu-id="418e0-108">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="418e0-109">Nesnenin serileştirilmesi gerekiyorsa, `NonSerialized` Bu özniteliği hassas verileri depolayan belirli alanlara uygulayın.</span><span class="sxs-lookup"><span data-stu-id="418e0-109">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="418e0-110">Bu alanları Serileştirmeden dışlamak istemiyorsanız, depotıkları verilerin serileştirme izni olan herhangi bir koda açık olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="418e0-110">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="418e0-111">Güvenli serileştirme kodu yazma hakkında daha fazla bilgi için bkz. [güvenlik ve serileştirme](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="418e0-111">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="418e0-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="418e0-112">See also</span></span>

- [<span data-ttu-id="418e0-113">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="418e0-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="418e0-114">XML ve SOAP serileştirme</span><span class="sxs-lookup"><span data-stu-id="418e0-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="418e0-115">Güvenlik ve Serileştirme</span><span class="sxs-lookup"><span data-stu-id="418e0-115">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
