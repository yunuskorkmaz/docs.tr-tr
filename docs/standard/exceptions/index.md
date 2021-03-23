---
title: .NET 'te özel durumları işleme ve atma
description: .NET ' te özel durumları nasıl işleyeceğinizi ve oluşturacağınızı öğrenin. Özel durumlar, .NET işlemlerinin uygulamalarda başarısız olduğunu gösterir.
ms.date: 06/19/2018
helpviewer_keywords:
- exceptions [.NET], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET], exceptions
- exceptions [.NET], throwing
- exceptions [.NET]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
ms.openlocfilehash: 3b64b9121cc784db7d76ff5501aedfd125d0002c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876480"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="eb0f2-104">.NET 'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="eb0f2-104">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="eb0f2-105">Uygulamalar, yürütme sırasında oluşan hataları tutarlı bir şekilde işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-105">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="eb0f2-106">.NET, hataların uygulamalarda tutarlı bir şekilde bildirimde bulunmak için bir model sağlar: .NET işlemleri özel durumlar oluşturarak hatanın başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-106">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="eb0f2-107">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="eb0f2-107">Exceptions</span></span>

<span data-ttu-id="eb0f2-108">Bir özel durum, çalıştırılan bir program tarafından karşılaşılan herhangi bir hata durumu veya beklenmedik davranıştır.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-108">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="eb0f2-109">Kodunuzda veya çağırdığınız kodda (örneğin, paylaşılan bir kitaplık), kullanılamayan işletim sistemi kaynaklarıyla, çalışma zamanının karşılaştığı beklenmeyen koşullar (doğrulanamayan kod gibi) veya benzeri bir hata nedeniyle özel durumlar oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-109">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on.</span></span> <span data-ttu-id="eb0f2-110">Uygulamanız bu koşullardan bazılarını kurtarabilir, ancak başkalarından daha fazlasını yapabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-110">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="eb0f2-111">Çoğu uygulama özel durumundan kurtarabilseniz de, çoğu çalışma zamanı özel durumu ' nu kurtaramazsınız.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-111">Although you can recover from most application exceptions, you can't recover from most runtime exceptions.</span></span>

<span data-ttu-id="eb0f2-112">.NET ' te, özel durum sınıfından devralan bir nesnedir <xref:System.Exception?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="eb0f2-112">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="eb0f2-113">Bir sorunun oluştuğu bir kod alanından bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-113">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="eb0f2-114">Özel durum, uygulama onu işleyene veya program sonlanana kadar yığını iletilir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-114">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="eb0f2-115">Özel durumlar ve geleneksel hata işleme yöntemleri karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="eb0f2-115">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="eb0f2-116">Geleneksel olarak, bir dilin hata işleme modeli, hataların hataları tespit etme ve işleyicileri bulma ve işletim sistemi tarafından sunulan hata işleme mekanizması üzerinde, dilin benzersiz yolunu ortadan kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-116">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="eb0f2-117">.NET özel durum işlemeyi uygulayan yol aşağıdaki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="eb0f2-117">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="eb0f2-118">Özel durum oluşturma ve işleme, .NET programlama dilleri için aynı şekilde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-118">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="eb0f2-119">Özel durumları işlemek için belirli bir dil sözdizimi gerektirmez, ancak her dilin kendi sözdizimini tanımlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-119">Doesn't require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="eb0f2-120">Özel durumlar işlem ve hatta makine sınırları arasında oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-120">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="eb0f2-121">Özel durum işleme kodu, program güvenilirliğini artırmak için bir uygulamaya eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-121">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="eb0f2-122">Özel durumlar, dönüş kodları gibi diğer hata bildirimi yöntemlerine ilişkin avantajlar sunar.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-122">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="eb0f2-123">Bir özel durum oluşursa ve bu işlemi işlemezseniz, çalışma zamanı uygulamanızı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-123">Failures don't go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="eb0f2-124">Geçersiz değerler, hata dönüş kodu denetimi başarısız olan kodun bir sonucu olarak sisteme yayılmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-124">Invalid values don't continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span>

