---
description: 'Daha fazla bilgi edinin: ISymUnmanagedBinder2 Interface'
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
ms.openlocfilehash: 73847cdc9366ec18974fac261cbbad4d7dc6ccc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689891"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="a62dc-103">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a62dc-103">ISymUnmanagedBinder2 Interface</span></span>

<span data-ttu-id="a62dc-104">Yönetilmeyen kod için bir sembol cildi temsil eder ve [ıstreamunmanagedciltçi](isymunmanagedbinder-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="a62dc-104">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a62dc-105">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="a62dc-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a62dc-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a62dc-106">Methods</span></span>  
  
|<span data-ttu-id="a62dc-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a62dc-107">Method</span></span>|<span data-ttu-id="a62dc-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a62dc-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a62dc-109">GetReaderForFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a62dc-109">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="a62dc-110">Meta veri arabirimi ve dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a62dc-110">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="a62dc-111">[Istreamunmanagedciltçi:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) yönteminden daha kapsamlı bir arama sağlar.</span><span class="sxs-lookup"><span data-stu-id="a62dc-111">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a62dc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a62dc-112">Requirements</span></span>  

 <span data-ttu-id="a62dc-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a62dc-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62dc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a62dc-114">See also</span></span>

- [<span data-ttu-id="a62dc-115">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a62dc-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="a62dc-116">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a62dc-116">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="a62dc-117">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a62dc-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
