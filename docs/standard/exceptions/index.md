---
title: .NET'te özel durumları işleme ve atma
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
ms.openlocfilehash: 8e78b2a8d7a815637e143eeb88bcfb51ded33771
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75741349"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="bbb78-102">.NET'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="bbb78-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="bbb78-103">Uygulamalar yürütme sırasında oluşan hataları tutarlı bir şekilde işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bbb78-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="bbb78-104">.NET, uygulamaları tek tip bir şekilde bildirmek için bir model sağlar: .NET işlemleri özel durumlar atarak başarısızlığı gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbb78-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="bbb78-105">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="bbb78-105">Exceptions</span></span>

<span data-ttu-id="bbb78-106">Özel durum, yürütme programı tarafından karşılaşılan herhangi bir hata koşulu veya beklenmeyen davranıştır.</span><span class="sxs-lookup"><span data-stu-id="bbb78-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="bbb78-107">Özel durumlar, kodunuzdaki bir hata dan veya (paylaşılan kitaplık gibi), kullanılamayan işletim sistemi kaynakları, çalışma zamanının karşılaştığı beklenmeyen koşullar (doğrulanamayan kod gibi) vb. olarak adlandırdığınız koddaki bir hata nedeniyle atılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbb78-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on.</span></span> <span data-ttu-id="bbb78-108">Uygulamanız bu koşullardan bazılarını kurtarabilir, ancak diğerlerinden kurtaramaz.</span><span class="sxs-lookup"><span data-stu-id="bbb78-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="bbb78-109">Çoğu uygulama özel durumlarından kurtarabilirsiniz, ancak çoğu çalışma zamanı özel durumlarını kurtaramazsınız.</span><span class="sxs-lookup"><span data-stu-id="bbb78-109">Although you can recover from most application exceptions, you can't recover from most runtime exceptions.</span></span>

<span data-ttu-id="bbb78-110">.NET'te özel <xref:System.Exception?displayProperty=nameWithType> durum, sınıftan devralan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="bbb78-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="bbb78-111">Bir özel durum, bir sorunun oluştuğu bir kod alanından atılır.</span><span class="sxs-lookup"><span data-stu-id="bbb78-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="bbb78-112">Özel durum, uygulama işlenine veya program sonlandırına kadar yığına aktarılır.</span><span class="sxs-lookup"><span data-stu-id="bbb78-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="bbb78-113">Özel durumlar ve geleneksel hata işleme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="bbb78-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="bbb78-114">Geleneksel olarak, bir dilin hata işleme modeli, dilin hataları algılama ve bunlar için işleyicileri bulma benzersiz bir şekilde veya işletim sistemi tarafından sağlanan hata işleme mekanizması dayanıyordu.</span><span class="sxs-lookup"><span data-stu-id="bbb78-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="bbb78-115">.NET'in özel durum işlemeyi uygulama şekli aşağıdaki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="bbb78-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="bbb78-116">Özel durum atma ve işleme .NET programlama dilleri için aynı çalışır.</span><span class="sxs-lookup"><span data-stu-id="bbb78-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="bbb78-117">Özel durumları işlemek için belirli bir dil sözdizimi gerektirmez, ancak her dilin kendi sözdizimini tanımlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="bbb78-117">Doesn't require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="bbb78-118">Özel durumlar proses ve hatta makine sınırları arasında atılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbb78-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="bbb78-119">Program güvenilirliğini artırmak için bir uygulamaya özel durum işleme kodu eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bbb78-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="bbb78-120">Özel durumlar, iade kodları gibi diğer hata bildirim yöntemlerine göre avantajlar sunar.</span><span class="sxs-lookup"><span data-stu-id="bbb78-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="bbb78-121">Bir özel durum atılırsa ve bunu işlemezseniz, çalışma zamanı uygulamanızı sonlandırdığından, hatalar fark edilmez.</span><span class="sxs-lookup"><span data-stu-id="bbb78-121">Failures don't go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="bbb78-122">Geçersiz değerler, hata iade kodunu denetlemede başarısız olan bir kod sonucunda sistem de yayılmaya devam etmez.</span><span class="sxs-lookup"><span data-stu-id="bbb78-122">Invalid values don't continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span>

