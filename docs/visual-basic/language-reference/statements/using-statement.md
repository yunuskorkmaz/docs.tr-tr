---
title: Using Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: fe53ea58dc98a4de793fe9dad1c3ceeac71622fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843207"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="7be8a-102">Using Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7be8a-102">Using Statement (Visual Basic)</span></span>
<span data-ttu-id="7be8a-103">Başlangıcı bildiren bir `Using` engelleyin ve isteğe bağlı olarak blok denetleyen sistem kaynaklarını alır.</span><span class="sxs-lookup"><span data-stu-id="7be8a-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be8a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7be8a-104">Syntax</span></span>  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a><span data-ttu-id="7be8a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7be8a-105">Parts</span></span>  
  
|<span data-ttu-id="7be8a-106">Terim</span><span class="sxs-lookup"><span data-stu-id="7be8a-106">Term</span></span>|<span data-ttu-id="7be8a-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="7be8a-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="7be8a-108">Gerekli değil sağladığınız varsa `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="7be8a-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="7be8a-109">Listesinde bir veya daha fazla sistem kaynakları bu `Using` block denetimleri, virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7be8a-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="7be8a-110">Gerekli değil sağladığınız varsa `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="7be8a-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="7be8a-111">Başvuru değişkenin veya ifadenin bu tarafından denetlenmesi için bir sistem kaynağını başvuran `Using` blok.</span><span class="sxs-lookup"><span data-stu-id="7be8a-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="7be8a-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7be8a-112">Optional.</span></span> <span data-ttu-id="7be8a-113">Deyimler bloğunu, `Using` bloğu çalışır.</span><span class="sxs-lookup"><span data-stu-id="7be8a-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="7be8a-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7be8a-114">Required.</span></span> <span data-ttu-id="7be8a-115">Tanımını sonlandırır `Using` bloğu hem de denetlediğini tüm kaynakları siler.</span><span class="sxs-lookup"><span data-stu-id="7be8a-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  
  
 <span data-ttu-id="7be8a-116">Her kaynağın `resourcelist` bölümü aşağıdaki söz dizimini ve bölümleri sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7be8a-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 <span data-ttu-id="7be8a-117">veya</span><span class="sxs-lookup"><span data-stu-id="7be8a-117">-or-</span></span>  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a><span data-ttu-id="7be8a-118">resourcelist bölümleri</span><span class="sxs-lookup"><span data-stu-id="7be8a-118">resourcelist Parts</span></span>  
  
