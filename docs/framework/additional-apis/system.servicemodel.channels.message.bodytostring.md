---
title: Message. BodyToString yöntemi (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 9f1f852c0bd82299fd40afe66a5f90cd7c0335cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215499"
---
# <a name="messagebodytostring-method"></a><span data-ttu-id="a0a01-102">Message. BodyToString yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0a01-102">Message.BodyToString Method</span></span>

<span data-ttu-id="a0a01-103"><xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> yöntemini çağırarak ileti gövdesini bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a0a01-103">Converts the message body into a string by calling the <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a><span data-ttu-id="a0a01-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0a01-104">Parameters</span></span>

- <span data-ttu-id="a0a01-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="a0a01-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="a0a01-106">İleti gövdesini bir dizeye dönüştürmek için kullanılan yazıcı.</span><span class="sxs-lookup"><span data-stu-id="a0a01-106">The writer that is used to convert the message body to a string.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0a01-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0a01-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="a0a01-108">`Message.BodyToString` yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0a01-108">The `Message.BodyToString` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a0a01-109">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a0a01-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a0a01-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0a01-110">Requirements</span></span>

<span data-ttu-id="a0a01-111">**Ad alanı:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="a0a01-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="a0a01-112">**Bütünleştirilmiş kod:** System. ServiceModel. dll</span><span class="sxs-lookup"><span data-stu-id="a0a01-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="a0a01-113">**.NET Framework sürümleri:** 3,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a0a01-113">**.NET Framework versions:** Available since 3.0.</span></span>
