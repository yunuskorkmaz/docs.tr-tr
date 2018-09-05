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
ms.openlocfilehash: 54859b3065e8e9bb9680d8b6bf7946b393f73b9f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541483"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="7df25-102">İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi</span><span class="sxs-lookup"><span data-stu-id="7df25-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>
<span data-ttu-id="7df25-103">Özel kontrollerinizi, bazen bir koleksiyon özelliği olarak açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="7df25-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="7df25-104">Bu izlenecek yolda nasıl kullanılacağını gösterir <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> koleksiyonu tasarım zamanında nasıl serileştirildiği denetlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="7df25-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="7df25-105">Uygulama <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> , koleksiyon özelliği için değer özelliği serileştirilecek sağlar.</span><span class="sxs-lookup"><span data-stu-id="7df25-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>  
  
 <span data-ttu-id="7df25-106">Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: seri hale getirme koleksiyonları standart türleri DesignerSerializationVisibilityAttribute ile](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).</span><span class="sxs-lookup"><span data-stu-id="7df25-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7df25-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7df25-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7df25-108">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="7df25-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7df25-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7df25-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7df25-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7df25-110">Prerequisites</span></span>  
 <span data-ttu-id="7df25-111">Bu izlenecek yolu tamamlamak için şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="7df25-111">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="7df25-112">Oluşturma ve Windows Forms application projesi Visual Studio'nun yüklü bilgisayarda çalıştırmak için yeterli izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="7df25-112">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a><span data-ttu-id="7df25-113">Seri hale getirilebilir bir koleksiyon olan bir denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="7df25-113">Creating a Control That Has a Serializable Collection</span></span>  
 <span data-ttu-id="7df25-114">İlk adım, bir özellik olarak seri hale getirilebilir bir koleksiyon içeren bir denetim oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="7df25-114">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="7df25-115">Bu koleksiyonu kullanarak içeriği düzenleyebilir **Koleksiyonu Düzenleyicisi**, gelen erişebileceğiniz **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="7df25-115">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a><span data-ttu-id="7df25-116">Bir denetim ile seri hale getirilebilir bir koleksiyon oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7df25-116">To create a control with a serializable collection</span></span>  
  
