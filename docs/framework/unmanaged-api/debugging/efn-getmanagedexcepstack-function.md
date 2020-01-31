---
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
ms.openlocfilehash: 824be4a401d265575b48f66045dd944d521e64a4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789147"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="10bda-102">\_EFN\_GetManagedExcepStack Işlevi</span><span class="sxs-lookup"><span data-stu-id="10bda-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="10bda-103">Yönetilen bir özel durum nesne adresi verildiğinde, içinde bulunan yığın izlemenin bir dize sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="10bda-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10bda-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10bda-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10bda-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10bda-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="10bda-106">'ndaki Hata ayıklamakta olan istemci.</span><span class="sxs-lookup"><span data-stu-id="10bda-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="10bda-107">'ndaki <xref:System.Exception>türetilen bir yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="10bda-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="10bda-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="10bda-108">szStackString</span></span>  
 <span data-ttu-id="10bda-109">dışı Döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="10bda-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="10bda-110">dışı Dize arabelleğinde kullanılabilir olan karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="10bda-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10bda-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10bda-111">Remarks</span></span>  
 <span data-ttu-id="10bda-112">Şu anda bağlamda iş parçacığında yönetilen kod yoksa, işlev, bir 0xa0 tesis değeri ve 0x1000 hata kodu ile HRESULT SOS_E_NOMANAGEDCODE döndürür.</span><span class="sxs-lookup"><span data-stu-id="10bda-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10bda-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10bda-113">Requirements</span></span>  
 <span data-ttu-id="10bda-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10bda-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10bda-115">**Üst bilgi:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="10bda-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="10bda-116">**.NET Framework sürümü:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10bda-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10bda-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10bda-117">See also</span></span>

- [<span data-ttu-id="10bda-118">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="10bda-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
