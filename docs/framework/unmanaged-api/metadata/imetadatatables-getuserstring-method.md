---
description: ': IMetaDataTables:: GetUserString metodu hakkında daha fazla bilgi edinin'
title: IMetaDataTables::GetUserString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
ms.openlocfilehash: 0909bfb2dbf4e6a34b746da7397a82845c2129c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687694"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="41bd5-103">IMetaDataTables::GetUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="41bd5-103">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="41bd5-104">Geçerli kapsamdaki dize sütununda belirtilen dizinde sabit kodlanmış dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="41bd5-104">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="41bd5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41bd5-105">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="41bd5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41bd5-106">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="41bd5-107">'ndaki Sabit kodlanmış dizenin alınacağı dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="41bd5-107">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="41bd5-108">dışı Boyutu için bir işaretçi `ppData` .</span><span class="sxs-lookup"><span data-stu-id="41bd5-108">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="41bd5-109">dışı Döndürülen dizeye bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="41bd5-109">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="41bd5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41bd5-110">Requirements</span></span>

<span data-ttu-id="41bd5-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41bd5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="41bd5-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="41bd5-112">**Header:** Cor.h</span></span>

<span data-ttu-id="41bd5-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="41bd5-113">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="41bd5-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41bd5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="41bd5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41bd5-115">See also</span></span>

- [<span data-ttu-id="41bd5-116">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41bd5-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="41bd5-117">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41bd5-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
