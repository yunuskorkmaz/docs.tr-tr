---
description: ': IAssemblyCacheItem:: CreateStream yöntemi hakkında daha fazla bilgi edinin'
title: IAssemblyCacheItem::CreateStream Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
ms.openlocfilehash: 89592d8fe1a7f43a7da20dd10883881c3339f088
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760881"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="ebfa3-103">IAssemblyCacheItem::CreateStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebfa3-103">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="ebfa3-104">Belirtilen ad ve biçimle bir akış oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ebfa3-104">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="ebfa3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebfa3-105">Syntax</span></span>

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a><span data-ttu-id="ebfa3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ebfa3-106">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="ebfa3-107">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="ebfa3-107">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="ebfa3-108">'ndaki Oluşturulacak akışın adı.</span><span class="sxs-lookup"><span data-stu-id="ebfa3-108">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="ebfa3-109">'ndaki Akışa eklenecek dosyanın biçimi.</span><span class="sxs-lookup"><span data-stu-id="ebfa3-109">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="ebfa3-110">'ndaki Fusion. IDL içinde tanımlı formata özgü bayraklar.</span><span class="sxs-lookup"><span data-stu-id="ebfa3-110">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="ebfa3-111">dışı Döndürülen [IStream](/windows/desktop/api/objidl/nn-objidl-istream) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ebfa3-111">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="ebfa3-112">[ın, isteğe bağlı] Tarafından başvurulan akışın en büyük boyutu `ppIStream` .</span><span class="sxs-lookup"><span data-stu-id="ebfa3-112">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="ebfa3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebfa3-113">Requirements</span></span>

<span data-ttu-id="ebfa3-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebfa3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ebfa3-115">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ebfa3-115">**Header:** Fusion.h</span></span>

<span data-ttu-id="ebfa3-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebfa3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ebfa3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebfa3-117">See also</span></span>

- [<span data-ttu-id="ebfa3-118">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebfa3-118">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
