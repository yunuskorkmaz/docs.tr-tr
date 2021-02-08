---
description: ': IMetaDataImport:: GetScopeProps yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetScopeProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: 2ed7c08cc876f467a46fe38c7c27719e5608e623
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789157"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="18c7e-103">IMetaDataImport::GetScopeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="18c7e-103">IMetaDataImport::GetScopeProps Method</span></span>

<span data-ttu-id="18c7e-104">Geçerli meta veri kapsamındaki derleme ya da modülün adını ve isteğe bağlı olarak sürüm tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="18c7e-104">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18c7e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18c7e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18c7e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18c7e-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="18c7e-107">dışı Derleme veya modül adı için bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="18c7e-107">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="18c7e-108">'ndaki Öğesinin geniş karakterdeki boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="18c7e-108">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="18c7e-109">dışı İçinde döndürülen geniş karakter sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="18c7e-109">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="18c7e-110">[Out, isteğe bağlı] Derlemenin veya modülün sürümünü benzersiz bir şekilde tanımlayan GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="18c7e-110">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18c7e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18c7e-111">Remarks</span></span>  

 <span data-ttu-id="18c7e-112">Bu özellikleri ayarlamak için [ımetadatayayma:: SetModuleProps](imetadataemit-setmoduleprops-method.md) yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="18c7e-112">The [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18c7e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18c7e-113">Requirements</span></span>  

 <span data-ttu-id="18c7e-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18c7e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18c7e-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="18c7e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18c7e-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="18c7e-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18c7e-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18c7e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18c7e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18c7e-118">See also</span></span>

- [<span data-ttu-id="18c7e-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18c7e-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="18c7e-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18c7e-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
