---
title: Uzantı Yöntemleri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 9e005d0dc7da154fbaffbf7e02c55445a1213195
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296244"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="6d6a9-102">Uzantı Yöntemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d6a9-102">Extension Methods (Visual Basic)</span></span>
<span data-ttu-id="6d6a9-103">Genişletme yöntemleri, geliştiricilerin zaten yeni bir türetilmiş tür oluşturmadan tanımlanan veri türlerine özel işlevsellik eklemek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="6d6a9-104">Genişletme yöntemleri mevcut türü bir örnek yöntemi gibi çağrılabilen bir yöntem yazmaktır mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d6a9-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d6a9-105">Remarks</span></span>  
 <span data-ttu-id="6d6a9-106">Bir genişletme yöntemi yalnızca olabilir bir `Sub` yordamı veya `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="6d6a9-107">Bir uzantı özelliği, alan veya olay tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="6d6a9-108">Tüm uzantı yöntemleri uzantı özniteliğiyle işaretlenmelidir `<Extension()>` gelen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-108">All extension methods must be marked with the extension attribute `<Extension()>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="6d6a9-109">Bir genişletme yöntemi tanımındaki ilk parametre, yöntemin genişlettiği hangi veri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-109">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="6d6a9-110">Yöntem çalıştırıldığında ilk parametre yöntemi çağıran veri türü örneğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-110">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d6a9-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d6a9-111">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6d6a9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d6a9-112">Description</span></span>  
 <span data-ttu-id="6d6a9-113">Aşağıdaki örnekte tanımlayan bir `Print` uzantısı <xref:System.String> veri türü.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-113">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="6d6a9-114">Yöntemini kullanan `Console.WriteLine` bir dize görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-114">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="6d6a9-115">Parametresi `Print` yöntemi `aString`, yöntem genişletir <xref:System.String> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-115">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]  
  
 <span data-ttu-id="6d6a9-116">Uzantı yöntemi tanımının uzantı özniteliğiyle işaretlendiğine dikkat edin `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-116">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="6d6a9-117">Yöntemin tanımlandığı modülün işaretlenmesi isteğe bağlıdır, ancak her bir genişletme yöntemi işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-117">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <xref:System.Runtime.CompilerServices> <span data-ttu-id="6d6a9-118">Uzantı özniteliğine erişim sağlamak için içeri aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-118">must be imported in order to access the extension attribute.</span></span>  
  
 <span data-ttu-id="6d6a9-119">Uzantı yöntemleri yalnızca modüllerde bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-119">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="6d6a9-120">Genellikle, bir uzantı yönteminin tanımlandığı modül, çağrıldığı olarak aynı modül değil.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-120">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="6d6a9-121">Kapsama alınmak üzere olması gerekiyorsa bunun yerine, genişletme yöntemini içeren modül içe aktarılır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-121">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="6d6a9-122">İçeren modül sonra `Print` olan yöntem kapsamda gibi hiçbir bağımsız değişken alan normal bir örnek yöntem gibi çağrılabilir `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="6d6a9-122">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]  
  
 <span data-ttu-id="6d6a9-123">Sonraki örnek, `PrintAndPunctuate`, ayrıca bir uzantı olduğu <xref:System.String>, bu kez iki parametre ile tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-123">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="6d6a9-124">İlk parametre `aString`, genişletme yönteminin genişletir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-124">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="6d6a9-125">İkinci parametre `punc`, yöntem çağrıldığında, bağımsız değişken olarak geçirilen bir noktalama işaretleri dizesi olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-125">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="6d6a9-126">Yöntem sonrasındaki noktalama işaretlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-126">The method displays the string followed by the punctuation marks.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]  
  
 <span data-ttu-id="6d6a9-127">Yöntem için bir dize bağımsız değişken göndererek çağrılır `punc`:</span><span class="sxs-lookup"><span data-stu-id="6d6a9-127">The method is called by sending in a string argument for `punc`:</span></span> `example.PrintAndPunctuate(".")`  
  
 <span data-ttu-id="6d6a9-128">Aşağıdaki örnekte gösterildiği `Print` ve `PrintAndPunctuate` tanımlanan ve çağrılan.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-128">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <xref:System.Runtime.CompilerServices> <span data-ttu-id="6d6a9-129">Uzantı özniteliğine erişim sağlamak için tanım modülüne içe aktarılır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-129">is imported in the definition module in order to enable access to the extension attribute.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6d6a9-130">Kod</span><span class="sxs-lookup"><span data-stu-id="6d6a9-130">Code</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="6d6a9-131">Ardından, genişletme yöntemleri kapsama alınır ve çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-131">Next, the extension methods are brought into scope and called.</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="6d6a9-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d6a9-132">Comments</span></span>  
 <span data-ttu-id="6d6a9-133">Tüm bunlar çalıştırılabilmesi için gereken veya benzer genişletme yöntemlerini kapsam içinde yer.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="6d6a9-134">Bir uzantı yöntemini içeren modül kapsamları dahilinde olması durumunda, Intellisense'te görünür duruma gelir ve normal bir örnek yöntem gibi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>  
  
 <span data-ttu-id="6d6a9-135">Yöntemler çağrıldığında hiçbir bağımsız değişken ilk parametre için gönderilmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="6d6a9-136">Parametre `aString` önceki yöntem tanımlarını bağlı `example`, örneğini `String` onları çağırır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="6d6a9-137">Derleyicinin kullanacağı `example` ilk parametreye gönderilen bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>  
  
 <span data-ttu-id="6d6a9-138">Ayarlanmış bir nesne için bir genişletme yöntemi çağrılırsa `Nothing`, genişletme yöntemi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="6d6a9-139">Bu sıradan örnek yöntemleri için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="6d6a9-140">Açıkça denetleyebilirsiniz `Nothing` uzantı yönteminde.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-140">You can explicitly check for `Nothing` in the extension method.</span></span>  
  
