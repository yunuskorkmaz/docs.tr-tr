---
description: 'Hakkında daha fazla bilgi edinin: using deyimleri (Visual Basic)'
title: Using Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: fea77a441182b7c3ecac58d4fe7f1297a87f086c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740892"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="71a0d-103">Using Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71a0d-103">Using Statement (Visual Basic)</span></span>

<span data-ttu-id="71a0d-104">Bir bloğun başlangıcını bildirir `Using` ve isteğe bağlı olarak, blok denetimlerinin bulunduğu sistem kaynaklarını alır.</span><span class="sxs-lookup"><span data-stu-id="71a0d-104">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>

## <a name="syntax"></a><span data-ttu-id="71a0d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="71a0d-105">Syntax</span></span>

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a><span data-ttu-id="71a0d-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="71a0d-106">Parts</span></span>

|<span data-ttu-id="71a0d-107">Süre</span><span class="sxs-lookup"><span data-stu-id="71a0d-107">Term</span></span>|<span data-ttu-id="71a0d-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="71a0d-108">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="71a0d-109">Belirtmezseniz gereklidir `resourceexpression` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-109">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="71a0d-110">Bu `Using` blok tarafından denetimlerin, virgülle ayrılmış bir veya daha fazla sistem kaynağı listesi.</span><span class="sxs-lookup"><span data-stu-id="71a0d-110">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="71a0d-111">Belirtmezseniz gereklidir `resourcelist` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-111">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="71a0d-112">Bu blok tarafından denetlenebilecek bir sistem kaynağına başvuran başvuru değişkeni veya ifadesi `Using` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-112">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="71a0d-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="71a0d-113">Optional.</span></span> <span data-ttu-id="71a0d-114">`Using`Bloğun çalıştığı deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="71a0d-114">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="71a0d-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="71a0d-115">Required.</span></span> <span data-ttu-id="71a0d-116">, `Using` Denetlediği tüm kaynakların bloğunun ve ayırdığından oluşan tanımı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="71a0d-116">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  

 <span data-ttu-id="71a0d-117">Parçasındaki her kaynak `resourcelist` aşağıdaki söz dizimi ve bölümlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="71a0d-117">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 <span data-ttu-id="71a0d-118">-veya-</span><span class="sxs-lookup"><span data-stu-id="71a0d-118">-or-</span></span>

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a><span data-ttu-id="71a0d-119">resourceList bölümleri</span><span class="sxs-lookup"><span data-stu-id="71a0d-119">resourcelist Parts</span></span>

