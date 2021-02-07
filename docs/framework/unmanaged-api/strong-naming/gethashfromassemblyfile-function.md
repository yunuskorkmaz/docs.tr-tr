---
description: 'Daha fazla bilgi edinin: GetHashFromAssemblyFile Işlevi'
title: GetHashFromAssemblyFile İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
ms.openlocfilehash: 79cc6289ebcf33f5a9ea8b4ef139c4b2a67e55e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736784"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="21763-103">GetHashFromAssemblyFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="21763-103">GetHashFromAssemblyFile Function</span></span>

<span data-ttu-id="21763-104">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="21763-104">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="21763-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="21763-105">This function has been deprecated.</span></span> <span data-ttu-id="21763-106">Bunun yerine [ICLRStrongName:: GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="21763-106">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21763-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21763-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21763-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21763-108">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="21763-109">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="21763-109">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="21763-110">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="21763-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="21763-111">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="21763-111">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="21763-112">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="21763-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="21763-113">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="21763-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="21763-114">dışı Bayt cinsinden döndürülen boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="21763-114">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21763-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21763-115">Requirements</span></span>  

 <span data-ttu-id="21763-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21763-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21763-117">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="21763-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="21763-118">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="21763-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="21763-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21763-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21763-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21763-120">See also</span></span>

- [<span data-ttu-id="21763-121">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21763-121">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="21763-122">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21763-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="21763-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21763-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
