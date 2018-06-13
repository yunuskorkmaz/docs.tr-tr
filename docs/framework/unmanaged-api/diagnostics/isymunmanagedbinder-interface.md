---
title: ISymUnmanagedBinder Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7bbdc4b1f15c8dbb154ed7b967bb21c61d11782a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425558"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="08c4d-102">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08c4d-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="08c4d-103">Yönetilmeyen kod için bir simge bağlayıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="08c4d-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="08c4d-104">Güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyasını açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08c4d-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08c4d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="08c4d-105">Methods</span></span>  
  
|<span data-ttu-id="08c4d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="08c4d-106">Method</span></span>|<span data-ttu-id="08c4d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08c4d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08c4d-108">GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08c4d-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="08c4d-109">Bir meta veri arabirimi ve bir dosya adı doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) modülle ilişkili hata ayıklama simgeleri okuma yapacak yapısı.</span><span class="sxs-lookup"><span data-stu-id="08c4d-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="08c4d-110">GetReaderFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08c4d-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="08c4d-111">Bir meta veri arabirimi ve sembol deposu içeren bir akışı doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) hata ayıklama okuma yapısı belirtilen simge Mağazası'ndan simgeler.</span><span class="sxs-lookup"><span data-stu-id="08c4d-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08c4d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08c4d-112">Requirements</span></span>  
 <span data-ttu-id="08c4d-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="08c4d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c4d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08c4d-114">See Also</span></span>  
 [<span data-ttu-id="08c4d-115">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="08c4d-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="08c4d-116">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08c4d-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="08c4d-117">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08c4d-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
