---
title: Düğme denetimi seçme yolları
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740009"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Windows Forms Düğme Denetimi Seçmenin Yolları
Windows Forms bir düğme aşağıdaki yollarla seçilebilir:  
  
- Düğmeye tıklayarak fare kullanın.  
  
- Koddaki <xref:System.Windows.Forms.Control.Click> olayını çağırın.  
  
- Sekme tuşuna basarak odağı düğmeye taşıyın ve ardından ara çubuğuna veya ENTER tuşuna basarak düğmeyi seçin.  
  
- Düğme için erişim tuşuna (ALT + altı çizili harfe) basın. Erişim anahtarları hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms denetimleri Için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls.md).  
  
- Düğme, formun "kabul etme" düğmesidir, başka bir denetim odağa sahip olsa bile ENTER tuşuna basmak, diğer denetimin başka bir düğme, çok satırlı bir metin kutusu ya da Enter tuşunu yakaladığı özel bir denetim olması dışında, düğmeyi seçer.  
  
- Düğme, formun "iptal" düğmesidir, başka bir denetim odağa sahip olsa bile ESC tuşuna basmak düğmeyi seçer.  
  
- Düğmeyi program aracılığıyla seçmek için <xref:System.Windows.Forms.Button.PerformClick%2A> yöntemini çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Düğme Kontrolüne Genel Bakış](button-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](how-to-respond-to-windows-forms-button-clicks.md)
- [Düğme Kontrolü](button-control-windows-forms.md)