## <a name="common-exceptions"></a><span data-ttu-id="bbb78-123">Sık karşılaşılan özel durumlar</span><span class="sxs-lookup"><span data-stu-id="bbb78-123">Common exceptions</span></span>

<span data-ttu-id="bbb78-124">Aşağıdaki tabloda, bunlara neyin neden olabileceğine dair örnekleriçeren bazı yaygın özel durumlar listelenebilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbb78-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="bbb78-125">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="bbb78-125">Exception type</span></span> | <span data-ttu-id="bbb78-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbb78-126">Description</span></span> | <span data-ttu-id="bbb78-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbb78-127">Example</span></span> |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | <span data-ttu-id="bbb78-128">Tüm özel durumlar için taban sınıf.</span><span class="sxs-lookup"><span data-stu-id="bbb78-128">Base class for all exceptions.</span></span> | <span data-ttu-id="bbb78-129">Yok (bu özel durum türetilmiş bir sınıf kullanın).</span><span class="sxs-lookup"><span data-stu-id="bbb78-129">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <span data-ttu-id="bbb78-130">Yalnızca bir dizi yanlış dizieklendiğinde çalışma zamanı tarafından atılır.</span><span class="sxs-lookup"><span data-stu-id="bbb78-130">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="bbb78-131">Bir diziyi geçerli aralığının dışında dizidizileme:</span><span class="sxs-lookup"><span data-stu-id="bbb78-131">Indexing an array outside its valid range:</span></span> <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <span data-ttu-id="bbb78-132">Yalnızca null nesne başvurulduğunda çalışma zamanı tarafından atılır.</span><span class="sxs-lookup"><span data-stu-id="bbb78-132">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | <span data-ttu-id="bbb78-133">Geçersiz bir durumdayken yöntemlerle atılır.</span><span class="sxs-lookup"><span data-stu-id="bbb78-133">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="bbb78-134">Bir `Enumerator.MoveNext()` öğeyi temel koleksiyondan kaldırdıktan sonra arama.</span><span class="sxs-lookup"><span data-stu-id="bbb78-134">Calling `Enumerator.MoveNext()` after removing an item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <span data-ttu-id="bbb78-135">Tüm bağımsız değişken özel durumları için taban sınıf.</span><span class="sxs-lookup"><span data-stu-id="bbb78-135">Base class for all argument exceptions.</span></span> | <span data-ttu-id="bbb78-136">Yok (bu özel durum türetilmiş bir sınıf kullanın).</span><span class="sxs-lookup"><span data-stu-id="bbb78-136">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <span data-ttu-id="bbb78-137">Bir bağımsız değişkenin null olmasını izin vermez yöntemler tarafından atılır.</span><span class="sxs-lookup"><span data-stu-id="bbb78-137">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | <span data-ttu-id="bbb78-138">Bağımsız değişkenlerin belirli bir aralıkta olduğunu doğrulayan yöntemlertarafından atılır.</span><span class="sxs-lookup"><span data-stu-id="bbb78-138">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="bbb78-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbb78-139">See also</span></span>

- [<span data-ttu-id="bbb78-140">Özel Durumu Sınıfı ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="bbb78-140">Exception Class and Properties</span></span>](exception-class-and-properties.md)
- [<span data-ttu-id="bbb78-141">Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma</span><span class="sxs-lookup"><span data-stu-id="bbb78-141">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [<span data-ttu-id="bbb78-142">Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma</span><span class="sxs-lookup"><span data-stu-id="bbb78-142">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
- [<span data-ttu-id="bbb78-143">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bbb78-143">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="bbb78-144">Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bbb78-144">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="bbb78-145">Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="bbb78-145">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
- [<span data-ttu-id="bbb78-146">Nasıl yapılır: Finally Bloklarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="bbb78-146">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
- [<span data-ttu-id="bbb78-147">COM Birlikte Çalışması Özel Durumlarını İşleme</span><span class="sxs-lookup"><span data-stu-id="bbb78-147">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
- [<span data-ttu-id="bbb78-148">Özel Durumlar için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bbb78-148">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)
- [<span data-ttu-id="bbb78-149">Her Dev'in Çalışma ZamanındaKi İstisnalar Hakkında Bilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="bbb78-149">What Every Dev needs to Know About Exceptions in the Runtime</span></span>](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/exceptions.md)
