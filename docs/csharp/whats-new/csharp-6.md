---
title: "C# 6 - C# Kılavuzu yenilikler nelerdir?"
description: "C# sürüm 6'deki yeni özelliklerin öğrenin"
keywords: .NET, .NET core
author: BillWagner
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: f3e7a515b1dde52461ab6abf8a9adbe84d27b7c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="e8a40-104">C# 6 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="e8a40-104">What's New in C# 6</span></span>

<span data-ttu-id="e8a40-105">C# 6.0 yayın geliştiriciler için verimliliğini artıran birçok özellik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e8a40-105">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="e8a40-106">Bu sürümdeki özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e8a40-106">Features in this release include:</span></span>

* <span data-ttu-id="e8a40-107">[Salt okunur otomatik özellikleri](#read-only-auto-properties):</span><span class="sxs-lookup"><span data-stu-id="e8a40-107">[Read-only Auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="e8a40-108">Salt okunur otomatik yalnızca kurucularda ayarlanabilecek özelliklerini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-108">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="e8a40-109">[Otomatik özelliği başlatıcıları](#auto-property-initializers):</span><span class="sxs-lookup"><span data-stu-id="e8a40-109">[Auto-Property Initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="e8a40-110">Bir otomatik özelliğinin ilk değeri ayarlamak için başlatma ifadeler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-110">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="e8a40-111">[İşlev ifadesi bodied üyeleri](#expression-bodied-function-members):</span><span class="sxs-lookup"><span data-stu-id="e8a40-111">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="e8a40-112">Lambda ifadeleri kullanma tek satır yöntemleri yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-112">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="e8a40-113">[statik kullanarak](#using-static):</span><span class="sxs-lookup"><span data-stu-id="e8a40-113">[using static](#using-static):</span></span>
    - <span data-ttu-id="e8a40-114">Tek bir sınıfın tüm yöntemleri geçerli ad alanı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-114">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="e8a40-115">[Null - Koşullu işleçler](#null-conditional-operators):</span><span class="sxs-lookup"><span data-stu-id="e8a40-115">[Null - conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="e8a40-116">Null ile null koşullu işleç için hala denetlenirken bir nesnenin üyelerine yönelik olarak kısaca ve güvenli bir şekilde erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-116">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="e8a40-117">[Dize ilişkilendirme](#string-interpolation):</span><span class="sxs-lookup"><span data-stu-id="e8a40-117">[String Interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="e8a40-118">Satır içi ifadeler yerine konumsal bağımsız değişkenler kullanarak ifadeleri biçimlendirme dizesi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-118">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="e8a40-119">[Özel durum filtreleri](#exception-filters):</span><span class="sxs-lookup"><span data-stu-id="e8a40-119">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="e8a40-120">Özel durum veya diğer program durumunu bir özelliğe göre ifadeler yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-120">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="e8a40-121">[nameof ifadeleri](#nameof-expressions):</span><span class="sxs-lookup"><span data-stu-id="e8a40-121">[nameof Expressions](#nameof-expressions):</span></span>
    - <span data-ttu-id="e8a40-122">Simgeler dize temsilini oluşturmak derleyici izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-122">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="e8a40-123">[catch await ve son olarak engeller](#await-in-catch-and-finally-blocks):</span><span class="sxs-lookup"><span data-stu-id="e8a40-123">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="e8a40-124">Kullanabileceğiniz `await` daha önce bunları izin verilmeyen konumları ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="e8a40-124">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="e8a40-125">[Dizin başlatıcıları](#index-initializers):</span><span class="sxs-lookup"><span data-stu-id="e8a40-125">[index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="e8a40-126">Başlatma ifadeleri sıralı kapsayıcıları yanı sıra ilişkilendirilebilir kapsayıcıları için yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-126">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="e8a40-127">[Koleksiyon başlatıcıları için genişletme yöntemleri](#extension-add-methods-in-collection-initializers):</span><span class="sxs-lookup"><span data-stu-id="e8a40-127">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="e8a40-128">Koleksiyon başlatıcıları üye yöntemleri yanı sıra erişilebilir uzantı yöntemleri güvenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-128">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="e8a40-129">[Geliştirilmiş aşırı yükleme çözünürlüğü](#improved-overload-resolution):</span><span class="sxs-lookup"><span data-stu-id="e8a40-129">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="e8a40-130">Belirsiz yöntem çağrılarını şimdi daha önce oluşturulan bazı yapıları doğru şekilde çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="e8a40-130">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>

<span data-ttu-id="e8a40-131">Genel bu özelliklerin de daha okunabilir daha kısa kod yazma etkisidir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-131">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="e8a40-132">Birçok ortak uygulamalar için daha az seremoni sözdizimi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e8a40-132">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="e8a40-133">Daha az seremoni ile tasarım hedefi görmek daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="e8a40-133">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="e8a40-134">Bu özellikler de öğrenin ve daha üretken, daha okunabilir kod yazın ve daha dil yapıları, çekirdek özellikleri yoğunlaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-134">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="e8a40-135">Bu konunun geri kalanında bu özelliklerin her biri hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-135">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="e8a40-136">Otomatik özellik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="e8a40-136">Auto-Property enhancements</span></span> 

<span data-ttu-id="e8a40-137">Otomatik uygulanan özellikler (genellikle 'otomatik-Özellikler' adlandırılır) sözdizimi yaptığı basit get vardı özellikleri oluşturmak çok kolay ve erişimciler ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e8a40-137">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="e8a40-138">Ancak, bu basit sözdizimi otomatik özelliklerini kullanarak destekleyebilir tasarımları türlerini sınırlı.</span><span class="sxs-lookup"><span data-stu-id="e8a40-138">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="e8a40-139">Daha fazla senaryolarda kullanabilmeleri C# 6 otomatik özellikleri yeteneklerini artırır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-139">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="e8a40-140">Geri dönüş bildirme ve kadar sık yedekleme alanını el ile düzenleme hakkında daha ayrıntılı sözdizimi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e8a40-140">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="e8a40-141">Yeni sözdizimini senaryoları salt okunur özellikler ve değişken depolama otomatik özelliği arkasında başlatma yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-141">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="e8a40-142">Salt okunur otomatik özellikleri</span><span class="sxs-lookup"><span data-stu-id="e8a40-142">Read-only auto-properties</span></span>

<span data-ttu-id="e8a40-143">*Salt okunur otomatik özelliklerini* değişmez türleri oluşturmak için daha kısa bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-143">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="e8a40-144">Özel ayarlayıcılar bildirmek için en yakın önceki sürümlerinde, C# değişmez türlerine alabilir oluştu:</span><span class="sxs-lookup"><span data-stu-id="e8a40-144">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="e8a40-145">Bu sözdizimini kullanarak, derleyici türü gerçekten değişmez garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="e8a40-145">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="e8a40-146">Onu yalnızca, zorlar `FirstName` ve `LastName` sınıfı dışında herhangi bir koddan özellikleri değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="e8a40-146">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="e8a40-147">Salt okunur otomatik özellikler doğru salt okunur davranışını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-147">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="e8a40-148">Otomatik özelliği yalnızca bir get erişimcisine bildirin:</span><span class="sxs-lookup"><span data-stu-id="e8a40-148">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="e8a40-149">`FirstName` Ve `LastName` özellikleri yalnızca bir oluşturucu gövdesinde ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="e8a40-149">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="e8a40-150">Ayarlanmaya çalışılırken `LastName` içinde başka bir yöntem oluşturur bir `CS0200` derleme hatası:</span><span class="sxs-lookup"><span data-stu-id="e8a40-150">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="e8a40-151">Bu özellik sabit türleri daha kısa ve uygun otomatik özelliği sözdizimini kullanarak doğru dil için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-151">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="e8a40-152">Otomatik özelliği başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="e8a40-152">Auto-Property Initializers</span></span>

<span data-ttu-id="e8a40-153">*Otomatik özelliği başlatıcıları* özellik bildirimi bir parçası olarak bir otomatik özelliğinin ilk değeri bildirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-153">*Auto-Property Initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="e8a40-154">Önceki sürümlerde, bu özellikleri ayarlayıcılar olması gerekir ve yedekleme alanı tarafından kullanılan veri depolama alanı başlatmak için bu ayarlayıcı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-154">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="e8a40-155">Bu sınıf adı ve öğrencinin dereceleri listesini içeren bir öğrenci için göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e8a40-155">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
<span data-ttu-id="e8a40-156">Bu sınıf büyüdükçe, diğer oluşturucular içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-156">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="e8a40-157">Bu alan başlatmak her Oluşturucusu gerekiyor veya hatalara neden.</span><span class="sxs-lookup"><span data-stu-id="e8a40-157">Each constructor needs to initialize this field, or you'll introduce errors.</span></span>

<span data-ttu-id="e8a40-158">C# 6 otomatik özelliği otomatik özellik bildirimi tarafından kullanılan depolama alanı için bir başlangıç değeri atamanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="e8a40-158">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="e8a40-159">`Grades` Üyesi olduğu bildirilmiş başlatılır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-159">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="e8a40-160">Tam olarak bir kez başlatma işlemini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-160">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="e8a40-161">Başlatma için ortak arabirimi ile depolama ayırma eşitlemek daha kolay özellik bildirimi parçası olan `Student` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e8a40-161">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="e8a40-162">Özellik başlatıcıları gösterildiği gibi salt okunur özellikler yanı sıra okuma/yazma özellikleri ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-162">Property Initializers can be used with read/write properties as well as read-only properties, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="e8a40-163">İşlev ifadesi bodied üyeleri</span><span class="sxs-lookup"><span data-stu-id="e8a40-163">Expression-bodied function members</span></span>

<span data-ttu-id="e8a40-164">Biz yazma üyeleri çok gövdesi bir ifade olarak temsil edilebilir yalnızca bir deyim oluşur.</span><span class="sxs-lookup"><span data-stu-id="e8a40-164">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="e8a40-165">Bunun yerine bir ifade bodied üye yazarak o sözdizimi azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-165">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="e8a40-166">Bu yöntemleri ve salt okunur özellikler için çalışır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-166">It works for methods and read-only properties.</span></span> <span data-ttu-id="e8a40-167">Örneğin, bir geçersiz kılma `ToString()` genellikle mükemmel bir adaydır:</span><span class="sxs-lookup"><span data-stu-id="e8a40-167">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="e8a40-168">İfade bodied üyeleri de salt okunur özellikler de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e8a40-168">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a><span data-ttu-id="e8a40-169">statik kullanma</span><span class="sxs-lookup"><span data-stu-id="e8a40-169">using static</span></span>

<span data-ttu-id="e8a40-170">*Statik kullanarak* geliştirme, tek bir sınıfın statik yöntemleri içeri aktarmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-170">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="e8a40-171">Daha önce `using` beyanının içeri aktarılıp bir ad alanındaki tüm türleri.</span><span class="sxs-lookup"><span data-stu-id="e8a40-171">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="e8a40-172">Genellikle bir sınıfın statik yöntemleri kodumuza kullanırız.</span><span class="sxs-lookup"><span data-stu-id="e8a40-172">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="e8a40-173">Art arda sınıf adını yazarak kodunuzu anlamını soyutlamaması.</span><span class="sxs-lookup"><span data-stu-id="e8a40-173">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="e8a40-174">Birçok sayısal hesaplamalar sınıfları yazdığınızda, ortak bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-174">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="e8a40-175">Kodunuz ile littered <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> ve diğer çağrılar farklı yöntemlere <xref:System.Math> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e8a40-175">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="e8a40-176">Yeni `using static` sözdizimi yapabilir bu sınıfların çok temizleyici okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="e8a40-176">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="e8a40-177">Kullanmakta olduğunuz sınıfı belirtin:</span><span class="sxs-lookup"><span data-stu-id="e8a40-177">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="e8a40-178">Ve şimdi, tüm statik yönteminde kullanabilirsiniz <xref:System.Math> niteleme olmadan sınıfı <xref:System.Math> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e8a40-178">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="e8a40-179"><xref:System.Math> Sınıfı herhangi bir örnek yöntem içermediğinden bu özellik için harika kullanımı söz konusu değildir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-179">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="e8a40-180">Aynı zamanda `using static` statik olan bir sınıfı için bir sınıfın statik yöntemleri alıp yöntemleri örneği.</span><span class="sxs-lookup"><span data-stu-id="e8a40-180">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="e8a40-181">En yararlı örnekler biri <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="e8a40-181">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="e8a40-182">Tam sınıf adını kullanmalısınız `System.String` statik olarak using deyimi.</span><span class="sxs-lookup"><span data-stu-id="e8a40-182">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="e8a40-183">Kullanamazsınız `string` anahtar sözcüğü yerine.</span><span class="sxs-lookup"><span data-stu-id="e8a40-183">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="e8a40-184">Tanımlanan statik yöntemler çağırabilirsiniz <xref:System.String> bu yöntemleri o sınıfın bir üyesi olarak niteleme olmadan sınıfı:</span><span class="sxs-lookup"><span data-stu-id="e8a40-184">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="e8a40-185">`static using` Özelliği ve uzantı yöntemleri ilginç şekillerde etkileşim ve özellikle bu etkileşimler adres bazı kurallar dil tasarım dahil.</span><span class="sxs-lookup"><span data-stu-id="e8a40-185">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="e8a40-186">Varolan önemli değişiklikler herhangi olasılığını en aza indirmek için sizin de dahil olmak üzere olarak kullanılabilecek kod temeli hedeftir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-186">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="e8a40-187">Bir statik yöntem olarak değil çağrıldığında uzantı yöntemi çağırma sözdizimini kullanarak çağrıldığında kapsamında uzantı yöntemleri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-187">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="e8a40-188">Bu LINQ sorguları genellikle görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-188">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="e8a40-189">İçeri aktararak LINQ düzeni aktarabilirsiniz <xref:System.Linq.Enumerable>.</span><span class="sxs-lookup"><span data-stu-id="e8a40-189">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="e8a40-190">Bu tüm yöntemleri alır <xref:System.Linq.Enumerable> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e8a40-190">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="e8a40-191">Ancak, genişletme yöntemleri genişletme yöntemleri olarak çağrıldığında kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-191">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="e8a40-192">Statik yöntem sözdizimi kullanılarak çağrılır varsa bunlar kapsamında değildir:</span><span class="sxs-lookup"><span data-stu-id="e8a40-192">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="e8a40-193">Genişletme yöntemleri, genellikle uzantı yöntemi çağırma ifadeler kullanarak denir çünkü bu bir karardır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-193">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="e8a40-194">Bunlar statik yöntemini kullanarak burada adlandırılır nadir durumda karışıklığı çözmek için olan sözdizimi çağırın.</span><span class="sxs-lookup"><span data-stu-id="e8a40-194">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="e8a40-195">Sınıf adı çağırma bir parçası olarak gerektiren akıllıca gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="e8a40-195">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="e8a40-196">Bir son özelliğini yok `static using`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-196">There's one last feature of `static using`.</span></span> <span data-ttu-id="e8a40-197">`static using` Yönergesi de tüm iç içe geçmiş türler alır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-197">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="e8a40-198">Bu tüm iç içe geçmiş türler niteliğe olmadan başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-198">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="e8a40-199">Null-conditional işleçleri</span><span class="sxs-lookup"><span data-stu-id="e8a40-199">Null-conditional operators</span></span>

<span data-ttu-id="e8a40-200">Null değerler kod zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-200">Null values complicate code.</span></span> <span data-ttu-id="e8a40-201">Her erişim değişkenlerinin değil başvurusunun kaldırılmasının emin olmak için kontrol etmeniz `null`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-201">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="e8a40-202">*Null koşullu işleç* bu denetimlerini çok daha kolay ve akıcı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-202">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="e8a40-203">Üye erişimi yalnızca Değiştir `.` ile `?.`:</span><span class="sxs-lookup"><span data-stu-id="e8a40-203">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="e8a40-204">Önceki örnekte, değişken `first` atanan `null` kişi nesne ise `null`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-204">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="e8a40-205">Değeri, aksi takdirde, atanan `FirstName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="e8a40-205">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="e8a40-206">En önemlisi, `?.` Bu kod satırı oluşturmayacak anlamına gelir bir `NullReferenceException` zaman `person` değişken `null`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-206">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="e8a40-207">Bunun yerine, short-circuits ve üreten `null`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-207">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="e8a40-208">Ayrıca, bu deyim döndürür Not bir `string`değerinin ne olursa olsun `person`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-208">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="e8a40-209">Kestirmeler, söz konusu olduğunda `null` tam ifadeyle eşleşecek döndürülen değeri belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="e8a40-209">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="e8a40-210">Bu yapı ile genellikle kullanabilirsiniz *null birleştirmesi* özelliklerinden biri olduğunda, varsayılan değerleri atamak için işleci `null`:</span><span class="sxs-lookup"><span data-stu-id="e8a40-210">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="e8a40-211">Sağ taraftaki yan işleneni `?.` işleci özellikler veya alanlar için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-211">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="e8a40-212">Koşullu yöntemleri çağırmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-212">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="e8a40-213">Üye işlevleri null koşullu işleç ile en yaygın kullanımı güvenle temsilciler (veya olay işleyicileri) çağırmaktır olabilecek `null`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-213">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="e8a40-214">Siz temsilcinin çağırarak gerçekleştirirsiniz `Invoke` yöntemini kullanarak `?.` üye erişimi işleci.</span><span class="sxs-lookup"><span data-stu-id="e8a40-214">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="e8a40-215">Bir örneğe bakın</span><span class="sxs-lookup"><span data-stu-id="e8a40-215">You can see an example in the</span></span>  
<span data-ttu-id="e8a40-216">[desenler temsilci](../delegates-patterns.md#handling-null-delegates) konu.</span><span class="sxs-lookup"><span data-stu-id="e8a40-216">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="e8a40-217">Kurallarına `?.` işleci olun işlecinin sol taraftaki yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-217">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="e8a40-218">Bu önemlidir ve olay işleyicilerini kullanarak örnek dahil olmak üzere birçok deyimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-218">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="e8a40-219">Olay işleyici kullanımıyla başlayalım.</span><span class="sxs-lookup"><span data-stu-id="e8a40-219">Let's start with the event handler usage.</span></span> <span data-ttu-id="e8a40-220">Önceki sürümlerinde C#, aşağıdakine benzer bir kod yazmak için önerilir:</span><span class="sxs-lookup"><span data-stu-id="e8a40-220">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="e8a40-221">Bu, daha basit bir söz dizimi tercih edilen:</span><span class="sxs-lookup"><span data-stu-id="e8a40-221">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="e8a40-222">Önceki örnekte bir yarış durumu sunar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-222">The preceding example introduces a race condition.</span></span> <span data-ttu-id="e8a40-223">`SomethingHappened` Olay karşı işaretlendiğinde aboneleri olabilir `null`, ve olay tetiklenir önce bu aboneleri kaldırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-223">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="e8a40-224">Neden bir <xref:System.NullReferenceException> oluşturulmasına.</span><span class="sxs-lookup"><span data-stu-id="e8a40-224">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="e8a40-225">Bu ikinci sürümünde `SomethingHappened` olay işleyicisi sınandığında null olmayan olabilir, ancak başka bir kod bir işleyici kaldırırsa, olay işleyicisi çağrıldığında hala null olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-225">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="e8a40-226">Derleyici için kod oluşturur `?.` sol tarafındaki sağlar işleci (`this.SomethingHappened`), `?.` ifade kez değerlendirilir ve sonucu önbelleğe alınır:</span><span class="sxs-lookup"><span data-stu-id="e8a40-226">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="e8a40-227">Sol tarafta yalnızca bir kez değerlendirilir sağlama da sol tarafındaki yöntem çağrıları dahil olmak üzere herhangi bir ifade kullanabilmenizi sağlar `?.` bu yan etkileri sahip olsa bile yan etkileri yalnızca bir kez gerçekleşebilir, yani bir kez değerlendirilme.</span><span class="sxs-lookup"><span data-stu-id="e8a40-227">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="e8a40-228">Bizim içerik örnek görebilirsiniz [olayları](../events-overview.md#language-support-for-events).</span><span class="sxs-lookup"><span data-stu-id="e8a40-228">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="e8a40-229">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="e8a40-229">String Interpolation</span></span>

<span data-ttu-id="e8a40-230">C# 6 bir biçim dizesi ve diğer dize değerlerini üretmek için değerlendirilen bir ifade dizelerden oluşturmak için yeni sözdizimi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e8a40-230">C# 6 contains new syntax for composing strings from a format string and expressions that can be evaluated to produce other string values.</span></span>

<span data-ttu-id="e8a40-231">Konumsal parametreler gibi bir yöntem kullanmak için gereken geleneksel olarak, `string.Format`:</span><span class="sxs-lookup"><span data-stu-id="e8a40-231">Traditionally, you needed to use positional parameters in a method like `string.Format`:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="e8a40-232">C# 6 ile yeni dize ilişkilendirme özellik Biçim dizesinde ifade katıştırma olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-232">With C# 6, the new string interpolation feature enables you to embed the expressions in the format string.</span></span> <span data-ttu-id="e8a40-233">Basit yazdığınızdan dizesiyle `$`:</span><span class="sxs-lookup"><span data-stu-id="e8a40-233">Simple preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="e8a40-234">Bu ilk örnek değiştirilen ifadeler için değişken ifadeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-234">This initial example used variable expressions for the substituted expressions.</span></span> <span data-ttu-id="e8a40-235">Herhangi bir ifade kullanmak için bu sözdizimini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-235">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="e8a40-236">Örneğin, öğrencinin Not noktası ortalaması ilişkilendirme bir parçası olarak işlem:</span><span class="sxs-lookup"><span data-stu-id="e8a40-236">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="e8a40-237">Önceki örnekte çalışan, size, çıktı için bulur `Grades.Average()` istediğiniz olandan daha fazla ondalık hane olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-237">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="e8a40-238">Dize ilişkilendirme sözdizimi tüm biçim dizeleri kullanılabilir önceki biçimlendirme yöntemlerine kullanılmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="e8a40-238">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="e8a40-239">Biçim dizeleri kaşlı ayraçlar içinde ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e8a40-239">You add the format strings inside the braces.</span></span> <span data-ttu-id="e8a40-240">Ekleme bir `:` ifade biçimlendirmek için aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="e8a40-240">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="e8a40-241">Önceki kod satırı ile değeri biçimlendirir `Grades.Average()` iki ondalık basamak içeren bir kayan noktalı sayı olarak.</span><span class="sxs-lookup"><span data-stu-id="e8a40-241">The preceding line of code will format the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="e8a40-242">`:` Her zaman biçimlendirilen ifadesi ve biçim dizesi arasındaki ayırıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-242">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="e8a40-243">İfadeniz kullandığında, bu sorunları ortaya çıkarabilir bir `:` koşullu bir işleç gibi başka bir şekilde:</span><span class="sxs-lookup"><span data-stu-id="e8a40-243">This can introduce problems when your expression uses a `:` in another way, such as a conditional operator:</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="e8a40-244">Önceki örnekte `:` koşullu işleç parçası olmayan biçim dizesi başlayan olarak ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-244">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="e8a40-245">Burada bu gerçekleşir tüm durumlarda ifade düşündüğünüz olarak ifade yorumlamaya derleyici zorlamak için parantez ile çevreleyen:</span><span class="sxs-lookup"><span data-stu-id="e8a40-245">In all cases where this happens, you can surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="e8a40-246">Kaşlı ayraç yerleştirebilirsiniz ifadeleri sınırlamalar değil.</span><span class="sxs-lookup"><span data-stu-id="e8a40-246">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="e8a40-247">Karmaşık bir LINQ Sorgu sonucu görüntülemek ve hesaplamalar gerçekleştirmek için Ara değerli bir dize içinde çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e8a40-247">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="e8a40-248">Bir dize ilişkilendirme ifadesi başka bir dize ilişkilendirme deyimi içinde bile geçirebilmenize bu örnekten görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-248">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="e8a40-249">Bu örnek daha daha karmaşık üretim kodunda istersiniz olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-249">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="e8a40-250">Bunun yerine, yalnızca tanım özellik derecesini.</span><span class="sxs-lookup"><span data-stu-id="e8a40-250">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="e8a40-251">Ara değerli bir dize süslü ayraçlar arasında herhangi bir C# ifade yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-251">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="e8a40-252">Dize ilişkilendirme ve belirli kültürler</span><span class="sxs-lookup"><span data-stu-id="e8a40-252">String interpolation and specific cultures</span></span>

<span data-ttu-id="e8a40-253">Önceki bölümde gösterilen tüm örnekler burada kodu yürütür makinede dil ve geçerli kültürü kullanarak dizeleri biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-253">All the examples shown in the preceding section will format the strings using the current culture and language on the machine where the code executes.</span></span> <span data-ttu-id="e8a40-254">Genellikle bir kültürü kullanarak üretilen dize biçiminde gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-254">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="e8a40-255">Bir dize ilişkilendirme üretilen nesne ya da örtük bir dönüştürme sahip türüdür <xref:System.String> veya <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="e8a40-255">The object produced from a string interpolation is a type that has an implicit conversion to either <xref:System.String> or <xref:System.FormattableString>.</span></span>

<span data-ttu-id="e8a40-256"><xref:System.FormattableString> Türü biçim dizesi ve bağımsız değişkenler dizeleri dönüştürme önce değerlendirme sonuçlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-256">The <xref:System.FormattableString> type contains the format string, and the results of evaluating the arguments before converting them to strings.</span></span> <span data-ttu-id="e8a40-257">Ortak yöntemlerini kullanabilirsiniz <xref:System.FormattableString> bir dize biçimlendirme sırasında kültür belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="e8a40-257">You can use public methods of <xref:System.FormattableString> to specify the culture when formatting a string.</span></span> <span data-ttu-id="e8a40-258">Örneğin, aşağıdaki Almanca dil ve kültür kullanarak bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8a40-258">For example, the following will produce a string using German as the language and culture.</span></span> <span data-ttu-id="e8a40-259">(İçin ondalık ayırıcı, ',' karakterini kullanır ve '.' karakteri olarak binlik ayırıcı.)</span><span class="sxs-lookup"><span data-stu-id="e8a40-259">(It will use the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = string.Format(null, 
    System.Globalization.CultureInfo.CreateSpecificCulture("de-de"),
    str.GetFormat(), str.GetArguments());
```

> [!NOTE]
> <span data-ttu-id="e8a40-260">Önceki örnekte 1.0.1 .NET Core sürümünde desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e8a40-260">The preceding example is not supported in .NET Core version 1.0.1.</span></span> <span data-ttu-id="e8a40-261">Yalnızca .NET Framework de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-261">It is only supported in the .NET Framework.</span></span>

<span data-ttu-id="e8a40-262">Genel olarak, dize ilişkilendirme ifadeler dizeleri kendi çıktı olarak üretir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-262">In general, string interpolation expressions produce strings as their output.</span></span> <span data-ttu-id="e8a40-263">Bununla birlikte, dize biçimlendirmek için kullanılan kültür üzerinde daha fazla denetim istediğinizde, belirli bir çıkış belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-263">However, when you want greater control over the culture used to format the string, you can specify a specific output.</span></span>  <span data-ttu-id="e8a40-264">Genellikle gereken bir özellik varsa, kolay belirli kültür biçimlendirme etkinleştirmek için genişletme yöntemleri olarak kullanışlı yöntemler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-264">If this is a capability you often need, you can create convenience methods, as extension methods, to enable easy formatting with specific cultures.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="e8a40-265">Özel durum filtreleri</span><span class="sxs-lookup"><span data-stu-id="e8a40-265">Exception Filters</span></span>

<span data-ttu-id="e8a40-266">C# 6 başka bir yeni özelliği *özel durum filtreleri*.</span><span class="sxs-lookup"><span data-stu-id="e8a40-266">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="e8a40-267">Özel durum filtreleri verilen catch yan tümcesinin ne zaman uygulanacağını belirleme tümceler var.</span><span class="sxs-lookup"><span data-stu-id="e8a40-267">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="e8a40-268">Bir özel durum filtresi için kullanılan ifade değerlendiren varsa `true`, catch yan tümcesi, özel durum normal işleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-268">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="e8a40-269">İfade değerlendirilirse `false`, sonra `catch` yan tümcesi atlandı.</span><span class="sxs-lookup"><span data-stu-id="e8a40-269">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="e8a40-270">Bir kullanım olduğunu belirlemek için bir özel durum bilgilerini incelemek için bir `catch` yan tümcesi, özel durumu işleyebilir:</span><span class="sxs-lookup"><span data-stu-id="e8a40-270">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="e8a40-271">Özel durum filtreleri tarafından oluşturulan kodu oluşturulur ve işlenmemiş bir özel durum hakkında daha iyi bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-271">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="e8a40-272">Özel durum filtreleri diline eklenmeden önce aşağıdaki gibi bir kod oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="e8a40-272">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="e8a40-273">Özel değişiklikler bu iki örnek arasında olduğu durum noktası.</span><span class="sxs-lookup"><span data-stu-id="e8a40-273">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="e8a40-274">Önceki kodda, burada bir `throw` yan tümcesi kullanıldığında, özel durumu, herhangi bir yığın izleme çözümlemesi veya kilitlenme bilgi dökümleri incelenmesi gösterecektir `throw` catch yan tümcesi deyiminde.</span><span class="sxs-lookup"><span data-stu-id="e8a40-274">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="e8a40-275">Gerçek özel durum nesnesi özgün çağrı yığını içerir, ancak bu throw noktası ve özgün throw noktasının konumunu arasında çağrı yığınında tüm değişkenleri hakkında diğer tüm bilgiler kaybolmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-275">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="e8a40-276">Bir özel durum filtresi kullanarak kodu nasıl işleneceğini ile karşılaştırın: özel durum filtre ifadesi değerlendiren `false`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-276">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="e8a40-277">Bu nedenle, yürütme hiçbir zaman girer `catch` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e8a40-277">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="e8a40-278">Çünkü `catch` yan tümcesi yürütülmez, hiçbir yığın geriye doğru izleme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-278">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="e8a40-279">Anlamına gelir özgün konum throw daha sonra gerçekleşmesi hata ayıklama etkinlikler için korunur.</span><span class="sxs-lookup"><span data-stu-id="e8a40-279">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="e8a40-280">Alanları veya yalnızca özel durum türü üzerinde kalmak yerine bir özel durum özelliklerini değerlendirmek gerektiğinde daha fazla hata ayıklama bilgilerini korumak için bir özel durum filtresi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8a40-280">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="e8a40-281">Özel durum filtreleri önerilen başka bir desenle günlük yordamları için bunları kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-281">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="e8a40-282">Bu kullanım da, özel durum throw noktası korunur bir özel durum filtresi olarak değerlendirildiğinde şekilde yararlanır `false`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-282">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="e8a40-283">Günlüğe kayıt yöntemi, bağımsız değişkeni olan koşulsuz olarak döndüren özel bir yöntem olacaktır `false`:</span><span class="sxs-lookup"><span data-stu-id="e8a40-283">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="e8a40-284">Bir özel durum günlüğe kaydetmek istediğiniz her bir catch yan tümcesi ekleyin ve bu yöntemi özel durum filtre olarak kullanın:</span><span class="sxs-lookup"><span data-stu-id="e8a40-284">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="e8a40-285">Özel durumlar hiçbir zaman, çünkü yakalanan `LogException` yöntem her zaman döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-285">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="e8a40-286">Bu her zaman yanlış özel durum filtresi anlamına gelir, bu günlüğü işleyicisi herhangi bir özel durum işleyicileri önce yerleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e8a40-286">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="e8a40-287">Önceki örnekte bir özel durum filtreleri güvenliğin çok önemli vurgular.</span><span class="sxs-lookup"><span data-stu-id="e8a40-287">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="e8a40-288">Özel durum filtreleri daha genel bir özel durum catch yan tümcesi önce daha belirli bir yere görünebilir senaryoları etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="e8a40-288">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="e8a40-289">Birden çok catch tümcelerinde yer aynı özel durum türü olması mümkündür:</span><span class="sxs-lookup"><span data-stu-id="e8a40-289">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="e8a40-290">Başka bir önerilen deseni, bir hata ayıklayıcısı ekli özel durumları işleme catch yan tümceleri önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e8a40-290">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="e8a40-291">Bu teknik hata ayıklayıcısı ile bir uygulamayı çalıştırın ve bir özel durum yakalandığında yürütme durdurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-291">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="e8a40-292">Böylece yalnızca bir hata ayıklayıcısı değil iliştirildiğinde herhangi bir kurtarma kodu yürütür, kodunuzda bir özel durum filtresi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e8a40-292">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="e8a40-293">Bu kodda ekledikten sonra tüm işlenmeyen özel durumlarını ayırmak için hata ayıklayıcı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e8a40-293">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="e8a40-294">Hata ayıklayıcı altında programını çalıştırın ve hata ayıklayıcısı sonları her `PerformFailingOperation()` oluşturur bir `RecoverableException`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-294">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="e8a40-295">Catch yan tümcesi nedeniyle false döndüren özel durum filtresi yürütülen olmaz çünkü hata ayıklayıcı programınızın keser.</span><span class="sxs-lookup"><span data-stu-id="e8a40-295">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="nameof-expressions"></a><span data-ttu-id="e8a40-296">`nameof`İfadeler</span><span class="sxs-lookup"><span data-stu-id="e8a40-296">`nameof` Expressions</span></span>

<span data-ttu-id="e8a40-297">`nameof` Bir simge adı için ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-297">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="e8a40-298">Bir değişken, bir özellik veya bir üye alanı adını ihtiyaç duyduğunuzda çalışma araçları almak için harika bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="e8a40-298">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="e8a40-299">En yaygın birini kullanan için `nameof` bir özel duruma neden bir sembol adını sağlar:</span><span class="sxs-lookup"><span data-stu-id="e8a40-299">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="e8a40-300">Başka bir uygulama temel XAML uygulamaları ile kullanılır `INotifyPropertyChanged` arabirimi:</span><span class="sxs-lookup"><span data-stu-id="e8a40-300">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="e8a40-301">Kullanmanın avantajı `nameof` bir sabit dize üzerinden işlecidir araçları simgenin anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8a40-301">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="e8a40-302">Simgenin yeniden adlandırmak için yeniden düzenleme araçları kullanırsanız, içindeki adlandıracak `nameof` ifade.</span><span class="sxs-lookup"><span data-stu-id="e8a40-302">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="e8a40-303">Sabit Dizeler Bu avantajı yok.</span><span class="sxs-lookup"><span data-stu-id="e8a40-303">Constant strings don't have that advantage.</span></span> <span data-ttu-id="e8a40-304">Sık kullanılan düzenleyicinizde kendiniz deneyin: bir değişken ve herhangi bir yeniden adlandırma `nameof` ifadeler de güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-304">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="e8a40-305">`nameof` İfade bağımsız değişkeni nitelenmemiş adı üretir (`LastName` önceki örneklerde) dahi bağımsız değişkeni için tam ad kullanın:</span><span class="sxs-lookup"><span data-stu-id="e8a40-305">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="e8a40-306">Bu `nameof` ifade üretir `FirstName`değil `UXComponents.ViewModel.FirstName`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-306">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="e8a40-307">Catch await ve son olarak engeller</span><span class="sxs-lookup"><span data-stu-id="e8a40-307">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="e8a40-308">C# 5 vardı nereye geçici bazı sınırlamaları `await` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="e8a40-308">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="e8a40-309">Bunlardan birini C# 6'kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e8a40-309">One of those has been removed in C# 6.</span></span> <span data-ttu-id="e8a40-310">Artık kullanabilirsiniz `await` içinde `catch` veya `finally` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="e8a40-310">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="e8a40-311">Eklenmesi await catch ifadelerinde ve finally blokları olanlar nasıl işlendiği karmaşık hale gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-311">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="e8a40-312">Bu görünme tartışmak için örnek ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="e8a40-312">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="e8a40-313">Herhangi bir zaman uyumsuz yöntem bekleme deyimde kullanabileceğiniz bir finally yan tümcesinin.</span><span class="sxs-lookup"><span data-stu-id="e8a40-313">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="e8a40-314">C# 6 catch ifadelerinde beklemek.</span><span class="sxs-lookup"><span data-stu-id="e8a40-314">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="e8a40-315">Bu günlük kaydı senaryoları ile en sık kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e8a40-315">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="e8a40-316">Eklemek için uygulama ayrıntılarını `await` içinde destek `catch` ve `finally` yan tümceleri davranışı zaman uyumlu bir kod davranışını ile tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8a40-316">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="e8a40-317">Ne zaman yürütülen kod içinde bir `catch` veya `finally` yan tümcesi oluşturur, yürütme için uygun bir arar `catch` yan tümcesinde sonraki çevresindeki bloğu.</span><span class="sxs-lookup"><span data-stu-id="e8a40-317">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="e8a40-318">Geçerli bir özel durum varsa, bu özel durum kaybolur.</span><span class="sxs-lookup"><span data-stu-id="e8a40-318">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="e8a40-319">Beklemenin ifadelerinde ile aynı olur `catch` ve `finally` yan tümceleri: uygun bir `catch` , aranır ve varsa, geçerli özel durumun kaybolur.</span><span class="sxs-lookup"><span data-stu-id="e8a40-319">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="e8a40-320">Bu davranış önerilen yazmak için nedeni `catch` ve `finally` yan tümceleri dikkatle, yeni özel durumları önlemek için.</span><span class="sxs-lookup"><span data-stu-id="e8a40-320">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="e8a40-321">Dizin başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="e8a40-321">Index Initializers</span></span>

<span data-ttu-id="e8a40-322">*Dizin başlatıcıları* koleksiyon başlatıcıları daha tutarlı hale iki özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-322">*Index Initializers* is one of two features that make collection initializers more consistent.</span></span> <span data-ttu-id="e8a40-323">Önceki sürümlerinde, C#, kullanabileceğinizi *koleksiyon başlatıcıları* dizisi stili koleksiyonlarıyla yalnızca:</span><span class="sxs-lookup"><span data-stu-id="e8a40-323">In earlier releases of C#, you could use *collection initializers* only with sequence style collections:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="e8a40-324">Şimdi, ayrıca bunları ile kullanabileceğiniz <xref:System.Collections.Generic.Dictionary%602> koleksiyonları ve benzer türleri:</span><span class="sxs-lookup"><span data-stu-id="e8a40-324">Now, you can also use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="e8a40-325">Bu özellik ilişkilendirilebilir kapsayıcıları ne birkaç sürümleri için dizisi kapsayıcıları için yerinde bırakıldı için benzer bir sözdizimi kullanılarak başlatılabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-325">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

### <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="e8a40-326">Uzantı `Add` koleksiyon başlatıcıları yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e8a40-326">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="e8a40-327">Kullanma yeteneğini koleksiyonu başlatma kolaylaştırır başka bir özellik olan bir *genişletme yöntemi* için `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e8a40-327">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="e8a40-328">Bu özellik, Visual Basic ile eşlik için eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-328">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="e8a40-329">Bir yöntem anlamsal olarak yeni öğeler eklemek için farklı bir ada sahip olan bir özel koleksiyon sınıfı olduğunda en kullanışlı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-329">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="e8a40-330">Örneğin, şöyle Öğrenciler koleksiyonu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e8a40-330">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="e8a40-331">`Enroll` Yöntemi öğrencinin ekler.</span><span class="sxs-lookup"><span data-stu-id="e8a40-331">The `Enroll` method adds a student.</span></span> <span data-ttu-id="e8a40-332">Ancak bunu IU `Add` düzeni.</span><span class="sxs-lookup"><span data-stu-id="e8a40-332">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="e8a40-333">Önceki sürümlerde, C# ile koleksiyon başlatıcıları kullanılamadı bir `Enrollment` nesnesi:</span><span class="sxs-lookup"><span data-stu-id="e8a40-333">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="e8a40-334">Artık, ancak yalnızca eşleyen bir genişletme yöntemi oluşturursanız `Add` için `Enroll`:</span><span class="sxs-lookup"><span data-stu-id="e8a40-334">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="e8a40-335">Bu özellik ile yapmakta olduğunuz hangi yöntemi adlı bir yöntem bir koleksiyona öğe ekler eşlemektir `Add` bir genişletme yöntemi oluşturarak:</span><span class="sxs-lookup"><span data-stu-id="e8a40-335">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method:</span></span> 

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]
[!code-csharp[ExtensionAddSample](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAddSample)]

## <a name="improved-overload-resolution"></a><span data-ttu-id="e8a40-336">Geliştirilmiş aşırı yükleme çözümü</span><span class="sxs-lookup"><span data-stu-id="e8a40-336">Improved overload resolution</span></span>

<span data-ttu-id="e8a40-337">Son bu özellik, büyük olasılıkla farkına biridir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-337">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="e8a40-338">C# Derleyici'nın önceki sürümünü lambda ifadeleri belirsiz içeren bazı yöntem çağrılarını bulunduğu yapıları vardı.</span><span class="sxs-lookup"><span data-stu-id="e8a40-338">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="e8a40-339">Bu yöntem göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e8a40-339">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="e8a40-340">Önceki sürümlerde, C#, yöntemi Grup sözdizimini kullanarak bu yöntem çağırma başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="e8a40-340">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="e8a40-341">Önceki derleyici doğru arasında ayrım yapmamak `Task.Run(Action)` ve `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="e8a40-341">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="e8a40-342">Önceki sürümlerde, bağımsız değişken olarak bir lambda ifadesi kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="e8a40-342">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="e8a40-343">C# 6 derleyici doğru belirleyen `Task.Run(Func<Task>())` daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="e8a40-343">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>
