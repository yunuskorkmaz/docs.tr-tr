---
title: ServicePointManager. CloseConnectionGroups yöntemi (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: aae9a389ae35e249d43c9dc830a68ec32cf4afef
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990364"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a><span data-ttu-id="cb61f-102">ServicePointManager. CloseConnectionGroups yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb61f-102">ServicePointManager.CloseConnectionGroups method</span></span>

<span data-ttu-id="cb61f-103">Tüm hizmet noktalarında dolaşır ve belirtilen ada sahip bağlantı gruplarını kapatır.</span><span class="sxs-lookup"><span data-stu-id="cb61f-103">Iterates through all service points and closes connection groups that have the specified name.</span></span>

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> <span data-ttu-id="cb61f-104">Bu yöntem dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb61f-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="cb61f-105">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cb61f-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="cb61f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb61f-106">Parameters</span></span>

<span data-ttu-id="cb61f-107">`connectionGroupName` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="cb61f-107">`connectionGroupName` <xref:System.String></span></span>

<span data-ttu-id="cb61f-108">Kapatılacak bağlantı grubunun adı.</span><span class="sxs-lookup"><span data-stu-id="cb61f-108">The name of the connection group to close.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb61f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb61f-109">Requirements</span></span>

<span data-ttu-id="cb61f-110">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="cb61f-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="cb61f-111">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="cb61f-111">**Assembly:** System (in System.dll)</span></span>
