---
title: Tasarımcıyı kullanarak bir türe denetim bağlama
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 2257489e123ceeea819ad3538952db51b726c7e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742023"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak bir Windows Formları Denetimini bir Türe Bağlama

Verilerle etkileşen denetimleri oluştururken, bazen bir denetimi bir nesne yerine bir türe bağlamanız gerekir. Genellikle bir denetimi tasarım zamanında bir türe bağlamanız gerekir, ancak veriler kullanılamayabilir, ancak yine de veri bağlama denetimlerinizi bir türün ortak arabiriminden verileri görüntülemesini istiyorsanız. Aşağıdaki yordamlarda, bir türe bağlı yeni <xref:System.Windows.Forms.BindingSource> oluşturma ve ardından türün özelliklerinden birinin bir <xref:System.Windows.Forms.TextBox><xref:System.Windows.Forms.TextBox.Text%2A> özelliğine nasıl bağlanacağı gösterilmektedir.

### <a name="to-bind-the-bindingsource-to-a-type"></a>BindingSource 'un bir türe bağlanması için

1. Windows Forms projesi oluşturun (**Dosya** > **Yeni** > **Proje** > **görsel C#**  veya **Visual Basic** > **Klasik Masaüstü** > Windows Forms **uygulaması**).

2. **Tasarım** görünümü ' nde, form üzerine bir <xref:System.Windows.Forms.BindingSource> bileşeni sürükleyin.

3. **Özellikler** penceresinde <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğinin okuna tıklayın.

4. **DataSource Kullanıcı arabirimi türü düzenleyicisinde**, **proje veri kaynağı Ekle**' ye tıklayın.

5. **Veri kaynağı türü seçin** sayfasında, **nesne** ' yi seçin ve **İleri**' ye tıklayın.

6. Bağlanacak türü seçin:

    - Bağlamak istediğiniz tür geçerli projede ise veya türü içeren derleme zaten başvuru olarak eklendiyse, istediğiniz türü bulmak için düğümleri genişletin ve ardından seçin.

      \-veya-

    - Bağlamak istediğiniz tür diğer bir derlemede ise, şu anda başvuru listesinde değilse, **Başvuru Ekle**' ye tıklayın ve ardından **Projeler** sekmesine tıklayın. istediğiniz Iş nesnesini Içeren projeyi seçin ve **Tamam 'a**tıklayın. Bu proje, derlemeler listesinde görünür, böylece istediğiniz türü bulmak için düğümleri genişletebilir ve ardından bunu seçebilirsiniz.

      > [!NOTE]
      > Bir Framework veya Microsoft derlemesinde bir türe bağlamak istiyorsanız, **Microsoft veya System ile başlayan derlemeleri Gizle** onay kutusunu temizleyin.

7. **İleri**'ye ve ardından **Son**'a tıklayın.

### <a name="to-bind-the-control-to-the-bindingsource"></a>Denetimi BindingSource 'a bağlamak için

1. Forma <xref:System.Windows.Forms.TextBox> ekleyin.

2. **Özellikler** penceresinde **(DataBindings)** düğümünü genişletin.

3. <xref:System.Windows.Forms.TextBox.Text%2A> özelliğinin yanındaki oka tıklayın.

4. **DataSource Kullanıcı arabirimi türü düzenleyicisinde**, daha önce eklenen <xref:System.Windows.Forms.BindingSource> düğümünü genişletin ve <xref:System.Windows.Forms.TextBox><xref:System.Windows.Forms.TextBox.Text%2A> özelliğine bağlamak istediğiniz bağlı türün özelliğini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
