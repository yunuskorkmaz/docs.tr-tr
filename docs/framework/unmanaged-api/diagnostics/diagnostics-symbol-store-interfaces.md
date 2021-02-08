---
description: 'Daha fazla bilgi edinin: Tanılama sembol deposu arabirimleri'
title: Tanılama Sembol Deposu Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: 253a6e5eaa97c91332bca62f8fc47ad2945bf741
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800441"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="17d0d-103">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="17d0d-103">Diagnostics Symbol Store Interfaces</span></span>

<span data-ttu-id="17d0d-104">Bu konuda, bir derleyicinin hata ayıklayıcı tarafından kullanılmak üzere sembol bilgisi oluşturmasını sağlayan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="17d0d-104">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17d0d-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="17d0d-105">In This Section</span></span>  

 [<span data-ttu-id="17d0d-106">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-106">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)  
 <span data-ttu-id="17d0d-107">Çalışan uygulamayla ilgili geçerli bağlama bilgilerini görüntüleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-107">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="17d0d-108">IDebugAutoAttach Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-108">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)  
 <span data-ttu-id="17d0d-109">Sunucu tarafından çağrılan bir hata ayıklayıcı otomatik iliştirme arabirimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-109">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="17d0d-110">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-110">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)  
 <span data-ttu-id="17d0d-111">Bağlantı bildirim kaynağını kaydetme ve kaydını silme yöntemlerini bildirir.</span><span class="sxs-lookup"><span data-stu-id="17d0d-111">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="17d0d-112">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-112">INotifySink2 Interface</span></span>](inotifysink2-interface.md)  
 <span data-ttu-id="17d0d-113">Havuz bildirimi için yöntemler bildirir.</span><span class="sxs-lookup"><span data-stu-id="17d0d-113">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="17d0d-114">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)  
 <span data-ttu-id="17d0d-115">Bildirim filtrelerini ayarlamak için bir yöntem bildirir.</span><span class="sxs-lookup"><span data-stu-id="17d0d-115">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="17d0d-116">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-116">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="17d0d-117">Düzenle ve devam et özelliği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-117">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="17d0d-118">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-118">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="17d0d-119">Bu arabirim, [ıvmunmanagedasyncmethodpropertieswriter arabirimini](isymunmanagedasyncmethodpropertieswriter-interface.md)tamamlayan okuma işlemi.</span><span class="sxs-lookup"><span data-stu-id="17d0d-119">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="17d0d-120">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-120">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="17d0d-121">Yöntem simgesi başına isteğe bağlı zaman uyumsuz yöntem bilgilerinin tanımına izin verir.</span><span class="sxs-lookup"><span data-stu-id="17d0d-121">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="17d0d-122">, Bir açık yöntemle kullanılmalıdır (diğer bir deyişle, [OpenMethod yöntemi](isymunmanagedwriter-openmethod-method.md)ve [CloseMethod yöntemi](isymunmanagedwriter-closemethod-method.md)çağrıları arasında).</span><span class="sxs-lookup"><span data-stu-id="17d0d-122">Must use with an opened method (that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="17d0d-123">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-123">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)  
 <span data-ttu-id="17d0d-124">Yönetilmeyen kod için bir sembol cildi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17d0d-124">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="17d0d-125">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-125">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="17d0d-126">Yönetilmeyen kod için bir sembol cildi temsil eder ve arabirimi genişletir `ISymUnmanagedBinder` .</span><span class="sxs-lookup"><span data-stu-id="17d0d-126">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="17d0d-127">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-127">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="17d0d-128">Yönetilmeyen kod için bir sembol cildi temsil eder ve arabirimi genişletir `ISymUnmanagedBinder` .</span><span class="sxs-lookup"><span data-stu-id="17d0d-128">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="17d0d-129">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-129">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)  
 <span data-ttu-id="17d0d-130">Yönetilmeyen sabitlere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-130">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="17d0d-131">ISymUnmanagedDispose Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-131">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)  
 <span data-ttu-id="17d0d-132">Yönetilmeyen kaynakları ortadan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="17d0d-132">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="17d0d-133">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-133">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)  
 <span data-ttu-id="17d0d-134">Bir sembol deposu tarafından başvurulan bir belgeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17d0d-134">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="17d0d-135">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-135">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="17d0d-136">Sembol deposu tarafından başvurulan bir belgeye yazmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-136">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="17d0d-137">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-137">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="17d0d-138">Düzenle ve devam et özelliği için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-138">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="17d0d-139">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-139">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)  
 <span data-ttu-id="17d0d-140">Sembol deposu içindeki bir yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17d0d-140">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="17d0d-141">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-141">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)  
 <span data-ttu-id="17d0d-142">Bir ad alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17d0d-142">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="17d0d-143">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-143">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)  
 <span data-ttu-id="17d0d-144">Bir sembol deposu içindeki belgelere, yöntemlere ve değişkenlere erişim sağlayan bir sembol okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17d0d-144">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="17d0d-145">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-145">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)  
 <span data-ttu-id="17d0d-146">Bir yöntem belirteci ve bir düzenleme ve kopyalama sürümü numarası verilen bir sembol okuyucu yöntemini alır.</span><span class="sxs-lookup"><span data-stu-id="17d0d-146">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="17d0d-147">ISymUnmanagedReaderSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-147">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="17d0d-148">Sembol arama bilgilerini alan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-148">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="17d0d-149">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-149">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)  
 <span data-ttu-id="17d0d-150">Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17d0d-150">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="17d0d-151">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-151">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)  
 <span data-ttu-id="17d0d-152">Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder ve `ISymUnmanagedScope` arabirimi, kapsam içinde tanımlanan sabitler hakkında bilgi alan yöntemlerle genişletir.</span><span class="sxs-lookup"><span data-stu-id="17d0d-152">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="17d0d-153">ISymUnmanagedSourceServerModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-153">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="17d0d-154">Bir modül için kaynak sunucu verisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-154">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="17d0d-155">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-155">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="17d0d-156">Arama yolu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-156">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="17d0d-157">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-157">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)  
 <span data-ttu-id="17d0d-158">Bir parametre, yerel değişken veya bir alan gibi bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17d0d-158">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="17d0d-159">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-159">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)  
 <span data-ttu-id="17d0d-160">Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-160">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="17d0d-161">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-161">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="17d0d-162">Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-162">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="17d0d-163">Arabirimini genişletir `ISymUnmanagedWriter` .</span><span class="sxs-lookup"><span data-stu-id="17d0d-163">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="17d0d-164">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-164">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="17d0d-165">Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0d-165">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="17d0d-166">Arabirimini genişletir `ISymUnmanagedWriter` .</span><span class="sxs-lookup"><span data-stu-id="17d0d-166">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="17d0d-167">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-167">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="17d0d-168">ISymUnmanagedWriter4 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="17d0d-168">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="17d0d-169">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17d0d-169">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="17d0d-170">ISymUnmanagedWriter5 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="17d0d-170">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="17d0d-171">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="17d0d-171">Related Sections</span></span>  

 [<span data-ttu-id="17d0d-172">Tanılama Sembol Deposu Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="17d0d-172">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="17d0d-173">Tanılama Sembol Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="17d0d-173">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="17d0d-174">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="17d0d-174">Debugging</span></span>](../debugging/index.md)
