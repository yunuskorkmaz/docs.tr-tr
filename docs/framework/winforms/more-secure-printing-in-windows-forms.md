---
title: Daha güvenli yazdırma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 6285b76d01660bfa761ea606421f264bdc0c0af5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734884"
---
# <a name="more-secure-printing-in-windows-forms"></a>Windows Forms'ta Daha Güvenli Yazdırma
Windows Forms uygulamalar genellikle yazdırma yeteneklerini içerir. .NET Framework, erişim düzeyini göstermek için yazdırma özelliklerine ve ilişkili <xref:System.Drawing.Printing.PrintingPermissionLevel> numaralandırma değerine erişimi denetlemek için <xref:System.Drawing.Printing.PrintingPermission> sınıfını kullanır. Varsayılan olarak, yazdırma varsayılan olarak yerel Intranet ve Internet bölgelerinde etkindir; Ancak, erişim düzeyi her iki bölgede de kısıtlıdır. Uygulamanızın yazdırabilir, Kullanıcı etkileşimi ister veya yazdıramayacağı, uygulamaya verilen izin değerine bağlıdır. Varsayılan olarak, yerel Intranet bölgesi <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> erişim alır ve Intranet bölgesi <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> erişim alır.  
  
 Aşağıdaki tabloda, her yazdırma izni düzeyinde kullanılabilen işlevler gösterilmektedir.  
  
|PrintingPermissionLevel|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Tüm yüklü yazıcılara tam erişim sağlar.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Varsayılan yazıcıda programlı yazdırmayı ve kısıtlayıcı bir yazdırma iletişim kutusu aracılığıyla daha güvenli bir şekilde yazdırmayı sağlar. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>, <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>bir alt kümesidir.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Yalnızca daha kısıtlamalı bir iletişim kutusundan yazdırma sağlar. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>, <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>bir alt kümesidir.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Yazıcılara erişimi engeller. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>, <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>bir alt kümesidir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi](more-secure-file-and-data-access-in-windows-forms.md)
- [Windows Forms'ta Ek Güvenlik Konuları](additional-security-considerations-in-windows-forms.md)
- [Windows Forms'ta Güvenliğe Genel Bakış](security-in-windows-forms-overview.md)
- [Windows Forms Güvenliği](windows-forms-security.md)
