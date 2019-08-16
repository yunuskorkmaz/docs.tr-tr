---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Kabul Düğmesi olarak bir Windows Forms Düğmesi Atama'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27ecb26c493232bcfb996d012f9760b7ef91e5b2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039654"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Kabul Düğmesi olarak bir Windows Forms Düğmesi Atama
Herhangi bir Windows formunda, bir <xref:System.Windows.Forms.Button> denetimi varsayılan düğme olarak da bilinen kabul et düğmesi olacak şekilde belirleyebilirsiniz. Kullanıcı ENTER tuşuna bastığında, form üzerindeki diğer denetimin odağa sahip olduğu bağımsız olarak varsayılan düğme tıklanmalıdır. Bunun özel durumları, odağa sahip olan denetimin başka bir düğme olduğu durumdur. Bu durumda, odağa sahip düğme veya çok satırlı bir metin kutusu ya da ENTER tuşunu yakaladığı özel bir denetim olur.

## <a name="to-designate-the-accept-button"></a>Kabul et düğmesini belirlemek için

1. Düğmenin bulunduğu formu seçin.

2. **Özellikler** penceresinde, formun <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğini <xref:System.Windows.Forms.Button> denetimin adı olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Düğme Kontrolüne Genel Bakış](button-control-overview-windows-forms.md)
- [Windows Forms Düğme Kontrolü Seçme Yolları](ways-to-select-a-windows-forms-button-control.md)
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt verme](how-to-respond-to-windows-forms-button-clicks.md)
- [Nasıl yapılır: Tasarımcıyı kullanarak Iptal düğmesi olarak bir Windows Forms düğmesi belirleyin](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Düğme Kontrolü](button-control-windows-forms.md)
