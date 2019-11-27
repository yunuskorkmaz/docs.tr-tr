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
ms.openlocfilehash: a020a0343eecceb4a85ebbddffe323c7f7bdca3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437116"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="22902-102">IMetaDataImport::GetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22902-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="22902-103">Belirtilen Izin belirteciyle temsil edilen <xref:System.Security.PermissionSet?displayProperty=nameWithType> ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="22902-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22902-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22902-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22902-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22902-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="22902-106">'ndaki Meta veri özelliklerini almak için ayarlanan izni temsil eden Izin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="22902-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="22902-107">dışı İzin kümesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="22902-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="22902-108">dışı İzin kümesinin ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="22902-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="22902-109">dışı `ppvPermission`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="22902-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22902-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22902-110">Requirements</span></span>  
 <span data-ttu-id="22902-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22902-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22902-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="22902-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22902-113">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="22902-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22902-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22902-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22902-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22902-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="22902-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22902-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="22902-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22902-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
