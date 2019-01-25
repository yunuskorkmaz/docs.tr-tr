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
ms.openlocfilehash: e149f121de8c965c2215f58dba1a485feebd32ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643630"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="757d7-102">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="757d7-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="757d7-103">Yönetilmeyen kod için bir simge bağlayıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="757d7-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="757d7-104">Bu, güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyası açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="757d7-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="757d7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="757d7-105">Methods</span></span>  
  
|<span data-ttu-id="757d7-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="757d7-106">Method</span></span>|<span data-ttu-id="757d7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="757d7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="757d7-108">GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="757d7-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="757d7-109">Meta veri arayüzü ve bir dosya adı, doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) modülle ilişkili hata ayıklama sembolleri okuyacaksa yapısı.</span><span class="sxs-lookup"><span data-stu-id="757d7-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="757d7-110">GetReaderFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="757d7-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="757d7-111">Bir meta veri arabirimi ve sembol deposu içeren bir akış doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) hata ayıklama okuyacaksa yapısı belirli sembol deposundan simgeler.</span><span class="sxs-lookup"><span data-stu-id="757d7-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="757d7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="757d7-112">Requirements</span></span>  
 <span data-ttu-id="757d7-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="757d7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="757d7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="757d7-114">See also</span></span>
- [<span data-ttu-id="757d7-115">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="757d7-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="757d7-116">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="757d7-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="757d7-117">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="757d7-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
