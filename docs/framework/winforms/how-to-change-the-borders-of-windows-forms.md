---
title: 'Nasıl yapılır: Windows Formlarının Kenarlıklarını Değiştirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 936d9d67454a272e79990f2e1b432391ecdc26a5
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="035ab-102">Nasıl yapılır: Windows Formlarının Kenarlıklarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="035ab-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="035ab-103">Windows Forms davranışı ve görünümü belirlerken aralarından seçim yapabileceğiniz çeşitli kenarlık stilleri var.</span><span class="sxs-lookup"><span data-stu-id="035ab-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="035ab-104">Değiştirerek <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliği, formu yeniden boyutlandırma davranışını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="035ab-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="035ab-105">Ayrıca, ayarı <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ne düğmeleri üzerinde görünebilir yanı sıra başlık çubuğunu nasıl görüntüleneceğini etkiler.</span><span class="sxs-lookup"><span data-stu-id="035ab-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="035ab-106">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.FormBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="035ab-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="035ab-107">Visual Studio'da bu görev için kapsamlı destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="035ab-107">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="035ab-108">Ayrıca bkz. [nasıl yapılır: Tasarımcı kullanarak Windows formlarının kenarlıklarını değiştirme](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="035ab-108">See also [How to: Change the Borders of Windows Forms Using the Designer](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="035ab-109">Windows Forms kenarlık stilini programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="035ab-109">To set the border style of Windows Forms programmatically</span></span>  
  
-   <span data-ttu-id="035ab-110">Ayarlama <xref:System.Windows.Forms.Form.FormBorderStyle%2A> istediğiniz stil özelliğine.</span><span class="sxs-lookup"><span data-stu-id="035ab-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="035ab-111">Aşağıdaki kod örneğinde form kenarlık stilini ayarlar `DlgBx1` için <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span><span class="sxs-lookup"><span data-stu-id="035ab-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
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
  
     <span data-ttu-id="035ab-112">Ayrıca bkz. [nasıl yapılır: tasarım zamanında iletişim kutuları oluşturma](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="035ab-112">Also see [How to: Create Dialog Boxes at Design Time](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).</span></span>  
  
     <span data-ttu-id="035ab-113">Ayrıca, isteğe bağlı sağlayan form için kenarlık stili seçmiş olduğunuz varsa **simge durumuna küçült** ve **Ekranı Kapla** düğmeleri, ya da işlevsel olması için bu düğmelerin her ikisi de isteyip istemediğinizi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="035ab-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="035ab-114">Bu düğme, yakından kullanıcı deneyimini kontrol etmek istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="035ab-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="035ab-115">**Simge durumuna küçült** ve **Ekranı Kapla** düğmeleri, varsayılan olarak etkinleştirilir ve bunların işlevi aracılığıyla yönetilebilir **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="035ab-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035ab-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="035ab-116">See Also</span></span>  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [<span data-ttu-id="035ab-117">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="035ab-117">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
