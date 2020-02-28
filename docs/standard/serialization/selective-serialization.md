---
title: Seçmeli serileştirme
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: cc5d7964d5f3268f08721593fefc07e3eff853ca
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159604"
---
# <a name="selective-serialization"></a><span data-ttu-id="364ca-102">Seçmeli serileştirme</span><span class="sxs-lookup"><span data-stu-id="364ca-102">Selective serialization</span></span>
<span data-ttu-id="364ca-103">Bir sınıf genellikle serileştirilmemelidir alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="364ca-103">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="364ca-104">Örneğin, bir sınıf bir iş parçacığı kimliği bir üye değişkeni depolar varsayar.</span><span class="sxs-lookup"><span data-stu-id="364ca-104">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="364ca-105">Sınıf seri durumdan çıkarıldığında, sınıf seri hale getirilme sırasında KIMLIĞI depolanan iş parçacığı artık çalışmıyor olabilir; Bu nedenle bu değerin serileştirilmesi anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="364ca-105">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="364ca-106">Aşağıdaki gibi, [seri olmayan](xref:System.NonSerializedAttribute) özniteliğiyle işaretleyerek üye değişkenlerinin serileştirilmesine engel olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="364ca-106">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="364ca-107">Mümkünse, güvenlik bakımından hassas verileri nonserializable içerebilecek bir nesne olun.</span><span class="sxs-lookup"><span data-stu-id="364ca-107">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="364ca-108">Nesnenin serileştirilmesi gerekiyorsa, hassas verileri depolayan belirli alanlara `NonSerialized` özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="364ca-108">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="364ca-109">Bu alanları Serileştirmeden dışlamak istemiyorsanız, depotıkları verilerin serileştirme izni olan herhangi bir koda açık olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="364ca-109">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="364ca-110">Güvenli serileştirme kodu yazma hakkında daha fazla bilgi için bkz. [güvenlik ve serileştirme](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="364ca-110">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="364ca-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="364ca-111">See also</span></span>

- [<span data-ttu-id="364ca-112">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="364ca-112">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="364ca-113">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="364ca-113">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="364ca-114">Güvenlik ve serileştirme</span><span class="sxs-lookup"><span data-stu-id="364ca-114">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
