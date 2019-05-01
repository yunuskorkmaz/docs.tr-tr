---
title: ISymUnmanagedWriter::OpenMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b05ba185a9ad4ab076d29d7d609734d41677b760
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986056"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="efca3-102">ISymUnmanagedWriter::OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efca3-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="efca3-103">Hangi sembolün üretileceği bilgi yayılan bir yöntem açılır.</span><span class="sxs-lookup"><span data-stu-id="efca3-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="efca3-104">Belirtilen yöntem geçerli yöntem dizi noktaları, parametreler ve sözcük kapsamları tanımlamak çağrılar için olur.</span><span class="sxs-lookup"><span data-stu-id="efca3-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="efca3-105">Örtük bir sözcük kapsamı tüm yöntemi etrafında yoktur.</span><span class="sxs-lookup"><span data-stu-id="efca3-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="efca3-106">Daha önce kapatılan bir yöntem yeniden açmayı, bu yöntem için önceden tanımlanmış semboller siler.</span><span class="sxs-lookup"><span data-stu-id="efca3-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="efca3-107">Bir kerede yalnızca bir açık yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="efca3-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efca3-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efca3-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efca3-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="efca3-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="efca3-110">[in] Meta veri belirteci açılması yöntemi.</span><span class="sxs-lookup"><span data-stu-id="efca3-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efca3-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="efca3-111">Return Value</span></span>  
 <span data-ttu-id="efca3-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="efca3-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efca3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="efca3-113">Requirements</span></span>  
 <span data-ttu-id="efca3-114">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="efca3-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efca3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efca3-115">See also</span></span>

- [<span data-ttu-id="efca3-116">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efca3-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="efca3-117">CloseMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efca3-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="efca3-118">OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efca3-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
