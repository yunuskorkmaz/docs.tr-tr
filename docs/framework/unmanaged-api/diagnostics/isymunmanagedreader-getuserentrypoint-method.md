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
ms.openlocfilehash: 995c7edf99c917b8bcdc1d51dcc0bf50868e4f35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777061"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="f1259-102">ISymUnmanagedReader::GetUserEntryPoint Metodu</span><span class="sxs-lookup"><span data-stu-id="f1259-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="f1259-103">Modül için kullanıcı giriş noktası olarak belirtilen yöntem varsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="f1259-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="f1259-104">Örneğin, bu yöntem, derleyicinin ürettiği saptamalar önce ana yöntem yerine kullanıcının ana yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1259-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1259-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1259-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1259-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1259-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="f1259-107">[out] Giriş noktası alan bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1259-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1259-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f1259-108">Return Value</span></span>  
 <span data-ttu-id="f1259-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f1259-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1259-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1259-110">Requirements</span></span>  
 <span data-ttu-id="f1259-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f1259-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1259-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1259-112">See also</span></span>

- [<span data-ttu-id="f1259-113">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1259-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
