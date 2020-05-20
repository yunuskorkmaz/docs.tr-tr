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
ms.openlocfilehash: 8b51a9dc3a968c6bd2f5f9b149f13f88dc6a1e05
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614753"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="32d07-102">ISymUnmanagedWriter::SetUserEntryPoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32d07-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="32d07-103">Bu modülün giriş noktası olan Kullanıcı tanımlı yöntemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="32d07-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="32d07-104">Örneğin, bu giriş noktası, Main öncesinde derleyicinin ürettiği saplamalar yerine kullanıcının ana yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="32d07-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32d07-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="32d07-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32d07-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32d07-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="32d07-107">'ndaki Kullanıcı giriş noktası olan yöntemi için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="32d07-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32d07-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="32d07-108">Return Value</span></span>  
 <span data-ttu-id="32d07-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="32d07-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32d07-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32d07-110">Requirements</span></span>  
 <span data-ttu-id="32d07-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="32d07-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d07-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32d07-112">See also</span></span>

- [<span data-ttu-id="32d07-113">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32d07-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
