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
ms.openlocfilehash: 1f1412f03f912c0142b08d5ad8581e421252cfb3
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882355"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="6c4db-102">İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi</span><span class="sxs-lookup"><span data-stu-id="6c4db-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>

<span data-ttu-id="6c4db-103">Özel kontrollerinizi, bazen bir koleksiyon özelliği olarak açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6c4db-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="6c4db-104">Bu izlenecek yolda nasıl kullanılacağını gösterir <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> koleksiyonu tasarım zamanında nasıl serileştirildiği denetlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="6c4db-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="6c4db-105">Uygulama <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> , koleksiyon özelliği için değer özelliği serileştirilecek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c4db-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>

<span data-ttu-id="6c4db-106">Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="6c4db-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6c4db-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="6c4db-107">Prerequisites</span></span>

<span data-ttu-id="6c4db-108">Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="6c4db-108">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-a-control-with-a-serializable-collection"></a><span data-ttu-id="6c4db-109">Bir denetimi ile seri hale getirilebilir bir koleksiyon oluşturma</span><span class="sxs-lookup"><span data-stu-id="6c4db-109">Create a control with a serializable collection</span></span>

<span data-ttu-id="6c4db-110">İlk adım, bir özellik olarak seri hale getirilebilir bir koleksiyon içeren bir denetim oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="6c4db-110">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="6c4db-111">Bu koleksiyonu kullanarak içeriği düzenleyebilir **Koleksiyonu Düzenleyicisi**, gelen erişebileceğiniz **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="6c4db-111">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>

1. <span data-ttu-id="6c4db-112">Visual Studio'da adlı bir Windows Denetim Kitaplığı projesi oluşturun `SerializationDemoControlLib`.</span><span class="sxs-lookup"><span data-stu-id="6c4db-112">In Visual Studio, create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="6c4db-113">Daha fazla bilgi için [Windows Denetim Kitaplığı şablonu](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6c4db-113">For more information, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>

2. <span data-ttu-id="6c4db-114">Yeniden adlandırma `UserControl1` için `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="6c4db-114">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="6c4db-115">Daha fazla bilgi için [bir kod sembol yeniden düzenlemeyi yeniden adlandırma](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="6c4db-115">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

3. <span data-ttu-id="6c4db-116">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> özelliğini `10`.</span><span class="sxs-lookup"><span data-stu-id="6c4db-116">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>

4. <span data-ttu-id="6c4db-117">Bir yerde bir <xref:System.Windows.Forms.TextBox> denetim `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="6c4db-117">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>

5. <span data-ttu-id="6c4db-118">Seçin <xref:System.Windows.Forms.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="6c4db-118">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="6c4db-119">İçinde **özellikleri** penceresinde, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6c4db-119">In the **Properties** window, set the following properties.</span></span>

    |<span data-ttu-id="6c4db-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="6c4db-120">Property</span></span>|<span data-ttu-id="6c4db-121">Değiştirin</span><span class="sxs-lookup"><span data-stu-id="6c4db-121">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="6c4db-122">**Çok satırlı**</span><span class="sxs-lookup"><span data-stu-id="6c4db-122">**Multiline**</span></span>|`true`|
    |<span data-ttu-id="6c4db-123">**Dock**</span><span class="sxs-lookup"><span data-stu-id="6c4db-123">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|
    |<span data-ttu-id="6c4db-124">**Kaydırma çubukları**</span><span class="sxs-lookup"><span data-stu-id="6c4db-124">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |<span data-ttu-id="6c4db-125">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="6c4db-125">**ReadOnly**</span></span>|`true`|

6. <span data-ttu-id="6c4db-126">İçinde **Kod Düzenleyicisi**, adında bir dize dizisi alan bildirin `stringsValue` içinde `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="6c4db-126">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. <span data-ttu-id="6c4db-127">Tanımlama `Strings` özellikte `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="6c4db-127">Define the `Strings` property on the `SerializationDemoControl`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="6c4db-128"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Değer koleksiyonu etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c4db-128">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. <span data-ttu-id="6c4db-129">Tuşuna **F5** projeyi oluşturun ve denetim Çalıştır **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="6c4db-129">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

