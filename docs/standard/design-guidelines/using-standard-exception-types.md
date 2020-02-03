---
title: Standart Özel Durum Türlerini Kullanma
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743546"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="1805f-102">Standart Özel Durum Türlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="1805f-102">Using Standard Exception Types</span></span>
<span data-ttu-id="1805f-103">Bu bölümde, çerçevesi tarafından sunulan standart özel durumlar ve kullanımlarının ayrıntıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1805f-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="1805f-104">Liste, ayrıntılı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1805f-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="1805f-105">Diğer Framework özel durum türlerinin kullanımı için lütfen .NET Framework başvuru belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="1805f-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="1805f-106">Özel durum ve SystemException</span><span class="sxs-lookup"><span data-stu-id="1805f-106">Exception and SystemException</span></span>
 <span data-ttu-id="1805f-107">❌ <xref:System.Exception?displayProperty=nameWithType> veya <xref:System.SystemException?displayProperty=nameWithType>oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="1805f-107">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="1805f-108">❌, yeniden oluşturma amacını belirtmedikçe Framework kodunda `System.Exception` veya `System.SystemException` yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="1805f-108">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="1805f-109">❌, üst düzey özel durum işleyicileri dışında `System.Exception` veya `System.SystemException`yakalanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="1805f-109">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="1805f-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="1805f-110">ApplicationException</span></span>
 <span data-ttu-id="1805f-111">❌ <xref:System.ApplicationException>oluşturmaz veya türemeyin.</span><span class="sxs-lookup"><span data-stu-id="1805f-111">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="1805f-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="1805f-112">InvalidOperationException</span></span>
 <span data-ttu-id="1805f-113">✔️, nesne uygunsuz bir durumdaysa <xref:System.InvalidOperationException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1805f-113">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="1805f-114">ArgumentException, ArgumentNullException ve ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="1805f-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>
 <span data-ttu-id="1805f-115">bir üyeye hatalı bağımsız değişkenler geçirilirse ✔️ <xref:System.ArgumentException> veya alt türlerinden birini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1805f-115">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="1805f-116">Varsa, en çok türetilmiş özel durum türünü tercih edin.</span><span class="sxs-lookup"><span data-stu-id="1805f-116">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="1805f-117">✔️ `ArgumentException`alt sınıflarından birini oluştururken `ParamName` özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1805f-117">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="1805f-118">Bu özellik, özel durumun oluşturulmasına neden olan parametrenin adını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1805f-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="1805f-119">Özelliğin, Oluşturucu aşırı yüklerinden biri kullanılarak ayarlankullanılamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1805f-119">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="1805f-120">✔️ Özellik ayarlayıcılarının örtük değer parametresinin adı için `value` kullanın.</span><span class="sxs-lookup"><span data-stu-id="1805f-120">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="1805f-121">NullReferenceException, IndexOutOfRangeException ve AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="1805f-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>
 <span data-ttu-id="1805f-122">❌, genel olarak çağrılabilir API 'Lerin <xref:System.NullReferenceException>, <xref:System.AccessViolationException>veya <xref:System.IndexOutOfRangeException>açıkça veya örtük olarak throw yapmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="1805f-122">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="1805f-123">Bu özel durumlar, yürütme altyapısı tarafından ayrılmıştır ve oluşturulur ve çoğu durumda bir hata olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1805f-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="1805f-124">Bağımsız değişken denetimini, bu özel durumların üretilmesini önlemek için yapın.</span><span class="sxs-lookup"><span data-stu-id="1805f-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="1805f-125">Bu özel durumları oluşturmak, zaman içinde değişebilir yönteminizin uygulama ayrıntılarını sunar.</span><span class="sxs-lookup"><span data-stu-id="1805f-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="1805f-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="1805f-126">StackOverflowException</span></span>
 <span data-ttu-id="1805f-127">❌ açıkça <xref:System.StackOverflowException>oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="1805f-127">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="1805f-128">Özel durum yalnızca CLR tarafından açıkça oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1805f-128">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="1805f-129">❌ `StackOverflowException`yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="1805f-129">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="1805f-130">Rastgele yığın taşlarına sahip olan yönetilen kodu yazmak neredeyse imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="1805f-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="1805f-131">CLR 'nin yönetilmeyen parçaları, yığın dışına çıkmaları, rastgele yığın taşlarından yedeklenmek yerine iyi tanımlanmış konumlara taşımak için yoklamalar kullanılarak tutarlı kalır.</span><span class="sxs-lookup"><span data-stu-id="1805f-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="1805f-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="1805f-132">OutOfMemoryException</span></span>
 <span data-ttu-id="1805f-133">❌ açıkça <xref:System.OutOfMemoryException>oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="1805f-133">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="1805f-134">Bu özel durum yalnızca CLR altyapısı tarafından oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1805f-134">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="1805f-135">ComException, şehir özel durumu ve ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="1805f-135">ComException, SEHException, and ExecutionEngineException</span></span>
 <span data-ttu-id="1805f-136">❌ açıkça <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>ve <xref:System.Runtime.InteropServices.SEHException>oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="1805f-136">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="1805f-137">Bu özel durumlar yalnızca CLR altyapısı tarafından atılır.</span><span class="sxs-lookup"><span data-stu-id="1805f-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="1805f-138">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="1805f-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1805f-139">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="1805f-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1805f-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1805f-140">See also</span></span>

- [<span data-ttu-id="1805f-141">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1805f-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="1805f-142">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1805f-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
