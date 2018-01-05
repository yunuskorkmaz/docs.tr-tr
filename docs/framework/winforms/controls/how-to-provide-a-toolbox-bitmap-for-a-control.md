---
title: "Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama"
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
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 947ac4f8783b388135cf9e8147bb48eda93cfa08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="5a9d1-102">Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama</span><span class="sxs-lookup"><span data-stu-id="5a9d1-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="5a9d1-103">Sahip olmak istiyorsanız denetlemek için özel bir simgesi görünür **araç**, kullanarak belirli bir görüntü belirtebilirsiniz <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="5a9d1-104">Bu sınıf, bir *özniteliği*, özel türde bir sınıfı diğer sınıfların iliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="5a9d1-105">Öznitelikler hakkında daha fazla bilgi için bkz: [NOT ın yapı: Visual Basic'te öznitelikler genel bakış](http://msdn.microsoft.com/en-us/0d0cff64-892d-4f57-83bd-bef388553d4f) için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ve [öznitelikleri](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) için [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a9d1-105">For more information about attributes, see [NOT IN BUILD: Attributes Overview in Visual Basic](http://msdn.microsoft.com/en-us/0d0cff64-892d-4f57-83bd-bef388553d4f) for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] and [Attributes](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) for [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span></span>  
  
 <span data-ttu-id="5a9d1-106">Kullanarak <xref:System.Drawing.ToolboxBitmapAttribute>, 16 x 16 piksel bit eşlem için yolu ve dosya adını belirten bir dize belirtin.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="5a9d1-107">Bu bit eşlemi eklendiğinde, Denetim yanındaki sonra görünür **araç**.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="5a9d1-108">Ayrıca belirtebilirsiniz bir <xref:System.Type>, o türü ile ilişkili bit eşlem; bu durumda yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="5a9d1-109">Her ikisini de belirtirseniz bir <xref:System.Type> ve tarafından belirtilen türünü içeren bütünleştirilmiş dizesi parametresi tarafından belirtilen ada sahip bir görüntü kaynağı için bir dize denetimi arar <xref:System.Type> parametresi.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="5a9d1-110">Denetim için araç kutusu bit eşlemi belirtmek için</span><span class="sxs-lookup"><span data-stu-id="5a9d1-110">To specify a Toolbox bitmap for your control</span></span>  
  
1.  <span data-ttu-id="5a9d1-111">Ekleme <xref:System.Drawing.ToolboxBitmapAttribute> önce denetiminizin sınıfı bildirimine `Class` for anahtar sözcüğü [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]ve için sınıf bildiriminin üstüne [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a9d1-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], and above the class declaration for [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span></span>  
  
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
  
2.  <span data-ttu-id="5a9d1-112">Projeyi yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a9d1-113">Bit eşlem otomatik olarak oluşturulur denetimleri ve bileşenleri için Araç Kutusu'nda görünmez.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="5a9d1-114">Bit eşlem görmek için denetimi kullanarak yeniden **araç kutusu öğelerini Seç** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="5a9d1-115">Daha fazla bilgi için bkz: [izlenecek yol: araç kutusunu özel bileşenlerle'otomatik olarak doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="5a9d1-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a9d1-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a9d1-116">See Also</span></span>  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [<span data-ttu-id="5a9d1-117">İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma</span><span class="sxs-lookup"><span data-stu-id="5a9d1-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="5a9d1-118">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="5a9d1-118">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="5a9d1-119">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a9d1-119">Attributes (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="5a9d1-120">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5a9d1-120">Attributes</span></span>](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
