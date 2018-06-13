---
title: ISymUnmanagedWriter3::OpenMethod2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 643666df9f93d1aa5e09579359ae0db87908f10b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428339"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="82379-102">ISymUnmanagedWriter3::OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82379-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="82379-103">Bir yöntem açar ve gerçek bölüm sapması görüntüdeki sağlar.</span><span class="sxs-lookup"><span data-stu-id="82379-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82379-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82379-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82379-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82379-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="82379-106">[in] Yöntemin açılması meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="82379-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="82379-107">[in] Görüntüde bölüm uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="82379-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="82379-108">[in] Görüntüde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="82379-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82379-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="82379-109">Return Value</span></span>  
 <span data-ttu-id="82379-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="82379-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82379-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82379-111">Requirements</span></span>  
 <span data-ttu-id="82379-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="82379-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82379-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82379-113">See Also</span></span>  
 [<span data-ttu-id="82379-114">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82379-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="82379-115">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82379-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
