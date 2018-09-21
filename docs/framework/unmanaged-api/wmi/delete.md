---
title: Delete işlevi (yönetilmeyen API Başvurusu)
description: Silme işlevi, belirtilen özellik ve tüm alt niteleyicileri bir CIM sınıfı tanımından siler.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 791e75aa60fd651dde1555339e31664a3523e1eb
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46470907"
---
# <a name="delete-function"></a><span data-ttu-id="53c62-103">İşlevi Sil</span><span class="sxs-lookup"><span data-stu-id="53c62-103">Delete function</span></span>
<span data-ttu-id="53c62-104">Belirtilen özellik ve tüm alt niteleyicileri bir CIM sınıfı tanımını siler.</span><span class="sxs-lookup"><span data-stu-id="53c62-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="53c62-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53c62-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="53c62-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53c62-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="53c62-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="53c62-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="53c62-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="53c62-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="53c62-109">[in] Silmek için özellik adı.</span><span class="sxs-lookup"><span data-stu-id="53c62-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="53c62-110">`wszName` Geçerli bir işaretçi olmalıdır `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="53c62-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="53c62-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="53c62-111">Return value</span></span>

<span data-ttu-id="53c62-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="53c62-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="53c62-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="53c62-113">Constant</span></span>  |<span data-ttu-id="53c62-114">Değer</span><span class="sxs-lookup"><span data-stu-id="53c62-114">Value</span></span>  |<span data-ttu-id="53c62-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53c62-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="53c62-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="53c62-116">0x80041001</span></span> | <span data-ttu-id="53c62-117">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="53c62-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="53c62-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="53c62-118">0x80041016</span></span> | <span data-ttu-id="53c62-119">Özelliği silinemiyor.</span><span class="sxs-lookup"><span data-stu-id="53c62-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="53c62-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="53c62-120">0x80041008</span></span> | <span data-ttu-id="53c62-121">`wszzName` geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="53c62-121">`wszzName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="53c62-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="53c62-122">0x80041002</span></span> | <span data-ttu-id="53c62-123">Belirtilen özellik yok.</span><span class="sxs-lookup"><span data-stu-id="53c62-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="53c62-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="53c62-124">0x80041006</span></span> | <span data-ttu-id="53c62-125">İşlemi tamamlamak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="53c62-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="53c62-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="53c62-126">0x8004101c</span></span> | <span data-ttu-id="53c62-127">Özellik, bir taban sınıftan devralınır.</span><span class="sxs-lookup"><span data-stu-id="53c62-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="53c62-128">Bir sistem özelliği özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="53c62-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="53c62-129">0</span><span class="sxs-lookup"><span data-stu-id="53c62-129">0</span></span> | <span data-ttu-id="53c62-130">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="53c62-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="53c62-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="53c62-131">0x80041030</span></span> | <span data-ttu-id="53c62-132">İşlevi, geçerli sınıf için bir geçersiz kılma varsayılan değer silindi.</span><span class="sxs-lookup"><span data-stu-id="53c62-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="53c62-133">Bu özelliğin üst sınıftaki varsayılan değeri reactiviated olmuştur.</span><span class="sxs-lookup"><span data-stu-id="53c62-133">The default value for this property in the parent class has been reactiviated.</span></span> | 

## <a name="remarks"></a><span data-ttu-id="53c62-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53c62-134">Remarks</span></span>

<span data-ttu-id="53c62-135">Bu işlev bir çağrı sarılır [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="53c62-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="53c62-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53c62-136">Requirements</span></span>  
 <span data-ttu-id="53c62-137">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53c62-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53c62-138">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="53c62-138">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="53c62-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="53c62-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53c62-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53c62-140">See also</span></span>  
[<span data-ttu-id="53c62-141">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="53c62-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
