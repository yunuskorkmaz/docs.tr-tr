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
ms.openlocfilehash: be91591bfbbe4531c5518b90e560bc05457c92da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730171"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="da9fb-102">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da9fb-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="da9fb-103">Sembol bağlayıcı arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="da9fb-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="da9fb-104">Bu arabirim çağırarak elde `QueryInterface` uygulayan bir nesne üzerinde `ISymUnmanagedBinder` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="da9fb-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="da9fb-105">Bu, güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyası açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da9fb-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da9fb-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="da9fb-106">Methods</span></span>  
  
|<span data-ttu-id="da9fb-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="da9fb-107">Method</span></span>|<span data-ttu-id="da9fb-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da9fb-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da9fb-109">GetReaderFromCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da9fb-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="da9fb-110">Uygulama veya geri çağırma ya da kaynağı izin verir bir `IID_IDiaReadExeAtRVACallback` veya `IID_IDiaReadExeAtOffsetCallback` bellekten hata ayıklama dizin bilgileri almak için</span><span class="sxs-lookup"><span data-stu-id="da9fb-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da9fb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da9fb-111">Requirements</span></span>  
 <span data-ttu-id="da9fb-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="da9fb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da9fb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da9fb-113">See also</span></span>
- [<span data-ttu-id="da9fb-114">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="da9fb-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="da9fb-115">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da9fb-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="da9fb-116">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da9fb-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
