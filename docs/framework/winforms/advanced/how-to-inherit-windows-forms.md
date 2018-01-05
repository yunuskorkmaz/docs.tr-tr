---
title: "Nasıl yapılır: Windows Formlarını Devralma"
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
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f190fb101a3ff666d194d854c9ce152657ebf85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="cfc8b-102">Nasıl yapılır: Windows Formlarını Devralma</span><span class="sxs-lookup"><span data-stu-id="cfc8b-102">How to: Inherit Windows Forms</span></span>
<span data-ttu-id="cfc8b-103">Temel formlardan devralarak yeni Windows Forms oluşturma en iyi çabalarınız bunu gerektiren her zaman bir form tamamen yeniden sürecinde geçmeden çoğaltmak için kullanışlı bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="cfc8b-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>  
  
 <span data-ttu-id="cfc8b-104">Tasarım zamanı kullanarak form devralma hakkında daha fazla bilgi için **devralma Seçici** iletişim kutusu ve görsel olarak güvenlik düzeyleri arasında ayrım yapma devralınan denetimleri için bkz: [nasıl yapılır: formları kullanarak devral Devralma Seçici iletişim kutusu](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span><span class="sxs-lookup"><span data-stu-id="cfc8b-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>  
  
 <span data-ttu-id="cfc8b-105">**Not** bir formdan devralmak için dosya veya ad alanı, formu içeren bir yürütülebilir dosya veya DLL'e oluşturulmuş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cfc8b-105">**Note** In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="cfc8b-106">Projeyi oluşturmak için tercih **yapı** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cfc8b-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="cfc8b-107">Ayrıca, ad alanı referansı formun devralma sınıfı eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cfc8b-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span> <span data-ttu-id="cfc8b-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="cfc8b-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cfc8b-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cfc8b-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cfc8b-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="cfc8b-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-inherit-a-form-programmatically"></a><span data-ttu-id="cfc8b-111">Bir form program aracılığıyla devralmak için</span><span class="sxs-lookup"><span data-stu-id="cfc8b-111">To inherit a form programmatically</span></span>  
  
1.  <span data-ttu-id="cfc8b-112">Sınıfınızda, devralınan istediğiniz formu içeren ad alanı için bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cfc8b-112">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>  
  
2.  <span data-ttu-id="cfc8b-113">Sınıf tanımında form devralmak için bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cfc8b-113">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="cfc8b-114">Başvuru noktayla, ardından taban formun adını ve ardından formu içeren ad alanı içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cfc8b-114">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 <span data-ttu-id="cfc8b-115">Forms devralırken her olay hem temel sınıfını hem de devralınan sınıfı tarafından işlenmediğinden oluşabilecek sorunları, iki kez çağrılan olay işleyicileri açısından göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="cfc8b-115">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="cfc8b-116">Bu sorunu önlemek nasıl daha fazla bilgi için bkz: [sorun giderme devralınmış olay işleyicileri Visual Basic'te](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="cfc8b-116">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc8b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cfc8b-117">See Also</span></span>  
 [<span data-ttu-id="cfc8b-118">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="cfc8b-118">Inherits Statement</span></span>](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="cfc8b-119">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="cfc8b-119">Imports Statement (.NET Namespace and Type)</span></span>](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="cfc8b-120">using</span><span class="sxs-lookup"><span data-stu-id="cfc8b-120">using</span></span>](~/docs/csharp/language-reference/keywords/using.md)  
 [<span data-ttu-id="cfc8b-121">Taban Formun Görünüşünü Değiştirmenin Etkileri</span><span class="sxs-lookup"><span data-stu-id="cfc8b-121">Effects of Modifying a Base Form's Appearance</span></span>](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [<span data-ttu-id="cfc8b-122">Windows Forms Görsel Devralma</span><span class="sxs-lookup"><span data-stu-id="cfc8b-122">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
