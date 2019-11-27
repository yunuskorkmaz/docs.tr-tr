---
title: -link
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: ecb7b0448b8ee9c1c1fc1eb9542b693d60a38ffd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335842"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="2c75d-102">-bağlantı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c75d-102">-link (Visual Basic)</span></span>
<span data-ttu-id="2c75d-103">Derleyicinin, belirtilen derlemelerdeki COM tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="2c75d-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c75d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c75d-104">Syntax</span></span>  
  
```console  
-link:fileList  
```

<span data-ttu-id="2c75d-105">veya</span><span class="sxs-lookup"><span data-stu-id="2c75d-105">or</span></span>  

```console
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="2c75d-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2c75d-106">Arguments</span></span>  
  
|<span data-ttu-id="2c75d-107">Terim</span><span class="sxs-lookup"><span data-stu-id="2c75d-107">Term</span></span>|<span data-ttu-id="2c75d-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="2c75d-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="2c75d-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2c75d-109">Required.</span></span> <span data-ttu-id="2c75d-110">Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="2c75d-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="2c75d-111">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="2c75d-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c75d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c75d-112">Remarks</span></span>  
 <span data-ttu-id="2c75d-113">`-link` seçeneği, gömülü tür bilgilerine sahip bir uygulamayı dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c75d-113">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="2c75d-114">Uygulama daha sonra, çalışma zamanı derlemesine bir başvuruya gerek duymadan gömülü tür bilgilerini uygulayan bir çalışma zamanı derlemesinde türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2c75d-114">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="2c75d-115">Çalışma zamanı derlemesinin çeşitli sürümleri yayımlanıyorsa, katıştırılmış tür bilgilerini içeren uygulama, yeniden derlenmesi gerekmeden çeşitli sürümlerle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="2c75d-115">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="2c75d-116">Bir örnek için bkz. [Izlenecek yol: yönetilen derlemelerden tür ekleme](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="2c75d-116">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="2c75d-117">`-link` seçeneğinin kullanılması özellikle COM birlikte çalışabilirliğine çalışırken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2c75d-117">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="2c75d-118">Uygulamanızın artık hedef bilgisayarda bir birincil birlikte çalışma derlemesi (PIA) gerektirmemesi için COM türlerini katıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c75d-118">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="2c75d-119">`-link` seçeneği, derleyicinin başvurulan birlikte çalışma derlemesinden alınan COM tür bilgilerini elde edilen derlenmiş koda katıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="2c75d-119">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="2c75d-120">COM türü, CLSID (GUID) değeri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="2c75d-120">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="2c75d-121">Sonuç olarak, uygulamanız aynı CLSID değerleriyle aynı COM türlerini yükleyen bir hedef bilgisayarda çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="2c75d-121">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="2c75d-122">Microsoft Office otomatikleştiren uygulamalar iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="2c75d-122">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="2c75d-123">Office gibi uygulamalar genellikle farklı sürümlerde aynı CLSID değerini tutacağından, uygulamanız hedef bilgisayarda .NET Framework 4 veya sonraki bir sürüm yüklendiği sürece başvurulan COM türlerini kullanabilir ve uygulamanız Yöntemler, özellikler veya uygulamalar kullanır. başvurulan COM türlerine dahil edilen olaylar.</span><span class="sxs-lookup"><span data-stu-id="2c75d-123">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="2c75d-124">`-link` seçeneği yalnızca arabirimleri, yapıları ve temsilcileri katıştırır.</span><span class="sxs-lookup"><span data-stu-id="2c75d-124">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="2c75d-125">COM sınıfları ekleme desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2c75d-125">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c75d-126">Kodunuzda gömülü bir COM türünün örneğini oluşturduğunuzda, uygun arabirimi kullanarak örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c75d-126">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="2c75d-127">CoClass kullanarak gömülü COM türünün bir örneğini oluşturma girişimi hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="2c75d-127">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="2c75d-128">Visual Studio 'da `-link` seçeneğini ayarlamak için bir derleme başvurusu ekleyin ve `Embed Interop Types` özelliğini **true**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2c75d-128">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="2c75d-129">`Embed Interop Types` özelliği için varsayılan değer **false**'dur.</span><span class="sxs-lookup"><span data-stu-id="2c75d-129">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="2c75d-130">Başka bir COM derlemesine (derleme B) başvuran bir COM derlemesine (derleme A) bağlarsanız, aşağıdakilerden biri doğruysa derleme B 'ye de bağlantı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2c75d-130">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="2c75d-131">Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="2c75d-131">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="2c75d-132">B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2c75d-132">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="2c75d-133">Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](libpath.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c75d-133">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="2c75d-134">[-Reference](reference.md) derleyici seçeneği gibi `-link` derleyici seçeneği, sık kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2c75d-134">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="2c75d-135">Derleyicinin Vbc. rsp dosyasını kullanmasını istemiyorsanız [-noconfig](noconfig.md) derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c75d-135">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="2c75d-136">`-link` kısa biçimi `-l`.</span><span class="sxs-lookup"><span data-stu-id="2c75d-136">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="2c75d-137">Genel türler ve katıştırılmış türler</span><span class="sxs-lookup"><span data-stu-id="2c75d-137">Generics and Embedded Types</span></span>  
 <span data-ttu-id="2c75d-138">Aşağıdaki bölümlerde, birlikte çalışma türlerini gömün uygulamalarda genel türleri kullanma sınırlamaları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2c75d-138">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="2c75d-139">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="2c75d-139">Generic Interfaces</span></span>  
 <span data-ttu-id="2c75d-140">Birlikte çalışma derlemesinden gömülü genel arabirimler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2c75d-140">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="2c75d-141">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="2c75d-141">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="2c75d-142">Genel parametrelere sahip türler</span><span class="sxs-lookup"><span data-stu-id="2c75d-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="2c75d-143">Türü bir birlikte çalışma derlemesinden gömülü olan genel bir parametreye sahip türler, bu tür bir dış derlemeden ise kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2c75d-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="2c75d-144">Bu kısıtlama, arabirimler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2c75d-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="2c75d-145">Örneğin, <xref:Microsoft.Office.Interop.Excel> derlemesinde tanımlanan <xref:Microsoft.Office.Interop.Excel.Range> arabirimini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="2c75d-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="2c75d-146">Bir kitaplık <xref:Microsoft.Office.Interop.Excel> derlemesinden birlikte çalışma türleri katıştırır ve türü <xref:Microsoft.Office.Interop.Excel.Range> arabirimi olan bir parametreye sahip genel bir tür döndüren bir yöntemi ortaya koyar, bu yöntem, aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="2c75d-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="2c75d-147">Aşağıdaki örnekte, istemci kodu <xref:System.Collections.IList> genel arabirimini hata olmadan döndüren yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="2c75d-147">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="2c75d-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c75d-148">Example</span></span>  
 <span data-ttu-id="2c75d-149">Aşağıdaki komut satırı, kaynak dosya `OfficeApp.vb` ve `COMData1.dll` ve `COMData2.dll` başvuru derlemelerini `OfficeApp.exe`üretecek şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="2c75d-149">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c75d-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c75d-150">See also</span></span>

- [<span data-ttu-id="2c75d-151">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2c75d-151">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="2c75d-152">İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma</span><span class="sxs-lookup"><span data-stu-id="2c75d-152">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="2c75d-153">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c75d-153">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="2c75d-154">-noconfig</span><span class="sxs-lookup"><span data-stu-id="2c75d-154">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="2c75d-155">-libpath</span><span class="sxs-lookup"><span data-stu-id="2c75d-155">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="2c75d-156">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="2c75d-156">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="2c75d-157">COM Birlikte Çalışma'ya Giriş</span><span class="sxs-lookup"><span data-stu-id="2c75d-157">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
