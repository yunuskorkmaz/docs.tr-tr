---
title: GetMethodOrigin işlevi (Yönetilmeyen API Başvurusu)
description: GetMethodOrigin işlevi, yöntemin bildirildiği sınıfı belirler.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b4609b6649be875aea7dfcf52ba36b1e98ab7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176805"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="3faa7-103">GetMethodOrigin işlevi</span><span class="sxs-lookup"><span data-stu-id="3faa7-103">GetMethodOrigin function</span></span>
<span data-ttu-id="3faa7-104">Yöntemin bildirildiği sınıfı belirler.</span><span class="sxs-lookup"><span data-stu-id="3faa7-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="3faa7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3faa7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a><span data-ttu-id="3faa7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3faa7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3faa7-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="3faa7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3faa7-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3faa7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="3faa7-109">[içinde] Sahibi sınıfı istenen nesne için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="3faa7-109">[in] The name of the method for the object whose owning class is being requested.</span></span>

`pstrClassName`  
<span data-ttu-id="3faa7-110">[çıkış] Yöntemin sahibi sınıfın adını alır.</span><span class="sxs-lookup"><span data-stu-id="3faa7-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="3faa7-111">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="3faa7-111">Return value</span></span>

<span data-ttu-id="3faa7-112">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3faa7-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3faa7-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="3faa7-113">Constant</span></span>  |<span data-ttu-id="3faa7-114">Değer</span><span class="sxs-lookup"><span data-stu-id="3faa7-114">Value</span></span>  |<span data-ttu-id="3faa7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3faa7-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="3faa7-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="3faa7-116">0x80041002</span></span> | <span data-ttu-id="3faa7-117">Belirtilen yöntem bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="3faa7-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3faa7-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3faa7-118">0x80041008</span></span> | <span data-ttu-id="3faa7-119">Bir veya daha fazla parametre geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="3faa7-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3faa7-120">0</span><span class="sxs-lookup"><span data-stu-id="3faa7-120">0</span></span> | <span data-ttu-id="3faa7-121">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="3faa7-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3faa7-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3faa7-122">Remarks</span></span>

<span data-ttu-id="3faa7-123">Bu [işlev, IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="3faa7-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="3faa7-124">Bir sınıf yöntemleri bir veya daha fazla temel sınıftan devralabileceğinden, geliştiriciler genellikle belirli bir yöntemin tanımlandığı sınıfı belirlemek ister.</span><span class="sxs-lookup"><span data-stu-id="3faa7-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="3faa7-125">Bu `pstrClassName` bir parametre olduğundan, `BSTR` işlev çağrılmadan önce `out` parametre geçerliyi işaret etmemelidir; bu işaretçi işlev döndükten sonra ayrılmaz.</span><span class="sxs-lookup"><span data-stu-id="3faa7-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="3faa7-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3faa7-126">Requirements</span></span>  
<span data-ttu-id="3faa7-127">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3faa7-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3faa7-128">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3faa7-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3faa7-129">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3faa7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3faa7-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3faa7-130">See also</span></span>

- [<span data-ttu-id="3faa7-131">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3faa7-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
