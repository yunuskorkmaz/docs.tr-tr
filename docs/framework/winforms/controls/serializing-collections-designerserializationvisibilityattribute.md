---
title: 'İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2fbb0715d148b443b1eca8f400e4ad43eb51fa43
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015730"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a><span data-ttu-id="6c993-102">İzlenecek yol: Standart türlerin koleksiyonlarını serileştirme</span><span class="sxs-lookup"><span data-stu-id="6c993-102">Walkthrough: Serialize collections of standard types</span></span>

<span data-ttu-id="6c993-103">Özel denetimleriniz bazen bir koleksiyonu özellik olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="6c993-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="6c993-104">Bu izlenecek yol, <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> bir koleksiyonun tasarım zamanında nasıl serileştirildiği denetlemek için sınıfının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c993-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="6c993-105"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Değer koleksiyon özelliğine uygulandığında, özelliğin serileştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c993-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>

<span data-ttu-id="6c993-106">Bu konudaki kodu tek bir liste olarak kopyalamak için bkz [. nasıl yapılır: Standart türlerin koleksiyonlarını DesignerSerializationVisibilityAttribute](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))ile serileştirme.</span><span class="sxs-lookup"><span data-stu-id="6c993-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6c993-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="6c993-107">Prerequisites</span></span>

<span data-ttu-id="6c993-108">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c993-108">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-a-control-with-a-serializable-collection"></a><span data-ttu-id="6c993-109">Seri hale getirilebilir koleksiyonla bir denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="6c993-109">Create a control with a serializable collection</span></span>

<span data-ttu-id="6c993-110">İlk adım, bir seri hale getirilebilir koleksiyonu özelliği olarak bir denetim oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="6c993-110">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="6c993-111">Bu koleksiyonun içeriğini, **Özellikler** penceresinden erişebileceğiniz **koleksiyon düzenleyicisini**kullanarak düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c993-111">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>

1. <span data-ttu-id="6c993-112">Visual Studio 'da bir Windows Denetim Kitaplığı projesi oluşturun ve **SerializationDemoControlLib**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="6c993-112">In Visual Studio, create a Windows Control Library project, and name it **SerializationDemoControlLib**.</span></span>

