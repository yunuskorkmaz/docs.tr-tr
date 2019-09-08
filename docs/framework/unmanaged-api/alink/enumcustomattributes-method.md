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
ms.openlocfilehash: 5d8827f46a12bd090fa27e71072d833607d34677
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777353"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="ccaec-102">EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ccaec-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="ccaec-103">Derleme düzeyi özel özniteliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="ccaec-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccaec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccaec-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccaec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ccaec-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="ccaec-106">Numaralandırıcı tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="ccaec-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="ccaec-107">Numaralandırılacak özniteliklerin türü.</span><span class="sxs-lookup"><span data-stu-id="ccaec-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="ccaec-108">Tüm `mdTokenNill` öznitelikler için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccaec-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="ccaec-109">Özel öznitelik belirteçleri alır.</span><span class="sxs-lookup"><span data-stu-id="ccaec-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ccaec-110">`rCustomValues` Dizinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ccaec-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="ccaec-111">İsteğe bağlı olarak belirteç değerleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ccaec-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccaec-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ccaec-112">Return Value</span></span>  
 <span data-ttu-id="ccaec-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="ccaec-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccaec-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ccaec-114">Requirements</span></span>  
 <span data-ttu-id="ccaec-115">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="ccaec-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccaec-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccaec-116">See also</span></span>

- [<span data-ttu-id="ccaec-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ccaec-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ccaec-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ccaec-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ccaec-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="ccaec-119">ALink API</span></span>](index.md)
