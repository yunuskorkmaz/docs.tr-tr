---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataImport:: Getpınvokemap yöntemi'
title: IMetaDataImport::GetPinvokeMap Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
ms.openlocfilehash: fcf45f4741709423aa48dcf895dfc4be276e19fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649448"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="87d50-103">IMetaDataImport::GetPinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87d50-103">IMetaDataImport::GetPinvokeMap Method</span></span>

<span data-ttu-id="87d50-104">Bir PInvoke çağrısının hedef derlemesini temsil eden bir ModuleRef belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="87d50-104">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87d50-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87d50-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87d50-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87d50-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="87d50-107">'ndaki İçin PInvoke eşleme meta verilerini almak için FieldDef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="87d50-107">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="87d50-108">dışı Eşleme için kullanılan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="87d50-108">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="87d50-109">Bu değer, [Corpınvokemap](corpinvokemap-enumeration.md) numaralandırmasındaki bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="87d50-109">This value is a bitmask from the [CorPinvokeMap](corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="87d50-110">dışı Yönetilmeyen hedef DLL 'in adı.</span><span class="sxs-lookup"><span data-stu-id="87d50-110">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="87d50-111">'ndaki Öğesinin geniş karakterdeki boyutu `szImportName` .</span><span class="sxs-lookup"><span data-stu-id="87d50-111">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="87d50-112">dışı İçinde döndürülen geniş karakter sayısı `szImportName` .</span><span class="sxs-lookup"><span data-stu-id="87d50-112">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="87d50-113">dışı Yönetilmeyen hedef nesne kitaplığını temsil eden bir ModuleRef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="87d50-113">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87d50-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87d50-114">Requirements</span></span>  

 <span data-ttu-id="87d50-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87d50-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d50-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="87d50-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87d50-117">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="87d50-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87d50-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87d50-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d50-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87d50-119">See also</span></span>

- [<span data-ttu-id="87d50-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87d50-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="87d50-121">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87d50-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
