---
title: 'Nasıl yapılır: Tasarımcı Kullanarak İptal Düğmesi olarak bir Windows Forms Düğmesi Atama'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: cc352f15fb1e8b531cd0f9b298b2db4ce649d3cf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039642"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak İptal Düğmesi olarak bir Windows Forms Düğmesi Atama
Herhangi bir Windows formunda, bir <xref:System.Windows.Forms.Button> denetimi iptal düğmesi olacak şekilde belirleyebilirsiniz. Kullanıcı, form üzerindeki diğer denetimin odağa sahip olduğu bağımsız olarak ESC tuşuna bastığında bir iptal düğmesi görüntülenir. Bu tür bir düğme, genellikle kullanıcının herhangi bir eylemde bulunmadan bir işlemden hızlı bir şekilde çıkmasına olanak tanımak üzere programlanır.

## <a name="to-designate-the-cancel-button"></a>İptal düğmesini belirlemek için

1. Düğmenin bulunduğu formu seçin.

2. **Özellikler** penceresinde, formun <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğini <xref:System.Windows.Forms.Button> denetimin adı olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Düğme Kontrolüne Genel Bakış](button-control-overview-windows-forms.md)
- [Windows Forms Düğme Kontrolü Seçme Yolları](ways-to-select-a-windows-forms-button-control.md)
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt verme](how-to-respond-to-windows-forms-button-clicks.md)
- [Nasıl yapılır: Tasarımcıyı kullanarak kabul et düğmesi olarak bir Windows Forms düğmesi belirleyin](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Düğme Kontrolü](button-control-windows-forms.md)
