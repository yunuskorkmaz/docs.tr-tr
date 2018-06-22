---
title: İşleme ve .NET özel durumları atma
ms.date: 06/19/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET], exceptions
- exceptions [.NET], throwing
- exceptions [.NET]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a278940528966e32646a3551b4c133223de9746e
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298350"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="931c2-102">İşleme ve .NET özel durumları atma</span><span class="sxs-lookup"><span data-stu-id="931c2-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="931c2-103">Uygulamaları tutarlı bir şekilde yürütme sırasında oluşan hataları ele kurabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="931c2-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="931c2-104">.NET uygulamaları hataların Tekdüzen şekilde bildirmek için bir model sağlar: .NET işlemlerini özel durumları atma hatası belirtin.</span><span class="sxs-lookup"><span data-stu-id="931c2-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="931c2-105">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="931c2-105">Exceptions</span></span>

<span data-ttu-id="931c2-106">Herhangi bir hata koşulu veya çalışan bir program tarafından karşılaşılan beklenmeyen davranışları bir özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="931c2-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="931c2-107">Kodunuzu veya (gibi paylaşılan bir kitaplık) çağıran kodu, kullanılamayan işletim sistem kaynakları, çalışma zamanı (doğrulanamayan kodu gibi) karşılaştığında beklenmeyen koşullar ve benzeri bir hata nedeniyle durumlar.</span><span class="sxs-lookup"><span data-stu-id="931c2-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on.</span></span> <span data-ttu-id="931c2-108">Uygulamanızı bazı Bu koşullar, ancak diğer kurtarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="931c2-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="931c2-109">Çoğu uygulama özel durumları kurtarabilirsiniz rağmen çoğu çalışma zamanı özel durumları kurtaramazsınız.</span><span class="sxs-lookup"><span data-stu-id="931c2-109">Although you can recover from most application exceptions, you can't recover from most runtime exceptions.</span></span>

<span data-ttu-id="931c2-110">.NET içinde öğesinden devralan bir nesne istisnadır <xref:System.Exception?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="931c2-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="931c2-111">Bir sorun oluştuğu bir alanından kod bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="931c2-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="931c2-112">Özel durum yığını uygulama, işleme veya program sonlandırır kadar geçirilir.</span><span class="sxs-lookup"><span data-stu-id="931c2-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="931c2-113">Özel durumlar geleneksel hata işleme yöntemlerini karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="931c2-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="931c2-114">Geleneksel olarak, bir dil hata işleme modeli hataları algılama ve bunlar için işleyiciler bulma dil benzersiz şekilde veya işletim sistemi tarafından sağlanan hata işleme mekanizması dayanıyordu.</span><span class="sxs-lookup"><span data-stu-id="931c2-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="931c2-115">Özel durum işleme .NET uygulayan yol aşağıdaki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="931c2-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="931c2-116">Özel durum atma ve işleme .NET programlama dilleri için aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="931c2-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="931c2-117">Özel durum işleme için belirli bir dili sözdizimi gerektirmez, ancak kendi sözdizimi tanımlamak her bir dilin verir.</span><span class="sxs-lookup"><span data-stu-id="931c2-117">Doesn't require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="931c2-118">Özel işlem ve hatta makine sınırları içinde durum.</span><span class="sxs-lookup"><span data-stu-id="931c2-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="931c2-119">Özel durum işleme kod program güvenilirliğini artırmak için uygulamaya eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="931c2-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="931c2-120">Özel durumlar hata bildirimi, dönüş kodları gibi diğer yöntemleri avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="931c2-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="931c2-121">Bir özel durum ve işlemek yok, çalışma zamanı uygulamanızı sona erdiğinden hataları gözden kaçan geçmez.</span><span class="sxs-lookup"><span data-stu-id="931c2-121">Failures don't go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="931c2-122">Geçersiz değerler denetlemek için bir hata dönüş kodu için başarısız kod sonucunda sistemi aracılığıyla yayılmaya devam yok.</span><span class="sxs-lookup"><span data-stu-id="931c2-122">Invalid values don't continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span>

