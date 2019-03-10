---
title: Windows Forms'ta Daha Güvenli Yazdırma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 2fd61ea1c56ee2dbe7ff725d9f9f79df6b6cdfd8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723055"
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
- [Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi](more-secure-file-and-data-access-in-windows-forms.md)
- [Windows Forms'ta Ek Güvenlik Konuları](additional-security-considerations-in-windows-forms.md)
- [Windows Forms'ta Güvenliğe Genel Bakış](security-in-windows-forms-overview.md)
- [Windows Forms Güvenliği](windows-forms-security.md)
