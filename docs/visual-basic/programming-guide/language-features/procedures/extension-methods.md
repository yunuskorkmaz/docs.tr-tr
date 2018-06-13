---
title: Uzantı Metotları (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 1cc2ccef09dd027c6f1e82f60ed4ac5f50db6ebe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655290"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="11e75-102">Uzantı Metotları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11e75-102">Extension Methods (Visual Basic)</span></span>
<span data-ttu-id="11e75-103">Genişletme yöntemleri yeni türetilmiş bir tür oluşturmadan önceden tanımlanmış veri türlerine özel işlevsellik eklemek için geliştiricilere etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="11e75-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="11e75-104">Genişletme yöntemleri varolan türünün bir örneği yöntemi değilmiş gibi çağrılabilir bir yöntem yazmak mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="11e75-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11e75-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11e75-105">Remarks</span></span>  
 <span data-ttu-id="11e75-106">Bir genişletme yöntemi yalnızca olabilir bir `Sub` yordamı veya `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="11e75-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="11e75-107">Uzantı özelliği, alan veya olay tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="11e75-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="11e75-108">Tüm uzantı yöntemleri uzantısı özniteliği ile işaretlenmiş olmalıdır `<Extension()>` gelen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="11e75-108">All extension methods must be marked with the extension attribute `<Extension()>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="11e75-109">Bir genişletme yöntemi tanımında ilk parametresi, yöntemin genişlettiği hangi veri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="11e75-109">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="11e75-110">Yöntem çalıştırdığınızda, ilk parametre yöntemi çağırır veri türü örneğine bağlı.</span><span class="sxs-lookup"><span data-stu-id="11e75-110">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11e75-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="11e75-111">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="11e75-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11e75-112">Description</span></span>  
 <span data-ttu-id="11e75-113">Aşağıdaki örnek tanımlayan bir `Print` uzantısı <xref:System.String> veri türü.</span><span class="sxs-lookup"><span data-stu-id="11e75-113">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="11e75-114">Bir yöntem `Console.WriteLine` bir dize görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="11e75-114">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="11e75-115">Parametresi, `Print` yöntemi, `aString`, yöntemin genişlettiği kurar <xref:System.String> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="11e75-115">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 <span data-ttu-id="11e75-116">Uzantı yöntemi tanımı uzantısı özniteliğiyle işaretlenmiş fark `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="11e75-116">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="11e75-117">Yöntem tanımlandığı modülü işaretleme isteğe bağlıdır, ancak her bir genişletme yöntemi işaretlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="11e75-117">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="11e75-118"><xref:System.Runtime.CompilerServices> Uzantı özniteliği erişmek için içeri aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11e75-118"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>  
  
 <span data-ttu-id="11e75-119">Genişletme yöntemleri yalnızca modülleri içinde bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="11e75-119">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="11e75-120">Genellikle, bir genişletme yöntemi tanımlandığı modül adı verilir olarak aynı modül değil.</span><span class="sxs-lookup"><span data-stu-id="11e75-120">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="11e75-121">Bu kapsam içine duruma getirmek üzere olması gerekiyorsa bunun yerine, genişletme yöntemi içeren modülü, içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="11e75-121">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="11e75-122">İçeren modülü sonra `Print` olduğu gibi hiç bağımsız değişken alan sıradan örnek yöntemi değilmiş gibi kapsamda yöntemi çağrılabilir `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="11e75-122">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 <span data-ttu-id="11e75-123">Sonraki örnek `PrintAndPunctuate`, ayrıca bir uzantı olduğu <xref:System.String>, iki parametreyle tanımlanan bu süre.</span><span class="sxs-lookup"><span data-stu-id="11e75-123">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="11e75-124">İlk parametre `aString`, genişletme yöntemi genişleten kurar <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11e75-124">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="11e75-125">İkinci parametre `punc`, yöntem çağrıldığında, bağımsız değişken olarak geçirilen noktalama işaretleri dizesi olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="11e75-125">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="11e75-126">Yöntem noktalama işaretleri tarafından izlenen dizesi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="11e75-126">The method displays the string followed by the punctuation marks.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 <span data-ttu-id="11e75-127">Dize bağımsız değişkeni için göndererek çağrılan yöntemi `punc`: `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="11e75-127">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>  
  
 <span data-ttu-id="11e75-128">Aşağıdaki örnekte gösterildiği `Print` ve `PrintAndPunctuate` tanımlanan ve çağrılır.</span><span class="sxs-lookup"><span data-stu-id="11e75-128">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="11e75-129"><xref:System.Runtime.CompilerServices> tanımı modülünde extension özniteliği erişimi etkinleştirmek için alınır.</span><span class="sxs-lookup"><span data-stu-id="11e75-129"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>  
  
### <a name="code"></a><span data-ttu-id="11e75-130">Kod</span><span class="sxs-lookup"><span data-stu-id="11e75-130">Code</span></span>  
  
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
  
 <span data-ttu-id="11e75-131">Ardından, genişletme yöntemleri kapsam içine alınır ve çağrılır.</span><span class="sxs-lookup"><span data-stu-id="11e75-131">Next, the extension methods are brought into scope and called.</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="11e75-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11e75-132">Comments</span></span>  
 <span data-ttu-id="11e75-133">Tüm bunlar çalıştırılabilmesi için gereken veya benzer genişletme yöntemleri kapsamında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11e75-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="11e75-134">Bir genişletme yöntemi içeren modülü kapsamları dahilinde olması durumunda, IntelliSense içinde görünür ve sıradan örnek yöntemi değilmiş gibi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="11e75-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>  
  
 <span data-ttu-id="11e75-135">Yöntem çağrıldığında, bağımsız değişken ilk parametre için gönderilmesini dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="11e75-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="11e75-136">Parametre `aString` önceki yönteminde tanımları bağlı `example`, örneği `String` bunları çağırır.</span><span class="sxs-lookup"><span data-stu-id="11e75-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="11e75-137">Derleyici kullanacağı `example` ilk parametre olarak gönderilen bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="11e75-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>  
  
 <span data-ttu-id="11e75-138">Ayarlanmış bir nesne için bir genişletme yöntemi çağrılıp çağrılmayacağını `Nothing`, genişletme yöntemi yürütür.</span><span class="sxs-lookup"><span data-stu-id="11e75-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="11e75-139">Bu normal örnek yöntemleri için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="11e75-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="11e75-140">Açıkça denetleyebilirsiniz `Nothing` uzantı yönteminde.</span><span class="sxs-lookup"><span data-stu-id="11e75-140">You can explicitly check for `Nothing` in the extension method.</span></span>  
  
## <a name="types-that-can-be-extended"></a><span data-ttu-id="11e75-141">Genişletilebilir türleri</span><span class="sxs-lookup"><span data-stu-id="11e75-141">Types That Can Be Extended</span></span>  
 <span data-ttu-id="11e75-142">Bir genişletme yöntemi, aşağıdakiler de dahil olmak üzere bir Visual Basic parametre listesinde, temsil edilebilir çoğu türlerinde tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="11e75-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>  
  
-   <span data-ttu-id="11e75-143">Sınıflar (başvuru türleri)</span><span class="sxs-lookup"><span data-stu-id="11e75-143">Classes (reference types)</span></span>  
  
-   <span data-ttu-id="11e75-144">Yapılar (değer türleri için)</span><span class="sxs-lookup"><span data-stu-id="11e75-144">Structures (value types)</span></span>  
  
-   <span data-ttu-id="11e75-145">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="11e75-145">Interfaces</span></span>  
  
-   <span data-ttu-id="11e75-146">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="11e75-146">Delegates</span></span>  
  
-   <span data-ttu-id="11e75-147">ByRef ve ByVal bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="11e75-147">ByRef and ByVal arguments</span></span>  
  
-   <span data-ttu-id="11e75-148">Genel yöntem parametreleri</span><span class="sxs-lookup"><span data-stu-id="11e75-148">Generic method parameters</span></span>  
  
-   <span data-ttu-id="11e75-149">Diziler</span><span class="sxs-lookup"><span data-stu-id="11e75-149">Arrays</span></span>  
  
 <span data-ttu-id="11e75-150">İlk parametre uzantısı yöntemin genişlettiği veri türü belirttiğinden, gerekli ve isteğe bağlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="11e75-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="11e75-151">Bu nedenle, `Optional` parametreleri ve `ParamArray` parametreleri, parametre listesindeki ilk parametre olamaz.</span><span class="sxs-lookup"><span data-stu-id="11e75-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="11e75-152">Genişletme yöntemleri geç bağlama dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="11e75-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="11e75-153">Aşağıdaki örnekte, deyim `anObject.PrintMe()` başlatır bir <xref:System.MissingMemberException> özel durum, görüyorsanız, aynı özel durum ikinci `PrintMe` yöntemi tanımı uzantısı silindi.</span><span class="sxs-lookup"><span data-stu-id="11e75-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a><span data-ttu-id="11e75-154">En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="11e75-154">Best Practices</span></span>  
 <span data-ttu-id="11e75-155">Genişletme yöntemleri, mevcut bir türle genişletmek için kullanışlı ve güçlü bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="11e75-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="11e75-156">Ancak, başarılı bir şekilde kullanmak için vardır bazı noktaları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="11e75-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="11e75-157">Bu noktalar çoğunlukla sınıf kitaplıkları yazarları için geçerlidir, ancak genişletme yöntemlerini kullanan herhangi bir uygulama etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="11e75-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>  
  
 <span data-ttu-id="11e75-158">En genel olarak, sahibi olmadığınız türleri ekleme genişletme yöntemleri, sizin denetlediğiniz türlerine eklenen genişletme yöntemleri daha savunmasız.</span><span class="sxs-lookup"><span data-stu-id="11e75-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="11e75-159">Birkaç uzantı yöntemleriyle etkileyebilir sahibi olmadığınız sınıflardaki ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="11e75-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>  
  
-   <span data-ttu-id="11e75-160">Bağımsız değişkenden parametresi gerekli hiçbir daraltma dönüşümleri ile arama deyiminde bağımsız değişkenle uyumlu bir imzaya sahip herhangi bir erişilebilir örneği üyesi varsa, örnek yöntemi herhangi bir genişletme yöntemi yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11e75-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="11e75-161">Bu nedenle, uygun örnek yöntemi, belirli bir noktada bir sınıfa eklediyseniz, bağlı olan bir uzantı üye erişilemez hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="11e75-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>  
  
-   <span data-ttu-id="11e75-162">Bir genişletme yöntemi yazarı diğer programcıları öncelik özgün uzantısı olabilir çakışan genişletme yöntemleri yazma engelleyemez.</span><span class="sxs-lookup"><span data-stu-id="11e75-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>  
  
-   <span data-ttu-id="11e75-163">Genişletme yöntemleri, kendi ad alanında koyarak sağlamlık artırabilir.</span><span class="sxs-lookup"><span data-stu-id="11e75-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="11e75-164">Tüketiciler kitaplığınızın bir ad alanı dahil edebilir veya dışarıda veya ad alanları, ayrı ayrı geri kalanından kitaplığı arasından seçim.</span><span class="sxs-lookup"><span data-stu-id="11e75-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>  
  
-   <span data-ttu-id="11e75-165">Özellikle, arabirimi veya sınıfı değil sahipseniz sınıfları, genişletilecek olduğundan arabirimleri genişletmek daha güvenli olabilir.</span><span class="sxs-lookup"><span data-stu-id="11e75-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="11e75-166">Arabirimdeki bir değişiklik, uygulayan her sınıf etkiler.</span><span class="sxs-lookup"><span data-stu-id="11e75-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="11e75-167">Bu nedenle, yazarın eklemek veya bir arabirim yöntemleri değiştirmek olasılığı daha düşüktür.</span><span class="sxs-lookup"><span data-stu-id="11e75-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="11e75-168">Ancak, bir sınıf uzantısı yöntemleri aynı imzayla iki arabirim uygularsa, hiçbiri genişletme yöntemi görünür olur.</span><span class="sxs-lookup"><span data-stu-id="11e75-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>  
  
-   <span data-ttu-id="11e75-169">Yapabilecekleriniz en belirgin türü genişletir.</span><span class="sxs-lookup"><span data-stu-id="11e75-169">Extend the most specific type you can.</span></span> <span data-ttu-id="11e75-170">Türlerinin bir hiyerarşide, diğer birçok türetilen, bir tür seçerseniz katmanı vardır olasılıklar giriş örnek yöntemleri ya da sizin ile engelleyebilmesi diğer genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="11e75-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>  
  
## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="11e75-171">Genişletme yöntemleri, örnek yöntemleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="11e75-171">Extension Methods, Instance Methods, and Properties</span></span>  
 <span data-ttu-id="11e75-172">Kapsam örnek yöntemi çağıran bir deyim bağımsız değişkenleri ile uyumlu bir imzası olduğunda, örnek yöntemi yerine herhangi bir genişletme yöntemi seçilir.</span><span class="sxs-lookup"><span data-stu-id="11e75-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="11e75-173">Daha iyi bir eşleşme genişletme yöntemi olsa bile, örnek yöntemi önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="11e75-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="11e75-174">Aşağıdaki örnekte, `ExampleClass` adlandırılmış bir örnek yöntemi içerir `ExampleMethod` türünde bir parametre olan `Integer`.</span><span class="sxs-lookup"><span data-stu-id="11e75-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="11e75-175">Genişletme yöntemi `ExampleMethod` genişletir `ExampleClass`, ve parametresinin türü `Long`.</span><span class="sxs-lookup"><span data-stu-id="11e75-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 <span data-ttu-id="11e75-176">İlk çağrıda `ExampleMethod` aşağıdaki kodda genişletme yöntemi çağırır çünkü `arg1` olan `Long` ve yalnızca ile uyumlu `Long` genişletme yöntemi parametresinde.</span><span class="sxs-lookup"><span data-stu-id="11e75-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="11e75-177">İkinci çağrı `ExampleMethod` sahip bir `Integer` bağımsız değişkeni, `arg2`, ve örnek yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="11e75-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 <span data-ttu-id="11e75-178">Şimdi geriye doğru parametrelere iki yöntem de veri türleri:</span><span class="sxs-lookup"><span data-stu-id="11e75-178">Now reverse the data types of the parameters in the two methods:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 <span data-ttu-id="11e75-179">Bu sefer kodda `Main` iki kez örneği yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="11e75-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="11e75-180">Bunun nedeni, her ikisi de `arg1` ve `arg2` değerine Genişletme dönüşümü `Long`, ve örnek yöntemi her iki durumda da genişletme yöntemi önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="11e75-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 <span data-ttu-id="11e75-181">Bu nedenle, bir genişletme yöntemi, varolan bir örnek yöntemi değiştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="11e75-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="11e75-182">Ancak, bir genişletme yöntemi örnek yöntemi olarak aynı ada sahip ancak imzaları çakışmasını yöntemlerin her ikisi de erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="11e75-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="11e75-183">Örneğin, varsa sınıfı `ExampleClass` adlı bir yöntem içerir `ExampleMethod` hiçbir bağımsız değişkenler, aynı ada sahip genişletme yöntemleri alır ancak farklı imzalar izin verilir, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="11e75-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 <span data-ttu-id="11e75-184">Bu kod çıkışı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="11e75-184">The output from this code is as follows:</span></span>  
  
 `Extension method`  
  
 `Instance method`  
  
 <span data-ttu-id="11e75-185">Durum özelliklerle basittir: bir genişletme yöntemi, genişletir sınıfın özelliği aynı ada sahipse, genişletme yöntemi görünür değil ve erişilemiyor.</span><span class="sxs-lookup"><span data-stu-id="11e75-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>  
  
## <a name="extension-method-precedence"></a><span data-ttu-id="11e75-186">Uzantı yöntemi önceliği</span><span class="sxs-lookup"><span data-stu-id="11e75-186">Extension Method Precedence</span></span>  
 <span data-ttu-id="11e75-187">Daha yüksek önceliğe sahip olanla aynı imzaya sahip iki uzantı yöntemleri kapsamında ve erişilebilir olduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="11e75-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="11e75-188">Bir uzantı yöntemin öncelik yöntemi kapsam içine getirmek için kullanılan mekanizmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="11e75-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="11e75-189">Aşağıdaki listede yüksekten en düşüğe öncelik hiyerarşisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="11e75-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>  
  
1.  <span data-ttu-id="11e75-190">İçinde bulunduğu geçerli modülü tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="11e75-190">Extension methods defined inside the current module.</span></span>  
  
2.  <span data-ttu-id="11e75-191">Genişletme yöntemleri içinde veri türleri geçerli ad veya üst öğelerinden birini üst ad alanları daha yüksek önceliğe sahip alt ad ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="11e75-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>  
  
3.  <span data-ttu-id="11e75-192">Geçerli dosyasında bulunan tüm türü içeri aktarmalar içinde tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="11e75-192">Extension methods defined inside any type imports in the current file.</span></span>  
  
4.  <span data-ttu-id="11e75-193">Tüm ad alanı içe aktarımlarını geçerli dosyasında içinde tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="11e75-193">Extension methods defined inside any namespace imports in the current file.</span></span>  
  
5.  <span data-ttu-id="11e75-194">Tüm proje düzeyi türü içeri aktarmalar içinde tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="11e75-194">Extension methods defined inside any project-level type imports.</span></span>  
  
6.  <span data-ttu-id="11e75-195">Tüm proje düzeyi ad alanı içeri aktarmalar içinde tanımlanan genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="11e75-195">Extension methods defined inside any project-level namespace imports.</span></span>  
  
 <span data-ttu-id="11e75-196">Öncelik belirsizliği çözmezse tam adı, aradığınız yöntemini belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11e75-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="11e75-197">Varsa `Print` yöntemi önceki örnekte adlı bir modülde tanımlanan `StringExtensions`, tam ad `StringExtensions.Print(example)` yerine `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="11e75-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e75-198">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11e75-198">See Also</span></span>  
 <xref:System.Runtime.CompilerServices>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [<span data-ttu-id="11e75-199">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="11e75-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [<span data-ttu-id="11e75-200">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="11e75-200">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="11e75-201">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="11e75-201">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="11e75-202">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="11e75-202">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="11e75-203">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="11e75-203">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="11e75-204">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="11e75-204">Attributes overview</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="11e75-205">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="11e75-205">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
