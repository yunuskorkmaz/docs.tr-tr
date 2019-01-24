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
ms.openlocfilehash: a8519577bb2b9d3ff8fa2138ba007d04d9fde159
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730158"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="b4745-102">ISymUnmanagedReader::GetUserEntryPoint Metodu</span><span class="sxs-lookup"><span data-stu-id="b4745-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="b4745-103">Modül için kullanıcı giriş noktası olarak belirtilen yöntem varsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="b4745-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="b4745-104">Örneğin, bu yöntem, derleyicinin ürettiği saptamalar önce ana yöntem yerine kullanıcının ana yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4745-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4745-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4745-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4745-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4745-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="b4745-107">[out] Giriş noktası alan bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b4745-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4745-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b4745-108">Return Value</span></span>  
 <span data-ttu-id="b4745-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b4745-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4745-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4745-110">Requirements</span></span>  
 <span data-ttu-id="b4745-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b4745-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4745-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4745-112">See also</span></span>
- [<span data-ttu-id="b4745-113">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4745-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