## <a name="common-exceptions"></a><span data-ttu-id="931c2-123">Genel özel durumlar</span><span class="sxs-lookup"><span data-stu-id="931c2-123">Common exceptions</span></span>

<span data-ttu-id="931c2-124">Aşağıdaki tabloda ortak bazı özel durumlar ne bunlara neden olabilecek örnekleri ile listeler.</span><span class="sxs-lookup"><span data-stu-id="931c2-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="931c2-125">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="931c2-125">Exception type</span></span> | <span data-ttu-id="931c2-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="931c2-126">Description</span></span> | <span data-ttu-id="931c2-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="931c2-127">Example</span></span> |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | <span data-ttu-id="931c2-128">Tüm özel durumlar için temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="931c2-128">Base class for all exceptions.</span></span> | <span data-ttu-id="931c2-129">Hiçbiri (Bu özel durumun türetilmiş bir sınıf kullanın).</span><span class="sxs-lookup"><span data-stu-id="931c2-129">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <span data-ttu-id="931c2-130">Çalışma zamanı tarafından yalnızca bir dizi yanlış sıralandığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="931c2-130">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="931c2-131">Geçerli aralığın dışında bir dizi dizin oluşturma:</span><span class="sxs-lookup"><span data-stu-id="931c2-131">Indexing an array outside its valid range:</span></span> <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <span data-ttu-id="931c2-132">Çalışma zamanı tarafından yalnızca null bir nesne başvurulduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="931c2-132">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | <span data-ttu-id="931c2-133">Geçersiz bir durumda olduğunda yöntemler tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="931c2-133">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="931c2-134">Çağırma `Enumerator.MoveNext()` bir öğe temel alınan koleksiyonundan kaldırdıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="931c2-134">Calling `Enumerator.MoveNext()` after removing an item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <span data-ttu-id="931c2-135">Tüm bağımsız değişken özel durumlar için temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="931c2-135">Base class for all argument exceptions.</span></span> | <span data-ttu-id="931c2-136">Hiçbiri (Bu özel durumun türetilmiş bir sınıf kullanın).</span><span class="sxs-lookup"><span data-stu-id="931c2-136">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <span data-ttu-id="931c2-137">Bir bağımsız değişken boş olmasına izin verme yöntemler tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="931c2-137">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | <span data-ttu-id="931c2-138">Bağımsız değişkenler aralıktan doğrulayın yöntemler tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="931c2-138">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="931c2-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="931c2-139">See also</span></span>

[<span data-ttu-id="931c2-140">Özel Durum Sınıfı ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="931c2-140">Exception Class and Properties</span></span>](exception-class-and-properties.md)  
[<span data-ttu-id="931c2-141">Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma</span><span class="sxs-lookup"><span data-stu-id="931c2-141">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)  
[<span data-ttu-id="931c2-142">Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma</span><span class="sxs-lookup"><span data-stu-id="931c2-142">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)  
[<span data-ttu-id="931c2-143">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="931c2-143">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)  
[<span data-ttu-id="931c2-144">Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="931c2-144">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)  
[<span data-ttu-id="931c2-145">Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="931c2-145">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)  
[<span data-ttu-id="931c2-146">Nasıl yapılır: Finally Bloklarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="931c2-146">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)  
[<span data-ttu-id="931c2-147">COM Birlikte Çalışma Özel Durumlarını İşleme</span><span class="sxs-lookup"><span data-stu-id="931c2-147">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)  
[<span data-ttu-id="931c2-148">Özel Durumlar için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="931c2-148">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)  
<span data-ttu-id="931c2-149">[Her geliştirici bilmeniz hakkında özel durumlara çalışma zamanında gereken](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="931c2-149">[What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span></span>
