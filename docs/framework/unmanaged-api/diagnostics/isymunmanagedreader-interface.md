---
title: ISymUnmanagedReader Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a78616ea1dccdf82c4e00d23d2ff630c98cb4e38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431909"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="45cd3-102">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45cd3-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="45cd3-103">Belgeler, yöntemleri ve sembol deposu değişkenler erişim sağlayan bir simge okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="45cd3-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45cd3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="45cd3-104">Methods</span></span>  
  
|<span data-ttu-id="45cd3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="45cd3-105">Method</span></span>|<span data-ttu-id="45cd3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45cd3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45cd3-107">GetDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="45cd3-108">Bir belge bulur.</span><span class="sxs-lookup"><span data-stu-id="45cd3-108">Finds a document.</span></span>|  
|[<span data-ttu-id="45cd3-109">GetDocuments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="45cd3-110">Sembol deposunda tanımlanan tüm belgeleri bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="45cd3-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="45cd3-111">GetDocumentVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="45cd3-112">Belirtilen belge belirtilen sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="45cd3-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="45cd3-113">GetGlobalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="45cd3-114">Tüm genel değişkenler döndürür.</span><span class="sxs-lookup"><span data-stu-id="45cd3-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="45cd3-115">GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="45cd3-116">Bir simge okuyucu yöntemi bir yöntem belirteci verilen alır.</span><span class="sxs-lookup"><span data-stu-id="45cd3-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="45cd3-117">GetMethodByVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="45cd3-118">Bir simge okuyucu yöntemi, verilen bir yöntem belirteci ve düzenleme ve kopyalama sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="45cd3-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="45cd3-119">GetMethodFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="45cd3-120">Belgede verilen konumunda kesme noktası içerdiğinden yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="45cd3-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="45cd3-121">GetMethodsFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="45cd3-122">Her biri bir belgede verilen konumunda kesme noktası içeren bir dizi yöntemleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="45cd3-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="45cd3-123">GetMethodVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="45cd3-124">Yöntem sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="45cd3-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="45cd3-125">GetNamespaces Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="45cd3-126">Bu simge deposundaki genel kapsamda tanımlanan ad alanları alır.</span><span class="sxs-lookup"><span data-stu-id="45cd3-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="45cd3-127">GetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="45cd3-128">Adını dayalı özel bir öznitelik alır.</span><span class="sxs-lookup"><span data-stu-id="45cd3-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="45cd3-129">GetSymbolStoreFileName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="45cd3-130">Sembol deposu disk üzerinde dosya adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="45cd3-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="45cd3-131">GetUserEntryPoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="45cd3-132">Modül için kullanıcı giriş noktası olarak belirtilen yöntem varsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="45cd3-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="45cd3-133">GetVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="45cd3-134">Kendi üst adı verilen bir yerel olmayan değişkeni döndürür.</span><span class="sxs-lookup"><span data-stu-id="45cd3-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="45cd3-135">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="45cd3-136">Bu okuyucu modülü dosya adı yanı sıra, ilişkili meta verileri alma arabirimi simgesi okuyucu başlatır.</span><span class="sxs-lookup"><span data-stu-id="45cd3-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="45cd3-137">ReplaceSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="45cd3-138">Varolan sembol deposu delta sembol deposu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="45cd3-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="45cd3-139">UpdateSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="45cd3-140">Varolan sembol deposu delta sembol deposu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="45cd3-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45cd3-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45cd3-141">Requirements</span></span>  
 <span data-ttu-id="45cd3-142">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="45cd3-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45cd3-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45cd3-143">See Also</span></span>  
 [<span data-ttu-id="45cd3-144">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="45cd3-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="45cd3-145">ISymUnmanagedReader2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cd3-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
