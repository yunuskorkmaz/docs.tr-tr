---
title: "PrintDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20bbfd02c7fe8f5ca89d67e045b0edd4f2db996c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="57483-102">PrintDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="57483-102">PrintDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="57483-103">Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) bir yazıcı seçin, yazdırmak için sayfaları seçin ve Windows tabanlı uygulamalar içindeki yazdırma ilgili diğer ayarları belirlemek için kullanılan önceden yapılandırılmış iletişim kutusunu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="57483-103">The Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="57483-104">Yazıcı ve kendi iletişim kutusu yapılandırma yerine yazdırma ilgili ayarlar seçimi için basit bir çözüm kullanın.</span><span class="sxs-lookup"><span data-stu-id="57483-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="57483-105">Kullanıcılar kendi belgelerini birçok bölümlerini yazdırmak etkinleştirebilirsiniz: tüm yazdırma, seçili sayfa aralığını yazdırmak veya bir seçim yazdırma.</span><span class="sxs-lookup"><span data-stu-id="57483-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="57483-106">Standart Windows iletişim kutularında bağlı olarak, temel işlevleri kullanıcılara hemen alışkın olduğu uygulamalar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="57483-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="57483-107"><xref:System.Windows.Forms.PrintDialog> Bileşen devraldığı <xref:System.Windows.Forms.CommonDialog> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="57483-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-component"></a><span data-ttu-id="57483-108">Bileşeni ile çalışma</span><span class="sxs-lookup"><span data-stu-id="57483-108">Working with the Component</span></span>  
 <span data-ttu-id="57483-109">Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="57483-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="57483-110">Bu bileşen ya da tek bir yazdırma işi ile ilgili özellikleri vardır (<xref:System.Drawing.Printing.PrintDocument> sınıfı) veya ayrı bir yazıcı ayarları (<xref:System.Drawing.Printing.PrinterSettings> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="57483-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="57483-111">Bunlardan, buna karşılık, birden çok yazıcı tarafından paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="57483-111">Either of these, in turn, may be shared by multiple printers.</span></span>  
  
 <span data-ttu-id="57483-112">Bir form için eklendiğinde <xref:System.Windows.Forms.PrintDialog> Tepsisi Windows Forms Tasarımcısı'nın altındaki Bileşen görünür.</span><span class="sxs-lookup"><span data-stu-id="57483-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57483-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57483-113">See Also</span></span>  
 <xref:System.Windows.Forms.PrintDialog>  
 [<span data-ttu-id="57483-114">PrintDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="57483-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