|<span data-ttu-id="7be8a-119">Terim</span><span class="sxs-lookup"><span data-stu-id="7be8a-119">Term</span></span>|<span data-ttu-id="7be8a-120">Tanım</span><span class="sxs-lookup"><span data-stu-id="7be8a-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="7be8a-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7be8a-121">Required.</span></span> <span data-ttu-id="7be8a-122">Bir sistem kaynağa başvuruda bulunan bir başvuru değişkenini, `Using` denetimleri engelleyin.</span><span class="sxs-lookup"><span data-stu-id="7be8a-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="7be8a-123">Gerekli if `Using` deyimi kaynak alır.</span><span class="sxs-lookup"><span data-stu-id="7be8a-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="7be8a-124">Kaynak aldıysanız, ikinci sözdizimi alternatifi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7be8a-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="7be8a-125">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7be8a-125">Required.</span></span> <span data-ttu-id="7be8a-126">Kaynak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7be8a-126">The class of the resource.</span></span> <span data-ttu-id="7be8a-127">Sınıf uygulamalıdır <xref:System.IDisposable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7be8a-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="7be8a-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7be8a-128">Optional.</span></span> <span data-ttu-id="7be8a-129">Oluşturucuya bir örneğini oluşturmak için kaçı bağımsız değişkenlerinin listesi `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="7be8a-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="7be8a-130">Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="7be8a-130">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="7be8a-131">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7be8a-131">Required.</span></span> <span data-ttu-id="7be8a-132">Değişkenin veya ifadenin gereksinimlerini karşılayan bir sistem kaynağa başvuran `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="7be8a-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="7be8a-133">İkinci sözdizimi alternatif kullanırsanız, kaynak denetimine geçirmeden önce almalıdır `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7be8a-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7be8a-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7be8a-134">Remarks</span></span>  
 <span data-ttu-id="7be8a-135">Bazen bir dosya tanıtıcısı, COM sarmalayıcı veya bir SQL bağlantı gibi yönetilmeyen bir kaynağı kodunuzu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7be8a-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="7be8a-136">A `Using` blok kodunuz ile bunları tamamlandığında bir veya daha fazla gibi kaynakların elden garanti eder.</span><span class="sxs-lookup"><span data-stu-id="7be8a-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="7be8a-137">Bu bunları kullanmak başka bir kod için kullanılabilir yapar.</span><span class="sxs-lookup"><span data-stu-id="7be8a-137">This makes them available for other code to use.</span></span>  
  
 <span data-ttu-id="7be8a-138">Yönetilen kaynaklar, .NET Framework atık toplayıcı (GC) tarafından ek kodlamaya bulunmanıza gerek kalmadan kaldırıldıklarından.</span><span class="sxs-lookup"><span data-stu-id="7be8a-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="7be8a-139">Gereksinim duymadığınız bir `Using` yönetilen kaynaklar için blok.</span><span class="sxs-lookup"><span data-stu-id="7be8a-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="7be8a-140">Ancak, yine de kullanabileceğiniz bir `Using` çöp toplayıcının beklemek yerine bir yönetilen kaynak elden zorlamak için blok.</span><span class="sxs-lookup"><span data-stu-id="7be8a-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="7be8a-141">A `Using` bloğu üç bölümü vardır: alım, kullanım ve silinecek.</span><span class="sxs-lookup"><span data-stu-id="7be8a-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>  
  
-   <span data-ttu-id="7be8a-142">*Alım* bir değişken oluşturma ve sistem kaynağına başvurmak için başlatma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7be8a-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="7be8a-143">`Using` Deyimi bir veya daha fazla kaynak elde veya tam olarak bir kaynak blok girmeden önce almak ve sağlamak için `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7be8a-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="7be8a-144">Sağlarsanız, `resourceexpression`, kaynak denetimine geçirmeden önce almalıdır `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7be8a-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>  
  
-   <span data-ttu-id="7be8a-145">*Kullanım* kaynaklara erişirken ve bunları eylemleri gerçekleştirme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7be8a-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="7be8a-146">Deyimleri arasında `Using` ve `End Using` kaynak kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7be8a-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>  
  
-   <span data-ttu-id="7be8a-147">*Çıkarma* çağırma anlamına gelir <xref:System.IDisposable.Dispose%2A> nesneye yöntemi `resourcename`.</span><span class="sxs-lookup"><span data-stu-id="7be8a-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="7be8a-148">Bu nesne kaynaklarını düzgün bir şekilde sonlandırmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7be8a-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="7be8a-149">`End Using` Deyimi siler altında kaynakların `Using` bloğun denetimi.</span><span class="sxs-lookup"><span data-stu-id="7be8a-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="7be8a-150">Davranış</span><span class="sxs-lookup"><span data-stu-id="7be8a-150">Behavior</span></span>  
 <span data-ttu-id="7be8a-151">A `Using` blok davranacağını gibi bir `Try`... `Finally` , yapım `Try` blok kaynakları kullanır ve `Finally` blok onları siler.</span><span class="sxs-lookup"><span data-stu-id="7be8a-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="7be8a-152">Bu nedenle, `Using` blok blok çıkış ne olursa olsun, kaynakların elden garanti eder.</span><span class="sxs-lookup"><span data-stu-id="7be8a-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="7be8a-153">Hatta işlenmeyen bir özel durum söz konusu olduğunda, bu doğrudur dışında bir <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="7be8a-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>  
  
 <span data-ttu-id="7be8a-154">Tarafından alınan her kaynak değişkenin kapsamını `Using` deyimdir sınırlı `Using` blok.</span><span class="sxs-lookup"><span data-stu-id="7be8a-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>  
  
 <span data-ttu-id="7be8a-155">Birden fazla sistem kaynağında belirtirseniz `Using` deyimi, etkin olduğu aynı iç içe kabul `Using` içindeki başka bir engeller.</span><span class="sxs-lookup"><span data-stu-id="7be8a-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>  
  
 <span data-ttu-id="7be8a-156">Varsa `resourcename` olduğu `Nothing`, hiçbir <xref:System.IDisposable.Dispose%2A> yapılmış ve hiçbir özel durum.</span><span class="sxs-lookup"><span data-stu-id="7be8a-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>  
  
## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="7be8a-157">Yapılandırılmış özel durum işleme kullanan bir blok içinde</span><span class="sxs-lookup"><span data-stu-id="7be8a-157">Structured Exception Handling Within a Using Block</span></span>  
 <span data-ttu-id="7be8a-158">İçinde oluşabilecek bir özel durumu işlemek gereken `Using` bloğu tam ekleyebilirsiniz `Try`... `Finally` ona oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7be8a-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="7be8a-159">Durumu işlemek gerekirse burada `Using` deyimi, bir kaynak edinilirken başarılı değil, olmadığını sınayabilirsiniz `resourcename` olduğu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7be8a-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="7be8a-160">Yapılandırılmış özel durum işleme kullanan bir bloğu yerine</span><span class="sxs-lookup"><span data-stu-id="7be8a-160">Structured Exception Handling Instead of a Using Block</span></span>  
 <span data-ttu-id="7be8a-161">Edinme kaynakları üzerinde daha hassas bir denetime ihtiyacınız varsa veya ek kod, ihtiyaç duyarsanız `Finally` bloğu, yeniden `Using` olarak engelleyecek bir `Try`... `Finally` oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7be8a-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="7be8a-162">Aşağıdaki örnek, çatı gösterir `Try` ve `Using` edinme ve elden yapılarını `resource`.</span><span class="sxs-lookup"><span data-stu-id="7be8a-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>  
  
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
>  <span data-ttu-id="7be8a-163">İçinde kod `Using` blok atama nesnesinde `resourcename` başka bir değişkene.</span><span class="sxs-lookup"><span data-stu-id="7be8a-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="7be8a-164">Çıktığınızda `Using` blok, kaynak bırakıldı ve diğer değişkenin işaret ettiği kaynağa erişemiyor.</span><span class="sxs-lookup"><span data-stu-id="7be8a-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7be8a-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="7be8a-165">Example</span></span>  
 <span data-ttu-id="7be8a-166">Aşağıdaki örnek, iki satırlık bir metin dosyasına yazar ve log.txt adlı bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7be8a-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="7be8a-167">Örnek ayrıca, aynı dosyasını okur ve metin satırlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7be8a-167">The example also reads that same file and displays the lines of text.</span></span>  
  
 <span data-ttu-id="7be8a-168">Çünkü <xref:System.IO.TextWriter> ve <xref:System.IO.TextReader> sınıfları uygulama <xref:System.IDisposable> arabirimi, kod kullanabileceğiniz `Using` deyimlerini dosyanın doğru kapalı sonra yazma ve okuma işlemleri sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="7be8a-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a><span data-ttu-id="7be8a-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7be8a-169">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="7be8a-170">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="7be8a-170">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="7be8a-171">Nasıl yapılır: Bir sistem kaynağını atma</span><span class="sxs-lookup"><span data-stu-id="7be8a-171">How to: Dispose of a System Resource</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
