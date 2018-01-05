---
title: "OpenFileDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3e5dc6630d9bc7a2090a28daabbf08eeed59005
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="a133f-102">OpenFileDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a133f-102">OpenFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="a133f-103">Windows Forms <xref:System.Windows.Forms.OpenFileDialog> bir önceden yapılandırılmış iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="a133f-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="a133f-104">Aynı olduğundan **açık dosya** Windows işletim sistemi tarafından kullanıma sunulan iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="a133f-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="a133f-105">Öğesinden devralınan <xref:System.Windows.Forms.CommonDialog> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a133f-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="using-this-component"></a><span data-ttu-id="a133f-106">Bu bileşeni kullanma</span><span class="sxs-lookup"><span data-stu-id="a133f-106">Using this Component</span></span>  
 <span data-ttu-id="a133f-107">Bu bileşen, Windows tabanlı bir uygulama içinde kendi iletişim kutusu yapılandırma yerine dosya seçimi için basit bir çözüm kullanın.</span><span class="sxs-lookup"><span data-stu-id="a133f-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="a133f-108">Standart Windows iletişim kutularında bağlı olarak, temel işlevleri kullanıcılara hemen alışkın olduğu uygulamalar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a133f-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="a133f-109">Ancak, aklınızda bulundurun olduğunda kullanarak <xref:System.Windows.Forms.OpenFileDialog> bileşeni, kendi dosya açılırken mantığı yazma gerekir.</span><span class="sxs-lookup"><span data-stu-id="a133f-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>  
  
 <span data-ttu-id="a133f-110">Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="a133f-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="a133f-111">Kullanıcılar ile açılması için çoklu seçim dosyalarını etkinleştirebilir <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a133f-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="a133f-112">Ayrıca, kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> özelliği salt okunur onay kutusu iletişim kutusunda görünüp görünmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="a133f-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="a133f-113"><xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Özelliği, salt okunur onay kutusunun seçili olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a133f-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="a133f-114">Son olarak, <xref:System.Windows.Forms.FileDialog.Filter%2A> özelliği ayarlar iletişim kutusundaki "Dosya türü" görünür seçimleri belirleyen geçerli dosya adı filtre dizesi,.</span><span class="sxs-lookup"><span data-stu-id="a133f-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>  
  
 <span data-ttu-id="a133f-115">Bir form için eklendiğinde <xref:System.Windows.Forms.OpenFileDialog> Tepsisi Windows Forms Tasarımcısı'nın altındaki Bileşen görünür.</span><span class="sxs-lookup"><span data-stu-id="a133f-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a133f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a133f-116">See Also</span></span>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [<span data-ttu-id="a133f-117">OpenFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="a133f-117">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
