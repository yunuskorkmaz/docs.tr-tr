---
title: Serileştirme işlemi adımları
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: ef81ecc7ca177fa9360f53a6b66015412d282065
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084927"
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="a08f8-102">Serileştirme işlemi adımları</span><span class="sxs-lookup"><span data-stu-id="a08f8-102">Steps in the serialization process</span></span>
<span data-ttu-id="a08f8-103">Zaman <xref:System.Runtime.Serialization.Formatter.Serialize*> yöntemi çağrıldığında bir [biçimlendirici](xref:System.Runtime.Serialization.Formatter), nesne seri hale getirme aşağıdaki kuralları dizisini göre devam eder:</span><span class="sxs-lookup"><span data-stu-id="a08f8-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize*> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="a08f8-104">Biçimlendirici bir vekil Seçici olup olmadığını belirlemek için bir onay yapılır.</span><span class="sxs-lookup"><span data-stu-id="a08f8-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="a08f8-105">Biçimlendirici varsa, vekil Seçici belirtilen türe ait nesneleri işleme olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a08f8-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="a08f8-106">Nesne türü Seçici işliyorsa <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> vekil seçici üzerinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a08f8-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="a08f8-107">Hiçbir vekil Seçici yok veya nesne türü işlemez, nesne ile işaretlenmiş olup olmadığını belirlemek için bir onay yapılır [Serializable](xref:System.SerializableAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a08f8-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="a08f8-108">Nesne, yoksa bir <xref:System.Runtime.Serialization.SerializationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a08f8-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="a08f8-109">Nesne uygun şekilde işaretlenmişse, nesne uygulayan olup olmadığını denetleyin. <xref:System.Runtime.Serialization.ISerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a08f8-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="a08f8-110">Nesne varsa, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> nesnesinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a08f8-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> is called on the object.</span></span>
  
- <span data-ttu-id="a08f8-111">Nesne uygulamazsa <xref:System.Runtime.Serialization.ISerializable>, varsayılan seri hale getirme İlkesi kullanılır, tüm alanları serileştirmek işaretlenmemiş olarak [getirilmemiş](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="a08f8-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="a08f8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a08f8-112">See also</span></span>

- [<span data-ttu-id="a08f8-113">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="a08f8-113">Binary Serialization</span></span>](binary-serialization.md)  
- [<span data-ttu-id="a08f8-114">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="a08f8-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
