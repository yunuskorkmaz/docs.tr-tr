---
title: 'Nasıl yapılır: Windows Formlarının Kenarlıklarını Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: e04234b4f2f18738567c3f9846d8ae0c94780fcb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615917"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="b8ea5-102">Nasıl yapılır: Windows Formlarının Kenarlıklarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="b8ea5-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="b8ea5-103">Görünümünü ve davranışını Windows formlarınızın belirlerken, aralarından seçim yapabileceğiniz çeşitli kenarlık stillerini var.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="b8ea5-104">Değiştirerek <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliği, formu yeniden boyutlandırma davranışını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="b8ea5-105">Ayrıca, ayarı <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ne düğme üzerinde görünebilir yanı sıra başlık çubuğunun nasıl görüntüleneceğini etkiler.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="b8ea5-106">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.FormBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="b8ea5-107">Visual Studio'da bu görevi için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-107">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="b8ea5-108">Ayrıca bkz: [nasıl yapılır: Tasarımcı kullanarak Windows formlarının kenarlıklarını değiştirme](https://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b8ea5-108">See also [How to: Change the Borders of Windows Forms Using the Designer](https://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="b8ea5-109">Windows Forms kenarlık stilini program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b8ea5-109">To set the border style of Windows Forms programmatically</span></span>  
  
-   <span data-ttu-id="b8ea5-110">Ayarlama <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliğini istediğiniz stili.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="b8ea5-111">Aşağıdaki kod örneği form kenarlık stilini ayarlar `DlgBx1` için <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     <span data-ttu-id="b8ea5-112">Ayrıca bkz: [nasıl yapılır: tasarım zamanında iletişim kutuları oluşturma](https://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b8ea5-112">Also see [How to: Create Dialog Boxes at Design Time](https://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).</span></span>  
  
     <span data-ttu-id="b8ea5-113">Ayrıca, isteğe bağlı sağlayan form için bir kenarlık stili seçtiniz, **simge durumuna küçült** ve **Ekranı Kapla** düğmeleri, ya da işlevsel olması için bu düğmeleri isteyip istemediğinizi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="b8ea5-114">Bu düğmeler, kullanıcı deneyimini yakından denetlemek istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="b8ea5-115">**Simge durumuna küçült** ve **Ekranı Kapla** düğmeler, varsayılan olarak etkinleştirilir ve işlevleri aracılığıyla yönetilebilir **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ea5-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8ea5-116">See Also</span></span>  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [<span data-ttu-id="b8ea5-117">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="b8ea5-117">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
