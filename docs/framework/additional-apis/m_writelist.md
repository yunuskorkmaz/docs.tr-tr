---
title: Connection. m_WriteList alanı
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
ms.openlocfilehash: 22f939d13cceac4d1c0b39e9e8fe20cdc0ab9387
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214909"
---
# <a name="connectionm_writelist-field"></a><span data-ttu-id="8d725-102">Connection. d\_WriteList alanı</span><span class="sxs-lookup"><span data-stu-id="8d725-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="8d725-103">`Connection.m_WriteList`, HTTP üzerinden gönderilmek üzere sıralanan <xref:System.Net.HttpWebRequest> nesnelerinin bir <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="8d725-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d725-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d725-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="8d725-105">`Connection.m_WriteList` alanı özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d725-105">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="8d725-106">Microsoft, herhangi bir koşulda bu alanın bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8d725-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d725-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d725-107">Requirements</span></span>

<span data-ttu-id="8d725-108">**Ad alanı:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="8d725-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="8d725-109">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="8d725-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="8d725-110">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d725-110">**.NET Framework versions:** Available since 2.0.</span></span>
