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
ms.openlocfilehash: 0267ae8b57c837b097d496c8e119085d03417e36
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211276"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="d14fd-102">ISymUnmanagedReader::GetUserEntryPoint Metodu</span><span class="sxs-lookup"><span data-stu-id="d14fd-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="d14fd-103">Modül için kullanıcı giriş noktası olarak belirtilen yöntem varsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="d14fd-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="d14fd-104">Örneğin, bu yöntem, derleyicinin ürettiği saptamalar önce ana yöntem yerine kullanıcının ana yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="d14fd-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d14fd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d14fd-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d14fd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d14fd-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="d14fd-107">[out] Giriş noktası alan bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d14fd-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d14fd-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d14fd-108">Return Value</span></span>  
 <span data-ttu-id="d14fd-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d14fd-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d14fd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d14fd-110">Requirements</span></span>  
 <span data-ttu-id="d14fd-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d14fd-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d14fd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d14fd-112">See also</span></span>

- [<span data-ttu-id="d14fd-113">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d14fd-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
