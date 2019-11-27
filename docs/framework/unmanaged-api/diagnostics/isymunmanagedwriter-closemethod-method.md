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
ms.openlocfilehash: a6a6aa937078ed0627688a4eed3d9142a2e6e0ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428097"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="42ab0-102">ISymUnmanagedWriter::CloseMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42ab0-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="42ab0-103">Geçerli yöntemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="42ab0-103">Closes the current method.</span></span> <span data-ttu-id="42ab0-104">Bir yöntem kapatıldıktan sonra bunun içinde başka semboller tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="42ab0-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42ab0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42ab0-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="42ab0-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="42ab0-106">Return Value</span></span>  
 <span data-ttu-id="42ab0-107">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="42ab0-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42ab0-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42ab0-108">Requirements</span></span>  
 <span data-ttu-id="42ab0-109">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="42ab0-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42ab0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42ab0-110">See also</span></span>

- [<span data-ttu-id="42ab0-111">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42ab0-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="42ab0-112">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42ab0-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
