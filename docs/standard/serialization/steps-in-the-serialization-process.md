---
title: Serileştirme işlemindeki adımlar
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
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="5766b-102">Serileştirme işlemindeki adımlar</span><span class="sxs-lookup"><span data-stu-id="5766b-102">Steps in the serialization process</span></span>
<span data-ttu-id="5766b-103"><xref:System.Runtime.Serialization.Formatter.Serialize%2A> yöntemi bir [biçimlendirici](xref:System.Runtime.Serialization.Formatter)üzerinde çağrıldığında, nesne serileştirme aşağıdaki kural dizisine göre devam eder:</span><span class="sxs-lookup"><span data-stu-id="5766b-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="5766b-104">Biçimlendirici bir vekil Seçici olup olmadığını belirlemek için bir onay yapılır.</span><span class="sxs-lookup"><span data-stu-id="5766b-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="5766b-105">Biçimlendirici varsa, vekil Seçici belirtilen türe ait nesneleri işleme olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5766b-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="5766b-106">Seçici, nesne türünü işlediğinde, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> vekil seçicide çağırılır.</span><span class="sxs-lookup"><span data-stu-id="5766b-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="5766b-107">Vekil seçici yoksa veya nesne türünü işleyemiyorsa, nesnenin [serileştirilebilir](xref:System.SerializableAttribute) özniteliğiyle işaretlenip işaretlenmediğini belirlemekte bir denetim yapılır.</span><span class="sxs-lookup"><span data-stu-id="5766b-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="5766b-108">Nesne yoksa, bir <xref:System.Runtime.Serialization.SerializationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5766b-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="5766b-109">Nesne uygun şekilde işaretlenmişse, nesnenin <xref:System.Runtime.Serialization.ISerializable> arabirimini uygulayıp uygulamadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="5766b-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="5766b-110">Nesne varsa, nesne üzerinde <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> çağırılır.</span><span class="sxs-lookup"><span data-stu-id="5766b-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> is called on the object.</span></span>
  
- <span data-ttu-id="5766b-111">Nesne <xref:System.Runtime.Serialization.ISerializable>uygulamamışsa, varsayılan serileştirme ilkesi kullanılır ve [seri hale](xref:System.NonSerializedAttribute)getirilmemiş olarak işaretlenmemiş tüm alanlar serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="5766b-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="5766b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5766b-112">See also</span></span>

- [<span data-ttu-id="5766b-113">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="5766b-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="5766b-114">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="5766b-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
