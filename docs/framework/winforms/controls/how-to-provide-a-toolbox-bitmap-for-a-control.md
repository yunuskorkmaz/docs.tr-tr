---
title: 'Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: aa32850b9bcd1a15a93bd6c80b2278278d12c417
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746551"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="e933b-102">Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama</span><span class="sxs-lookup"><span data-stu-id="e933b-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="e933b-103">Denetiminiz için özel bir simge görünür olmasını istiyorsanız **araç kutusu**, belirli bir görüntü kullanarak belirtebilirsiniz <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e933b-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="e933b-104">Bu sınıf, bir *özniteliği*, diğer sınıflara iliştirebilirsiniz sınıfı özel bir tür.</span><span class="sxs-lookup"><span data-stu-id="e933b-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="e933b-105">Öznitelikler hakkında daha fazla bilgi için bkz. [öznitelikler genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) Visual Basic veya [öznitelikler (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) C# için.</span><span class="sxs-lookup"><span data-stu-id="e933b-105">For more information about attributes, see [Attributes overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) for Visual Basic or [Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) for C#.</span></span>  
  
 <span data-ttu-id="e933b-106">Kullanarak <xref:System.Drawing.ToolboxBitmapAttribute>, 16 x 16 piksel bit eşlem yolunu ve dosya adını belirten bir dize belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e933b-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="e933b-107">Bu bit eşlem eklendiğinde denetim ardından yanında **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="e933b-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="e933b-108">Ayrıca belirtebileceğiniz bir <xref:System.Type>, bu durumda, türü ile ilişkili bit eşlem yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e933b-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="e933b-109">Her ikisini de belirtirseniz bir <xref:System.Type> ve bir dize denetim tarafından belirtilen tür içeren derlemenin dize parametresi tarafından belirtilen ada sahip bir görüntü kaynağı için arar <xref:System.Type> parametresi.</span><span class="sxs-lookup"><span data-stu-id="e933b-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="e933b-110">Denetiminiz için bir araç kutusu bit eşlemi belirtmek için</span><span class="sxs-lookup"><span data-stu-id="e933b-110">To specify a Toolbox bitmap for your control</span></span>  
  
1.  <span data-ttu-id="e933b-111">Ekleme <xref:System.Drawing.ToolboxBitmapAttribute> denetiminizin önce sınıf bildirimine `Class` visual Basic ve Visual C# sınıf bildiriminin üstüne anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e933b-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2.  <span data-ttu-id="e933b-112">Projeyi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="e933b-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e933b-113">Bit eşlem otomatik olarak oluşturulan denetimleri ve bileşenleri için Araç Kutusu'nda görünmez.</span><span class="sxs-lookup"><span data-stu-id="e933b-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="e933b-114">Bit eşlem görmek için denetimi kullanarak yeniden **araç kutusu öğelerini Seç** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e933b-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="e933b-115">Daha fazla bilgi için [izlenecek yol: otomatik olarak, araç kutusunu özel bileşenlerle doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="e933b-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e933b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e933b-116">See also</span></span>

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [<span data-ttu-id="e933b-117">İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma</span><span class="sxs-lookup"><span data-stu-id="e933b-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="e933b-118">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="e933b-118">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="e933b-119">Öznitelikler genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e933b-119">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="e933b-120">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="e933b-120">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
