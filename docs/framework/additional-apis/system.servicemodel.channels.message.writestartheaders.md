---
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
ms.openlocfilehash: c826e6a3b976e5705e9815586441e8a25b64f76e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214873"
---
# <a name="messagewritestartheaders-method"></a><span data-ttu-id="8311a-102">Message. WriteStartHeaders yöntemi</span><span class="sxs-lookup"><span data-stu-id="8311a-102">Message.WriteStartHeaders Method</span></span>

<span data-ttu-id="8311a-103">Başlangıç üstbilgisini, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> yöntemini çağırarak bir XML dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="8311a-103">Writes the start header into an XML file by calling the <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a><span data-ttu-id="8311a-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8311a-104">Parameters</span></span>

- <span data-ttu-id="8311a-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="8311a-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="8311a-106">Başlangıç üst bilgisini bir XML dosyasına yazmak için kullanılan yazıcı.</span><span class="sxs-lookup"><span data-stu-id="8311a-106">The writer that is used to write the start header into an XML file.</span></span>

## <a name="remarks"></a><span data-ttu-id="8311a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8311a-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="8311a-108">`Message.WriteStartHeaders` yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8311a-108">The `Message.WriteStartHeaders` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="8311a-109">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8311a-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8311a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8311a-110">Requirements</span></span>

<span data-ttu-id="8311a-111">**Ad alanı:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="8311a-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="8311a-112">**Bütünleştirilmiş kod:** System. ServiceModel. dll</span><span class="sxs-lookup"><span data-stu-id="8311a-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="8311a-113">**.NET Framework sürümleri:** 3,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8311a-113">**.NET Framework versions:** Available since 3.0.</span></span>
