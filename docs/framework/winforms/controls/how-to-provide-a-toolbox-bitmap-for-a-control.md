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
ms.openlocfilehash: 428af7e4396fde8ac29046d73adda95dbe2182f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910478"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="d1250-102">Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama</span><span class="sxs-lookup"><span data-stu-id="d1250-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="d1250-103">Denetiminizin **araç kutusunda**görünmesi için özel bir simgenin olması isterseniz, belirli bir görüntüyü kullanarak <xref:System.Drawing.ToolboxBitmapAttribute>belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1250-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="d1250-104">Bu sınıf, diğer sınıflara iliştirebilmeniz için özel bir sınıf türü olan bir *özniteliktir*.</span><span class="sxs-lookup"><span data-stu-id="d1250-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="d1250-105">Öznitelikler hakkında daha fazla bilgi için bkz C#. Visual Basic veya [öznitelikleri (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) için [özniteliklere genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) .</span><span class="sxs-lookup"><span data-stu-id="d1250-105">For more information about attributes, see [Attributes overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) for Visual Basic or [Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) for C#.</span></span>  
  
 <span data-ttu-id="d1250-106"><xref:System.Drawing.ToolboxBitmapAttribute>Kullanarak, 16 x 16 piksellik bit eşlem için yolu ve dosya adını belirten bir dize belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1250-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="d1250-107">Bu bit eşlem daha sonra **araç kutusuna**eklendiğinde denetiminizin yanında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d1250-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="d1250-108">Ayrıca, bir <xref:System.Type>de belirtebilirsiniz, bu durumda, bu tür ile ilişkili bit eşlem yüklenir.</span><span class="sxs-lookup"><span data-stu-id="d1250-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="d1250-109">Hem hem de <xref:System.Type> bir dize belirtirseniz, denetim, <xref:System.Type> parametresi tarafından belirtilen türü içeren derlemede dize parametresi tarafından belirtilen ada sahip bir görüntü kaynağı arar.</span><span class="sxs-lookup"><span data-stu-id="d1250-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="d1250-110">Denetiminiz için araç kutusu bit eşlemi belirtmek için</span><span class="sxs-lookup"><span data-stu-id="d1250-110">To specify a Toolbox bitmap for your control</span></span>  
  
1. <span data-ttu-id="d1250-111">Visual Basic için `Class` anahtar sözcüğünden önce ve Visual C#için sınıf bildiriminin üstüne, denetiminizin sınıf bildirimine ekleyin. <xref:System.Drawing.ToolboxBitmapAttribute></span><span class="sxs-lookup"><span data-stu-id="d1250-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>  
  
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
  
2. <span data-ttu-id="d1250-112">Projeyi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="d1250-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d1250-113">Bit eşlem, otomatik olarak oluşturulan denetimler ve bileşenler için araç kutusunda görünmez.</span><span class="sxs-lookup"><span data-stu-id="d1250-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="d1250-114">Bit eşlemi görmek için **araç kutusu öğelerini Seç** iletişim kutusunu kullanarak denetimi yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d1250-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="d1250-115">Daha fazla bilgi için bkz [. İzlenecek yol: Araç kutusunu özel bileşenlerle](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)otomatik olarak doldurma.</span><span class="sxs-lookup"><span data-stu-id="d1250-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1250-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1250-116">See also</span></span>

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [<span data-ttu-id="d1250-117">İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma</span><span class="sxs-lookup"><span data-stu-id="d1250-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="d1250-118">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="d1250-118">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="d1250-119">Özniteliklere genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1250-119">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="d1250-120">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="d1250-120">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
