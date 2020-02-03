---
title: Basit denetim geliştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 5383cee5358dbd260fc6c023d3db607da6b10ea4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742261"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="80a35-102">Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme</span><span class="sxs-lookup"><span data-stu-id="80a35-102">How to: Develop a Simple Windows Forms Control</span></span>

<span data-ttu-id="80a35-103">Bu bölümde, özel bir Windows Forms denetimi yazmak için temel adımlarda izlenecek yol gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="80a35-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="80a35-104">Bu izlenecek yolda geliştirilen basit denetim <xref:System.Windows.Forms.Control.Text%2A> özelliğinin hizalanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="80a35-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="80a35-105">Olayları oluşturmaz veya işlemez.</span><span class="sxs-lookup"><span data-stu-id="80a35-105">It does not raise or handle events.</span></span>

### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="80a35-106">Basit bir özel denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="80a35-106">To create a simple custom control</span></span>

1. <span data-ttu-id="80a35-107"><xref:System.Windows.Forms.Control?displayProperty=nameWithType>türeten bir sınıf tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="80a35-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>

    ```vb
    Public Class FirstControl
       Inherits Control

    End Class
    ```

    ```csharp
    public class FirstControl:Control {}
    ```

2. <span data-ttu-id="80a35-108">Özellikleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="80a35-108">Define properties.</span></span> <span data-ttu-id="80a35-109">(Bir denetim <xref:System.Windows.Forms.Control> sınıfından birçok özelliği devraldığından, ancak çoğu özel denetim genellikle ek özellikler tanımlayacağından, özellikleri tanımlamanız gerekmez.) Aşağıdaki kod parçası, <xref:System.Windows.Forms.Control>devralınmış <xref:System.Windows.Forms.Control.Text%2A> özelliğinin görüntülenmesini biçimlendirmek için `FirstControl` tarafından kullanılan `TextAlignment` adlı bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80a35-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="80a35-110">Özellikleri tanımlama hakkında daha fazla bilgi için bkz. [özelliklere genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).</span><span class="sxs-lookup"><span data-stu-id="80a35-110">For more information about defining properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).</span></span>

     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]

     <span data-ttu-id="80a35-111">Denetimin görsel görüntüsünü değiştiren bir özelliği ayarladığınızda, denetimi yeniden çizmek için <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="80a35-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="80a35-112"><xref:System.Windows.Forms.Control.Invalidate%2A>, temel sınıfta <xref:System.Windows.Forms.Control>tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="80a35-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>

3. <span data-ttu-id="80a35-113">Denetiminizin işleme mantığını sağlamak için <xref:System.Windows.Forms.Control> devralınmış korunan <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="80a35-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="80a35-114"><xref:System.Windows.Forms.Control.OnPaint%2A>geçersiz kılamazsınız, denetiminiz kendisini çizmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="80a35-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="80a35-115">Aşağıdaki kod parçasında <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi, `alignmentValue` alanı tarafından belirtilen hizalamayla <xref:System.Windows.Forms.Control> devralınan <xref:System.Windows.Forms.Control.Text%2A> özelliğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="80a35-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]

4. <span data-ttu-id="80a35-116">Denetiminizin özniteliklerini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="80a35-116">Provide attributes for your control.</span></span> <span data-ttu-id="80a35-117">Öznitelikler görsel tasarımcı 'nın, tasarım zamanında denetiminizi ve özelliklerini ve olaylarını uygun şekilde görüntülemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="80a35-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="80a35-118">Aşağıdaki kod parçası, `TextAlignment` özelliğine öznitelikler uygular.</span><span class="sxs-lookup"><span data-stu-id="80a35-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="80a35-119">Visual Studio gibi bir tasarımcıda <xref:System.ComponentModel.CategoryAttribute.Category%2A> özniteliği (kod parçasında gösterilmektedir) özelliğin bir mantıksal kategori altında görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="80a35-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="80a35-120"><xref:System.ComponentModel.DescriptionAttribute.Description%2A> özniteliği, `TextAlignment` özelliği seçildiğinde **Özellikler** penceresinin alt kısmında açıklayıcı bir dizenin görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="80a35-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="80a35-121">Öznitelikler hakkında daha fazla bilgi için bkz. [Bileşenler Için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="80a35-121">For more information about attributes, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>

     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]

