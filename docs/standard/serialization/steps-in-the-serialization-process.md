---
title: "Seri hale getirme işlemi adımları"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c232a76c8a000fcf4ac6c98d3f5c19e50869a362
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="e37f7-102">Seri hale getirme işlemi adımları</span><span class="sxs-lookup"><span data-stu-id="e37f7-102">Steps in the serialization process</span></span>
<span data-ttu-id="e37f7-103">Zaman <xref:System.Runtime.Serialization.Formatter.Serialize*> yöntemi çağrıldığında bir [biçimlendirici](xref:System.Runtime.Serialization.Formatter), nesneyi seri hale getirme aşağıdaki kuralları dizisi göre devam eder:</span><span class="sxs-lookup"><span data-stu-id="e37f7-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize*> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="e37f7-104">Biçimlendirici bir vekil Seçici olup olmadığını belirlemek için bir onay yapılır.</span><span class="sxs-lookup"><span data-stu-id="e37f7-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="e37f7-105">Biçimlendirici varsa, vekil Seçici belirtilen türe ait nesneleri işleme olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e37f7-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="e37f7-106">Seçici nesne türü işliyorsa <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> yedek seçicisinde olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e37f7-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="e37f7-107">Hiçbir yedek Seçici yok veya nesne türündeki işlemiyor, nesne ile işaretlenmiş olup olmadığını belirlemek için bir denetim gerçekleştirilir [Serializable](xref:System.SerializableAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e37f7-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="e37f7-108">Nesne, yoksa bir <xref:System.Runtime.Serialization.SerializationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e37f7-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="e37f7-109">Nesne uygun şekilde işaretlenir nesne uygulayan olup olmadığını kontrol edin <xref:System.Runtime.Serialization.ISerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e37f7-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="e37f7-110">Nesne varsa, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> nesnede olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e37f7-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> is called on the object.</span></span>
  
- <span data-ttu-id="e37f7-111">Nesne uygulamazsa <xref:System.Runtime.Serialization.ISerializable>, varsayılan seri hale getirme ilke kullanılır, tüm alanları serileştirmek işaretlenmemiş olarak [getirilmemiş](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="e37f7-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="e37f7-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e37f7-112">See Also</span></span>  
 [<span data-ttu-id="e37f7-113">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e37f7-113">Binary Serialization</span></span>](binary-serialization.md)  
 [<span data-ttu-id="e37f7-114">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e37f7-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)