---
title: ISymUnmanagedBinder2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder2 Interface
helpviewer_keywords: ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c276f0abedf4ccab92770af649a8dd0afb6d39d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="cce25-102">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cce25-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="cce25-103">Yönetilmeyen kod için bir simge bağlayıcı temsil eder ve genişleten [Isymunmanagedbinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="cce25-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cce25-104">Güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyasını açmak için bir güvenlik riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cce25-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cce25-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cce25-105">Methods</span></span>  
  
|<span data-ttu-id="cce25-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cce25-106">Method</span></span>|<span data-ttu-id="cce25-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cce25-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cce25-108">GetReaderForFile2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="cce25-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="cce25-109">Bir meta veri arabirimi ve bir dosya adı doğru döndürür <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> modülü ile ilişkili hata ayıklama simgeleri okuma yapacak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="cce25-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="cce25-110">' Den daha kapsamlı bir arama sağlar [Isymunmanagedbinder::getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cce25-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cce25-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cce25-111">Requirements</span></span>  
 <span data-ttu-id="cce25-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cce25-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce25-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cce25-113">See Also</span></span>  
 [<span data-ttu-id="cce25-114">Tanılama sembol deposu arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cce25-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="cce25-115">Isymunmanagedbinder arabirimi</span><span class="sxs-lookup"><span data-stu-id="cce25-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="cce25-116">Isymunmanagedbinder3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="cce25-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
