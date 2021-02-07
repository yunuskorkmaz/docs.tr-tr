---
description: 'Daha fazla bilgi edinin: Message. WriteStartHeaders yöntemi'
title: Message. WriteStartHeaders yöntemi (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 20cadf5f1eecf6d8e02c5dc4597889abaef4ec36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699369"
---
# <a name="messagewritestartheaders-method"></a><span data-ttu-id="c7909-103">Message. WriteStartHeaders yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7909-103">Message.WriteStartHeaders Method</span></span>

<span data-ttu-id="c7909-104">Yöntemini çağırarak başlangıç üstbilgisini bir XML dosyasına yazar <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c7909-104">Writes the start header into an XML file by calling the <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a><span data-ttu-id="c7909-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7909-105">Parameters</span></span>

- <span data-ttu-id="c7909-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="c7909-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="c7909-107">Başlangıç üst bilgisini bir XML dosyasına yazmak için kullanılan yazıcı.</span><span class="sxs-lookup"><span data-stu-id="c7909-107">The writer that is used to write the start header into an XML file.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7909-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7909-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="c7909-109">`Message.WriteStartHeaders`Yöntemi iç yöntemidir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="c7909-109">The `Message.WriteStartHeaders` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="c7909-110">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c7909-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7909-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7909-111">Requirements</span></span>

<span data-ttu-id="c7909-112">**Ad alanı:**<xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="c7909-112">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="c7909-113">**Bütünleştirilmiş kod:** System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="c7909-113">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="c7909-114">**.NET Framework sürümleri:** 3,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7909-114">**.NET Framework versions:** Available since 3.0.</span></span>
