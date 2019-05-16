---
title: EnumImportTypes Yöntemi
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cd154ac90418dd0f6f476151686ff670c01c98c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632242"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="94906-102">EnumImportTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94906-102">EnumImportTypes Method</span></span>

<span data-ttu-id="94906-103">Her kapsamda her türünü numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="94906-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="94906-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94906-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="94906-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94906-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="94906-106">Numaralandırıcı için işler.</span><span class="sxs-lookup"><span data-stu-id="94906-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="94906-107">Alınacak türleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="94906-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="94906-108">Aşmayan türü belirteçlerini alır `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="94906-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="94906-109">Türünde gerçek sayısını alır `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="94906-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="94906-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="94906-110">Return Value</span></span>

<span data-ttu-id="94906-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="94906-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="94906-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94906-112">Requirements</span></span>

<span data-ttu-id="94906-113">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="94906-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="94906-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94906-114">See also</span></span>

- [<span data-ttu-id="94906-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94906-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="94906-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94906-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="94906-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="94906-117">ALink API</span></span>](index.md)
