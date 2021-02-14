---
description: 'Daha fazla bilgi edinin: uzantı yöntemleri (Visual Basic)'
title: Uzantı Metotları
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 5a1482502b144524c0be90e1c83a38f49b4a4d26
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434361"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="bc2a2-103">Uzantı Yöntemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc2a2-103">Extension Methods (Visual Basic)</span></span>

<span data-ttu-id="bc2a2-104">Uzantı yöntemleri, geliştiricilerin zaten yeni bir türetilmiş tür oluşturmadan tanımlanmış olan veri türlerine özel işlevler eklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-104">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="bc2a2-105">Uzantı yöntemleri, var olan türün bir örnek yöntemi gibi çağrılabilecek bir yöntem yazmayı mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-105">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc2a2-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc2a2-106">Remarks</span></span>

<span data-ttu-id="bc2a2-107">Genişletme yöntemi yalnızca bir `Sub` yordam veya `Function` yordam olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-107">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="bc2a2-108">Uzantı özelliğini, alanı veya olayı tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-108">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="bc2a2-109">Tüm genişletme yöntemlerinin ad alanından uzantı özniteliğiyle işaretlenmesi `<Extension>` <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ve bir [modülde](../../../language-reference/statements/module-statement.md)tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-109">All extension methods must be marked with the extension attribute `<Extension>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace and must be defined in a [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="bc2a2-110">Bir uzantı yöntemi bir modül dışında tanımlanmışsa, Visual Basic Derleyicisi Hata [BC36551](../../../misc/bc36551.md)oluşturur, "uzantı yöntemleri yalnızca modüllerde tanımlanabilir".</span><span class="sxs-lookup"><span data-stu-id="bc2a2-110">If an extension method is defined outside a module, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules".</span></span>

<span data-ttu-id="bc2a2-111">Bir genişletme yöntemi tanımındaki ilk parametre, yöntemin hangi veri türünde genişletiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-111">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="bc2a2-112">Yöntemi çalıştırıldığında, ilk parametre yöntemini çağıran veri türü örneğine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-112">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>

<span data-ttu-id="bc2a2-113">`Extension`Özniteliği yalnızca bir Visual Basic [`Module`](../../../language-reference/statements/module-statement.md) , veya için uygulanabilir [`Sub`](../../../language-reference/statements/sub-statement.md) [`Function`](../../../language-reference/statements/function-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="bc2a2-113">The `Extension` attribute can only be applied to a Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md), or [`Function`](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="bc2a2-114">Bunu bir veya a 'ya uygularsanız `Class` `Structure` Visual Basic Derleyicisi Hata [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md)oluşturuyor, "' Extension" özniteliği yalnızca ' Module ', ' Sub ' veya ' function ' bildirimlerine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-114">If you apply it to a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), "'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations".</span></span>

## <a name="example"></a><span data-ttu-id="bc2a2-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc2a2-115">Example</span></span>

<span data-ttu-id="bc2a2-116">Aşağıdaki örnek, `Print` veri türü için bir uzantı tanımlar <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="bc2a2-116">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="bc2a2-117">Yöntemi `Console.WriteLine` bir dizeyi göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-117">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="bc2a2-118">Yönteminin parametresi, `Print` `aString` yönteminin sınıfını genişlettiğini belirler <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="bc2a2-118">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>

