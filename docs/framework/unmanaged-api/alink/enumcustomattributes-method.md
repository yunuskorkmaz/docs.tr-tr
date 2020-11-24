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
ms.openlocfilehash: 445c833d10631341ef7ad579eaff8ddd96be3428
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684856"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="4f1c2-102">EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f1c2-102">EnumCustomAttributes Method</span></span>

<span data-ttu-id="4f1c2-103">Derleme düzeyi özel özniteliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="4f1c2-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f1c2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4f1c2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f1c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f1c2-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="4f1c2-106">Numaralandırıcı tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="4f1c2-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="4f1c2-107">Numaralandırılacak özniteliklerin türü.</span><span class="sxs-lookup"><span data-stu-id="4f1c2-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="4f1c2-108">`mdTokenNill`Tüm öznitelikler için kullanın.</span><span class="sxs-lookup"><span data-stu-id="4f1c2-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="4f1c2-109">Özel öznitelik belirteçleri alır.</span><span class="sxs-lookup"><span data-stu-id="4f1c2-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4f1c2-110">Dizinin boyutunu belirtir `rCustomValues` .</span><span class="sxs-lookup"><span data-stu-id="4f1c2-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="4f1c2-111">İsteğe bağlı olarak belirteç değerleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4f1c2-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f1c2-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4f1c2-112">Return Value</span></span>  

 <span data-ttu-id="4f1c2-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="4f1c2-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f1c2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f1c2-114">Requirements</span></span>  

 <span data-ttu-id="4f1c2-115">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="4f1c2-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1c2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f1c2-116">See also</span></span>

- [<span data-ttu-id="4f1c2-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f1c2-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4f1c2-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f1c2-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4f1c2-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="4f1c2-119">ALink API</span></span>](index.md)
