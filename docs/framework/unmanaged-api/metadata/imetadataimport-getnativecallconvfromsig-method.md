---
title: IMetaDataImport::GetNativeCallConvFromSig Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
ms.openlocfilehash: 44439eda62f85c32893b73f17bd057195cf6b2e1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503555"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="56d01-102">IMetaDataImport::GetNativeCallConvFromSig Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56d01-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="56d01-103">Belirtilen imza işaretçisi tarafından temsil edilen yöntem için yerel çağırma kuralını alır.</span><span class="sxs-lookup"><span data-stu-id="56d01-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56d01-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="56d01-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56d01-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56d01-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="56d01-106">'ndaki Çağırma kuralını döndürmek için yönteminin meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="56d01-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="56d01-107">'ndaki Bayt cinsinden boyut `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="56d01-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="56d01-108">dışı Yerel çağırma kuralına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="56d01-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56d01-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56d01-109">Requirements</span></span>  
 <span data-ttu-id="56d01-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56d01-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56d01-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="56d01-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56d01-112">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="56d01-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56d01-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56d01-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d01-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56d01-114">See also</span></span>

- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="56d01-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56d01-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="56d01-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56d01-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