## <a name="common-exceptions"></a><span data-ttu-id="eb0f2-125">Sık karşılaşılan özel durumlar</span><span class="sxs-lookup"><span data-stu-id="eb0f2-125">Common exceptions</span></span>

<span data-ttu-id="eb0f2-126">Aşağıdaki tablo, bazı yaygın özel durumları, bunlara neden olabilecek örneklere örnek olarak listelemektedir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-126">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="eb0f2-127">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="eb0f2-127">Exception type</span></span> | <span data-ttu-id="eb0f2-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb0f2-128">Description</span></span> | <span data-ttu-id="eb0f2-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb0f2-129">Example</span></span> |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | <span data-ttu-id="eb0f2-130">Tüm özel durumlar için temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-130">Base class for all exceptions.</span></span> | <span data-ttu-id="eb0f2-131">Hiçbiri (Bu özel durumun türetilmiş bir sınıfını kullanın).</span><span class="sxs-lookup"><span data-stu-id="eb0f2-131">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <span data-ttu-id="eb0f2-132">Çalışma zamanı tarafından yalnızca bir dizi yanlış dizin oluşturulduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-132">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="eb0f2-133">Dizinin geçerli aralığının dışında dizin oluşturma:</span><span class="sxs-lookup"><span data-stu-id="eb0f2-133">Indexing an array outside its valid range:</span></span> <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <span data-ttu-id="eb0f2-134">Çalışma zamanı tarafından yalnızca null bir nesneye başvuruluyorsa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-134">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | <span data-ttu-id="eb0f2-135">Geçersiz bir durumda olan yöntemler tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-135">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="eb0f2-136">`Enumerator.MoveNext()`Temel alınan koleksiyondan bir öğe kaldırıldıktan sonra çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-136">Calling `Enumerator.MoveNext()` after removing an item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <span data-ttu-id="eb0f2-137">Tüm bağımsız değişken özel durumları için temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-137">Base class for all argument exceptions.</span></span> | <span data-ttu-id="eb0f2-138">Hiçbiri (Bu özel durumun türetilmiş bir sınıfını kullanın).</span><span class="sxs-lookup"><span data-stu-id="eb0f2-138">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <span data-ttu-id="eb0f2-139">Bağımsız değişkenin null olması için izin verilmeyen yöntemler tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-139">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | <span data-ttu-id="eb0f2-140">Bağımsız değişkenlerin belirli bir aralıkta olduğunu doğrulayan yöntemler tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-140">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="eb0f2-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-141">See also</span></span>

- [<span data-ttu-id="eb0f2-142">Özel durum sınıfı ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="eb0f2-142">Exception Class and Properties</span></span>](exception-class-and-properties.md)
- [<span data-ttu-id="eb0f2-143">Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma</span><span class="sxs-lookup"><span data-stu-id="eb0f2-143">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [<span data-ttu-id="eb0f2-144">Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma</span><span class="sxs-lookup"><span data-stu-id="eb0f2-144">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
- [<span data-ttu-id="eb0f2-145">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb0f2-145">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="eb0f2-146">Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb0f2-146">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="eb0f2-147">Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="eb0f2-147">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
- [<span data-ttu-id="eb0f2-148">Nasıl yapılır: Finally Bloklarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="eb0f2-148">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
- [<span data-ttu-id="eb0f2-149">COM Birlikte Çalışması Özel Durumlarını İşleme</span><span class="sxs-lookup"><span data-stu-id="eb0f2-149">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
- [<span data-ttu-id="eb0f2-150">Özel Durumlar için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eb0f2-150">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)
- [<span data-ttu-id="eb0f2-151">Çalışma zamanındaki özel durumları öğrenmek için her dev gerekir</span><span class="sxs-lookup"><span data-stu-id="eb0f2-151">What Every Dev needs to Know About Exceptions in the Runtime</span></span>](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/exceptions.md)