|<span data-ttu-id="71a0d-120">Süre</span><span class="sxs-lookup"><span data-stu-id="71a0d-120">Term</span></span>|<span data-ttu-id="71a0d-121">Tanım</span><span class="sxs-lookup"><span data-stu-id="71a0d-121">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="71a0d-122">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="71a0d-122">Required.</span></span> <span data-ttu-id="71a0d-123">Blok denetimlerinin bulunduğu bir sistem kaynağına başvuran başvuru değişkeni `Using` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-123">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="71a0d-124">Deyimin kaynağı alması durumunda gereklidir `Using` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-124">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="71a0d-125">Kaynağı zaten aldıysanız, ikinci söz dizimi alternatifini kullanın.</span><span class="sxs-lookup"><span data-stu-id="71a0d-125">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="71a0d-126">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="71a0d-126">Required.</span></span> <span data-ttu-id="71a0d-127">Kaynağın sınıfı.</span><span class="sxs-lookup"><span data-stu-id="71a0d-127">The class of the resource.</span></span> <span data-ttu-id="71a0d-128">Sınıfın arabirimini uygulaması gerekir <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="71a0d-128">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="71a0d-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="71a0d-129">Optional.</span></span> <span data-ttu-id="71a0d-130">Bir örneği oluşturmak için oluşturucuya geçirdiğiniz bağımsız değişkenlerin listesi `resourcetype` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-130">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="71a0d-131">Bkz. [parametre listesi](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="71a0d-131">See [Parameter List](parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="71a0d-132">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="71a0d-132">Required.</span></span> <span data-ttu-id="71a0d-133">Gereksinimlerini karşılayan bir sistem kaynağına başvuran değişken veya ifade `resourcetype` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-133">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="71a0d-134">İkinci sözdizimi alternatif kullanırsanız, denetimi deyime geçirmeden önce kaynağı edinmeniz gerekir `Using` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-134">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71a0d-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71a0d-135">Remarks</span></span>

 <span data-ttu-id="71a0d-136">Bazen kodunuzun dosya tanıtıcısı, COM sarmalayıcısı veya SQL bağlantısı gibi yönetilmeyen bir kaynak olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="71a0d-136">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="71a0d-137">Bir `Using` blok, kodunuz ile işiniz bittiğinde bir veya daha fazla kaynağı elden çıkarma garantisi verir.</span><span class="sxs-lookup"><span data-stu-id="71a0d-137">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="71a0d-138">Bu, diğer kodun kullanması için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="71a0d-138">This makes them available for other code to use.</span></span>

 <span data-ttu-id="71a0d-139">Yönetilen kaynaklar, .NET Framework atık toplayıcı (GC) tarafından, sizin bölümlemeden herhangi bir ek kodlama yapılmadan elden alınır.</span><span class="sxs-lookup"><span data-stu-id="71a0d-139">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="71a0d-140">`Using`Yönetilen kaynaklar için bir bloğa ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="71a0d-140">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="71a0d-141">Ancak, `Using` çöp toplayıcıyı beklemek yerine, yönetilen bir kaynağın elden çıkarılmasını zorlamak için bir bloğu kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71a0d-141">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

 <span data-ttu-id="71a0d-142">Bir `Using` blok üç bölümden oluşur: alım, kullanım ve çıkarma.</span><span class="sxs-lookup"><span data-stu-id="71a0d-142">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>

- <span data-ttu-id="71a0d-143">*Alım* , bir değişken oluşturma ve sistem kaynağına başvuracak şekilde başlatma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="71a0d-143">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="71a0d-144">`Using`Deyimde bir veya daha fazla kaynak alabilir ya da bloğu girmeden önce tam olarak bir kaynak alabilir ve bunu `Using` deyime sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71a0d-144">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="71a0d-145">Sağlarsanız `resourceexpression` , denetimi deyime geçirmeden önce kaynağı edinmeniz gerekir `Using` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-145">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>

- <span data-ttu-id="71a0d-146">*Kullanım* , kaynaklara erişmek ve bunlarla eylemler gerçekleştirmek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="71a0d-146">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="71a0d-147">Ve arasındaki deyimler `Using` , `End Using` kaynakların kullanımını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="71a0d-147">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>

- <span data-ttu-id="71a0d-148">*Aktiften çıkarma* , <xref:System.IDisposable.Dispose%2A> içindeki nesnesinde yöntemi çağırma anlamına gelir `resourcename` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-148">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="71a0d-149">Bu, nesnenin kaynaklarını düzgün bir şekilde sonlanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="71a0d-149">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="71a0d-150">`End Using`Bildiri, blok denetimindeki kaynakları ortadan kaldırır `Using` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-150">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>

## <a name="behavior"></a><span data-ttu-id="71a0d-151">Davranış</span><span class="sxs-lookup"><span data-stu-id="71a0d-151">Behavior</span></span>

 <span data-ttu-id="71a0d-152">Bir `Using` blok, `Try` `Finally` `Try` bloğun kaynakları ve blok tarafından kullanıldığı bir... oluşturma gibi davranır `Finally` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-152">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="71a0d-153">Bu nedenle, bloğundan `Using` çıktığınızda bağımsız olarak blok kaynakların elden çıkarılmasını güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="71a0d-153">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="71a0d-154">Bunun dışında, işlenmemiş bir özel durum durumunda da geçerlidir <xref:System.StackOverflowException> .</span><span class="sxs-lookup"><span data-stu-id="71a0d-154">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>

 <span data-ttu-id="71a0d-155">İfadesiyle alınan her kaynak değişkeninin kapsamı `Using` `Using` bloğuyla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="71a0d-155">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>

 <span data-ttu-id="71a0d-156">Deyimde birden fazla sistem kaynağı belirtirseniz, efekt, bir diğeri `Using` içinde iç içe `Using` taşlarla aynı olur.</span><span class="sxs-lookup"><span data-stu-id="71a0d-156">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>

 <span data-ttu-id="71a0d-157">`resourcename`İse `Nothing` , hiçbir çağrı <xref:System.IDisposable.Dispose%2A> yapılmaz ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="71a0d-157">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>

## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="71a0d-158">Bir using bloğu Içinde yapılandırılmış özel durum Işleme</span><span class="sxs-lookup"><span data-stu-id="71a0d-158">Structured Exception Handling Within a Using Block</span></span>

 <span data-ttu-id="71a0d-159">Blok içinde oluşabilecek bir özel durumu işlemeniz gerekiyorsa `Using` , buna bir tamamlanmış `Try` ... `Finally` oluşturma ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71a0d-159">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="71a0d-160">`Using`Deyimin bir kaynağı alırken başarılı olmadığı durumu işlemeniz gerekiyorsa, olup olmadığını görmek için test edebilirsiniz `resourcename` `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-160">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>

## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="71a0d-161">Bir using bloğu yerine yapılandırılmış özel durum Işleme</span><span class="sxs-lookup"><span data-stu-id="71a0d-161">Structured Exception Handling Instead of a Using Block</span></span>

 <span data-ttu-id="71a0d-162">Kaynakların alımı üzerinde daha fazla denetime ihtiyacınız varsa veya blokta ek koda ihtiyacınız varsa `Finally` , `Using` bloğu bir... oluşturma olarak yeniden yazabilirsiniz `Try` `Finally` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-162">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="71a0d-163">Aşağıdaki örnek, `Try` `Using` alma ve aktiften çıkarma ile eşdeğer olan iskelet ve kurulumlarını gösterir `resource` .</span><span class="sxs-lookup"><span data-stu-id="71a0d-163">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>

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
> <span data-ttu-id="71a0d-164">Bloğun içindeki kod `Using` nesneyi `resourcename` başka bir değişkene atamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="71a0d-164">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="71a0d-165">`Using`Bloğundan çıktığınızda, kaynak atılmış olur ve diğer değişken işaret ettiği kaynağa erişemez.</span><span class="sxs-lookup"><span data-stu-id="71a0d-165">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>

## <a name="example"></a><span data-ttu-id="71a0d-166">Örnek</span><span class="sxs-lookup"><span data-stu-id="71a0d-166">Example</span></span>

 <span data-ttu-id="71a0d-167">Aşağıdaki örnek, log.txt adında bir dosya oluşturur ve dosyaya iki satırlık metin yazar.</span><span class="sxs-lookup"><span data-stu-id="71a0d-167">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="71a0d-168">Örnek ayrıca aynı dosyayı okur ve metin satırlarını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="71a0d-168">The example also reads that same file and displays the lines of text:</span></span>

 <span data-ttu-id="71a0d-169"><xref:System.IO.TextWriter>Ve <xref:System.IO.TextReader> sınıfları <xref:System.IDisposable> arabirimini uygulamadığından, kod, `Using` yazma ve okuma işlemlerinden sonra dosyanın doğru şekilde kapatılmasını sağlamak için deyimlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="71a0d-169">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a><span data-ttu-id="71a0d-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71a0d-170">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="71a0d-171">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="71a0d-171">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="71a0d-172">Nasıl yapılır: Bir Sistem Kaynağını Atma</span><span class="sxs-lookup"><span data-stu-id="71a0d-172">How to: Dispose of a System Resource</span></span>](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
