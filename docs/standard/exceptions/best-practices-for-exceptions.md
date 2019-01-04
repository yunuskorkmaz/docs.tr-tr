---
title: Özel Durumlar için En İyi Yöntemler
ms.date: 12/05.2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 220e43ed6aadbcc443f4cf06310fe12e970abcf2
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030431"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="7cef7-102">Özel durumlar için en iyi yöntemler</span><span class="sxs-lookup"><span data-stu-id="7cef7-102">Best practices for exceptions</span></span>

<span data-ttu-id="7cef7-103">İyi tasarlanmış bir uygulama, özel durumları ve hataları işleyerek uygulama kilitlenmelerini önler.</span><span class="sxs-lookup"><span data-stu-id="7cef7-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="7cef7-104">Bu bölümde, özel durumlar oluşturma ve işleme için en iyi uygulamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7cef7-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="7cef7-105">Hataları kurtarmak veya kaynakları serbest bırakmak için try/catch/finally blokları kullanın</span><span class="sxs-lookup"><span data-stu-id="7cef7-105">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="7cef7-106">Kullanım `try` / `catch` etrafında büyük olasılıkla bir özel durum oluşturabilir kod blokları ***ve*** kodunuzu bu özel durumdan kurtarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7cef7-106">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="7cef7-107">İçinde `catch` engeller, her zaman en çok türetilen sipariş durumlardan az türetilmiş için.</span><span class="sxs-lookup"><span data-stu-id="7cef7-107">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="7cef7-108">Tüm özel durumları türetilmesi <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="7cef7-108">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="7cef7-109">Daha fazla türetilmiş özel durumları temel özel durum sınıfı için bir catch yan tümcesi öncesinde bir catch yan tümcesi tarafından işlenmesini değil.</span><span class="sxs-lookup"><span data-stu-id="7cef7-109">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="7cef7-110">Kodunuz bir özel durumdan kurtarılamazsa, o özel durumu hiçbir öğeyi yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="7cef7-110">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="7cef7-111">Daha fazla çağrı yığınına mümkünse kurtarmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7cef7-111">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="7cef7-112">Temiz ile ayrılan kaynakları `using` deyimleri veya `finally` engeller.</span><span class="sxs-lookup"><span data-stu-id="7cef7-112">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="7cef7-113">Tercih ettiğiniz `using` özel durumlar oluşturulduğunda otomatik olarak kaynakları temizlemek için deyimleri.</span><span class="sxs-lookup"><span data-stu-id="7cef7-113">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="7cef7-114">Kullanım `finally` uygulamayıp kaynakları temizlemek için blokları <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="7cef7-114">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="7cef7-115">Kod bir `finally` yan tümcesi bile özel durumlar oluşturulduğunda neredeyse her zaman yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7cef7-115">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="7cef7-116">Genel koşullar, özel durumları atma olmadan işleme</span><span class="sxs-lookup"><span data-stu-id="7cef7-116">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="7cef7-117">Oluşur ancak bir özel durum harekete, bunları özel durum kaçınır şekilde işlemesi göz önünde bulundurun olasılığı koşulları.</span><span class="sxs-lookup"><span data-stu-id="7cef7-117">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="7cef7-118">Örneğin, zaten kapalı bir bağlantıyı kapatmak çalışırsanız elde edecekleriniz bir `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="7cef7-118">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="7cef7-119">Bunu kullanarak önlemek bir `if` kapatmak denemeden önce bağlantı durumu denetlemek için bildirimi.</span><span class="sxs-lookup"><span data-stu-id="7cef7-119">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

<span data-ttu-id="7cef7-120">Kapatmadan önce bağlantı durumunu denetleme, yakalayabilir `InvalidOperationException` özel durum.</span><span class="sxs-lookup"><span data-stu-id="7cef7-120">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

<span data-ttu-id="7cef7-121">Seçmek için yöntem olayın meydana gelmesine ne sıklıkta beklediğinize bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7cef7-121">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="7cef7-122">Olay çok sık oluşmuyorsa, yani gerçekten olağanüstüyse ve bir hatayı gösteriyorsa (beklenmeyen bir dosya sonu gibi), özel durum işlemeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7cef7-122">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="7cef7-123">Özel durum işleme kullandığınızda, normal koşullarda daha az kod çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="7cef7-123">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="7cef7-124">Olay düzenli olarak gerçekleşiyorsa ve normal yürütmenin bir parçası olarak kabul, kodda hata koşulları için kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="7cef7-124">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="7cef7-125">Sık karşılaşılan hata koşulları için iade ettiğinizde, özel durumlar önlemek için daha az kod yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7cef7-125">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="7cef7-126">Sınıflar, özel durumlar önlenebilir olacağı şekilde tasarlayın</span><span class="sxs-lookup"><span data-stu-id="7cef7-126">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="7cef7-127">Bir sınıfı yöntemleri sağlayabilir veya bir özel durum çağrı yapmak önlemek etkinleştirdiğiniz özellikler tetikleyecektir.</span><span class="sxs-lookup"><span data-stu-id="7cef7-127">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="7cef7-128">Örneğin, bir <xref:System.IO.FileStream> sınıfı, dosyanın sonuna ulaşılıp ulaşılmadığını belirlemeye yardımcı yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7cef7-128">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="7cef7-129">Bu, dosyanın sonundan okuduğunuzda oluşturulan özel durum önlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7cef7-129">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="7cef7-130">Aşağıdaki örnek, bir özel durum tetiklemeden dosya sonuna kadar okumak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7cef7-130">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

<span data-ttu-id="7cef7-131">Özel durumlar önlemek için başka bir yolu geri döndürmektir `null` bir özel durum oluşturmaktansa çok yaygın hata durumları için.</span><span class="sxs-lookup"><span data-stu-id="7cef7-131">Another way to avoid exceptions is to return `null` for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="7cef7-132">Çok yaygın olan bir hata durumu, denetiminin normal akışı olarak kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="7cef7-132">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="7cef7-133">Döndürerek `null` bu gibi durumlarda, uygulama performansı üzerindeki etkisini en aza.</span><span class="sxs-lookup"><span data-stu-id="7cef7-133">By returning `null` in these cases, you minimize the performance impact to an app.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="7cef7-134">Bir hata kodunu döndürmek yerine özel durumlar</span><span class="sxs-lookup"><span data-stu-id="7cef7-134">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="7cef7-135">Özel durumlar hataları çağırmak için kod dönüş kodu denetlemedi gözden kaçan geçmemektedir emin olun.</span><span class="sxs-lookup"><span data-stu-id="7cef7-135">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="7cef7-136">Önceden tanımlanmış .NET özel durum türlerini kullanın</span><span class="sxs-lookup"><span data-stu-id="7cef7-136">Use the predefined .NET exception types</span></span>

<span data-ttu-id="7cef7-137">Önceden tanımlanmış bir yalnızca geçerli değildir, yeni bir özel durum sınıfı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="7cef7-137">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="7cef7-138">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7cef7-138">For example:</span></span>

- <span data-ttu-id="7cef7-139">Throw bir <xref:System.InvalidOperationException> bir özellik kümesi veya yöntem çağrısı bir nesnenin geçerli durumuna uygun değilse bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="7cef7-139">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="7cef7-140">Throw bir <xref:System.ArgumentException> özel durum veya önceden tanımlanmış sınıfların türetilmesi <xref:System.ArgumentException> geçersiz parametreler geçirilmiş.</span><span class="sxs-lookup"><span data-stu-id="7cef7-140">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="7cef7-141">Son özel durum sınıf adlarını sözcüğü `Exception`</span><span class="sxs-lookup"><span data-stu-id="7cef7-141">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="7cef7-142">Bir özel durum gerekli olduğunda, uygun şekilde adlandırın ve türetmeniz <xref:System.Exception> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7cef7-142">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="7cef7-143">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7cef7-143">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="7cef7-144">Üç Oluşturucusu özel durum sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="7cef7-144">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="7cef7-145">En az üç ortak oluşturucu kendi özel durum sınıflarınızı oluştururken kullanmak: varsayılan oluşturucu, bir dize iletisi alan bir oluşturucu ve bir dize iletisi ve bir iç özel durum alan bir oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="7cef7-145">Use at least the three common constructors when creating your own exception classes: the default constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

* <span data-ttu-id="7cef7-146"><xref:System.Exception.%23ctor>, varsayılan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="7cef7-146"><xref:System.Exception.%23ctor>, which uses default values.</span></span>
  
* <span data-ttu-id="7cef7-147"><xref:System.Exception.%23ctor%28System.String%29>, bir dize iletisi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="7cef7-147"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>  
  
* <span data-ttu-id="7cef7-148"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, kabul eden bir dize iletisi ve bir iç özel durum.</span><span class="sxs-lookup"><span data-stu-id="7cef7-148"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>  
  
<span data-ttu-id="7cef7-149">Bir örnek için bkz [nasıl yapılır: Kullanıcı tanımlı özel durumlar oluşturma](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="7cef7-149">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="7cef7-150">Uzaktan kod yürütüldüğünde, özel durum verileri kullanılabilir olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="7cef7-150">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="7cef7-151">Kullanıcı tanımlı özel durumlar oluştururken, özel durumları için meta verileri uzaktan yürütülmekte olan kod için kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7cef7-151">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span> 

<span data-ttu-id="7cef7-152">Örneğin, uygulama etki alanları destekleyen .NET uygulamalarında, uygulama etki alanları arasında özel durumları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="7cef7-152">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="7cef7-153">Bir özel durum kodu yürütür uygulama etki alanı B uygulama etki alanı oluşturduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7cef7-153">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="7cef7-154">Uygulama etki alanı için düzgün şekilde catch ve özel durumu işlemek için b uygulama etki alanı tarafından oluşturulan özel durumu içeren derlemeyi bulabilir olmalıdır B uygulama etki alanı kendi uygulama temel bir derlemede bulunan bir özel durum oluşturur, ancak uygulama etki alanı'nın uygulama temel altında değil, uygulama etki alanı özel mümkün olmayacaktır ve ortak dil çalışma zamanı bir <xref:System.IO.FileNotFoundException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="7cef7-154">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="7cef7-155">Bu durumu önlemek için, özel durum bilgisini içeren derlemeyi iki şekilde dağıtabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7cef7-155">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="7cef7-156">Derlemeyi iki uygulama etki alanı tarafından paylaşılan ortak bir uygulama temel dizinine koyun.</span><span class="sxs-lookup"><span data-stu-id="7cef7-156">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="7cef7-157">\- veya -</span><span class="sxs-lookup"><span data-stu-id="7cef7-157">\- or -</span></span>

- <span data-ttu-id="7cef7-158">Eğer etki alanları ortak bir uygulama temel dizini paylaşmıyorsa, özel durum bilgisi içeren derlemeyi bir tanımlayıcı ad ile imzalayıp derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtarak.</span><span class="sxs-lookup"><span data-stu-id="7cef7-158">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="7cef7-159">Dilbilgisi bakımından doğru hata iletileri kullanın</span><span class="sxs-lookup"><span data-stu-id="7cef7-159">Use grammatically correct error messages</span></span>

<span data-ttu-id="7cef7-160">Açık bir cümle yazın ve bitiş için noktalama işaretleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7cef7-160">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="7cef7-161">Atanan dizesindeki her cümle <xref:System.Exception.Message?displayProperty=nameWithType> özelliği, nokta ile bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="7cef7-161">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="7cef7-162">Örneğin, "günlük tablosu taştı."</span><span class="sxs-lookup"><span data-stu-id="7cef7-162">For example, "The log table has overflowed."</span></span> <span data-ttu-id="7cef7-163">uygun ileti dizesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="7cef7-163">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="7cef7-164">Her özel duruma bir yerelleştirilmiş dize arar: mesaj ekleyin</span><span class="sxs-lookup"><span data-stu-id="7cef7-164">Include a localized string message in every exception</span></span>

<span data-ttu-id="7cef7-165">Kullanıcının gördüğü hata iletisi türetilir <xref:System.Exception.Message?displayProperty=nameWithType> özelliği oluşturulan özel durumun ve değil, özel durum sınıfı adı.</span><span class="sxs-lookup"><span data-stu-id="7cef7-165">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="7cef7-166">Genellikle, bir değer atayın <xref:System.Exception.Message?displayProperty=nameWithType> mesajı dizesine eşliyor geçirerek özelliği `message` bağımsız değişkeni bir [özel Oluşturucu](xref:System.Exception.%23ctor%2A).</span><span class="sxs-lookup"><span data-stu-id="7cef7-166">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span> 

<span data-ttu-id="7cef7-167">Yerelleştirilmiş uygulamalar için uygulamanızı oluşturabilecek her bir özel durum için ileti yerelleştirilmiş bir dize sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7cef7-167">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="7cef7-168">Kaynak dosyaları, yerelleştirilmiş hata iletileri sağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="7cef7-168">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="7cef7-169">Uygulamaları yerelleştirme ve yerelleştirilmiş dizeleri alma hakkında daha fazla bilgi için bkz: [masaüstü uygulamalarında kaynakların](../../framework/resources/index.md) ve <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7cef7-169">For information on localizing applications and retrieving localized strings, see [Resources in Desktop Apps](../../framework/resources/index.md) and <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="7cef7-170">Özel durumlar, gerektiği gibi ek özellikler sağlar</span><span class="sxs-lookup"><span data-stu-id="7cef7-170">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="7cef7-171">(Ek olarak özel ileti dizesi) bir özel durum için ek özellikler sağlar. ek bilgiler nerede olursa kullanışlı olacağı programlı bir senaryo olduğunda.</span><span class="sxs-lookup"><span data-stu-id="7cef7-171">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="7cef7-172">Örneğin, <xref:System.IO.FileNotFoundException> sağlar <xref:System.IO.FileNotFoundException.FileName> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7cef7-172">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="7cef7-173">Yığın izlemesi yararlı olacaktır, böylece bir yerde throw deyimleri</span><span class="sxs-lookup"><span data-stu-id="7cef7-173">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="7cef7-174">Burada özel durum oluşturulur ve bitişi deyim yığın izleme başlangıcı `catch` deyimi özel durumu yakalar.</span><span class="sxs-lookup"><span data-stu-id="7cef7-174">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="7cef7-175">Exception Oluşturucu yöntemleri kullanın</span><span class="sxs-lookup"><span data-stu-id="7cef7-175">Use exception builder methods</span></span>

<span data-ttu-id="7cef7-176">Bir sınıfın uygulamasında aynı özel durumu farklı yerlerde oluşturması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="7cef7-176">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="7cef7-177">Fazla kodu önlemek için, özel durumu oluşturmak ve döndürmek için yardımcı yöntemler kullanın.</span><span class="sxs-lookup"><span data-stu-id="7cef7-177">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="7cef7-178">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7cef7-178">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
<span data-ttu-id="7cef7-179">Bazı durumlarda, özel durum oluşturmak için özel durumun oluşturucusunu kullanmak daha uygun olacak.</span><span class="sxs-lookup"><span data-stu-id="7cef7-179">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="7cef7-180">Örnek bir genel özel durum sınıfı olduğu gibi <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="7cef7-180">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="7cef7-181">Özel durum nedeniyle yöntemleri yoksa tamamladığınızda durumu geri yükle</span><span class="sxs-lookup"><span data-stu-id="7cef7-181">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="7cef7-182">Bir yöntemi çağıranlar, bu yöntemde özel durum oluşturulduğunda bunun yan etkileri olmayacağını varsayabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7cef7-182">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="7cef7-183">Örneğin, bir hesaptan geri alınmasının ve başka bir hesabı ürünü para aktarımı kodunuz ve havale yürütülürken bir özel durum mevzuatı etkin kalmasını istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7cef7-183">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

<span data-ttu-id="7cef7-184">Yukarıdaki yöntemi doğrudan özel durumları oluşturmaz, ancak mevzuatı tersine havale işlem başarısız olursa, böylece biçimde geliştirmelisiniz yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7cef7-184">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="7cef7-185">Bu durumu yönetmek için bir havale işlem tarafından oluşturulan özel durumlar yakalayın ve geri çekilen alma yoludur.</span><span class="sxs-lookup"><span data-stu-id="7cef7-185">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

<span data-ttu-id="7cef7-186">Bu örnek kullanımını gösterir `throw` inceleyin gerek kalmadan gerçek sorunun nedenini görmek çağıranlar kolaylaştırmak özgün özel yeniden harekete geçirileceğini <xref:System.Exception.InnerException> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7cef7-186">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="7cef7-187">Yeni bir özel durum ve iç özel durum olarak özgün özel durumu içerecek şekilde bir alternatiftir:</span><span class="sxs-lookup"><span data-stu-id="7cef7-187">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

## <a name="see-also"></a><span data-ttu-id="7cef7-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cef7-188">See also</span></span>

- [<span data-ttu-id="7cef7-189">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="7cef7-189">Exceptions</span></span>](index.md)
