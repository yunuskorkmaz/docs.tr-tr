---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24560ed4b0bb7ca04d5859280baa594fbb2e4097
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473478"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="e476c-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e476c-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="e476c-103">Zaman uyumsuz işlem başlattığı başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e476c-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e476c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e476c-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e476c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e476c-105">Parameters</span></span>  
  
|<span data-ttu-id="e476c-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="e476c-106">Parameter</span></span>|<span data-ttu-id="e476c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e476c-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="e476c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e476c-108">Return Value</span></span>  
 <span data-ttu-id="e476c-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="e476c-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e476c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e476c-110">Requirements</span></span>  
 <span data-ttu-id="e476c-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e476c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e476c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e476c-112">See also</span></span>
- [<span data-ttu-id="e476c-113">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e476c-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
