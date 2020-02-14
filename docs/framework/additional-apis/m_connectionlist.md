---
title: ConnectionGroup. m_ConnectionList alanı
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
ms.openlocfilehash: d53eeb54d212adb011dae138e103ea5b30f7fb99
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215537"
---
# <a name="connectiongroupm_connectionlist-field"></a><span data-ttu-id="6d54d-102">ConnectionGroup. d\_ConnectionList alanı</span><span class="sxs-lookup"><span data-stu-id="6d54d-102">ConnectionGroup.m\_ConnectionList Field</span></span>

<span data-ttu-id="6d54d-103">`ConnectionGroup.m_ConnectionList`, aynı URI 'ye hizmet veren ve süre sonu ve kimlik doğrulama gibi bazı özellikler için aynı değerleri paylaşan bağlantı nesnelerinin bir <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="6d54d-103">`ConnectionGroup.m_ConnectionList` is an <xref:System.Collections.ArrayList> of connection objects that serves the same URI and share the same values for some other properties like expiration and authentication.</span></span>

## <a name="syntax"></a><span data-ttu-id="6d54d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d54d-104">Syntax</span></span>
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> <span data-ttu-id="6d54d-105">`ConnectionGroup.m_ConnectionList` alanı özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6d54d-105">The `ConnectionGroup.m_ConnectionList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="6d54d-106">Microsoft, herhangi bir koşulda bu alanın bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6d54d-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6d54d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d54d-107">Requirements</span></span>

<span data-ttu-id="6d54d-108">**Ad alanı:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="6d54d-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="6d54d-109">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="6d54d-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="6d54d-110">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d54d-110">**.NET Framework versions:** Available since 2.0.</span></span>