[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

<span data-ttu-id="bc2a2-119">Uzantı metodu tanımının uzantı özniteliğiyle işaretlendiğine dikkat edin `<Extension()>` .</span><span class="sxs-lookup"><span data-stu-id="bc2a2-119">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="bc2a2-120">Yöntemin tanımlandığı modülün işaretlenmesi isteğe bağlıdır, ancak her genişletme yöntemi işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-120">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="bc2a2-121"><xref:System.Runtime.CompilerServices> Uzantı özniteliğine erişebilmek için içeri aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-121"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>

<span data-ttu-id="bc2a2-122">Uzantı yöntemleri yalnızca modüller içinde bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-122">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="bc2a2-123">Genellikle, bir uzantı yönteminin tanımlandığı modül, çağrıldığı bir modül olarak değildir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-123">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="bc2a2-124">Bunun yerine, uzantı yöntemini içeren modül içeri aktarıldıysa, kapsama getirmek için içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-124">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="bc2a2-125">İçeren modül `Print` kapsam içinde olduğunda, yöntemi bağımsız değişken içermeyen sıradan bir örnek yöntemi gibi çağrılabilir, örneğin `ToUpper` :</span><span class="sxs-lookup"><span data-stu-id="bc2a2-125">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

<span data-ttu-id="bc2a2-126">Sonraki örnek, `PrintAndPunctuate` için de bir uzantısıdır <xref:System.String> , bu kez iki parametreyle tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-126">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="bc2a2-127">İlk parametresi, `aString` Uzantı yönteminin genişlettiğini belirler <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="bc2a2-127">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="bc2a2-128">İkinci parametresi, `punc` yöntemi çağrıldığında bağımsız değişken olarak geçirilen bir noktalama işaretleri dizesi olmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-128">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="bc2a2-129">Yöntemi, dizeyi ve ardından noktalama işaretlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-129">The method displays the string followed by the punctuation marks.</span></span>

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

<span data-ttu-id="bc2a2-130">Yöntemi, için bir dize bağımsız değişkeninde göndererek çağrılır `punc` : `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="bc2a2-130">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>

<span data-ttu-id="bc2a2-131">Aşağıdaki örnek gösterir `Print` ve `PrintAndPunctuate` tanımlanır ve çağırılır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-131">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="bc2a2-132"><xref:System.Runtime.CompilerServices> Uzantı özniteliğine erişimi etkinleştirmek için tanım modülüne içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-132"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

<span data-ttu-id="bc2a2-133">Ardından, uzantı yöntemleri kapsama alınır ve çağrılır:</span><span class="sxs-lookup"><span data-stu-id="bc2a2-133">Next, the extension methods are brought into scope and called:</span></span>

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

<span data-ttu-id="bc2a2-134">Bu veya benzer uzantı yöntemlerini çalıştırmak için gerekli olan tüm bunlar kapsam içinde yer alırlar.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-134">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="bc2a2-135">Bir genişletme yöntemi içeren modül kapsamdadır, IntelliSense 'de görünür ve sıradan bir örnek yöntemi gibi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-135">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>

<span data-ttu-id="bc2a2-136">Yöntemler çağrıldığında, ilk parametre için ' de bir bağımsız değişken gönderildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-136">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="bc2a2-137">`aString`Önceki yöntem tanımlarındaki parametresi `example` , `String` bunları çağıran örneği olan öğesine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-137">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="bc2a2-138">Derleyici, `example` ilk parametreye gönderilen bağımsız değişken olarak kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-138">The compiler will use `example` as the argument sent to the first parameter.</span></span>

<span data-ttu-id="bc2a2-139">Olarak ayarlanmış bir nesne için bir genişletme yöntemi çağrılırsa `Nothing` , genişletme yöntemi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-139">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="bc2a2-140">Bu, sıradan örnek yöntemlerine uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-140">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="bc2a2-141">Uzantı yönteminde açıkça kontrol edebilirsiniz `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="bc2a2-141">You can explicitly check for `Nothing` in the extension method.</span></span>

## <a name="types-that-can-be-extended"></a><span data-ttu-id="bc2a2-142">Genişletilebilen türler</span><span class="sxs-lookup"><span data-stu-id="bc2a2-142">Types that can be extended</span></span>

<span data-ttu-id="bc2a2-143">Aşağıdakiler de dahil olmak üzere Visual Basic parametre listesinde gösterilebilen çoğu tür için bir genişletme yöntemi tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bc2a2-143">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>

- <span data-ttu-id="bc2a2-144">Sınıflar (başvuru türleri)</span><span class="sxs-lookup"><span data-stu-id="bc2a2-144">Classes (reference types)</span></span>
- <span data-ttu-id="bc2a2-145">Yapılar (değer türleri)</span><span class="sxs-lookup"><span data-stu-id="bc2a2-145">Structures (value types)</span></span>
- <span data-ttu-id="bc2a2-146">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bc2a2-146">Interfaces</span></span>
- <span data-ttu-id="bc2a2-147">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="bc2a2-147">Delegates</span></span>
- <span data-ttu-id="bc2a2-148">ByRef ve ByVal bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="bc2a2-148">ByRef and ByVal arguments</span></span>
- <span data-ttu-id="bc2a2-149">Genel yöntem parametreleri</span><span class="sxs-lookup"><span data-stu-id="bc2a2-149">Generic method parameters</span></span>
- <span data-ttu-id="bc2a2-150">Diziler</span><span class="sxs-lookup"><span data-stu-id="bc2a2-150">Arrays</span></span>

<span data-ttu-id="bc2a2-151">İlk parametre Uzantı yönteminin genişlettiği veri türünü belirttiğinden, gereklidir ve isteğe bağlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-151">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="bc2a2-152">Bu nedenle, `Optional` Parametreler ve `ParamArray` parametreleri parametre listesindeki ilk parametre olamaz.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-152">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>

<span data-ttu-id="bc2a2-153">Genişletme metotları geç bağlamada dikkate alınmıyor.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-153">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="bc2a2-154">Aşağıdaki örnekte, ifade `anObject.PrintMe()` bir <xref:System.MissingMemberException> özel durum oluşturur, ikinci `PrintMe` uzantı yöntemi tanımı silinmişse aynı özel durum görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-154">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a><span data-ttu-id="bc2a2-155">En iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="bc2a2-155">Best practices</span></span>

<span data-ttu-id="bc2a2-156">Uzantı yöntemleri, var olan bir türü genişletmek için kullanışlı ve güçlü bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-156">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="bc2a2-157">Ancak, bunları başarılı bir şekilde kullanmak için göz önünde bulundurmanız gereken bazı noktaları vardır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-157">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="bc2a2-158">Bu konular temel olarak sınıf kitaplıklarının yazarlarına uygulanır, ancak uzantı yöntemlerini kullanan herhangi bir uygulamayı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-158">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>

<span data-ttu-id="bc2a2-159">Genellikle, sahip olmadığınız türlere eklediğiniz genişletme yöntemleri, denetlediğiniz türlere eklenen genişletme yöntemlerinden daha savunmasız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-159">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="bc2a2-160">Uzantı yöntemlerinizi kesintiye uğratabilecek, sahip olmadığınız sınıflarda bir dizi şey meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-160">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>

- <span data-ttu-id="bc2a2-161">Çağırma deyimindeki bağımsız değişkenlerle uyumlu imzaya sahip herhangi bir erişilebilir örnek üye varsa, bağımsız değişkenden parametreye hiçbir daraltma dönüştürmesi gerekmiyorsa, örnek yöntemi herhangi bir genişletme yöntemine tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-161">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="bc2a2-162">Bu nedenle, belirli bir noktada bir sınıfa uygun bir örnek yöntemi eklenirse, kullandığınız mevcut bir uzantı üyesi erişilemez hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-162">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>

- <span data-ttu-id="bc2a2-163">Bir genişletme yönteminin yazarı, diğer programcıların özgün uzantıya göre önceliğe sahip olabilecek, çakışan uzantı yöntemleri yazmasını engelleyemez.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-163">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>

- <span data-ttu-id="bc2a2-164">Uzantı yöntemlerini kendi ad alanına yerleştirerek sağlamlık düzeyini artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-164">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="bc2a2-165">Daha sonra kitaplığınızın tüketicileri, bir ad alanı içerebilir veya hariç tutabilir ya da kitaplığın geri kalanından ayrı olarak ad alanları arasından seçim yapabilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-165">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>

- <span data-ttu-id="bc2a2-166">Arabirimleri genişletmekten daha güvenli olabilir, özellikle arabirimin veya sınıfınızın sahibi olmadığınız durumlarda sınıfları genişletebiliriz.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-166">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="bc2a2-167">Bir arabirimdeki değişiklik, onu uygulayan her sınıfı etkiler.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-167">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="bc2a2-168">Bu nedenle, yazarın bir arabirimdeki yöntemleri ekleme veya değiştirme olasılığı daha düşüktür.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-168">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="bc2a2-169">Ancak, bir sınıf aynı imzaya sahip uzantı yöntemlerine sahip iki arabirim uygularsa, hiçbir genişletme yöntemi görünür değildir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-169">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>

- <span data-ttu-id="bc2a2-170">Kullanabileceğiniz en belirli türü genişletin.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-170">Extend the most specific type you can.</span></span> <span data-ttu-id="bc2a2-171">Bir tür hiyerarşisinde, diğer birçok türden türetilmiş bir tür seçerseniz, örnek yöntemlerinin veya sizinkilerle karıştabilecek diğer uzantı yöntemlerinin tanıtımı için bazı olanaklar katmanları vardır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-171">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>

## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="bc2a2-172">Uzantı yöntemleri, örnek yöntemleri ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="bc2a2-172">Extension methods, instance methods, and properties</span></span>

<span data-ttu-id="bc2a2-173">Kapsam içi bir örnek yöntemi, bir çağırma ifadesinin bağımsız değişkenleriyle uyumlu bir imzaya sahip olduğunda, örnek yöntemi herhangi bir genişletme yöntemine göre tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-173">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="bc2a2-174">Uzantı yöntemi daha iyi bir eşleşme olsa bile örnek yöntemi önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-174">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="bc2a2-175">Aşağıdaki örnekte, `ExampleClass` `ExampleMethod` türünde bir parametreye sahip adlı bir örnek yöntemi içerir `Integer` .</span><span class="sxs-lookup"><span data-stu-id="bc2a2-175">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="bc2a2-176">Genişletme yöntemi `ExampleMethod` `ExampleClass` , ve türünde bir parametreye sahiptir `Long` .</span><span class="sxs-lookup"><span data-stu-id="bc2a2-176">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

<span data-ttu-id="bc2a2-177">Aşağıdaki kodda öğesine yapılan ilk çağrı `ExampleMethod` uzantı yöntemini çağırır, çünkü `arg1` `Long` ve yalnızca `Long` genişletme yöntemindeki parametresiyle uyumludur.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-177">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="bc2a2-178">İkinci çağrısının `ExampleMethod` bir `Integer` bağımsız değişkeni vardır `arg2` ve örnek yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-178">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

<span data-ttu-id="bc2a2-179">Şimdi iki yöntemde parametrelerin veri türlerini tersine çevirin:</span><span class="sxs-lookup"><span data-stu-id="bc2a2-179">Now reverse the data types of the parameters in the two methods:</span></span>

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

<span data-ttu-id="bc2a2-180">Bu kez, içindeki kod `Main` her iki kez örnek yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-180">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="bc2a2-181">Bunun nedeni, hem hem de `arg1` `arg2` üzerinde bir genişletme dönüştürmesi olması `Long` ve örnek yönteminin her iki durumda da genişletme yöntemine göre öncelikli olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-181">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

<span data-ttu-id="bc2a2-182">Bu nedenle, bir genişletme yöntemi var olan bir örnek yönteminin yerini alamaz.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-182">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="bc2a2-183">Ancak, bir genişletme yöntemi bir örnek yöntemiyle aynı ada sahip olsa da imzalar çakışmadığında her iki yönteme de erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-183">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="bc2a2-184">Örneğin, sınıfı `ExampleClass` bağımsız değişken içermeyen adlı bir yöntemi içeriyorsa `ExampleMethod` , aşağıdaki kodda gösterildiği gibi, aynı ada sahip ve farklı imzalara sahip genişletme yöntemlerine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-184">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

<span data-ttu-id="bc2a2-185">Bu kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bc2a2-185">The output from this code is as follows:</span></span>

```console
Extension method
Instance method
```

<span data-ttu-id="bc2a2-186">Durum, özelliklerle daha basittir: bir genişletme yöntemi, genişlettiği sınıfın bir özelliği ile aynı ada sahipse, genişletme yöntemi görünür değildir ve erişilemez.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-186">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>

## <a name="extension-method-precedence"></a><span data-ttu-id="bc2a2-187">Uzantı yöntemi önceliği</span><span class="sxs-lookup"><span data-stu-id="bc2a2-187">Extension method precedence</span></span>

<span data-ttu-id="bc2a2-188">Aynı imzaya sahip iki genişletme yöntemi kapsam içinde ve erişilebilir olduğunda, daha yüksek önceliğe sahip olan bir yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-188">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="bc2a2-189">Uzantı yönteminin önceliği, yöntemi kapsama getirmek için kullanılan mekanizmaya dayanır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-189">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="bc2a2-190">Aşağıdaki listede, en yüksekten en düşüğe öncelik hiyerarşisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-190">The following list shows the precedence hierarchy, from highest to lowest.</span></span>

1. <span data-ttu-id="bc2a2-191">Geçerli modülün içinde tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-191">Extension methods defined inside the current module.</span></span>

2. <span data-ttu-id="bc2a2-192">Geçerli ad alanındaki veya üst öğelerinden herhangi birindeki veri türleri içinde tanımlanan uzantı yöntemleri, alt ad alanları üst ad alanlarından daha yüksek önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-192">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>

3. <span data-ttu-id="bc2a2-193">Herhangi bir tür içinde tanımlanan genişletme yöntemleri geçerli dosyaya içe aktarılır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-193">Extension methods defined inside any type imports in the current file.</span></span>

4. <span data-ttu-id="bc2a2-194">Herhangi bir ad alanı içinde tanımlanan genişletme yöntemleri geçerli dosyaya içe aktarılır.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-194">Extension methods defined inside any namespace imports in the current file.</span></span>

5. <span data-ttu-id="bc2a2-195">Herhangi bir proje düzeyi türü içeri aktarma içinde tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-195">Extension methods defined inside any project-level type imports.</span></span>

6. <span data-ttu-id="bc2a2-196">Herhangi bir proje düzeyi ad alanı içeri aktarma içinde tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-196">Extension methods defined inside any project-level namespace imports.</span></span>

<span data-ttu-id="bc2a2-197">Öncelik belirsizlik çözümlenmezse, aradığınız yöntemi belirtmek için tam nitelikli adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-197">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="bc2a2-198">`Print`Önceki örnekteki yöntem adlı bir modülde tanımlanmışsa `StringExtensions` , tam adı `StringExtensions.Print(example)` yerine olur `example.Print()` .</span><span class="sxs-lookup"><span data-stu-id="bc2a2-198">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc2a2-199">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc2a2-199">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="bc2a2-200">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="bc2a2-200">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="bc2a2-201">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="bc2a2-201">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="bc2a2-202">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="bc2a2-202">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bc2a2-203">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc2a2-203">Optional Parameters</span></span>](optional-parameters.md)
- [<span data-ttu-id="bc2a2-204">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="bc2a2-204">Parameter Arrays</span></span>](parameter-arrays.md)
- [<span data-ttu-id="bc2a2-205">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="bc2a2-205">Attributes overview</span></span>](../../concepts/attributes/index.md)
- [<span data-ttu-id="bc2a2-206">Visual Basic'de Kapsam</span><span class="sxs-lookup"><span data-stu-id="bc2a2-206">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
