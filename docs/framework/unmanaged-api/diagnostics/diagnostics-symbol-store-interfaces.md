---
title: "Tanılama Sembol Deposu Arabirimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 50ef54c90609bf8ef1e3a943664daef95f50d926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="d4e71-102">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d4e71-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="d4e71-103">Bu konuda, bir hata ayıklayıcısı tarafından kullanılmak üzere sembol bilgileri oluşturmak bir derleyici etkinleştirmek yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4e71-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4e71-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d4e71-104">In This Section</span></span>  
 [<span data-ttu-id="d4e71-105">Ibindingdisplay arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="d4e71-106">Çalışan uygulama geçerli bağlama bilgilerini görüntüleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="d4e71-107">Idebugautoattach arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="d4e71-108">Bir sunucu çağrılan hata ayıklayıcı otomatik eklemek için arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="d4e71-109">Inotifyconnection2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="d4e71-110">Kaydetme ve bağlantı bildirim kaynağı kaydını kaldırmak için kullanılan yöntemler bildirir.</span><span class="sxs-lookup"><span data-stu-id="d4e71-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="d4e71-111">Inotifysink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="d4e71-112">Havuz bildirim için yöntemleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="d4e71-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="d4e71-113">Inotifysource2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="d4e71-114">Bildirim filtreleri ayarlamak için bir yöntem bildirir.</span><span class="sxs-lookup"><span data-stu-id="d4e71-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="d4e71-115">Isymencunmanagedmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="d4e71-116">Düzenle ve devam et özelliği için bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="d4e71-117">Isymunmanagedasyncmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="d4e71-118">Bu bir arabirimdir okuma tamamlayan [Isymunmanagedasyncmethodpropertieswriter arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d4e71-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="d4e71-119">Isymunmanagedasyncmethodpropertieswriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="d4e71-120">İsteğe bağlı zaman uyumsuz yöntem bilgileri yöntemi simge başına tanımlanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d4e71-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="d4e71-121">İle açılmış bir yöntem kullanmanız gerekir (diğer bir deyişle, yapılan çağrılar arasında [OpenMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)ve [CloseMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="d4e71-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="d4e71-122">Isymunmanagedbinder arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="d4e71-123">Yönetilmeyen kod için bir simge bağlayıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4e71-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="d4e71-124">Isymunmanagedbinder2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="d4e71-125">Yönetilmeyen kod için bir simge bağlayıcı temsil eder ve genişleten `ISymUnmanagedBinder` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d4e71-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="d4e71-126">Isymunmanagedbinder3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="d4e71-127">Yönetilmeyen kod için bir simge bağlayıcı temsil eder ve genişleten `ISymUnmanagedBinder` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d4e71-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="d4e71-128">Isymunmanagedconstant arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="d4e71-129">Yönetilmeyen sabitleri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="d4e71-130">Isymunmanageddispose arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="d4e71-131">Yönetilmeyen kaynakları siler.</span><span class="sxs-lookup"><span data-stu-id="d4e71-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="d4e71-132">Isymunmanageddocument arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="d4e71-133">Sembol deposu tarafından başvurulan bir belgeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4e71-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="d4e71-134">Isymunmanageddocumentwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="d4e71-135">Sembol deposu tarafından başvurulan bir belge için yazma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="d4e71-136">Isymunmanagedencupdate arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="d4e71-137">Düzenle ve devam et özelliği için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="d4e71-138">Isymunmanagedmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="d4e71-139">Sembol deposu içinde yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4e71-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="d4e71-140">Isymunmanagednamespace arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="d4e71-141">Bir ad alanı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4e71-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="d4e71-142">Isymunmanagedreader arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="d4e71-143">Belgeler, yöntemleri ve sembol deposu değişkenler erişim sağlayan bir simge okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4e71-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="d4e71-144">Isymunmanagedreader2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="d4e71-145">Verilen bir yöntem belirteci ve bir düzenleme ve kopyalama sürüm numarası bir simge okuyucu yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="d4e71-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="d4e71-146">Isymunmanagedreadersymbolsearchınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="d4e71-147">Sembol arama bilgilerini alma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="d4e71-148">Isymunmanagedscope arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="d4e71-149">Bir yöntem sözcük kapsamında temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4e71-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="d4e71-150">Isymunmanagedscope2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="d4e71-151">Bir sözcük kapsamı içinde bir yöntemi gösterir ve genişletir `ISymUnmanagedScope` arabirimi yöntemleriyle kapsamı içinde tanımlanan sabitleri hakkında bilgi edinin...</span><span class="sxs-lookup"><span data-stu-id="d4e71-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="d4e71-152">Isymunmanagedsourceservermodule arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="d4e71-153">Kaynak sunucu veriler için bir modül sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="d4e71-154">Isymunmanagedsymbolsearchınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="d4e71-155">Arama yolu hakkında bilgi edinme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="d4e71-156">Isymunmanagedvariable arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="d4e71-157">Bir parametre, yerel bir değişken ya da bir alan gibi bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4e71-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="d4e71-158">Isymunmanagedwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="d4e71-159">Sembol yazıcıyı temsil eder ve belgeleri, sıralama noktaları, sözcük kapsamlar ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="d4e71-160">Isymunmanagedwriter2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="d4e71-161">Sembol yazıcıyı temsil eder ve belgeleri, sıralama noktaları, sözcük kapsamlar ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="d4e71-162">Genişletir `ISymUnmanagedWriter` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d4e71-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="d4e71-163">Isymunmanagedwriter3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="d4e71-164">Sembol yazıcıyı temsil eder ve belgeleri, sıralama noktaları, sözcük kapsamlar ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e71-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="d4e71-165">Genişletir `ISymUnmanagedWriter` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d4e71-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="d4e71-166">Isymunmanagedwriter4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="d4e71-167">Isymunmanagedwriter4 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d4e71-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="d4e71-168">Isymunmanagedwriter5 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e71-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="d4e71-169">Isymunmanagedwriter5 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d4e71-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d4e71-170">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d4e71-170">Related Sections</span></span>  
 [<span data-ttu-id="d4e71-171">Tanılama sembol deposu numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="d4e71-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="d4e71-172">Tanılama sembol deposu yapıları</span><span class="sxs-lookup"><span data-stu-id="d4e71-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="d4e71-173">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d4e71-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
