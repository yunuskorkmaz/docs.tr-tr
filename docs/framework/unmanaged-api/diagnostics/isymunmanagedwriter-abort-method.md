---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: Abort yöntemi'
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
ms.openlocfilehash: 312694bf2b667ea78bf5ddc993d0e2b71c85a8ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762688"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="000e5-103">ISymUnmanagedWriter::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="000e5-103">ISymUnmanagedWriter::Abort Method</span></span>

<span data-ttu-id="000e5-104">Sembol deposuna sembolleri kaydetmeden sembol yazıcısını kapatır.</span><span class="sxs-lookup"><span data-stu-id="000e5-104">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="000e5-105">Bu çağrıdan sonra sembol yazıcısı, daha fazla güncelleştirme için geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="000e5-105">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="000e5-106">Sembolleri yürütmek ve sembol yazıcısını kapatmak için, bunun yerine [ıvmunmanagedwriter:: Close](isymunmanagedwriter-close-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="000e5-106">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="000e5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="000e5-107">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="000e5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="000e5-108">Return Value</span></span>  

 <span data-ttu-id="000e5-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="000e5-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="000e5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="000e5-110">Requirements</span></span>  

 <span data-ttu-id="000e5-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="000e5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="000e5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="000e5-112">See also</span></span>

- [<span data-ttu-id="000e5-113">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="000e5-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
