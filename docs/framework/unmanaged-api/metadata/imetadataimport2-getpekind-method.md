---
title: IMetaDataImport2::GetPEKind Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d9dda1fb38546138d52b5fe61754d5497e676c37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113509"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="8137c-102">IMetaDataImport2::GetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8137c-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="8137c-103">Alır dosya taşınabilir çalıştırılabilir (PE) kod yapısını tanımlayan bir değeri, geçerli meta veri kapsamda tanımlanan genellikle bir DLL veya EXE dosyasının.</span><span class="sxs-lookup"><span data-stu-id="8137c-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8137c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8137c-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8137c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8137c-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="8137c-106">[out] Bir işaretçi değerini [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) PE dosyası açıklayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="8137c-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="8137c-107">[out] Makine mimarisini tanımlayan bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8137c-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="8137c-108">Olası değerler için sonraki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="8137c-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8137c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8137c-109">Remarks</span></span>  
 <span data-ttu-id="8137c-110">Tarafından başvurulan değer `pdwMachine` parametresi aşağıdakilerden biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="8137c-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="8137c-111">Değer</span><span class="sxs-lookup"><span data-stu-id="8137c-111">Value</span></span>|<span data-ttu-id="8137c-112">Makine mimarisi</span><span class="sxs-lookup"><span data-stu-id="8137c-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="8137c-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="8137c-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="8137c-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="8137c-114">0x014C</span></span>|<span data-ttu-id="8137c-115">x86</span><span class="sxs-lookup"><span data-stu-id="8137c-115">x86</span></span>|  
|<span data-ttu-id="8137c-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="8137c-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="8137c-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="8137c-117">0x0200</span></span>|<span data-ttu-id="8137c-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="8137c-118">Intel IPF</span></span>|  
|<span data-ttu-id="8137c-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="8137c-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="8137c-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="8137c-120">0x8664</span></span>|<span data-ttu-id="8137c-121">X64</span><span class="sxs-lookup"><span data-stu-id="8137c-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8137c-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8137c-122">Requirements</span></span>  
 <span data-ttu-id="8137c-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8137c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8137c-124">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8137c-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8137c-125">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="8137c-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="8137c-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="8137c-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8137c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8137c-127">See also</span></span>

- [<span data-ttu-id="8137c-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8137c-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="8137c-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8137c-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8137c-130">CorPEKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8137c-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
