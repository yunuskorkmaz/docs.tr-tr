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
ms.openlocfilehash: e4a415b21e3980e7603319d7acbb3831462fac9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449288"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="65fd9-102">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65fd9-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="65fd9-103">Sembol bağlayıcı arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="65fd9-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="65fd9-104">`ISymUnmanagedBinder` arabirimini uygulayan bir nesne üzerinde `QueryInterface` çağırarak bu arabirimi elde edin.</span><span class="sxs-lookup"><span data-stu-id="65fd9-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="65fd9-105">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="65fd9-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65fd9-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="65fd9-106">Methods</span></span>  
  
|<span data-ttu-id="65fd9-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="65fd9-107">Method</span></span>|<span data-ttu-id="65fd9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65fd9-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65fd9-109">GetReaderFromCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65fd9-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="65fd9-110">Kullanıcının bellekten hata ayıklama dizini bilgilerini elde etmek için bir `IID_IDiaReadExeAtRVACallback` veya `IID_IDiaReadExeAtOffsetCallback` geri çağırma yoluyla uygulama veya sağlama olanağı sağlar</span><span class="sxs-lookup"><span data-stu-id="65fd9-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65fd9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65fd9-111">Requirements</span></span>  
 <span data-ttu-id="65fd9-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="65fd9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65fd9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65fd9-113">See also</span></span>

- [<span data-ttu-id="65fd9-114">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="65fd9-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="65fd9-115">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65fd9-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="65fd9-116">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65fd9-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
