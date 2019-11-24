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
# <a name="enumcustomattributes-method"></a><span data-ttu-id="854b5-102">EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="854b5-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="854b5-103">Retrieves assembly-level custom attributes.</span><span class="sxs-lookup"><span data-stu-id="854b5-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="854b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="854b5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="854b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="854b5-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="854b5-106">Handle of enumerator.</span><span class="sxs-lookup"><span data-stu-id="854b5-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="854b5-107">Type of attributes to be enumerated.</span><span class="sxs-lookup"><span data-stu-id="854b5-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="854b5-108">Use `mdTokenNill` for all attributes.</span><span class="sxs-lookup"><span data-stu-id="854b5-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="854b5-109">Receives custom attributes tokens.</span><span class="sxs-lookup"><span data-stu-id="854b5-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="854b5-110">Specifies size of `rCustomValues` array.</span><span class="sxs-lookup"><span data-stu-id="854b5-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="854b5-111">Optionally receives count of token values.</span><span class="sxs-lookup"><span data-stu-id="854b5-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="854b5-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="854b5-112">Return Value</span></span>  
 <span data-ttu-id="854b5-113">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="854b5-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="854b5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="854b5-114">Requirements</span></span>  
 <span data-ttu-id="854b5-115">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="854b5-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="854b5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="854b5-116">See also</span></span>

- [<span data-ttu-id="854b5-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="854b5-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="854b5-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="854b5-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="854b5-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="854b5-119">ALink API</span></span>](index.md)
