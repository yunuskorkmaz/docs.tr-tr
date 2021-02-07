---
description: 'Daha fazla bilgi edinin: GetHashFromFile Işlevi'
title: GetHashFromFile İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: f91bfe8a3988b6aae563b5a852997d6fd3c309d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736602"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="723a4-103">GetHashFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="723a4-103">GetHashFromFile Function</span></span>

<span data-ttu-id="723a4-104">Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="723a4-104">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="723a4-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="723a4-105">This function has been deprecated.</span></span> <span data-ttu-id="723a4-106">Bunun yerine [ICLRStrongName:: GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="723a4-106">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="723a4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="723a4-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="723a4-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="723a4-108">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="723a4-109">'ndaki Karma yapılacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="723a4-109">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="723a4-110">[in, out] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="723a4-110">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="723a4-111">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır.</span><span class="sxs-lookup"><span data-stu-id="723a4-111">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="723a4-112">`piHashAlg`0 olarak ayarlanırsa, CALG_SHA-1 varsayılan algoritma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="723a4-112">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="723a4-113">dışı Oluşturulan karmayı içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="723a4-113">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="723a4-114">'ndaki İşaret eden arabelleğin en büyük boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="723a4-114">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="723a4-115">dışı Döndürülen bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="723a4-115">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="723a4-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="723a4-116">Remarks</span></span>  

 <span data-ttu-id="723a4-117">Bu işlev, [GetHashFromFileW](gethashfromfilew-function.md)ile aynıdır, ancak dosya adı belirtimi UNICODE yerine ANSI olur.</span><span class="sxs-lookup"><span data-stu-id="723a4-117">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="723a4-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="723a4-118">Requirements</span></span>  

 <span data-ttu-id="723a4-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="723a4-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="723a4-120">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="723a4-120">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="723a4-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="723a4-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="723a4-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="723a4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723a4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="723a4-123">See also</span></span>

- [<span data-ttu-id="723a4-124">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="723a4-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="723a4-125">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="723a4-125">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="723a4-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="723a4-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
