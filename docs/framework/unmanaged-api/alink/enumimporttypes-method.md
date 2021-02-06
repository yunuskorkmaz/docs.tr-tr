---
description: 'Daha fazla bilgi edinin: EnumImportTypes yöntemi'
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
ms.openlocfilehash: 39570740f3560f5bfef8ba80b95c0eb2aca41f59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638125"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="ebd25-103">EnumImportTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebd25-103">EnumImportTypes Method</span></span>

<span data-ttu-id="ebd25-104">Her kapsamdaki her türü numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="ebd25-104">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="ebd25-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebd25-105">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="ebd25-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ebd25-106">Parameters</span></span>

`hEnum`\
<span data-ttu-id="ebd25-107">Numaralandırıcı için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="ebd25-107">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="ebd25-108">Alınacak maksimum tür sayısı.</span><span class="sxs-lookup"><span data-stu-id="ebd25-108">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="ebd25-109">Tür belirteçlerini alır, aşılamaz `dwMax` .</span><span class="sxs-lookup"><span data-stu-id="ebd25-109">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="ebd25-110">İçindeki gerçek tür sayısını alır `aTypeDefs` .</span><span class="sxs-lookup"><span data-stu-id="ebd25-110">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="ebd25-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ebd25-111">Return Value</span></span>

<span data-ttu-id="ebd25-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="ebd25-112">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="ebd25-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebd25-113">Requirements</span></span>

<span data-ttu-id="ebd25-114">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="ebd25-114">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="ebd25-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebd25-115">See also</span></span>

- [<span data-ttu-id="ebd25-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebd25-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ebd25-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebd25-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ebd25-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="ebd25-118">ALink API</span></span>](index.md)
