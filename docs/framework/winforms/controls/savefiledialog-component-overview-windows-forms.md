---
title: "SaveFileDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cbdc1cb96234e302458cbeac6d6ae26b63c956e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="d9488-102">SaveFileDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d9488-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="d9488-103">Windows Forms <xref:System.Windows.Forms.SaveFileDialog> bir önceden yapılandırılmış iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="d9488-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="d9488-104">Standart olarak aynı olduğundan **dosyayı Kaydet** Windows tarafından kullanılan iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d9488-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="d9488-105">Öğesinden devralınan <xref:System.Windows.Forms.CommonDialog> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d9488-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="d9488-106">SaveFileDialog bileşeni ile çalışma</span><span class="sxs-lookup"><span data-stu-id="d9488-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="d9488-107">Basit bir çözüm kendi iletişim kutusu yapılandırma yerine dosyaları kaydetmek kullanıcıların etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9488-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="d9488-108">Standart Windows iletişim kutularında bağlı olan temel oluşturduğunuz uygulamaların kullanıcılarına hemen tanıdık bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="d9488-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="d9488-109">Ancak, aklınızda bulundurun olduğunda kullanarak <xref:System.Windows.Forms.SaveFileDialog> bileşeni, kendi dosya kaydetme mantığı yazma gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9488-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="d9488-110">Kullanabileceğiniz <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d9488-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="d9488-111">Okuma/yazma modu kullanarak bir dosyayı açabilmek için <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d9488-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="d9488-112">Bir form için eklendiğinde <xref:System.Windows.Forms.SaveFileDialog> Tepsisi Windows Forms Tasarımcısı'nın altındaki Bileşen görünür.</span><span class="sxs-lookup"><span data-stu-id="d9488-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9488-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9488-113">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="d9488-114">SaveFileDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="d9488-114">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
