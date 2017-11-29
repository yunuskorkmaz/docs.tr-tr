---
title: ISymUnmanagedBinder3 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3 Interface
helpviewer_keywords: ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: df5cd6d4015fad1baf98909ee9cc923cd9bce05e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="4dc1b-102">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4dc1b-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="4dc1b-103">Sembol bağlayıcı arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="4dc1b-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="4dc1b-104">Bu arabirim çağırarak elde `QueryInterface` uygulayan bir nesne üzerinde `ISymUnmanagedBinder` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4dc1b-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4dc1b-105">Güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyasını açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4dc1b-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4dc1b-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4dc1b-106">Methods</span></span>  
  
|<span data-ttu-id="4dc1b-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4dc1b-107">Method</span></span>|<span data-ttu-id="4dc1b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4dc1b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4dc1b-109">GetReaderFromCallback yöntemi</span><span class="sxs-lookup"><span data-stu-id="4dc1b-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="4dc1b-110">Uygulama veya geri çağırma ya da sağlayın olanak tanır. bir `IID_IDiaReadExeAtRVACallback` veya `IID_IDiaReadExeAtOffsetCallback` bellekten hata ayıklama dizin bilgilerini almak için</span><span class="sxs-lookup"><span data-stu-id="4dc1b-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4dc1b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4dc1b-111">Requirements</span></span>  
 <span data-ttu-id="4dc1b-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4dc1b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc1b-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4dc1b-113">See Also</span></span>  
 [<span data-ttu-id="4dc1b-114">Tanılama sembol deposu arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4dc1b-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="4dc1b-115">Isymunmanagedbinder arabirimi</span><span class="sxs-lookup"><span data-stu-id="4dc1b-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="4dc1b-116">Isymunmanagedbinder2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="4dc1b-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
