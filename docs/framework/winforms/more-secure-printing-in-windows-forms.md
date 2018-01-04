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
# <a name="more-secure-printing-in-windows-forms"></a>Windows Forms'ta Daha Güvenli Yazdırma
Windows Forms uygulamaları sık sık yazdırma yetenekleri içerir. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Kullanan <xref:System.Drawing.Printing.PrintingPermission> yazdırma yeteneklerini erişimi denetleme ve ilişkili sınıfına <xref:System.Drawing.Printing.PrintingPermissionLevel> erişim düzeyini belirtmek için numaralandırma değeri. Varsayılan olarak, yazdırma, yerel Intranet ve Internet bölgelerinde varsayılan olarak etkindir; Ancak, erişim düzeyi hem bölgelerinde sınırlıdır. Uygulamanızı yazdırabilir olup olmadığını, kullanıcı etkileşimi gerektirir veya olamaz yazdırma bağlıdır uygulamaya verilmiş iznini değeri. Varsayılan olarak, yerel Intranet bölgesine alır <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> erişim ve Intranet bölgesine alan <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> erişim.  
  
 Aşağıdaki tabloda, her yazdırma izin düzeyinde işlevselliği gösterilmektedir.  
  
|PrintingPermissionLevel|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Tüm yüklenen yazıcıları tam erişim sağlar.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Program aracılığıyla yazdırma varsayılan yazıcıya ve kısıtlayıcı bir yazdırma iletişim kutusu üzerinden daha güvenli yazdırma sağlar. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>bir alt kümesidir <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Yalnızca çok sınırlı iletişim kutusundan yazdırma sağlar. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>bir alt kümesidir <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Yazıcılara erişimi engeller. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>bir alt kümesidir <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [Windows Forms'ta Ek Güvenlik Konuları](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Windows Forms'ta Güvenliğe Genel Bakış](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Windows Forms Güvenliği](../../../docs/framework/winforms/windows-forms-security.md)
