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
ms.openlocfilehash: 06a4d5b1b108c15fa7ee4a7f5270b73f7adc1e6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426348"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="03bbe-102">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03bbe-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="03bbe-103">Sembol bağlayıcı arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="03bbe-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="03bbe-104">Bu arabirim çağırarak elde `QueryInterface` uygulayan bir nesne üzerinde `ISymUnmanagedBinder` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="03bbe-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03bbe-105">Güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyasını açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="03bbe-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03bbe-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="03bbe-106">Methods</span></span>  
  
|<span data-ttu-id="03bbe-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="03bbe-107">Method</span></span>|<span data-ttu-id="03bbe-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03bbe-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03bbe-109">GetReaderFromCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03bbe-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="03bbe-110">Uygulama veya geri çağırma ya da sağlayın olanak tanır. bir `IID_IDiaReadExeAtRVACallback` veya `IID_IDiaReadExeAtOffsetCallback` bellekten hata ayıklama dizin bilgilerini almak için</span><span class="sxs-lookup"><span data-stu-id="03bbe-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03bbe-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03bbe-111">Requirements</span></span>  
 <span data-ttu-id="03bbe-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="03bbe-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03bbe-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03bbe-113">See Also</span></span>  
 [<span data-ttu-id="03bbe-114">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="03bbe-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="03bbe-115">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03bbe-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="03bbe-116">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03bbe-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
