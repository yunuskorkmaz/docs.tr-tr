---
title: IMetaDataImport::IsValidToken Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: 9190d021b801be951d214406dde7e6d76da15608
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503448"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="9c32d-102">IMetaDataImport::IsValidToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c32d-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="9c32d-103">Belirtilen belirtecin bir kod nesnesine geçerli bir başvuru içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="9c32d-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c32d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9c32d-104">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c32d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c32d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="9c32d-106">'ndaki Başvuru geçerliliğini denetlenecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="9c32d-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c32d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9c32d-107">Return Value</span></span>  
 <span data-ttu-id="9c32d-108">`true``tk`geçerli kapsam içinde geçerli bir meta veri belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="9c32d-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="9c32d-109">Tersi durumda `false`.</span><span class="sxs-lookup"><span data-stu-id="9c32d-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c32d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c32d-110">Requirements</span></span>  
 <span data-ttu-id="9c32d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c32d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c32d-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9c32d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c32d-113">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9c32d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c32d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c32d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c32d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c32d-115">See also</span></span>

- [<span data-ttu-id="9c32d-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c32d-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9c32d-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c32d-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