2. <span data-ttu-id="6c993-113">`UserControl1` Olarak`SerializationDemoControl`yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="6c993-113">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="6c993-114">Daha fazla bilgi için bkz. [kod sembolünü yeniden düzenlemeyi yeniden adlandırma](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="6c993-114">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

3. <span data-ttu-id="6c993-115">**Özellikler** penceresinde, <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> özelliğinin değerini **10**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6c993-115">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to **10**.</span></span>

4. <span data-ttu-id="6c993-116">İçine bir <xref:System.Windows.Forms.TextBox> denetim koyun. `SerializationDemoControl`</span><span class="sxs-lookup"><span data-stu-id="6c993-116">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>

5. <span data-ttu-id="6c993-117"><xref:System.Windows.Forms.TextBox> Denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="6c993-117">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="6c993-118">**Özellikler** penceresinde, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6c993-118">In the **Properties** window, set the following properties.</span></span>

    |<span data-ttu-id="6c993-119">Özellik</span><span class="sxs-lookup"><span data-stu-id="6c993-119">Property</span></span>|<span data-ttu-id="6c993-120">Değiştir</span><span class="sxs-lookup"><span data-stu-id="6c993-120">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="6c993-121">**Çok satırlı**</span><span class="sxs-lookup"><span data-stu-id="6c993-121">**Multiline**</span></span>|`true`|
    |<span data-ttu-id="6c993-122">**Dock**</span><span class="sxs-lookup"><span data-stu-id="6c993-122">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|
    |<span data-ttu-id="6c993-123">**Çubuklarını**</span><span class="sxs-lookup"><span data-stu-id="6c993-123">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |<span data-ttu-id="6c993-124">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="6c993-124">**ReadOnly**</span></span>|`true`|

6. <span data-ttu-id="6c993-125">**Kod düzenleyicisinde**, içinde `stringsValue` `SerializationDemoControl`adlı bir dize dizisi alanı bildirin.</span><span class="sxs-lookup"><span data-stu-id="6c993-125">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. <span data-ttu-id="6c993-126">Üzerinde özelliğini tanımlayın. `SerializationDemoControl` `Strings`</span><span class="sxs-lookup"><span data-stu-id="6c993-126">Define the `Strings` property on the `SerializationDemoControl`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="6c993-127"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Değer, koleksiyonun serileştirmesini etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c993-127">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. <span data-ttu-id="6c993-128">Projeyi derlemek için **F5** tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6c993-128">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

9. <span data-ttu-id="6c993-129">**UserControl test kapsayıcısının**içinde <xref:System.Windows.Forms.PropertyGrid> **dizeler** özelliğini bulun.</span><span class="sxs-lookup"><span data-stu-id="6c993-129">Find the **Strings** property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="6c993-130">**Dizeler** özelliğini seçin, sonra **dize koleksiyonu düzenleyicisini**açmak için![üç nokta (Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi) düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6c993-130">Select the **Strings** property, then select the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

10. <span data-ttu-id="6c993-131">**Dize koleksiyonu düzenleyicisine**birkaç dize girin.</span><span class="sxs-lookup"><span data-stu-id="6c993-131">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="6c993-132">Her bir dizenin sonundaki **ENTER** tuşuna basarak onları ayırın.</span><span class="sxs-lookup"><span data-stu-id="6c993-132">Separate them by pressing the **Enter** key at the end of each string.</span></span> <span data-ttu-id="6c993-133">Dizeleri girmeyi tamamladığınızda **Tamam** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6c993-133">Click **OK** when you are finished entering strings.</span></span>

   > [!NOTE]
   > <span data-ttu-id="6c993-134">Yazdığınız dizeler içinde <xref:System.Windows.Forms.TextBox> `SerializationDemoControl`görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6c993-134">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

## <a name="serialize-a-collection-property"></a><span data-ttu-id="6c993-135">Koleksiyon özelliğini serileştirme</span><span class="sxs-lookup"><span data-stu-id="6c993-135">Serialize a collection property</span></span>

<span data-ttu-id="6c993-136">Denetiminizin serileştirme davranışını test etmek için, bunu bir forma yerleştirip koleksiyonun içeriğini **koleksiyon Düzenleyicisi**ile değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c993-136">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="6c993-137">Seri hale getirilmiş koleksiyon durumunu, **Windows Form Tasarımcısı** kod yaydığı özel bir tasarımcı dosyasına bakarak görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c993-137">You can see the serialized collection state by looking at a special designer file into which the **Windows Forms Designer** emits code.</span></span>

1. <span data-ttu-id="6c993-138">Çözüme bir Windows uygulama projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6c993-138">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="6c993-139">Projeyi `SerializationDemoControlTest`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="6c993-139">Name the project `SerializationDemoControlTest`.</span></span>

2. <span data-ttu-id="6c993-140">**Araç kutusunda** **SerializationDemoControlLib bileşenleri**adlı sekmeyi bulun.</span><span class="sxs-lookup"><span data-stu-id="6c993-140">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="6c993-141">Bu sekmede, `SerializationDemoControl`' yi bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="6c993-141">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="6c993-142">Daha fazla bilgi için bkz [. İzlenecek yol: Araç kutusunu özel bileşenlerle](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)otomatik olarak doldurma.</span><span class="sxs-lookup"><span data-stu-id="6c993-142">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

3. <span data-ttu-id="6c993-143">Formunuza bir `SerializationDemoControl` koyun.</span><span class="sxs-lookup"><span data-stu-id="6c993-143">Place a `SerializationDemoControl` on your form.</span></span>

4. <span data-ttu-id="6c993-144">`Strings` **Özellikler** penceresinde özelliği bulun.</span><span class="sxs-lookup"><span data-stu-id="6c993-144">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="6c993-145">Özelliği tıklatın, ardından **dize koleksiyonu düzenleyicisini**açmak için![üç nokta (Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi) düğmesine tıklayın. `Strings`</span><span class="sxs-lookup"><span data-stu-id="6c993-145">Click the `Strings` property, then click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

5. <span data-ttu-id="6c993-146">**Dize koleksiyonu düzenleyicisine**birkaç dize yazın.</span><span class="sxs-lookup"><span data-stu-id="6c993-146">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="6c993-147">Her bir dizenin sonunda **ENTER** tuşuna basarak onları ayırın.</span><span class="sxs-lookup"><span data-stu-id="6c993-147">Separate them by pressing **Enter** at the end of each string.</span></span> <span data-ttu-id="6c993-148">Dizeleri girmeyi tamamladığınızda **Tamam** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6c993-148">Click **OK** when you are finished entering strings.</span></span>

> [!NOTE]
> <span data-ttu-id="6c993-149">Yazdığınız dizeler içinde <xref:System.Windows.Forms.TextBox> `SerializationDemoControl`görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6c993-149">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

6. <span data-ttu-id="6c993-150">**Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6c993-150">In **Solution Explorer**, click the **Show All Files** button.</span></span>

7. <span data-ttu-id="6c993-151">**Form1** düğümünü açın.</span><span class="sxs-lookup"><span data-stu-id="6c993-151">Open the **Form1** node.</span></span> <span data-ttu-id="6c993-152">Bunun altında **Form1.Designer.cs** veya **Form1. Designer. vb**adlı bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="6c993-152">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="6c993-153">Bu, **Windows Form Tasarımcısı** formunuzun tasarım zamanı durumunu ve onun alt denetimlerini temsil eden kodu yaydığı dosyadır.</span><span class="sxs-lookup"><span data-stu-id="6c993-153">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="6c993-154">Bu dosyayı **kod düzenleyicisinde**açın.</span><span class="sxs-lookup"><span data-stu-id="6c993-154">Open this file in the **Code Editor**.</span></span>

8. <span data-ttu-id="6c993-155">**Windows Form Tasarımcısı tarafından oluşturulan kod** adlı bölgeyi açın ve **serializationDemoControl1**etiketli bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="6c993-155">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="6c993-156">Bu etiketin altında, denetiminizin serileştirilmiş durumunu temsil eden kod bulunur.</span><span class="sxs-lookup"><span data-stu-id="6c993-156">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="6c993-157">5\. adımda yazdığınız dizeler, `Strings` özelliği için bir atamada görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6c993-157">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="6c993-158">C# Ve Visual Basic aşağıdaki kod örnekleri, "Red", "turuncu" ve "sarı" dizelerini yazdığınız sırada göreceğiniz koda benzer kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c993-158">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. <span data-ttu-id="6c993-159">**Kod düzenleyicisinde**, <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> `Strings` özelliğindeki öğesinin değerini olarak <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6c993-159">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. <span data-ttu-id="6c993-160">Çözümü yeniden derleyin ve 3. ve 4. adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="6c993-160">Rebuild the solution and repeat steps 3 and 4.</span></span>

> [!NOTE]
> <span data-ttu-id="6c993-161">Bu durumda **Windows Form Tasarımcısı** , `Strings` özelliğe atama yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="6c993-161">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6c993-162">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="6c993-162">Next steps</span></span>

<span data-ttu-id="6c993-163">Standart türlerden oluşan bir koleksiyonun nasıl serileştirildiğini öğrendikten sonra, özel denetimlerinizi tasarım zamanı ortamına göre daha ayrıntılı bir şekilde tümleştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="6c993-163">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="6c993-164">Aşağıdaki konularda, özel denetimlerinizin tasarım zamanı tümleştirmesinin nasıl geliştirileceğini anlatmaktadır:</span><span class="sxs-lookup"><span data-stu-id="6c993-164">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>

- <span data-ttu-id="6c993-165">[Tasarım zamanı mimarisi](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6c993-165">[Design-Time Architecture](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span></span>

- [<span data-ttu-id="6c993-166">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c993-166">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)

- <span data-ttu-id="6c993-167">[Tasarımcı serileştirmesine genel bakış](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6c993-167">[Designer Serialization Overview](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>

- [<span data-ttu-id="6c993-168">İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6c993-168">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a><span data-ttu-id="6c993-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c993-169">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [<span data-ttu-id="6c993-170">İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma</span><span class="sxs-lookup"><span data-stu-id="6c993-170">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
