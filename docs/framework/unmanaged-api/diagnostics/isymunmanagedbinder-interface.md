---
description: 'Daha fazla bilgi edinin: ıstreamunmanagedciltçi arabirimi'
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
ms.openlocfilehash: 14ebccb028ab3388a8058dd05504c56a6df74c95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689930"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="eddd9-103">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eddd9-103">ISymUnmanagedBinder Interface</span></span>

<span data-ttu-id="eddd9-104">Yönetilmeyen kod için bir sembol cildi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eddd9-104">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eddd9-105">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="eddd9-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eddd9-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eddd9-106">Methods</span></span>  
  
|<span data-ttu-id="eddd9-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eddd9-107">Method</span></span>|<span data-ttu-id="eddd9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eddd9-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eddd9-109">GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eddd9-109">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="eddd9-110">Meta veri arabirimi ve bir dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) yapısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="eddd9-110">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="eddd9-111">GetReaderFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eddd9-111">GetReaderFromStream Method</span></span>](isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="eddd9-112">Meta veri arabirimi ve sembol deposunu içeren bir akış verildiğinde, verilen sembol deposundan hata ayıklama sembollerini okuyan doğru [ıstreamunmanagedreader](isymunmanagedreader-interface.md) yapısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="eddd9-112">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eddd9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eddd9-113">Requirements</span></span>  

 <span data-ttu-id="eddd9-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="eddd9-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eddd9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eddd9-115">See also</span></span>

- [<span data-ttu-id="eddd9-116">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eddd9-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="eddd9-117">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eddd9-117">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="eddd9-118">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eddd9-118">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
