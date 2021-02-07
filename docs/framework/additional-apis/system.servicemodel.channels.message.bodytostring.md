---
description: 'Daha fazla bilgi edinin: Message. BodyToString yöntemi'
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
ms.openlocfilehash: babcd881d191ff46b98e9999c4ff04166479a68d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699382"
---
# <a name="messagebodytostring-method"></a><span data-ttu-id="81dc2-103">Message. BodyToString yöntemi</span><span class="sxs-lookup"><span data-stu-id="81dc2-103">Message.BodyToString Method</span></span>

<span data-ttu-id="81dc2-104">Yöntemi çağırarak ileti gövdesini bir dizeye dönüştürür <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="81dc2-104">Converts the message body into a string by calling the <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a><span data-ttu-id="81dc2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81dc2-105">Parameters</span></span>

- <span data-ttu-id="81dc2-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="81dc2-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="81dc2-107">İleti gövdesini bir dizeye dönüştürmek için kullanılan yazıcı.</span><span class="sxs-lookup"><span data-stu-id="81dc2-107">The writer that is used to convert the message body to a string.</span></span>

## <a name="remarks"></a><span data-ttu-id="81dc2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81dc2-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="81dc2-109">`Message.BodyToString`Yöntemi iç yöntemidir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="81dc2-109">The `Message.BodyToString` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="81dc2-110">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="81dc2-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="81dc2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81dc2-111">Requirements</span></span>

<span data-ttu-id="81dc2-112">**Ad alanı:**<xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="81dc2-112">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="81dc2-113">**Bütünleştirilmiş kod:** System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="81dc2-113">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="81dc2-114">**.NET Framework sürümleri:** 3,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81dc2-114">**.NET Framework versions:** Available since 3.0.</span></span>