5. <span data-ttu-id="80a35-122">seçim Denetiminizin kaynaklarını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="80a35-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="80a35-123">Denetim için bir derleyici seçeneği (`/res` için C#) kullanarak denetim için bit eşlem gibi bir kaynak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80a35-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="80a35-124">Çalışma zamanında, kaynak <xref:System.Resources.ResourceManager> sınıfının yöntemleri kullanılarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="80a35-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="80a35-125">Kaynakları oluşturma ve kullanma hakkında daha fazla bilgi için, bkz. [Masaüstü uygulamalarındaki kaynaklar](../../resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="80a35-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../resources/index.md).</span></span>

6. <span data-ttu-id="80a35-126">Denetiminizi derleyin ve dağıtın.</span><span class="sxs-lookup"><span data-stu-id="80a35-126">Compile and deploy your control.</span></span> <span data-ttu-id="80a35-127">Derlemek ve dağıtmak için `FirstControl,` aşağıdaki adımları yürütün:</span><span class="sxs-lookup"><span data-stu-id="80a35-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>

    1. <span data-ttu-id="80a35-128">Aşağıdaki örnekteki kodu bir kaynak dosyasına kaydedin (örneğin, FirstControl.cs veya FirstControl. vb).</span><span class="sxs-lookup"><span data-stu-id="80a35-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>

    2. <span data-ttu-id="80a35-129">Kaynak kodu bir derlemede derleyin ve uygulamanızın dizinine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="80a35-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="80a35-130">Bunu gerçekleştirmek için, kaynak dosyayı içeren dizinden aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="80a35-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>

        ```console
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb
        ```

        ```console
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs
        ```

         <span data-ttu-id="80a35-131">`/t:library` derleyici seçeneği derleyiciye oluşturmakta olduğunuz derlemenin bir kitaplık (yürütülebilir değil) olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="80a35-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="80a35-132">`/out` seçeneği, derlemenin yolunu ve adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="80a35-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="80a35-133">`/r` seçeneği, kodunuzun başvurduğu derlemelerin adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="80a35-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="80a35-134">Bu örnekte, yalnızca uygulamalarınızın kullanabileceği özel bir derleme oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="80a35-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="80a35-135">Bu nedenle, uygulamayı uygulamanızın dizinine kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="80a35-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="80a35-136">Dağıtım için bir denetim paketleme ve dağıtma hakkında daha fazla bilgi için bkz. [dağıtım](../../deployment/index.md).</span><span class="sxs-lookup"><span data-stu-id="80a35-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../deployment/index.md).</span></span>

<span data-ttu-id="80a35-137">Aşağıdaki örnekte `FirstControl`kodu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="80a35-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="80a35-138">Denetim ad alanı `CustomWinControls`alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="80a35-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="80a35-139">Bir ad alanı ilgili türlerin mantıksal bir gruplandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="80a35-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="80a35-140">Denetiminizi yeni veya mevcut bir ad alanında oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80a35-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="80a35-141">' C#De `using` bildirimine (Visual Basic, `Imports`), türün tam adı kullanılmadan bir ad alanından erişilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="80a35-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="80a35-142">Aşağıdaki örnekte `using` bildirimi, kodun, <xref:System.Windows.Forms.Control?displayProperty=nameWithType>tam adı kullanmak yerine <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms?displayProperty=nameWithType> <xref:System.Windows.Forms.Control> sınıfına erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="80a35-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>

[!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
[!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]

## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="80a35-143">Bir form üzerinde özel denetimi kullanma</span><span class="sxs-lookup"><span data-stu-id="80a35-143">Using the Custom Control on a Form</span></span>

<span data-ttu-id="80a35-144">Aşağıdaki örnekte `FirstControl`kullanan basit bir form gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="80a35-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="80a35-145">Her biri `TextAlignment` özelliği için farklı bir değere sahip `FirstControl`üç örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="80a35-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>

#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="80a35-146">Bu örneği derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="80a35-146">To compile and run this sample</span></span>

1. <span data-ttu-id="80a35-147">Aşağıdaki örnekteki kodu bir kaynak dosyasına (SimpleForm.cs veya SimpleForms. vb) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="80a35-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>

2. <span data-ttu-id="80a35-148">Kaynak dosyayı içeren dizinden aşağıdaki komutu yürüterek, kaynak kodu yürütülebilir bir derlemede derleyin.</span><span class="sxs-lookup"><span data-stu-id="80a35-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>

    ```console
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb
    ```

    ```console
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs
    ```

     <span data-ttu-id="80a35-149">CustomWinControls. dll, `FirstControl`sınıfını içeren derlemedir.</span><span class="sxs-lookup"><span data-stu-id="80a35-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="80a35-150">Bu derleme, kendisine erişen form için kaynak dosyayla aynı dizinde olmalıdır (SimpleForm.cs veya SimpleForms. vb).</span><span class="sxs-lookup"><span data-stu-id="80a35-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>

3. <span data-ttu-id="80a35-151">Aşağıdaki komutu kullanarak SimpleForm. exe ' yi yürütün.</span><span class="sxs-lookup"><span data-stu-id="80a35-151">Execute SimpleForm.exe using the following command.</span></span>

    ```console
    SimpleForm
    ```

[!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
[!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]

## <a name="see-also"></a><span data-ttu-id="80a35-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80a35-152">See also</span></span>

- [<span data-ttu-id="80a35-153">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="80a35-153">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="80a35-154">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="80a35-154">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
