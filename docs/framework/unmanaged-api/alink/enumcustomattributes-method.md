---
description: 'Daha fazla bilgi edinin: EnumCustomAttributes yöntemi'
title: EnumCustomAttributes Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: d5b537462745914903f0cdb1e9f4436f2c27a68d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638150"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="fc58b-103">EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc58b-103">EnumCustomAttributes Method</span></span>

<span data-ttu-id="fc58b-104">Derleme düzeyi özel özniteliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="fc58b-104">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc58b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc58b-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc58b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc58b-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="fc58b-107">Numaralandırıcı tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="fc58b-107">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="fc58b-108">Numaralandırılacak özniteliklerin türü.</span><span class="sxs-lookup"><span data-stu-id="fc58b-108">Type of attributes to be enumerated.</span></span> <span data-ttu-id="fc58b-109">`mdTokenNill`Tüm öznitelikler için kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc58b-109">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="fc58b-110">Özel öznitelik belirteçleri alır.</span><span class="sxs-lookup"><span data-stu-id="fc58b-110">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fc58b-111">Dizinin boyutunu belirtir `rCustomValues` .</span><span class="sxs-lookup"><span data-stu-id="fc58b-111">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="fc58b-112">İsteğe bağlı olarak belirteç değerleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="fc58b-112">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc58b-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fc58b-113">Return Value</span></span>  

 <span data-ttu-id="fc58b-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc58b-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc58b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc58b-115">Requirements</span></span>  

 <span data-ttu-id="fc58b-116">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="fc58b-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc58b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc58b-117">See also</span></span>

- [<span data-ttu-id="fc58b-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc58b-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="fc58b-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc58b-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="fc58b-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="fc58b-120">ALink API</span></span>](index.md)
