---
title: ISymUnmanagedReader Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader
helpviewer_keywords: ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e8daea11292cb37deb8e956e6a666c14579fbfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="fa133-102">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa133-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="fa133-103">Belgeler, yöntemleri ve sembol deposu değişkenler erişim sağlayan bir simge okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fa133-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa133-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa133-104">Methods</span></span>  
  
|<span data-ttu-id="fa133-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fa133-105">Method</span></span>|<span data-ttu-id="fa133-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa133-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa133-107">GetDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="fa133-108">Bir belge bulur.</span><span class="sxs-lookup"><span data-stu-id="fa133-108">Finds a document.</span></span>|  
|[<span data-ttu-id="fa133-109">GetDocuments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="fa133-110">Sembol deposunda tanımlanan tüm belgeleri bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa133-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="fa133-111">GetDocumentVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="fa133-112">Belirtilen belge belirtilen sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="fa133-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="fa133-113">GetGlobalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="fa133-114">Tüm genel değişkenler döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa133-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="fa133-115">GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="fa133-116">Bir simge okuyucu yöntemi bir yöntem belirteci verilen alır.</span><span class="sxs-lookup"><span data-stu-id="fa133-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="fa133-117">GetMethodByVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="fa133-118">Bir simge okuyucu yöntemi, verilen bir yöntem belirteci ve düzenleme ve kopyalama sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="fa133-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="fa133-119">GetMethodFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="fa133-120">Belgede verilen konumunda kesme noktası içerdiğinden yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa133-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="fa133-121">GetMethodsFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="fa133-122">Her biri bir belgede verilen konumunda kesme noktası içeren bir dizi yöntemleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa133-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="fa133-123">GetMethodVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="fa133-124">Yöntem sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="fa133-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="fa133-125">GetNamespaces Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="fa133-126">Bu simge deposundaki genel kapsamda tanımlanan ad alanları alır.</span><span class="sxs-lookup"><span data-stu-id="fa133-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="fa133-127">GetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="fa133-128">Adını dayalı özel bir öznitelik alır.</span><span class="sxs-lookup"><span data-stu-id="fa133-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="fa133-129">GetSymbolStoreFileName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="fa133-130">Sembol deposu disk üzerinde dosya adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa133-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="fa133-131">GetUserEntryPoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="fa133-132">Modül için kullanıcı giriş noktası olarak belirtilen yöntem varsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa133-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="fa133-133">GetVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="fa133-134">Kendi üst adı verilen bir yerel olmayan değişkeni döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa133-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="fa133-135">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="fa133-136">Bu okuyucu modülü dosya adı yanı sıra, ilişkili meta verileri alma arabirimi simgesi okuyucu başlatır.</span><span class="sxs-lookup"><span data-stu-id="fa133-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="fa133-137">ReplaceSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="fa133-138">Varolan sembol deposu delta sembol deposu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="fa133-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="fa133-139">UpdateSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="fa133-140">Varolan sembol deposu delta sembol deposu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="fa133-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa133-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa133-141">Requirements</span></span>  
 <span data-ttu-id="fa133-142">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fa133-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa133-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa133-143">See Also</span></span>  
 [<span data-ttu-id="fa133-144">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fa133-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="fa133-145">ISymUnmanagedReader2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa133-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
