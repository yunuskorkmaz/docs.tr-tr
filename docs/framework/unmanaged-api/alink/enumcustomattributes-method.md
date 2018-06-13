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
ms.openlocfilehash: 5a3d7d3bb05a878f4d9832cf39a8e8863929c4e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403220"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="3be07-102">EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3be07-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="3be07-103">Derleme düzeyi özel öznitelikleri alır.</span><span class="sxs-lookup"><span data-stu-id="3be07-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3be07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3be07-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3be07-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3be07-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="3be07-106">Numaralandırıcı tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="3be07-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="3be07-107">Numaralandırılacak özniteliklerin türü.</span><span class="sxs-lookup"><span data-stu-id="3be07-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="3be07-108">Kullanım `mdTokenNill` tüm öznitelikler için.</span><span class="sxs-lookup"><span data-stu-id="3be07-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="3be07-109">Özel öznitelikler belirteçlerini alır.</span><span class="sxs-lookup"><span data-stu-id="3be07-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3be07-110">Boyutunu belirtir `rCustomValues` dizi.</span><span class="sxs-lookup"><span data-stu-id="3be07-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="3be07-111">İsteğe bağlı olarak belirteç değerlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3be07-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3be07-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3be07-112">Return Value</span></span>  
 <span data-ttu-id="3be07-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="3be07-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3be07-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3be07-114">Requirements</span></span>  
 <span data-ttu-id="3be07-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="3be07-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be07-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3be07-116">See Also</span></span>  
 [<span data-ttu-id="3be07-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3be07-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="3be07-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3be07-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="3be07-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="3be07-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
