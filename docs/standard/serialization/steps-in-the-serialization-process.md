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
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="72a6a-104">Serileştirme işlemi adımları</span><span class="sxs-lookup"><span data-stu-id="72a6a-104">Steps in the serialization process</span></span>
<span data-ttu-id="72a6a-105"><xref:System.Runtime.Serialization.Formatter.Serialize%2A>Yöntem bir [biçimlendirici](xref:System.Runtime.Serialization.Formatter)üzerinde çağrıldığında, nesne serileştirme aşağıdaki kural dizisine göre devam eder:</span><span class="sxs-lookup"><span data-stu-id="72a6a-105">When the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="72a6a-106">Biçimlendirici bir vekil Seçici olup olmadığını belirlemek için bir onay yapılır.</span><span class="sxs-lookup"><span data-stu-id="72a6a-106">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="72a6a-107">Biçimlendirici varsa, vekil Seçici belirtilen türe ait nesneleri işleme olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="72a6a-107">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="72a6a-108">Seçici, nesne türünü işlediğinde, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> vekil seçicide çağrılır.</span><span class="sxs-lookup"><span data-stu-id="72a6a-108">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="72a6a-109">Vekil seçici yoksa veya nesne türünü işleyemiyorsa, nesnenin [serileştirilebilir](xref:System.SerializableAttribute) özniteliğiyle işaretlenip işaretlenmediğini belirlemekte bir denetim yapılır.</span><span class="sxs-lookup"><span data-stu-id="72a6a-109">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="72a6a-110">Nesne yoksa, bir oluşturulur <xref:System.Runtime.Serialization.SerializationException> .</span><span class="sxs-lookup"><span data-stu-id="72a6a-110">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="72a6a-111">Nesne uygun şekilde işaretlenmişse, nesnenin arabirimi uygulayıp uygulamadığını kontrol edin <xref:System.Runtime.Serialization.ISerializable> .</span><span class="sxs-lookup"><span data-stu-id="72a6a-111">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="72a6a-112">Nesne varsa, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> nesne üzerinde çağırılır.</span><span class="sxs-lookup"><span data-stu-id="72a6a-112">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> is called on the object.</span></span>
  
- <span data-ttu-id="72a6a-113">Nesne uygulamamışsa <xref:System.Runtime.Serialization.ISerializable> , varsayılan serileştirme ilkesi kullanılır ve [seri hale](xref:System.NonSerializedAttribute)getirilmemiş olarak işaretlenmemiş tüm alanlar serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="72a6a-113">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="72a6a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72a6a-114">See also</span></span>

- [<span data-ttu-id="72a6a-115">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="72a6a-115">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="72a6a-116">XML ve SOAP serileştirme</span><span class="sxs-lookup"><span data-stu-id="72a6a-116">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