9. <span data-ttu-id="6c4db-130">Bulma `Strings` özelliğinde <xref:System.Windows.Forms.PropertyGrid> , **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="6c4db-130">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="6c4db-131">Tıklayın `Strings` özelliği, sonra üç nokta simgesine tıklayın (![Visual Studio Özellikler penceresinde üç nokta düğmesini (…)](./media/visual-studio-ellipsis-button.png)) açmak için düğmeyi **Dize Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="6c4db-131">Click the `Strings` property, then click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

10. <span data-ttu-id="6c4db-132">Birkaç dizeleri girin **Dize Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="6c4db-132">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="6c4db-133">Tuşlarına basarak ayırarak **Enter** her bir dizenin sonunda anahtar.</span><span class="sxs-lookup"><span data-stu-id="6c4db-133">Separate them by pressing the **Enter** key at the end of each string.</span></span> <span data-ttu-id="6c4db-134">Tıklayın **Tamam** dizeleri girmeyi tamamladığınızda.</span><span class="sxs-lookup"><span data-stu-id="6c4db-134">Click **OK** when you are finished entering strings.</span></span>

   > [!NOTE]
   > <span data-ttu-id="6c4db-135">Yazdığınız dizeleri görünür <xref:System.Windows.Forms.TextBox> , `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="6c4db-135">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

## <a name="serializing-a-collection-property"></a><span data-ttu-id="6c4db-136">Bir koleksiyon özelliği seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="6c4db-136">Serializing a Collection Property</span></span>

<span data-ttu-id="6c4db-137">Serileştirme davranışını test için bir form üzerinde yerleştirmek ve koleksiyonuyla içeriğini değiştirme **Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="6c4db-137">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="6c4db-138">Seri hale getirilmiş toplama durumu, özel bir tasarımcı dosyasına bakarak gördüğünüz **Windows Form Tasarımcısı** kod yayar.</span><span class="sxs-lookup"><span data-stu-id="6c4db-138">You can see the serialized collection state by looking at a special designer file into which the **Windows Forms Designer** emits code.</span></span>

### <a name="to-serialize-a-collection"></a><span data-ttu-id="6c4db-139">Bir koleksiyonu sıralamak için</span><span class="sxs-lookup"><span data-stu-id="6c4db-139">To serialize a collection</span></span>

1. <span data-ttu-id="6c4db-140">Bir Windows uygulaması projesi çözüme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6c4db-140">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="6c4db-141">Projeyi adlandırın `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="6c4db-141">Name the project `SerializationDemoControlTest`.</span></span>

2. <span data-ttu-id="6c4db-142">İçinde **araç kutusu**, adlı sekmeyi bulun **SerializationDemoControlLib bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="6c4db-142">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="6c4db-143">Bu sekmede bulursunuz `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="6c4db-143">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="6c4db-144">Daha fazla bilgi için [izlenecek yol: Otomatik olarak araç kutusunu özel bileşenlerle doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="6c4db-144">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

3. <span data-ttu-id="6c4db-145">Bir yerde bir `SerializationDemoControl` formunuzdaki.</span><span class="sxs-lookup"><span data-stu-id="6c4db-145">Place a `SerializationDemoControl` on your form.</span></span>

4. <span data-ttu-id="6c4db-146">Bulma `Strings` özelliğinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="6c4db-146">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="6c4db-147">Tıklayın `Strings` özelliği, sonra üç nokta simgesine tıklayın (![Visual Studio Özellikler penceresinde üç nokta düğmesini (…)](./media/visual-studio-ellipsis-button.png)) açmak için düğmeyi **Dize Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="6c4db-147">Click the `Strings` property, then click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

5. <span data-ttu-id="6c4db-148">Birkaç dizelerde yazın **Dize Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="6c4db-148">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="6c4db-149">Bunları, her bir dizenin sonunda ENTER tuşuna basarak ayırın.</span><span class="sxs-lookup"><span data-stu-id="6c4db-149">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="6c4db-150">Tıklayın **Tamam** dizeleri girmeyi tamamladığınızda.</span><span class="sxs-lookup"><span data-stu-id="6c4db-150">Click **OK** when you are finished entering strings.</span></span>

> [!NOTE]
> <span data-ttu-id="6c4db-151">Yazdığınız dizeleri görünür <xref:System.Windows.Forms.TextBox> , `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="6c4db-151">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

