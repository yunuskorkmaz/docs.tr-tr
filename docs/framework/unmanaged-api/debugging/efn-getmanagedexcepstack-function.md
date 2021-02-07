---
description: 'Hakkında daha fazla bilgi edinin: _EFN_GetManagedExcepStack Işlevi'
title: _EFN_GetManagedExcepStack İşlevi
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
ms.openlocfilehash: a3c7e30a377e10b9d4d0b1dd663a594a0e872f3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738318"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="a88fa-103">\_EFN \_ getmanagedexcepstack işlevi</span><span class="sxs-lookup"><span data-stu-id="a88fa-103">\_EFN\_GetManagedExcepStack Function</span></span>

<span data-ttu-id="a88fa-104">Yönetilen bir özel durum nesne adresi verildiğinde, içinde bulunan yığın izlemenin bir dize sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="a88fa-104">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a88fa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a88fa-105">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a88fa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a88fa-106">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="a88fa-107">'ndaki Hata ayıklamakta olan istemci.</span><span class="sxs-lookup"><span data-stu-id="a88fa-107">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="a88fa-108">'ndaki Öğesinden türetilmiş bir yönetilen nesne işaretçisi <xref:System.Exception> .</span><span class="sxs-lookup"><span data-stu-id="a88fa-108">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="a88fa-109">szStackString</span><span class="sxs-lookup"><span data-stu-id="a88fa-109">szStackString</span></span>  
 <span data-ttu-id="a88fa-110">dışı Döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a88fa-110">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="a88fa-111">dışı Dize arabelleğinde kullanılabilir olan karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="a88fa-111">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a88fa-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a88fa-112">Remarks</span></span>  

 <span data-ttu-id="a88fa-113">Şu anda bağlamda iş parçacığında yönetilen kod yoksa, işlev, bir 0xa0 tesis değeri ve 0x1000 hata kodu ile HRESULT SOS_E_NOMANAGEDCODE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a88fa-113">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a88fa-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a88fa-114">Requirements</span></span>  

 <span data-ttu-id="a88fa-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a88fa-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a88fa-116">**Üst bilgi:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="a88fa-116">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="a88fa-117">**.NET Framework sürümü:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a88fa-117">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a88fa-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a88fa-118">See also</span></span>

- [<span data-ttu-id="a88fa-119">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a88fa-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