1.  <span data-ttu-id="7df25-117">Adlı bir Windows Denetim Kitaplığı projesi oluşturun `SerializationDemoControlLib`.</span><span class="sxs-lookup"><span data-stu-id="7df25-117">Create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="7df25-118">Daha fazla bilgi için [Windows Denetim Kitaplığı şablonu](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="7df25-118">For more information, see [Windows Control Library Template](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="7df25-119">Yeniden adlandırma `UserControl1` için `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="7df25-119">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="7df25-120">Daha fazla bilgi için [nasıl yapılır: yeniden adlandırma tanımlayıcıları](https://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).</span><span class="sxs-lookup"><span data-stu-id="7df25-120">For more information, see [How to: Rename Identifiers](https://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).</span></span>  
  
3.  <span data-ttu-id="7df25-121">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> özelliğini `10`.</span><span class="sxs-lookup"><span data-stu-id="7df25-121">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>  
  
4.  <span data-ttu-id="7df25-122">Bir yerde bir <xref:System.Windows.Forms.TextBox> denetim `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="7df25-122">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>  
  
5.  <span data-ttu-id="7df25-123">Seçin <xref:System.Windows.Forms.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7df25-123">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="7df25-124">İçinde **özellikleri** penceresinde, aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7df25-124">In the **Properties** window, set the following properties.</span></span>  
  
    |<span data-ttu-id="7df25-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="7df25-125">Property</span></span>|<span data-ttu-id="7df25-126">Değiştirin</span><span class="sxs-lookup"><span data-stu-id="7df25-126">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="7df25-127">**Çok satırlı**</span><span class="sxs-lookup"><span data-stu-id="7df25-127">**Multiline**</span></span>|`true`|  
    |<span data-ttu-id="7df25-128">**Dock**</span><span class="sxs-lookup"><span data-stu-id="7df25-128">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |<span data-ttu-id="7df25-129">**Kaydırma çubukları**</span><span class="sxs-lookup"><span data-stu-id="7df25-129">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |<span data-ttu-id="7df25-130">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="7df25-130">**ReadOnly**</span></span>|`true`|  
  
6.  <span data-ttu-id="7df25-131">İçinde **Kod Düzenleyicisi**, adında bir dize dizisi alan bildirin `stringsValue` içinde `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="7df25-131">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  <span data-ttu-id="7df25-132">Tanımlama `Strings` özellikte `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="7df25-132">Define the `Strings` property on the `SerializationDemoControl`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7df25-133"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Değer koleksiyonu etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7df25-133">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  <span data-ttu-id="7df25-134">Projeyi oluşturmak ve denetim çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="7df25-134">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="7df25-135">Bulma `Strings` özelliğinde <xref:System.Windows.Forms.PropertyGrid> , **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="7df25-135">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="7df25-136">Tıklayın `Strings` özelliği, sonra üç nokta simgesine tıklayın (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) açmak için düğmeyi **Dize Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="7df25-136">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="7df25-137">Birkaç dizeleri girin **Dize Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="7df25-137">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="7df25-138">Bunları, her bir dizenin sonunda ENTER tuşuna basarak ayırın.</span><span class="sxs-lookup"><span data-stu-id="7df25-138">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="7df25-139">Tıklayın **Tamam** dizeleri girmeyi tamamladığınızda.</span><span class="sxs-lookup"><span data-stu-id="7df25-139">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7df25-140">Yazdığınız dizeleri görünür <xref:System.Windows.Forms.TextBox> , `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="7df25-140">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
## <a name="serializing-a-collection-property"></a><span data-ttu-id="7df25-141">Bir koleksiyon özelliği seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="7df25-141">Serializing a Collection Property</span></span>  
 <span data-ttu-id="7df25-142">Serileştirme davranışını test için bir form üzerinde yerleştirmek ve koleksiyonuyla içeriğini değiştirme **Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="7df25-142">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="7df25-143">Seri hale getirilmiş toplama durumu, bir özel Tasarımcı dosyasından bakarak gördüğünüz **Windows Form Tasarımcısı** kod yayar.</span><span class="sxs-lookup"><span data-stu-id="7df25-143">You can see the serialized collection state by looking at a special designer file, into which the **Windows Forms Designer** emits code.</span></span>  
  
#### <a name="to-serialize-a-collection"></a><span data-ttu-id="7df25-144">Bir koleksiyonu sıralamak için</span><span class="sxs-lookup"><span data-stu-id="7df25-144">To serialize a collection</span></span>  
  
1.  <span data-ttu-id="7df25-145">Bir Windows uygulaması projesi çözüme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7df25-145">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="7df25-146">Projeyi adlandırın `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="7df25-146">Name the project `SerializationDemoControlTest`.</span></span>  
  
2.  <span data-ttu-id="7df25-147">İçinde **araç kutusu**, adlı sekmeyi bulun **SerializationDemoControlLib bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="7df25-147">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="7df25-148">Bu sekmede bulursunuz `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="7df25-148">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="7df25-149">Daha fazla bilgi için [izlenecek yol: otomatik olarak, araç kutusunu özel bileşenlerle doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="7df25-149">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
3.  <span data-ttu-id="7df25-150">Bir yerde bir `SerializationDemoControl` formunuzdaki.</span><span class="sxs-lookup"><span data-stu-id="7df25-150">Place a `SerializationDemoControl` on your form.</span></span>  
  
4.  <span data-ttu-id="7df25-151">Bulma `Strings` özelliğinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="7df25-151">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="7df25-152">Tıklayın `Strings` özelliği, sonra üç nokta simgesine tıklayın (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) açmak için düğmeyi **Dize Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="7df25-152">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="7df25-153">Birkaç dizelerde yazın **Dize Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="7df25-153">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="7df25-154">Bunları, her bir dizenin sonunda ENTER tuşuna basarak ayırın.</span><span class="sxs-lookup"><span data-stu-id="7df25-154">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="7df25-155">Tıklayın **Tamam** dizeleri girmeyi tamamladığınızda.</span><span class="sxs-lookup"><span data-stu-id="7df25-155">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7df25-156">Yazdığınız dizeleri görünür <xref:System.Windows.Forms.TextBox> , `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="7df25-156">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
1.  <span data-ttu-id="7df25-157">İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7df25-157">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
2.  <span data-ttu-id="7df25-158">Açık **Form1** düğümü.</span><span class="sxs-lookup"><span data-stu-id="7df25-158">Open the **Form1** node.</span></span> <span data-ttu-id="7df25-159">Adlı bir dosya olduğu beneath **Form1.Designer.cs** veya **Form1.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="7df25-159">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="7df25-160">Bu dosyaya, **Windows Form Tasarımcısı** formunuza ve onun alt denetimleri tasarım zamanı durumunu temsil eden kod yayar.</span><span class="sxs-lookup"><span data-stu-id="7df25-160">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="7df25-161">Bu dosyayı açmak **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="7df25-161">Open this file in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="7df25-162">Bölge adında açın **Windows Form Designer üretilen kod** ve etiketlenmiş bölümü bulun **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="7df25-162">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="7df25-163">Bu etiketi altında denetiminizin serileştirilmiş durumu temsil eden kodudur.</span><span class="sxs-lookup"><span data-stu-id="7df25-163">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="7df25-164">5. adımda yazdığınız dizeleri atama görünen `Strings` özelliği.</span><span class="sxs-lookup"><span data-stu-id="7df25-164">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="7df25-165">C# ve Visual Basic'te, aşağıdaki kod örnekleri Göster kod benzer şekilde, hangi dizeleri "red", "turuncu" ve "Sarı" yazılı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="7df25-165">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  <span data-ttu-id="7df25-166">İçinde **Kod Düzenleyicisi**, değiştirin <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> üzerinde `Strings` özelliğini <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="7df25-166">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. <span data-ttu-id="7df25-167">3 ve 4 yineleme adımları ve çözümü yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7df25-167">Rebuild the solution and repeat steps 3 and 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7df25-168">Bu durumda, **Windows Form Tasarımcısı** atama bulunamadı yayan `Strings` özelliği.</span><span class="sxs-lookup"><span data-stu-id="7df25-168">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7df25-169">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="7df25-169">Next Steps</span></span>  
 <span data-ttu-id="7df25-170">Standart türlerin koleksiyonunu serileştirmek nasıl öğrendikten sonra özel kontrollerinizi tasarım zamanı ortamına daha derin tümleştirme göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7df25-170">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="7df25-171">Aşağıdaki konular, özel kontrollerinizi, tasarım zamanı tümleştirmeyi geliştirmek nasıl açıklar:</span><span class="sxs-lookup"><span data-stu-id="7df25-171">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>  
  
-   [<span data-ttu-id="7df25-172">Tasarım zamanı mimarisi</span><span class="sxs-lookup"><span data-stu-id="7df25-172">Design-Time Architecture</span></span>](https://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [<span data-ttu-id="7df25-173">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7df25-173">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [<span data-ttu-id="7df25-174">Tasarımcı serileştirmeye genel bakış</span><span class="sxs-lookup"><span data-stu-id="7df25-174">Designer Serialization Overview</span></span>](https://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [<span data-ttu-id="7df25-175">İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7df25-175">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a><span data-ttu-id="7df25-176">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7df25-176">See Also</span></span>  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [<span data-ttu-id="7df25-177">Tasarımcı serileştirmeye genel bakış</span><span class="sxs-lookup"><span data-stu-id="7df25-177">Designer Serialization Overview</span></span>](https://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [<span data-ttu-id="7df25-178">Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="7df25-178">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [<span data-ttu-id="7df25-179">İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma</span><span class="sxs-lookup"><span data-stu-id="7df25-179">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
