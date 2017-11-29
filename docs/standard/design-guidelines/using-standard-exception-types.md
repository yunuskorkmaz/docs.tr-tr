---
title: "Standart özel durum türleri kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 91cd9a03ad1acf61681ecfad0edb061802c4362c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="7aa3f-102">Standart özel durum türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="7aa3f-102">Using Standard Exception Types</span></span>
<span data-ttu-id="7aa3f-103">Bu bölümde Framework ve bunların kullanım ayrıntılarını tarafından sağlanan standart özel durumlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="7aa3f-104">Halinde kapsamlı listesidir.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="7aa3f-105">Lütfen .NET Framework başvuru diğer Framework özel durum türleri kullanım için belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="7aa3f-106">Özel durum ve SystemException</span><span class="sxs-lookup"><span data-stu-id="7aa3f-106">Exception and SystemException</span></span>  
 <span data-ttu-id="7aa3f-107">**X yok** throw <xref:System.Exception?displayProperty=nameWithType> veya <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="7aa3f-108">**X yok** catch `System.Exception` veya `System.SystemException` framework kodunda yeniden oluşturulması düşünmüyorsanız.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="7aa3f-109">**KAÇININ x** yakalama `System.Exception` veya `System.SystemException`, üst düzey özel durum işleyicileri dışındaki.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="7aa3f-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="7aa3f-110">ApplicationException</span></span>  
 <span data-ttu-id="7aa3f-111">**X yok** throw veya öğesinden türetilen <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="7aa3f-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="7aa3f-112">InvalidOperationException</span></span>  
 <span data-ttu-id="7aa3f-113">**✓ YAPMAK** throw bir <xref:System.InvalidOperationException> nesne uygunsuz bir durumda ise.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="7aa3f-114">ArgumentException, ArgumentNullException ve ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="7aa3f-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="7aa3f-115">**✓ YAPMAK** throw <xref:System.ArgumentException> ya da hatalı değişkenler üye aktarılırsa, alt türlerinden birini.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="7aa3f-116">En çok türetilen özel durum türü varsa tercih eder.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="7aa3f-117">**✓ YAPMAK** ayarlamak `ParamName` sınıfları birini atarken özelliği `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="7aa3f-118">Bu özellik, özel durum oluşturulmasına neden parametre adını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="7aa3f-119">Özelliği Oluşturucusu aşırı birini kullanarak ayarlanabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="7aa3f-120">**✓ YAPMAK** kullanmak `value` özellik ayarlayıcıları örtük değeri parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="7aa3f-121">NullReferenceException, IndexOutOfRangeException ve AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="7aa3f-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="7aa3f-122">**X yok** açıkça veya örtük throw herkese açık şekilde çağrılabilir izin vermek <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, veya <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="7aa3f-123">Bu özel durumlar ayrılmış ve yürütme altyapısı tarafından oluşturulur ve buna genellikle bir hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="7aa3f-124">Bu özel durumları atma önlemek için denetimi bağımsız değişkeni yapın.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="7aa3f-125">Bu özel durumları atma zaman içinde değişebilir yönteminizi uygulama ayrıntılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="7aa3f-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="7aa3f-126">StackOverflowException</span></span>  
 <span data-ttu-id="7aa3f-127">**X yok** açıkça throw <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="7aa3f-128">Özel yalnızca CLR tarafından açıkça durum.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="7aa3f-129">**X yok** catch `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="7aa3f-130">Rastgele yığını taşmaları varlığında tutarlılığın yönetilen kod yazmaya neredeyse mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="7aa3f-131">CLR yönetilmeyen bölümlerini araştırmalar yığını iyi tanımlanmış basamağa taşar taşımak için yerine kullanarak rasgele yığını taşmaları yedekleme tutarlı kalır.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="7aa3f-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="7aa3f-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="7aa3f-133">**X yok** açıkça throw <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="7aa3f-134">Bu durum yalnızca CLR altyapısı tarafından oluşturulan olmaktır.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="7aa3f-135">ComException, SEHException ve ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="7aa3f-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="7aa3f-136">**X yok** açıkça throw <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, ve <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="7aa3f-137">Bu özel durumlar, yalnızca CLR altyapısı tarafından oluşturulan üzeresiniz.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="7aa3f-138">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="7aa3f-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7aa3f-139">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="7aa3f-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aa3f-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-140">See Also</span></span>  
 [<span data-ttu-id="7aa3f-141">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="7aa3f-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="7aa3f-142">Özel durumlar için tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="7aa3f-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
