---
title: IMetaDataImport::GetPermissionSetProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
ms.openlocfilehash: 5faf1a6ae89045b2ef17fab789ee6e5bf23eecf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175349"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="18de9-102">IMetaDataImport::GetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18de9-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="18de9-103">Belirtilen İzin belirteci <xref:System.Security.PermissionSet?displayProperty=nameWithType> tarafından temsil edilenile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="18de9-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18de9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18de9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18de9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18de9-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="18de9-106">[içinde] Meta veri özelliklerini almak için izin kümesini temsil eden İzin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="18de9-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="18de9-107">[çıkış] İzin kümesiiçin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18de9-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="18de9-108">[çıkış] İzin kümesinin ikili meta veri imzasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18de9-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="18de9-109">[çıkış] `ppvPermission`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="18de9-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18de9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18de9-110">Requirements</span></span>  
 <span data-ttu-id="18de9-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18de9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18de9-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="18de9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18de9-113">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="18de9-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18de9-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18de9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18de9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18de9-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="18de9-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18de9-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="18de9-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18de9-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
