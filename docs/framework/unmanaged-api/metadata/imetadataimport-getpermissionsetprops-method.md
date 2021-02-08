---
description: ': IMetaDataImport:: GetPermissionSetProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9dc10b7bf531b6eec389334d80cf6a1cece20ee9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789196"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="46c9c-103">IMetaDataImport::GetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46c9c-103">IMetaDataImport::GetPermissionSetProps Method</span></span>

<span data-ttu-id="46c9c-104"><xref:System.Security.PermissionSet?displayProperty=nameWithType>Belirtilen izin belirteciyle temsil edilen ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="46c9c-104">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c9c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46c9c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46c9c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46c9c-106">Parameters</span></span>  

 `pm`  
 <span data-ttu-id="46c9c-107">'ndaki Meta veri özelliklerini almak için ayarlanan izni temsil eden Izin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="46c9c-107">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="46c9c-108">dışı İzin kümesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="46c9c-108">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="46c9c-109">dışı İzin kümesinin ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="46c9c-109">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="46c9c-110">dışı Bayt cinsinden boyut `ppvPermission` .</span><span class="sxs-lookup"><span data-stu-id="46c9c-110">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46c9c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46c9c-111">Requirements</span></span>  

 <span data-ttu-id="46c9c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46c9c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46c9c-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="46c9c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46c9c-114">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="46c9c-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="46c9c-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46c9c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c9c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46c9c-116">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="46c9c-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46c9c-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="46c9c-118">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46c9c-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
