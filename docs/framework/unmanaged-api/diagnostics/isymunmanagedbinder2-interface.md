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
ms.openlocfilehash: f6155eb777b5071ff522af4f27d5fb2d73aa25ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501839"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="fe7ea-102">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe7ea-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="fe7ea-103">Yönetilmeyen kod için bir sembol cildi temsil eder ve [ıstreamunmanagedciltçi](isymunmanagedbinder-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fe7ea-104">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe7ea-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fe7ea-105">Methods</span></span>  
  
|<span data-ttu-id="fe7ea-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe7ea-106">Method</span></span>|<span data-ttu-id="fe7ea-107">Description</span><span class="sxs-lookup"><span data-stu-id="fe7ea-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe7ea-108">GetReaderForFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe7ea-108">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="fe7ea-109">Meta veri arabirimi ve dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="fe7ea-110">[Istreamunmanagedciltçi:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) yönteminden daha kapsamlı bir arama sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe7ea-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe7ea-111">Requirements</span></span>  
 <span data-ttu-id="fe7ea-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fe7ea-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe7ea-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe7ea-113">See also</span></span>

- [<span data-ttu-id="fe7ea-114">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe7ea-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="fe7ea-115">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe7ea-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="fe7ea-116">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe7ea-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
