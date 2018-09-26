---
title: C# 6 - C# Kılavuzu yenilikler nelerdir?
description: C# sürüm 6'daki yeni özelliklerin öğrenin
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: f6f953eacc935d38cc7d45173109c96c52a5e2f3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208191"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="6f05c-103">C# 6 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="6f05c-103">What's New in C# 6</span></span>

<span data-ttu-id="6f05c-104">C# 6.0 sürüm, geliştiriciler için üretkenliği artıran birçok özellik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6f05c-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="6f05c-105">Bu sürümde aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6f05c-105">Features in this release include:</span></span>

* <span data-ttu-id="6f05c-106">[Salt okunur otomatik özelliklerde](#read-only-auto-properties):</span><span class="sxs-lookup"><span data-stu-id="6f05c-106">[Read-only Auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="6f05c-107">Salt okunur otomatik yalnızca oluşturucularda ayarlanabilen özelliklerde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-107">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="6f05c-108">[Otomatik-özellik başlatıcıları](#auto-property-initializers):</span><span class="sxs-lookup"><span data-stu-id="6f05c-108">[Auto-Property Initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="6f05c-109">Otomatik özellik başlangıç değeri ayarlamak için başlatma ifadeleri yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-109">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="6f05c-110">[İfade gövdeli işlev üyeleri](#expression-bodied-function-members):</span><span class="sxs-lookup"><span data-stu-id="6f05c-110">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="6f05c-111">Lambda ifadeleri kullanarak bir satır içi yöntemler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-111">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="6f05c-112">[' using static](#using-static):</span><span class="sxs-lookup"><span data-stu-id="6f05c-112">[using static](#using-static):</span></span>
    - <span data-ttu-id="6f05c-113">Tek bir sınıfın tüm yöntemler geçerli bir ad alanına içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-113">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="6f05c-114">[Null - Koşullu işleçler](#null-conditional-operators):</span><span class="sxs-lookup"><span data-stu-id="6f05c-114">[Null - conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="6f05c-115">Null null koşullu işleci ile hala denetleme sırasında bir nesnenin üyelerine kısaca ve güvenli bir şekilde erişebilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-115">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="6f05c-116">[Dize ilişkilendirme](#string-interpolation):</span><span class="sxs-lookup"><span data-stu-id="6f05c-116">[String Interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="6f05c-117">Satır içi ifadeler yerine konumsal bağımsız değişkenlerle ifadeleri biçimlendirme dizesi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-117">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="6f05c-118">[Özel durum filtreleri](#exception-filters):</span><span class="sxs-lookup"><span data-stu-id="6f05c-118">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="6f05c-119">İfadeleri özelliklerine göre özel durum veya diğer program durumunu yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-119">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="6f05c-120">[nameof ifadeleri](#nameof-expressions):</span><span class="sxs-lookup"><span data-stu-id="6f05c-120">[nameof Expressions](#nameof-expressions):</span></span>
    - <span data-ttu-id="6f05c-121">Semboller dize temsillerini oluşturmak derleyici izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-121">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="6f05c-122">[await catch ve finally bloklarında](#await-in-catch-and-finally-blocks):</span><span class="sxs-lookup"><span data-stu-id="6f05c-122">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="6f05c-123">Kullanabileceğiniz `await` ifadeleri önceden izin verilmeyen bir konumda.</span><span class="sxs-lookup"><span data-stu-id="6f05c-123">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="6f05c-124">[Dizin başlatıcılar](#index-initializers):</span><span class="sxs-lookup"><span data-stu-id="6f05c-124">[index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="6f05c-125">Sıra kapsayıcılar yanı sıra, ilişkili kapsayıcılar için başlatma ifadeleri yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-125">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="6f05c-126">[Koleksiyon başlatıcıları için genişletme yöntemleri](#extension-add-methods-in-collection-initializers):</span><span class="sxs-lookup"><span data-stu-id="6f05c-126">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="6f05c-127">Koleksiyon başlatıcıları, üye yöntemleri yanı sıra erişilebilir genişletme yöntemleri üzerinde güvenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-127">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="6f05c-128">[Geliştirilmiş aşırı yükleme çözünürlüğü](#improved-overload-resolution):</span><span class="sxs-lookup"><span data-stu-id="6f05c-128">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="6f05c-129">Belirsiz yöntem çağrıları artık daha önce oluşturulan bazı yapıları doğru bir şekilde çözün.</span><span class="sxs-lookup"><span data-stu-id="6f05c-129">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>
* <span data-ttu-id="6f05c-130">[`deterministic` derleyici seçeneği](#deterministic-compiler-output):</span><span class="sxs-lookup"><span data-stu-id="6f05c-130">[`deterministic` compiler option](#deterministic-compiler-output):</span></span>
    - <span data-ttu-id="6f05c-131">Sonraki derlemeleri aynı kaynak aynı ikili çıkışı Oluştur belirleyici derleyici seçeneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-131">The deterministic compiler option ensures that subsequent compilations of the same source generate the same binary output.</span></span>

<span data-ttu-id="6f05c-132">Bu özellikler genel etkisini de daha okunabilir daha kısa kod yazma ' dir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-132">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="6f05c-133">Birçok ortak uygulamalar için daha az seremoni söz dizimi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6f05c-133">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="6f05c-134">Tasarım hedefi ile daha az seremoni görmek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-134">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="6f05c-135">Bu özellikler de öğrenin ve daha üretken olmanıza, daha okunabilir bir kod yazma ve daha çekirdek özellikleri dil yapıları üzerinde yoğunlaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-135">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="6f05c-136">Bu konunun geri kalanı bu özelliklerin her biri hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-136">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="6f05c-137">Otomatik-özellik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="6f05c-137">Auto-Property enhancements</span></span>

<span data-ttu-id="6f05c-138">Otomatik olarak uygulanan özellikler (genellikle 'otomatik-Özellikler' adlandırılır) sözdizimi kolay, çok basit get olan özellikler oluşturma ve ayarlama erişimci:</span><span class="sxs-lookup"><span data-stu-id="6f05c-138">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="6f05c-139">Ancak, bu basit söz dizimi otomatik özelliklerde kullanarak destekleyebilir tasarımları tür sınırlı.</span><span class="sxs-lookup"><span data-stu-id="6f05c-139">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="6f05c-140">Daha fazla senaryoda kullanmak C# 6 otomatik özelliklerde özellikleri geliştirir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-140">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="6f05c-141">Bildirme ve Destek alanı çoğunlukla el ile düzenleme hakkında daha ayrıntılı sözdizimi dönmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6f05c-141">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="6f05c-142">Yeni sözdizimi senaryoları için salt okunur özellikler ve değişken depolama otomatik-özellik arkasında başlatma için yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-142">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="6f05c-143">Salt okunur otomatik özellikleri</span><span class="sxs-lookup"><span data-stu-id="6f05c-143">Read-only auto-properties</span></span>

<span data-ttu-id="6f05c-144">*Salt okunur otomatik özelliklerde* değişmez türleri oluşturmak için daha kısa bir söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-144">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="6f05c-145">Özel ayarlayıcılar bildirmek için C# ' ın önceki sürümlerinde sabit türlerine alabilir en yakın şöyleydi:</span><span class="sxs-lookup"><span data-stu-id="6f05c-145">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="6f05c-146">Bu söz dizimini kullanarak derleyicinin türü gerçekten sabit olduğunu garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="6f05c-146">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="6f05c-147">Bu yalnızca, zorlar `FirstName` ve `LastName` sınıf dışındaki herhangi bir kod öğesinden özellikleri değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="6f05c-147">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="6f05c-148">Salt okunur otomatik özelliklerde true salt okunur davranışı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6f05c-148">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="6f05c-149">Otomatik özelliği yalnızca bir alma erişimcisi ile bildirdiğiniz:</span><span class="sxs-lookup"><span data-stu-id="6f05c-149">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="6f05c-150">`FirstName` Ve `LastName` özellikleri yalnızca Oluşturucu gövdesinde ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="6f05c-150">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="6f05c-151">Ayarlanmaya çalışılırken `LastName` içinde başka bir yöntem oluşturur bir `CS0200` derleme hatası:</span><span class="sxs-lookup"><span data-stu-id="6f05c-151">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="6f05c-152">Bu özellik sabit türleri oluşturma ve daha net ve uygun otomatik-özellik söz dizimini kullanarak true dil desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-152">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="6f05c-153">Bu söz dizimi ekleme değil erişilebilir bir yöntemi kaldırmaz gerekiyorsa bir [ikili uyumlu değişiklik](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="6f05c-153">If adding this syntax does not not remove an accessible method, it is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="6f05c-154">Otomatik-özellik başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="6f05c-154">Auto-Property Initializers</span></span>

<span data-ttu-id="6f05c-155">*Otomatik-özellik başlatıcıları* başlangıç değeri otomatik özellik için özellik bildiriminde bir parçası olarak bildirmenize.</span><span class="sxs-lookup"><span data-stu-id="6f05c-155">*Auto-Property Initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="6f05c-156">Önceki sürümlerde, bu özellikleri ayarlayıcılar olması gerekir ve yedekleme alanı tarafından kullanılan veri depolama alanı başlatmak için ayarlayıcı'ı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-156">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="6f05c-157">Bu sınıf adı ve öğrencinin derece listesini içeren bir öğrenci için göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="6f05c-157">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
<span data-ttu-id="6f05c-158">Bu sınıf büyüdükçe, diğer oluşturucular içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-158">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="6f05c-159">Her Oluşturucu, bu alanı başlatmak gereken veya hatalara neden.</span><span class="sxs-lookup"><span data-stu-id="6f05c-159">Each constructor needs to initialize this field, or you'll introduce errors.</span></span>

<span data-ttu-id="6f05c-160">C# 6 otomatik-özellik bildiriminde otomatik-özellik tarafından kullanılan depolama alanı için bir başlangıç değeri atamanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="6f05c-160">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="6f05c-161">`Grades` Üyesi olduğu bildirilir başlatılır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-161">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="6f05c-162">Bu, tam bir kez başlatma gerçekleştirmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-162">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="6f05c-163">Başlatma ile ortak arabirim için depolama ayırmayı excel'dir kolaylaştırarak özellik bildiriminde bir parçasıdır `Student` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6f05c-163">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="6f05c-164">Özellik başlatıcıları gösterildiği salt okunur özellikler yanı sıra okuma/yazma özellikleri burada kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-164">Property Initializers can be used with read/write properties as well as read-only properties, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="6f05c-165">İfade gövdeli işlev üyeleri</span><span class="sxs-lookup"><span data-stu-id="6f05c-165">Expression-bodied function members</span></span>

<span data-ttu-id="6f05c-166">Bir ifade olarak temsil edilebilir yalnızca bir deyim gövdesi çok sayıda biz yazma üyeleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="6f05c-166">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="6f05c-167">Bunun yerine bir ifade gövdeli üye yazarak bu söz dizimini azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-167">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="6f05c-168">Bu yöntemler ve salt okunur özellikler için çalışır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-168">It works for methods and read-only properties.</span></span> <span data-ttu-id="6f05c-169">Örneğin, bir geçersiz kılma `ToString()` genellikle iyi bir adaydır:</span><span class="sxs-lookup"><span data-stu-id="6f05c-169">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="6f05c-170">İfade gövdeli üyeler de salt okunur özellikler de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f05c-170">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="6f05c-171">Varolan bir üye ifadesi bodied üyesine değiştirme bir [ikili uyumlu değişiklik](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="6f05c-171">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>


## <a name="using-static"></a><span data-ttu-id="6f05c-172">' Using static</span><span class="sxs-lookup"><span data-stu-id="6f05c-172">using static</span></span>

<span data-ttu-id="6f05c-173">*'Using static* geliştirme, tek bir sınıfın statik yöntemleri içeri aktarmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-173">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="6f05c-174">Daha önce `using` beyanının içeri aktarılıp, bir ad alanındaki tüm türleri.</span><span class="sxs-lookup"><span data-stu-id="6f05c-174">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="6f05c-175">Genellikle bir sınıfın statik yöntemleri kodumuz kullanırız.</span><span class="sxs-lookup"><span data-stu-id="6f05c-175">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="6f05c-176">Art arda sınıf adını yazarak kodunuzu anlamını gizlememeniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-176">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="6f05c-177">Birçok sayısal hesaplamalar sınıfları yazdığınızda yaygın bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-177">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="6f05c-178">Kodunuz ile littered <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> ve diğer çağrılar farklı yöntemlere <xref:System.Math> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6f05c-178">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="6f05c-179">Yeni `using static` söz dizimi yapabilir bu sınıfların okumak için çok daha net.</span><span class="sxs-lookup"><span data-stu-id="6f05c-179">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="6f05c-180">Kullanmakta olduğunuz sınıfı belirtin:</span><span class="sxs-lookup"><span data-stu-id="6f05c-180">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="6f05c-181">Artık, herhangi bir statik yöntemdeki kullanabileceğiniz <xref:System.Math> niteleme olmadan sınıfı <xref:System.Math> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6f05c-181">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="6f05c-182"><xref:System.Math> Sınıfı, herhangi bir örnek yöntem içermediğinden bu özellik için harika kullanım durumu değildir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-182">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="6f05c-183">Ayrıca `using static` bir sınıfın statik yöntemleri statik bir sınıf için içeri aktarma ve örnek yöntemler.</span><span class="sxs-lookup"><span data-stu-id="6f05c-183">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="6f05c-184">En kullanışlı örneklerden biridir <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="6f05c-184">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="6f05c-185">Tam nitelikli sınıf adınız kullanmalısınız `System.String` statik olarak using deyimi.</span><span class="sxs-lookup"><span data-stu-id="6f05c-185">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="6f05c-186">Kullanamazsınız `string` anahtar sözcüğü yerine.</span><span class="sxs-lookup"><span data-stu-id="6f05c-186">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="6f05c-187">Tanımlanan statik yöntemlerini çağırabilirsiniz <xref:System.String> bu yöntemleri söz konusu sınıfın bir üye olarak niteleme olmadan sınıfı:</span><span class="sxs-lookup"><span data-stu-id="6f05c-187">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="6f05c-188">`static using` Özellik ve uzantı yöntemleri ilginç şekillerde etkileşim ve dil tasarımını, özellikle bu etkileşimlerin bazı kuralları dahil.</span><span class="sxs-lookup"><span data-stu-id="6f05c-188">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="6f05c-189">Varolan önemli değişiklikler herhangi olasılığını en aza indirmek için sizinki de dahil olmak üzere kod tabanlarında hedeftir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-189">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="6f05c-190">Uzantı yöntemleri yalnızca statik bir yöntem olarak değil çağrıldığında yöntem çağırma söz dizimi uzantısı kullanarak çağrıldığında kapsamına dahildir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-190">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="6f05c-191">Bu, LINQ sorgularında sık sık görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-191">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="6f05c-192">İçeri aktararak LINQ desen aktarabilirsiniz <xref:System.Linq.Enumerable>.</span><span class="sxs-lookup"><span data-stu-id="6f05c-192">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="6f05c-193">Bu tüm yöntemleri aktarır <xref:System.Linq.Enumerable> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6f05c-193">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="6f05c-194">Ancak, genişletme yöntemleri genişletme yöntemleri çağrıldığında kapsamına dahildir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-194">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="6f05c-195">Statik yöntem sözdizimini kullanarak çağrılır, bunlar kapsamda değildir:</span><span class="sxs-lookup"><span data-stu-id="6f05c-195">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="6f05c-196">Çünkü bu kararı genişletme yöntemleri, genellikle uzantı metodu çağırma ifadeleri kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-196">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="6f05c-197">Burada statik yöntemi kullanılarak çağrılır nadir durumlarda, söz dizimi belirsizliği olduğu çağırın.</span><span class="sxs-lookup"><span data-stu-id="6f05c-197">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="6f05c-198">Sınıf adı çağrısının bir parçası olarak gerek akıllıca gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="6f05c-198">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="6f05c-199">Bir son özelliği yoktur `static using`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-199">There's one last feature of `static using`.</span></span> <span data-ttu-id="6f05c-200">`static using` Yönergesi, tüm iç içe geçmiş türler de alır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-200">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="6f05c-201">Tüm iç içe geçmiş türler nitelik olmadan başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-201">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="6f05c-202">Null koşullu işleçleri</span><span class="sxs-lookup"><span data-stu-id="6f05c-202">Null-conditional operators</span></span>

<span data-ttu-id="6f05c-203">Null değerler kod zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-203">Null values complicate code.</span></span> <span data-ttu-id="6f05c-204">Değişken değil başvuruluyor emin olmak için her bir erişim denetimi için ihtiyacınız `null`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-204">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="6f05c-205">*Null koşullu işleci* bu denetimleri çok daha kolay ve akıcı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-205">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="6f05c-206">Üye erişimi yalnızca değiştirmek `.` ile `?.`:</span><span class="sxs-lookup"><span data-stu-id="6f05c-206">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="6f05c-207">Yukarıdaki örnekte, değişken `first` atanan `null` kişi nesnesi varsa `null`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-207">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="6f05c-208">Aksi takdirde, değeri atandığını `FirstName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="6f05c-208">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="6f05c-209">En önemlisi de `?.` Bu kod satırı oluşturmaz anlamına gelir bir `NullReferenceException` olduğunda `person` değişkendir `null`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-209">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="6f05c-210">Bunun yerine, short-circuits ve üretir `null`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-210">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="6f05c-211">Ayrıca, bu ifade döndürür Not bir `string`değerini bakılmaksızın `person`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-211">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="6f05c-212">Kestirmeler, söz konusu olduğunda `null` tam ifadeyle eşleşecek döndürülen değerin türü.</span><span class="sxs-lookup"><span data-stu-id="6f05c-212">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="6f05c-213">Genellikle bu yapı ile kullanabileceğiniz *null birleşim* özelliklerinden olduğunda varsayılan değer atamak için işleç `null`:</span><span class="sxs-lookup"><span data-stu-id="6f05c-213">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="6f05c-214">Sağ taraf işleneni `?.` işleci, özellikler veya alanlar için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-214">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="6f05c-215">Koşullu olarak yöntemlerini çağırmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-215">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="6f05c-216">Temsilciler (veya olay işleyicileri) güvenli bir şekilde çağrılacak üye işlevleri null koşullu işleci ile en yaygın kullanımı olan olabilecek `null`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-216">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="6f05c-217">Bu temsilcinin çağırarak yaparsınız `Invoke` yöntemi kullanarak `?.` üye erişim işleci.</span><span class="sxs-lookup"><span data-stu-id="6f05c-217">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="6f05c-218">Bir örnek görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-218">You can see an example in the</span></span>  
<span data-ttu-id="6f05c-219">[desenler temsilci](../delegates-patterns.md#handling-null-delegates) konu.</span><span class="sxs-lookup"><span data-stu-id="6f05c-219">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="6f05c-220">Kurallarına `?.` işleci olun işlecinin sol tarafı yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-220">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="6f05c-221">Bu önemlidir ve olay işleyicilerini kullanarak örnek dahil olmak üzere birçok deyimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-221">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="6f05c-222">Olay işleyicisi kullanım ile başlayalım.</span><span class="sxs-lookup"><span data-stu-id="6f05c-222">Let's start with the event handler usage.</span></span> <span data-ttu-id="6f05c-223">Önceki sürümlerinde C#, aşağıdakine benzer bir kod yazmak için önerilir:</span><span class="sxs-lookup"><span data-stu-id="6f05c-223">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="6f05c-224">Bu, daha basit bir söz dizimi tercih edilen:</span><span class="sxs-lookup"><span data-stu-id="6f05c-224">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="6f05c-225">Yukarıdaki örnekte, bir yarış durumu ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-225">The preceding example introduces a race condition.</span></span> <span data-ttu-id="6f05c-226">`SomethingHappened` Olay karşı işaretlendiğinde aboneleri olabilir `null`, ve olay gerçekleşmeden önce bu aboneleri kaldırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-226">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="6f05c-227">Bu neden bir <xref:System.NullReferenceException> oluşturulması için.</span><span class="sxs-lookup"><span data-stu-id="6f05c-227">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="6f05c-228">Bu ikinci sürüm `SomethingHappened` olay işleyicisi, test edildiğinde null olmayan olabilir, ancak diğer kod bir işleyici kaldırırsa, olay işleyicisi çağrıldığında hala null olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-228">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="6f05c-229">Derleyici için kod oluşturur `?.` sol tarafındaki sağlar işleci (`this.SomethingHappened`), `?.` ifade bir kez değerlendirilir ve sonuç önbelleğe alınır:</span><span class="sxs-lookup"><span data-stu-id="6f05c-229">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="6f05c-230">Sol tarafta yalnızca bir kez değerlendirilir sağlamak da sol tarafındaki yöntem çağrıları dahil olmak üzere herhangi bir ifade kullanmanıza olanak sağlar `?.` bu yan etkilere sahip olsanız bile, yan etkileri yalnızca bir kez meydana şekilde bunlar bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-230">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="6f05c-231">Sunduğumuz içeriğin bir örnekte gördüğünüz [olayları](../events-overview.md#language-support-for-events).</span><span class="sxs-lookup"><span data-stu-id="6f05c-231">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="6f05c-232">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="6f05c-232">String Interpolation</span></span>

<span data-ttu-id="6f05c-233">C# 6 dizeleri bir biçim dizesi ve diğer string değerleri oluşturmak için değerlendirilen ifadeleri oluşturmak için yeni sözdizimi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6f05c-233">C# 6 contains new syntax for composing strings from a format string and expressions that are evaluated to produce other string values.</span></span>

<span data-ttu-id="6f05c-234">Geleneksel olarak, konumsal parametreler gibi bir yöntem kullanmak için gereken `string.Format`:</span><span class="sxs-lookup"><span data-stu-id="6f05c-234">Traditionally, you needed to use positional parameters in a method like `string.Format`:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="6f05c-235">C# 6, yeni [dize ilişkilendirme](../language-reference/tokens/interpolated.md) özelliği Biçim dizesinde ifade katıştırma olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-235">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed the expressions in the format string.</span></span> <span data-ttu-id="6f05c-236">Yalnızca dize ile yazdığınızdan `$`:</span><span class="sxs-lookup"><span data-stu-id="6f05c-236">Simply preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="6f05c-237">Bu ilk örnek için yedek ifadeleri özellik ifadeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-237">This initial example uses property expressions for the substituted expressions.</span></span> <span data-ttu-id="6f05c-238">Herhangi bir ifade kullanmak için bu sözdizimini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-238">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="6f05c-239">Örneğin, bir öğrencinin sınıf noktası ortalama ilişkilendirme bir parçası olarak işlem:</span><span class="sxs-lookup"><span data-stu-id="6f05c-239">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="6f05c-240">Önceki örnekte çalışan, size, çıktısı bulur `Grades.Average()` istediğiniz çok daha fazla ondalık basamak olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-240">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="6f05c-241">Dize ilişkilendirme sözdizimi tüm biçim dizeleri kullanılabilir daha önce biçimlendirme yöntemleri kullanmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="6f05c-241">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="6f05c-242">Küme ayraçları içinde biçim dizeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6f05c-242">You add the format strings inside the braces.</span></span> <span data-ttu-id="6f05c-243">Ekleme bir `:` biçimlendirmek için ifadeyi aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="6f05c-243">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="6f05c-244">Önceki kod satırının değeri biçimlendirir `Grades.Average()` iki ondalık kayan noktalı bir sayı olarak.</span><span class="sxs-lookup"><span data-stu-id="6f05c-244">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="6f05c-245">`:` Her zaman biçimlendirilen ifade ve biçim dizesi arasındaki ayırıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-245">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="6f05c-246">İfadeniz kullandığında bu sorunları ortaya çıkarabilir bir `:` koşullu bir işleç gibi başka bir şekilde:</span><span class="sxs-lookup"><span data-stu-id="6f05c-246">This can introduce problems when your expression uses a `:` in another way, such as a conditional operator:</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="6f05c-247">Önceki örnekte `:` koşullu işleç parçası olmayan biçim dizesinin başlangıcı olarak ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-247">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="6f05c-248">Burada böyle her durumda, ifade düşündüğünüz olarak yorumlamak üzere zorlamanız parantezli ifade çevreleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f05c-248">In all cases where this happens, you can surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="6f05c-249">Küme ayraçları arasında yerleştirebilirsiniz ifadeleri herhangi bir sınırlama yok.</span><span class="sxs-lookup"><span data-stu-id="6f05c-249">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="6f05c-250">Hesaplamaları gerçekleştirmek ve sonucu görüntülemek için bir aradeğerlendirme dizesinde içinde karmaşık bir LINQ Sorgu yürütebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f05c-250">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="6f05c-251">Bu örnekten başka bir dize ilişkilendirme ifadesi bir dize ilişkilendirme ifadesinde bile yuvalayabilirsiniz görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-251">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="6f05c-252">Bu örnek daha daha karmaşık üretim kodunda istersiniz olasılıktır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-252">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="6f05c-253">Bunun yerine, bu özelliğin kapsamını yalnızca tanım olur.</span><span class="sxs-lookup"><span data-stu-id="6f05c-253">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="6f05c-254">Herhangi bir C# deyimi, bir aradeğerlendirme dizesinde arasında ve küme ayraçlarının yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-254">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="6f05c-255">Dize ilişkilendirme ve özel kültürler</span><span class="sxs-lookup"><span data-stu-id="6f05c-255">String interpolation and specific cultures</span></span>

<span data-ttu-id="6f05c-256">Önceki bölümde gösterilen örnekler, geçerli kültür ve dil burada kodu yürütür makine üzerinde kullanarak dizeleri biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="6f05c-256">All the examples shown in the preceding section format the strings using the current culture and language on the machine where the code executes.</span></span> <span data-ttu-id="6f05c-257">Genellikle belirli bir kültür kullanılarak üretilen dize biçimlendirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-257">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="6f05c-258">Yapmak için bir dize ilişkilendirme tarafından üretilen nesne için örtük olarak dönüştürülebilir olgu kullanan <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="6f05c-258">To do that use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString>.</span></span>

<span data-ttu-id="6f05c-259"><xref:System.FormattableString> Örnek biçim dizesi ve dizeleri için dönüştürme önce ifadeleri değerlendirme sonuçlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-259">The <xref:System.FormattableString> instance contains the format string, and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="6f05c-260">Genel yöntemleri kullanabilirsiniz <xref:System.FormattableString> kültür biçimlendirme dizesi bir zaman belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6f05c-260">You can use public methods of <xref:System.FormattableString> to specify the culture when formatting a string.</span></span> <span data-ttu-id="6f05c-261">Örneğin, aşağıdaki örnekte, Alman kültürü kullanarak bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6f05c-261">For example, the following example produces a string using German culture.</span></span> <span data-ttu-id="6f05c-262">(',' Karakteri ondalık ayırıcısı için kullanır ve '.' karakteri olarak binlik ayırıcı.)</span><span class="sxs-lookup"><span data-stu-id="6f05c-262">(It uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="6f05c-263">Daha fazla bilgi için [dize ilişkilendirme](../language-reference/tokens/interpolated.md) konu.</span><span class="sxs-lookup"><span data-stu-id="6f05c-263">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="6f05c-264">Özel durum filtreleri</span><span class="sxs-lookup"><span data-stu-id="6f05c-264">Exception Filters</span></span>

<span data-ttu-id="6f05c-265">Başka bir yeni özelliktir C# 6 *özel durum filtreleri*.</span><span class="sxs-lookup"><span data-stu-id="6f05c-265">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="6f05c-266">Özel durum, belirli bir catch yan tümcesinin ne zaman uygulanacağını belirleme yan tümceleri filtrelerdir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-266">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="6f05c-267">Bir özel durum filtresi için kullanılan ifade olmaması halinde `true`, catch yan tümcesi, bir özel normal işleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-267">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="6f05c-268">İfade değerlendirme sonucu `false`, ardından `catch` yan tümcesi atlandı.</span><span class="sxs-lookup"><span data-stu-id="6f05c-268">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="6f05c-269">Bir kullanım olup olmadığını belirlemek için bir özel durum hakkında bilgileri incelemek için bir `catch` yan tümcesi, özel durumu işleyebilir:</span><span class="sxs-lookup"><span data-stu-id="6f05c-269">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="6f05c-270">Özel durum filtreleri tarafından oluşturulan kodu oluşturulur ve işlenmemiş bir özel durum hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-270">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="6f05c-271">Dile özel durum filtreleri eklenmeden önce aşağıdaki gibi bir kod oluşturmak için ihtiyacınız:</span><span class="sxs-lookup"><span data-stu-id="6f05c-271">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="6f05c-272">Burada bu iki örnek arasındaki değişiklikleri özel durum noktası.</span><span class="sxs-lookup"><span data-stu-id="6f05c-272">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="6f05c-273">Önceki kodda, burada bir `throw` yan tümcesi kullanıldığında, herhangi bir yığın izleme analiz veya kilitlenme bilgi dökümleri incelenmesi öğesinden özel durumun oluştuğu gösterecektir `throw` deyiminde, catch yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6f05c-273">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="6f05c-274">Gerçek özel durum nesnesi orijinal çağrı yığını içerir, ancak bu throw noktası özgün throw noktasının konumunu arasındaki çağrı yığınındaki tüm değişkenler hakkında diğer tüm bilgi kaybı olmadı.</span><span class="sxs-lookup"><span data-stu-id="6f05c-274">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="6f05c-275">Özel durum filtresi kullanarak kodu nasıl işleneceği ile karşılaştırın: özel durum filtresi ifadesi olarak değerlendirilen `false`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-275">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="6f05c-276">Bu nedenle, hiçbir zaman yürütme aşamasına girer `catch` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6f05c-276">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="6f05c-277">Çünkü `catch` yan tümcesi yürütülmez, hiçbir yığın geriye doğru izleme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-277">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="6f05c-278">Yol özgün konum throw daha sonra gerçekleşmesi hata ayıklama etkinlikler için korunur.</span><span class="sxs-lookup"><span data-stu-id="6f05c-278">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="6f05c-279">Alanlar ve özellikler, yalnızca özel durum türü üzerinde kalmak yerine bir özel durumun değerlendirmek gerektiğinde daha fazla hata ayıklama bilgileri korumak için bir özel durum filtresi kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f05c-279">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="6f05c-280">Özel durum filtreleri ile başka bir önerilen düzen, bunları için günlük rutinleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-280">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="6f05c-281">Bu kullanım, özel durum throw noktası korunur bir özel durum filtresi sonucunu verdiğinde bir şekilde de yararlanır `false`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-281">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="6f05c-282">Günlüğe kayıt yöntemi, bağımsız değişken olan koşulsuz olarak döndüren özel bir yöntem olacaktır `false`:</span><span class="sxs-lookup"><span data-stu-id="6f05c-282">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="6f05c-283">Bir özel durum günlüğe kaydetmek istediğiniz her bir catch yan tümcesi ekleyin ve özel durum filtre olarak bu yöntemi kullanın:</span><span class="sxs-lookup"><span data-stu-id="6f05c-283">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="6f05c-284">Özel durumları hiçbir zaman, çünkü yakalanan `LogException` yöntemi her zaman döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-284">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="6f05c-285">Bu her zaman false özel durum filtresi anlamına gelir, bu günlüğü işleyicisi önce herhangi bir özel durum işleyiciler koyabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f05c-285">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="6f05c-286">Yukarıdaki örnekte, bir özel durum filtreleri güvenliğin çok önemli vurgular.</span><span class="sxs-lookup"><span data-stu-id="6f05c-286">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="6f05c-287">Özel durum filtreleri daha genel bir özel durum catch yan tümcesi önce daha belirli bir yeri görünebilir senaryolara olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-287">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="6f05c-288">Birden çok catch yan tümcelerinde yer aynı özel durum türü olması mümkündür:</span><span class="sxs-lookup"><span data-stu-id="6f05c-288">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="6f05c-289">Başka bir önerilen Düzen catch yan tümceleri bir hata ayıklayıcı eklendiğinde özel durumları işleme engeller.</span><span class="sxs-lookup"><span data-stu-id="6f05c-289">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="6f05c-290">Bu teknik, hata ayıklayıcısı ile bir uygulamayı çalıştırmak ve bir özel durum oluştuğunda yürütmeyi durdurmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-290">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="6f05c-291">Yalnızca bir hata ayıklayıcısı iliştirilmemiş olduğunda herhangi bir kurtarma kodu yürütür, böylece kodunuza, bir özel durum filtresi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6f05c-291">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="6f05c-292">Bu kodu ekledikten sonra tüm işlenmemiş özel durumlarda kesin, hata ayıklayıcının ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6f05c-292">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="6f05c-293">Hata ayıklayıcısı altında programı çalıştırın ve hata ayıklayıcı keser her `PerformFailingOperation()` oluşturur bir `RecoverableException`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-293">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="6f05c-294">Catch yan tümcesi false döndüren özel durum filtresi nedeniyle yürütülen gerekmez çünkü hata ayıklayıcı, programınızın keser.</span><span class="sxs-lookup"><span data-stu-id="6f05c-294">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="nameof-expressions"></a><span data-ttu-id="6f05c-295">`nameof` İfadeleri</span><span class="sxs-lookup"><span data-stu-id="6f05c-295">`nameof` Expressions</span></span>

<span data-ttu-id="6f05c-296">`nameof` Bir sembol adı için ifadeyi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-296">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="6f05c-297">Her bir değişken, bir özellik veya üye alan adını ihtiyaç duyduğunuzda çalışma araçları almak için harika bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="6f05c-297">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="6f05c-298">En yaygın birini kullanan için `nameof` bir özel durum nedeniyle bir sembol adını sağlar:</span><span class="sxs-lookup"><span data-stu-id="6f05c-298">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="6f05c-299">Başka bir uygulama XAML tabanlı uygulamalar ile kullanılır `INotifyPropertyChanged` arabirimi:</span><span class="sxs-lookup"><span data-stu-id="6f05c-299">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="6f05c-300">Kullanmanın avantajı `nameof` işleci bir sabit dize üzerinden, araçları sembol anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f05c-300">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="6f05c-301">Sembolü yeniden adlandır için yeniden düzenleme araçları kullanırsanız, içindeki adlandıracak `nameof` ifade.</span><span class="sxs-lookup"><span data-stu-id="6f05c-301">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="6f05c-302">Sabit dizelerini, bu avantajı yoktur.</span><span class="sxs-lookup"><span data-stu-id="6f05c-302">Constant strings don't have that advantage.</span></span> <span data-ttu-id="6f05c-303">Sık kullandığınız düzenleyicinizde kendiniz deneyin: bir değişkeni veya herhangi bir yeniden adlandırma `nameof` ifadeleri de güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-303">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="6f05c-304">`nameof` İfade bağımsız değişkenini nitelenmemiş adı üretir (`LastName` önceki örneklerde) tam adı bağımsız değişkeni için kullanıyor olsanız bile:</span><span class="sxs-lookup"><span data-stu-id="6f05c-304">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="6f05c-305">Bu `nameof` ifade üretir `FirstName`değil `UXComponents.ViewModel.FirstName`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-305">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="6f05c-306">Await catch ve Finally bloklarında</span><span class="sxs-lookup"><span data-stu-id="6f05c-306">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="6f05c-307">C# 5 vardı yerleştirdiğiniz etrafında bazı sınırlamaları `await` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="6f05c-307">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="6f05c-308">Bunlardan biri, C# 6'da kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6f05c-308">One of those has been removed in C# 6.</span></span> <span data-ttu-id="6f05c-309">Artık `await` içinde `catch` veya `finally` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="6f05c-309">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="6f05c-310">Ek await ifadeleri catch ve blokları son olarak bunları nasıl işlendiği karmaşık görünebilir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-310">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="6f05c-311">Bunun nasıl göründüğünü tartışmak için örnek ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="6f05c-311">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="6f05c-312">Herhangi bir zaman uyumsuz yöntemdeki bir await ifadesine kullanabileceğiniz bir finally yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6f05c-312">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="6f05c-313">C# 6 ile catch ifadelerinde await.</span><span class="sxs-lookup"><span data-stu-id="6f05c-313">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="6f05c-314">Bu, genellikle günlük kaydı senaryoları ile kullanılır:</span><span class="sxs-lookup"><span data-stu-id="6f05c-314">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="6f05c-315">Uygulama ayrıntılarını ekleme `await` içinde destek `catch` ve `finally` yan tümceleri davranışı eş zamanlı kod davranışı ile tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f05c-315">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="6f05c-316">Ne zaman yürütülen kod içinde bir `catch` veya `finally` yan tümcesi oluşturmaz, yürütme için uygun görünüyor `catch` yan tümcesinde sonraki çevreleyen bloğu.</span><span class="sxs-lookup"><span data-stu-id="6f05c-316">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="6f05c-317">Geçerli bir özel durum varsa, bu özel durum kaybolur.</span><span class="sxs-lookup"><span data-stu-id="6f05c-317">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="6f05c-318">Beklenen ifadelerinde ile aynı olur `catch` ve `finally` yan tümceleri: uygun bir `catch` , aranır ve varsa, geçerli özel durumun kaybolur.</span><span class="sxs-lookup"><span data-stu-id="6f05c-318">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="6f05c-319">Bu, davranıştır yazmak için önerilir nedeni `catch` ve `finally` yan tümceleri dikkatli bir şekilde, yeni özel durumlar önlemek için.</span><span class="sxs-lookup"><span data-stu-id="6f05c-319">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="6f05c-320">Dizin başlatıcılar</span><span class="sxs-lookup"><span data-stu-id="6f05c-320">Index Initializers</span></span>

<span data-ttu-id="6f05c-321">*Dizin başlatıcılar* koleksiyon başlatıcıları dizin kullanımı ile daha tutarlı hale getirmek iki özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-321">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="6f05c-322">Önceki sürümlerinde, C#, kullanabileceğinizi *koleksiyon başlatıcıları* koleksiyonlarıyla da dahil olmak üzere yalnızca dizisi stili, <xref:System.Collections.Generic.Dictionary%602> anahtar ve değer çiftlerini etrafında ayraç ekleyerek:</span><span class="sxs-lookup"><span data-stu-id="6f05c-322">In earlier releases of C#, you could use *collection initializers* only with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602> by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="6f05c-323">Şimdi ile kullanabilmek için <xref:System.Collections.Generic.Dictionary%602> koleksiyonları ve benzer türleri.</span><span class="sxs-lookup"><span data-stu-id="6f05c-323">Now, you can use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types.</span></span> <span data-ttu-id="6f05c-324">Yeni söz dizimini kullanarak koleksiyona bir dizin atama destekler:</span><span class="sxs-lookup"><span data-stu-id="6f05c-324">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="6f05c-325">Bu özellik, ilişkili kapsayıcılar dizisi kapsayıcıları çeşitli sürümleri için yerinde çürütülen için benzer bir sözdizimi kullanılarak başlatılabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-325">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="6f05c-326">Uzantı `Add` koleksiyon başlatıcıları yöntemleri</span><span class="sxs-lookup"><span data-stu-id="6f05c-326">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="6f05c-327">Toplama başlatma kolaylaştırır başka bir özellik kullanma yeteneğini olduğu bir *genişletme yöntemi* için `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6f05c-327">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="6f05c-328">Bu özellik, Visual Basic ile eşlik için eklendi.</span><span class="sxs-lookup"><span data-stu-id="6f05c-328">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="6f05c-329">Anlamsal olarak yeni öğeler eklemek için farklı bir ada sahip bir yöntemi olan bir özel koleksiyon sınıfı varsa, en yararlı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-329">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="6f05c-330">Örneğin, bu gibi öğrencilere koleksiyonunu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="6f05c-330">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="6f05c-331">`Enroll` Yöntemi bir öğrenci ekler.</span><span class="sxs-lookup"><span data-stu-id="6f05c-331">The `Enroll` method adds a student.</span></span> <span data-ttu-id="6f05c-332">Ancak izleyin değil `Add` deseni.</span><span class="sxs-lookup"><span data-stu-id="6f05c-332">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="6f05c-333">Önceki sürümlerinde C#, koleksiyon başlatıcıları kullanılamadı bir `Enrollment` nesnesi:</span><span class="sxs-lookup"><span data-stu-id="6f05c-333">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="6f05c-334">Artık, ancak yalnızca eşleyen bir genişletme yöntemi oluşturursanız `Add` için `Enroll`:</span><span class="sxs-lookup"><span data-stu-id="6f05c-334">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="6f05c-335">Bu özellik ile neler yaptığına yöntem öğeleri bir koleksiyona adlı bir yöntem ekler eşlemektir `Add` bir genişletme yöntemi yaratarak.</span><span class="sxs-lookup"><span data-stu-id="6f05c-335">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="6f05c-336">Geliştirilmiş aşırı yükleme çözünürlüğü</span><span class="sxs-lookup"><span data-stu-id="6f05c-336">Improved overload resolution</span></span>

<span data-ttu-id="6f05c-337">Son bu özellik, büyük olasılıkla fark olmaz biridir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-337">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="6f05c-338">C# derleyicisinin önceki sürümünü içeren lambda ifadeleri belirsiz bazı yöntem çağrıları bulunduğu yapıları vardı.</span><span class="sxs-lookup"><span data-stu-id="6f05c-338">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="6f05c-339">Bu yöntem göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="6f05c-339">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="6f05c-340">Önceki sürümlerde, C#, yöntem grubu söz dizimini kullanarak bu yöntemini çağırmak başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="6f05c-340">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="6f05c-341">Önceki derleyici doğru arasında ayrım değil `Task.Run(Action)` ve `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="6f05c-341">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="6f05c-342">Önceki sürümlerinde, bir lambda ifadesi bağımsız değişken olarak kullanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="6f05c-342">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="6f05c-343">C# 6 derleyici doğru belirleyen `Task.Run(Func<Task>())` daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-343">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="6f05c-344">Belirleyici derleyici çıkışı</span><span class="sxs-lookup"><span data-stu-id="6f05c-344">Deterministic compiler output</span></span>

<span data-ttu-id="6f05c-345">`-deterministic` Bayt için aynı çıkış derlemesi için aynı kaynak dosyaları art arda gelen derlemesi üretmek için derleyici seçeneği bildirir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-345">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="6f05c-346">Varsayılan olarak, her derleme her derleme üzerinde benzersiz bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="6f05c-346">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="6f05c-347">Derleyici bir zaman damgası ekler ve rastgele sayı bir GUID oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6f05c-347">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="6f05c-348">İçin-derlemeler arasında tutarlılık sağlamak için çıkış bayt karşılaştırmak istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f05c-348">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="6f05c-349">Daha fazla bilgi için [-belirleyici derleyici seçeneği](../language-reference/compiler-options/deterministic-compiler-option.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="6f05c-349">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
