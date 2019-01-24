---
title: ISymUnmanagedWriter::Close Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 780c19acd3d6980c0fb3e31d01e569a61fd04d6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647315"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="11ce4-102">ISymUnmanagedWriter::Close Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11ce4-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="11ce4-103">Sembolleri sembol deposuna uyguladıktan sonra sembol yazıcı kapatır.</span><span class="sxs-lookup"><span data-stu-id="11ce4-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11ce4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11ce4-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="11ce4-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="11ce4-105">Return Value</span></span>  
 <span data-ttu-id="11ce4-106">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="11ce4-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11ce4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11ce4-107">Remarks</span></span>  
 <span data-ttu-id="11ce4-108">Bu çağrıdan sonra sembol yazıcısı güncelleştirmeleri daha fazla geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="11ce4-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="11ce4-109">Sembol yazıcı simgeleri kaydetmeden kapatmak için kullanmak [Isymunmanagedwriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="11ce4-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11ce4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11ce4-110">Requirements</span></span>  
 <span data-ttu-id="11ce4-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="11ce4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ce4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11ce4-112">See also</span></span>
- [<span data-ttu-id="11ce4-113">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11ce4-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
