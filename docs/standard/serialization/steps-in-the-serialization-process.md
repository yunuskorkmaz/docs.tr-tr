---
title: Serileştirme işlemi adımları
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: b697e8c590d0865b26eaa9f66a333504a5faece2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954056"
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="54350-102">Serileştirme işlemi adımları</span><span class="sxs-lookup"><span data-stu-id="54350-102">Steps in the serialization process</span></span>
<span data-ttu-id="54350-103">Zaman <xref:System.Runtime.Serialization.Formatter.Serialize*> yöntemi çağrıldığında bir [biçimlendirici](xref:System.Runtime.Serialization.Formatter), nesne seri hale getirme aşağıdaki kuralları dizisini göre devam eder:</span><span class="sxs-lookup"><span data-stu-id="54350-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize*> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="54350-104">Biçimlendirici bir vekil Seçici olup olmadığını belirlemek için bir onay yapılır.</span><span class="sxs-lookup"><span data-stu-id="54350-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="54350-105">Biçimlendirici varsa, vekil Seçici belirtilen türe ait nesneleri işleme olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="54350-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="54350-106">Nesne türü Seçici işliyorsa <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> vekil seçici üzerinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="54350-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="54350-107">Hiçbir vekil Seçici yok veya nesne türü işlemez, nesne ile işaretlenmiş olup olmadığını belirlemek için bir onay yapılır [Serializable](xref:System.SerializableAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="54350-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="54350-108">Nesne, yoksa bir <xref:System.Runtime.Serialization.SerializationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="54350-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="54350-109">Nesne uygun şekilde işaretlenmişse, nesne uygulayan olup olmadığını denetleyin. <xref:System.Runtime.Serialization.ISerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="54350-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="54350-110">Nesne varsa, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> nesnesinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="54350-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> is called on the object.</span></span>
  
- <span data-ttu-id="54350-111">Nesne uygulamazsa <xref:System.Runtime.Serialization.ISerializable>, varsayılan seri hale getirme İlkesi kullanılır, tüm alanları serileştirmek işaretlenmemiş olarak [getirilmemiş](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="54350-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="54350-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54350-112">See also</span></span>

- [<span data-ttu-id="54350-113">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="54350-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="54350-114">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="54350-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
