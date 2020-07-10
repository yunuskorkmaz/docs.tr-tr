---
title: 'Nasıl yapılır: MDI Üst Formları Oluşturma'
description: Programlama yoluyla ve Windows Form Tasarımcısı kullanarak bir MDI üst formu oluşturmayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d387837a565ca247f62828c19f353990b35117c7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174711"
---
# <a name="how-to-create-mdi-parent-forms"></a>Nasıl yapılır: MDI Üst Formları Oluşturma

> [!IMPORTANT]
> Bu konu, <xref:System.Windows.Forms.MainMenu> Denetim tarafından değiştirilmiş olan denetimini kullanır <xref:System.Windows.Forms.MenuStrip> . <xref:System.Windows.Forms.MainMenu>' Yi seçerseniz, Denetim hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Kullanarak bir MDI parent formu oluşturma hakkında daha fazla bilgi için <xref:System.Windows.Forms.MenuStrip> bkz. [nasıl yapılır: MENUSTRIP Ile MDI pencere listesi oluşturma](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).

Çoklu belge arabirimi (MDI) uygulamasının temeli MDI parent formundadır. Bu, kullanıcının MDI uygulamasıyla etkileşime girdiği alt pencereler olan MDI alt pencerelerini içeren formdur. MDI parent form oluşturmak kolaydır, hem Windows Form Tasarımcısı hem de programlı olarak.

## <a name="create-an-mdi-parent-form-at-design-time"></a>Tasarım zamanında bir MDI parent formu oluşturma

1. Visual Studio 'da bir Windows uygulama projesi oluşturun.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliği **true**olarak ayarlayın.

     Bu, formu alt Windows için bir MDI kapsayıcısı olarak belirler.

    > [!NOTE]
    > **Özellikler penceresinde özellikleri** ayarlarken, `WindowState` üst form ekranı KAPLADıKTAN sonra MDI alt pencerelerini işlemek en kolay olduğu Için özelliği de **ekranı kaplamış**olarak ayarlayabilirsiniz. Ayrıca, MDI parent form ucunun, özelliği kullanarak ayarladığınız arka rengi yerine sistem rengini (Windows Sistem Denetim Masası 'nda ayarlanır) aldığını unutmayın <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> .

3. **Araç kutusundan**bir **MenuStrip** denetimini forma sürükleyin. **Metin** özelliği, **yeni&** ve **&kapat**olarak adlandırılan alt menü öğeleriyle **&dosya** olarak ayarlanmış bir üst düzey menü öğesi oluşturun. Ayrıca **&pencere**adlı bir üst düzey menü öğesi oluşturun.

     İlk menü çalışma zamanında menü öğelerini oluşturup gizler ve ikinci menü açık MDI alt pencerelerini takip eder. Bu noktada, bir MDI üst penceresi oluşturdunuz.

4. Uygulamayı çalıştırmak için **F5**'e basın. MDI parent form içinde çalışan MDI alt pencereleri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: MDI alt formları oluşturma](how-to-create-mdi-child-forms.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu Belge Arabirimi (MDI) Uygulamaları](multiple-document-interface-mdi-applications.md)
- [Nasıl yapılır: MDI Alt Formları Oluşturma](how-to-create-mdi-child-forms.md)
- [Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme](how-to-determine-the-active-mdi-child.md)
- [Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme](how-to-send-data-to-the-active-mdi-child.md)
- [Nasıl yapılır: MDI Alt Formlarını Düzenleme](how-to-arrange-mdi-child-forms.md)
