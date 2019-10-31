---
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
ms.openlocfilehash: dc241324f5844610d7b86b7cb9668f84d4525395
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140657"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="a3ad0-102">GetHashFromHandle İşlevi</span><span class="sxs-lookup"><span data-stu-id="a3ad0-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="a3ad0-103">Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a3ad0-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="a3ad0-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="a3ad0-104">This function has been deprecated.</span></span> <span data-ttu-id="a3ad0-105">Bunun yerine [ICLRStrongName:: GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a3ad0-105">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3ad0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3ad0-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3ad0-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3ad0-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="a3ad0-108">'ndaki Karma hale getirilen dosyanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="a3ad0-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a3ad0-109">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="a3ad0-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="a3ad0-110">Varsayılan algoritma için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="a3ad0-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a3ad0-111">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="a3ad0-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a3ad0-112">'ndaki İstenen en büyük boyut `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="a3ad0-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a3ad0-113">dışı Döndürülen `pbHash`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="a3ad0-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3ad0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3ad0-114">Requirements</span></span>  
 <span data-ttu-id="a3ad0-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3ad0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3ad0-116">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="a3ad0-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a3ad0-117">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a3ad0-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a3ad0-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3ad0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ad0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3ad0-119">See also</span></span>

- [<span data-ttu-id="a3ad0-120">GetHashFromHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3ad0-120">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="a3ad0-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3ad0-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
