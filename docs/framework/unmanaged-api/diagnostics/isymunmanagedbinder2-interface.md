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
ms.openlocfilehash: 8a4fbb40ec2426d000628fbd6d5f0241d3152c18
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441675"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="2c2aa-102">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c2aa-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="2c2aa-103">Yönetilmeyen kod için bir sembol cildi temsil eder ve [ıstreamunmanagedciltçi](isymunmanagedbinder-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2c2aa-104">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c2aa-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2c2aa-105">Methods</span></span>  
  
|<span data-ttu-id="2c2aa-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2c2aa-106">Method</span></span>|<span data-ttu-id="2c2aa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c2aa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c2aa-108">GetReaderForFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c2aa-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="2c2aa-109">Meta veri arabirimi ve dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="2c2aa-110">[Istreamunmanagedciltçi:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) yönteminden daha kapsamlı bir arama sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c2aa-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c2aa-111">Requirements</span></span>  
 <span data-ttu-id="2c2aa-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2c2aa-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c2aa-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-113">See also</span></span>

- [<span data-ttu-id="2c2aa-114">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2c2aa-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="2c2aa-115">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c2aa-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="2c2aa-116">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c2aa-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
