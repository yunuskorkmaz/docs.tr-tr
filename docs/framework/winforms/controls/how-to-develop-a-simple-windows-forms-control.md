---
title: "Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da876ec74bf80d4329451a9bf125421731c7f9de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="b916d-102">Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme</span><span class="sxs-lookup"><span data-stu-id="b916d-102">How to: Develop a Simple Windows Forms Control</span></span>
<span data-ttu-id="b916d-103">Bu bölüm, özel bir Windows Forms denetimi geliştirme için önemli adımlar anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b916d-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="b916d-104">Bu kılavuzda geliştirilmiş basit denetim hizalamasını sağlar, <xref:System.Windows.Forms.Control.Text%2A> değiştirilecek özelliği.</span><span class="sxs-lookup"><span data-stu-id="b916d-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="b916d-105">Yükseltme değil veya olayları işlemek.</span><span class="sxs-lookup"><span data-stu-id="b916d-105">It does not raise or handle events.</span></span>  
  
### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="b916d-106">Basit bir özel denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b916d-106">To create a simple custom control</span></span>  
  
1.  <span data-ttu-id="b916d-107">Türeyen bir sınıf tanımlama <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b916d-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  <span data-ttu-id="b916d-108">Özellikleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b916d-108">Define properties.</span></span> <span data-ttu-id="b916d-109">(Bir denetim birçok özelliklerinden devralındığından özelliklerini tanımlamak gerekmez <xref:System.Windows.Forms.Control> sınıfı, ancak çoğu özel denetimler genellikle ek özellikleri tanımlar.) Aşağıdaki kod parçası adlı bir özelliğini tanımlar `TextAlignment` , `FirstControl` görüntüsünü biçimlendirmek için kullandığı <xref:System.Windows.Forms.Control.Text%2A> özelliği devralınan <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="b916d-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="b916d-110">Özellikleri tanımlama hakkında daha fazla bilgi için bkz: [özelliklerine genel bakış](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="b916d-110">For more information about defining properties, see [Properties Overview](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     <span data-ttu-id="b916d-111">Denetim görsel görünümünü değiştirir bir özellik ayarladığınızda, çağırmanız gerekir <xref:System.Windows.Forms.Control.Invalidate%2A> denetimi yeniden boyutlandırmaya yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b916d-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="b916d-112"><xref:System.Windows.Forms.Control.Invalidate%2A>taban sınıf içinde tanımlanan <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="b916d-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>  
  
3.  <span data-ttu-id="b916d-113">Korumalı geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi devralınan <xref:System.Windows.Forms.Control> denetim işleme mantığı sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="b916d-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="b916d-114">Değil geçersiz kılarsanız <xref:System.Windows.Forms.Control.OnPaint%2A>, denetiminizi kendisini çizmek mümkün olmaz.</span><span class="sxs-lookup"><span data-stu-id="b916d-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="b916d-115">Aşağıdaki kod parçası olarak <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi görüntüler <xref:System.Windows.Forms.Control.Text%2A> özelliği devralınan <xref:System.Windows.Forms.Control> tarafından belirtilen hizalama ile `alignmentValue` alan.</span><span class="sxs-lookup"><span data-stu-id="b916d-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  <span data-ttu-id="b916d-116">Öznitelikler için denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b916d-116">Provide attributes for your control.</span></span> <span data-ttu-id="b916d-117">Öznitelikleri tasarım zamanında denetiminizi ve özellikleri ve olayları uygun şekilde görüntülemek bir görsel tasarımcı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b916d-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="b916d-118">Aşağıdaki kod parçası özniteliklere uygulanır `TextAlignment` özelliği.</span><span class="sxs-lookup"><span data-stu-id="b916d-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="b916d-119">Visual Studio gibi bir Tasarımcısı'nda <xref:System.ComponentModel.CategoryAttribute.Category%2A> (kod parçasında gösterilen) öznitelik mantıksal kategorisi altında görüntülenecek özelliği neden olur.</span><span class="sxs-lookup"><span data-stu-id="b916d-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="b916d-120"><xref:System.ComponentModel.DescriptionAttribute.Description%2A> Özniteliği neden olur. alt kısmındaki görüntülenecek tanımlayıcı bir dize **özellikleri** penceresi zaman `TextAlignment` özelliği seçilidir.</span><span class="sxs-lookup"><span data-stu-id="b916d-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="b916d-121">Öznitelikler hakkında daha fazla bilgi için bkz: [bileşenleri için tasarım zamanı öznitelikleri](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span><span class="sxs-lookup"><span data-stu-id="b916d-121">For more information about attributes, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  <span data-ttu-id="b916d-122">(isteğe bağlı) Kaynaklar için denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b916d-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="b916d-123">Derleyici seçeneği kullanarak denetlemek için bir bit eşlem gibi bir kaynak sağlayın (`/res` için C#), Denetim ile paket kaynaklarına.</span><span class="sxs-lookup"><span data-stu-id="b916d-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="b916d-124">Çalışma zamanında kaynak yöntemleri kullanılarak alınabilir <xref:System.Resources.ResourceManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b916d-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="b916d-125">Oluşturma ve kaynakları kullanma hakkında daha fazla bilgi için bkz: [masaüstü uygulamalarında kaynakları](../../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="b916d-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../../../docs/framework/resources/index.md).</span></span>  
  
6.  <span data-ttu-id="b916d-126">Derleme ve denetiminizin dağıtın.</span><span class="sxs-lookup"><span data-stu-id="b916d-126">Compile and deploy your control.</span></span> <span data-ttu-id="b916d-127">Derleme ve dağıtmak için `FirstControl,` aşağıdaki adımları yürütün:</span><span class="sxs-lookup"><span data-stu-id="b916d-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>  
  
    1.  <span data-ttu-id="b916d-128">Bir kaynak dosyaya (örneğin, FirstControl.cs veya FirstControl.vb) aşağıdaki örnekteki kod kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b916d-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>  
  
    2.  <span data-ttu-id="b916d-129">Bir derlemeye kaynak kodu derleme ve uygulamanızın dizinine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b916d-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="b916d-130">Bunu başarmak için kaynak dosyasını içeren dizininden aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="b916d-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>  
  
        ```vb  
        vbc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```csharp  
        csc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.cs  
        ```  
  
         <span data-ttu-id="b916d-131">`/t:library` Derleyici seçeneği derleyici oluşturmakta derleme kitaplık (ve bir yürütülebilir) olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b916d-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="b916d-132">`/out` Seçeneği derlemenin adını ve yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b916d-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="b916d-133">`/r` Seçeneği kodunuz tarafından başvurulan bir derleme adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b916d-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="b916d-134">Bu örnekte, yalnızca uygulamalarınızı kullanabileceğiniz özel bir derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b916d-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="b916d-135">Bu nedenle, uygulamanızın dizininde kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b916d-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="b916d-136">Paketleme ve dağıtım için bir denetim dağıtma hakkında daha fazla bilgi için bkz: [dağıtım](../../../../docs/framework/deployment/index.md).</span><span class="sxs-lookup"><span data-stu-id="b916d-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../../../docs/framework/deployment/index.md).</span></span>  
  
 <span data-ttu-id="b916d-137">Aşağıdaki örnek kodunu gösterir `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="b916d-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="b916d-138">Ad alanında denetimi içine `CustomWinControls`.</span><span class="sxs-lookup"><span data-stu-id="b916d-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="b916d-139">Bir ad alanı, ilgili türleri mantıksal bir gruplandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b916d-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="b916d-140">Yeni veya var olan bir ad alanında denetiminizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b916d-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="b916d-141">C# ' ta, `using` bildirimi (Visual Basic'te `Imports`) türünün tam adını kullanmadan bir ad alanından erişilecek türlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="b916d-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="b916d-142">Aşağıdaki örnekte, `using` bildirimi sınıfa erişmek kod sağlar <xref:System.Windows.Forms.Control> gelen <xref:System.Windows.Forms?displayProperty=nameWithType> basit <xref:System.Windows.Forms.Control> tam adı kullanmak zorunda olmak yerine <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b916d-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="b916d-143">Bir Form üzerinde özel denetimi kullanma</span><span class="sxs-lookup"><span data-stu-id="b916d-143">Using the Custom Control on a Form</span></span>  
 <span data-ttu-id="b916d-144">Aşağıdaki örnekte kullanan basit bir form gösterilmektedir `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="b916d-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="b916d-145">Üç örneklerini oluşturur `FirstControl`, her biri için farklı bir değer `TextAlignment` özelliği.</span><span class="sxs-lookup"><span data-stu-id="b916d-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>  
  
#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="b916d-146">Derlemek ve bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b916d-146">To compile and run this sample</span></span>  
  
1.  <span data-ttu-id="b916d-147">Aşağıdaki örnekte bir kaynak dosyasının (SimpleForm.cs veya SimpleForms.vb) kodunu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b916d-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
2.  <span data-ttu-id="b916d-148">Kaynak kodu kaynak dosyasını içeren dizininden aşağıdaki komutu çalıştırarak yürütülebilir bir derlemeye derleyin.</span><span class="sxs-lookup"><span data-stu-id="b916d-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>  
  
    ```vb  
    vbc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```csharp  
    csc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     <span data-ttu-id="b916d-149">CustomWinControls.dll olan sınıfı içeren bütünleştirilmiş kodun `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="b916d-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="b916d-150">Bu derleme (SimpleForm.cs veya SimpleForms.vb) eriştiği form için kaynak dosyası ile aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b916d-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
3.  <span data-ttu-id="b916d-151">Aşağıdaki komutu kullanarak SimpleForm.exe yürütün.</span><span class="sxs-lookup"><span data-stu-id="b916d-151">Execute SimpleForm.exe using the following command.</span></span>  
  
    ```  
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="b916d-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b916d-152">See Also</span></span>  
 [<span data-ttu-id="b916d-153">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="b916d-153">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="b916d-154">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="b916d-154">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