1. <span data-ttu-id="6c4db-152">İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6c4db-152">In **Solution Explorer**, click the **Show All Files** button.</span></span>

2. <span data-ttu-id="6c4db-153">Açık **Form1** düğümü.</span><span class="sxs-lookup"><span data-stu-id="6c4db-153">Open the **Form1** node.</span></span> <span data-ttu-id="6c4db-154">Adlı bir dosya olduğu beneath **Form1.Designer.cs** veya **Form1.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="6c4db-154">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="6c4db-155">Bu dosyaya, **Windows Form Tasarımcısı** formunuza ve onun alt denetimleri tasarım zamanı durumunu temsil eden kod yayar.</span><span class="sxs-lookup"><span data-stu-id="6c4db-155">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="6c4db-156">Bu dosyayı açmak **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="6c4db-156">Open this file in the **Code Editor**.</span></span>

3. <span data-ttu-id="6c4db-157">Bölge adında açın **Windows Form Designer üretilen kod** ve etiketlenmiş bölümü bulun **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="6c4db-157">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="6c4db-158">Bu etiketi altında denetiminizin serileştirilmiş durumu temsil eden kodudur.</span><span class="sxs-lookup"><span data-stu-id="6c4db-158">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="6c4db-159">5. adımda yazdığınız dizeleri atama görünen `Strings` özelliği.</span><span class="sxs-lookup"><span data-stu-id="6c4db-159">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="6c4db-160">C# ve Visual Basic'te, aşağıdaki kod örnekleri Göster kod benzer şekilde, hangi dizeleri "red", "turuncu" ve "Sarı" yazılı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="6c4db-160">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

4. <span data-ttu-id="6c4db-161">İçinde **Kod Düzenleyicisi**, değiştirin <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> üzerinde `Strings` özelliğini <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="6c4db-161">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

5. <span data-ttu-id="6c4db-162">3 ve 4 yineleme adımları ve çözümü yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6c4db-162">Rebuild the solution and repeat steps 3 and 4.</span></span>

> [!NOTE]
> <span data-ttu-id="6c4db-163">Bu durumda, **Windows Form Tasarımcısı** atama bulunamadı yayan `Strings` özelliği.</span><span class="sxs-lookup"><span data-stu-id="6c4db-163">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6c4db-164">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="6c4db-164">Next Steps</span></span>

<span data-ttu-id="6c4db-165">Standart türlerin koleksiyonunu serileştirmek nasıl öğrendikten sonra özel kontrollerinizi tasarım zamanı ortamına daha derin tümleştirme göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="6c4db-165">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="6c4db-166">Aşağıdaki konular, özel kontrollerinizi, tasarım zamanı tümleştirmeyi geliştirmek nasıl açıklar:</span><span class="sxs-lookup"><span data-stu-id="6c4db-166">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>

- <span data-ttu-id="6c4db-167">[Tasarım zamanı mimarisi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6c4db-167">[Design-Time Architecture](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span></span>

- [<span data-ttu-id="6c4db-168">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c4db-168">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)

- <span data-ttu-id="6c4db-169">[Tasarımcı serileştirmeye genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6c4db-169">[Designer Serialization Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>

- [<span data-ttu-id="6c4db-170">İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6c4db-170">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a><span data-ttu-id="6c4db-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c4db-171">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- <span data-ttu-id="6c4db-172">[Tasarımcı serileştirmeye genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6c4db-172">[Designer Serialization Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>
- <span data-ttu-id="6c4db-173">[Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6c4db-173">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
- [<span data-ttu-id="6c4db-174">İzlenecek yol: Otomatik olarak araç kutusunu özel bileşenlerle doldurma</span><span class="sxs-lookup"><span data-stu-id="6c4db-174">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
