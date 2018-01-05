---
title: "Windows Forms'ta Daha Güvenli Yazdırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f36ee150e4dcca74141b644a55451abd4a4fd21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="281b9-102">Windows Forms'ta Daha Güvenli Yazdırma</span><span class="sxs-lookup"><span data-stu-id="281b9-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="281b9-103">Windows Forms uygulamaları sık sık yazdırma yetenekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="281b9-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="281b9-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Kullanan <xref:System.Drawing.Printing.PrintingPermission> yazdırma yeteneklerini erişimi denetleme ve ilişkili sınıfına <xref:System.Drawing.Printing.PrintingPermissionLevel> erişim düzeyini belirtmek için numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="281b9-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="281b9-105">Varsayılan olarak, yazdırma, yerel Intranet ve Internet bölgelerinde varsayılan olarak etkindir; Ancak, erişim düzeyi hem bölgelerinde sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="281b9-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="281b9-106">Uygulamanızı yazdırabilir olup olmadığını, kullanıcı etkileşimi gerektirir veya olamaz yazdırma bağlıdır uygulamaya verilmiş iznini değeri.</span><span class="sxs-lookup"><span data-stu-id="281b9-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="281b9-107">Varsayılan olarak, yerel Intranet bölgesine alır <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> erişim ve Intranet bölgesine alan <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> erişim.</span><span class="sxs-lookup"><span data-stu-id="281b9-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="281b9-108">Aşağıdaki tabloda, her yazdırma izin düzeyinde işlevselliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="281b9-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="281b9-109">PrintingPermissionLevel</span><span class="sxs-lookup"><span data-stu-id="281b9-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="281b9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="281b9-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="281b9-111">Tüm yüklenen yazıcıları tam erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="281b9-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="281b9-112">Program aracılığıyla yazdırma varsayılan yazıcıya ve kısıtlayıcı bir yazdırma iletişim kutusu üzerinden daha güvenli yazdırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="281b9-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="281b9-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>bir alt kümesidir <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span><span class="sxs-lookup"><span data-stu-id="281b9-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="281b9-114">Yalnızca çok sınırlı iletişim kutusundan yazdırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="281b9-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="281b9-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>bir alt kümesidir <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span><span class="sxs-lookup"><span data-stu-id="281b9-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="281b9-116">Yazıcılara erişimi engeller.</span><span class="sxs-lookup"><span data-stu-id="281b9-116">Prevents access to printers.</span></span> <span data-ttu-id="281b9-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>bir alt kümesidir <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span><span class="sxs-lookup"><span data-stu-id="281b9-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="281b9-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="281b9-118">See Also</span></span>  
 [<span data-ttu-id="281b9-119">Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="281b9-119">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [<span data-ttu-id="281b9-120">Windows Forms'ta Ek Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="281b9-120">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [<span data-ttu-id="281b9-121">Windows Forms'ta Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="281b9-121">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [<span data-ttu-id="281b9-122">Windows Forms Güvenliği</span><span class="sxs-lookup"><span data-stu-id="281b9-122">Windows Forms Security</span></span>](../../../docs/framework/winforms/windows-forms-security.md)
