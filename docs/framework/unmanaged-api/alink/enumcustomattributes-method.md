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
ms.openlocfilehash: 6a5b3f1e9bf1444feb73949ef7133fbd9ae35134
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446478"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="f3a56-102">EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3a56-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="f3a56-103">Derleme düzeyi özel özniteliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="f3a56-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3a56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3a56-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3a56-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3a56-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="f3a56-106">Numaralandırıcı tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="f3a56-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="f3a56-107">Numaralandırılacak özniteliklerin türü.</span><span class="sxs-lookup"><span data-stu-id="f3a56-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="f3a56-108">Tüm öznitelikler için `mdTokenNill` kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3a56-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="f3a56-109">Özel öznitelik belirteçleri alır.</span><span class="sxs-lookup"><span data-stu-id="f3a56-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f3a56-110">`rCustomValues` dizisinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3a56-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="f3a56-111">İsteğe bağlı olarak belirteç değerleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f3a56-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3a56-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f3a56-112">Return Value</span></span>  
 <span data-ttu-id="f3a56-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3a56-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3a56-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3a56-114">Requirements</span></span>  
 <span data-ttu-id="f3a56-115">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="f3a56-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a56-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3a56-116">See also</span></span>

- [<span data-ttu-id="f3a56-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3a56-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="f3a56-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3a56-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="f3a56-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="f3a56-119">ALink API</span></span>](index.md)
