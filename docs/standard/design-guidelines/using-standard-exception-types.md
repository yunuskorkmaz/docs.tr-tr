---
title: Standart özel durum türlerini kullanma
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: KrzysztofCwalina
ms.openlocfilehash: b947c7cce057c060b1ab5054d1227f5703ccbf89
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543912"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="6bbd0-102">Standart özel durum türlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="6bbd0-102">Using Standard Exception Types</span></span>
<span data-ttu-id="6bbd0-103">Bu bölümde, Framework ve bunların kullanım ayrıntılarını tarafından sağlanan standart özel durumlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="6bbd0-104">Listede olmadığı göre Hayır hepsine yer.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="6bbd0-105">Lütfen .NET Framework başvuru diğer Framework özel durum türlerinin kullanımı için belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="6bbd0-106">Özel durum ve SystemException</span><span class="sxs-lookup"><span data-stu-id="6bbd0-106">Exception and SystemException</span></span>  
 <span data-ttu-id="6bbd0-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> veya <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="6bbd0-108">**X DO NOT** catch `System.Exception` veya `System.SystemException` framework kodunda yeniden oluşturulması düşünmüyorsanız.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="6bbd0-109">**X AVOID** yakalama `System.Exception` veya `System.SystemException`, üst düzey özel durum işleyicileri dışındaki.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="6bbd0-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="6bbd0-110">ApplicationException</span></span>  
 <span data-ttu-id="6bbd0-111">**X DO NOT** throw veya öğesinden türetilen <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="6bbd0-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="6bbd0-112">InvalidOperationException</span></span>  
 <span data-ttu-id="6bbd0-113">**✓ DO** throw bir <xref:System.InvalidOperationException> nesne uygunsuz bir durumda ise.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="6bbd0-114">ArgumentException ArgumentNullException ve üretiliyor</span><span class="sxs-lookup"><span data-stu-id="6bbd0-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="6bbd0-115">**✓ DO** throw <xref:System.ArgumentException> ya da hatalı değişkenler üye aktarılırsa, alt türlerinden birini.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="6bbd0-116">En çok türetilen özel durum türü varsa tercih eder.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="6bbd0-117">**✓ DO** ayarlamak `ParamName` sınıfları birini atarken özelliği `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="6bbd0-118">Bu özellik, özel durum oluşturulmasına neden olan parametrenin adını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="6bbd0-119">Özellik oluşturucu aşırı yüklemeleri birini kullanarak ayarlanabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="6bbd0-120">**✓ DO** kullanmak `value` özellik ayarlayıcıları örtük değeri parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="6bbd0-121">NullReferenceException ve IndexOutOfRangeException AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="6bbd0-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="6bbd0-122">**X DO NOT** açıkça veya örtük throw herkese açık şekilde çağrılabilir izin vermek <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, veya <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="6bbd0-123">Bu özel durumlar ayrılmış ve yürütme altyapısı tarafından oluşturulur ve buna genellikle bir hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="6bbd0-124">Bağımsız değişken bu özel durumları atma önlemek için denetimi yapın.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="6bbd0-125">Bu özel durumları atma zaman içinde değişebileceğini yönteminizi uygulama ayrıntılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="6bbd0-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="6bbd0-126">StackOverflowException</span></span>  
 <span data-ttu-id="6bbd0-127">**X DO NOT** açıkça throw <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="6bbd0-128">Özel durum CLR tarafından yalnızca açıkça durum.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="6bbd0-129">**X DO NOT** catch `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="6bbd0-130">Rastgele yığını taşmaları saklanacaktır tutarlılığın yönetilen kod yazmak neredeyse imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="6bbd0-131">CLR yönetilmeyen bölümlerini, iyi tanımlanmış basamağa yığın taşmaları taşımak araştırmalarını kullanan yerine rastgele yığını taşmaları yedekleme göre tutarlı kalır.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="6bbd0-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="6bbd0-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="6bbd0-133">**X DO NOT** açıkça throw <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="6bbd0-134">Bu durum CLR altyapısı tarafından yalnızca durum sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="6bbd0-135">ComException SEHException ve ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="6bbd0-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="6bbd0-136">**X DO NOT** açıkça throw <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, ve <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="6bbd0-137">Bu özel durumların CLR altyapısı tarafından yalnızca durum üzeresiniz.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="6bbd0-138">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="6bbd0-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6bbd0-139">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="6bbd0-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bbd0-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bbd0-140">See also</span></span>

- [<span data-ttu-id="6bbd0-141">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6bbd0-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="6bbd0-142">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6bbd0-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
