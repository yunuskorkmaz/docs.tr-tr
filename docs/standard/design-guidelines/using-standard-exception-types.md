---
title: Standart Özel Durum Türlerini Kullanma
description: .NET 'teki standart özel durum türleri hakkında bilgi edinin. SystemException, ApplicationException, ArgumentException, ComException ve daha fazlasını öğrenin.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: f95529eabd87d9ec7c379b9f790e039e1192ac53
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663063"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="22e6b-104">Standart Özel Durum Türlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="22e6b-104">Using Standard Exception Types</span></span>
<span data-ttu-id="22e6b-105">Bu bölümde, çerçevesi tarafından sunulan standart özel durumlar ve kullanımlarının ayrıntıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="22e6b-105">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="22e6b-106">Liste, ayrıntılı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="22e6b-106">The list is by no means exhaustive.</span></span> <span data-ttu-id="22e6b-107">Diğer Framework özel durum türlerinin kullanımı için lütfen .NET Framework başvuru belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="22e6b-107">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="22e6b-108">Özel durum ve SystemException</span><span class="sxs-lookup"><span data-stu-id="22e6b-108">Exception and SystemException</span></span>
 <span data-ttu-id="22e6b-109">❌<xref:System.Exception?displayProperty=nameWithType>Veya oluşturun <xref:System.SystemException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="22e6b-109">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="22e6b-110">❌`System.Exception` `System.SystemException` Yeniden oluşturma amacını taşımadığınız müddetçe, çerçeve kodunu yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="22e6b-110">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="22e6b-111">❌`System.Exception` `System.SystemException` En üst düzey özel durum işleyicileri dışında, yakalanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="22e6b-111">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="22e6b-112">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="22e6b-112">ApplicationException</span></span>
 <span data-ttu-id="22e6b-113">❌' İ throw veya türemeyin <xref:System.ApplicationException> .</span><span class="sxs-lookup"><span data-stu-id="22e6b-113">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="22e6b-114">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="22e6b-114">InvalidOperationException</span></span>
 <span data-ttu-id="22e6b-115"><xref:System.InvalidOperationException>nesne uygunsuz bir durumdaysa ✔️ oluşturun.</span><span class="sxs-lookup"><span data-stu-id="22e6b-115">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="22e6b-116">ArgumentException, ArgumentNullException ve ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="22e6b-116">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>
 <span data-ttu-id="22e6b-117"><xref:System.ArgumentException>bir üyeye hatalı bağımsız değişkenler geçirilmezse, ✔️ veya alt türlerinden birini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="22e6b-117">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="22e6b-118">Varsa, en çok türetilmiş özel durum türünü tercih edin.</span><span class="sxs-lookup"><span data-stu-id="22e6b-118">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="22e6b-119">✔️, alt `ParamName` sınıflarından birini oluştururken özelliğini ayarlayın `ArgumentException` .</span><span class="sxs-lookup"><span data-stu-id="22e6b-119">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="22e6b-120">Bu özellik, özel durumun oluşturulmasına neden olan parametrenin adını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="22e6b-120">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="22e6b-121">Özelliğin, Oluşturucu aşırı yüklerinden biri kullanılarak ayarlankullanılamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="22e6b-121">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="22e6b-122">`value`özellik ayarlayıcılarının örtük değer parametresinin adı için ✔️ kullanın.</span><span class="sxs-lookup"><span data-stu-id="22e6b-122">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="22e6b-123">NullReferenceException, IndexOutOfRangeException ve AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="22e6b-123">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>
 <span data-ttu-id="22e6b-124">❌Genel olarak çağrılabilir API 'Lerin açıkça veya örtük olarak,, veya olarak throw yapmasına izin vermeyin <xref:System.NullReferenceException> <xref:System.AccessViolationException> <xref:System.IndexOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="22e6b-124">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="22e6b-125">Bu özel durumlar, yürütme altyapısı tarafından ayrılmıştır ve oluşturulur ve çoğu durumda bir hata olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="22e6b-125">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="22e6b-126">Bağımsız değişken denetimini, bu özel durumların üretilmesini önlemek için yapın.</span><span class="sxs-lookup"><span data-stu-id="22e6b-126">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="22e6b-127">Bu özel durumları oluşturmak, zaman içinde değişebilir yönteminizin uygulama ayrıntılarını sunar.</span><span class="sxs-lookup"><span data-stu-id="22e6b-127">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="22e6b-128">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="22e6b-128">StackOverflowException</span></span>
 <span data-ttu-id="22e6b-129">❌Açık olarak throw <xref:System.StackOverflowException> .</span><span class="sxs-lookup"><span data-stu-id="22e6b-129">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="22e6b-130">Özel durum yalnızca CLR tarafından açıkça oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22e6b-130">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="22e6b-131">❌Yakalamayın `StackOverflowException` .</span><span class="sxs-lookup"><span data-stu-id="22e6b-131">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="22e6b-132">Rastgele yığın taşlarına sahip olan yönetilen kodu yazmak neredeyse imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="22e6b-132">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="22e6b-133">CLR 'nin yönetilmeyen parçaları, yığın dışına çıkmaları, rastgele yığın taşlarından yedeklenmek yerine iyi tanımlanmış konumlara taşımak için yoklamalar kullanılarak tutarlı kalır.</span><span class="sxs-lookup"><span data-stu-id="22e6b-133">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="22e6b-134">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="22e6b-134">OutOfMemoryException</span></span>
 <span data-ttu-id="22e6b-135">❌Açık olarak throw <xref:System.OutOfMemoryException> .</span><span class="sxs-lookup"><span data-stu-id="22e6b-135">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="22e6b-136">Bu özel durum yalnızca CLR altyapısı tarafından oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22e6b-136">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="22e6b-137">ComException, şehir özel durumu ve ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="22e6b-137">ComException, SEHException, and ExecutionEngineException</span></span>
 <span data-ttu-id="22e6b-138">❌Açık olarak <xref:System.Runtime.InteropServices.COMException> , <xref:System.ExecutionEngineException> , ve oluşturun <xref:System.Runtime.InteropServices.SEHException> .</span><span class="sxs-lookup"><span data-stu-id="22e6b-138">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="22e6b-139">Bu özel durumlar yalnızca CLR altyapısı tarafından atılır.</span><span class="sxs-lookup"><span data-stu-id="22e6b-139">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="22e6b-140">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="22e6b-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="22e6b-141">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="22e6b-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="22e6b-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22e6b-142">See also</span></span>

- [<span data-ttu-id="22e6b-143">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="22e6b-143">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="22e6b-144">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="22e6b-144">Design Guidelines for Exceptions</span></span>](exceptions.md)
