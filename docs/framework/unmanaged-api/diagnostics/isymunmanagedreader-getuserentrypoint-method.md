---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetUserEntryPoint yöntemi'
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
ms.openlocfilehash: b8696a339fc8aefca2b1a1f9b960ba94ce565d8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763923"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="f2658-103">ISymUnmanagedReader::GetUserEntryPoint Metodu</span><span class="sxs-lookup"><span data-stu-id="f2658-103">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>

<span data-ttu-id="f2658-104">Varsa modül için Kullanıcı giriş noktası olarak belirtilen yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2658-104">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="f2658-105">Örneğin, bu yöntem, Main yönteminden önce derleyicinin ürettiği saplamalar yerine kullanıcının ana yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2658-105">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2658-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2658-106">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2658-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2658-107">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="f2658-108">dışı Giriş noktasını alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2658-108">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2658-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f2658-109">Return Value</span></span>  

 <span data-ttu-id="f2658-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f2658-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2658-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2658-111">Requirements</span></span>  

 <span data-ttu-id="f2658-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f2658-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2658-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2658-113">See also</span></span>

- [<span data-ttu-id="f2658-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2658-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