## <a name="types-that-can-be-extended"></a><span data-ttu-id="6d6a9-141">Genişletilebilen türler</span><span class="sxs-lookup"><span data-stu-id="6d6a9-141">Types That Can Be Extended</span></span>  
 <span data-ttu-id="6d6a9-142">Aşağıdakiler dahil olmak üzere bir Visual Basic parametre listesinde temsil edilebilir çoğu türlerinde bir genişletme yöntemi tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6d6a9-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>  
  
-   <span data-ttu-id="6d6a9-143">Sınıflar (başvuru türleri)</span><span class="sxs-lookup"><span data-stu-id="6d6a9-143">Classes (reference types)</span></span>  
  
-   <span data-ttu-id="6d6a9-144">Yapılar (değer türleri)</span><span class="sxs-lookup"><span data-stu-id="6d6a9-144">Structures (value types)</span></span>  
  
-   <span data-ttu-id="6d6a9-145">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="6d6a9-145">Interfaces</span></span>  
  
-   <span data-ttu-id="6d6a9-146">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="6d6a9-146">Delegates</span></span>  
  
-   <span data-ttu-id="6d6a9-147">ByRef ve ByVal bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="6d6a9-147">ByRef and ByVal arguments</span></span>  
  
-   <span data-ttu-id="6d6a9-148">Genel yöntem parametreleri</span><span class="sxs-lookup"><span data-stu-id="6d6a9-148">Generic method parameters</span></span>  
  
-   <span data-ttu-id="6d6a9-149">Diziler</span><span class="sxs-lookup"><span data-stu-id="6d6a9-149">Arrays</span></span>  
  
 <span data-ttu-id="6d6a9-150">İlk parametre genişletme yönteminin genişlettiği veri türünü belirttiğinden gereklidir ve isteğe bağlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="6d6a9-151">Bu nedenle `Optional` parametreleri ve `ParamArray` parametreleri parametre listesindeki ilk parametre olamaz.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="6d6a9-152">Genişletme yöntemleri geç bağlama kapsamında değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="6d6a9-153">Aşağıdaki örnekte, deyim `anObject.PrintMe()` başlatan bir <xref:System.MissingMemberException> özel durum, görüyorsanız, aynı özel durum ikinci `PrintMe` genişletme yöntemi tanımı silindiğinde.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]  
  
