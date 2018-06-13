---
title: ISymUnmanagedWriter::CloseMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71be697a8a1decd9b5f780d047c3dbb397e351d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426899"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="a5510-102">ISymUnmanagedWriter::CloseMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5510-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="a5510-103">Geçerli yöntemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="a5510-103">Closes the current method.</span></span> <span data-ttu-id="a5510-104">Bir yöntem kapatıldıktan sonra daha fazla simge içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a5510-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5510-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5510-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a5510-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a5510-106">Return Value</span></span>  
 <span data-ttu-id="a5510-107">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a5510-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5510-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5510-108">Requirements</span></span>  
 <span data-ttu-id="a5510-109">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a5510-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5510-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5510-110">See Also</span></span>  
 [<span data-ttu-id="a5510-111">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5510-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="a5510-112">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5510-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
