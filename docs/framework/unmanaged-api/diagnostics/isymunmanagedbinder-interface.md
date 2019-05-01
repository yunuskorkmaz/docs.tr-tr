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
ms.openlocfilehash: b6d91f68ac737ce28cdbef926119bb3711bc1096
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940068"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="85716-102">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85716-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="85716-103">Yönetilmeyen kod için bir simge bağlayıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="85716-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85716-104">Bu, güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyası açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85716-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85716-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="85716-105">Methods</span></span>  
  
|<span data-ttu-id="85716-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="85716-106">Method</span></span>|<span data-ttu-id="85716-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85716-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85716-108">GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85716-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="85716-109">Meta veri arayüzü ve bir dosya adı, doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) modülle ilişkili hata ayıklama sembolleri okuyacaksa yapısı.</span><span class="sxs-lookup"><span data-stu-id="85716-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="85716-110">GetReaderFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85716-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="85716-111">Bir meta veri arabirimi ve sembol deposu içeren bir akış doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) hata ayıklama okuyacaksa yapısı belirli sembol deposundan simgeler.</span><span class="sxs-lookup"><span data-stu-id="85716-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85716-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85716-112">Requirements</span></span>  
 <span data-ttu-id="85716-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="85716-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85716-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85716-114">See also</span></span>

- [<span data-ttu-id="85716-115">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="85716-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="85716-116">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85716-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="85716-117">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85716-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
