---
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
ms.openlocfilehash: e376544a9d428ce5110a7e38b92a8e830f574664
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725189"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="31393-102">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="31393-102">Diagnostics Symbol Store Interfaces</span></span>

<span data-ttu-id="31393-103">Bu konuda, bir derleyicinin hata ayıklayıcı tarafından kullanılmak üzere sembol bilgisi oluşturmasını sağlayan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31393-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31393-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="31393-104">In This Section</span></span>  

 [<span data-ttu-id="31393-105">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-105">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)  
 <span data-ttu-id="31393-106">Çalışan uygulamayla ilgili geçerli bağlama bilgilerini görüntüleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="31393-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="31393-107">IDebugAutoAttach Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-107">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)  
 <span data-ttu-id="31393-108">Sunucu tarafından çağrılan bir hata ayıklayıcı otomatik iliştirme arabirimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31393-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="31393-109">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-109">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)  
 <span data-ttu-id="31393-110">Bağlantı bildirim kaynağını kaydetme ve kaydını silme yöntemlerini bildirir.</span><span class="sxs-lookup"><span data-stu-id="31393-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="31393-111">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-111">INotifySink2 Interface</span></span>](inotifysink2-interface.md)  
 <span data-ttu-id="31393-112">Havuz bildirimi için yöntemler bildirir.</span><span class="sxs-lookup"><span data-stu-id="31393-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="31393-113">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)  
 <span data-ttu-id="31393-114">Bildirim filtrelerini ayarlamak için bir yöntem bildirir.</span><span class="sxs-lookup"><span data-stu-id="31393-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="31393-115">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="31393-116">Düzenle ve devam et özelliği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="31393-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="31393-117">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-117">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="31393-118">Bu arabirim, [ıvmunmanagedasyncmethodpropertieswriter arabirimini](isymunmanagedasyncmethodpropertieswriter-interface.md)tamamlayan okuma işlemi.</span><span class="sxs-lookup"><span data-stu-id="31393-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="31393-119">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="31393-120">Yöntem simgesi başına isteğe bağlı zaman uyumsuz yöntem bilgilerinin tanımına izin verir.</span><span class="sxs-lookup"><span data-stu-id="31393-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="31393-121">, Bir açık yöntemle kullanılmalıdır (diğer bir deyişle, [OpenMethod yöntemi](isymunmanagedwriter-openmethod-method.md)ve [CloseMethod yöntemi](isymunmanagedwriter-closemethod-method.md)çağrıları arasında).</span><span class="sxs-lookup"><span data-stu-id="31393-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="31393-122">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-122">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)  
 <span data-ttu-id="31393-123">Yönetilmeyen kod için bir sembol cildi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="31393-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="31393-124">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-124">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="31393-125">Yönetilmeyen kod için bir sembol cildi temsil eder ve arabirimi genişletir `ISymUnmanagedBinder` .</span><span class="sxs-lookup"><span data-stu-id="31393-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="31393-126">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-126">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="31393-127">Yönetilmeyen kod için bir sembol cildi temsil eder ve arabirimi genişletir `ISymUnmanagedBinder` .</span><span class="sxs-lookup"><span data-stu-id="31393-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="31393-128">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-128">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)  
 <span data-ttu-id="31393-129">Yönetilmeyen sabitlere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="31393-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="31393-130">ISymUnmanagedDispose Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-130">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)  
 <span data-ttu-id="31393-131">Yönetilmeyen kaynakları ortadan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="31393-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="31393-132">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-132">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)  
 <span data-ttu-id="31393-133">Bir sembol deposu tarafından başvurulan bir belgeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="31393-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="31393-134">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-134">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="31393-135">Sembol deposu tarafından başvurulan bir belgeye yazmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="31393-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="31393-136">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-136">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="31393-137">Düzenle ve devam et özelliği için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="31393-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="31393-138">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-138">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)  
 <span data-ttu-id="31393-139">Sembol deposu içindeki bir yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="31393-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="31393-140">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-140">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)  
 <span data-ttu-id="31393-141">Bir ad alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="31393-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="31393-142">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-142">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)  
 <span data-ttu-id="31393-143">Bir sembol deposu içindeki belgelere, yöntemlere ve değişkenlere erişim sağlayan bir sembol okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="31393-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="31393-144">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-144">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)  
 <span data-ttu-id="31393-145">Bir yöntem belirteci ve bir düzenleme ve kopyalama sürümü numarası verilen bir sembol okuyucu yöntemini alır.</span><span class="sxs-lookup"><span data-stu-id="31393-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="31393-146">ISymUnmanagedReaderSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="31393-147">Sembol arama bilgilerini alan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="31393-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="31393-148">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-148">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)  
 <span data-ttu-id="31393-149">Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="31393-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="31393-150">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-150">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)  
 <span data-ttu-id="31393-151">Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder ve `ISymUnmanagedScope` arabirimi, kapsam içinde tanımlanan sabitler hakkında bilgi alan yöntemlerle genişletir.</span><span class="sxs-lookup"><span data-stu-id="31393-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="31393-152">ISymUnmanagedSourceServerModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-152">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="31393-153">Bir modül için kaynak sunucu verisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="31393-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="31393-154">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="31393-155">Arama yolu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="31393-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="31393-156">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-156">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)  
 <span data-ttu-id="31393-157">Bir parametre, yerel değişken veya bir alan gibi bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="31393-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="31393-158">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-158">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)  
 <span data-ttu-id="31393-159">Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="31393-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="31393-160">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-160">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="31393-161">Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="31393-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="31393-162">Arabirimini genişletir `ISymUnmanagedWriter` .</span><span class="sxs-lookup"><span data-stu-id="31393-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="31393-163">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-163">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="31393-164">Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="31393-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="31393-165">Arabirimini genişletir `ISymUnmanagedWriter` .</span><span class="sxs-lookup"><span data-stu-id="31393-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="31393-166">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-166">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="31393-167">ISymUnmanagedWriter4 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="31393-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="31393-168">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31393-168">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="31393-169">ISymUnmanagedWriter5 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="31393-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="31393-170">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="31393-170">Related Sections</span></span>  

 [<span data-ttu-id="31393-171">Tanılama Sembol Deposu Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="31393-171">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="31393-172">Tanılama Sembol Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="31393-172">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="31393-173">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="31393-173">Debugging</span></span>](../debugging/index.md)
