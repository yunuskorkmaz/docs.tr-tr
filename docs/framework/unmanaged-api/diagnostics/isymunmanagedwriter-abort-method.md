---
title: ISymUnmanagedWriter::Abort Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
ms.openlocfilehash: 6074ec5248d27b1405d2367349904f6630df951b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445987"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="aec3c-102">ISymUnmanagedWriter::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aec3c-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="aec3c-103">Sembol deposuna sembolleri kaydetmeden sembol yazıcısını kapatır.</span><span class="sxs-lookup"><span data-stu-id="aec3c-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="aec3c-104">Bu çağrıdan sonra sembol yazıcısı, daha fazla güncelleştirme için geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="aec3c-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="aec3c-105">Sembolleri yürütmek ve sembol yazıcısını kapatmak için, bunun yerine [ıvmunmanagedwriter:: Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="aec3c-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aec3c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aec3c-106">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="aec3c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aec3c-107">Return Value</span></span>  
 <span data-ttu-id="aec3c-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="aec3c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aec3c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aec3c-109">Requirements</span></span>  
 <span data-ttu-id="aec3c-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="aec3c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec3c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aec3c-111">See also</span></span>

- [<span data-ttu-id="aec3c-112">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aec3c-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
