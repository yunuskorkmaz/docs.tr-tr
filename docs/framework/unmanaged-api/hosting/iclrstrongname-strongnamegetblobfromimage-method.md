---
description: ': ICLRStrongName:: StrongNameGetBlobFromImage yöntemi hakkında daha fazla bilgi edinin'
title: ICLRStrongName::StrongNameGetBlobFromImage Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
ms.openlocfilehash: 32f04e21f1f08f3872ccdd27a64f39ea29d7e060
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799622"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="9aa55-103">ICLRStrongName::StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9aa55-103">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>

<span data-ttu-id="9aa55-104">Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="9aa55-104">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aa55-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9aa55-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9aa55-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9aa55-106">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="9aa55-107">'ndaki Eşlenen derleme bildiriminin bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="9aa55-107">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="9aa55-108">'ndaki İçindeki görüntünün bayt cinsinden boyutu `pbBase` .</span><span class="sxs-lookup"><span data-stu-id="9aa55-108">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="9aa55-109">'ndaki Görüntünün ikili gösterimini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="9aa55-109">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="9aa55-110">[in, out] İstenen en büyük boyut (bayt) `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="9aa55-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="9aa55-111">Dönüş sonrasında, bayt cinsinden gerçek boyut `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="9aa55-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9aa55-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9aa55-112">Return Value</span></span>  

 <span data-ttu-id="9aa55-113">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="9aa55-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aa55-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9aa55-114">Requirements</span></span>  

 <span data-ttu-id="9aa55-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aa55-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aa55-116">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9aa55-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9aa55-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9aa55-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9aa55-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aa55-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa55-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9aa55-119">See also</span></span>

- [<span data-ttu-id="9aa55-120">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9aa55-120">StrongNameGetBlob Method</span></span>](iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="9aa55-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9aa55-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
