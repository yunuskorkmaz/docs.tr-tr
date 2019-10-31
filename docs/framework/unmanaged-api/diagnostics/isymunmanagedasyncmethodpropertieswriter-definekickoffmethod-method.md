---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: ccf1287a1b0218e7f2560e1afbb0930c93b43263
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129169"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="934be-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="934be-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="934be-103">Zaman uyumsuz işlemi başlatan başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="934be-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="934be-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="934be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="934be-105">Parameters</span></span>  
  
|<span data-ttu-id="934be-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="934be-106">Parameter</span></span>|<span data-ttu-id="934be-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="934be-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="934be-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="934be-108">Return Value</span></span>  
 <span data-ttu-id="934be-109">`HRESULT`döndürür.</span><span class="sxs-lookup"><span data-stu-id="934be-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934be-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="934be-110">Requirements</span></span>  
 <span data-ttu-id="934be-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="934be-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934be-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="934be-112">See also</span></span>

- [<span data-ttu-id="934be-113">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="934be-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
