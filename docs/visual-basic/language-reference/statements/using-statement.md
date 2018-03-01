---
title: Using Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed9cc0d04c89eac1fe342a0924dd89bb1e258a11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="8e9e4-102">Using Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e9e4-102">Using Statement (Visual Basic)</span></span>
<span data-ttu-id="8e9e4-103">Başlangıcı bildiren bir `Using` engelleme ve isteğe bağlı olarak blok denetimleri sistem kaynakları alır.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e9e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e9e4-104">Syntax</span></span>  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a><span data-ttu-id="8e9e4-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8e9e4-105">Parts</span></span>  
  
|<span data-ttu-id="8e9e4-106">Terim</span><span class="sxs-lookup"><span data-stu-id="8e9e4-106">Term</span></span>|<span data-ttu-id="8e9e4-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="8e9e4-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="8e9e4-108">Değil sağladığınız varsa gerekli `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="8e9e4-109">Listesinde bir veya daha fazla sistem kaynaklarının bu `Using` engellemek denetimleri, virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="8e9e4-110">Değil sağladığınız varsa gerekli `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="8e9e4-111">Başvuru değişkenini veya ifadesi bu tarafından denetlenmesi için bir sistem kaynağa başvuran `Using` bloğu.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="8e9e4-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-112">Optional.</span></span> <span data-ttu-id="8e9e4-113">İfadeler bloğu, `Using` engelleme çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="8e9e4-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-114">Required.</span></span> <span data-ttu-id="8e9e4-115">Tanımını sonlandırır `Using` bloğu ve denetlediği tüm kaynakları siler.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  
  
 <span data-ttu-id="8e9e4-116">Her bir kaynağın `resourcelist` bölümü aşağıdaki söz dizimini ve bölümleri sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8e9e4-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 <span data-ttu-id="8e9e4-117">veya</span><span class="sxs-lookup"><span data-stu-id="8e9e4-117">-or-</span></span>  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a><span data-ttu-id="8e9e4-118">resourcelist bölümleri</span><span class="sxs-lookup"><span data-stu-id="8e9e4-118">resourcelist Parts</span></span>  
  
|<span data-ttu-id="8e9e4-119">Terim</span><span class="sxs-lookup"><span data-stu-id="8e9e4-119">Term</span></span>|<span data-ttu-id="8e9e4-120">Tanım</span><span class="sxs-lookup"><span data-stu-id="8e9e4-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="8e9e4-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-121">Required.</span></span> <span data-ttu-id="8e9e4-122">Bir sistem kaynağı başvuruyor başvuru değişkeni, `Using` engelleme kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="8e9e4-123">Gerekli olursa `Using` deyimi kaynak edinir.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="8e9e4-124">Kaynak zaten aldıysanız, ikinci sözdizimi alternatif kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="8e9e4-125">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-125">Required.</span></span> <span data-ttu-id="8e9e4-126">Kaynak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-126">The class of the resource.</span></span> <span data-ttu-id="8e9e4-127">Sınıf uygulamalıdır <xref:System.IDisposable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="8e9e4-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-128">Optional.</span></span> <span data-ttu-id="8e9e4-129">Örneği oluşturmak için oluşturucusuna geçirerek bağımsız değişkenler listesi `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="8e9e4-130">Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="8e9e4-130">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="8e9e4-131">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-131">Required.</span></span> <span data-ttu-id="8e9e4-132">Değişken veya başvuran gereksinimlerini karşılayan bir sistem kaynağı deyim `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="8e9e4-133">İkinci sözdizimi alternatif kullanırsanız, denetimine geçirmeden önce kaynak almalıdır `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e9e4-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e9e4-134">Remarks</span></span>  
 <span data-ttu-id="8e9e4-135">Bazen bir dosya tanıtıcısı, COM sarmalayıcı veya bir SQL bağlantısı gibi yönetilmeyen bir kaynak kodunuzu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="8e9e4-136">A `Using` blok kodunuzu bunlarla tamamlandığında, bir veya daha fazla gibi kaynakların elden garanti eder.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="8e9e4-137">Bu bunları kullanmak başka bir kod için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-137">This makes them available for other code to use.</span></span>  
  
 <span data-ttu-id="8e9e4-138">Yönetilen kaynaklar için .NET Framework Atık toplayıcısının (GC) tarafından hiçbir ek kodlama yapmanız olmadan elden.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="8e9e4-139">İhtiyacınız olmayan bir `Using` yönetilen kaynaklar için bloğu.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="8e9e4-140">Ancak, kullanmaya devam edebilirsiniz bir `Using` için atık toplayıcısını beklemek yerine yönetilen bir kaynağın elden zorlamak için blok.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="8e9e4-141">A `Using` blok sahip üç bölümden: edinme, kullanım ve elden.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>  
  
