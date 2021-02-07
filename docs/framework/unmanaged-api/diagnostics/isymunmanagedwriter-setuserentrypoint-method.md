---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: SetUserEntryPoint Yöntemi'
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
ms.openlocfilehash: a01d23a0462fabd7a2fc259722dcdf2a1c8e0a4c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761986"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="d0d97-103">ISymUnmanagedWriter::SetUserEntryPoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0d97-103">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>

<span data-ttu-id="d0d97-104">Bu modülün giriş noktası olan Kullanıcı tanımlı yöntemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0d97-104">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="d0d97-105">Örneğin, bu giriş noktası, Main öncesinde derleyicinin ürettiği saplamalar yerine kullanıcının ana yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0d97-105">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0d97-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0d97-106">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0d97-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0d97-107">Parameters</span></span>  

 `entryMethod`  
 <span data-ttu-id="d0d97-108">'ndaki Kullanıcı giriş noktası olan yöntemi için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="d0d97-108">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0d97-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0d97-109">Return Value</span></span>  

 <span data-ttu-id="d0d97-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d0d97-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0d97-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0d97-111">Requirements</span></span>  

 <span data-ttu-id="d0d97-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d0d97-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d97-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0d97-113">See also</span></span>

- [<span data-ttu-id="d0d97-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0d97-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