## <a name="best-practices"></a><span data-ttu-id="6d6a9-154">En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6d6a9-154">Best Practices</span></span>  
 <span data-ttu-id="6d6a9-155">Genişletme yöntemleri mevcut türü genişletmek için kullanışlı ve güçlü bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="6d6a9-156">Ancak, başarıyla kullanmak için dikkate alınması gereken bazı noktalar vardır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="6d6a9-157">Esas olarak sınıf kitaplıklarını yazarları için aşağıdaki maddeler geçerlidir, ancak bunlar genişletme yöntemlerini kullanan tüm uygulamaları etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>  
  
 <span data-ttu-id="6d6a9-158">Genellikle sahibi olmadığınız türlere eklediğiniz genişletme yöntemleri daha denetim türlere eklenen genişletme yöntemlerinden daha savunmasızdır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="6d6a9-159">Birkaç uzantı yöntemlerinizi engelleyebilecek birçok ait olmayan sınıflarda ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>  
  
-   <span data-ttu-id="6d6a9-160">Parametreye daraltma dönüşümü bağımsız değişkenden parametreye ile çağrı deyimindeki bağımsız değişkenlerle uyumlu imzası olan bir erişilebilir örnek üye varsa, örnek yöntemi herhangi bir genişletme yöntemi yerine kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="6d6a9-161">Bu nedenle, uygun bir örnek yöntemi, belirli bir noktada bir sınıfa eklenirse, bağlı olduğunuz mevcut uzantı üyesi erişilemez duruma gelebilir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>  
  
-   <span data-ttu-id="6d6a9-162">Genişletme yönteminin yazarı diğer programcıların öncelik özgün öncelikli olabilecek, çakışan genişletme yöntemleri yazmasını engelleyemez.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>  
  
-   <span data-ttu-id="6d6a9-163">Genişletme yöntemleri kendi ad alanına yerleştirerek sağlamlığı artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="6d6a9-164">Kitaplığınızı kullanan Tüketiciler, bir ad alanı dahil edebilir veya hariç veya kitaplık kalanından ayrı olarak ad alanları arasından seçim.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>  
  
-   <span data-ttu-id="6d6a9-165">Özellikle, arabirimin veya sınıfın sahibi değil, bu sınıfları genişletmek yerine arabirimleri genişletmek daha güvenli olabilir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="6d6a9-166">Arabirimdeki bir değişiklik, uygulandığı her sınıfı etkiler.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="6d6a9-167">Bu nedenle, yazarın ekleme veya bir arabirimdeki yöntemlerde değiştirme olasılığı daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="6d6a9-168">Ancak, bir sınıf, aynı imzaya sahip genişletme yöntemleri olan iki arabirim uygularsa, her iki uzantı yöntemi görülebilir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>  
  
-   <span data-ttu-id="6d6a9-169">Yapabilecekleriniz en belirgin türü genişletin.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-169">Extend the most specific type you can.</span></span> <span data-ttu-id="6d6a9-170">Tür hiyerarşisinde çok türetildiği bir tür seçerseniz katmanı vardır örnek yöntemlerine veya yöntemlerinizle çakışabilecek genişletme yöntemlerine giriş olasılıklarını.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>  
  
## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="6d6a9-171">Genişletme yöntemleri, örnek yöntemler ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="6d6a9-171">Extension Methods, Instance Methods, and Properties</span></span>  
 <span data-ttu-id="6d6a9-172">Bir kapsamdaki örnek yöntemi deyim çağırma bağımsız değişkenlerle uyumlu imzası olan, örnek yöntemi yerine herhangi bir genişletme yöntemi seçilir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="6d6a9-173">Genişletme yönteminin eşleşmesi daha iyi olsa bile örnek yönteminindir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="6d6a9-174">Aşağıdaki örnekte, `ExampleClass` adlandırılmış bir örnek yöntemi içeren `ExampleMethod` türünde bir parametreye sahip `Integer`.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="6d6a9-175">Genişletme yöntemi `ExampleMethod` genişletir `ExampleClass`, ve türünde bir parametreye sahip `Long`.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]  
  
 <span data-ttu-id="6d6a9-176">İlk çağrıda `ExampleMethod` aşağıdaki kodda genişletme yöntemini çağırır çünkü `arg1` olduğu `Long` ve yalnızca ile uyumlu `Long` genişletme yönteminin parametresi.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="6d6a9-177">İçin yapılan ikinci çağrı `ExampleMethod` sahip bir `Integer` bağımsız değişkeni, `arg2`, ve örnek yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]  
  
 <span data-ttu-id="6d6a9-178">Şimdi geriye doğru iki yöntemle parametrelerinin veri türleri:</span><span class="sxs-lookup"><span data-stu-id="6d6a9-178">Now reverse the data types of the parameters in the two methods:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]  
  
 <span data-ttu-id="6d6a9-179">Bu sefer kodda `Main` iki seferde de örnek yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="6d6a9-180">Bunun nedeni, her ikisi de `arg1` ve `arg2` genişletme dönüştürmesi sahip `Long`, ve örnek yöntemin her iki durumda da uzantı yöntemini önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]  
  
 <span data-ttu-id="6d6a9-181">Bu nedenle, bir genişletme yöntemi, bir mevcut örnek yönteminin yerine kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="6d6a9-182">Ancak, bir genişletme yöntemi örnek yöntemle aynı ada sahiptir ancak imzalar, her iki yöntem de erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="6d6a9-183">Örneğin, sınıf `ExampleClass` adında bir yöntem içeriyorsa `ExampleMethod` hiçbir bağımsız değişken, aynı ada sahip genişletme yöntemleri alır ancak farklı imzalara izin verilir, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]  
  
 <span data-ttu-id="6d6a9-184">Bu kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6d6a9-184">The output from this code is as follows:</span></span>  
  
 `Extension method`  
  
 `Instance method`  
  
 <span data-ttu-id="6d6a9-185">Durum özellikler ile daha basittir: genişletme yöntemi genişlettiği sınıfın bir özelliği aynı ada sahipse, genişletme yöntemi görünmez ve erişilemez.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>  
  
## <a name="extension-method-precedence"></a><span data-ttu-id="6d6a9-186">Genişletme yöntemini önceliği</span><span class="sxs-lookup"><span data-stu-id="6d6a9-186">Extension Method Precedence</span></span>  
 <span data-ttu-id="6d6a9-187">Aynı imzaya sahip iki uzantı yöntemi kapsam içinde ve erişilebilir olduğunda, daha yüksek önceliğe sahip çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="6d6a9-188">Bir uzantı yönteminin önceliği, yöntemi kapsam içine almak için kullanılan mekanizmaya dayanır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="6d6a9-189">Aşağıdaki liste, yüksekten en düşüğe öncelik hiyerarşisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>  
  
1. <span data-ttu-id="6d6a9-190">Geçerli modül içinde tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-190">Extension methods defined inside the current module.</span></span>  
  
2. <span data-ttu-id="6d6a9-191">Genişletme yöntemleri veri türleri geçerli ad alanı veya üst öğelerinden birini üst öğe ad alanlarına daha yüksek bir önceliğe sahip alt ad alanları ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>  
  
3. <span data-ttu-id="6d6a9-192">Geçerli dosyadaki herhangi bir türü alır içinde tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-192">Extension methods defined inside any type imports in the current file.</span></span>  
  
4. <span data-ttu-id="6d6a9-193">Geçerli dosyadaki tüm ad alanı içeri aktarmaları içinde tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-193">Extension methods defined inside any namespace imports in the current file.</span></span>  
  
5. <span data-ttu-id="6d6a9-194">Tüm proje düzeyi türündeki aktarılır tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-194">Extension methods defined inside any project-level type imports.</span></span>  
  
6. <span data-ttu-id="6d6a9-195">Tüm proje düzeyindeki ad alanında aktarılır tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-195">Extension methods defined inside any project-level namespace imports.</span></span>  
  
 <span data-ttu-id="6d6a9-196">Öncelik belirsizliği, kaldırmazsa çağırdığınız yöntemi belirtmek için tam nitelikli adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="6d6a9-197">Varsa `Print` yöntemi önceki örnekte bulunan adında bir modülde tanımlanan `StringExtensions`, tam nitelikli ad `StringExtensions.Print(example)` yerine `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d6a9-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d6a9-198">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="6d6a9-199">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="6d6a9-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="6d6a9-200">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="6d6a9-200">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="6d6a9-201">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="6d6a9-201">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6d6a9-202">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d6a9-202">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="6d6a9-203">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="6d6a9-203">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="6d6a9-204">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="6d6a9-204">Attributes overview</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="6d6a9-205">Visual Basic'de Kapsam</span><span class="sxs-lookup"><span data-stu-id="6d6a9-205">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
