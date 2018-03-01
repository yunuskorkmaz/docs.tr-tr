---
title: ISymUnmanagedReader::GetUserEntryPoint Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 328f44e797a49a899545fa43d940a3b0399ee8c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="4f856-102">ISymUnmanagedReader::GetUserEntryPoint Metodu</span><span class="sxs-lookup"><span data-stu-id="4f856-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="4f856-103">Modül için kullanıcı giriş noktası olarak belirtilen yöntem varsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="4f856-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="4f856-104">Örneğin, bu yöntem, derleyicinin ürettiği saplamalar main yöntemini önce yerine kullanıcının ana yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="4f856-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f856-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f856-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f856-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f856-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="4f856-107">[out] Bir işaretçi bir değişkene giriş noktası alır.</span><span class="sxs-lookup"><span data-stu-id="4f856-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f856-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4f856-108">Return Value</span></span>  
 <span data-ttu-id="4f856-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4f856-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f856-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f856-110">Requirements</span></span>  
 <span data-ttu-id="4f856-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4f856-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f856-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f856-112">See Also</span></span>  
 [<span data-ttu-id="4f856-113">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f856-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
