---
title: "Nasıl yapılır: Windows Formlarının Kenarlıklarını Değiştirme"
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
- cpp
helpviewer_keywords: Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94c95d1d938ff8038f1057ac7648082819562b98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="32c2c-102">Nasıl yapılır: Windows Formlarının Kenarlıklarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="32c2c-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="32c2c-103">Windows Forms davranışı ve görünümü belirlerken aralarından seçim yapabileceğiniz çeşitli kenarlık stilleri var.</span><span class="sxs-lookup"><span data-stu-id="32c2c-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="32c2c-104">Değiştirerek <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliği, formu yeniden boyutlandırma davranışını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32c2c-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="32c2c-105">Ayrıca, ayarı <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ne düğmeleri üzerinde görünebilir yanı sıra başlık çubuğunu nasıl görüntüleneceğini etkiler.</span><span class="sxs-lookup"><span data-stu-id="32c2c-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="32c2c-106">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.FormBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="32c2c-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="32c2c-107">Bu görev için kapsamlı destek [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32c2c-107">There is extensive support for this task in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="32c2c-108">Ayrıca bkz. [nasıl yapılır: Tasarımcı kullanarak Windows formlarının kenarlıklarını değiştirme](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="32c2c-108">See also [How to: Change the Borders of Windows Forms Using the Designer](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="32c2c-109">Windows Forms kenarlık stilini programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="32c2c-109">To set the border style of Windows Forms programmatically</span></span>  
  
-   <span data-ttu-id="32c2c-110">Ayarlama <xref:System.Windows.Forms.Form.FormBorderStyle%2A> istediğiniz stil özelliğine.</span><span class="sxs-lookup"><span data-stu-id="32c2c-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="32c2c-111">Aşağıdaki kod örneğinde form kenarlık stilini ayarlar `DlgBx1` için <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span><span class="sxs-lookup"><span data-stu-id="32c2c-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
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
  
     <span data-ttu-id="32c2c-112">Ayrıca bkz. [nasıl yapılır: tasarım zamanında iletişim kutuları oluşturma](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="32c2c-112">Also see [How to: Create Dialog Boxes at Design Time](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).</span></span>  
  
     <span data-ttu-id="32c2c-113">Ayrıca, isteğe bağlı sağlayan form için kenarlık stili seçmiş olduğunuz varsa **simge durumuna küçült** ve **Ekranı Kapla** düğmeleri, ya da işlevsel olması için bu düğmelerin her ikisi de isteyip istemediğinizi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32c2c-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="32c2c-114">Bu düğme, yakından kullanıcı deneyimini kontrol etmek istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="32c2c-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="32c2c-115">**Simge durumuna küçült** ve **Ekranı Kapla** düğmeleri, varsayılan olarak etkinleştirilir ve bunların işlevi aracılığıyla yönetilebilir **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="32c2c-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c2c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32c2c-116">See Also</span></span>  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [<span data-ttu-id="32c2c-117">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="32c2c-117">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
