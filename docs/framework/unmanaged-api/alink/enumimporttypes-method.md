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
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448739"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="a8624-102">EnumImportTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8624-102">EnumImportTypes Method</span></span>

<span data-ttu-id="a8624-103">Her kapsamdaki her türü numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="a8624-103">Enumerates each type in each scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8624-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8624-104">Syntax</span></span>

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a><span data-ttu-id="a8624-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8624-105">Parameters</span></span>

`hEnum`\
<span data-ttu-id="a8624-106">Numaralandırıcı için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="a8624-106">Handle for enumerator.</span></span>

`dwMax`\
<span data-ttu-id="a8624-107">Alınacak maksimum tür sayısı.</span><span class="sxs-lookup"><span data-stu-id="a8624-107">Maximum number of types to retrieve.</span></span>

`aTypeDefs`\
<span data-ttu-id="a8624-108">Tür belirteçlerini alır, `dwMax`aşmamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a8624-108">Receives type tokens, not to exceed `dwMax`.</span></span>

`pdwCount`\
<span data-ttu-id="a8624-109">`aTypeDefs`gerçek tür sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a8624-109">Receives actual number of type in `aTypeDefs`.</span></span>

## <a name="return-value"></a><span data-ttu-id="a8624-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a8624-110">Return Value</span></span>

<span data-ttu-id="a8624-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="a8624-111">Returns S_OK if the method succeeds.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8624-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8624-112">Requirements</span></span>

<span data-ttu-id="a8624-113">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="a8624-113">Requires alink.h</span></span>

## <a name="see-also"></a><span data-ttu-id="a8624-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8624-114">See also</span></span>

- [<span data-ttu-id="a8624-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8624-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a8624-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8624-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a8624-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="a8624-117">ALink API</span></span>](index.md)
