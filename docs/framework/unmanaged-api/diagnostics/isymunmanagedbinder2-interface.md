---
title: ISymUnmanagedBinder2 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38de9fa878db18222d2666ba86420ca856e4b121
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199121"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="25860-102">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25860-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="25860-103">Yönetilmeyen kod için bir simge bağlayıcı temsil eder ve genişleten [Isymunmanagedbinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="25860-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="25860-104">Bu, güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyası açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="25860-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25860-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="25860-105">Methods</span></span>  
  
|<span data-ttu-id="25860-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="25860-106">Method</span></span>|<span data-ttu-id="25860-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25860-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25860-108">GetReaderForFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25860-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="25860-109">Meta veri arayüzü ve bir dosya adı, doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) modülle ilişkili hata ayıklama sembolleri okuyacaksa arabirimi.</span><span class="sxs-lookup"><span data-stu-id="25860-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="25860-110">Daha kapsamlı bir arama daha sağlar [Isymunmanagedbinder::getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="25860-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25860-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25860-111">Requirements</span></span>  
 <span data-ttu-id="25860-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="25860-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25860-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25860-113">See also</span></span>

- [<span data-ttu-id="25860-114">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="25860-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="25860-115">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25860-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="25860-116">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25860-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
