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
ms.openlocfilehash: f0a688aef9fbc6f7bfac85e06cbe7e76704d3230
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720537"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="7bf25-102">ISymUnmanagedReader::GetUserEntryPoint Metodu</span><span class="sxs-lookup"><span data-stu-id="7bf25-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>

<span data-ttu-id="7bf25-103">Varsa modül için Kullanıcı giriş noktası olarak belirtilen yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bf25-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="7bf25-104">Örneğin, bu yöntem, Main yönteminden önce derleyicinin ürettiği saplamalar yerine kullanıcının ana yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="7bf25-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf25-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7bf25-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bf25-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7bf25-106">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="7bf25-107">dışı Giriş noktasını alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7bf25-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bf25-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7bf25-108">Return Value</span></span>  

 <span data-ttu-id="7bf25-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7bf25-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bf25-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bf25-110">Requirements</span></span>  

 <span data-ttu-id="7bf25-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7bf25-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf25-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bf25-112">See also</span></span>

- [<span data-ttu-id="7bf25-113">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bf25-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
