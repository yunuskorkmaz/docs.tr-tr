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
ms.openlocfilehash: d465f830fa73016c3cf3f7df3a4a4d0c42bc0980
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615507"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="ad54e-102">ISymUnmanagedReader::GetUserEntryPoint Metodu</span><span class="sxs-lookup"><span data-stu-id="ad54e-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="ad54e-103">Varsa modül için Kullanıcı giriş noktası olarak belirtilen yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ad54e-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="ad54e-104">Örneğin, bu yöntem, Main yönteminden önce derleyicinin ürettiği saplamalar yerine kullanıcının ana yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad54e-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad54e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ad54e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad54e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad54e-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="ad54e-107">dışı Giriş noktasını alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ad54e-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad54e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ad54e-108">Return Value</span></span>  
 <span data-ttu-id="ad54e-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ad54e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad54e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad54e-110">Requirements</span></span>  
 <span data-ttu-id="ad54e-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ad54e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad54e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad54e-112">See also</span></span>

- [<span data-ttu-id="ad54e-113">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad54e-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
