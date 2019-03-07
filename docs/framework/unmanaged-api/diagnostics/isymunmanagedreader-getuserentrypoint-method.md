---
title: ISymUnmanagedReader::GetUserEntryPoint Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea0cba1f1b9154ccb14d75f7c377a8153c24f2b0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499501"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="5531c-102">ISymUnmanagedReader::GetUserEntryPoint Metodu</span><span class="sxs-lookup"><span data-stu-id="5531c-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="5531c-103">Modül için kullanıcı giriş noktası olarak belirtilen yöntem varsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="5531c-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="5531c-104">Örneğin, bu yöntem, derleyicinin ürettiği saptamalar önce ana yöntem yerine kullanıcının ana yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="5531c-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5531c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5531c-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5531c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5531c-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="5531c-107">[out] Giriş noktası alan bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5531c-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5531c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5531c-108">Return Value</span></span>  
 <span data-ttu-id="5531c-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5531c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5531c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5531c-110">Requirements</span></span>  
 <span data-ttu-id="5531c-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5531c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5531c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5531c-112">See also</span></span>
- [<span data-ttu-id="5531c-113">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5531c-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
