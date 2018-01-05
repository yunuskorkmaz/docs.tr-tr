---
title: "FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26d2b6294a503edd25b499da2ab67739cdf87174
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="2e080-102">FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2e080-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="2e080-103">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> gözatma ve klasörleri seçmek için kullanılan bir modal iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="2e080-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="2e080-104">Yeni klasörler de oluşturulabilir içinden <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="2e080-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e080-105">Dosyaları, klasörleri, yerine seçmek için kullanın [OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md) bileşeni.</span><span class="sxs-lookup"><span data-stu-id="2e080-105">To select files, instead of folders, use the [OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md) component.</span></span>  
  
 <span data-ttu-id="2e080-106"><xref:System.Windows.Forms.FolderBrowserDialog> Bileşen çalıştırma kullanarak görüntülenir <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2e080-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="2e080-107">Ayarlama <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> en üst klasör ve iletişim kutusunu ağaç görünümü içinde görünür alt klasörleri belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="2e080-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="2e080-108">İletişim kutusunda gösterilen sonra kullanabileceğiniz <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> seçilmedi klasörünün yolunu almak için özellik.</span><span class="sxs-lookup"><span data-stu-id="2e080-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>  
  
 <span data-ttu-id="2e080-109">Bir form için eklendiğinde <xref:System.Windows.Forms.FolderBrowserDialog> Tepsisi Windows Forms Tasarımcısı'nın altındaki Bileşen görünür.</span><span class="sxs-lookup"><span data-stu-id="2e080-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e080-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e080-110">See Also</span></span>  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [<span data-ttu-id="2e080-111">Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme</span><span class="sxs-lookup"><span data-stu-id="2e080-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)  
 [<span data-ttu-id="2e080-112">FolderBrowserDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="2e080-112">FolderBrowserDialog Component</span></span>](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
