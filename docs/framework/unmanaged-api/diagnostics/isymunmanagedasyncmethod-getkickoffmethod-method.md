---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
ms.openlocfilehash: 879b9eac7cb6df06ffe4f994b505ea9cb2396d7f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441844"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="ba12b-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba12b-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="ba12b-103">Bkz. [DefineKickoffMethod Yöntemi](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="ba12b-103">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba12b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ba12b-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba12b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba12b-105">Parameters</span></span>  
  
|<span data-ttu-id="ba12b-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="ba12b-106">Parameter</span></span>|<span data-ttu-id="ba12b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba12b-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="ba12b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ba12b-108">Return Value</span></span>  
 <span data-ttu-id="ba12b-109">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="ba12b-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba12b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba12b-110">Requirements</span></span>  
 <span data-ttu-id="ba12b-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ba12b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba12b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba12b-112">See also</span></span>

- [<span data-ttu-id="ba12b-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba12b-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
