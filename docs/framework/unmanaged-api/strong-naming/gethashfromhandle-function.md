---
description: 'Daha fazla bilgi edinin: GetHashFromHandle Işlevi'
title: GetHashFromHandle İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
ms.openlocfilehash: 5951a5befd9e66b13a3b3033398614fca1f1a9d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736576"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="5820c-103">GetHashFromHandle İşlevi</span><span class="sxs-lookup"><span data-stu-id="5820c-103">GetHashFromHandle Function</span></span>

<span data-ttu-id="5820c-104">Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5820c-104">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="5820c-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5820c-105">This function has been deprecated.</span></span> <span data-ttu-id="5820c-106">Bunun yerine [ICLRStrongName:: GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5820c-106">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5820c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5820c-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5820c-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5820c-108">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="5820c-109">'ndaki Karma hale getirilen dosyanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="5820c-109">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="5820c-110">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="5820c-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="5820c-111">Varsayılan algoritma için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="5820c-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="5820c-112">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="5820c-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="5820c-113">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="5820c-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="5820c-114">dışı Döndürülen bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="5820c-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5820c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5820c-115">Requirements</span></span>  

 <span data-ttu-id="5820c-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5820c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5820c-117">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="5820c-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5820c-118">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5820c-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5820c-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5820c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5820c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5820c-120">See also</span></span>

- [<span data-ttu-id="5820c-121">GetHashFromHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5820c-121">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="5820c-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5820c-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
