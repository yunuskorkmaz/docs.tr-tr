---
title: QualifierSet_EndEnumeration işlevi (yönetilmeyen API Başvurusu)
description: Bir numaralandırma QualifierSet_EndEnumeration işlevi sonlandırır.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbf47dbfddac7d48b78c9d52969de1ef03385c15
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486824"
---
# <a name="qualifiersetendenumeration-function"></a><span data-ttu-id="3d748-103">QualifierSet_EndEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="3d748-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="3d748-104">Bir çağrı ile başlamış numaralandırma sonlandırır [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="3d748-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="3d748-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d748-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="3d748-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d748-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3d748-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="3d748-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="3d748-108">[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.</span><span class="sxs-lookup"><span data-stu-id="3d748-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="3d748-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="3d748-109">Return value</span></span>

<span data-ttu-id="3d748-110">Bu işlev tarafından döndürülen aşağıdaki değer *WbemCli.h* üst bilgi dosyası veya tanımlayabilir, bir sabit olarak kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="3d748-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="3d748-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="3d748-111">Constant</span></span>  |<span data-ttu-id="3d748-112">Değer</span><span class="sxs-lookup"><span data-stu-id="3d748-112">Value</span></span>  |<span data-ttu-id="3d748-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d748-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3d748-114">0</span><span class="sxs-lookup"><span data-stu-id="3d748-114">0</span></span> | <span data-ttu-id="3d748-115">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="3d748-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3d748-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d748-116">Remarks</span></span>

<span data-ttu-id="3d748-117">Bu işlev bir çağrı sarılır [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3d748-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="3d748-118">Bu çağrı önerilir, ancak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3d748-118">This call is recommended, but not required.</span></span> <span data-ttu-id="3d748-119">Numaralandırma ile ilişkili kaynakları hemen serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="3d748-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="3d748-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d748-120">Requirements</span></span>  

<span data-ttu-id="3d748-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d748-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="3d748-122">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3d748-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="3d748-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3d748-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d748-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d748-124">See also</span></span>  
[<span data-ttu-id="3d748-125">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3d748-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
