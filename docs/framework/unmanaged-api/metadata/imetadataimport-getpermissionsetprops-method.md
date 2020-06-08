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
ms.openlocfilehash: 54c75156c32e5b40aa933ef6530b2cc33edf7de4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490997"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="2bbc4-102">IMetaDataImport::GetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2bbc4-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="2bbc4-103"><xref:System.Security.PermissionSet?displayProperty=nameWithType>Belirtilen izin belirteciyle temsil edilen ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="2bbc4-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bbc4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2bbc4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bbc4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2bbc4-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="2bbc4-106">'ndaki Meta veri özelliklerini almak için ayarlanan izni temsil eden Izin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="2bbc4-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="2bbc4-107">dışı İzin kümesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2bbc4-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="2bbc4-108">dışı İzin kümesinin ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2bbc4-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="2bbc4-109">dışı Bayt cinsinden boyut `ppvPermission` .</span><span class="sxs-lookup"><span data-stu-id="2bbc4-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bbc4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2bbc4-110">Requirements</span></span>  
 <span data-ttu-id="2bbc4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bbc4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bbc4-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2bbc4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2bbc4-113">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="2bbc4-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2bbc4-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bbc4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bbc4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bbc4-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="2bbc4-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2bbc4-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2bbc4-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2bbc4-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
