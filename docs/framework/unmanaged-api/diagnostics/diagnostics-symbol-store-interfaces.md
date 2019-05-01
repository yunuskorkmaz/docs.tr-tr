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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fca7359888b8b73b2e1cf709ab708d71abf0db6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787900"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="d6269-102">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d6269-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="d6269-103">Bu konuda, bir hata ayıklayıcı tarafından kullanım için sembol bilgisi oluşturmak bir derleyiciyi etkinleştir yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d6269-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6269-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d6269-104">In This Section</span></span>  
 [<span data-ttu-id="d6269-105">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="d6269-106">Çalışan uygulamayı geçerli bağlama bilgilerini görüntülemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="d6269-107">IDebugAutoAttach Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="d6269-108">Hata ayıklayıcı sunucu çağrılan otomatik iliştirme için arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="d6269-109">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="d6269-110">Kaydetme ve bağlantı bildirim kaynağı kaydını kaldırmak için kullanılan yöntemler bildirir.</span><span class="sxs-lookup"><span data-stu-id="d6269-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="d6269-111">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="d6269-112">Havuz bildirim için yöntemleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="d6269-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="d6269-113">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="d6269-114">Bildirim filtreleri ayarlamak için bir yöntem bildirir.</span><span class="sxs-lookup"><span data-stu-id="d6269-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="d6269-115">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="d6269-116">Düzenle ve devam et özelliği için bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="d6269-117">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="d6269-118">Bu bir arabirimdir okuma tamamlayan [Isymunmanagedasyncmethodpropertieswriter arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d6269-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="d6269-119">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="d6269-120">İsteğe bağlı zaman uyumsuz yöntem bilgileri yöntemi sembol başına tanımlanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d6269-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="d6269-121">Açılan bir yöntemle kullanmanız gerekir (diğer bir deyişle, yapılan çağrılar arasında [OpenMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)ve [CloseMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="d6269-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="d6269-122">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="d6269-123">Yönetilmeyen kod için bir simge bağlayıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6269-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="d6269-124">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="d6269-125">Yönetilmeyen kod için bir simge bağlayıcı temsil eder ve genişleten `ISymUnmanagedBinder` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d6269-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="d6269-126">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="d6269-127">Yönetilmeyen kod için bir simge bağlayıcı temsil eder ve genişleten `ISymUnmanagedBinder` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d6269-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="d6269-128">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="d6269-129">Yönetilmeyen sabitleri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="d6269-130">ISymUnmanagedDispose Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="d6269-131">Yönetilmeyen kaynakları siler.</span><span class="sxs-lookup"><span data-stu-id="d6269-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="d6269-132">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="d6269-133">Bir sembol deposu tarafından başvurulan bir belgeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6269-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="d6269-134">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="d6269-135">Bir sembol deposu tarafından başvurulan bir belge için yazma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="d6269-136">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="d6269-137">Düzenle ve devam et özelliği için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="d6269-138">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6269-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="d6269-139">Sembol deposundaki bir yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6269-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="d6269-140">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="d6269-141">Bir ad alanı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6269-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="d6269-142">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="d6269-143">Belgeler, yöntemler ve değişkenler bir sembol deposundaki erişim sağlayan bir sembol okuyucu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6269-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="d6269-144">ISymUnmanagedReader2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6269-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="d6269-145">Bir sembol okuyucu yöntemi verilen token metody ve bir düzenleme ve kopyalama sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="d6269-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="d6269-146">ISymUnmanagedReaderSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="d6269-147">Sembol arama bilgilerini almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="d6269-148">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="d6269-149">Bir sözlü kapsamda bir yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6269-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="d6269-150">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6269-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="d6269-151">Bir sözcük kapsamı içindeki bir yöntemi temsil eder ve genişleten `ISymUnmanagedScope` arabirim yöntemleriyle kapsamında tanımlanmış sabitleri hakkında bilgi edinin...</span><span class="sxs-lookup"><span data-stu-id="d6269-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="d6269-152">ISymUnmanagedSourceServerModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="d6269-153">Kaynak sunucu verileri için bir modül sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="d6269-154">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="d6269-155">Arama yolu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="d6269-156">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="d6269-157">Bir parametre, yerel bir değişken veya bir alan gibi bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6269-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="d6269-158">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="d6269-159">Sembol yazıcıyı temsil eder ve belgeler, dizi noktaları, sözcük kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="d6269-160">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="d6269-161">Sembol yazıcıyı temsil eder ve belgeler, dizi noktaları, sözcük kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="d6269-162">Genişletir `ISymUnmanagedWriter` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d6269-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="d6269-163">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="d6269-164">Sembol yazıcıyı temsil eder ve belgeler, dizi noktaları, sözcük kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6269-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="d6269-165">Genişletir `ISymUnmanagedWriter` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d6269-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="d6269-166">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="d6269-167">Isymunmanagedwriter4 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d6269-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="d6269-168">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6269-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="d6269-169">Isymunmanagedwriter5 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d6269-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d6269-170">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d6269-170">Related Sections</span></span>  
 [<span data-ttu-id="d6269-171">Tanılama Simge Deposu Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d6269-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="d6269-172">Tanılama Simge Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="d6269-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="d6269-173">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d6269-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
