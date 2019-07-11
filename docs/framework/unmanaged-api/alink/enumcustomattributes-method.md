---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09ccf731f0494b6eda49f6a15d04970a723c473b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742061"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="35702-102">EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35702-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="35702-103">Derleme düzeyi özel öznitelikleri alır.</span><span class="sxs-lookup"><span data-stu-id="35702-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35702-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35702-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="35702-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35702-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="35702-106">Numaralandırıcı tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="35702-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="35702-107">Numaralandırılacak özniteliklerin türü.</span><span class="sxs-lookup"><span data-stu-id="35702-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="35702-108">Kullanım `mdTokenNill` tüm öznitelikler için.</span><span class="sxs-lookup"><span data-stu-id="35702-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="35702-109">Özel öznitelikler belirteçlerini alır.</span><span class="sxs-lookup"><span data-stu-id="35702-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="35702-110">Boyutunu belirtir `rCustomValues` dizisi.</span><span class="sxs-lookup"><span data-stu-id="35702-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="35702-111">İsteğe bağlı olarak belirteç değerlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="35702-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35702-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="35702-112">Return Value</span></span>  
 <span data-ttu-id="35702-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="35702-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35702-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35702-114">Requirements</span></span>  
 <span data-ttu-id="35702-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="35702-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35702-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35702-116">See also</span></span>

- [<span data-ttu-id="35702-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35702-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="35702-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35702-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="35702-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="35702-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
