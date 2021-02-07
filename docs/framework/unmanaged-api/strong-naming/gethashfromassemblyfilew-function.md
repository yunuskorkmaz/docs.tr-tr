---
description: 'Daha fazla bilgi edinin: GetHashFromAssemblyFileW Işlevi'
title: GetHashFromAssemblyFileW İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
ms.openlocfilehash: 7f44106f12a2d21ea67acb874b577c5b303632b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736680"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="52dcc-103">GetHashFromAssemblyFileW İşlevi</span><span class="sxs-lookup"><span data-stu-id="52dcc-103">GetHashFromAssemblyFileW Function</span></span>

<span data-ttu-id="52dcc-104">Belirtilen karma algoritmasını kullanarak belirtilen derleme dosyasının karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="52dcc-104">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="52dcc-105">Derleme dosyasının yolu Unicode dize olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="52dcc-105">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="52dcc-106">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="52dcc-106">This function has been deprecated.</span></span> <span data-ttu-id="52dcc-107">Bunun yerine [ICLRStrongName:: GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="52dcc-107">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52dcc-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52dcc-108">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52dcc-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52dcc-109">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="52dcc-110">'ndaki Karma hale getirilen dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="52dcc-110">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="52dcc-111">Bu parametre bir Unicode dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52dcc-111">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="52dcc-112">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="52dcc-112">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="52dcc-113">Varsayılan karma algoritması için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="52dcc-113">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="52dcc-114">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="52dcc-114">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="52dcc-115">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="52dcc-115">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="52dcc-116">dışı Bayt cinsinden döndürülen boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="52dcc-116">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52dcc-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52dcc-117">Requirements</span></span>  

 <span data-ttu-id="52dcc-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52dcc-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52dcc-119">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="52dcc-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="52dcc-120">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="52dcc-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52dcc-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52dcc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52dcc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52dcc-122">See also</span></span>

- [<span data-ttu-id="52dcc-123">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52dcc-123">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="52dcc-124">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52dcc-124">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="52dcc-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52dcc-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
