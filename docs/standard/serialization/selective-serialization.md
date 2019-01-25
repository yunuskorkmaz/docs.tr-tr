---
title: Seçmeli serileştirme
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: af608031a661037b89c9783ac2451a6b536f9cd4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731393"
---
# <a name="selective-serialization"></a><span data-ttu-id="2f162-102">Seçmeli serileştirme</span><span class="sxs-lookup"><span data-stu-id="2f162-102">Selective serialization</span></span>
<span data-ttu-id="2f162-103">Bir sınıf seri hale olmamalıdır alanlar genellikle içerir.</span><span class="sxs-lookup"><span data-stu-id="2f162-103">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="2f162-104">Örneğin, bir sınıf bir iş parçacığı kimliği bir üye değişkeni depolar varsayar.</span><span class="sxs-lookup"><span data-stu-id="2f162-104">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="2f162-105">Sınıf seri olduğunda, iş parçacığı kimliği depolanan sınıfı zaman seri duruma artık çalışmıyor; Bu nedenle bu değeri serileştirmek mantıklı değildir.</span><span class="sxs-lookup"><span data-stu-id="2f162-105">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="2f162-106">Üye değişkenleri ile işaretleyerek serileştirilen öğesinden engelleyebilirsiniz [getirilmemiş](xref:System.NonSerializedAttribute) özniteliğini aşağıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="2f162-106">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="2f162-107">Mümkünse, güvenlik bakımından hassas verileri nonserializable içerebilecek bir nesne olun.</span><span class="sxs-lookup"><span data-stu-id="2f162-107">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="2f162-108">Nesnenin serileştirildiği, Uygula `NonSerialized` öznitelik hassas verileri depolamak için belirli alanlar.</span><span class="sxs-lookup"><span data-stu-id="2f162-108">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="2f162-109">Serileştirme bu alanlar dışarıda tutmamanızı, bunlar depolamak verileri seri hale getirmek için izni olan herhangi bir kod sunulan dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2f162-109">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="2f162-110">Güvenli serileştirme kod yazma hakkında daha fazla bilgi için bkz. [güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="2f162-110">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="2f162-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f162-111">See also</span></span>

- [<span data-ttu-id="2f162-112">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2f162-112">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="2f162-113">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2f162-113">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="2f162-114">Güvenlik ve Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2f162-114">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
