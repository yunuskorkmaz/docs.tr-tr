---
title: Windows Forms'ta Daha Güvenli Yazdırma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 2bf05461014c3511725cb28caf2de0eb4c2e1d5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621805"
---
# <a name="more-secure-printing-in-windows-forms"></a>Windows Forms'ta Daha Güvenli Yazdırma
Windows Forms uygulamaları sık yazdırma yetenekleri içerir. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Kullanan <xref:System.Drawing.Printing.PrintingPermission> yazdırma özelliklerine erişimi denetlemek ve ilişkili sınıf <xref:System.Drawing.Printing.PrintingPermissionLevel> erişim düzeyini belirtmek için numaralandırma değeri. Varsayılan olarak, yazdırma, yerel Intranet ve Internet bölgelerinde varsayılan olarak etkindir; Ancak, erişim düzeyi, her iki bölgeleri sınırlıdır. Uygulamanızı yazdırabilir olup olmadığını, kullanıcı etkileşimi gerektirir ya da yazdırma öğesinin uygulamaya verilen izin değeri bağlı olamaz. Varsayılan olarak, yerel Intranet bölgesine alır <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> erişim ve Intranet bölgesi alan <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> erişim.  
  
 Aşağıdaki tablo, her yazdırma izin düzeyinde işlevselliği gösterir.  
  
|PrintingPermissionLevel|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Tüm yüklenen yazıcıları tam erişim sağlar.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Varsayılan yazıcı için program aracılığıyla yazdırma ve kısıtlayıcı bir yazdırma iletişim kutusu aracılığıyla daha güvenli yazdırma sağlar. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> bir alt kümesini <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Yazdırma yalnızca çok sınırlı iletişim kutusu sağlar. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> bir alt kümesini <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Yazıcılar için erişimi engeller. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> bir alt kümesini <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)
- [Windows Forms'ta Ek Güvenlik Konuları](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)
- [Windows Forms'ta Güvenliğe Genel Bakış](../../../docs/framework/winforms/security-in-windows-forms-overview.md)
- [Windows Forms Güvenliği](../../../docs/framework/winforms/windows-forms-security.md)
