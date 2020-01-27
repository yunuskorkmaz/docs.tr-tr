---
title: Tasarımcı kullanarak bir düğmeyi Iptal düğmesi olarak belirleme
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: 95d1139b6e339055f944ad0b0967a6d91283d49e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746056"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak İptal Düğmesi olarak bir Windows Formları Düğmesi Atama
Herhangi bir Windows formunda, bir <xref:System.Windows.Forms.Button> denetimini iptal düğmesi olacak şekilde belirleyebilirsiniz. Kullanıcı, form üzerindeki diğer denetimin odağa sahip olduğu bağımsız olarak ESC tuşuna bastığında bir iptal düğmesi görüntülenir. Bu tür bir düğme, genellikle kullanıcının herhangi bir eylemde bulunmadan bir işlemden hızlı bir şekilde çıkmasına olanak tanımak üzere programlanır.

## <a name="to-designate-the-cancel-button"></a>İptal düğmesini belirlemek için

1. Düğmenin bulunduğu formu seçin.

2. **Özellikler** penceresinde, formun <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğini <xref:System.Windows.Forms.Button> denetimin adı olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Düğme Kontrolüne Genel Bakış](button-control-overview-windows-forms.md)
- [Windows Forms Düğme Kontrolü Seçme Yolları](ways-to-select-a-windows-forms-button-control.md)
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](how-to-respond-to-windows-forms-button-clicks.md)
- [Nasıl yapılır: Tasarımcı Kullanarak Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Düğme Kontrolü](button-control-windows-forms.md)
