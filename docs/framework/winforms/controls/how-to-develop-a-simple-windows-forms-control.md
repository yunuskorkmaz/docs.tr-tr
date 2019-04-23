---
title: 'Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 457069cd7ac5af62e08115d84060c9c7fb25beee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328146"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="f5e32-102">Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme</span><span class="sxs-lookup"><span data-stu-id="f5e32-102">How to: Develop a Simple Windows Forms Control</span></span>
<span data-ttu-id="f5e32-103">Bu bölümde özel bir Windows Forms denetimi geliştirme için anahtar adımlarında size kılavuzluk eder.</span><span class="sxs-lookup"><span data-stu-id="f5e32-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="f5e32-104">Bu izlenecek yolda geliştirilmiş basit denetimin hizalamasını izin kendi <xref:System.Windows.Forms.Control.Text%2A> özelliği değiştirilecek.</span><span class="sxs-lookup"><span data-stu-id="f5e32-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="f5e32-105">Yükseltme değil veya olaylarını işleme.</span><span class="sxs-lookup"><span data-stu-id="f5e32-105">It does not raise or handle events.</span></span>  
  
### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="f5e32-106">Basit bir özel denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f5e32-106">To create a simple custom control</span></span>  
  
1. <span data-ttu-id="f5e32-107">Türetilen bir sınıf tanımlama <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5e32-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control {}  
    ```  
  
2. <span data-ttu-id="f5e32-108">Özelliklerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f5e32-108">Define properties.</span></span> <span data-ttu-id="f5e32-109">(Bir denetim birçok özellikleri devraldığından özelliklerini tanımlamak gerekmez <xref:System.Windows.Forms.Control> sınıfı, ancak çoğu özel denetimler genellikle ek özellikleri tanımlar.) Aşağıdaki kod parçası adlı bir özellik tanımlar `TextAlignment` , `FirstControl` görüntülenmesini biçimlendirmek için kullandığı <xref:System.Windows.Forms.Control.Text%2A> özelliği öğesinden devralınan <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="f5e32-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="f5e32-110">Özellikleri tanımlama hakkında daha fazla bilgi için bkz. [özelliklerine genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).</span><span class="sxs-lookup"><span data-stu-id="f5e32-110">For more information about defining properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     <span data-ttu-id="f5e32-111">Denetimin görsel görünümünü değiştirir bir özelliği ayarlamak, çağırmalıdır <xref:System.Windows.Forms.Control.Invalidate%2A> denetimi yeniden çizmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f5e32-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="f5e32-112"><xref:System.Windows.Forms.Control.Invalidate%2A> temel sınıfta tanımlanan <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="f5e32-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>  
  
3. <span data-ttu-id="f5e32-113">Geçersiz kılma korumalı <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi öğesinden devralınan <xref:System.Windows.Forms.Control> denetiminiz için işleme mantığı sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="f5e32-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="f5e32-114">Geçersiz olursa <xref:System.Windows.Forms.Control.OnPaint%2A>, Denetim kendisini çizmek mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="f5e32-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="f5e32-115">Aşağıdaki kod parçası, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi görüntüler <xref:System.Windows.Forms.Control.Text%2A> özelliği öğesinden devralınan <xref:System.Windows.Forms.Control> tarafından belirtilen hizalama ile `alignmentValue` alan.</span><span class="sxs-lookup"><span data-stu-id="f5e32-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4. <span data-ttu-id="f5e32-116">Öznitelikler için denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5e32-116">Provide attributes for your control.</span></span> <span data-ttu-id="f5e32-117">Öznitelikler, tasarım zamanında denetiminizi ve özellikleri ve olayları uygun şekilde görüntülemek bir görsel tasarımcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5e32-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="f5e32-118">Aşağıdaki kod parçası özniteliklere uygulanır `TextAlignment` özelliği.</span><span class="sxs-lookup"><span data-stu-id="f5e32-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="f5e32-119">Visual Studio gibi bir tasarımcıda <xref:System.ComponentModel.CategoryAttribute.Category%2A> özniteliği (kod parçasında gösterilen) bir mantıksal kategorisi altında görüntülenecek özelliği neden olur.</span><span class="sxs-lookup"><span data-stu-id="f5e32-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="f5e32-120"><xref:System.ComponentModel.DescriptionAttribute.Description%2A> Öznitelik neden olur, alt kısmında görüntülenmesi açıklayıcı bir dize **özellikleri** penceresi zaman `TextAlignment` özellik seçildiğinde.</span><span class="sxs-lookup"><span data-stu-id="f5e32-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="f5e32-121">Öznitelikler hakkında daha fazla bilgi için bkz. [bileşenler için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="f5e32-121">For more information about attributes, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5. <span data-ttu-id="f5e32-122">(isteğe bağlı) Kaynaklar için denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5e32-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="f5e32-123">Derleyici seçeneğini kullanarak denetlemek için bir bit eşlem gibi bir kaynak sağlayabilir (`/res` için C#) ile denetiminizi paket kaynaklarına.</span><span class="sxs-lookup"><span data-stu-id="f5e32-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="f5e32-124">Çalışma zamanında, kaynak yöntemleri kullanılarak alınabilir <xref:System.Resources.ResourceManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5e32-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="f5e32-125">Oluşturma ve kaynakları kullanma hakkında daha fazla bilgi için bkz. [masaüstü uygulamalarında kaynakların](../../resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="f5e32-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../resources/index.md).</span></span>  
  
6. <span data-ttu-id="f5e32-126">Derleme ve denetim dağıtın.</span><span class="sxs-lookup"><span data-stu-id="f5e32-126">Compile and deploy your control.</span></span> <span data-ttu-id="f5e32-127">Derlemek ve dağıtmak için `FirstControl,` aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="f5e32-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>  
  
    1.  <span data-ttu-id="f5e32-128">Aşağıdaki örnek bir kaynak dosyasına (örneğin, FirstControl.cs veya FirstControl.vb) kod kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f5e32-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>  
  
    2.  <span data-ttu-id="f5e32-129">Kaynak kodu bir araya derlemek ve uygulamanızın dizine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f5e32-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="f5e32-130">Bunu yapmak için kaynak dosyasını içeren dizinden aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="f5e32-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         <span data-ttu-id="f5e32-131">`/t:library` Derleyici seçeneği derleyici oluşturduğunuz derleme bir kitaplık (ve çalıştırılabilir değil) olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="f5e32-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="f5e32-132">`/out` Seçeneği derlemenin adını ve yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f5e32-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="f5e32-133">`/r` Seçeneği, kodunuz tarafından başvurulan bir derleme adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5e32-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="f5e32-134">Bu örnekte, yalnızca uygulamalarınızı kullanabileceğiniz özel bir derleme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5e32-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="f5e32-135">Bu nedenle, uygulamanızın dizininde kaydetmek sahip.</span><span class="sxs-lookup"><span data-stu-id="f5e32-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="f5e32-136">Paketleme ve dağıtım için bir denetim dağıtma hakkında daha fazla bilgi için bkz. [dağıtım](../../deployment/index.md).</span><span class="sxs-lookup"><span data-stu-id="f5e32-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../deployment/index.md).</span></span>  
  
 <span data-ttu-id="f5e32-137">Aşağıdaki örnek kodu gösterilir `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="f5e32-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="f5e32-138">Denetimin ad alanı içinde alınmış `CustomWinControls`.</span><span class="sxs-lookup"><span data-stu-id="f5e32-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="f5e32-139">Bir ad alanı, ilişkili mantıksal bir gruplandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5e32-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="f5e32-140">Yeni veya mevcut bir ad alanındaki denetim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5e32-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="f5e32-141">C# ' ta, `using` bildirimi (Visual Basic'te `Imports`) türünün tam adını kullanarak olmadan bir ad alanından erişilecek türlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="f5e32-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="f5e32-142">Aşağıdaki örnekte, `using` bildirimi sağlar sınıfını erişmek için kod <xref:System.Windows.Forms.Control> gelen <xref:System.Windows.Forms?displayProperty=nameWithType> basit <xref:System.Windows.Forms.Control> tam adı kullanmak zorunda olmak yerine <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5e32-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="f5e32-143">Formda özel denetim kullanarak</span><span class="sxs-lookup"><span data-stu-id="f5e32-143">Using the Custom Control on a Form</span></span>  
 <span data-ttu-id="f5e32-144">Aşağıdaki örnek, kullanan basit bir form gösterir `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="f5e32-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="f5e32-145">Üç örneklerini oluşturur `FirstControl`, her biri için farklı bir değerle `TextAlignment` özelliği.</span><span class="sxs-lookup"><span data-stu-id="f5e32-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>  
  
#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="f5e32-146">Derlemek ve bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f5e32-146">To compile and run this sample</span></span>  
  
1. <span data-ttu-id="f5e32-147">Kodu aşağıdaki örnekte bir kaynak dosyasına (SimpleForm.cs veya SimpleForms.vb) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f5e32-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
2. <span data-ttu-id="f5e32-148">Kaynak kodu, yürütülebilir bir derlemeye kaynak dosyasını içeren dizinden aşağıdaki komutu yürüterek derleyin.</span><span class="sxs-lookup"><span data-stu-id="f5e32-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     <span data-ttu-id="f5e32-149">CustomWinControls.dll olan sınıfı içeren derlemeyi `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="f5e32-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="f5e32-150">Bu derleme (SimpleForm.cs veya SimpleForms.vb) eriştiği formu için kaynak dosyayla aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f5e32-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
3. <span data-ttu-id="f5e32-151">Aşağıdaki komutu kullanarak SimpleForm.exe yürütün.</span><span class="sxs-lookup"><span data-stu-id="f5e32-151">Execute SimpleForm.exe using the following command.</span></span>  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="f5e32-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5e32-152">See also</span></span>

- [<span data-ttu-id="f5e32-153">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="f5e32-153">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="f5e32-154">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="f5e32-154">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
