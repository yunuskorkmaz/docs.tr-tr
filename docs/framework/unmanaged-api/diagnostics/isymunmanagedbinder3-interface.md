---
title: ISymUnmanagedBinder3 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfd8e8fc419809a3a490639ada1c533f286fe8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157514"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="74a68-102">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74a68-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="74a68-103">Sembol bağlayıcı arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="74a68-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="74a68-104">Bu arabirim çağırarak elde `QueryInterface` uygulayan bir nesne üzerinde `ISymUnmanagedBinder` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="74a68-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74a68-105">Bu, güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyası açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74a68-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74a68-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="74a68-106">Methods</span></span>  
  
|<span data-ttu-id="74a68-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="74a68-107">Method</span></span>|<span data-ttu-id="74a68-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74a68-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74a68-109">GetReaderFromCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74a68-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="74a68-110">Uygulama veya geri çağırma ya da kaynağı izin verir bir `IID_IDiaReadExeAtRVACallback` veya `IID_IDiaReadExeAtOffsetCallback` bellekten hata ayıklama dizin bilgileri almak için</span><span class="sxs-lookup"><span data-stu-id="74a68-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74a68-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74a68-111">Requirements</span></span>  
 <span data-ttu-id="74a68-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="74a68-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a68-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74a68-113">See also</span></span>

- [<span data-ttu-id="74a68-114">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="74a68-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="74a68-115">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74a68-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="74a68-116">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74a68-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
