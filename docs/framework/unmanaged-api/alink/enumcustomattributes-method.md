---
title: "EnumCustomAttributes Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d616babb47ac0282ef56d119ab448a94fd24c7c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="28cd3-102">EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28cd3-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="28cd3-103">Derleme düzeyi özel öznitelikleri alır.</span><span class="sxs-lookup"><span data-stu-id="28cd3-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28cd3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28cd3-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28cd3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28cd3-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="28cd3-106">Numaralandırıcı tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="28cd3-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="28cd3-107">Numaralandırılacak özniteliklerin türü.</span><span class="sxs-lookup"><span data-stu-id="28cd3-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="28cd3-108">Kullanım `mdTokenNill` tüm öznitelikler için.</span><span class="sxs-lookup"><span data-stu-id="28cd3-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="28cd3-109">Özel öznitelikler belirteçlerini alır.</span><span class="sxs-lookup"><span data-stu-id="28cd3-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="28cd3-110">Boyutunu belirtir `rCustomValues` dizi.</span><span class="sxs-lookup"><span data-stu-id="28cd3-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="28cd3-111">İsteğe bağlı olarak belirteç değerlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="28cd3-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28cd3-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="28cd3-112">Return Value</span></span>  
 <span data-ttu-id="28cd3-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="28cd3-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28cd3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28cd3-114">Requirements</span></span>  
 <span data-ttu-id="28cd3-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="28cd3-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28cd3-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28cd3-116">See Also</span></span>  
 [<span data-ttu-id="28cd3-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28cd3-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="28cd3-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28cd3-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="28cd3-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="28cd3-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