-   <span data-ttu-id="8e9e4-142">*Alım* bir değişken oluşturma ve bu sistem kaynağı başvurmak için başlatma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="8e9e4-143">`Using` Deyimi bir veya daha fazla kaynak elde veya blok girmeden önce tam olarak bir kaynak almak ve ona tedarik `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="8e9e4-144">Sağladığınız varsa `resourceexpression`, kaynak denetimine geçirmeden önce almalıdır `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>  
  
-   <span data-ttu-id="8e9e4-145">*Kullanım* kaynaklara erişme ve bunlarla gerçekleştirme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="8e9e4-146">Arasında deyimleri `Using` ve `End Using` kaynak kullanımını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>  
  
-   <span data-ttu-id="8e9e4-147">*Elden* çağırma anlamına gelir <xref:System.IDisposable.Dispose%2A> yöntemi nesnedeki `resourcename`.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="8e9e4-148">Bu, düzgün bir şekilde kaynaklarını sonlandırmak nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="8e9e4-149">`End Using` Deyimi siler altında kaynakların `Using` bloğun denetim.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="8e9e4-150">Davranış</span><span class="sxs-lookup"><span data-stu-id="8e9e4-150">Behavior</span></span>  
 <span data-ttu-id="8e9e4-151">A `Using` engelleme davranacağını gibi bir `Try`... `Finally` hangi yapısında `Try` bloğu kaynakları kullanır ve `Finally` blok bunları siler.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="8e9e4-152">Bu nedenle, `Using` blok blok çıkmak nasıl olsun bu kaynakların elden güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="8e9e4-153">Bu bile işlenmeyen bir özel durum söz konusu olduğunda, geçerlidir dışında bir <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>  
  
 <span data-ttu-id="8e9e4-154">Tarafından alınan her kaynak değişkenin kapsamını `Using` deyimi sınırlıdır `Using` bloğu.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>  
  
 <span data-ttu-id="8e9e4-155">Birden fazla sistem kaynağında belirtirseniz `Using` deyimi, etkisi ise aynı iç içe gibi `Using` bir diğeri içindeki engeller.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>  
  
 <span data-ttu-id="8e9e4-156">Varsa `resourcename` olan `Nothing`, hiçbir çağrısına <xref:System.IDisposable.Dispose%2A> yapılmış ve hiçbir özel durum.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>  
  
## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="8e9e4-157">Yapılandırılmış özel durum işleme kullanan bir blokta</span><span class="sxs-lookup"><span data-stu-id="8e9e4-157">Structured Exception Handling Within a Using Block</span></span>  
 <span data-ttu-id="8e9e4-158">İçinde oluşabilecek bir özel durum işleme gerekiyorsa `Using` bloğu, bir tam ekleyebilirsiniz `Try`... `Finally` ona oluşturma.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="8e9e4-159">Servis talebi işlemek gerekirse burada `Using` deyimi bir kaynak alınırken başarılı değil, olup olmadığını sınayabilirsiniz `resourcename` olan `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="8e9e4-160">Yapılandırılmış özel durum işleme kullanan bir blok yerine</span><span class="sxs-lookup"><span data-stu-id="8e9e4-160">Structured Exception Handling Instead of a Using Block</span></span>  
 <span data-ttu-id="8e9e4-161">Kaynakları alımını üzerinde daha hassas denetim gerekir veya ek kod, ihtiyacınız varsa `Finally` bloğu yeniden yazana `Using` olarak engelleme bir `Try`... `Finally` oluşturma.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="8e9e4-162">Aşağıdaki örnek, iskelet gösterir `Try` ve `Using` edinme ve elden eşdeğer kurulumlarını `resource`.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
>  <span data-ttu-id="8e9e4-163">Kod içinde `Using` blok nesnesinde değil atamanız `resourcename` başka bir değişkene.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="8e9e4-164">Çıktığınızda `Using` bloğu, kaynak kapatılır ve diğer değişkenin işaret ettiği kaynağına erişemiyor.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e9e4-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e9e4-165">Example</span></span>  
 <span data-ttu-id="8e9e4-166">Aşağıdaki örnek log.txt adlı ve iki satırlık bir metin dosyasına yazan bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="8e9e4-167">Örnek ayrıca, aynı dosyasını okur ve metin satırlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-167">The example also reads that same file and displays the lines of text.</span></span>  
  
 <span data-ttu-id="8e9e4-168">Çünkü <xref:System.IO.TextWriter> ve <xref:System.IO.TextReader> sınıfları uygulama <xref:System.IDisposable> arabirimi kodu kullanabilirsiniz `Using` deyimleri dosyanın doğru sonra yazma kapalı ve okuma işlemlerini emin olun.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8e9e4-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e9e4-169">See Also</span></span>  
 <xref:System.IDisposable>  
 [<span data-ttu-id="8e9e4-170">Try... Catch... Finally ifadesi</span><span class="sxs-lookup"><span data-stu-id="8e9e4-170">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="8e9e4-171">Nasıl yapılır: bir sistem kaynağını atma</span><span class="sxs-lookup"><span data-stu-id="8e9e4-171">How to: Dispose of a System Resource</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
