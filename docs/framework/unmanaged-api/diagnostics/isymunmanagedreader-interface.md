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
ms.openlocfilehash: 9d3c05715ffb4f7a366e3b3c9951ab68477c5c32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561497"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="9f376-102">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f376-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="9f376-103">Belgeler, yöntemler ve değişkenler bir sembol deposundaki erişim sağlayan bir sembol okuyucu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9f376-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f376-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9f376-104">Methods</span></span>  
  
|<span data-ttu-id="9f376-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9f376-105">Method</span></span>|<span data-ttu-id="9f376-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f376-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f376-107">GetDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="9f376-108">Bir belgeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="9f376-108">Finds a document.</span></span>|  
|[<span data-ttu-id="9f376-109">GetDocuments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="9f376-110">Sembol deposu içerisinde tanımlanan tüm belgelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f376-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="9f376-111">GetDocumentVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="9f376-112">Belirtilen belge belirtilen sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="9f376-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="9f376-113">GetGlobalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="9f376-114">Tüm genel değişkenler döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f376-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="9f376-115">GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="9f376-116">Token metody verilen sembol okuyucu yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="9f376-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="9f376-117">GetMethodByVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="9f376-118">Bir sembol okuyucu yöntemi verilen token metody ve bir düzenleme ve kopyalama sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="9f376-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="9f376-119">GetMethodFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="9f376-120">Bir belge belirtilen konumda bir kesme noktası içeren yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f376-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="9f376-121">GetMethodsFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="9f376-122">Yöntemler, her biri bir belge belirtilen konumda bir kesme noktası içeren bir dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f376-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="9f376-123">GetMethodVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="9f376-124">Yöntem sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="9f376-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="9f376-125">GetNamespaces Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="9f376-126">Bu sembol deposundaki genel kapsamda tanımlanan ad alanları alır.</span><span class="sxs-lookup"><span data-stu-id="9f376-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="9f376-127">GetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="9f376-128">Özel bir öznitelik adı üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="9f376-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="9f376-129">GetSymbolStoreFileName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="9f376-130">Sembol deposundaki disk dosya adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f376-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="9f376-131">GetUserEntryPoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="9f376-132">Modül için kullanıcı giriş noktası olarak belirtilen yöntem varsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f376-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="9f376-133">GetVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="9f376-134">Bir yerel olmayan değişken adı ve üst verilen döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f376-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="9f376-135">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="9f376-136">Bu okuyucu modülü dosya adının yanı sıra, ile ilişkili meta verileri alma arabirimiyle sembol okuyucu başlatır.</span><span class="sxs-lookup"><span data-stu-id="9f376-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="9f376-137">ReplaceSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="9f376-138">Mevcut simge deposu delta sembol deposu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9f376-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="9f376-139">UpdateSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="9f376-140">Mevcut simge deposu delta sembol deposu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="9f376-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9f376-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f376-141">Requirements</span></span>  
 <span data-ttu-id="9f376-142">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9f376-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f376-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f376-143">See also</span></span>
- [<span data-ttu-id="9f376-144">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9f376-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="9f376-145">ISymUnmanagedReader2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f376-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
