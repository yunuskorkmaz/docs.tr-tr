---
title: 'Nasıl yapılır: Açılır Yardımı Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
ms.openlocfilehash: bf3bcbff0cd6f3bbf71e96e748cb170d5ce68dfc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211407"
---
# <a name="how-to-display-pop-up-help"></a>Nasıl yapılır: Açılır Yardımı görüntüleme

Windows Forms'ta Yardımı görüntülemek için yöntemlerden biri **yardımcı** erişilebilir başlık çubuğunun sağ tarafında bulunan düğmesini <xref:System.Windows.Forms.Form.HelpButton%2A> özelliği. Bu tür bir Yardım görünen iletişim kutuları ile kullanım için uygundur. Kalıcı olarak gösterilen iletişim kutuları (ile <xref:System.Windows.Forms.Form.ShowDialog%2A> yöntemi) kalıcı iletişim kutuları için başka bir pencere odağı kaydırabilirsiniz önce kapatılması gerektiğinden dış yardım sistemleri, getirme konusunda sorun vardır. Ayrıca, kullanarak **yardımcı** düğme gerektirir olduğunu hiçbir **simge durumuna küçült** düğmesini veya **Ekranı Kapla** başlık çubuğunda gösterilen düğmesi. Forms genellikle sahip bir standart iletişim kutusu kuralı ise **simge durumuna küçült** ve **Ekranı Kapla** düğmeleri.

Ayrıca <xref:System.Windows.Forms.HelpProvider> denetimler açılır Yardımı uyguladıysanız olsa bile bir Yardım sisteminde dosyalarına Bağlama bileşeni. Daha fazla bilgi için [bir Windows uygulamasında Yardım sağlama](how-to-provide-help-in-a-windows-application.md).

## <a name="display-pop-up-help"></a>Açılır Yardımı görüntüleme

1. Visual Studio'da sürükleyin bir [HelpProvider](../controls/helpprovider-component-windows-forms.md) formunuza bileşen araç kutusundan.

   Windows Form Tasarımcısı'nın altındaki tepsisinde şaşıracaksınız.

2. Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.Form.HelpButton%2A> özelliğini `true`. Bu düğmeye sahip bir soru işareti içinde formun başlık çubuğunun sağ tarafında görüntülenir.

3. Sırayla <xref:System.Windows.Forms.Form.HelpButton%2A> görüntülemek için formun <xref:System.Windows.Forms.Form.MinimizeBox%2A> ve <xref:System.Windows.Forms.Form.MaximizeBox%2A> özellikler ayarlanmalıdır `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> özelliğini `true`ve <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliğini şu değerlerden biri: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> veya <xref:System.Windows.Forms.FormBorderStyle.Sizable>.

4. Formunuzda yardımını göster ve Özellikler penceresinde Yardım dizesi ayarlamak istediğiniz denetimi seçin. Benzer şekilde bir pencerede görüntülenen metin dizesidir bir [araç ipucu](../controls/tooltip-component-windows-forms.md).

5. Tuşuna **F5**.

6. Tuşuna **yardımcı** başlık çubuğunda düğme ve Yardım dizesi ayarladığınız denetimi tıklatın.

## <a name="see-also"></a>Ayrıca bkz.

- [ToolTips Kullanarak Denetim Yardımı](control-help-using-tooltips.md)
- [Windows Forms'ta Kullanıcı Yardımını Tümleştirme](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
