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
ms.openlocfilehash: 8e78b2a8d7a815637e143eeb88bcfb51ded33771
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741349"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="c6e61-102">İşleme ve .NET özel durumları atma</span><span class="sxs-lookup"><span data-stu-id="c6e61-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="c6e61-103">Uygulamalar, yürütme sırasında oluşan hataları tutarlı bir şekilde işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="c6e61-104">.NET, hataların uygulamalarda tutarlı bir şekilde bildirimde bulunmak için bir model sağlar: .NET işlemleri özel durumlar oluşturarak hatanın başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="c6e61-105">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="c6e61-105">Exceptions</span></span>

<span data-ttu-id="c6e61-106">Bir özel durum, çalıştırılan bir program tarafından karşılaşılan herhangi bir hata durumu veya beklenmedik davranıştır.</span><span class="sxs-lookup"><span data-stu-id="c6e61-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="c6e61-107">Kodunuzda veya çağırdığınız kodda (örneğin, paylaşılan bir kitaplık), kullanılamayan işletim sistemi kaynaklarıyla, çalışma zamanının karşılaştığı beklenmeyen koşullar (doğrulanamayan kod gibi) veya benzeri bir hata nedeniyle özel durumlar oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on.</span></span> <span data-ttu-id="c6e61-108">Uygulamanız bu koşullardan bazılarını kurtarabilir, ancak başkalarından daha fazlasını yapabilir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="c6e61-109">Çoğu uygulama özel durumundan kurtarabilseniz de, çoğu çalışma zamanı özel durumu ' nu kurtaramazsınız.</span><span class="sxs-lookup"><span data-stu-id="c6e61-109">Although you can recover from most application exceptions, you can't recover from most runtime exceptions.</span></span>

<span data-ttu-id="c6e61-110">.NET sürümünde, özel durum <xref:System.Exception?displayProperty=nameWithType> sınıfından devralan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c6e61-111">Bir sorunun oluştuğu bir kod alanından bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="c6e61-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="c6e61-112">Özel durum, uygulama onu işleyene veya program sonlanana kadar yığını iletilir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="c6e61-113">Özel durumlar ve geleneksel hata işleme yöntemleri karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="c6e61-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="c6e61-114">Geleneksel olarak, bir dilin hata işleme modeli, hataların hataları tespit etme ve işleyicileri bulma ve işletim sistemi tarafından sunulan hata işleme mekanizması üzerinde, dilin benzersiz yolunu ortadan kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="c6e61-115">.NET özel durum işlemeyi uygulayan yol aşağıdaki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="c6e61-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="c6e61-116">Özel durum oluşturma ve işleme, .NET programlama dilleri için aynı şekilde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="c6e61-117">Özel durumları işlemek için belirli bir dil sözdizimi gerektirmez, ancak her dilin kendi sözdizimini tanımlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-117">Doesn't require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="c6e61-118">Özel durumlar işlem ve hatta makine sınırları arasında oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="c6e61-119">Özel durum işleme kodu, program güvenilirliğini artırmak için bir uygulamaya eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="c6e61-120">Özel durumlar, dönüş kodları gibi diğer hata bildirimi yöntemlerine ilişkin avantajlar sunar.</span><span class="sxs-lookup"><span data-stu-id="c6e61-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="c6e61-121">Bir özel durum oluşursa ve bu işlemi işlemezseniz, çalışma zamanı uygulamanızı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="c6e61-121">Failures don't go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="c6e61-122">Geçersiz değerler, hata dönüş kodu denetimi başarısız olan kodun bir sonucu olarak sisteme yayılmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="c6e61-122">Invalid values don't continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span>

## <a name="common-exceptions"></a><span data-ttu-id="c6e61-123">Sık karşılaşılan özel durumlar</span><span class="sxs-lookup"><span data-stu-id="c6e61-123">Common exceptions</span></span>

<span data-ttu-id="c6e61-124">Aşağıdaki tablo, bazı yaygın özel durumları, bunlara neden olabilecek örneklere örnek olarak listelemektedir.</span><span class="sxs-lookup"><span data-stu-id="c6e61-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="c6e61-125">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="c6e61-125">Exception type</span></span> | <span data-ttu-id="c6e61-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6e61-126">Description</span></span> | <span data-ttu-id="c6e61-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6e61-127">Example</span></span> |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | <span data-ttu-id="c6e61-128">Tüm özel durumlar için temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="c6e61-128">Base class for all exceptions.</span></span> | <span data-ttu-id="c6e61-129">Hiçbiri (Bu özel durumun türetilmiş bir sınıfını kullanın).</span><span class="sxs-lookup"><span data-stu-id="c6e61-129">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <span data-ttu-id="c6e61-130">Çalışma zamanı tarafından yalnızca bir dizi yanlış dizin oluşturulduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c6e61-130">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="c6e61-131">Dizinin geçerli aralığının dışında dizin oluşturma:</span><span class="sxs-lookup"><span data-stu-id="c6e61-131">Indexing an array outside its valid range:</span></span> <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <span data-ttu-id="c6e61-132">Çalışma zamanı tarafından yalnızca null bir nesneye başvuruluyorsa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c6e61-132">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | <span data-ttu-id="c6e61-133">Geçersiz bir durumda olan yöntemler tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="c6e61-133">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="c6e61-134">Temel koleksiyondan bir öğe kaldırıldıktan sonra `Enumerator.MoveNext()` çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="c6e61-134">Calling `Enumerator.MoveNext()` after removing an item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <span data-ttu-id="c6e61-135">Tüm bağımsız değişken özel durumları için temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="c6e61-135">Base class for all argument exceptions.</span></span> | <span data-ttu-id="c6e61-136">Hiçbiri (Bu özel durumun türetilmiş bir sınıfını kullanın).</span><span class="sxs-lookup"><span data-stu-id="c6e61-136">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <span data-ttu-id="c6e61-137">Bağımsız değişkenin null olması için izin verilmeyen yöntemler tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="c6e61-137">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | <span data-ttu-id="c6e61-138">Bağımsız değişkenlerin belirli bir aralıkta olduğunu doğrulayan yöntemler tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c6e61-138">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="c6e61-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6e61-139">See also</span></span>

- [<span data-ttu-id="c6e61-140">Özel Durum Sınıfı ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c6e61-140">Exception Class and Properties</span></span>](exception-class-and-properties.md)
- [<span data-ttu-id="c6e61-141">Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma</span><span class="sxs-lookup"><span data-stu-id="c6e61-141">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [<span data-ttu-id="c6e61-142">Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c6e61-142">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
- [<span data-ttu-id="c6e61-143">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6e61-143">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="c6e61-144">Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6e61-144">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="c6e61-145">Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="c6e61-145">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
- [<span data-ttu-id="c6e61-146">Nasıl yapılır: Finally Bloklarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="c6e61-146">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
- [<span data-ttu-id="c6e61-147">COM Birlikte Çalışma Özel Durumlarını İşleme</span><span class="sxs-lookup"><span data-stu-id="c6e61-147">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
- [<span data-ttu-id="c6e61-148">Özel Durumlar için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c6e61-148">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)
- [<span data-ttu-id="c6e61-149">Çalışma zamanındaki özel durumları öğrenmek için her dev gerekir</span><span class="sxs-lookup"><span data-stu-id="c6e61-149">What Every Dev needs to Know About Exceptions in the Runtime</span></span>](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/exceptions.md)
