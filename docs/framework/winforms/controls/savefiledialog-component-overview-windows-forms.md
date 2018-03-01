---
title: "SaveFileDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1505e2bc31afb4f44f0d635b06624528cb16ba15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="f0fc8-102">SaveFileDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f0fc8-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="f0fc8-103">Windows Forms <xref:System.Windows.Forms.SaveFileDialog> bir önceden yapılandırılmış iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="f0fc8-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="f0fc8-104">Standart olarak aynı olduğundan **dosyayı Kaydet** Windows tarafından kullanılan iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="f0fc8-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="f0fc8-105">Öğesinden devralınan <xref:System.Windows.Forms.CommonDialog> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f0fc8-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="f0fc8-106">SaveFileDialog bileşeni ile çalışma</span><span class="sxs-lookup"><span data-stu-id="f0fc8-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="f0fc8-107">Basit bir çözüm kendi iletişim kutusu yapılandırma yerine dosyaları kaydetmek kullanıcıların etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0fc8-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="f0fc8-108">Standart Windows iletişim kutularında bağlı olan temel oluşturduğunuz uygulamaların kullanıcılarına hemen tanıdık bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="f0fc8-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="f0fc8-109">Ancak, aklınızda bulundurun olduğunda kullanarak <xref:System.Windows.Forms.SaveFileDialog> bileşeni, kendi dosya kaydetme mantığı yazma gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0fc8-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="f0fc8-110">Kullanabileceğiniz <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="f0fc8-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="f0fc8-111">Okuma/yazma modu kullanarak bir dosyayı açabilmek için <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f0fc8-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="f0fc8-112">Bir form için eklendiğinde <xref:System.Windows.Forms.SaveFileDialog> Tepsisi Windows Forms Tasarımcısı'nın altındaki Bileşen görünür.</span><span class="sxs-lookup"><span data-stu-id="f0fc8-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0fc8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0fc8-113">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="f0fc8-114">SaveFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="f0fc8-114">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
