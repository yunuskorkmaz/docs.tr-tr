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
ms.openlocfilehash: 3626998c456e23fb922ae45a68bedb0e45a7ccba
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490438"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="8bd93-102">IMetaDataImport2::GetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8bd93-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="8bd93-103">Taşınabilir yürütülebilir (PE) dosyasındaki, genellikle geçerli meta veri kapsamında tanımlanan bir DLL veya EXE dosyası olan kodun yapısını tanımlayan bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="8bd93-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bd93-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8bd93-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bd93-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8bd93-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="8bd93-106">dışı PE dosyasını tanımlayan bir [CorPEKind](corpekind-enumeration.md) numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8bd93-106">[out] A pointer to a value of the [CorPEKind](corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="8bd93-107">dışı Makinenin mimarisini tanımlayan bir değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8bd93-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="8bd93-108">Olası değerler için sonraki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="8bd93-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bd93-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bd93-109">Remarks</span></span>  
 <span data-ttu-id="8bd93-110">Parametresi tarafından başvurulan değer `pdwMachine` aşağıdakilerden biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="8bd93-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="8bd93-111">Değer</span><span class="sxs-lookup"><span data-stu-id="8bd93-111">Value</span></span>|<span data-ttu-id="8bd93-112">Makine mimarisi</span><span class="sxs-lookup"><span data-stu-id="8bd93-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="8bd93-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="8bd93-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="8bd93-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="8bd93-114">0x014C</span></span>|<span data-ttu-id="8bd93-115">x86</span><span class="sxs-lookup"><span data-stu-id="8bd93-115">x86</span></span>|  
|<span data-ttu-id="8bd93-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="8bd93-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="8bd93-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="8bd93-117">0x0200</span></span>|<span data-ttu-id="8bd93-118">Intel ıPF</span><span class="sxs-lookup"><span data-stu-id="8bd93-118">Intel IPF</span></span>|  
|<span data-ttu-id="8bd93-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="8bd93-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="8bd93-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="8bd93-120">0x8664</span></span>|<span data-ttu-id="8bd93-121">x64</span><span class="sxs-lookup"><span data-stu-id="8bd93-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8bd93-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bd93-122">Requirements</span></span>  
 <span data-ttu-id="8bd93-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bd93-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bd93-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8bd93-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bd93-125">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8bd93-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8bd93-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bd93-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd93-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bd93-127">See also</span></span>

- [<span data-ttu-id="8bd93-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bd93-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="8bd93-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bd93-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8bd93-130">CorPEKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8bd93-130">CorPEKind Enumeration</span></span>](corpekind-enumeration.md)
