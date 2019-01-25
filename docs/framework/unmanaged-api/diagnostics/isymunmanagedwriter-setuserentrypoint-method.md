---
title: ISymUnmanagedWriter::SetUserEntryPoint Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7595b4a69dd327e448aade1e2dcba06100e55bf4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638693"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="9549b-102">ISymUnmanagedWriter::SetUserEntryPoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9549b-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="9549b-103">Bu modülü için giriş noktası kullanıcı tanımlı bir yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9549b-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="9549b-104">Örneğin, bu giriş noktası, derleyicinin ürettiği saptamalar ana önce yerine kullanıcının ana yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="9549b-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9549b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9549b-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9549b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9549b-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="9549b-107">[in] Kullanıcı girişini yöntemi için meta veri belirteci gelin.</span><span class="sxs-lookup"><span data-stu-id="9549b-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9549b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9549b-108">Return Value</span></span>  
 <span data-ttu-id="9549b-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="9549b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9549b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9549b-110">Requirements</span></span>  
 <span data-ttu-id="9549b-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9549b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9549b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9549b-112">See also</span></span>
- [<span data-ttu-id="9549b-113">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9549b-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
